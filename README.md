Fraud Detection Knowledge Graph Pipeline

This notebook demonstrates a comprehensive pipeline for creating a fraud detection knowledge graph using Amazon Bedrock via the Langchain LLM Graph Transformer library. The graph is then stored into Neptune where a GNN (graphical neural network) is run via SageMaker to perform the fraudulent transaction detection.

Overview

The pipeline consists of the following main steps:

-Data Preparation
-Knowledge Graph Generation using Amazon Bedrock
-Loading Data into Amazon Neptune
-Machine Learning with Neptune ML leveraging GNN (graphical neural networks)

Prerequisites

AWS account with access to Amazon Bedrock, Amazon Neptune, and Neptune ML
Python 3.x
Required Python libraries: boto3, gremlinpython, and tqdm (install using pip)

Setup

Ensure you have the necessary AWS credentials and permissions set up.
Install required Python libraries:

```pip install boto3 gremlinpython tqdm langchain langchain_experimental nest_asyncio```


Main Components

Data Preparation:

Load and preprocess the credit card transaction data (in csv format).
Create input batches for Bedrock processing.


Knowledge Graph Generation:

Use Amazon Bedrock with Claude 3 Sonnet to generate knowledge graph structures from transaction data.
Process batches of data in parallel using Bedrock batch inference jobs.


Neptune Graph Database:

Load the generated nodes and relationships into Amazon Neptune leveraging the following CloudFormation template: https://docs.aws.amazon.com/neptune/latest/userguide/machine-learning-quick-start.html

Import the Python notebook generated from the template into Neptune in order to perform basic graph queries to verify data loading.


Neptune ML:

Export graph data for ML processing.
Set up and run data processing, model training, and endpoint creation for fraud detection. Leverage GNN (graphical neural networks).
Perform inferences on the graph to predict fraudulent transactions using the GNNs.



Usage
Run the notebook cells sequentially, following the comments and instructions provided in each section.
Important Notes

Ensure proper IAM roles and permissions are set up for accessing AWS services.
Be aware of the costs associated with using Amazon Bedrock, Neptune, and Neptune ML.
The notebook includes steps to clean up resources (e.g., deleting endpoints) to avoid unnecessary charges.

Customization
You can customize the pipeline by modifying:

-The input data source (adding more data)
-The knowledge graph schema
-The ML model configuration for fraud detection

Troubleshooting
If you encounter issues:

Make sure you have model access on Bedrock
Check AWS service quotas and limits
Verify IAM permissions
Review the AWS CloudWatch logs for detailed error messages