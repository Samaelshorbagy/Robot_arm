# Robot_arm
#Sama Elshorbagy  1190582
#Mona Mohsen  1190540
#Ahmed Osama  1190415
Robotic Arm Modelling:
Our model consists of a robotic arm that has a shoulder,elbow,fingers,and phalanges.
We have 4 fingers with each finger consists of 2 phalanges.Each body part is modeled as a cube.
We used basic graphic operations to produce the model like PushMatrix,PopMatrix,Translate,Rotate,Scale.
Also,we assigned different dimensions to each operation in order to control the arm movements with the keyboard with movement limitation 
to make the model look realistic as much as possible.
We had some challenges in assigning the parameters to the cases that are responsible for controling the robotic arm.

![image](https://user-images.githubusercontent.com/101284922/158034151-cf1a759a-4175-45b6-80ad-20edebdc5504.png)
![image](https://user-images.githubusercontent.com/101284922/158034205-a04298bf-366b-46b4-a5a8-ba7dd0fb5930.png)
![image](https://user-images.githubusercontent.com/101284922/158034217-ab11dd9c-edd1-46d1-b7d8-3a83c4053712.png)
![image](https://user-images.githubusercontent.com/101284922/158034228-c8abc75d-e7a2-4f24-9461-d7f356b50004.png)
![image](https://user-images.githubusercontent.com/101284922/158034235-e041e1a8-9d7e-4e2e-bb3a-de6a76af2e5a.png)
![image](https://user-images.githubusercontent.com/101284922/158034248-c1d85a8f-6b90-41a7-b41d-9b136b6a199a.png)
![image](https://user-images.githubusercontent.com/101284922/158034254-1b1ff211-66a2-4438-8735-0d9f91696091.png)


First,movement of elbows were 360 degrees.We managed to make the elbow flexion to be realistic using:
       elbow = (elbow + 5) % 120; 
while we controled the elbow extension using a condition which is: if (elbow > 0)
       {
           elbow = (elbow - 5) % 360;
           glutPostRedisplay();
           break;
       }.
       
Similarly,fingers were moving 360 degrees.Concerning the closing of fingers, we find that the most realistic solution is:      
        fingerBase = (fingerBase + 5) % 90; 
        
The same applies to opening the finger yet there is a condition:
        if ( fingerBase>0) before the command in order to manage our axes coordinates for the suitable movement.
        
Similarly, we wrote the command related to the phalanges in each finger produce suitable However,upper fingers and lower fingers were moving in the same direction 
which is not realstic for a robotic arm that is designed to hold objects and items.In this way, it will not do its job.We fixed this using command:  
      glRotatef((GLfloat)fingerUp, 0.0, 0.0, -1.0); for the upper fingers.
      
Hence, the rotaion of the fingers will move the other way so that upper fingers and lower fingers close on each other properly.
The most challenge we had was regarding the fingers of the arm,actually we found out that they were moving alone in space and far from our axes(robotic hand).
Hence,we placed two of the most imprtant commands in the openGL that solved for us the problem totally.

     The commands were PushMatrix() and PopMatrix().
     
