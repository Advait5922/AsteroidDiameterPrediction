# Asteroid Diameter Prediction

## Overview of Problem
1) An asteroid is a celestial body found in the inner Solar System, characterized by its metallic or rocky composition and the absence of an atmosphere. Asteroids exhibit diverse sizes and shapes, ranging from small bodies to dwarf planets, but they are distinct from actual planets. The majority of asteroids are situated within the asteroid belt, positioned between the orbits of Mars and Jupiter. Typically, they follow orbits with relatively low eccentricity, indicating orbits that are not highly elongated.

   Near-Earth asteroids (NEAs) constitute a subset of asteroids whose orbits bring them close to Earth's orbit. Those asteroids that intersect Earth's orbital path are termed Earth-crossers. As of April 2022, 28,772 near-Earth asteroids have been identified, with 878 having a diameter of one kilometer or larger. There is a growing interest in detecting asteroids with Earth-crossing orbits that, given sufficient time, could pose a collision threat to Earth.

   In the event of a rocky meteoroid impact larger than 25 meters but smaller than one kilometer, local damage to the impact area is anticipated. Objects surpassing one to two kilometers in diameter, however, have the potential for global consequences. Predicting the diameter of an asteroid is a complex task, and in this study, the aim is to forecast the diameter of asteroids. This information is crucial for making informed decisions and implementing proactive strategies to mitigate potential asteroid threats. Various deflection strategies exist, such as altering an asteroid's trajectory or inducing a controlled collision with a projectile from Earth, with the ultimate goal of preventing impact on Earth's surface.

2) I have taken the asteroid dataset from kaggle. It contains features of asteroid and will be helpful to predict diameter of asteroid

### Business objective and constraint
This task involves a regression problem where the objective is to maximize the R2 score or minimize the mean squared error in predicting the diameter of asteroids. There is no stringent requirement for real-time predictions, allowing for a timeframe of several minutes to forecast asteroid diameters accurately.
