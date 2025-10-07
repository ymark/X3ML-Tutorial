# 🎨 Exercise 1: Creating Mappings for Paintings and Painters

In this first exercise, you will learn how to design **schema mappings** that connect data about *paintings* and *painters* using CIDOC CRM Ontology.
The goal is to understand the basic concepts behind schema mapping and to become familiar with the **3M mapping editor** and the **X3ML language**.

--- 

## 🗂️ Dataset Overview

The provided sample dataset consists of two files:

- paintings.xml: contains information about paintings 
- painters.xml: contains information about painters

--- 

## ⚙️ Instructions

### Step1. Use 3M Editor

1. Visit 3M Editor (https://demos.isl.ics.forth.gr/3m/) and log in (if you already have an account) or register (if you do not have an account)
![3m-1](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-1.png)

### Step2. Create a new schema mapping project

Create a new schema mapping project by including the provided XML datasets as source data. The indicative steps for doing so are: 

1. After logging in, click on **Add New**
2. Provide a short title and description of your project
3. Upload the provided XML datasets as source data
4. Select CIDOC CRM (v7.1.1) as a target schema
5. Use the basic generator policy (we will deal with more sophisticated generators later)
6. Click Finish (below you can see a summary of the information that are needed for creating the project in 3M Editor- you should have something similar)

![3m-2.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-2.png)

### Step3. Define schema mappings

After creating your schema mapping project, you can start defining your schema mappings. 
To do so, you have to find and open the schema mapping project you created earlier. 
Find it and click on Open (*hint: you can search for it using the project name you provided during the previous step*).
After opening the project you will be notified about the data resources of your project 
(i.e. source input files and target schema files). Unless you want to update them (there is not need to do so if you followed accurately the previous step) 
click on SAVE & CLOSE button found at the end of the page.

To facilitate you with the schema mappings, you are given the conceptual model that you should adopt. 
It comprises of classes and properties from the three different target schemata you selected in the previous step. 
Your task is to associate the corresponding parts of the source input file to classes and properties of the target schemata. 
The conceptual map is shown in Appendix A. 

If you need some extra hints, you can find the actual mappings of particular elements of the source input schema, to the classes shown in the conceptual map. 
These mappings are described in Appendix B.  

Below you can find details and instructions for creating a single mapping (i.e. the domain of a mapping, and a link). 
You can adopt those mappings and continue with the rest of them accordingly. 

### Step3.1. Define the domain of a schema mapping

Here we will demonstrate how to initiate schema mappings by creating a mapping and adding its domain part. 
The domain is describes how a key entity is mapped between the source schema and the target ontologies and is used as an achor for connecting all the mappings that will be described in the links subsequently.
In this example, we will describe how different paintings (element `painting` in the source data will be mapped as instances of the class ```E22_Human-Made_Object``` from CIDOC CRM.
You have to do the following: 

1. Select the first mapping (Mapping #1)
2. Select the Domain
3. In the text field with name 'Source Node' start typing the element name 'painting'. You will notice that the source analyze will propose the actual XPATH expression 
of the corresponding element from the source schemata (i.e. ```/root/painting```)
4. In the text field with name 'Target Entity' start typing the name of the target class (i.e. ```E22_Human-Made_Object```). The system will propose the classes that were found from 
the target schemata as you type. 
In the end, the domain part of your first mapping should like the following image.

![3m-3.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-3.png)
