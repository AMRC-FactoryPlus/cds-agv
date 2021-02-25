# Factory+ AGV Common Data Structure

The CDS is a common order and format of variables taken from different devices to ensure data/metadata is gathered in a consistent format when stored and shared across the the Factory+ architecture.

Decided that we should have a separate Fleet/AGV CDS.

In the AGV Fleet Manager CDS, have included:
* Fleet State
* Mission List
* Robot List -> Status
* Mission Scheduler (this is the set of parameters that allows for control of the robots)
* Users


Also included is the CDS for an individual robot. The extracting data from an individual AGV and storing it in its own CDS has not yet been implemented as part of Factory+. Since we have multiple AGVs, only the data from the Fleet has been implemented. Here we include an initial draft of what the CDS for a single AGV would look like.

List of datatypes used for the variables in this CDS:
* String
* Boolean
* UInt32
* Float
* DateTime

These datatypes are what is currently being used. Any other Sparkplug compliant datatype can be used for `User_Defined` variables.

Example variable: the `x` coordinate of a robot (with Robot ID = 5) would be under `AGV_Fleet_Manager/MiR_Fleet_1/Robot_List/5/Status/Current_Position/Pos_X`.
