# Publish a Microservice 

Insights are delivered through microservices with published APIs. The code in this section prepares an execution environment for the microservice, builds a microservice using the machine-learning model, deploys the microservice into the execution environment, and publishes an API enpoint for the microservice. Design the microservice and deploy it. The work of creating the microservice and deploying it will be done automatically. The code will also automatically handle the source code reposity management.

This video provides an overview of the algorithm execution environment provided by Algorithmia. It describes the basic concept of the Algorithmia AI Layer and walks you through publishing a microservice. Watch this video if you are unfamiliar with publishing microservices using Algorithmia. This video should be removed or replaced if the microservices are run using something other than Algorithmia.

[![overview of algorithm](https://img.youtube.com/vi/56yt2Bouq0o/0.jpg)](https://www.youtube.com/watch?v=56yt2Bouq0o)

### publish_microservice(microservice_design, trained_model):

__Configure the microservice execution environment__

The execution environment is where the micorservice runs. This code assumes that the microservice execution environment is Algorithmia.  In order to provide the information required to design the microservice, you must:
- create an Algorithmia account
- create an <a href = "https://algorithmia.com/signin#credentials"> API key</a> with BOTH "Read & Write Data" and "Manage Algorithms" permissions enabled
- create an algorithm user name

__Design the microservice__
This code defines the parameters needed to build and delpoy a microservice based on the trained model. Update microservice_design with parameters appropriate for your project. The parameters must contain valid keys, namespaces, and model paths from Algorithmia.

```
trained_model is the output of run_experiment() function
microservice_design = {
    "microservice_name": "<Name of your microservice>",
    "microservice_description": "<Brief description about your microservice>",
    "execution_environment_username": "<Algorithmia username>",
    "api_key": "<your api_key>",
    "api_namespace": "<your api namespace>",   
    "model_path":"<your model_path>"
}

```