# Wine Quality

## Links

- Repository: https://github.com/Oxel40/sml-wine-quality
- HuggingFace Model: https://huggingface.co/spaces/Oxel40/Wine
- HuggingFace Monitor: https://huggingface.co/spaces/Oxel40/Wine-monitor


## Description

### Feature Pipeline
The file `wine-feature-pipeline.ipynb` is a jupyter notebook that registers the wine quality dataset `winequality.csv` as a Feature Group with Hopsworks.


### Training Pipeline
The file `wine-training-pipeline.ipynb` jupyter notebook takes care of the training pipeline. It reads training data from Hopsworks, trains a K-Nerest-Neighbors regression model from scikit-learn (KNeighborsRegressor), and upploads the model to Hopsworks. 

### Gradio Application
In the directory `hugggingface-spaces-wine` the file `app.py` is responsible for the Gradio application that downloads the model from Hopsworks and provides an user interface in which users can enter and select feature values to predict the wine quality based on those features.

### Gradio Monitor
In the directory `higgingface-space-wine-monitor`. This Gardio application shows the latest four predictions registered by the batch inference pipeline in a table and in a comfution matrix, data/images it fetches from Hopsworks. It's hoosted on HuggingFace.

### Data Generator
The file `wine-feature-pipeline-daily.py`, runs once per day using GitHub actions (see `.github/workflows/wine-feature-pipeline-daily.yml`). This generates five new datapoints of wine quality and uploads them to Hopsworks. The feature values are generated by sampling appropriately formatted normal distributions.

### Batch Inference Pipeline
The file `wine-batch-inference-pipeline.py`, runs once per day using GitHub actions (see `.github/workflows/wine-batch-inference.yml`) and predicts the quaity of the new wine