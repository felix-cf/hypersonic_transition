# Machine Learning for Hypersonic Laminar-to-Turbulant Prediction

This project was sponsered by the AEROS program of the University of Maryland Aerospace Engineering Department. It was done with the help of Dr. Christoph Brehm and Sean Dungan. 

Based off of a similar machine learning model used in Paredese et al., our research focused on using deep neural networks to predict amplification factors and growth rates of disturbances in a hypersonic boundary layer. We used the numerical solutions from LASTRAC to generate ground truth data, as well as boundary layer profiles to test our prediction tool. The solutions assume quasi-parallel linear stability theory, so only streamwise growth rates are calculated. The model may be trained on both first-mode instability waves (known as Tollmien–Schlichting waves) and second-mode instability waves (known as Mack modes).  

The model takes in an input boundary layer, sampling its density and streamwise velocity at 60 equidistant points, along with a wall-temperature to edge-temperature ratio, Reynolds number, temporal wave number, and Mach number. The corresponding length scale used is boundary layer thickness to maintain invariance to the streamwise location of the flow. It then outputs a growth-rate, which can be used to calculate amplification factors throughout the flow. 

The machine learning model uses a convolutional network to interpret the input boundary layer, and a fully connected neural network to interpret the other paremeters as well as the output from the network ran on the input boundary layer. To test the efficacy of this model, we used a data-starving technique known as "benign overfitting" to test whether the model used can in fact capture the complicated theory involved in otherwise numerically solving the Navier-Stokes equations with LASTRAC. With only 15k datapoints per mode, the model performs quite well: it is able to interpolate between Mach numbers, provide fine resolution where data is sparse, and extrapolate into higher or lower Mach numbers well. 

The Powerpoint presentation shows the main results of the work. One can also view the source code in ml1.ipynb.
