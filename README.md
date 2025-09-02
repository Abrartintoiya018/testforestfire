Forest Fire Prediction using Machine LearningThis project is an end-to-end machine learning application that predicts the burned area of forest fires based on meteorological data. The model is built using a Random Forest Regressor and is deployed as a web application using Flask and containerized with Docker.Table of ContentsProject OverviewDatasetTechnologies UsedProject StructureSetup and InstallationHow to UseModel DetailsProject OverviewThe goal of this project is to predict the total burned area of a forest fire given specific weather conditions. This is a regression problem solved using a Random Forest model. The entire workflow, from data preprocessing to model training and deployment, is implemented. The final model is exposed via a REST API built with Flask and packaged into a Docker container for easy, cross-platform deployment.Key FeaturesData Preprocessing & Feature Engineering: Cleans and prepares the dataset for modeling.Predictive Modeling: Utilizes a Random Forest Regressor for accurate predictions.Web API: A simple and robust API built with Flask to serve predictions.Containerization: Dockerized for easy setup, scalability, and deployment.DatasetThe project uses the Forest Fires Data Set from the UCI Machine Learning Repository. It contains data from the Montesinho natural park in Portugal.Source: UCI Machine Learning RepositoryFeatures: Includes meteorological data like temperature, relative humidity, wind speed, rain, and FWI System components (FFMC, DMC, DC, ISI).Target Variable: area (the total burned area in hectares).Technologies UsedProgramming Language: Python 3.8Machine Learning Libraries: Scikit-learn, Pandas, NumPyWeb Framework: FlaskContainerization: DockerProject Structuretestforestfire/
├── app.py                  # Flask application script
├── dockerfile              # Docker configuration file
├── forestfire.csv          # The dataset
├── forest_fire_model.pkl   # Pre-trained machine learning model (pickle file)
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
Setup and InstallationTo run this project locally, you will need to have Git and Docker installed on your machine.Step 1: Clone the repositorygit clone [https://github.com/Abrartintoiya018/testforestfire.git](https://github.com/Abrartintoiya018/testforestfire.git)
cd testforestfire
Step 2: Build the Docker imageFrom the root directory of the project, run the following command to build the Docker image.docker build -t forest-fire-predictor .
Step 3: Run the Docker containerOnce the image is built, run the container to start the Flask application.docker run -p 5000:5000 forest-fire-predictor
The application will now be running and accessible at http://localhost:5000.How to UseThe application exposes a single endpoint /predict that accepts POST requests with a JSON payload containing the input features.Endpoint: http://localhost:5000/predictMethod: POSTHeaders: Content-Type: application/jsonExample Request using curl:You can use a tool like curl or Postman to send a request. Here is an example using curl:curl -X POST \
  http://localhost:5000/predict \
  -H 'Content-Type: application/json' \
  -d '{
        "temperature": 25,
        "rh": 60,
        "ws": 5,
        "rain": 0.2,
        "ffmc": 90.5,
        "dmc": 120.2,
        "dc": 550.8,
        "isi": 8.5
    }'
Example JSON Input:{
    "temperature": 25,
    "rh": 60,
    "ws": 5,
    "rain": 0.2,
    "ffmc": 90.5,
    "dmc": 120.2,
    "dc": 550.8,
    "isi": 8.5
}
Example Success Response:{
  "prediction": "The predicted burned area is 12.34 hectares."
}
Model DetailsThe predictive model is a Random Forest Regressor from the Scikit-learn library. It was chosen for its high accuracy, robustness against overfitting, and its ability to handle non-linear relationships in the data effectively. The model is pre-trained and saved as forest_fire_model.pkl.
Model Details
The predictive model is a Random Forest Regressor from the Scikit-learn library. It was chosen for its high accuracy, robustness against overfitting, and its ability to handle non-linear relationships in the data effectively. The model is pre-trained and saved as forest_fire_model.pkl.
