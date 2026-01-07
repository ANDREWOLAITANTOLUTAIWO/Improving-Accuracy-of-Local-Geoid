INTRODUCTION

Local geoid models are determined in order to convert ellipsoidal heights to orthometric heights and interpolate orthometric heights to points of known position.  The reference surface for orthometric height is the mean sea level or surface of the ocean when it is calm. That ideal ocean surface is called the geoid.  The height H measured above the geoid along the “vertical” is called orthometric height. Orthometric height is extended to points on the physical earth surface through the process of spirit leveling. Ellipsoidal height, h is related to the reference ellipsoid. It has no physical meaning since it is not based on any physical entity. The usefulness of ellipsoidal height is limited to GPS operations. Since the use of GPS is pervasive in modern times, converting ellipsoidal height to orthometric height has become a necessity. The difference between the two heights is called geoid height, N.  H, h and N are related by equation (1): 

N=H+h 											(1)

The ellipsoid is easily modelled through GPS measurements at any point on the earth surface. The geoid is not easily modelled. This is because height differences based on mean sea level (or the geoid surface) need to be extended from points of known orthometric heights through spirit levelling, a task which is very tedious, time consuming, labour-intensive, expensive, and difficult to carry through inaccessible remote areas. 

Thus, researchers have proposed various polynomials to model the local geoid surface, through which orthometric heights at some known points can be interpolated to other known points (Nwilo et al., 2009; Odumosu et al., 2016; Erol, 2011, Oluyori et al., 2020). The development of local geoid models aims basically at providing GPS users with an optimal transformation model between ellipsoidal heights and orthometric heights with respect to a given levelling datum. 
The geoid model is a mathematical function fitted to existing geoid heights to enable geoid heights of new points to be determined using variables such as geographic or rectangular coordinates of the points (Eteje et al., 2018). Researchers have worked with various surfaces such as plane surface, bi-linear surface, second degree polynomial, third degree polynomial and quintic fifth degree polynomial. The surface to be adopted as well as the degree and order of the polynomial depends on the size of the study area and the variation of the geoid heights. For a small area, the plane surface is found appropriate, while for a relatively large area, the second and third order polynomial surfaces are used (Nwilo et al., 2009; Olaleye et. al., 2013; Odumosu et al., 2016).

GEOID MODELING 

Polynomial of degree n that can model the local geoid surface can be derived provided the coordinates and ellipsoidal heights and orthometric heights of enough points in the area are available. The polynomial of smallest degree used in literature is the one-degree with three parameters, also called plane surface, which is expressed in equation (2) (Nwilo et al., 2009; Odumosu et al., 2016).

Machine Learning Techniques for Geoid Modeling 

MLTs have been applied in the analysis of various geospatial data in many areas of geomatics and the environment such as spatial predictions, classification and mapping (Kang et al., 2021); natural hazards and environmental risk assessments (Mousavi et al., 2011); and geoid modeling (Dawod & Abdel-Aziz, 2020). Recently, artificial neural networks models are employed in modeling local geoid surfaces and found to give better accuracies (Gullu et al., 2011, Akari et al., 2020, Cakir et al., 2014). Several researches have studied the performance of ANN with a different network topology in the modeling of a local geoid surface (Lin, 2007; Akcin and Celik, 2013; Erol and Erol, 2013; Albayrak et al., 2020). Five machine learning models are employed to model local geoid surface in this study; they include multilinear regression (MLR), random forest (RF), support vector regression (SVR), multilayer perceptron (MLP) and generalized regression neural network (GRNN). 

Global Geoid Models

The global geoid models such as Earth Geopotential Model 2008 (EGM08) make geoid height available globally. Since they are not regional or local, the global geoid models have a disadvantage that the geoid heights they provide are not reliable for mapping and engineering development locally. EGM08 global geoid model provides undulation values N with an uncertainty between ±37cm and ±22cm. (Gomaa et al, 2010). This is a good reason for creating local and regional geoid models. 
However, GNSS observations on large control points can be time-consuming and expensive. This study, therefore, aims to investigate how machine learning techniques can improve accuracy of geoid models using geoid heights provided by global geoid models. The strength of five machine learning models – multilinear regression (MLR), random forest (RF), support vector regression (SVR), multilayer perceptron (MLP) and generalized regression neural network (GRNN) – to model local geoid surface was investigated. Dataset used to build an existing local geoid model was used as test data, and the results were compared with existing accuracy. 

MATERIALS AND METHOD

Datasets

Three datasets were used in this study. The first dataset was sourced from the Federal Capital Development Authority. It comprises coordinates and orthometric heights of 2,108 control points (first-order, second-order and third-order) in Nigeria’s Federal Capital Territory (FCT). 
The second dataset is the geoid heights at those control points derived from EGM08 model. It was downloaded from University NAVSTAR Consortium (UNAVCO) website at https://www.unavco.org/software/geodetic-utilities/geoid-height-calculator/geoid-height-calculator.html. 
The third dataset is an existing data determined from GPS/leveling observations in the study area by Oluyori et al., (2020). The dataset consists of coordinates of 24 control points, their orthometric heights, ellipsoidal heights and geoid heights. 

