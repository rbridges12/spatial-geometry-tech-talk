# Pose Representations Tech Talk

## What is pose?
- the position and orientation of an object
- position is defined relative to some reference point
- orientation is defined relative to some reference frame
- visuals: coordinate axes, gifs of objects changing only position and only orientation

## What is a pose representation?
- mathematical/numerical way to define what an object's pose is
### what do we want from a pose representation?
- easy for humans to understand
- support common pose operations
    - composition
    - inversion
    - incrementing
    - conversion to other representations
    - extract components
- common operations are mathematically simple and easy to implement
- common operations are fast to compute and numerically stable
- requires minimal memory to store

## Why does this matter?
- pose representations are used in many applications
    - robotics
    - computer vision
    - augmented reality
    - computer graphics/rendering
    - physics simulations
    - video games
- visuals: images of each application

## 2D pose representations
- [x, y, theta]
    - Position: [x, y] vector
    - Orientation: angle
- [x, y, xdir, ydir] ?
    - Position: [x, y] vector
    - Orientation: [xdir, ydir] unit vector
- operations
- visuals: graph plot of each representation, using a racecar as an object

## 3D pose representations
- position: [x, y, z] vector
- orientation: ?
    - possible rotation around 3 orthogonal axes -> 3 degrees of freedom
    - not commutative (order matters)
    - this is where things get tricky (and confusing)
- visuals: 3D graph plot of object

## Euler angles
- 3 angles, each representing a rotation around a different axis
- often called roll (x axis), pitch (y axis), yaw (z axis)
- operations
- pros
    - easy to understand
- cons
    - many different conventions
    - smoothness
    - gimbal lock
- visuals: rpy visualization, visualizations of pitfalls

## Rotation Matrices
- 3x3 orthogonal matrix
- each column is a unit vector representing the direction of the x, y, and z axes of the rotated frame
- operations
- pros
    - fairly easy to understand
    - operations are simple and well known
- cons
    - requires more memory
    - requires more computation
- visuals: latex matrix

## Axis Angle/Rotation Vector
- 3D vector representing axis of rotation
- magnitude of vector represents angle of rotation
- also known as Rodrigues vector
- operations
- pros
    - fairly easy to understand
    - very compact
- cons
    - operations are more complicated
    - requires more computation?
- visuals: latex vector, axis angle visualization, rodrigues formula visualization?

## Quaternions
- normalized 4D vector
- operations
- pros
    - compact
    - operations are simple
- cons
    - very difficult to understand
    - requires frequent normalization to avoid numerical instability
    - duplicate representations of the same pose
- visuals: latex vector, quaternion visualization

## Aside: Matrix Groups
- these things are topological spaces, smooth manifolds, and matrix groups
- AKA Lie groups, manifolds
- position/translation: R2, R3
- orientation/rotation: SO(2), SO(3)
- pose: SE(2), SE(3)
- others: S1, S3
- Lie theory
- visuals: exp map?

## 3D pose representations, revisited
- Euler angles: [x, y, z], [roll, pitch, yaw]
- Homogenous transformation matrix: [R, t; 0, 1]
- Axis angle: [x, y, z], theta*[xhat, yhat, zhat]
- Quaternion: [x, y, z, w]

## Which representation should you use?
- depends on your application
- quaternions are standard, especially for performance
- if performance isn't important, rotation matrices are easy to use

## How to use them in practice?
- c++: Eigen, manif
- python: numpy, scipy, ROS tf.transformations

## References & Further Reading
- S. M. LaValle: Planning Algorithms Ch4

## Appendix: poses vs transformations

## Appendix: converting between representations

## Appendix: Lie theory