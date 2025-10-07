# 🎨 Exercise 2: Creating Mappings for Archaeological Excavations

In this exercise, you will learn how to design **schema mappings** about archaeological excavations using CIDOC CRM and its extensions.
The goal is to understand the basic concepts behind schema mapping and to become familiar with the **3M mapping editor** and the **X3ML language**.

--- 

## 🗂️ Dataset Overview

The provided sample dataset consists of one file:

- [archaeological_excavations.xml](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise3/x3ml/source%20files/archaeological_excavations.xml): contains information about archaeological excavations 

--- 

## ⚙️ Instructions

You will create a new schema mapping project by including the provided XML dataset as source data. 
Moreover, you will have to add three different target schemata 
1. CIDOC CRM (V 7.1.1) 
2. CRMarchaeo (V 2.1) 
3. CRMsci (V 2.0)

To facilitate you with the schema mappings, you are given the conceptual model that you should adopt. 
It comprises of classes and properties from the three different target schemata you selected in the previous step. 
Your task is to associate the corresponding parts of the source input file to classes and properties of the target schemata. 
The conceptual map is shown in [Appendix A](#Appendix-A---Conceptual-Map). 

If you need some extra hints, you can find the actual mappings of particular elements of the source input schema, 
to the classes shown in the conceptual map. These mappings are described in [Appendix B](#Appendix-B---Source-Data-Elements-Mappings).  

### Appendix A - Conceptual Map

![map.jpg](https://github.com/ymark/X3ML-Tutorial/blob/main/exercises/exercise2/images/map.jpg)

**namespaces used**

- `crm: http://www.cidoc-crm.org/cidoc-crm/`
- `crmarch: http://www.ics.forth.gr/isl/CRMarchaeo/`
- `crmsci: http://www.cidoc-crm.org/extensions/crmsci/`


### Appendix B - Source Data Elements Mappings

| Element (source data) | Target Class |
|---|---|
|`test`|`test`|
