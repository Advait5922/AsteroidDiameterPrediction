# Asteroid Diameter Prediction

## Introduction

Asteroids, small rocky objects orbiting the Sun in elliptical paths, are remnants from the early stages of our solar system's formation around 4.6 billion years ago. Often referred to as minor planets or planetoids, they vary in size from tiny specks to hundreds of kilometers across. Primarily situated in the asteroid belt between Mars and Jupiter, asteroids can also be found in other parts of the solar system.

Most asteroids exhibit irregular shapes, with only a few approaching a spherical form, often featuring pits or craters. When we discuss the diameter of irregularly shaped asteroids, we typically refer to their __equivalent diameter__. This represents the diameter of a sphere with the same volume as the asteroid, providing a convenient means to compare sizes. However, it's important to note that the equivalent diameter may not precisely reflect the asteroid's actual physical size or shape, occasionally overestimating or underestimating based on its density and form.

Two asteroid classes of particular interest to astronomers and planetary scientists are __NEAs__ (Near-Earth Asteroids) and __PHAs__ (Potentially Hazardous Asteroids). NEAs, coming close to Earth's orbit, have collision potential. PHAs, a subset of NEAs, pose a greater concern due to their proximity and potential for significant damage upon impact.

Diameter prediction holds immense significance, especially in identifying NEAs and PHAs. An asteroid's size influences its interaction with Earth, with smaller ones more likely to burn up in the atmosphere. Predicting diameters aids in assessing potential threats and devising strategies to mitigate harm. Additionally, diameter predictions offer insights into asteroid composition, structure, and evolution, contributing to a deeper understanding of the Solar System's origins.

## Overview of Problem
This project endeavors to estimate the sizes of asteroids within our solar system by leveraging various observable characteristics such as absolute magnitude, albedo, distance from the Sun, and orbital parameters. The precise prediction of asteroid sizes is paramount for comprehending their potential impact on Earth and strategizing future space missions dedicated to their study.

The initiative involves a comprehensive analysis of observational data provided by JPL’s Solar System Dynamics (SSD) group. Through this analysis, the aim is to construct models capable of predicting asteroid diameters based on observable features. Ultimately, the project seeks to advance our understanding of the asteroid population and its potential implications for our planet.

As someone deeply passionate about astronomy and intrigued by the insights data mining can offer, I eagerly anticipate the opportunity to engage in a project that allows me to explore captivating facets of my field of interest. This endeavor promises to provide hands-on experience with real astronomical data, enabling me to not only glean insights from textbooks but also to enhance my skills in meticulous data analysis and machine learning application, applying acquired knowledge to practical scenarios.

## SUMMARY

* Innovatively introduced an approximate diameter feature in the MLP(Multilayer Perceptron) model, resulting in an impressive 46.9% reduction in MSE and a significant 2.1% improvement in R2. This enhancement significantly elevated the accuracy and predictive power of the model.

* Showcased adeptness in constructing and fine-tuning diverse machine learning models, including MLP, CatBoost, and LightGBM. Applied advanced techniques such as scaling, one-hot encoding, grid search, and cross-validation to optimize model performance.

* Identified the MLP model as the top performer, achieving an outstanding MSE of 1.893 and an R2 score of 0.978 on the test set, surpassing other models in accuracy and reliability.

* Unearthed crucial patterns and correlations within a highly imbalanced dataset of 137,000 asteroid observations. This provided invaluable insights into understanding asteroid behavior, aiding assessments of potential impacts on Earth, and informing future space missions to study these celestial objects.

* Discovered key dataset characteristics, including a dominant class constituting 92% of asteroids, and pinpointed 7% with poorly determined orbits. This insight enables strategic decision-making for precise and reliable predictions.

* Enhanced data quality by identifying outliers and addressing missing values through appropriate methods such as imputation and removal.

