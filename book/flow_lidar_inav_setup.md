<div style="text-align: center">
<!-- <img src=""> -->
<h1 style="border: none; font-size: 2.8em; margin-top: 0;" id="Optical flow">Optical flow and LIDAR-Lite</h1>
</div>

This page shows you how to set up the PX4Flow and a LIDAR-Lite for position estimation in the INAV position estimator. A short video demonstrating a position hold can be seen here: 
* [indoor](https://www.youtube.com/watch?v=MtmWYCEEmS8) 
* [outdoor](https://www.youtube.com/watch?v=4MEEeTQiWrQ)

<!--![](images/hardware/px4flow.png)-->
<img src="images/hardware/px4flow.png" style="width: 200px;"/>
<img src="images/hardware/lidarlite.png" style="width: 180px;"/>

## Hardware
The PX4Flow has to point towards the ground and can be connected using the I2C port on the pixhawk. <br />
For the connection of the LIDAR-Lite please refer to [this](https://pixhawk.org/peripherals/rangefinder?s[]=lidar) page. <br />
For best performance make sure the PX4Flow is attached at a good position and is not exposed to vibration. (preferably on the down side of the quad-rotor).
<img src="images/hardware/flow_lidar_attached.jpg" style="width: 500px;"/>

## Parameters
All the parameters can be changed in QGroundControl
* SENS_EN_LL40LS <br />
	Set to 1 to enable lidar-lite distance measurements
* INAV_LIDAR_EST <br />
	Set to 1 to enable altitude estimation based on distance measurements
* INAV_FLOW_DIST_X and INAV_FLOW_DIST_Y <br />
	These two values (in meters) are used for yaw compensation. <br />
	The offset has to be measured according to the following figure: <br />
	<img src="images/hardware/px4flow_offset.png" style="width: 250px;"/> <br />
	In the above example the offset of the PX4Flow (red dot) would have a negative X offset and a negative Y offset.
* INAV_LIDAR_OFF <br />
	Set a calibration offset for the lidar-lite in meters. The value will be added to the measured distance.


## Advanced
For advanced usage/development the following parameters can be changed as well. Do NOT change them if you do not know what you are doing!
* INAV_FLOW_W <br />
	Sets the weight for the flow estimation/update
* INAV_LIDAR_ERR <br />
	Sets the threshold for altitude estimation/update in meters. If the correction term is bigger than this value, it will not be used for the update.