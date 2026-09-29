# predictive-crime-pattern-analysis-and-hotspot-evolution
Attention-based Spatio-Temporal Graph Convolutional Network (ASTGCN) for predictive crime pattern analysis and hotspot evolution.
#Abstract:
Crime patterns vary across different parts of a city and change over time. Predicting these variations requires a model that can account for both geographic relationships and temporal trends. This paper presents an Attention-based Spatio-Temporal Graph Convolutional Network (ASTGCN) for predictive crime pattern analysis and hotspot evolution. The proposed approach represents Chicago’s 77 community areas as nodes in a spatial graph and uses historical crime records to construct weekly crime-count sequences. Spatial and temporal attention mechanisms are incorporated to learn changing relationships between neighboring areas and historical time steps. The model generates weekly crime-count predictions and identifies changes in hotspot conditions across successive time windows.
Model is trained using Chicago crime records from 2001 to 2023. The results show that the proposed model can capture meaningful variations in crime activity across community
areas and provide information about the evolution of predicted hotspots.
Keywords—Crime prediction, spatio-temporal graph neural network, ASTGCN, spatial attention, temporal attention, hotspot evolution.

   # [1.] INTRODUCTION:
	Crime incidents are not distributed uniformly across an urban area. Some community areas experience consistently higher crime activity while others show changes depending on the time period. These variations make crime prediction a spatial as well as a temporal problem. A model that considers only the total number of incidents may overlook where crime activity is concentrated and how these concentrations change over time. Many existing crime prediction approaches use statistical models, machine learning algorithms, or deep learning architectures to forecast future crime counts. Although these methods can identify patterns in historical records, representing the relationships between different geographic areas remains a challenge. In particular, conventional grid-based approaches do not necessarily reflect the actual spatial organization of a city. This work considers Chicago's 77 community areas as connected geographic units rather than independent locations. A spatial graph is constructed by connecting nearby community areas, allowing the model to use information from neighboring regions during prediction. Historical crime records are aggregated into weekly counts, which are then used to learn temporal patterns. The proposed framework is based on an Attention-based Spatio-Temporal Graph Convolutional Network (ASTGCN). Temporal attention assigns different weights to historical time steps, while spatial attention learns the relative importance of geographic relationships. Graph convolution and temporal convolution are then used to extract spatio-temporal features from the input sequences. In addition to forecasting crime counts, this work examines how predicted crime activity changes across community areas. The model produces a crime-density representation and assigns hotspot transition states such as emerging, persisting, dissipating, and stable-normal. These outputs provide a way to examine changes in predicted crime concentration rather than relying only on a single forecast value. The study uses Chicago crime records collected between 2001 and 2023. The main objectives are to develop a graph-based crime-count prediction model, capture spatial and temporal dependencies through attention mechanisms, and use the resulting predictions to analyze hotspot evolution across community areas.
    ##[2.] PROBLEM STATEMENT:
	Existing crime forecasting methods have several limitations. Grid based CNN and LSTM models can learn local spatial or temporal patterns but they do not explicitly represent relationships between different regions. KNN based graph models can represent spatial relationships but their temporal modeling may be simpler. More detailed approaches such as street network or hybrid models can capture richer relationships but may require more data and a more complex pipeline. Crime data can also be sparse with many time periods having low or zero counts. Therefore, there is a need for a practical model that can represent spatial relationships using a simple distance based rule that will learn which historical time steps are most important through attention and produce clear hotspot evolution.
    ##[3.] OBJECTIVES:
• To develop an attention-based spatio-temporal graph model that captures spatial and temporal crime patterns for predictive analysis.
• To clean and transform crime records into spatial nodes and time-based sequences.
• To build a graph that represents relationships between nearby crime regions.
• To use spatial and temporal attention to learn important regions and historical time steps.
• To predict crime counts and identify high-risk regions for the next time period.
• To evaluate the model using MAE and RMSE, along with hotspot Precision, Recall, and F1-score where applicable.
    #[4.] SCOPE OF THE PROJECT:
The project focuses on public urban crime data containing location, timestamp, and crime-related attributes. The study area is represented using Chicago's 77 community area as  administrative regions. The system covers data preprocessing, graph construction, spatio-temporal model training, crime-count prediction, and hotspot evolution. The system incorporates features derived from crime records including arrest rate, domestic incident rate, time of day. The main outputs are the predicted crime count for each region and a hotspot evolution classification (emerging, persisting, dissipating or stable) describing how each region's crime activity is expected to change over the coming time window. The project is intended for research and decision support purposes not for identifying individual offenders.
   # [5.] PROPOSED SYSTEM:
