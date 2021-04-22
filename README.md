<h1 align="center">Project Assignment from ELuv.io</h1>

<h2 align="center">Text-Generation-Analysis(NLP)models as a Service</h2>

<p align="center">
<img alt="Project Insight" src="meta/meta.png">
</p>

## Contents

1. [Introduction](#section01)
    - [Features](#section01a)
2. [Installation](#section02)
    - [Setup and Documentation](#section02a)
3. [Project Details](#section03)
    - [Demonstration](#section03a)
    - [Directory Details](#section03b)


<a id='section01'></a>

## Introduction

Project Insight is designed to create NLP as a service with code base for both front end GUI (**`streamlit`**)  and backend server (**`FastApi`**) the usage of transformers models on various downstream NLP task.

The downstream NLP tasks covered:

* Sentence Completion(with seed text and context)

* Upvotes Prediction(Regression/Classification)

* Post Generation(with selected subject and upvotes)

* Sentiment Analysis

* Topic Prediction(Zero Shot) `To Do`

* Many more thing like NER, Clustering, Ranking etc could be done

<a id='section01a'></a>

### Features of the solution

* **Python Code Base**: Built using `Transformers` and `Streamlit` making the complete code base in Python. Also server could run from Jupyter notebook without writing any code for deployment and API Creation.
* **Expandable**: The Streamlit framwork is desinged in a way that code can be expanded and Streamlit also provides us '''@st.cache''' that we could use to cache the models which saves us a lot of time and use of more Transformer based models will make the models use in app more changable with writing much costum code and it will be available in the front end app automatically. 
* **Micro-Services**: The backend is designed with a microservices architecture, with no dockerfile for any of the service and leveraging colab ipython for execution we can run the notebook as a server independently with all models running independently.
    - This makes it easy to update, manitain, start, stop different NLP services.


<a id='section02'></a>

## Installation

* Clone the Repo.
* Run the `Docker Compose` to spin up the **Fastapi** based backend service.
* Run the **Streamlit app** with the `streamlit run command`.

<a id='section02a'></a>

### Setup and Documentation

1. **Download the models**
    - Download the models from [here](https://drive.google.com/drive/folders/1Lc7kvfNnMRgA7tkPR5zaSAoSjC2sCudI?usp=sharing)
    - Save them in the specific model folders inside the `src_fastapi` folder.

2. **Running the backend service.**
    - Go to the `src_fastapi` folder
    - Run the `Docker Compose` comnand

    ```console  
    $ cd src_fastapi
    src_fastapi:~$ sudo docker-compose up -d
    ```

3. **Running the frontend app.**
    <!---
    - Front end is a **`WIP`** as a change in the backend architecture.
    - Should be up in a few days.
    --->
    - Go to the `src_streamlit` folder
    <!---
    - Create the docker image from the `Docker File`
    - Then execute the docker image to spin up a container.
    ```console  
    $ cd src_streamlit
    src_streamlit:~$ sudo docker build -t streamlit_app .
    src_streamlit:~$ sudo docker run -d --name streamlit_app streamlit_app
    ```
    --->
    - Run the app with the streamlit run command
    ```console  
    $ cd src_streamlit
    src_streamlit:~$ streamlit run NLPfily.py
    ```

4. **Access to Fastapi Documentation**: Since this is a microservice based design, every NLP task has its own seperate documentation
    - News Classification: http://localhost:8080/api/v1/classification/docs
    - Sentiment Analysis: http://localhost:8080/api/v1/sentiment/docs
    - NER: http://localhost:8080/api/v1/ner/docs
    - Summarization: http://localhost:8080/api/v1/summary/docs


<a id='section03'></a>

## Project Details

<a id='section03a'></a>

### Demonstration

<p align="center">
<img alt="Project Insight Demo" src="meta/streamlit-NLPfiy.gif">
</p>

<a id='section03b'></a>

### Directory Details

* **Front End**: Front end code is in the `src_streamlit` folder. Along with the `Dockerfile` and `requirements.txt`

* **Back End**: Back End code is in the `src_fastapi` folder.
    * This folder contains directory for each task: `Classification`, `ner`, `summary`...etc
    * Each NLP task has been implemented as a microservice, with its own fastapi server and requirements and Dockerfile so that they can be independently mantained and managed.
    * Each NLP task has its own folder and within each folder each trained model has 1 folder each. For example:
    ```
    - sentiment
        > app
            > api
                > distilbert
                    - model.bin
                    - network.py
                    - tokeniser files
                >roberta
                    - model.bin
                    - network.py
                    - tokeniser files
    ```
    * For each new model under each service a new folder will have to be added.
    * Each folder model will need the following files:
        * Model bin file.
        * Tokenizer files
        * `network.py` Defining the class of the model if customised model used.

    * `config.json`: This file contains the details of the models in the backend and the dataset they are trained on.
