


### Visualization Analysis of Learning Attention Based on Single-image PnP Head Pose Estimation

![Focus.jpeg](https://upload-images.jianshu.io/upload_images/5786775-e326541fdfc61552.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![Not Fucus.jpeg](https://upload-images.jianshu.io/upload_images/5786775-5482d6a4f4065c35.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# Introduction

Learning attention analysis of students is the important indicator of classroom teaching/learning quantitative evaluation. Owing to the fact that the head-mounted eye tracker is expensive and unsuitable to be widely used in the large-scale classroom evaluation under expenditure limitation, in this paper, we uses the PnP(Perspective-nPoint) method to estimate student's head pose for single-image. And then we achieve visualization of learning attention. Experiments demonstrate the following advantages of our method. (1) The method limits the average head-pose estimation errors under 4.88° with Biwi database. (2) This work has implemented student learning attention visualization analyses for three typical learning cases including engagement, attention, and disregard.


# Method

Based on the above discussion, this paper proposes a method for visualization analysis of learning attention based on Single-image and develops a corresponding system. The method has 6 steps sequentially.

1. Video frames acquisition. With the help of LifeCam camera, we acquire classroom teaching videos and extract out of all frames.

2. （张氏标定法）Calibration of camera parameters. To improve the head pose recognition accuracy, we use a convenient and accurate method in paper [5] to calibrate camera parameters.

3. Face detection. Us face from each video frame.the face detection algorithm invented by Professor Yu Shiqi to detect

4. Facial feature point detection. With the Stochastic cascade regression tree , we can get the coordinate information of 19 facial feature points, which is used to provide 2D information of each frame image. algorithm

5. Head pose estimation. Using a standard facial statistical measurement model, we can get 3D coordinate information of each frame image, and then we can get the rotation and translation matrices, which mean the mapping relation between 2D and 3D models.

6. Students' sight location. With the use of the information of rotation and translation matrices, and spatial coordinate conversion, we can project the gaze point on the frame image of the teaching video.



### Visualization Analysis of Learning Attention Based on Single-image PnP Head Pose Estimation

![Focus.jpeg](https://upload-images.jianshu.io/upload_images/5786775-e326541fdfc61552.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![Not Fucus.jpeg](https://upload-images.jianshu.io/upload_images/5786775-5482d6a4f4065c35.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# Introduction

Learning attention analysis of students is the important indicator of classroom teaching/learning quantitative evaluation. Owing to the fact that the head-mounted eye tracker is expensive and unsuitable to be widely used in the large-scale classroom evaluation under expenditure limitation, in this paper, we uses the PnP(Perspective-nPoint) method to estimate student's head pose for single-image. And then we achieve visualization of learning attention. Experiments demonstrate the following advantages of our method. (1) The method limits the average head-pose estimation errors under 4.88° with Biwi database. (2) This work has implemented student learning attention visualization analyses for three typical learning cases including engagement, attention, and disregard.


# Method

Based on the above discussion, this paper proposes a method for visualization analysis of learning attention based on Single-image and develops a corresponding system. The method has 6 steps sequentially.

1. Video frames acquisition. With the help of LifeCam camera, we acquire classroom teaching videos and extract out of all frames.

2. （张氏标定法）Calibration of camera parameters. To improve the head pose recognition accuracy, we use a convenient and accurate method in paper [5] to calibrate camera parameters.

3. Face detection. Us face from each video frame.the face detection algorithm invented by Professor Yu Shiqi to detect

4. Facial feature point detection. With the Stochastic cascade regression tree , we can get the coordinate information of 19 facial feature points, which is used to provide 2D information of each frame image. algorithm

5. Head pose estimation. Using a standard facial statistical measurement model, we can get 3D coordinate information of each frame image, and then we can get the rotation and translation matrices, which mean the mapping relation between 2D and 3D models.

6. Students' sight location. With the use of the information of rotation and translation matrices, and spatial coordinate conversion, we can project the gaze point on the frame image of the teaching video.


# Detail

![image.png](https://upload-images.jianshu.io/upload_images/5786775-ffb37402ed5981e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Simplify Sight Location 
Because the project only have one camera, It's not easy to locate a precise sight location. So, based on pictrue I presented above, I regard a student is focus on the blackboard when the yaw is in (-30.0, 30.0).

#### Quantization

To make the evaluation Quantization, I extract head pose eatimation's Information and Lip change Angle, use the formula to calculate the score which is used to evaluate student's attention.

```python
    Score = 0.8 * math.cos(yaw * math.pi / 180.0 ) + 0.2 * math.sin(LipAngle * math.pi / 180.0)
```


What's more, I quantify the Student's Attention into a range([0,1]) which help to analyse the student's attention states dynamicly.


 
 
 

# Detail

![image.png](https://upload-images.jianshu.io/upload_images/5786775-ffb37402ed5981e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Simplify Sight Location 
Because the project only have one camera, It's not easy to locate a precise sight location. So, based on pictrue I presented above, I regard a student is focus on the blackboard when the yaw is in (-30.0, 30.0).

#### Quantization

To make the evaluation Quantization, I extract head pose eatimation's Information and Lip change Angle, use the formula to calculate the score which is used to evaluate student's attention.

```python
    Score = 0.8 * math.cos(yaw * math.pi / 180.0 ) + 0.2 * math.sin(LipAngle * math.pi / 180.0)
```


What's more, I quantify the Student's Attention into a range([0,1]) which help to analyse the student's attention states dynamicly.


 
 
 