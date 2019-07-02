# principal_component_analysis_tracking

6 DoF tracking using Principal Component Analysis (PCA).


## Usage

Start 3D sensor and its calibration:
```
roslaunch principal_component_analysis_tracking intel_realsense.launch
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

Start the charuco_detector:
```
roslaunch principal_component_analysis_tracking charuco_detector.launch
```

Adjust the tf publisher in [launch/tfs.launch](launch/tfs.launch) with the updated coordinate system given in:
```
rostopic echo /camera/color/image_raw_charuco_pose
```
