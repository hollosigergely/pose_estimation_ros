# Pose Estimation for ROS 2

Pose estimation for a predefined CAD model in depth image. The CAD model shall be provided in standard PCD format.

## Docker
Build docker image:
```
docker build -t pose_estimation .
```

Run image using GPU as
```
docker run --rm -ti --gpus all -v <assets>:/asset --network host pose_estimation
```

The `<assets>` directory shall contain the `config.yaml` (see example) and the point cloud asset in PCD format.

## Topics

Subscriptions:
 - `/camera/color/image_raw`
 - `/camera/aligned_depth_to_color/image_raw`
 - `/camera/aligned_depth_to_color/camera_info`

Publishers:
 - `/pose_estimation/diag/image`: image for diagnostics (`sensor_msgs/Image`)
 - `/pose_estimation/diag/points`: point cloud for diagnostics (`sensor_msgs/PointCloud2`)
 - `/pose_estimation/pose`: pose in user defined format, object2camera transformation (see `src/pe_interface`)
