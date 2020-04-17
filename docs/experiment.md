# Run an experiment

An experiment trains and tests a machine-learning model. The code in this section runs a model through a complete lifecycle and saves the final model to the local drive. Run the code that defines a machine-learning model and its lifecycle. Design an experiment and execute it. Most of the work of choosing features and specific model parameters will be done automatically. The code will also automatically score each option and return the options with the best predictive performance.

### run_experiment(experiment_design):

Below is a example for experiment_design in run_experiment() function.
```
experiment_design = {
    #model options include ['regression()', 'classification()']
    "model": regression(),
    "labels": df.avg_est_unit_cost_error,
    "data": df,
    #Tell the model which column is 'output'
    #Also note columns that aren't purely numerical
    #Examples include ['nlp', 'date', 'categorical', 'ignore']
    "meta_data": {
      "avg_est_unit_cost_error": "output",
      "_id.funding_source": "categorical",
      "_id.department_name": "categorical",
      "_id.replacement_body_style": "categorical",
      "_id.replacement_make": "categorical",
      "_id.replacement_model": "categorical",
      "_id.procurement_plan": "categorical"
  }
}
```

__The ML model and lifecycle__
The code in this section defines what we mean by a machine-learning model and the lifecyle that all models will go through. The model class defines a basic machine-learning model. All machine learning models must be a subclass of model. The run_experiment function takes in subclasses of model and defines the lifecycle of a model.

__Select a model__
The model provides the intelligent behavior that you will publish as a microservice. The code in this section provides you with options for the model. Each code block defines a different type of model. You must select a model capable of using df to learn the behavior specified in the design section of the datastory. Run this function by defining each model type, then choose the model most appropriate for your datastory. Each model adheres to the specifications of a model. This allows any of the models to run according to the standard model lifecycle defined in run_experiment.

_Prediction model:_ This section defines a new type of model by creating a subclass of model. The prediction model learns to predict a particular outcome. It automatically optimizes parameters, selects features, selects an algorithm, and scores the results.

_Regressor model:_ The regressor model makes a numeric prediction. Use this model when the design specification of the datastory requires the AI microservice to give a numerical outut prediction.

_Classification model:_ The classification model makes a classification prediction. Use this model when the design specification of the datastory requires the AI microservice to give a categorical (text-based) outut prediction.

__Execute the experiment__
This code executes an experiment by running run_experiment() on a model. Update experiment_design with parameters that fit your project. The data parameter should remain df-- the refined training data. The model parameter must be a model subclass. The labels parameter indicates the column of the data dataframe to be predicted. For the prediction model, the meta-data must describe the column to be predicted and the types for non-numeric columns.