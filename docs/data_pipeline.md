#Data Pipeline

## Build a data pipeline

A data pipeline takes raw data and turns it into refined data that can be used to train and score a machine-learning model. The code in this section takes the output of raw_data() and puts it into a data store. It instructs the data store to refine the raw data into training data. It extracts the training data for use in training a machine-learning model. Specifiy the details for how to connect to the data store. Run the code to connect to the data store. "Write code" that instructs the data store on how to refine the raw data. Run the code to extract the refined data. This code assumes that Mongo DB Atlas is the data store.

You will be using <a href="https://account.mongodb.com/account/login"> MongoDb </a> as your data store. This video provides a general overview of MongoDB. The document model of MongoDB breaks from the traditional relational model of common relational databases. This video describes the basic idea behind the document model. It also describes MongoDb clusters and the methods used to scale. It introduces MongoDB Atlas, which you will be using in the remainder of this notebook.

[![Document model](https://img.youtube.com/vi/EE8ZTQxa0AM/0.jpg)](https://www.youtube.com/watch?v=EE8ZTQxa0AM)

This video provides an overview of <a href="https://account.mongodb.com/account/login">Mongo DB Atlas</a>. It provides an explanation of the software. It walks you through the basic tasks of setting up an account and generating the proper connection credentials. Watch this video if you are unfamiliar with Mongo DB Atlas. This video should be removed or replaced if the data is stored using something other than Mongo DB Atlas.

[![Overview of Mongo DB](https://img.youtube.com/vi/rPqRyYJmx2g/0.jpg)](https://www.youtube.com/watch?v=rPqRyYJmx2g)

### write_raw_data(data_layer, raw_data, date_fields):

This code defines the meta-data needed to connect to Mongo DB Atlas and create a new data store cluster. This is where you define basic information about the location of the cluster and the collection and database to use. Update this code with information appropriate to your project. This code assumes that the data store is Mongo DB Atlas. In order to provide the information required in data_layer, you must:

- Create a MongoDB Atlas account
- Create a cluster
- Create a user
- Generate a connection string
__Note:__ When you configure the IP whitelist for your cluster, choose to allow a connection from anywhere. When creating the database connection string, choose the Python driver version 3.4 or later.

specify the data layer in your function in below format.
```
data_layer = {
    "connection_string": "<your connection_string>",
    "collection_name": "<your collection_name>",
    "database_name": "<your database_name>"
}
```
## Ingest and clean data

This video provides an overview of how to create aggregation pipelines in Mongo DB Atlas. It describes the basic concepts and walks you through example pipelines. Watch this video if you are unfamiliar with Mongo DB Atlas aggregation pipelines.

[![creating aggregation pipelines in Mongo DB](https://img.youtube.com/vi/Kk6Er0c7srU/0.jpg)](https://www.youtube.com/watch?v=Kk6Er0c7srU)

### access_data_from_pipeline(write_raw_data, pipe):

This code instructs the data store on how to refine the output of raw data into something that can be used to train a machine-learning model.The refined data will be stored in the df Pandas dataframe. Make sure the output is what you want before continuing.

Below is a example for defining pipe(aggregation pipeline) in your function.
```
pipe = [
        {
            '$group':{
                '_id': {
                    "funding_source":"$funding_source",
                    "request_type":"$request_type",
                    "department_name":"$department_name",
                    "replacement_body_style":"$replacement_body_style",
                    "equipment_class":"$equipment_class",
                    "replacement_make":"$replacement_make",
                    "replacement_model":"$replacement_model",
                    "procurement_plan":"$procurement_plan"
                    },
                "avg_est_unit_cost":{"$avg":"$est_unit_cost"},
                "avg_est_unit_cost_error":{"$avg":{ "$subtract": [ "$est_unit_cost", "$actual_unit_cost" ] }}
            }
        }
]
  ```
