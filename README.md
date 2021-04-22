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

Project Insight is designed to create NLP as a service with a code base for both front-end GUI (**`streamlit`**)  and Jupyter notebook the usage of transformers models on various downstream NLP task.

The downstream NLP tasks covered:

* Sentence Completion(with seed text and context)

* Upvotes Prediction(Regression/Classification)

* Post Generation(with selected subject and upvotes)

* Sentiment Analysis

* Topic Prediction(Zero-Shot) `To Do`

* Many more thing like NER, Clustering, Ranking, etc could be done

<a id='section01a'></a>

### Features of the solution

* **Python Code Base**: Built using `Transformers` and `Streamlit` making the complete code base in Python. Also, the server could run from the Jupyter notebook without writing any code for deployment and API Creation.
* **Expandable**: The Streamlit framework is designed in a way that code can be expanded and Streamlit also provides us (**`@st.cache`**) that we could use to cache the models which saves us a lot of time and use of more Transformer based models will make the models use in-app more changeable with writing much custom code and it will be available in the front end app automatically. 
* **Micro-Services**: The backend is designed with a microservices architecture, with no dockerfile for any of the services and leveraging notebooks for execution we can run the notebook as a server independently with all models running independently.
    - This makes it easy to update, maintain, start, stop different NLP services.


<a id='section02'></a>

## Installation

* Clone/Download the Repo.
* Run the `pip install -r requirements.txt ` to install specific versions(won't take much time)
* In the same directory Open the **Eluvio_data_science.ipynb** and run all of the cells
<a id='section02a'></a>

### Setup and Documentation

1. **Download the models**
    - Download the models from [here](https://drive.google.com/drive/folders/1-aeyS6ImGv0nTK3KLGJ0yiYZ1Eh7XPkm?usp=sharing)
    - Save them in your specific model folder.
    
2. **Running the backend service.**
    - Go to the `Eluvio_data_science.ipynb`
    - Run the all of the `Cells`

3. **Running the frontend**
    - It's simple to run(also you already did it)
   
    - After running this 'streamlit run "app.py"' cell
    - Go to the link in just the upper cell's output which should be 'Execute the next cell and go to the following URL: https://649b954f8f89.ngrok.io'
    - Click on this link
    --->
    
<a id='section03'></a>

## Project Details


### Demonstration

<p align="center">
<img alt="Project Insight Demo" src="meta/streamlit-NLPfiy.gif">
</p>


<a id='section03'></a>
