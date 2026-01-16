# Working with Prims

## Get the World Space Transforms for a Prim: 
[Documentation](https://docs.omniverse.nvidia.com/dev-guide/latest/programmer_ref/usd/transforms/get-world-transforms.html)


## Cameras

### coordinate system 
[USD Geom Camera](https://openusd.org/dev/api/class_usd_geom_camera.html)
Cameras in USD are always "Y up", regardless of the stage's orientation (i.e. UsdGeomGetStageUpAxis()). 'camXform' positions the camera in the world, and the inverse transforms the world such that the camera is at the origin, looking down the -Z axis, with +Y as the up axis, and +X pointing to the right. This describes a right handed coordinate system.

### target point 