* Constructed robust models crucial for accurate asteroid diameter predictions, facilitating the identification of potentially hazardous asteroids and enhancing classification models to distinguish between hazardous and non-hazardous asteroids.

## RESULTS

The project aimed to evaluate the performance of three models—MLP, CatBoost, and LGBM—in predicting asteroid diameters, using mean squared error (MSE) and R2 score as metrics.

While __all three__ models delivered __satisfactory results__ in predicting asteroid diameters, the MLP model emerged as the most accurate. Notably, the MLP model outperformed the others, achieving an impressive MSE of 1.893 and the highest R2 score of 0.978.

MSE scores for all models fell within the range of approximately 1.893 to 5.632, indicating a consistent average deviation of predicted diameters from actual diameters. This translated to a deviation within the range of 1.375 to 2.373 kilometers for different models. In terms of R2 scores, the models ranged from 0.933 to 0.978, signifying the percentage of variance in the target variable (diameters) explained by each model.

![](https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/test_results.png)

<a id="Project_At_A_Glance"></a>
## Project At A Glance

__Python Version__: 3.7.12

__Packages__: numpy, pandas, matplotlib, seaborn, sklearn, tensorflow, lightgbm, catboost.

<a id="prob"></a>

__The outline of the project looks like this:__

To initiate the project, my initial step involves delving into the dataset to uncover intriguing relationships among its features. In the "Exploring the Data" section, I will meticulously search for patterns and, when possible, provide explanations for the observed relationships.

Following the exploratory phase, the subsequent step focuses on preparing the data for the subsequent stages of diameter prediction model training. This involves essential tasks such as feature engineering, encoding categorical features, and scaling the data to ensure it is ready for modeling.

The primary emphasis then shifts towards the construction and fine-tuning of three distinct models: MLP neural network, CatBoost, and Light GBM. This iterative process involves exploring and optimizing each model to identify the most suitable one for our specific task—predicting asteroid diameter. Through a thorough comparative analysis of their performance metrics, I will make an informed decision regarding which model consistently produces the most accurate results.


