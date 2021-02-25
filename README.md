# factoryplus-cds-agv

The Common Data Structure (CDS) for AGVs in JSON format.

The CDS is a common order and format of variables taken from different devices to ensure data/metadata is gathered in a consistent format when stored on the Factory+ network.

Decided that we should have a separate Fleet/AGV CDS.

In the AGV Fleet Manager CDS, have included:
* Fleet State
* Mission List
* Robot List -> Status
* Mission Scheduler (this is the set of parameters that allows for control of the robots)
* Users


Also included is the CDS for an individual robot. The extracting data from an individual AGV and storing it in its own CDS has not yet been implemented as part of Factory+. Since we have multiple AGVs, only the data from the Fleet has been implemented. Here we include an initial draft of what the CDS for a single AGV would look like. **This will likely need to be refined when used for a real device.**

List of datatypes used for the variables in this CDS:

* String
* Boolean
* UInt32
* Float
* DateTime

These datatypes are what is currently being used. Any other Sparkplug compliant datatype can be used for "User_Defined" variables.

Example variable: the x coordinate of a robot (with Robot ID = 5) would be under "AGV_Fleet_Manager/MiR_Fleet_1/Robot_List/5/Status/Current_Position/Pos_X".

## Future work
Can potentially upload a tag structure diagram to this repository to be able to better visualise the hierarchy. This would need to be kept upto date as the CDS structure is updated in future merges - may be worth doing programmatically in the future; automatically generate a diagram as edits are made to the JSON file?

## Notes/changes:

20/10/2020
- Updated the structure of the CDS so that whenever an array object is encountered, the subsequent level in the CDS path must be an additional level containing the object's index/name. This is denoted by variables within <> in the CDS and these should be changed to provide meaningful names. For example to find the x coordinate of the origin of a map would be "MapList/Factory2050Mk1/OriginX".

05/01/2021
- Removed a lot of data from the CDS to keep payload size manageable for the translation app.
- Changed all names to use Title Case to be consistent with rest of Factory+ naming conventions.
- Added top-level folder of "AGV Fleet Manager" which will be the DeviceType for this dataset when used in an Origin Map.

11/01/2021
- changed from Title Case to Pascal_Snake_Case to be consistent with the rest of Factory+ naming (as there were issues with spaces in the group id of the topic structure).

18/01/2021
- added Created_By_Name and Submit_New_Mission_JSON under Mission_Scheduler to help with requesting missions through Factory+. Also added Users list.


25/01/2021

- removed `Metric Name` as the top level item
- put `User_Defined` as a folder under the `AGV_Fleet_Manager/<Fleet_Name>/` folder structure. This is now consistent with all CDSs
- applied the same changes to the AGV CDS
