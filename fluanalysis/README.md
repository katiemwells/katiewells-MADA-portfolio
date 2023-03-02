Author: Katie Wells
Date: 03/02/2023
Title : Flu Analysis Module 8

Raw data: fluanalysis -> data -> SympAct_Any_Pos.Rda 
  From: McKay, Brian et al. (2020), Virulence-mediated infectiousness and activity trade-offs and their impact on transmission potential of patients infected with influenza, Dryad, Dataset, https://doi.org/10.5061/dryad.51c59zw4v

Clean data: fluanalysis -> data -> flu2.rds

The data folder contains the raw and cleaned data used in this analysis. 

SympAct_Any_Pos.Rda variables and what they mean: 
"DxName1","DxName2","DxName3","DxName4","DxName5": diagnosis description(s)         "Unique.Visit": visit number      
"ActivityLevel","ActivityLevelF": patient's activity level from 0-10 and then as a factor   "SwollenLymphNodes","ChestCongestion","ChillsSweats","NasalCongestion","CoughYN"          ,"Sneeze","Fatigue","SubjectiveFever","Headache","WeaknessYN","CoughYN2","MyalgiaYN"      ,"RunnyNose","AbPain","ChestPain","Diarrhea","EyePn","Insomnia","ItchyEye","Nausea"     ,"EarPn","Hearing","Pharyngitis","Breathless","ToothPn","Vision","Vomit","Wheeze": response to symptom as Yes/No           
"CoughIntensity","Myalgia","Weakness": responses to symptom as none, mild, moderate, severe
"BodyTemp": patient's body temperature          
"RapidFluA","RapidFluB": Positive or Presumptive Negative for Influenza A/B       
"PCRFluA","PCRFluB": Influenza A/B detected/not detected
"TransScore1","TransScore1F","TransScore2","TransScore2F","TransScore3","TransScore3F"    ,"TransScore4","TransScore4F": calculated infectiousness score and as factor

Cleaned data (flu2) contains all the variables above except for "Unique.Visit" and any variables that contain the words Score, Total, FluA, FluB, Dxname, or Activity. Any NA observations were also removed. 

The code folder contains three Quarto documents for wrangling, exploring, and model fitting the cleaned dataset flu2. 
The wrangling.qmd contains code to load raw data, removed unwanted variables (those with 'Score' 'Total' 'FluA' 'FluB' 'Dxname' 'Activity' as well as 'Unique.Visit' and any NAs), and saving the cleaned data.
The exploration.qmd contains code to load cleaned data, get summary data for the main outcomes of interest (BodyTemp and Nausea), explore the distribution of the contiuous outcome of interest (BodyTemp), and create boxplots of the outcomes of interest and some predictors.
The fitting.qmd contains code to load cleaned data, prepare the linear model with the select engine, fit a linear model to the continuous outcome (BodyTemp) using only the main predictor of interest (RunnyNose) and all predictors, compare the performance of thelinear models, and repeat the same steps with a logistic model with the categorical outcome (Nausea) using only the main predictor of interest (RunnyNose) and all predictors.