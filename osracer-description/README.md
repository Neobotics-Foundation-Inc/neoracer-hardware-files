# osracer robot description (URDF)

The NeoRacer's ROS 2 robot description: the URDF, its meshes, and the
`robot_state_publisher` launch files that broadcast the car's transform tree.
This is what tools like RViz, SLAM, and Nav2 read to know where each sensor
sits relative to the body and how the wheels move.

## Source

Vendored **as is** from the upstream [osrbot/osracer](https://github.com/osrbot/osracer)
repository (`osracer_description` package, `dev` branch), which is **MIT
licensed**. The upstream license is included here as `LICENSE`. Files are
unmodified from upstream.

## Contents

- `urdf/osracer.urdf` — the robot description (11 links: chassis, four wheels,
  two front steering hinges, and the camera, LiDAR, and IMU frames).
- `urdf/osracer.csv` — the exporter's joint/link table.
- `meshes/` — the visual + collision STL meshes (full-resolution CAD exports).
- `launch/` — `osracer_description.launch.py` (full `robot_state_publisher`)
  and `robot_description_tf.launch.py` (static-transform-only variant).
- `config/joint_names_osracer.yaml`, `CMakeLists.txt`, `package.xml`.

## Frames

The transform tree is `base_footprint → base_link → { laser, imu_link,
camera_link, steering hinges → front wheels, rear wheels }`. Note the LiDAR
frame is named `laser`, not `lidar_link`.

## Known upstream issue (left as is)

The URDF references `meshes/laser.STL`, but the package ships the mesh as
`meshes/laser_link.STL`. To load the LiDAR mesh, either rename the file or
fix the `package://` path in the URDF. This is preserved as it is upstream.
