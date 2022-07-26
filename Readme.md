# BYOT: Bring Your Own Training

This repo acts as a template repo to bring your own custom training based of this feature

### How do I get started

You can clone this template and extend this and launch your own custom training. Notice the `config.yaml` file, this acts as a set of instructions on how to submit your job to ray. 

```yaml
name: experiment_1
entrypoint: python main.py # Entrypoint shell command to execute
metadata:
  key: value
runtime_env: #dependencies that need to be installed
  env_vars:
    TF_WARNINGS: none  
  #either pip or conda can be specified
  #pip:
  #- pendulum
  #- requests==2.27.1
  conda:
    dependencies:
    - pip
    - pip:
      - pytorch-lightning==1.6.1
```

When you run BYOT and point to a template repo containing the config.yaml, the entries from this file are read and an equivalent of the below command is executed

`ray job submit  --job-id ${JOB_ID} --no-wait --runtime-env  <runtime env that you defined aboe> --working-dir <location where you clone the template repo> --address ${RAY_ADDRESS}  -- <entrypoint> `
