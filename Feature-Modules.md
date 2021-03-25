This page lists the feature modules which Cineast uses for feature extraction and retrieval.

## Structure
A feature module implements either the `Retriever` or the `Extractor` interface, most implement both. The `Retriever` interface defines the methods used for similarity search while the `Extractor` interface defines the methods required for feature extraction. Feature modules are located in the `org.vitrivr.cineast.core.features` package.

## Segment Container
Segment containers contain a subset of information of a media segment and are used as input for retrievers and extractors.
A segment container may contain all of the information made available through the multiple provider interfaces implemented by it.
Depending on the type of media segment a segment container represents, it will contain a different subset of this information and provide only default values for the rest.

The information a segment container may provide includes:

Information | Description
--- | ---
Audio Frame | The list of audio frames contained within an audio segment.
Audio STFT | The Short-term Fourier Transform of an audio segment.
Average Image | The average image is the pixel-wise color average of all frames of a shot.
Boolean Expression | A boolean expression as defined by the class `BooleanExpression`.
Duration | The start and end position of a shot with respect to the entire video.
Frame List | The frame list consists of all frames of a shot in chronological order, including the absolute position of the frames within the video.
ID | The ID of this segment and of the media object it belongs to.
Instant | An instant in time.
Location | The location as defined by the class `Location`.
Median Image | The median image is the pixel-wise color median of all frames of a shot.
Mesh | The 3D mesh of the media segment.
Most Representative Frame | The most representative frame is the one frame of a shot with the smallest pixel-wise color distance to the average frame.
Path | Motion paths are sparely-tracked trajectories of interest-points.
Semantic Map | A map of semantic labels as defined in the class `SemanticMap`.
Subtitle Item | All subtitle elements which would be displayed during the shot.
Tag | A list of conceptual tags associated with the media segment.
Text | The text associated with the media segment.
Voxel Grid | The voxel grid of the media segment.

## Feature Modules

The following table lists all feature modules that are already implemented within Cineast:

