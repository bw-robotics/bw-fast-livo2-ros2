# bw-fast-livo2-ros2

FAST-LIVO2 ROS2 Humble package with vendored build dependencies for nested colcon workspaces.

Fork lineage: [v4rl-ucy/FAST-LIVO2-ROS2](https://github.com/v4rl-ucy/FAST-LIVO2-ROS2) → [bw-robotics/bw-fast-livo2-ros2](https://github.com/bw-robotics/bw-fast-livo2-ros2).

## Repository layout

| Path | ROS package | Role |
|------|-------------|------|
| `FAST-LIVO2/` | `fast_livo` | FAST-LIVO2 mapping node and upstream launch/configs |
| `rpg_vikit/` | `vikit_common`, `vikit_ros` | Camera math (build dependency) |
| `livox_ros_driver2/` | `livox_ros_driver2` | Livox message types (compile-time only for Ouster setups) |
| `Livox-SDK2/` | — | Built and installed to workspace `install/livox_sdk2` |

**Note:** Vendored dependencies are bundled here temporarily. They may be split into separate repositories in a future refactor.

## Cramim integration

Vehicle-specific launch, calibration loading, and bag-replay helpers live in the Cramim repo package `cramim_fast_livo`, not in this repository.

## Build (standalone or nested workspace)

Build order for a colcon workspace:

```bash
# 1. Install Livox-SDK2 and Sophus into workspace install/ (see cramim_fast_livo build script)
# 2. Build packages:
colcon build --symlink-install --paths \
  rpg_vikit/vikit_common \
  rpg_vikit/vikit_ros \
  livox_ros_driver2 \
  FAST-LIVO2
```

See `FAST-LIVO2/README.md` for upstream dataset launch examples.

## License

GPL-2.0 — see `FAST-LIVO2/LICENSE`.
