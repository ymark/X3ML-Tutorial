# 🎨 Exercise 1: Creating Mappings for Paintings and Painters

In this first exercise, you will learn how to design **schema mappings** that connect data about *paintings* and *painters* using CIDOC CRM Ontology.
The goal is to understand the basic concepts behind schema mapping and to become familiar with the **3M mapping editor** and the **X3ML language**.

--- 

## 🗂️ Dataset Overview

The provided sample dataset consists of two files:

- [paintings.xml](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/x3ml/source%20files/paintings.xml): contains information about paintings 
- [painters.xml](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/x3ml/source%20files/painters.xml): contains information about painters

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
6. Click Finish (below you can see a summary of the information that is needed for creating the project in 3M Editor- you should have something similar)

![3m-2.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-2.png)

### Step3. Define schema mappings

After creating your schema mapping project, you can start defining your schema mappings. 
To do so, you have to find and open the schema mapping project you created earlier. 
Find it and click on Open (*hint: you can search for it using the project name you provided during the previous step*).
After opening the project, you will be notified about the data resources of your project 
(i.e. source input files and target schema files). Unless you want to update them (there is no need to do so if you followed precisely the previous step) 
click on the 'SAVE & CLOSE' button found at the end of the page.

To facilitate you with the schema mappings, you are given the conceptual model that you should adopt. 
It comprises classes and properties from the three different target schemata you selected in the previous step. 
Your task is to associate the corresponding parts of the source input file with classes and properties of the target schemata. 
The conceptual map is shown in [Appendix A](#Appendix-A---Conceptual-Map). 

If you need some extra hints, you can find the actual mappings of particular elements of the source input schema to the classes shown in the conceptual map. 
These mappings are described in [Appendix B](#Appendix-B---Source-Data-Elements-Mappings).  

Below you can find details and instructions for creating a single mapping (i.e. the domain of a mapping and a link). 
You can adopt those mappings and continue with the rest of them accordingly. 

### Step3.1. Define the domain of a schema mapping

Here we will demonstrate how to initiate schema mappings by creating a mapping and adding its domain part. 
The domain describes how a key entity is mapped between the source schema and the target ontologies and is used as an anchor for connecting all the mappings that will be described in the links subsequently.
In this example, we will describe how different paintings (element `painting` in the source data will be mapped as instances of the class `E22_Human-Made_Object` from CIDOC CRM.
You have to do the following: 

1. Select the first mapping (Mapping #1)
2. Select the Domain
3. In the text field with the name 'Source Node', start typing the element name 'painting'. You will notice that the source analyze will propose the actual XPATH expression 
of the corresponding element from the source schemata (i.e. ```/root/painting```)
4. In the text field with name 'Target Entity', start typing the name of the target class (i.e. ``````). The system will propose the classes that were found from 
the target schemata as you type. 
In the end, the domain part of your first mapping should look like the following image.

![3m-3.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-3.png)

### Step3.2. Define the link of the schema mapping

Here, we will demonstrate the definition of a first link; more specifically, we will show visually how to specify that
`title` elements from the source data will be mapped as instances of the
class ```E35_Title``` from CIDOC CRM. 
Since we also want to associate this instance with its corresponding painting (which is already defined in the domain part),
we have to specify how these two instances are connected.
According to the conceptual map (that is given in [Appendix A](#Appendix-A---Conceptual-Map), these instances are connected using the property ```P102_has_title``` from CIDOC CRM.
To define the mapping for this link, do the following: 
1. Click on 'Add New Link' button
2. Click on 'Source Relation' found under Link #1 (of mapping #1) 
3. In the text field with name ‘Source Relation’ start typing the name of the element we want to map (i.e. `title`). You will notice that the source analyzer already provide the actual XPATH of those elements from the source data, as you type. 
4. Make sure that the desired element name (i.e. `title`), appears both under ‘Source Relation’ and ‘Source Node’ 
5. In the text field with name ‘Target Relation’ start typing the name of the relation we want to use from the target ontologies (i.e. `P102_has_title`) 
6. In the text field with name ‘Target Entity’ start typing the name of the class we want to use from the target ontologies (i.e. `E35_Title`) 

In the end the first link of the mapping should look like the following

![3m-4.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-4.png)

### Step4. Definition of URI generators

In this step we will demonstrate how URIs are created.
We will demonstrate how to do it for instances of the class `E22_Human-Made_Object` (it is the domain of the first mapping). 
To do that follow the steps below: 

1. Click on Mapping #1 (or wherever mappings for class `E22_Human-Made_Object` are)
2. Click on the Domain
3. Under the 'Target Entity' (where the class `E22_Human-Made_Object` is declared), click on 'GENERATOR'.
4. A pop-up menu will appear. Select 'LocalTermUri' from the available generators.
5. Under 'Argument #1: hierarchy' select as type 'Constant', and in the text field below (with name 'Value') type `painting`
6. Under 'Argument #2: term' select as type 'Xpath', and in the text field below (with name 'Select or add your own XPath') start typing `id`. You will notice that the system will provide you with all the valid XPATH expressions you could use for picking information from the source data. Select the following: `id/text()`
7. If the namespace prefix is empty, define one.
The generator should like the following

![3m-5.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-5.png)

Click 'Save Instance Generator & Namespace'. 
What we did is that we asked for each painting element from the source data, to create an instance of the class 'E22_Human-Made_Object', and the URI of that instance should be compsed of three parts:

* the prefix: `http://www.example.com/resource`
* a constant value: `painting`
* the value of each painting collected from the element `id`

Eventually, this will create URIs of the form `http://www.example.com/resource/painting/p-1`

### Step5. Define label generators

In this step, we will create the label generators. 
We will demonstrate how we will generate a label for the instances of the class 'E22_Human-Made_Object`.
To define them, do the following: 
1. Click on Mapping #1 (or wherever mappings for class 'E22_Human-Made_Object` are) 
2. Click on the Domain part 
3. Under the ‘Target Entity’ (where the class 'E22_Human-Made_Object` is declared), click on ‘GENERATOR’ 
4. Click on the LABEL tab (found on the upper menu bar of the pop-up window) 
5. Click on the '+' symbol to add a new label generator 
6. Select ‘CompositeLabel’ 
7. Under 'Argument #1: term1', select as type 'Constant', and in the text below (with name 'Value') type `Painting with title:`
8. Under 'Argument #2: term2', select as type 'Xpath', and in the text field with name 'Select or add your own XPath', start typing `title`. You will notice that the system will provide you with all the valid XPATH expressions you could use for picking information from the source data. Select the following: `title/text()`. Leave the 'Argument #3' empty (it is an optional argument that is used for declaring the language tag of the label).

![3m-6.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-6.png)

Click 'Save Label Generator' and close the pop-up window with the generators. This label generator will add a label for all the instances of the class 'E22_Human-Made_Object',
the textual contents of the corresponding element with name title. So practically, the instance with URI `http://www.example.com/resource/painting/p-1` will have as `rdfs:label` `Painting with title: Self-Portrait as a Painter`.  

### Step6. Transform Data

While defining your URI and label generators, you can also transform the provided source data and see the results in different serializations. 
To do that, you have to click the button 'Produce RDF', found at the bottom of your project editor. 
This will transform your data according to your schema mappings and the generators that are defined so far. 
You can also change the output format by selecting alternative serializations (i.e. Turtle, N-Triple, TriG). 

![3m-7.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-7.png)

### Step7. Visualize transformed data 

You can also see the transformed data visually, using RDF Visualizer, a tool that is embedded in 3M Editor, and provides features for exploring RDF datasets. 
To see your transformed data visually, do the following:  

1. Click on the button 'View in the RDF Visualizer', found at the bottom of your project screen 
2. Pick a class of interest (select the instances of which class would you like to visualize).  Select 'E22_Human-Made_Object` (the actual URI is `http://www.cidoc-crm.org/cidoc-crm/E22_Human-Made_Object`) 
3. Select one of the instances that appear (all of them are instances of the selected class)
4. Click 'Open in RDF Visualizer'
5. See the transformed data and browse accordingly 

![3m-8.png](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/3m-8.png)

### Appendix A - Conceptual Map

![map.jpg](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise1/images/map.jpg)

### Appendix B - Source Data Elements Mappings

| Element (source data) | Target Class |
|---|---|
|`/root/painting`|`crm:`|
|`/root/painting/title`|`crm:E35_Title`|
|`/root/painting/painter_id`|`crm:E21_Person`|
|`/root/painting/creation_date`|`crm:E52_Time-Span`|
|`/root/painter`|`crm:E21_Person`|
|`/root/painter/id`|`crm:E42_Identifier`|
|`/root/painter/ulan`|`crm:E42_Identifier`|

