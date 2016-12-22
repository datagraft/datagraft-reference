---
layout: page
title: Documentation
permalink: /documentation/
weight: 2
---
[Download pdf](/static/images/documentation/DataGraft.pdf)


1. [Data transformations](#data_transformations)
2. [Data pages](#data_pages)
3. [Exploring public transformations](#explore)
3. [User registration](#user_registration)
4. [Dashboard](#dashboard)
5. [The workflow overview](#workflow) 
6. [Publishing data](#publish)
7. [Data cleaning and transformation](#transform)
   * [Transformation metadata](#transform_meta)
   * [Transformation preview](#transform_preview)
   * [Constructing transformation pipeline](#transform_pipeline)
      * [Make Dataset](#make_dataset)      
      * [Reshape Dataset](#melt)      
      * [Add Columns](#add_columns)
      * [Take/Drop Columns](#columns)            
      * [Derive Colunm](#derive_column)      
      * [Map Columns](#mapc)      
      * [Rename Columns](#rename_columns)      
      * [Split Column](#split)      
      * [Take/Drop Rows](#rows)      
      * [Filter Rows](#grep)      
   * [Defining auxiliary functions](#customfuns)      
      * [Creating and Editing Custom Utility Functions](#utility)      
      * [Creating String Transformation Functions through Graphical Interface](#utility_string)
      * [Creating and Editing Prefixers](#prefixers)
   * [Building RDF mapping](#rdf)      
   * [Executing transformation](#apply)      
8. [Data visualization portal](#visual)
   * [Create visualization portal](#setup)
   * [Configure widget](#configure)
      * [Tabular view](#tabular)
      * [Line chart](#linechart)
      * [Bar chart](#barchart)
      * [Pie chart](#piechart)
      * [Scatter chart](#scatterchart)
      * [Map](#map)


This user guide describes a core functionality of the service and provides you with detailed step-by-step explanation of data publishing and transformation process with help of DataGraft portal. The most demonstrable way to get an overview of what can be done with help of DataGraft platform is to explore data pages and data transformations that other users of this platform chose to share. You can do it here [https://datagraft.net/pages/catalogs/](https://datagraft.net/pages/catalogs/) (sign in is required). The two terms mentioned above, **data pages** and **data transformations**, are two main concepts you work with while using DataGraft platform, therefore it may be useful to understand what each of them means in a context of the service. 




### <a name="data_transformations"></a>Data transformations
 Before publishing data, in most cases you will need to transform the original dataset -- clean messy data, remove unnecessary information, probably add some new data fields and sometimes convert tabular data to RDF. This sequence of operations you perform on your data to convert it to desirable form is called **data transformation**. The greatest thing about data transformations in DataGraft platform is that you may modify existing transformations, share them with other users, reuse them repeatedly on other datasets  and create new transformations by extending ones that you or other users created and shared(fork transformations).

![Transformations in DataGraft](/static/images/documentation/transf.jpg)


Transformations have some properties including transformation name, description, owner and public/private property. They are defined on a data transformation creation stage (see [Data cleaning and transformation](#transform) section) and stored as transformation metadata.

You can see the transformation metadata and get transformation details including pipeline overview, rdf mapping and clojure code if  you click on a transformation name in the list of [public](#explore) or [your](#dashboard) transformations. This may help you to get an understanding of what input data does this transformation require and the way this data is cleaned and transformed.

![Read-only preview of transformation](/static/images/documentation/readonly.png)

Transformations in this view are shown in read-only mode. If you wish to make changes to transformation please click <span style="color:blue; font-family:Georgia; font-size:18pt;">"Edit"</span> button for transformations that you own or <span style="color:blue; font-family:Georgia; font-size:18pt;">"Fork"</span> button to copy and edit a public transformation.

For further information on how transformations can be created and used on your data please refer to the  [Data cleaning and transformation](#transform) section.

### <a name="data_pages"></a>Data pages
Another type of asset that users may create and share in DataGraft is **data page**. Data pages contain cleaned and transformed data you want to publish. As well as data transformations, data pages are stored with some metadata, including data page name; short description; keywords, describing a data page; owner; creation date and public/private property (see [Publishing data](#publish) section). The latter is defined by data page owner and specifies whether this data page can be explored by other users of a platform or not. 

<a name="datapagemeta"></a>![Data page properties](/static/images/documentation/datapagemeta.png)

Users that have access to the data page (i.e. just owners in case of private pages and everyone else for public pages) can locally download information associated with a data page in a raw tabular format by pressing <span style="color:blue; font-family:Georgia; font-size:18pt;">"Export row data"</span> button; or as RDF by pressing <span style="color:blue; font-family:Georgia; font-size:18pt;">"Export RDF data"</span>. The list of supported RDF formats includes RDF/XML(.rdf), n-triple(.nt), turtle(.ttl), n3(.n3), nquads(.nq), RDF/JSON(.rj).

Data pages containing RDF also allow you to perform [SPARQL](http://www.w3.org/TR/sparql11-query/) querying on data they contain.  The example of such query and selection results are shown below.

![Export RDF data](/static/images/documentation/sparql.png)

In addition, data pages may be provided with data visualizations. To see the details on data visualizations refer to[Data visualizations](#visual) section.

### <a name="explore"></a>Exploring public transformations

To explore data pages and data transformations created by other users switch to the  <span style="color:blue; font-family:Georgia; font-size:18pt;">"Explore"</span> tab. Here you can see a list of public assets. You may receive basic information about any public data page or data transformation by clicking its name. If in a process of exploring data transformation you find it to be suitable for your needs, you can apply it to your data directly from the explore view. To do so, you just drag and drop your datafile in the white frame labeled "Create data page". In this way you create a new datapage, but the transformation itself is not added to the list of your assets. If you want to make some changes to the transformation before you use it or just find it interesting and want to explore it in detail, use <span style="color:blue; font-family:Georgia; font-size:18pt;">"Fork transformation"</span> button. The transformation thus will be copied to the list of your transformations.  


![Explore transformation](/static/images/documentation/exploretransformation1.png)



### <a name="user_registration"></a>User Registration
In order to use public data pages and transformations or create your assets through a platform, you should first sign up for DataGraft account. After registration you are automatically redirected to the data page creation service, from where you may start a process of creating your first data page. This process is described in detail in section [Publishing data](#publish) . After you have registered you can change your profile settings by clicking on the user name in top right corner of the website and choosing <span style="color:blue; font-family:Georgia; font-size:18pt;">"My account"</span> menu item.

###	 <a name="dashboard"></a>Dashboard
User dashboard helps to manage data pages and data transformations created by user.  The dashboard view gives you an overview of data pages and transformations you have created. From here you can search through your assets, delete them, edit their properties; fork and execute transformations and download data associated with data pages.

![Catalogue of your data pages and data transformations](/static/images/documentation/dashboardcatalog.png)

##  <a name="workflow"></a>The workflow overview

There are a lot of things that can be done with help of DataGraft portal. To give you a general overview of DataGraft functionality here is a summary of possible scenarios 


![Workflows](/static/images/documentation/workflows.jpg)

First, if you are interested in publishing your data in form of Linked Data and already have its RDF representation, you can simply upload it to the platform and create a data page.

If data you are working with is in tabular format, there are more alternatives. First one is creating data page from raw tabular data. It is as simple process as creating data page from RDF data and can be done just in few clicks (see [Publish data](#publish) for details). 
In case when your tabular data needs to go through some transformations, you can create data transformation and apply it to data. This may include dataset modification, data conversion from tabular to RDF form or both these procedures in one transformation. If all that you want is to transform data, on this stage you can download processed data to your computer, either in tabular or in linked data form. Alternatively you may go further and publish transformed data as a data page.

## <a name="video"></a>Grafterizer workflow demonstration

The following video demonstrates how Grafterizer can be used to clean and transform tabular data.

<iframe width="680" height="382" src="https://www.youtube.com/embed/PMim5BNqUag" frameborder="0" allowfullscreen></iframe>

##  <a name="publish"></a>Publishing data



 
Publishing data with help of DataGraft platform is a rather simple process. You can create a data page from several different points. You may start by switching to a <span style="color:blue; font-family:Georgia; font-size:18pt;">"Publish"</span> tab in a main menu. The first thing you do when creating a data page this way is uploading data. To do so, you just drop your dataset file in a raw CSV or RDF format in a white frame under "Upload your data" label. 
![Upload data](/static/images/documentation/upload.png)

After data is succesfully uploaded (this is indicated by a green mark in the top right corner of a file icon) you have several options:

1. Create data page from a raw data without applying any transformation on it.
2. Transform your data before creating a data page. This in turn can be done in two ways	
   1. By creating a new transformation to use on your data
   2. By applying an existing transformation to your data

	
	
Let's go through the most simple scenario by choosing the first alternative. To do this you just click <span style="color:blue; font-family:Georgia; font-size:18pt;">"Publish"</span> button. This automatically takes you to the next page where you specify data page properties(see [Data page properties](#datapagemeta)). After everything is in order, you simply click  <span style="color:blue; font-family:Georgia; font-size:18pt;">"Publish"</span>. And that's it, you have just created your very first data page. Now you (and other users in case if you defined this data page as public) have access to the data page, are able to download associated data, add more information and features to the created asset.


However, in most cases you still need to process your data before publishing it. In this case you should use the transformation service. By clicking  <span style="color:blue; font-family:Georgia; font-size:18pt;">"Create using new transformation"</span> button you may start transforming your data. Details on how data transformations are created are given in Section [Data cleaning and transformation](#transform).


##  <a name="transform"></a>Data cleaning and transformation
This section explains how tabular data is transformed in DataGraft platform and gives you the best strategies for data transformation.

At the basis of DataGraft data transformations there lies a [Grafter DSL](http://grafter.org/about/index.html) (Domain Specific Language), which in its turn is implemented in Clojure. Therefore, to take maximum advantage of the service, one should be acquainted with mentioned languages. However number of transformations, depending on their complexity, can be done through intuitive and user-friendly GUI without any coding.

There are several ways you can create a transformation on DataGraft. The first option is to go to the Transform tab and click the plus icon in the right bottom corner to create a new transformation. Please note, that in this case created transformation will not appear in a list of your transformations unless you press the save button explicitly. Another option is create a transformation as a copy of existing transformation from the list of your transformations or public transformations created by other users(fork transformation). Forking a transformation doesn't save a new transformation automatically as well. There is also a third option for creating a new transformation: after you have uploaded a tabular data you have an option of creating a datapage using  "Create using new transformation" button (more details can be found in [Publishing data](#publish) section). This action leads to creating and saving a new transformation automatically.

###  <a name="transform_meta"></a>Transformation metadata
The first tab seen in the transformation creation window is "Metadata". Here user defines transformation title and gives a short description of how this transformation processes targeted data. If you wish to share transformation, it is possible to expose it as public. In this case other platform users will be able to explore and use given transformation.


After describing metadata, you may save transformation by clicking “Save” button ![Save transformation](/static/images/documentation/save.png) in the top right corner. The transformation may be as well saved later at any moment.



![Transformation metadata](/static/images/documentation/transformationmeta.png)

###  <a name="transform_preview"></a>Transformation Preview

After your transformation was saved, in the bottom right corner you may see this icon: ![Apply to dataset](/static/images/documentation/open.png). By clicking on it you may immediately apply transformation being created to target data. This may be whether distribution already uploaded to a platform, or alternatively you may upload a new file. For the first option use button depicted as ![Load an existing distribution](/static/images/documentation/applytoexisting.png), and for the second -- this one ![Upload file](/static/images/documentation/uploadnew.png). In this way you are able to see instant effect of transformation on your data in the preview area. 

Preview area is located in the right part of transformation window. You can see two tabs there -- one with the original data and another with changes made through transformation pipeline. Each time you modify a pipeline, the transformation is  applied to the previewed dataset immediately, so you can see the effect of each performed step. You may adjust preview settings to check and evaluate transformation steps you are creating. Thus, it is possible to hide columns and to sort visible data. The changes made through these settings are not part of the data transformation and affect just previewed data. However, at any time you may export tabular data either as it looks in the preview or in a format it has at the current stage of your transformation. 

![Transformation preview](/static/images/documentation/preview.png)

###  <a name="transform_pipeline"></a>Constructing Transformation Pipeline

Data cleaning and transformation in DataGraft platform is performed with help of a “pipeline” concept.  To begin with, each single transformation step is defined as a pipe – a function that performs simple data conversion on its input. The great fact about these functions is that they may be combined together in a such way, that the output of one pipe acts as an input for another. Obviously, the input/output data, that travels through this pipeline is dataset being transformed. This way of composing operations gives a great flexibility and allows to perform rather complex data conversions.

The first implicit step of every transformation pipeline is getting the very first pipeline input. Therefore, each transformation starts from reading a dataset from an uploaded file. However, you do not need to include this step into your pipeline manually, since this action is performed automatically for each transformation.


To add a first transformation step click the ![Add step](/static/images/documentation/add.png) button next to the pipeline

![Pipeline view](/static/images/documentation/addpipefunction.png)


Now you can see the list of functions you may use to modify uploaded dataset. Available functions are logically grouped according to the type of effect they have on the data. Consequently, OPERATIONS ON COLUMNS add, remove or modify dataset columns, while OPERATIONS ON ROWS extract certain rows from a dataset based on row numbers or some condition that user defines. Operations "Make dataset" and "Reshape dataset" affect the entire dataset.


![Available function list](/static/images/documentation/functionlist.png)

 For each operation you can see a short documentation with simple illustrated example by clicking "show/hide documentation" button. For every pipeline function you create you may leave a short description note in the "Comment" field. This information helps you and other users of your transformation to understand operations that are performed here. If you ignore this field, the note will be created automatically based on function parameters you have specified.
 
![Common operations for all pipe functions](/static/images/documentation/pipefunccommon1.png)

Once you have added a new function to the pipeline, it will instantly appear in the pipeline view. You are free to change function parameters any time you need it by simply clicking on the correspondent function icon. To get a short information about the actions performed by this function you may just hover mouse pointer over its name. In many cases function order significantly affects the transformation result. It is very simple to change this order by just dragging function icons along the pipeline. To remove a function click ![Remove function](/static/images/documentation/minus.png)  button next to the function you would like to remove.
 
In DataGraft you are able to see the partial preview of the transformation on each step. Last option makes it possible to see how the transformed data looks like for every stage of transformation.

![Partial preview](/static/images/documentation/partial.png)

 The following sections provide you with detailed guidelines for each function usage.

  
####  <a name="make_dataset"></a>Make Dataset 

As its name suggests "Make dataset" operation creates new dataset from its input. If you leave all parameter fields blank new dataset will be created from all the input columns with column names given as a simple alphabetic sequence. By checking "move first row to header" option you get all the column names from the first row. The first row will be removed from your dataset.  You may as well specify column names you wish to see in a new dataset or fetch first n columns.


####  <a name="melt"></a>Reshape Dataset
Reshape dataset "melts" given dataset in a such way, that each row of the new dataset represents a unique combination of variables and values for the given column array. The best way to explain this function is through an example. 

![Example](/static/images/documentation/bulb.png)  **_Example:_**



*Let's consider the case, when dataset you are interested in is represented by some sensor measurement data:*

![Original measurement data](/static/images/documentation/ex1_1.png)


*Now you may want to put each measurement into a different row. To do so, you reshape your dataset on fields Date and Time. In this way combination of date and time will be considered as unique id key, while other data will be bound to this key as map of variables and values*

![Reshaped measurement data](/static/images/documentation/ex1_4.png)




####  <a name="add_columns"></a>Add Columns

The "Add columns"  results in adding a new column(s) to a given dataset. To add a new column you should specify column name and a value for a new column. This value will be copied into every row within the dataset. Cells in new column may contain some custom values like current date, dataset filename, row index or custom Clojure code. Note that the "Expression" field is prioritized, in other words, if you define both value and expression, only expression will be used to get a value for a new column.
You are able to add as many columns as you need with one operation. To add one more column simply click "Add more columns"

![Add Columns function](/static/images/documentation/addcolumnf1.png)


####  <a name="columns"></a>Take/Drop Columns

The "Take/Drop Columns" function narrows given dataset. You may explicitly define columns you wish to see in a dataset by listing their names, get first n columns or remove unnecessary columns from a dataset. In a second case, the dataset will be narrowed to specified number of columns with their names assigned as alphabetical sequence ("A","B","C" etc.). If more than 26 columns are fetched, column names will count "AA", "AB", "AC" ... "BA", "BB", "BC" etc.

![Take/Drop Columns function](/static/images/documentation/columns1.png)

####  <a name="derive_column"></a>Derive Column

This function creates a new column in a dataset by applying some transformation to existing column (or columns). To use this function you should specify a name for a new column, define one or several columns you are going to use to obtain new value and specify a function you apply to them. This function can be chosen from a drop-down list, which contains some standard functions and custom utility functions. For your convenience these functions are grouped together based on the type of operation they perform. 

If you think that functionality ordered by standard provided functions is not enough to build your transformation, you may define custom utility functions by yourself using Clojure code (see [Defining Auxiliary Functions](#customfuns) section). 

![Tip](/static/images/documentation/magic.png)**_Tips and tricks:_**


*One powerful feature of derive-column and similar pipeline functions is possibility to combine functions you apply to columns in the same way you combine functions in pipelines. Essentially, these are pipelines inside your dataset manipulation pipeline. To add one more "internal" function into your pipeline function, click <span style="color:blue; font-family:Georgia; font-size:18pt;">"Compose with"</span>  button. Note, that function order is significant in this case. Functions are composed as they appear from top to down. To remove a function from composition pipeline click trash icon  ![Remove function](/static/images/documentation/trash.png) next to the function you wish to delete.*


Some of the functions may expect input parameters in addition to columns, they will operate on. If this is the case, you may specify such a parameter by pressing ![add parameter](/static/images/documentation/plus.png) icon and entering parameter in a field that appears.



![Example](/static/images/documentation/bulb.png)  **_Example:_**

*To demonstrate a way in which functions with parameters can be used in DataGraft, let's consider one of such functions --**join-with**. This function joins collection of values into one string using custom separator specified as function parameter. Using this function inside derive-column pipeline function you may derive a new column as a result of merging several other columns. For example, you may have several fields describing address in your dataset and wish to obtain a column containing full address by joining elements using comma as separator. Original dataset looks as follows:*

![Original  data](/static/images/documentation/join_with_1.png)

*Now you may specify the way you wish address fields to be joined. For this define a name for a column, that will hold obtained address, choose columns to compose address from in necessary order, choose function join-with from a list of function and specify a desired separator as its parameter*

![Parameters](/static/images/documentation/join_with_2.png)

*After this function is applied to your dataset you will get a new column called address containing joined values:*

![Result](/static/images/documentation/join_with_3.png)

####  <a name="mapc"></a>Map Columns

This method allows you to apply some transformation to column and put the modified value back to the same column. In parameter list you must specify a column you wish to change and a function that will be used to perform this transformation. You may add as many column-function pairs as you need. 

![Tip](/static/images/documentation/magic.png)**_Tips and tricks:_**

*As you probably noticed, the function that appears by default each time you add a new mapping pair is string-literal. This function belongs to the group "CONVERT DATATYPE" and plays an important role in tabular-to-RDF conversion.*

*Whenever you need to treat a column value as a constant literal node, you should first define, which datatype it represents. String-literal will mark  column as one having datatype "string". Other functions used for defining data type are integer-literal and double-literal.*

####  <a name="rename_columns"></a>Rename Columns

This operation allows you to rename columns in the dataset. To get new names for columns you may either apply function (or function pipeline) to current column names or assign mapping from old to new column names directly.

![Rename Columns function](/static/images/documentation/renamecolumns1.png)


![Tip](/static/images/documentation/magic.png)**_Tips and tricks:_**

*You may see the function named "keyword" assigned by default as a function used to transform column names. This is done because the column names in Grafter DSL should be treated as keywords -- special symbolic identifiers used in Clojure language. Having this function as a first one in a list of functions used for column names conversion guarantees column names will be recognized as valid keywords.* 


####  <a name="split"></a>Split Column

This operation allows to split column on some separator. The column is splitted once, leaving substring obtained as original text before first instance of the separator in the source column and copying text after separator into a new column. The separator itself is extracted from text. Name of the new column is optional.


####  <a name="rows"></a>Take/Drop Rows
This function allows you to take or drop first n rows in a given dataset. Use switch Take rows/Drop rows at the top of the function parameter list to choose between these two options

####  <a name="grep"></a>Filter Rows
This method filters rows in the dataset for matches. This is a rather flexible filtering tool that allows you to filter your data in several different ways.

First field in in "Filter Dataset" parameter list specifies whether filter will be applied to specific column(s) or to all columns in dataset. For latter option just leave this field empty and matching will be performed for each column.

To perform actual data filtering you have several options.

First, it is possible to select only rows containing specified text. For this you enter the text in the field marked as "Text to match". By default this text is treated as case-sensitive. To perform a case insensitive filtering check the box "ignore case" next to the text field.

You may as well filter dataset with help of regular expressions. By pressing ![Regular expressions tutorial](/static/images/documentation/tutorial.png) button next to the "Regular expression" field  you will get the short quick start tutorial for pattern usage.

Finally, you may filter dataset by applying standard predicate or user-defined utility functions to columns. Note, that the function (or combination of functions) used for data filtering should return a true/false expression.

The priority of listed option is defined as they appear - from top to down: if "Text to match" field is specified, other fields are ignored, if "Text to match" is ignored, but "Regular expression" is defined -- this one will be used to filter your dataset ignoring functions below (if specified any).


###  <a name="customfuns"></a>Defining Auxiliary Functions 

Some complex transformations cannot be done with help of operations described above. In this case you may need to define your own pipeline functions. This can be done with the help of "Custom code" option using Clojure language

####  <a name="utility"></a>Creating and Editing Custom Utility Functions

Creating utility functions for transformations is a great way to encapsulate the logic of data modifications, thus making them independent of data they are applied to. For instance, if to convert data in several dataset columns you use the same formula, you can define a function, that performs all the necessary calculations based on its input parameters and call it any time and on any data you need. 

To create your custom function use <span style="color:blue; font-family:Georgia; font-size:18pt;">"Edit utility functions"</span> button. In the window that opens you can see the list of available functions at the left side and code editor at the right side.

![Create custom utility function](/static/images/documentation/createcustom.png)


Each function can be removed by pressing ![Remove custom utility function](/static/images/documentation/minus.png) icon next to the function name. New functions are added by a plus icon in the toolbox below function list.

Immediately after you have created a utility function you may start using it as a parameter in pipeline functions.


![Tip](/static/images/documentation/magic.png)**_Tips and tricks:_**

*If you create a function having a dataset as an input parameter, it is possible to make it a part of the transformation pipeline directly. You may add this function to a pipeline by choosing "Custom function" option from a pipeline function list.*


####  <a name="utility_string"></a>Creating String Transformation Functions through Graphical Interface

However to specify text transformations you may need to perform on your data, you cans define a new function in a more user-friendly way. To do so press ![Create text transformation function](/static/images/documentation/createstring.png)  button in the same window, that is used for creating custom utility functions. Now you can see the dialog, where  you specify transformations you want to perform on text values. All modifications you define are instantly  demonstrated with help of sample text in the right bottom corner.

![Create text transformation function](/static/images/documentation/createstringwin.png)


####  <a name="prefixers"></a>Creating and Editing Prefixers
One special type of utility functions you may define is **prefixer** -- function that expects one argument and adds some prefix to this argument in a such way, that the result represents an URI. This is something you may need in constructing RDF mapping part. If all you need is just constructing URI nodes by adding the same type of prefix to all values in a column, you should define prefixers in "Edit RDF mapping prefixes" dialog (see [Building RDF Mapping](#rdf) section). However, if you need to add some logic in assigning prefixes depending on column values, you should define prefixer functions here in pipeline view. 
You may create and edit prefixers in the "Edit prefixers" window. To see this window  press <span style="color:blue; font-family:Georgia; font-size:18pt;">"Edit prefixers"</span> button in the pipeline view. Here you can see the list of all prefixers you created for current transformation. You may add a new prefixer by specifying its name and URI and pressing <span style="color:blue; font-family:Georgia; font-size:18pt;">"Add prefixer"</span>  button. Created prefixer will instantly appear in the list of prefixers above. It is possible as well to create prefixer by adding some string to the existing one. In this case select a prefixer you wish to use as a base one, enter new prefixer name and string value and press <span style="color:blue; font-family:Georgia; font-size:18pt;">"Add prefixer from selected"</span>. Now, if the base prefixer is changed, changes will be as well applied to the child prefixers. To remove prefixers select all prefixers you wish to remove and press <span style="color:blue; font-family:Georgia; font-size:18pt;">"Remove prefixer"</span>.

###  <a name="rdf"></a>Building RDF Mapping 

One great method to publish your data on the Web is to use Linked Data for it. You can read about all the opportunities you get with linked data here: [http://www.w3.org/standards/semanticweb/data](http://www.w3.org/standards/semanticweb/data). If you've chosen to convert your data in a format of linked data, the first thing you need to do is to build an RDF map, that will determine way of getting linked data nodes from tabular data.

When tabular data is converted to a desirable format, you can start creating RDF mappings. In the process of creating RDF skeleton you can immediately see a clear visualization of nodes and corresponding relations.

To start creating RDF mapping of your dataset use switch "Map tabular data to RDF". 
The first step here  would be to specify the base graph URI. To create and edit prefixes you are going to need for the RDF generation use "Edit RDF prefixes button". By pressing it you open a dialog, where you can as well see RDF vocabularies available by default.

Now you can start to create, edit and remove RDF nodes and their properties. The three groups of nodes that can be created here are URI nodes, literal nodes and blank nodes. To construct a URI node both as one obtained from dataset column and as some constant URI, you need to define some prefix. Prefixes are separated from values they complement with semicolon. Note, that dataset columns may be converted to the URI form during the tabular transformation step. In this case you don't have to specify prefixers to make them URI nodes in RDF schema. If you, however try to create a URI node from data column that is not recognized as a valid URI, and do not assign any prefix value to  this column, it would be automatically converted to column literal node. Literal nodes are represented just by their value in the resulted RDF file. An example  of RDF mapping skeleton is shown below.

![RDF mapping skeleton](/static/images/documentation/rdfexample.png)

###  <a name="rdf"></a>Executing transformation 



After you've completed creating transformation either with or without RDF mapping part you may apply transformation to your data right in the transformation view. To do so press ![Apply transformation](/static/images/documentation/gear.png) icon. After you did this you can see a dialog, where you have few options:

 
![Apply transformation](/static/images/documentation/transform.png)

1. Execute and save. By pressing this button you can publish transformed data as a data page 
2. Execute and retreive. By pressing this button you can  download the results locally on your computer as rdf data(n-triples)
3. Download executable. By pressing this button you can  download the executable jar file on your computer. This file can then be used to transform datasets locally instead of in the cloud. The JAR file can be ran by using the command line interface from the location where the file is located as follows:

![jar](/static/images/documentation/jar.png)
 

Alternatively transformations can be executed from the "Dashboard" and "Explore" views as it have been discussed in sections [Dashboard](#dashboard) and [Exploring public transformations](#explore)

###  <a name="visual"></a>Data visualization portal

DataGraft allows publishers to create visualization portals in order to display data in graphical manner. The portal is identified by unique identified, has a title and consist of one or more widgets.
Each widget displayed in portal consist of 4 components: title of the widget, description of the data represented, visualization part, summary. The following image shows how widget looks like on the portal page and what are the four part of it:

![visualization widget](/static/images/documentation/widget.png)

####  <a name="setup"></a>Create visualization portal

The process for creating portal is accomplished by using ‘Setup visualization’ section in edit data page.


![Setup visualization](/static/images/documentation/setup.png)

The ID of the page is unique identifier in DataGraft to identify this portal. The default value is auto generate based on the data page name, but can be changed during edit process. Title property specifies title of the portal web page. Widgets table shows currently configured visualization widgets in the portal. For each widget there is an option to edit ![Edit](/static/images/documentation/edit.png) and delete ![Delete](/static/images/documentation/delete.png). 

Adding new widget to the portal is accomplished using  button. Both edit and add new widget buttons lead you to the configure widget dialog, where you can edit properties of the widget and data subset used to generate visualization.

####  <a name="configure"></a>Configure widget

![Configure widget](/static/images/documentation/configure.png)

The configure widget allows you to specify 4 components of the each widget: title, description, summary and visual component along with the data subset for the visual component. Currently the platform supports the following widgets types: tabular view, line char, bar chart, pie chart, scatter chart, bubble chart, maps. 

Each type is described later in this section.

The query section requires valid SPARQL query which will retrieve data subset from the repository and use this data as a input for the visualization.

There is option to preview how the widget will look like in the configure dialog by using ‘preview’ button.

#####  <a name="tabular"></a>Tabular view

![Tabular view](/static/images/documentation/tabular.png)

Tabular view is the simplest possible view and it shows data as a browsable table, similar to spreadsheet. This view has a pagination control and search capability. View can show any data from any valid SPARQL query.

#####  <a name="linechart"></a>Line chart

![Line chart](/static/images/documentation/linechart.png)

This view presents data as a line chart. View support single or multiple lines on the same chart. This view requires SPARQL query with ‘title’ column, which will be used as an X coordinate and all other columns are treated as numeric values of Y coordinate in the chart. Typical query looks like this:

SELECT ?title ?line_1_values ?line_2_values WHERE { … }



#####  <a name="barchart"></a>Bar chart

![Bar chart](/static/images/documentation/barchart.png)

This view presents data as a bar chart. View support single or multiple bars series on the same chart. This view requires SPARQL query with ‘title’ column, which will be used as an X coordinate and all other columns are treated as numeric values of Y coordinate in the chart. Typical query looks like this:

SELECT ?title ?bar_series_1_values ?bar_series_2_values WHERE { … }

#####  <a name="piechart"></a>Pie chart

![Pie chart](/static/images/documentation/piechart.png)

This view presents data as a pie chart. View support single or multiple pies on the same chart. This view requires SPARQL query with ‘title’ column, which will be used as an X coordinate and all other columns are treated as numeric values of Y coordinate in the chart. Typical query looks like this:

SELECT ?title ?pie_series_1_values ?pie_series_2_values WHERE { … }

#####  <a name="scatterchart"></a>Scatter chart

![Scatter chart](/static/images/documentation/scatterchart.png)

This view presents data as a scatter chart. View support single or multiple series on the same chart. This view requires SPARQL query with ‘title’ column, which will be used as an X coordinate and all other columns are treated as numeric values of Y coordinate in the chart. Typical query looks like this:

SELECT ?title ?series_1_values ?series_2_values WHERE { … }


#####  <a name="map"></a>Map

![Map](/static/images/documentation/map.png)

Map view shows geo aware data on the interactive map. This view support multidimensional data which is shown as a popup on the map location.

This view requires SPARQL query with ‘lat’ and ‘lng’ columns, which will be used as coordinates on the map and title column, which will be used as a title for the location. All other columns are treated as additional metadata for the location. Typical query looks like this:

SELECT ?title ?lat ?lng ?more_data_1 ?more_data_2 WHERE { … }

