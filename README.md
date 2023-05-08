Download Link: https://assignmentchef.com/product/solved-robotics-homework4-monte-carlo-localization-algorithm
<br>
The goal of homework 4 is to practice and implement what you have learned in the recent courses. In the following exercises, you will implement your own <strong>Monte Carlo Localization</strong> algorithm step by step and test on a real map visualized as following.

The overall algorithm is shown as below.

<h1>Exercise 0</h1>

Let’s take a look at what we have now. In the scripts folder, you will get:

<ol>

 <li>py : this file is the main program for the Monte Carlo Localization algorithm. By calling other functions you write in this homework, you will be able to help a robot localize itself. You should run this file after you finished implementing all the other modules. <strong>DO NOT MODIFY!!!</strong></li>

 <li>py : this file reads the map for you. <strong>DO NOT MODIFY!!!</strong></li>

 <li>py : this file is the motion model for the robot. You need to fill in the MotionModel.update function, which will be described in detail below.</li>

 <li>py : this file is for resampling particles. You need to fill in the</li>

</ol>

Resampling.low_variance_sampler function, which will be described in detail below.

<ol start="5">

 <li>py : this file is the sensor model for the robot. You need to fill in the</li>

</ol>

SensorModel.beam_range_finder_model function, which will be described in detail below.

You can add any other functions in the files for your convenience.

Then you need to install the dependencies. Python version 3.7 or 3.8 is recommended. It is recommended to use <em>conda</em> and virtual environment to configure the programming environment. Please run

to install the dependencies for this homework.

<h1>Exercise 1: Motion Model</h1>

You need to implement the MotionModel.update function. Please follow the notes below when implementing your algorithm.

<strong>NOTE1</strong>: This exercise asks you to implement the <strong>sample odometry motion model</strong>, which can be found in the slides.

<strong>NOTE2</strong>: <strong>DO NOT CHANGE THE SEQUENCE OF THE</strong> np.random <strong>TERM!!!</strong>. The sequence of the terms strongly correlates with our autotest program. Changing the sequence may affect the grading of this homework.

Here are the definitions of the variables you are going to be used in your implementation:

<ol>

 <li>u_t0 : input, vector  in the odometry motion model algorithm.</li>

 <li>u_t1 : input, vector  in the odometry motion model algorithm.</li>

 <li>x_t0 : input, vector  in the odometry motion model algorithm.</li>

 <li>x_t1 : output, vector  in the odometry motion model algorithm.</li>

 <li>del_rot1 : intermediate variable, in the odometry motion model algorithm.</li>

 <li>del_trans : intermediate variable,  in the odometry motion model algorithm.</li>

 <li>del_rot2 : intermediate variable, in the odometry motion model algorithm.</li>

 <li>del_rot1_h : intermediate variable,  in the odometry motion model algorithm.</li>

 <li>del_trans_h : intermediate variable,  in the odometry motion model algorithm.</li>

 <li>del_rot2_h : intermediate variable,  in the odometry motion model algorithm.</li>

 <li>alpha_1 , self.alpha_2 , self.alpha_3 , self.alpha_4 : hyper-parameters correlating with ,   ,               ,                in the odometry motion model algorithm.</li>

</ol>

<strong>Hint</strong>: Make sure that the output lies in .

<h1>Exercise 2: Resampling</h1>

You need to implement the Resampling.low_variance_sampler function. Please follow the notes below when implementing your algorithm.

<strong>NOTE1</strong>: This exercise asks you to implement the <strong>low variance sampling</strong> algorithm, which can be found in the slides.

<strong>NOTE2</strong>: For sampling , use the np.random.uniform function instead of other

random sampling libraries to pass the autotest. Not using the suggested function may affect the grading of your homework.

<strong>NOTE3</strong>: <strong>Strictly follow the low variance sampling algorithm</strong> in the slides or you might not pass the autotest program and might affect the grading.

Here are the definitions of the variables you are going to be used in your implementation:

<ol>

 <li>X_bar : input, the set  in the low variance sampling algorithm. In the implementation, X_bar is an        shaped array.</li>

 <li>X_bar_resampled : output, the set  in the low variance sampling algorithm. In the implementation, X_bar_resampled is an     shaped array.</li>

</ol>

<h1>Exercise 3: Sensor Model</h1>

You need to implement the SensorModel.beam_range_finder_model function. Please follow the notes below when implementing your algorithm.

<strong>NOTE1</strong>: This exercise asks you to implement the <strong>beam range finder model</strong>. The algorithm can be found in the slides.

<strong>NOTE2</strong>: The SensorModel.rayCast module is given. Please <strong>DO NOT MODIFY</strong> and do not implement your own ray cast algorithm even though the given one might be suboptimal.

<strong>NOTE3</strong>: The lidar is 25cm to the center of the agent, while the sensor data is centered at the location of the lidar. Therefore, in the sensor model, you need to calculate the coordinates of the laser based on the agent’s coordinates and orientations and then calculate the related weights.

Here are the definitions of the variables you are going to be used in your implementation:

<ol>

 <li>map : the map given by the main program. Please refer to instruct.txt for more information. <strong>DO NOT MODIFY</strong>.</li>

 <li>Z_MAX : the parameter for the four distributions.</li>

 <li>P_HIT_SIGMA : the  parameter for the Gaussian distribution</li>

 <li>P_SHORT_LAMBDA : the  parameter for the exponential distribution</li>

 <li>Z_PHIT , self.Z_PSHORT , self.PMAX , self.Z_PRAND : the weights , for the four distributions.</li>

 <li>z_t1_arr : laser range readings at time , correlates with  in the algorithm.</li>

 <li>x_t1 : particle state belief at time , correlates with  in the algorithm.</li>

 <li>q : probability of  at time , correlates with  in the algorithm.</li>

</ol>

<strong>Hint1</strong>: maybe you can use  to replace the original        for implementation convenience.

<strong>Hint2</strong>: when calculating the                    probabilities, make sure you filter out all the s.

<h1>Exercise 4: Run the entire program</h1>

After finishing all the modules required for the localization task, you need to run the program main.py to generate the final result. Here are the steps for finishing the whole homework.

<strong>Step 1</strong>: make sure that you are in the …/hw4/code/scripts directory before you run your entire program.

<strong>Step 2</strong>: set the save_flag to 1 and clear the <strong>CONTENTS</strong> of …/hw4/code/scripts/results directory if any exists. <strong>DO NOT DELETE THE DIRECTORY ITSELF!!!</strong>

<strong>Step 3</strong>: run python main.py . The main.py program will first read a series of data from

…/hw3/code/data/log/ . Then it will try to localize the robot using the modules you have implemented.

<strong>Step 4</strong>: after running main.py , there will be a number of photos generated into the

…/hw4/code/scripts/results folder. Run python make_video.py to generate video according to the photos generated. You can check the generated video with the given one to see if everything went right.

<strong>Tip1</strong>: there is a visualization of the sensor data in …/hw4/code/data/robotmovie1.gif , it might help you verify whether your implementation goes right.

<strong>Tip2</strong>: <strong>DO NOT MODIFY ANY SEED OR PARAMETER</strong>.