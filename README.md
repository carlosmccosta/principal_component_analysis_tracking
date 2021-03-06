# principal_component_analysis_tracking

Configuration for the [drl](https://github.com/carlosmccosta/dynamic_robot_localization) perception pipeline for performing 6 DoF tracking of an object within a [Region of Interest (ROI)](yaml/filters_roi.yaml) using Principal Component Analysis (PCA).

This package was tested for tracking the top section of a box moving on top of a conveyor, as seen in the figure below.

Check the documentation of the [dynamic_robot_localization](https://github.com/carlosmccosta/dynamic_robot_localization) package for customizing the perception pipeline for your specific use case.

![RViz overview of the PCA tracking of the top section of a box on top of a conveyor](docs/box_on_conveyor.jpg "RViz overview of the PCA tracking of the top section of a box on top of a conveyor")


## Usage

For starting all the main launch files:
```
roslaunch principal_component_analysis_tracking bringup.launch
```


For starting each of the main launch files separately, first run the 3D sensor driver with its extrinsic calibration:
```
roslaunch principal_component_analysis_tracking intel_realsense.launch
roslaunch principal_component_analysis_tracking intel_realsense_dynamic_reconfigure.launch
roslaunch principal_component_analysis_tracking tfs.launch
```


Then, run the PCA tracking node:
```
roslaunch principal_component_analysis_tracking principal_component_analysis_tracking.launch
```


For monitoring the tracking state, run:
```
roslaunch principal_component_analysis_tracking rviz.launch
```


## Calibration of coordinate system associated with the ROI

The PCA tracking is performed within a calibrated workspace, in which a ROI is defined for segmenting the region in which the target object will be moving (box on top of a conveyor).
For recalibrating it, start the [charuco_detector](https://github.com/carlosmccosta/charuco_detector):
```
roslaunch principal_component_analysis_tracking charuco_detector.launch
```

Then, adjust the tf publisher in [launch/tfs.launch](launch/tfs.launch) with the updated coordinate system given by:
```
rostopic echo /camera/color/image_raw_charuco_pose
```
