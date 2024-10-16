# model-running-using-observation-data
This project focuses on model calibration, adjusting parameters of a theoretical model using real-world data. By minimizing discrepancies between predictions and observations, the goal is to enhance the model’s accuracy and applicability, offering insights into the underlying system.

# Model Calibration Project

## Objective

This project aims to demonstrate the principles of model calibration, where parameters of a theoretical model are adjusted using real-world data. By minimizing the differences between model predictions and actual observations, the goal is to improve the accuracy and reliability of the model, making it more representative of real-world behavior.

## Methodology

1. **Data Collection**: 
   - In this example, the dataset used for calibration consists of *fictitious data* generated specifically for demonstrating the model recalibration process. 
   - These synthetic data points simulate real-world observations and are used to adjust the model parameters. In real applications, such data would be collected through experiments or measurements.

2. **Initial Model**: The starting point is a theoretical model with one or more parameters that influence its predictions. In many cases, these parameters are estimated from known constants or assumptions about the system.

3. **Calibration Process**:

   In this project, we employed multiple methods to calibrate the parameter `g`, each with its own advantages and applications. The following sections will describe these methods in detail.

   ## Method 1: Parameter Calibration Using Optimization

In this approach, we use an optimization algorithm to calibrate the parameter `g` of the model. The goal is to adjust `g` so that the model predictions closely match the observed data. This is done by minimizing the difference between the predicted and observed values using the **least squares** method.

### Overview of the Process

1. **Model Definition**: The model describes the theoretical relationship between the input variable (height `h`) and the output (fall time `t`). The model equation is:
   
   $$
   t = \sqrt{\frac{2h}{g}}
   $$

   where `t` is the time of free fall, `h` is the height, and `g` is the gravitational constant to be calibrated.

2. **Residuals Calculation**: The residuals are the differences between the observed times of fall (`t_mes`) and the predicted times based on the model. These residuals are normalized by the standard deviation of the observations (`sigOBS`) to account for uncertainty in the data.

3. **Least Squares Optimization**: 
   We use the **least squares** optimization method from the `scipy.optimize` library. The algorithm adjusts `g` to minimize the sum of squared residuals, effectively finding the value of `g` that best fits the observed data.


5. ## Method 2: Parameter Calibration Using Automatic Differentiation and Non-linear Optimization

In this second approach, we leverage **automatic differentiation** and non-linear optimization techniques to calibrate the parameter `β`. This method allows us to compute gradients and Hessians more efficiently, which can improve the optimization process. Notably, this method also incorporates the standard deviation of the observations, `sigOBS`, to better account for the uncertainty in the observed data.

### Overview of the Process

1. **Model Definition**: As before, the model relates the height `h` to the time of fall `t` using the equation:

   $`
   t = \sqrt{\frac{2h}{\beta}}
   `$

   Here, `β` is the parameter to be calibrated.

2. **Residuals Calculation**: Similar to the first method, we compute the residuals as the difference between the observed times (`t_mes`) and the predicted times from the model. The residuals are normalized by the standard deviation of the observations (`sigOBS`), allowing us to account for the uncertainty in the measurements.

3. **Non-linear Optimization**: We use the **least squares** optimization method again, but this time we calculate the Jacobian using automatic differentiation. This allows for more accurate gradient estimates, which can enhance the convergence of the optimization algorithm.

4. **Hessian Calculation**: We compute the Hessian matrix numerically to understand the curvature of the cost function around the estimated parameter. This is useful for assessing the confidence of the parameter estimates.
