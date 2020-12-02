[![almahaalhizam](https://circleci.com/gh/almahaalhizam/DevOps_Microservices.svg?style=svg)](https://github.com/almahaalhizam/DevOps_Microservices/tree/master)

## Project Summary

This project includes a pre-trained machine learning model (sklearn) that predicts housing prices. This prediction model is developed as a flask python application, containerized using docker, and deployed locally using kubernetes for testing and debugging purposes. The quality of the code is tested by importing the projrct repo into CircleCI.

### Dependencies (Requirements)
- Python
- Docker Desktop
- Kubernetes
- Circleci Account
- Hadolint


### Instructions 
All the commands used in this README file have been tested in a linux-based machine. For other types of operating systems, you may need to modify some commands. 

  1) Clone the repo. Then, go to the repository's folder and setup an isolated environment by running:
    python3 -m venv ~/.devops
    source ~/.devops/bin/activate

  2) Install the dependencies (required libraries) via `Makefile` by running `make install`. Many of the project dependencies are listed in the file `requirements.txt`; these can be installed using `pip` commands in the provided `Makefile`. Other required depenecies are listed above. Then run the `make lint` to check if hadolint catches any errors in your Dockerfile.


  3) Running the application will require 3 scripts:
      a- python app.py (standalone).
      b- ./run_docker.sh (run in docker).
      c- ./upload_docker.sh (run in docker).
      d- ./run_kubernetes.sh (run in kubernetes).
      
     In order to run the app in Docker container, you will need to have a Docker account and installation. You can have a Docker account through here [create a free docker account](https://hub.docker.com/signup) .
     The `Dockerfile` contains the instructions needed to containerize the `app.py` application. Firstly, run the `./run_docker.sh` script to be able to get Docker running locally from the docker image defined in `Dockerfile`. Then, in order to make it accessible to a Kubernets cluster, you will upload the recently built docker image to Docker hub by running the `upload_docker.sh`. After that, you will will need to install ([Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) to be able run the app in a local Kubernetes cluster through this script `run_kubernetes.sh`
     To make a house predection, Docker and Kubernetes should be running, then you will run the `make_predections.sh` while the app is up. This script basically prepare the payload of a POST request with a json object that contains the concrete values (the input) of the features of the prediction model. The folder `output_txt_files` contains `docker_out.txt` and `kubernetes_out.txt` which are examples of outputs running the app in Docker and Kubernetes, respectively.
     Lastly, the directory .circleci includes one configuration file named `config.yml`, which containes the required instructions to setup a continous integration pipeline to automate the process.
     
  

