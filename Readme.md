# BYOT: Bring Your Own Training

This repo acts as a template repo to bring your own custom training based of this feature https://github.com/guidebooks/store/pull/212

### How do I get started

You can clone this template and extend this and launch your own custom training.

We are running this command behind the scenes, here `CUSTOM_WORKING_DIR` will refer to your directory that was cloned off this template.

`ray job submit  --job-id ${JOB_ID} --no-wait --runtime-env  ${CUSTOM_WORKING_DIR}/runtime-env.yaml --working-dir ${CUSTOM_WORKING_DIR} --address ${RAY_ADDRESS}  -- python main.py `


Broadly, these are the main components of this repo: 

1. [main.py](https://github.com/guidebooks/store/compare/main...atinsood:store:custom_application_merged_v2?expand=1#diff-96e85c3f0a2a6b9054ac677dc591552fd1004314264fbd2bb170e14f46215e35R23) acts as the entry point and this is what will be executed when `ray job submit` will be executed. 

2. `runtime-env.yaml` will act as a a way to provide additional dependencies, and will be installed because of this param in the above command `--runtime-env  ${CUSTOM_WORKING_DIR}/runtime-env.yaml`

3. src/ can act as the placeholder for the rest of your python code. or you can create an other additional directories here. `--working-dir ${CUSTOM_WORKING_DIR}` flag in the above command makes sure that we copy the entire working directory over to the CodeFlare cluster, so all files under your directory will be available to you. 

## About this example

Refer to https://github.com/mlflow/mlflow/blob/master/examples/pytorch/BertNewsClassification/bert_classification.py
