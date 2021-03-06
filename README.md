# Predict-Posture-Standing-Sitting
Predict whether a person is standing or sitting.

**Code Reproduction**
The code can be reproduced using the same instructions as described here: https://github.com/asimniazi63/pose-detection

```
git clone https://github.com/hassaanmuzammil/Predict-Posture-Standing-Sitting.git
```
```
cd Predict-Posture-Standing-Sitting
```
```
pip install -r requirements.txt
```
```
python inference.py --path=input/example_standing.jpg --model=II --framework=tflite --visualize --store
```

**Introduction**

The task was to add a poster prediction function to the file that outputs x,y coordinates of body parts given an input image.
From the (x,y) coordinates of several body parts, I was required to predict the posture, specifically if the person is standing or sitting.
I considered the 3 major points of hips, knees, and ankles and found the angle formed by the line joining the ankle-knees and knees-hips. 
For this purpose the math library was used. The formula used was related to the dot product. Given three points A,B,C: AB.BC = |AB||BC|cos(ABC)

**Angle Criteria**

Odd Multiple of 90 >> (90,270) OR closer to it wrt a certain threshold: SITTING
Even Multiple of 90 >> (0,180,360) OR closer to it wrt a certain threshold: STANDING
Other Angles like (135,225): UNKNOWN POSTURE

**Changes Made**

Only two functions were added to the original code
1) get_angle - gets the angle formed from three points
2) get_posture - infers posture from a set of coordinates of body parts using the get_angle function

**Sample Output**
![image](https://user-images.githubusercontent.com/52124348/125157839-9fee6480-e186-11eb-8fb0-2fb8911be9dd.png)

**Comments**

The .ipynb file summarizes my work. The rest is just integrating my work into the main program

**References**

https://manivannan-ai.medium.com/find-the-angle-between-three-points-from-2d-using-python-348c513e2cd