<a id="EDA"></a>
## EDA
_Please note that if one is willing to see more of the takeaways from the EDA, then I suggest reading the whole notebook, which can be found either on [Github](https://github.com/Sofxley/asteroid-diameter-prediction/blob/main/asteroid_diameter_prediction.ipynb) or [Kaggle](https://www.kaggle.com/code/blulypsee/asteroid-diameter-prediction-mlp-catboost-lgbm)._

Here I present some of the highlights from the EDA. 	

<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/diameter_vs_class.png" width="600" align="right"/>
<img src="https://github.com/Sofxley/asteroid-diameter-prediction/blob/main/images/condition_code_distrib.png" width="600" align="right"/>

__Asteroid Classes, NEAs, PHAs__
* In the initial figure on the right, the majority of objects categorized as potentially hazardous are identified as Near-Earth Asteroids (NEAs) falling into classes AMO, APO, and ATE. These asteroids either intersect the Earth's orbit or closely approach it in their orbital paths. Notably, a prevalent characteristic among these potentially hazardous asteroids is their predominantly small diameters, ranging from 0.1 km to 1 km. Specifically, the median diameters for AMO, APO, and ATE are 0.56 km, 0.59 km, and 0.32 km, respectively.

* Further insights from additional plots, although not presented here, reveal a substantial imbalance between non-dangerous asteroids and potentially threatening ones. Despite the existence of 850 NEAs, only a small fraction among them is designated as potentially hazardous. This underscores the importance of distinguishing between these categories for a more accurate assessment of potential threats posed by Near-Earth Asteroids.

__Condition Code__
* The condition code spans from 0 to 9, where a code of 0 or 1 signifies a well-determined orbit. Codes 2-4 indicate a less certain orbit, while codes 5-9 signify a poorly determined orbit.

* In the lower plot on the right, a reassuring observation is the abundance of well-determined orbits across various classes. However, there are a few thousand asteroids with poorly determined orbits, primarily belonging to classes MBAs, OMBs, and IMBs. Notably, TNOs and CENs, characterized by large orbits, face challenges in accurate determination, leading to higher condition codes.

* Certain asteroid classes, like NEAs, garner substantial research interest, resulting in more observational data and lower condition codes for some subclasses (ATEs, AMOs, APOs). Despite these efforts, there are still NEAs, including APOs and AMOs, with uncertain orbits. This could be attributed to their small diameters, making them challenging to observe, compounded by their short orbital periods.

* In summary, no distinct correlation emerges between asteroid class and condition code; rather, the condition code appears to be contingent on the quantity of observations. Further exploration of this feature is detailed in the notebook.

<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/inclination_distrib.png" width="600" align="right"/>
<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/inclination_vs_eccentricity.png" width="600" align="right"/>

__Inclination & Eccentricity__
* In the upper plot on the right, the predominant eccentricities fall within the 0 to 25-degree range. Notably, most asteroids exhibit eccentricities between 0.05 to 0.2, coupled with inclinations around 2 to 7 degrees, or lower eccentricities below 0.15 with inclinations approximately around 10 degrees. This suggests a potential indication that the majority of asteroids in the dataset are Main Belt Asteroids (MBAs), known for their stable orbits. Additionally, within these inclination and eccentricity ranges, we find semi-major axes commonly associated with various asteroid classes such as MBAs, OMBs, IMBs, APOs, MCAs, AMOs, and ATEs.

* Consequently, the relationship between an asteroid's inclination and eccentricity serves as a valuable indicator of its class and overall orbital characteristics.

From the lower plots on the right, the following observations can be made:

* MBAs typically exhibit low eccentricities and inclinations, indicative of relatively stable orbits.
* MCAs commonly possess low inclinations but high eccentricities, potentially influenced by gravitational perturbations from Mars.
* NEAs, due to their proximity to or crossing of Earth's orbit, tend to have higher eccentricities and inclinations compared to MBAs. Specific NEA types, like ATEs, often display higher inclinations.
* TJNs, located around the Lagrange points of Jupiter's orbit, typically demonstrate low eccentricities and inclinations.
* CENs, orbiting between Jupiter and Neptune, often feature high inclinations and eccentricities, possibly originating from the Kuiper Belt and influenced by gravitational scattering from large planets like Neptune.
* TNOs exhibit a broad range of eccentricities and inclinations, with some displaying highly elliptical and inclined orbits, similar to CENs, due to gravitational interactions within the solar system.

<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/perihelion_vs_aphelion.png" width="600" align="left"/>
<img src="https://github.com/Sofxley/asteroid-diameter-prediction/blob/main/images/perihelion_vs_aphelion_zoom.png" width="600" align="left"/>

__Perihelion & Aphelion distances__
* The correlation between aphelion distance and perihelion distance varies among asteroids of different classes. Generally, asteroids with higher eccentricities tend to exhibit more significant differences between their aphelion and perihelion distances.

* NEAs, characterized by highly eccentric orbits, often showcase substantial differences between aphelion and perihelion distances. ATEs, confined entirely within Earth's orbit, typically have marginal differences between aphelion and perihelion distances. Conversely, APOs, crossing Earth's orbit, usually display much larger aphelion distances than perihelion distances. Similarly, for AMOs, whose orbits intersect Earth's orbit from the outside, aphelion distances can significantly exceed perihelion distances.

* IMBs and OMBs, with less eccentric orbits compared to NEAs and TNOs, generally exhibit more similar aphelion and perihelion distances.

* MBAs, known for their mostly circular orbits with eccentricities typically below 0.3, maintain relatively close aphelion and perihelion distances, indicating stable and predictable orbits.

* MCAs, whose orbits intersect Mars's orbit, have perihelion distances closer to the Sun than IMBs and OMBs. Their aphelion distances can vary significantly based on the specific asteroid's orbit.

* TJNs, benefiting from the stabilizing gravity of Jupiter, have relatively stable and less eccentric orbits, resulting in minimal differences between aphelion and perihelion distances.

* CENs and TNOs, characterized by highly elliptical orbits with eccentricities exceeding 0.3, exhibit substantial disparities between aphelion and perihelion distances. These orbits, marked by high eccentricities, contribute to chaotic and challenging predictability.

<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/aphelion_vs_semimajor.png" width="600" align="right"/>
<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/albedo_vs_diameter.png" width="600" align="right"/>


__Aphelion distance & Semi-major Axis__
* The semi-major axis of an asteroid defines the average distance between the asteroid and the sun, shaping the overall size and form of its elliptical orbit. The aphelion distance, marking the farthest point in the orbit from the sun, is intricately linked to the semi-major axis of the ellipse. Mathematically, the aphelion distance is expressed as $a(1+e)$, where $a$ represents the semi-major axis and $e$ denotes the eccentricity of the orbit.

* In essence, the relationship between the aphelion distance and the semi-major axis adheres to Kepler's laws of planetary motion, specifically delineating the elliptical orbit's shape and size. The upper plots on the right visually confirm and validate this fundamental astronomical principle.

__Absolute Magnitude & Albedo__
* Generally, smaller asteroids tend to exhibit higher absolute magnitudes, indicating darker surfaces, while larger asteroids typically have lower absolute magnitudes, signifying brighter surfaces. Albedo, the reflectivity of an object, also influences absolute magnitudes, with higher albedo corresponding to lower absolute magnitudes.

* The lower plots suggest that MBAs have a relatively uniform distribution of absolute magnitudes, centering around a mean value of approximately $H=13$. There's a discernible trend indicating that smaller asteroids within this class tend to have higher absolute magnitudes, while larger ones have lower absolute magnitudes. Notably, MBAs exhibit a correlation where brighter and larger asteroids tend to have lower albedos. Higher albedo values, typically around 14, are associated with greater reflectivity, but in the case of MBAs, those with $H > 14$ and $H < 14$ usually have albedos below 0.6. The trend suggests that as MBAs become brighter and larger, their albedo decreases.

* IMBs are distinguished by their high albedos, attributed to their composition of silicate rocks, which are inherently more reflective. Additionally, the process of space weathering contributes to their brighter surfaces by removing darker outer layers and revealing the brighter interior.

* OMBs and MCAs generally exhibit low albedos, aligning with the trend that lower absolute magnitudes correspond to larger sizes.

* NEAs showcase a tendency for higher albedos in brighter and larger asteroids. Despite their proximity to the Sun, NEAs generally have lower albedos compared to MBAs, and their albedos seldom exceed 0.6.

* TJNs demonstrate a correlation between absolute magnitude, diameter, and albedo. Brighter TJNs are generally larger and exhibit higher albedos.

* CENs follow a similar trend, with brighter CENs often being larger, though not necessarily exhibiting an increase in albedo. Most CENs have notably low albedos, and their distribution of absolute magnitudes centers around a mean value of approximately $H=10$.

* TNOs display a wide range of absolute magnitudes, with brighter TNOs generally being larger, although not necessarily less absorptive.

<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/moid.png" width="600" align="right"/>

__Minimum Orbit Intersection Distance (MOID)__
* NEAs tend to have smaller Minimum Orbit Intersection Distances (MOIDs) due to their proximity to Earth and the nature of their orbits intersecting with Earth's orbit.

* MBAs typically exhibit larger MOIDs since they possess more circular orbits and are situated at greater distances from Earth.

* Only NEAs meeting the criteria of $moid < 0.05$ and $H <= 22.0$ are typically classified as Potentially Hazardous Asteroids (PHAs). The right plot in our dataset confirms that all asteroids align with this criterion.

__Bivariate Distributions__
* The final figure illustrates the probability of two specific variables occurring together. Notably, a significant portion of asteroids exhibits inclinations below 15 degrees, and these occurrences are distributed across various values of the Longitude of Ascending Node (LAN) and Argument of Perihelion.

<img src="https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/bivariate_distributions.png" align="right"/>


<a id="ENG_PROC"></a>
## Feature Engineering and Data Preprocessing

In the feature engineering and data preprocessing phase, I implemented several techniques to refine the dataset for effective modeling and analysis. Initially, I introduced a new feature named `approx_diameter` through feature engineering, and its incorporation proved to be pivotal in enhancing the MLP model's performance significantly. This new feature, designed to approximate the diameter, played a critical role in improving the model's ability to capture intricate relationships between existing features and the target variable.

The MLP model benefited from the informative content embedded in the `approx_diameter` feature, uncovering hidden patterns or correlations that might not have been evident in the original features alone. Leveraging the MLP model's capability to discern complex relationships, the inclusion of `approx_diameter` led to superior predictions and heightened accuracy, positioning the MLP model as the top performer among others.

This underscores the importance of meticulous feature engineering in unraveling concealed insights within the data. The success of the MLP model, propelled by the introduction of `approx_diameter`, emphasizes how strategic feature creation can significantly contribute to model effectiveness.

Additionally, I addressed categorical features by employing one-hot encoding, transforming them into a binary format for better processing by the models. This encoding strategy facilitated the integration of categorical information into the modeling process.

To ensure unbiased model evaluation, I meticulously partitioned the dataset into training, validation, and test sets. The training set facilitated model training, the validation set aided in hyperparameter tuning and model selection, while the independent test set provided a robust evaluation of final model performance.

Furthermore, I applied data scaling techniques, specifically standardization, to normalize numerical features and ensure uniformity in scale across all features. This precautionary step prevented any individual feature from dominating the model's learning process.

In summary, through careful feature engineering, effective encoding of categorical features, strategic data splitting, and appropriate data scaling, I aimed to craft a dataset optimized for modeling and analysis. These steps were imperative in refining the data, enabling models to discern patterns effectively and make accurate predictions.

<a id="models"></a>
## Building and Fine-Tuning the Models

![](https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/test_results.png)

In this section, I conducted training and comparative analysis on three distinct models: MLP, CatBoost, and LightGBM. The models underwent training on both the complete dataset and a reduced dataset excluding the `approx_diameter` feature. Subsequently, fine-tuning was implemented to enhance their performance using the validation set, with evaluation metrics such as MSE and R2 score employed to assess model efficacy.

Initial training on the entire dataset revealed that the CatBoost model, especially when incorporating the `approx_diameter` feature, exhibited slightly superior performance. The MLP model also demonstrated competitive results. Surprisingly, when trained on the reduced dataset without the `approx_diameter` feature, the CatBoost model maintained strong performance, surpassing other results. This indicates the model's capacity to discern crucial patterns and relationships within the dataset, whether or not the engineered feature was present.

Further optimization efforts through hyperparameter fine-tuning yielded improved results for all models, particularly notable in the LightGBM model. The fine-tuned models demonstrated reduced MSE and elevated R2 scores, signifying enhanced accuracy and predictive capabilities.

In summary, the model comparison underscored the impact of feature engineering and fine-tuning in elevating overall model performance. The MLP model underscored the significance of the `approx_diameter` feature, significantly enhancing its predictive capabilities on the test set. Meanwhile, the robust performance of CatBoost and LightGBM on both entire and reduced validation datasets showcased their adaptability and ability to discern patterns in unseen data. Despite CatBoost leading on the validation set, the MLP model emerged as the top-performing model on the test set, affirming its superior predictive prowess.

![](https://raw.githubusercontent.com/Sofxley/asteroid-diameter-prediction/main/images/test_set_preds_MLP.png)
