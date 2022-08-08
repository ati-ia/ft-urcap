# ATI F/T URCap

This URCap software integrates the FT Sensor with Universal Robots' force feedback functionality, and includes example demo programs. Compatible with NET F/T systems, Ethernet Axia, and Serial Axia. Compatible with UR CB and E-Series.

## F/T URCap v2.7.8 Release Notes

- Combined URCap for E-series and CB compatibility into single URCap
- The options node requires a manual selection of the type of sensor if used. This is similar to the `Axia status bits` and `Net FT status bits` radio buttons on the previous versions. These new radio buttons are used for both the filter and the status code options.
- Invalid status codes on the sensor trigger a popup and pause the program.
   - The existing feature to set acceptable status code in the Options node will disable these behaviors for acceptable status codes
   - Status code changes will be logged even if set as acceptable. For status codes not set to acceptable, the messages will note that these are invalid status codes. Healthy or acceptable status codes will not state that it is an invalid status code.
- If the URCap runs into an error that causes the program to pause or stop, a popup is provided to call attention to this and state the source as F/T URCap.
- Certain sensor streaming commands require the Enable command to have been run prior in the program. These commands will stop the program and give a popup to state that the Enable command must be used if this condition is not met.
- Filter options match the associated selected sensor's available filter values. (previously the options did not match for NET Box sensor type)
- The Axia starts with the busy bit included in the acceptable status when using the options node. This is because using the options node will briefly cause this status code while the settings on the sensor are changed.
- Fixed several bugs that caused a `RTDE Fieldbus error` popup
- Reduced the amount of messages that are logged on the pendant dashboard.
- The `Disable` command now stops the sensor data stream
- The default logging level is `Info` on the Options node
- The default baud rate for serial communication is `115200`
- If an error occurs during sensor setup in the `Enable` command, there will be a popup stating that the error occurred during setup. If an error occurs while streaming, there will be a popup that states that an error occurred while streaming.
- The mounting options section of the F/T Sensor page on the Installation tab has been updated with a new summary and defaults most options to 0.
- UR has deprecated the command enable_external_ft_sensor(enable, sensor_mass = 0.0, sensor_measuring_offset = [0.0, 0.0, 0.0], sensor_cog = [0.0, 0.0, 0.0]) and added ft_rtde_input_enable() in its place. The URCap now defaults to the new method but as this is not backwards compatible with old Polyscope versions, the URCap checks the Polyscope version being used to determine what method should be called. The change in method use is implemented in Polyscope in E-series [5.9](https://www.universal-robots.com/articles/ur/release-notes/release-note-software-version-59xx/) and CB [3.14](https://www.universal-robots.com/articles/ur/release-notes/release-note-software-version-314xx/) versions.

