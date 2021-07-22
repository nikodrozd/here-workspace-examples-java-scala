# HERE Workspace Examples for Java and Scala Developers

## Introduction

This repository holds a series of Java and Scala examples, that demonstrate  typical use cases for the HERE Workspace – a part of HERE platform. HERE Workspace is an environment to enrich, transform and deploy location-centric data.
Go to [HERE platform](https://developer.here.com/products/open-location-platform) to learn more. If you are interested in knowing what the platform offers specifically for Java and Scala developers, visit [this page](https://developer.here.com/documentation/sdk-developer-guide/dev_guide/index.html).

## Prerequisites

In order to run the examples, you need to have a HERE Workspace account. If you do not have an account, navigate to [Pricing and Plans](https://developer.here.com/pricing/open-location-platform) to apply for a free trial.

You need to get access credentials and prepare your environment. For more information on how to prepare your environment, see our [guide for Java and Scala developers](https://developer.here.com/documentation/sdk-developer-guide/dev_guide/topics/how-to-use-sdk.html).

## Code Examples

### Processing Sensor Data

The following documents illustrate two use cases around inferring real-world situations from sensor data. [Batch processing](https://developer.here.com/documentation/java-scala-dev/dev_guide/topics/example-use-cases.html#use-case-map-of-recommended-speed-based-on-sensor-observations-and-other-data) is useful when it is important to aggregate sensor input over a longer time period (that is hours and longer). [Stream processing](https://developer.here.com/documentation/java-scala-dev/dev_guide/topics/example-use-cases.html#use-case-turning-sensor-data-into-warnings) is recommended for time-critical use cases, like informing about road hazards.

| Name | Description | Source | Labels / Topics |
| ---- | ----------- | ------ | --------------- |
| Infer Stop Sign Locations from Automotive Sensor Observations | The example takes archived sensor data, clusters and path-matches it in a distributed Spark batch environment, and creates a map layer with stop signs at the output. | [Scala](location/scala/spark/infer-stop-signs-from-sensors) | Location Library, Data Client Library, Spark, Batch, GeoJSON, SDII |
| Stream Path Matcher | The example stands for a similar but time critical use case. It does not hash out anything but map matching. It takes sensor data from a stream, map-matches it in Flink, and puts on an output stream. |  [Java](location/java/flink/stream-path-matcher)  | Location Library, Data Client Library, Flink, Stream, SDII  |

### Incremental Map Processing & Validation

For more information, see a use case illustration of [keeping a client map up to date with incremental processing](https://developer.here.com/documentation/java-scala-dev/dev_guide/topics/example-use-cases.html#use-case-incremental-map-processing).

| Name | Description | Source | Labels / Topics |
| ---- | ----------- | ------ | --------------- |
| Geometry Lifter | An application that takes level 12 partitions of road topology and geometry and aggregates them to higher-level (i.e. bigger) partitions. | [Java](data-processing/java/geometry-lifter) / [Scala](data-processing/scala/geometry-lifter) | Data Processing Library, Spark, Batch, Protobuf, HERE Map Content |
| Pedestrian Topologies Extraction to GeoJSON | Topologies, accessible by pedestrians, are selected based on the segment attributes and then are transformed into GeoJSON file format and stored in a new catalog. | [Java](data-processing/java/pedestrian-topologies-extraction-geojson) / [Scala](data-processing/scala/pedestrian-topologies-extraction-geojson) | Data Processing Library, Spark, Batch, GeoJSON, HERE Map Content |
| Pedestrian Topologies Extraction to Protobuf | Topologies, accessible by pedestrians, are selected based on the segment attributes and then are transformed to a newly created proto schema format and stored in a new catalog layer that follows that schema. | [Java](data-processing/java/pedestrian-topologies-extraction-protobuf) / [Scala](data-processing/scala/pedestrian-topologies-extraction-protobuf) | Data Processing Library, Spark, Batch, Protobuf, HERE Map Content |
| Statistics creation across multiple processing runs with stateful processing | The application counts how often the node cardinality of the topology changes in each partition. | [Java](data-processing/java/stateful-nodecardinality-extraction) / [Scala](data-processing/scala/stateful-nodecardinality-extraction) | Data Processing Library, Spark, Batch, JSON, HERE Map Content |
| Here Map Content Diff-Tool | An application to compare the content of two different versions of an input catalog. | [Java](data-processing/java/heremapcontent-difftool) / [Scala](data-processing/scala/heremapcontent-difftool) | Data Processing Library, Spark, Batch, JSON, HERE Map Content  |
| Here Map Content Validation | An application to validate road topology and geometry content against a set of acceptance criteria using [scalatest](www.scalatest.org). | [Scala](data-processing/scala/heremapcontent-validation) | Data Processing Library, Spark, Batch, JSON, HERE Map Content  |

### Archiving Stream Data

The HERE Workspace allows you to retain stream data for longer periods, which allows you to later query and process the retained data for non-real-time use cases.
For more information, see [Data Archiving Library Developer Guide](https://developer.here.com/documentation/data-archiving-library/dev_guide/index.html).

| Name | Description | Source | Labels / Topics |
| ---- | ----------- | ------ | --------------- |
| Archiving SDII stream data in Avro | The example shows how to use the Data Archiving Library to quickly develop an archiving solution that archives data in Avro format. | [Java](data-archive/java/avro-example) | Data Archiving Library, Flink, Stream, Avro, SDII |
| Archiving SDII stream data in Parquet | The example shows how to use the Data Archiving Library to quickly develop an archiving solution that archives data in Parquet format. | [Java](data-archive/java/parquet-example) | Data Archiving Library, Flink, Stream, Parquet, SDII |
| Archiving SDII stream data in Protobuf | The example shows how to use the Data Archiving Library to quickly develop an archiving solution that archives data in Protobuf format. | [Java](data-archive/java/protobuf-example) | Data Archiving Library, Flink, Stream, Protobuf, SDII|
| Archiving SENSORIS stream data in Parquet| The example shows how to use the Data Archiving Library to quickly develop an archiving solution that archives SENSORIS data in Parquet format. | [Java](data-archive/java/sensoris-parquet-example) | Data Archiving Library, Flink, Stream, SENSORIS, Parquet |
| Archiving SENSORIS stream data in Protobuf| The example shows how to use the Data Archiving Library to quickly develop an archiving solution that archives SENSORIS data in Protobuf format. | [Java](data-archive/java/sensoris-protobuf-example) | Data Archiving Library, Flink, Stream, SENSORIS, Protobuf |

### Compacting Index Data

The HERE Workspace allows you to compact data files with the same index attribute values into one or more files based on the configuration.
Compaction reduces the index layer storage cost, improves query performance, and makes subsequent data processing more efficient.
For more information, see [Index Compaction Library Developer Guide](https://developer.here.com/documentation/index-compaction-library/dev_guide/index.html).

| Name | Description | Source | Labels / Topics |
| ---- | ----------- | ------ | --------------- |
| Compacting Parquet format indexed data | The example shows how to use the Index Compaction Library to quickly develop a compaction application that compacts parquet format data. | [Java](index-compaction-batch/java/parquet-example) | Index Compaction Library, Spark, Batch, Parquet, SDII |
| Compacting Protobuf format indexed data | The example shows how to use the Index Compaction Library to quickly develop a compaction application that compacts protobuf format data. | [Java](index-compaction-batch/java/protobuf-example) | Index Compaction Library, Spark, Batch, Parquet, SDII | 

### Small Examples Showing Usage of Location Library

The following examples demonstrate how to use the Location Library. 

| Name | Description | Source | Labels / Topics |
| ---- | ----------- | ------ | --------------- |
| Point Matching Example | Takes probe points and matches each one against the closest geometry without consider the path. | [Java](location/java/standalone#point-matching-example) / [Scala](location/scala/standalone#point-matching-example) | Location Library, GeoJSON, CSV |
| Traversing the Graph | Shows how to create a traversable graph from the HERE Optimized Map for Location Library catalog. | [Java](location/java/standalone#traversing-the-graph) / [Scala](location/scala/standalone#traversing-the-graph) | Location Library, GeoJSON |
| Most Probable Path | Navigates the graph along the most probable path based on simple assumptions like try to stay on same functional class. | [Java](location/java/standalone#most-probable-path) / [Scala](location/scala/standalone#most-probable-path) | Location Library, GeoJSON |
| Path Matching Example | Matches path probe points against the graph. | [Java](location/java/standalone#path-matching-example) / [Scala](location/scala/standalone#path-matching-example) | Location Library, GeoJSON, CSV |
| Path Matching with Restrictions | Matches path probe points against a graph that excludes segments that are not accessible by taxis. | [Scala](location/scala/standalone#path-matching-with-restrictions) | Location Library, GeoJSON, CSV |
| Turn Restrictions | Shows how to check if turns on a road network are restricted or not. | [Java](location/java/standalone#turn-restrictions) / [Scala](location/scala/standalone#turn-restrictions) | Location Library, GeoJSON |
| Generic Range Based Attributes | Shows how to load a generic attribute that is not available in the HERE Optimized Map for Location Library using a Vertex reference as input. | [Java](location/java/standalone#generic-range-based-attributes) / [Scala](location/scala/standalone#generic-range-based-attributes) | Location Library |
| Path Matching Sparse Probe Data | Shows how to match sparse path points against the graph by traversing it using the most probable path assumptions. | [Java](location/java/standalone#path-matching-sparse-probe-data) / [Scala](location/scala/standalone#path-matching-sparse-probe-data) | Location Library, GeoJSON, CSV |
| Converting References from HERE Optimized Map for Location Library to HERE Map Content | Converts Vertex references to Topology Segments and vice versa. | [Java](location/java/standalone#converting-references-from-here-optimized-map-for-location-library-to-here-map-content) / [Scala](location/scala/standalone#converting-references-from-here-optimized-map-for-location-library-to-here-map-content) | Location Library, HERE Map Content |
| Converting References from TPEG2 to its Binary Representation | Shows how to read an OpenLR location reference that has been written in the TPEG2 XML encoding and convert it to its binary representation.| [Java](location/java/standalone#converting-references-from-tpeg2-to-its-binary-representation) / [Scala](location/scala/standalone#converting-references-from-tpeg2-to-its-binary-representation) | Location Library, TPEG2, OpenLR|
| Extracting TPEG2 Document | Demonstrates how to load a TPEG2 document and extract its parts.| [Java](location/java/standalone#extracting-tpeg2-document) / [Scala](location/scala/standalone#extracting-tpeg2-document) | Location Library, TPEG2 |
| Creating and Resolving TMC Reference | Searches for a well-known vertex that is covered by TMC to define the input location.| [Java](location/java/standalone#creating-and-resolving-tmc-reference) / [Scala](location/scala/standalone#creating-and-resolving-tmc-reference) | Location Library, TMC |
| Resolving TMC References in RTTI Message | Demonstrates how TMC references in Real Time Traffic Incident (RTTI) messages can be converted to TPEG2 TMC references, and how the `location-referencing` module can be used to resolve those references. | [Java](location/java/standalone#resolving-tmc-references-in-rtti-message) / [Scala](location/scala/standalone#resolving-tmc-references-in-rtti-message) | Location Library, TPEG2 |
| Creating OpenLR Reference from Road Segments | Transforms a path given as segment references in HERE Map Content to OpenLR reference. | [Java](location/java/standalone#creating-openlr-reference-from-road-segments) / [Scala](location/scala/standalone#creating-openlr-reference-from-road-segments) | Location Library, HERE Map Content, OpenLR |
| Resolving OpenLR Reference from Road Segments | Shows how to take an OpenLR reference given in XML and resolve this reference to segments in HERE Map Content | [Java](location/java/standalone#resolving-openlr-reference-from-road-segments) / [Scala](location/scala/standalone#resolving-openlr-reference-from-road-segments) | Location Library, HERE Map Content, OpenLR |
| Functional Class for a Vertex | Shows how you can get the functional class for a vertex. | [Java](location/java/standalone#functional-class-for-a-vertex) / [Scala](location/scala/standalone#functional-class-for-a-vertex) | Location Library, GeoJSON |
| ADAS Curvature Attribute | Shows how to fetch and use ADAS attributes in the HERE Optimized Map for Location Library using a Vertex or an Edge reference. | [Java](location/java/standalone#adas-curvature-attribute) / [Scala](location/scala/standalone#adas-curvature-attribute) | Location Library, GeoJSON |

## License

Copyright (C) 2017-2021 HERE Europe B.V.

Unless otherwise noted in `LICENSE` files, source code files for specific files or directories, the [LICENSE](LICENSE) in the root applies to all content in this repository.