EGM08-Computed and GPS/Leveling-Observed Geoid Heights

As mentioned above, geoid heights were computed from EGM08 global geoid model for all 2, 108 control points. The EGM08-computed geoid heights together with other computed features were input into the machine learning codes described above. On the other hand, Oluyori et al. (2020) dataset determined from GPS/leveling campaign carried out on 24 control points gives GPS/leveling-observed geoid heights in the same study area.
3.3	Performance Metrics
In assessing the performance of geometric surface model in a particular region, several tests can be applied to the results. Root mean square error (RMSE) and coefficient of determination R2 score or goodness of fit are applied in this study. A statistical measure of the goodness of model fit for a discrete set of points is given by the coefficient of determination, denoted by R2. It can be described as the ratio of the sum of the squares due to the fit, to the sum of the squares about the mean of the observations. Thus, the coefficient of determination varies between 0 and 1 (0 ≤ R2 ≤ 1) and the closer the value is to one, the smaller the residuals and hence the better the fit. 

Coding the Machine Learning Models
A program named geoid_surface_ABUJA.ipynb was written by this author in JupyterLab® to implement MLR, RF, SVR, MLP and GRNN modelS. GRNN was implemented using pyGRNN library developed by GKDD (Geosciences and Knowledge Discovery in Data) research group of the University of Lausanne, Switzerland (https://github.com/federhub/pyGRNN). 
Three functions named training, testing, and evaluation were hard-coded in JupyterLab and called each time a model was going to be implemented. Training trains the model, fitting it with the training data so it learns the relationships among the features in the data. Testing predicts new values of the target variable. The performance of the model when fed with the test dataset shows how it will perform when it encounters new data in the world (Taiwo et al., 2023). The evaluation function assesses the model performance with RMSE and R2. 
The coefficients of the quantic model were computed in Microsoft Excel® worksheet from the observed dataset and stored in a csv file, which holds the data input for the machine learning models, and is called into the codes. 

RESULTS

geoid_surface_ABUJA,ipynb outputs RMSE and R2 for both training and testing data for each of the machine learning models. It should be noted that machine models do not output parameters. However, machine learning models are good at prediction. Thus, the machine learning models produced predicted or interpolated values of N, the precision of which was measured by RMSE. 
Predicted Geoid Heights

 In order to investigate the accuracy of the predicted geoid heights, the models were trained with 50 control points, 1000 control points and 2000 control points. The R2 score values show that RF, MLP and GRNN well fitted the data. It can also be seen that GRNN model gives the highest accurate prediction with lowest RMSE. Thus, confirming that GRNN best model the local geoid surface. Table 7 shows sample predicted geoid height for ten control points. Table 8 shows the results of testing GRNN model with GPS/leveling-observed geoid heights. 

The above analysis shows that GRNN models the EGM08-computed geoid heights to 1cm level and fitted the data to 0.9 R2 score. However, when GPS/leveling-observed geoid heights of the same study area was tested with the same GRNN model the results in Table 8 show RMSE of 0.374m and 0.2 R2 score. 

Comparing the Present Results with the Accuracies Achieved by Existing Studies

RMSE of 37cm achieved in this study is worse compared to accuracy achieved when ellipsoidal heights from GPS/leveling observations were used for local geoid modeling. The study by Oluyori et al. (2020) whose dataset was used in this study RMSE of ±11 cm for multiquadratic polynomial, and RMSE of ±14 cm for bi-cubic polynomial. Similar studies by various researchers reported better accuracy. For example, Nwilo et al. (2009) got RMSE of 6cm; Olaleye et al. (2013) got RMSE of 15cm using a plane surface polynomial; and Odumosu et al. (2016) achieved RMSE of 9cm. The present results confirm that GPS/leveling observations should be carried out when modeling local geoid surfaces. They also confirm the findings of Gomaa et al. (2010) that global geoid models give uncertainty between ±37cm and ±22cm. 

CONCLUSION

This study investigated the accuracy of local geoid model in Nigeria’s FCT built with global geoid model EGM08-computed geoid heights and five machine learning techniques. Generalized Regression Neural Network (GRNN) model gives RMSE of 1cm and R2 score of 0.9 when trained and tested with EGM08-computed geoid heights. But when the model was tested with GPS/leveling-observed geoid heights, it gave RMSE of 37cm and R2 score of 0.2. Compared with accuracy of existing local geoid model of the same study area, it was concluded that geoid heights computed from EGM08 are not appropriate to use for local geoid modeling. It is therefore confirmed that, in order to achieve better accuracy when building local geoid model, GPS/leveling observations should be carried out to determine orthometric heights and ellipsoidal heights, from which geoid heights can be computed. GPS/leveling-observed geoid heights are more reliable than geoid heights computed from global geoid models such as EGM08. 
