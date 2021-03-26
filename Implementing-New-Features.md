Custom features can be created by extending the `Extractor` and `Retriever` interfaces.
Most features implement both of these interfaces, which can also be done by extending the abstract class `AbstractFeatureModule`, which provides additional utility functions and defaults.

## Simple Example

The following example demonstrates a how the `AbstractFeatureModule` class can be extended to create a simple new image feature representing a vector containing the dimensions of the image or video (Imports are omitted for brevity, class is expected to be contained in the `org.vitrivr.cineast.core.features` package):

```java
public class ImageDimensions extends AbstractFeatureModule {

  // A basic constructor call the super constructor must be provided with the following arguments:
  //   tableName: the name that the feature will have in the persistent storage (by convention "features_<class name>")
  //   maxDist: the maximum distance after which the similarity between two vectors should be considered 0
  //   vectorLength: the length of the feature vectors in the persistent storage
  public ImageDimensions() {
    super("features_ImageDimensions", 1000f, 2);
  }

  // This is the function required by the Extractor, which extracts the feature when new media objects are ingested
  @Override
  public void processSegment(SegmentContainer sc) {
    MultiImage image = sc.getAvgImg();
    // Here we check if the current media segment has an image component
    if (image == MultiImage.EMPTY_MULTIIMAGE) {
      return;
    }
    // Here we check that we haven't already extracted the current feature for the current media segment
    if (!phandler.idExists(sc.getId())) {
      float[] vector = new float[]{image.getWidth(), image.getHeight()};
      // Here we pass the calculated feature vector to the persistent storage
      persist(sc.getId(), new FloatVectorImpl(vector));
    }
  }

  // This is the function required by the Retriever, which performs a similarity query given a query media segment
  @Override
  public List<ScoreElement> getSimilar(SegmentContainer sc, ReadableQueryConfig qc) {
    MultiImage image = sc.getAvgImg();
    float[] query = new float[]{image.getWidth(), image.getHeight()};
    // Here we use the feature vector calculated from the query segment to search for similar segments using standard
    // nearest-neighbor search
    return getSimilar(query, qc);
  }
}
```

To use your custom feature in extraction and retrieval tasks:
- **Extraction:** Add the classname of your custom feature (`ImageDimensions` in the case of this example) to your extraction configuration file
- **Retrieval:** Add the classname of your custom feature to the Cineast configuration file as a retriever