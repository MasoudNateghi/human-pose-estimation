# human-pose-estimation
In this repository, a CNN-based Deep Neural Network, capable of detecting human joints from a picture, is implemented. 
# Human-Pose-estimation
In this repository, a CNN-based Deep Neural Network, capable of detecting human joints from a picture, is implemented.
## Preprocessing the data 
To prepare the data, after loading them with the original size, we first find the length and width of each and store the original image and the inverse of its length and width, which are used as a scale in a vector. Then multiply the coordinates of the joints in these scales and then subtract 0.5 to determine their normalized coordinates. We have assumed that the center of the box is in the middle of the image. Then we resize the images to 220 x 220 dimensions, which are the input data of the network. For data preprocessing, divide 220 x 220 images by 255, and We subtract half so that the pixel values are between -0.5 and +0.5. We transform the normalized location of 14 joints from 2 x 14 to a 28 vector. In this way, our data is prepared.

## Procedure
In this problem, we are dealing with 14 joints. PCP metric is defined according to body organs. For this reason, we have chosen 10 body parts for this task, and you can see their list and joints with their numbers below:
### Joints 
-  00 Right ankle 
-  01 Right knee 
-  02 Right hip 
- 03 Left hip 
- 04 Left knee 
- 05 Left ankle 
- 06 Right wrist
- 07 Right elbow 
- 08 Right shoulder 
- 09 Left shoulder 
- 10 Left elbow 
- 11 Left wrist 
- 12 Neck
- 13 Head top
### Limbs
- 00 Right Lower Leg: between joints 0 & 1  
- 01 Right Upper Leg: between joints 1 & 2  
- 02 Left Upper Leg: between joints 3 & 4  
- 03 Left Lower Leg: between joints 4 & 5  
- 04 Right Lower Arm: between joints 6 & 7  
- 05 Right Upper Arm: between joints 7 & 8  
- 06 Left Upper Arm: between joints 9 & 10 
- 07 Left Lower Arm: between joints 10 & 11  
- 08 Head: between joints 12 & 13 
- 09 Torso: between joints mean of 2 & 3 and mean of 8 & 9
## Metrics
### PCP : 
The PCP criterion means organ detection rate. We say that an organ is diagnosed when the distance between the two joints of its two ends from the main location of the joints is less than half the length of the organ. In this project, we have chosen the detection condition in such a way that both corresponding joints are less than half the length of the limb from their exact location. As mentioned in the article, the problem with this criterion is that if the length of the limb is small, the probability of the limb being detected is high.
### PDJ :
The PDJ criterion is determined for each joint. First, the length of the torso, which is almost the largest organ among these 10 organs, is calculated, and if the error distance of each joint is less than a percentage of this length, this joint is recognized as detected.