Name | Type | Input | Description
--- | --- | --- | ---
AudioFingerprint | TODO | TODO | TODO
AudioTranscriptionSearch | TODO | TODO | TODO
AverageColor | global color | average image | Average over all pixels of a shot
AverageColorArp44 | local color | average image | 4x4 ARP partition-wise average color over all pixels of a shot
AverageColorArp44Normalized | local color | average image | Same as AverageColorArp44 but the input image gets normalized first
AverageColorCLD | local color | average image | Color layout descriptor of the average image
AverageColorCLDNormalized | local color | average image | Same as AverageColorCLD but the input image gets normalized first
AverageColorGrid8 | local color | average image | 8x8 grid-wise average color
AverageColorGrid8Normalized | local color | average image | Same as AverageColorGrid8 but the input image gets normalized first
AverageColorGrid8Reduced11 | TODO | TODO | TODO
AverageColorGrid8Reduced15 | TODO | TODO | TODO
AverageColorRaster | local color | average image | 8x8 color-quantized image, registration is used as similarity measure
AverageColorRasterReduced11 | TODO | TODO | TODO
AverageColorRasterReduced15 | TODO | TODO | TODO
AverageFuzzyHist | global color | average image | 15-bin fuzzy color histogram
AverageFuzzyHistNormalized | global color | average image | Same as AverageFuzzyHist but the input image gets normalized first
AverageHPCP20F36B | TODO | TODO | TODO
AverageHPCP30F36B | TODO | TODO | TODO
CENS12BasslineShingle | TODO | TODO | TODO
CENS12MelodyShingle | TODO | TODO | TODO
CENS12Shingle | TODO | TODO | TODO
ChromaGrid8 | local color | most representative frame | 8x8 Grid of average chroma values
CLD | local color | most representative frame | Color Layout descriptor
CLDNormalized | local color | most representative frame | Same as CLD but the input image gets normalized first
CLDReduced11 | TODO | TODO | TODO
CLDReduced15 | TODO | TODO | TODO
ConceptMasks | TODO | TODO | TODO
ConceptMasksAde20k | TODO | TODO | TODO
**REMOVED** Contrast | global color | most representative frame | Contrast value of the frame
DailyCollectionBooleanRetriever | TODO | TODO | TODO
DailyRangeBooleanRetriever | TODO | TODO | TODO
DCTImageHash | TODO | TODO | TODO
DescriptionTextSearch | TODO | TODO | TODO
DominantColors | global color | most representative frame | Three most dominant colors as determined by k-means clustering
DominantEdgeGrid16 | edge | most representative frame | 16x16 grid of dominant edge direction quantized into 4 directions
DominantEdgeGrid8 | edge | most representative frame | 16x16 grid of dominant edge direction quantized into 4 directions
EdgeArp88 | edge | most representative frame | 8x8 arp partitioned ratio of edge and non-edge pixels
EdgeArp88Full | edge | frame list | same as EdgeArp88 but computed using all frames of a shot
EdgeGrid16 | edge | most representative frame | 16x16 grid partitioned ratio of edge and non-edge pixels
EdgeGrid16Full | edge | frame list | same as EdgeGrid16 but computed using all frames of a shot
EHD | edge | most representative frame | Edge Histogram Descriptor
ForegroundBoundingBox | TODO | TODO | TODO
HOGMirflickr25K256 | TODO | TODO | TODO
HOGMirflickr25K512 | TODO | TODO | TODO
HPCP12BasslineShingle | TODO | TODO | TODO
HPCP12MelodyShingle | TODO | TODO | TODO
HPCP12Shingle | TODO | TODO | TODO
HueHistogram | TODO | TODO | TODO
HueValueVarianceGrid8 | local color | frame list | 8x8 grid partitioned average and variance of hue and value of a shot
LightfieldFourier | TODO | TODO | TODO
LightfieldZernike | TODO | TODO | TODO
MedianColor | global color | median image | median color of a shot
MedianColorArp44 | local color | median image | 4x4 arp partitioned median color
MedianColorARP44Normalized | local color | median image | Same as MedianColorARP44Normalized but the input image gets normalized first
MedianColorGrid8 | local color | median image | 8x8 grid-wise median color
MedianColorGrid8Normalized | local color | median image | Same as MedianColorGrid8but the input image gets normalized first
MedianColorRaster | local color | median image | 8x8 color-quantised image, registration is used as similarity measure
MedianFuzzyHist | local color | median image | 15-bin fuzzy color histogram
MedianFuzzyHistNormalized | local color | median image | Same as MedianFuzzyHistbut the input image gets normalized first
MelodyEstimate | TODO | TODO | TODO
MFCCShingle | TODO | TODO | TODO
MotionHistogram | motion | motion paths | 8-bin normalized motion histogram
MotionHistogramBackground | TODO | TODO | TODO
**REMOVED** MotionSum | motion | motion paths | sum of total trajectory length
ObjectInstances | TODO | TODO | TODO
OCRSearch | TODO | TODO | TODO
RangeBooleanRetriever | TODO | TODO | TODO
SaturationGrid8 | local color | most representative frame | 8x8 grid-partitioned saturation value
SegmentTags | TODO | TODO | TODO
ShapeCentroidDistance | TODO | TODO | TODO
SpatialDistance | TODO | TODO | TODO
SphericalHarmonicsDefault | TODO | TODO | TODO
SphericalHarmonicsHigh | TODO | TODO | TODO
SphericalHarmonicsLow | TODO | TODO | TODO
STMP7EH | motion | frame list | STMP7EH motion descriptor
SubDivAverageFuzzyColor | local color | average image | same as AverageFuzzyHist but on a 3x3 grid-partition
SubDivMedianFuzzyColor | local color | median image | same as MedianFuzzyHist but on a 3x3 grid-partition
SubDivMotionHistogram2 | motion | motion paths | Same as MotionHistogram but with a 2x2 grid-partition
SubDivMotionHistogram3 | motion | motion paths | Same as MotionHistogram but with a 3x3 grid-partition
SubDivMotionHistogram4 | motion | motion paths | Same as MotionHistogram but with a 4x4 grid-partition
SubDivMotionHistogram5 | motion | motion paths | Same as MotionHistogram but with a 5x5 grid-partition
SubDivMotionHistogramBackground2 | TODO | TODO | TODO
SubDivMotionHistogramBackground3 | TODO | TODO | TODO
SubDivMotionHistogramBackground4 | TODO | TODO | TODO
SubDivMotionHistogramBackground5 | TODO | TODO | TODO
SubDivMotionSum2 | motion | motion paths | Same as MotionSum but with a 2x2 grid-partition
SubDivMotionSum3 | motion | motion paths | Same as MotionSum but with a 3x3 grid-partition
SubDivMotionSum4 | motion | motion paths | Same as MotionSum but with a 4x4 grid-partition
SubDivMotionSum5 | motion | motion paths | Same as MotionSum but with a 5x5 grid-partition
SubDivMotionSumBackground2 | TODO | TODO | TODO
SubDivMotionSumBackground3 | TODO | TODO | TODO
SubDivMotionSumBackground4 | TODO | TODO | TODO
SubDivMotionSumBackground5 | TODO | TODO | TODO
SubtitleFulltextSearch | text | subtitles | matches sentence fragments in subtitle elements
**REMOVED** SubtitleWordSearch | text | subtitles | matches words independent of order in subtitle elements
SURFMirflickr25K256 | TODO | TODO | TODO
SURFMirflickr25K512 | TODO | TODO | TODO
TagsFtSearch | TODO | TODO | TODO
TemporalDistance | TODO | TODO | TODO
WSDMTICollectionBooleanRetriever | TODO | TODO | TODO