The proposed system follows an ASTGCN-style workflow. First crime records are cleaned and aggregated into fixed time intervals for each spatial region. Each region becomes a graph node and nearby regions are connected using a spatial rule based on geographic distance. The historical node features are arranged as a spatio-temporal input. Spatial attention learns which regions have stronger relationships while temporal attention learns which historical time steps are more useful. The spatial-temporal convolution block then uses graph convolution to learn spatial patterns and temporal convolution to learn changes over time. A single step historical window is used as model input. An ablation study across window lengths (1, 3, 5 and 12 weeks) showed no significant performance difference and a 1-week window is selected for the final model based on efficiency and simplicity. The final layer predicts crime counts for the next time period which are converted into both a crime density map and a hotspot evolution map showing predicted transition states (emerging, persisting, dissipating or stable) for each region.
    #[6.] LITERATURE SURVEY:
S.NO	TITLE	MERITS	DEMERITS
1	Spatial-Temporal Sequential Hypergraph Network for Crime Prediction with Dynamic Multiplex Relation Learning	The paper models crime using spatial and temporal relationships and a hypergraph. It can learn relationships between different regions and crime types, including both nearby and more distant dependencies.	The hypergraph and multiplex relation learning make the model more complex. It also needs more computation and careful modeling than a basic ST-GNN.
2	Spatio-Temporal-Network Point Processes for Modeling Crime Events with Landmarks	The paper considers the street network instead of using only straight-line distance. It also includes nearby landmarks and learns relationships between crime and urban environment.	It requires detailed street-network and landmark information. The point-process framework is specialized and is more difficult to implement than a standard graph neural network.
3	Crime Forecasting: A Spatio-temporal Analysis with Deep Learning Models	The study shows that preprocessing crime records into time/space bins can improve prediction. The CNN-LSTM model learns spatial patterns with convolution and temporal patterns with LSTM.	The model is mainly grid-based and does not explicitly learn graph relationships between different regions. Poorly selected bins can also reduce spatial detail.
4	A Deep Neural Network for Spatiotemporal Prediction of Theft Crimes	The paper uses a deep neural network with spatial and temporal information for theft prediction. It considers recent and periodic temporal patterns and demonstrates the usefulness of deep learning for crime forecasting.	The study is focused on theft and its spatial representation is based on grid areas. It does not provide the same dynamic graph-based spatial learning used in the proposed project.
5	An Integrated Graph Model for Spatial-Temporal Urban Crime Prediction Based on Attention Mechanism	The model combines graph learning, temporal learning and attention to capture spatial-temporal crime dependencies. External information can also be included to improve prediction.	The integrated architecture contains several components, making implementation and tuning more difficult. It may also require additional external features.
6	Deep Spatio-Temporal Graph Attention Network for Street-Level 110 Call Incident Prediction	The study uses graph attention to learn different levels of influence between locations and combines spatial and temporal information. It is useful for understanding dynamic relationships in urban incidents.	The data are 110-call incidents rather than a general crime dataset. Street-level graph construction can also require detailed geographic information.
7	Crime Prediction Using Spatio-Temporal Analysis	The study demonstrates that combining spatial and temporal information is useful for crime prediction. It provides a practical comparison of deep-learning approaches for crime forecasting.	The approach is less focused on dynamic graph relationships. It therefore does not fully represent how one region can influence another region.
8	Hybrid Spatio-Temporal Crime Forecasting with Graph Neural Networks	The hybrid approach combines clustering, temporal learning and graph neural networks. This helps identify crime hotspots while also modeling changes over time.	The multi-stage pipeline is more complicated to train and maintain. Several models and processing steps must work correctly together.
9	Spatio-Temporal Graph Neural Networks for Accurate Crime Prediction	The study uses spatial coordinates and KNN to construct a graph. This allows the model to use relationships between nearby regions instead of treating every location independently.	The graph is mainly based on spatial proximity, so other urban relationships may not be represented. The temporal modeling is also less detailed than a full attention-based ASTGCN.
10	Attention Based Spatial-Temporal Graph Convolutional Networks for Traffic Flow Forecasting	This paper introduces the ASTGCN framework. It uses spatial attention, temporal attention and separate recent, daily and weekly components to learn changing spatial-temporal dependencies.	The original application is traffic forecasting rather than crime. Therefore, the architecture needs adaptation for sparse and zero-heavy crime-count data.
11	Diffusion Convolutional Recurrent Neural Network: Data-Driven Traffic Forecasting	DCRNN combines graph-based diffusion convolution with recurrent neural networks. It shows how spatial relationships and temporal dependencies can be learned together.	The model is designed for traffic networks and uses recurrent computation. It does not directly address crime-specific issues such as sparse crime counts or hotspot thresholds.
12	Spatio-Temporal Graph Convolutional Networks: A Deep Learning Framework for Traffic Forecasting	STGCN combines graph convolution and temporal convolution in one framework. It is useful for learning spatial relationships and time-dependent changes without treating regions as independent time series.	The original work focuses on traffic data. It does not include crime-specific factors such as crime type, sparse events, or near-repeat crime behavior.
13	Graph Attention Networks	GAT introduces attention over graph neighbors so that different neighboring nodes can receive different importance. This provides a useful basis for learning dynamic spatial relationships.	The original GAT is not a spatio-temporal crime model. A separate temporal component is required when the input changes over time.
14	Deep Spatio-Temporal Residual Networks for Citywide Crowd Flows Prediction	The model uses residual deep learning to capture spatial and temporal patterns in citywide data. It demonstrates that recent and periodic temporal information can improve urban prediction.	The model is designed for crowd-flow prediction and uses a grid-like spatial representation. It does not explicitly model graph topology between crime regions.
15	Long Short-Term Memory	LSTM is designed to learn long-term dependencies in sequential data. It is useful for modeling daily, weekly and other time-dependent crime patterns and can serve as a temporal baseline.	LSTM alone does not understand spatial relationships between regions. Each region may be treated as an independent sequence unless a spatial model is added.

    #[7.]  DESIGN & METHODOLOGY:
