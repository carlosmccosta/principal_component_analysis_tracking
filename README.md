# principal_component_analysis_tracking

Configuration for the [drl](https://github.com/carlosmccosta/dynamic_robot_localization) perception pipeline for performing 6 DoF tracking of an object within a [Region of Interest (ROI)](yaml/filters_roi.yaml) using Principal Component Analysis (PCA).
Check the documentation of the [dynamic_robot_localization](https://github.com/carlosmccosta/dynamic_robot_localization) package for customizing the perception pipeline for your specific use case.


## Usage

For starting all the main launch files:
```
roslaunch principal_component_analysis_tracking bringup.launch
```


Start 3D sensor driver with its extrinsic calibration:
```
roslaunch principal_component_analysis_tracking intel_realsense.launch
roslaunch principal_component_analysis_tracking intel_realsense_dynamic_reconfigure.launch
roslaunch principal_component_analysis_tracking tfs.launch
```


Start PCA tracking:
```
roslaunch principal_component_analysis_tracking principal_component_analysis_tracking.launch
```


For monitoring the tracking state, run:
```
roslaunch principal_component_analysis_tracking rviz.launch
```


## Calibration of coordinate system

Start the [charuco_detector](https://github.com/carlosmccosta/charuco_detector):
```
roslaunch principal_component_analysis_tracking charuco_detector.launch
```

Adjust the tf publisher in [launch/tfs.launch](launch/tfs.launch) with the updated coordinate system given in:
```
rostopic echo /camera/color/image_raw_charuco_pose
```
