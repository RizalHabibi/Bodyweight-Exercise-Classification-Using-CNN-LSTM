## Feature Extraction

Feature extraction was performed using MediaPipe Pose on each frame of the input video. 
The process converts video frames into numerical representations of human body pose in 
the form of body landmark coordinates. This representation allows the system to focus 
on body structure and movement while reducing the influence of background, clothing, 
and lighting variations.

### 1. MediaPipe Pose Extraction

MediaPipe Pose detects 33 body landmarks, with each landmark represented by three-dimensional 
coordinates `(x, y, z)`, resulting in 99 features per frame.

For this project, a selection of key landmarks was retained, including the shoulders, 
elbows, wrists, hips, knees, and ankles. This reduces the dimensionality of the pose 
representation while preserving important information related to body movement.

<img width="2209" height="514" alt="CNN-LSTM" src="https://github.com/user-attachments/assets/cc25f60a-fc59-41f6-b2fb-73f478d1c363" />

**Process:**

`Video Frame → MediaPipe Pose → 33 Body Landmarks → Selected Landmarks`

The selected landmarks form the basis for the subsequent spatial feature engineering process.

---

### 2. Spatial Feature Engineering

To provide a more informative representation of body posture, additional geometric 
features were derived from the selected landmarks. Nine geometric features were added 
to the landmark coordinates, including joint and hip angles, horizontal ankle distance, 
trunk angle, knee symmetry, and body proportion ratio.

This process produces a total of **45 spatial features per frame**.

<img width="243" height="527" alt="CNN-LSTM (1)" src="https://github.com/user-attachments/assets/a413be84-a37b-45ce-b5d0-4f0e6136b607" />


**Process:**

`Selected Landmarks → Geometric Relationships → 45 Spatial Features`

The additional geometric features represent relationships between body segments that 
cannot be directly captured by individual landmark coordinates. For example, knee 
angles can help distinguish different phases of movements such as squats and lunges, 
while trunk angle can provide information about body orientation during exercises such 
as push-ups, sit-ups, jumping jacks, and squats.

---

### 3. Temporal Feature Engineering

In addition to spatial information, temporal features were extracted to represent how 
the body changes between consecutive frames. Velocity and acceleration were calculated 
from the spatial features to capture movement dynamics.

<img width="2434" height="1834" alt="Grafik_Kinematika_SpatioTemporal" src="https://github.com/user-attachments/assets/3d2c93d6-7578-4de5-928f-ceaa5915bbb0" />

**Process:**

`Spatial Features → Velocity → Acceleration`

Position represents the body's spatial configuration at a given frame. Velocity represents 
the rate and direction of change, while acceleration captures changes in velocity and 
movement transitions.

In the context of Human Activity Recognition (HAR), these features provide complementary 
information:

- **Position:** represents body posture and spatial configuration.
- **Velocity:** represents movement direction and tempo.
- **Acceleration:** represents changes in movement and transitions between movement phases.

The combination of spatial and temporal features enables the system to represent not only 
the body's configuration at each frame, but also how that configuration changes throughout 
the activity.

### Final Feature Representation

The final feature representation consists of **135 features per frame**:

| Feature Type | Number of Features |
|---|---:|
| Spatial Features | 45 |
| Velocity Features | 45 |
| Acceleration Features | 45 |
| **Total** | **135** |

This representation provides richer spatial and temporal information than using landmark 
coordinates alone and serves as the input representation for the subsequent classification 