A. Data Preprocessing:
    • Relevant fields were selected from the raw crime records.
    • Date and time values were converted into a standard datetime format.
    • Latitude, longitude and community area values were converted into numeric form.
    • Boolean fields such as Arrest and Domestic were encoded as binary values.
    • Records with missing Date, Community Area, Latitude, or Longitude were removed.
    • Records with Community Area 0 were also excluded because they represent unclassified locations.
B. Spatial Graph Construction:
    • Chicago was divided into 77 community areas, with each area represented as a graph node.
    • The average latitude and longitude of the crime records were used to determine the location of each community area.
    • Pairwise distances between community-area centroids were calculated.
    • Connections were created between areas within the closest 15% of the observed distance distribution.
    • The resulting connections formed the adjacency matrix used by the graph convolution layers.
    • Chebyshev graph convolution was used to capture information from multiple spatial hops.
C. Temporal Aggregation:
    • Individual crime records were aggregated into weekly crime counts for each community area.
    • A logarithmic transformation was applied to reduce large differences in crime counts.
    • The transformed values were standardized using z-score normalization.
    • A sliding-window method was used to prepare the training samples.
    • The previous week's information was used to predict the crime count for the following week.
D. ASTGCN Deep Learning Core:
    • The model uses an Attention-based Spatio-Temporal Graph Convolutional Network (ASTGCN).
    • Temporal Attention Layer: identifies the time steps that contribute more to the prediction.
    • Spatial Attention Layer: learns different importance levels for relationships between community areas.
    • Spatio-Temporal Convolution: combines Chebyshev graph convolution with one-dimensional temporal convolution.
    • ReLU activation is applied after the convolution operations.
    • The spatio-temporal convolution block is applied twice for further feature extraction.
E. Prediction Output Head
The model produces two outputs:
    • Count Head: predicts the expected crime count for each community area in the next week.
    • Transition Head: assigns each area to one of four hotspot-transition categories such as Emerging,Persisting, Dissipating and Stable.
F. Final Forecast
    • The predicted crime counts are arranged into a crime density matrix covering the community areas and forecast weeks.
    • A hotspot evolution map displays the predicted transition category of each community area.
    • The map helps show areas where crime activity is expected to increase, remain persistent, decrease, or remain stable.
   # [8.] SAMPLE CODE:
Use the columns which are needed:


Data cleaning:


Spatial graph construction:




Spatio-Temporal Tensor:

 


Temporal Attention Layer:


















Spatial Attention Layer:


STConvBlock:


  #  [9.] OUTCOME OF THE PROJECT:
Predictive Crime Pattern Analysis:





        













ASTGCN Model Performance:

Evaluation Metric	Value
Mean Absolute Error (MAE)	9.49
Root Mean Squared Error (RMSE)	15.38
Coefficient of Determination (R2 )	0.8899

Hotspot Evolution Map:


[10.] FINDINGS IN LITERATURE SURVEY:
The reviewed studies show that crime forecasting has moved from traditional statistical and machine-learning methods toward deep spatio-temporal models. CNN-LSTM and related models can learn spatial and temporal patterns from gridded crime data, while GCN, STGCN and ST-GNN models represent relationships between different regions. Attention-based methods further allow the model to give different importance to locations and time steps. The reviewed crime-specific studies also show the value of KNN graphs, hypergraphs, street networks, external features and hybrid models. However, many approaches are either grid-based, computationally complex, or designed for another domain such as traffic. Therefore, this project focuses on an ASTGCN-style model that combines spatial graph learning, temporal patterns and attention in a comparatively simple framework for crime-count forecasting and hotspot visualization.
     [11.] SOFTWARE REQUIREMENTS:
         Functional Requirements:
    • Import and preprocess crime data.
    • Create spatial nodes and the graph structure.
    • Generate spatio-temporal input sequences.
    • Train and test the attention-based STGNN model.
    • Generate crime-count predictions and hotspot maps.
         Non Functional Requirements:
    • Performance: Support GPU training when available.
    • Scalability: Handle different numbers of spatial regions and historical time windows.
    • Reliability: Handle missing values and sparse crime counts safely.
    • Interpretability: Present predictions as clear regional hotspot maps.
#[11.] SUMMARY:
This project proposes a practical attention based spatio-temporal graph model for predictive crime pattern analysis. The main idea is simple. Represent the city as connected regions, use historical crime counts as time based features, learn important spatial and temporal relationships with attention and predict the next period crime count and classify how each region's hotspot status is evolving. The approach is supported by the reviewed literature on graph based crime prediction, attention models, grid based deep learning and STGNNs. The final predictions are evaluated with standard error measures and hotspot classification measures and shown on maps so that the results are easy to understand.

#[12.] REFERENCES:

    [1.] Xia, L., Huang, C., Xu, Y., Dai, P., Bo, L., Zhang, X., & Chen, T. (2021). Spatial-Temporal Sequential Hypergraph Network for Crime Prediction with Dynamic Multiplex Relation Learning. IJCAI.
    [2.] Dong, Z., Mateu, J., & Xie, Y. (2024). Spatio-Temporal-Network Point Processes for Modeling Crime Events with Landmarks. arXiv preprint.
    [3.] Li, M., Wei, D., Shuo, W., Qi, L., Tong, Z., & Wei, Z. (2025). Crime Forecasting: A Spatio-temporal Analysis with Deep Learning Models. arXiv preprint.
    [4.] Lv, X., Jing, C., Wang, Y., & Jin, S. (2022). A Deep Neural Network for Spatiotemporal Prediction of Theft Crimes. ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences.
    [5.] Hou, M., Hu, X., Cai, J., Han, X., & Yuan, S. (2022). An Integrated Graph Model for Spatial-Temporal Urban Crime Prediction Based on Attention Mechanism. ISPRS International Journal of Geo-Information.
    [6.] Sui, J., Chen, P., & Gu, H. (2024). Deep Spatio-Temporal Graph Attention Network for Street-Level 110 Call Incident Prediction. Applied Sciences.
    [7.] Akinyotu, D.V., Sako, D.J.S., & Igiri, C.G. (2026). Crime Prediction Using Spatio-Temporal Analysis. Research Journal of Pure Science and Technology.
    [8.] Orekoya, V. P., Mathias D., Bennett, E.O., & Anireh, V.I.E. (2025). Hybrid Spatio-Temporal Crime Forecasting with Graph Neural Networks. International Journal of Computer Science and Mathematical Theory.
    [9.] Roshankar, R., & Keyvanpour, M. R. (2023). Spatio-Temporal Graph Neural Networks for Accurate Crime Prediction. 13th International Conference on Computer and Knowledge Engineering (ICCKE).
    [10.] Guo, S., Lin, Y., Feng, N., Song, C., & Wan, H. (2019). Attention Based Spatial-Temporal Graph Convolutional Networks for Traffic Flow Forecasting. AAAI.
    [11.] Li, Y., Yu, R., Shahabi, C., & Liu, Y. (2018). Diffusion Convolutional Recurrent Neural Network: Data-Driven Traffic Forecasting. ICLR.
    [12.] Yu, B., Yin, H., & Zhu, Z. (2018). Spatio-Temporal Graph Convolutional Networks: A Deep Learning Framework for Traffic Forecasting. IJCAI.
    [13.] Veličković, P., Cucurull, G., Casanova, A., Romero, A., Lio, P., & Bengio, Y. (2018). Graph Attention Networks. ICLR.
    [14.] Zhang, J., Zheng, Y., & Qi, D. (2017). Deep Spatio-Temporal Residual Networks for Citywide Crowd Flows Prediction. AAAI.
    [15.] Hochreiter, S., & Schmidhuber, J. (1997). Long Short-Term Memory. Neural Computation.
