---
layout: page
title: Documentation
permalink: /documentation/
weight: 2
---
[Download pdf](/static/images/documentation/DataGraft.pdf)

1. [Components in DataGraft](#datagraft_components)
2. [DataGraft User Dashboard](#datagraft_homepage)
   * [DataGraft Assets](#datagraft_assets)
   * [Public and Private Assets](#public_private)
   * [Browse Assets](#browse_assets) 
   * [Create Assets](#create_assets)
      * [Create File Page](#create_file_page)      
      * [Create SPARQL End Point Page](#create_sparql_end_point_page)      
      * [SPARQL query](#add_sparql_query)   
   * [Versioning](#versioning)
3. [Data cleaning and transformation](#transform)
   * [Transformation metadata](#transform_meta)
   * [Transformation preview](#transform_preview)
   * [Constructing transformation pipeline](#transform_pipeline)
      * [Make Dataset](#make_dataset)   
      * [Group and Aggregate](#group_and_aggregate)
      * [Remove Duplicates](#remove_duplicates)
      * [Reshape Dataset](#melt)      
      * [Sort Dataset](#sort)
      * [Add Columns](#add_columns)
      * [Take/Drop Columns](#columns)            
      * [Derive Colunm](#derive_column)      
      * [Merge Columns](#merge_columns)      
      * [Map Columns](#mapc)      
      * [Rename Columns](#rename_columns)      
      * [Shift Column](#shift)      
      * [Split Column](#split)      
      * [Add Row](#add_row)   
      * [Shift Row](#shift_row)   
      * [Take/Drop Rows](#rows)      
      * [Filter Rows](#grep)      
   * [Defining auxiliary functions](#customfuns)      
      * [Creating and Editing Custom Utility Functions](#utility)      
      * [Creating String Transformation Functions through Graphical Interface](#utility_string)
      * [Creating and Editing Prefixers](#prefixers)
   * [Building RDF mapping](#rdf)      
   * [Executing transformation](#apply_tranformation)
 4. [User management](#user_management)  
   * [Quotas](#quotas) 
   * [API keys](#api_keys)
   * [Authorized applications](#authorized_applications)

## <a name="datagraft_components"></a>Components in DataGraft
DataGraft is a cloud-based service, which provides an integrated web environment for data hosting (linked data and file storage, dataset sharing, data querying) and data transformations (interactively building, modifying, and sharing of repeatable and reusable data transformations). DataGraft provides a user interface that enables user data and account management, user assets cataloguing and dataset and database management.

DataGraft consits of the following components:
* DataGraft portal: The portal serves several functions. Firstly, it provides the web-based front- end that is used by the proDataMarket data publishers. Internally, it implements the data model and provides object-relational mapping between it and the database back-end. It also enables the communication with the database and manages the storage of uploaded files (Docker volume, or Amazon RDS3 in production). Finally, this component implements the connection to the data hosting and access services.
* DataGraft DBMS: This component represents the database management system (PostgreSQL4) for the user data and asset catalogue. Data are stored in a separate volume (Docker volume or Amazon S35 in production).

## <a name="datagraft_homepage"></a>DataGraft User Dashboard
### <a name="datagraft_assets"></a>DataGraft Assets
Users of the DataGraft can operate on four types of assets:
* File pages
* SPARQL endpoints
* Data transformations
* SPARQL queries

File pages contain data files in Excel or delimiter-separated value format and metadata. 
[SPARQL endpoints](http://semanticweb.org/wiki/SPARQL_endpoint.html) are  services that allow user to query a knowledge base with the help of SPARQL queries and return results. 
Data transformations in DataGraft are pipelines of data transformation functions that can be executed on Excel or delimiter-separated data files and produce either CSV file or RDF.
[SPARQL](https://www.w3.org/TR/rdf-sparql-query/) query assets contain the queries to a knowledge base and metadata.

### <a name="public_private"></a>Public and Private Assets
All types of assets can be either private or public. By default all assets created by user are private and can be seen and accessed only by the asset owner. 
Such assets as SPARQL endpoints can be accessed outside DataGraft. In order to query private endpoints user should use [API keys](#api_keys).

User can make own asset available to all DataGraft users by turning on "Public" switch for the asset. Public assets can be used directly or copied as user assets and edited.


### <a name="browse_assets"></a>Browse Assets
The DataGraft home page after user has logged in represents user dashboard. The dashboard contains two tabs that allows users to browse or create assets. The "Browse Assets" tab (see Figure 1) presents a list of available assets (files, SPARQL endpoints, data transformation and queries) and corresponding filter options for the type of assets. Users can also search assets by name and include other users' public assets.

![DataGraft Homepage Browse Assets](/static/images/documentation/datagraft_homepage_browse.png)
<p align="center">Figure 1: DataGraft homepage - browse assets</p>

### <a name="create_assets"></a>Create Assets
The "Create Assets" tab (see Figure 2) enables users to create assets. A step-by-step wizard guides the user in creating a file page, allowing the user to upload a new file or use an existing file, and start the Grafterizer tool to clean and transform the selected files. Similarly, a step-by-step wizard guides the user in creating a SPARQL endpoint page, allowing the user to upload RDF data, provision a SPARQL endpoint for storing and accessing the data, or use Grafterizer to transform a tabular data file.

![DataGraft Homepage Create Assets](/static/images/documentation/datagraft_homepage_create.png)
<p align="center">Figure 2: DataGraft homepage -create assets</p>

The three main functions you can perform under Create Assets are:
* Create File Page
* Create SPARQL End Point Page
* SPARQL query

#### <a name="create_file_page"></a>Create File Page
A file page (see Figure 3) contains information about the file assets such as file name, description, owner, last modified date, upload date, license, download link, file size.
The filestore asset is used for storing and sharing tabular data. The data can be in Excel or delimiter-separated value formats. Administration of metadata and sharing files with other users as public data is provided in the DataGraft GUI.

For creating a filepage, you can either upload a new file or choose an existing file. After you uploaded your own data file or chose an existing file from DataGraft, you may proceed to edit the metadata of the file, as shown in Figure 5. If you choose to **Cleanup and Transform File**, you can refer to [Data cleaning and transformation](#transform) section.

![Create File Page by Uploading New File](/static/images/documentation/1.5create_file_page_uploaded_file0.png)
<p align="center">Figure 3: Create Filepage by uploading a new file</p>

![Create File Page With Existing File](/static/images/documentation/1.4create_file_page_exist_file.png)
<p align="center">Figure 4: Create Filepage by choosing an existing file</p>

![Edit File Metadata](/static/images/documentation/1.6edit_metadata_label.png)
<p align="center">Figure 5: Edit File Metadata</p>

![Finish File Page](/static/images/documentation/1.7finished_file_store0.png)
<p align="center">Figure 6: File Page Completed</p>

#### <a name="create_sparql_end_point_page"></a>Create SPARQL Endpoint Page
Just as creating File Page, you can create a SPARQL Endpoint Page by either uploading a new file or choosing an existing file to transform(Figure 7). 
If you upload data file in Excel or delimiter-separated value format, you will need to transform file to RDF in order to add it to the SPARQL endpoint. The details on how to perform mapping to RDF you can find in [Building RDF mapping](#rdf) section.
After that, you may proceed to filling in the details of the SPARQL Endpoint (Figure 8).

![Create SPARQL endpoint: Upload or Select a file](/static/images/documentation/create_sparql_endpoint_file.png)
<p align="center">Figure 7: Create SPARQL endpoint: Upload or Select a file</p>

![Add SPARQL endpopint details](/static/images/documentation/add_sparql_endpoint_details_label.png)
<p align="center">Figure 8: Add SPARQL endpopint details</p>

A SPARQL endpoint page contains two tabs. The "Endpoint Info" tab (see Figure 9) displays information such as description, keywords, license, provision date and the size of the data.

![Finish SPARQL Endpoint](/static/images/documentation/endpoint_info_label.png)
<p align="center">Figure 9: SPARQL Endpoint Aage - Endpoint Info</p>

The "Querying" tab (see Figure 10) provides a searchable list of queries (including other public queries). Queries that are linked to this particular endpoint are highlighted. Each query list is presented as an expandable card, where you can click on the query listing to get more details (i.e. the description and the query text). Clicking the "Run" button executes the query on this endpoint and displays the results in a result table. It is also possible to define a new SPARQL query and run in this view.
![Query SPARQL Endpoint](/static/images/documentation/query_sparql_endpoint_label.png)
<p align="center">Figure 10: SPARQL Endpoint Page - Querying</p>

#### <a name="add_sparql_query"></a>SPARQL Query
A query page (see Figure 11) displays information about the query – query textual description, query text, and the SPARQL endpoints that are associated with this query. The user has the option to navigate to the endpoint page or select the endpoint and execute the query. Results are displayed in a results table.

![Query SPARQL Endpoint](/static/images/documentation/sparql_query2.png)
<p align="center">Figure 11: Query Page</p>

![Query SPARQL Endpoint](/static/images/documentation/add_sparql_query_details_label.png)
<p align="center">Figure 12: Add SPARQL Query Details</p>
### <a name="versioning"></a>Versioning
Assets in DataGraft are kept in several versions at the same time. In addition to the current state of the asset, it is possible to browse previous versions of the asset by pressing "Versions" button.
![Browse asset versions](/static/images/documentation/browse_versions.png)
##  <a name="transform"></a>Data cleaning and transformation
This section explains how tabular data is transformed in DataGraft platform and gives you the best strategies for data transformation.

At the basis of DataGraft data transformations there lies a [Grafter DSL](http://grafter.org/about/index.html) (Domain Specific Language), which in its turn is implemented in Clojure. Therefore, to take maximum advantage of the service, one should be acquainted with mentioned languages. However number of transformations, depending on their complexity, can be done through intuitive and user-friendly GUI without any coding.

###  <a name="launching_grafterizer"></a>Launching Grafterizer
After you have uploaded your delimiter-separated value or Excel file or have chosed existing file, you can transform the file with Grafterizer by clicking the **Launch** button.
![Launch Grafterizer](/static/images/documentation/launchgrafterizer.png)
<p align="center">Figure 14: Launch Grafterizer</p>

###  <a name="transform_meta"></a>Transformation metadata
Once you are in Grafterizer, the first tab seen in the transformation creation window is **Metadata**. You are required to fill in the following on the left pane of the transformation creation window: 
* Title (Name of transformation)
* Description (Short description of transformation)
* Add a keyword (Keywords of transformation)

If you wish to share the transformation, it is possible to toggle it as public. If the transformation is public, other users will be able to explore and use that transformation.

After describing metadata, you may save transformation by clicking “Save” button ![Save transformation](/static/images/documentation/save0.png) in the bottom right corner. The transformation will be saved for later.

###  <a name="transform_preview"></a>Transformation Preview
Preview area is located on the right part of transformation window. You can see two tabs there -- one with the original data and another with changes made through transformation pipeline. Each time you modify a pipeline, the transformation is  applied to the previewed dataset immediately, so you can see the effect of each performed step. You may adjust preview settings to check and evaluate transformation steps you are creating. Thus, it is possible to hide columns and to sort visible data. The changes made through these settings are not part of the data transformation and affect just previewed data. However, at any time you may export tabular data either as it looks in the preview or in a format it has at the current stage of your transformation.

![Transformation metadata](/static/images/documentation/metadatatransform.png)
<p align="center">Transformation metadata</p>

###  <a name="transform_pipeline"></a>Constructing Transformation Pipeline

Data cleaning and transformation in DataGraft platform is performed with the help of a “pipeline” concept.  To begin with, each single transformation step is defined as a pipe – a function that performs simple data conversion on its input. The great fact about these functions is that they may be combined together in a such way, that the output of one pipe acts as an input for another. Obviously, the input/output data, that travels through this pipeline is dataset being transformed. This way of composing operations gives a great flexibility and allows to perform rather complex data conversions.

The first implicit step of every transformation pipeline is getting the very first pipeline input. Therefore, each transformation starts from reading a dataset from an uploaded file. However, you do not need to include this step into your pipeline manually, since this action is performed automatically for each transformation.

To add a first transformation step click the ![Add step](/static/images/documentation/add.png) button next to the pipeline

![Pipeline view](/static/images/documentation/addpipefunction.png)
<p align="center">Add pipeline function</p>

Now you can see the list of functions you may use to modify uploaded dataset. Available functions are logically grouped according to the type of effect they have on the data. Consequently, OPERATIONS ON COLUMNS add, remove or modify dataset columns, while OPERATIONS ON ROWS extract certain rows from a dataset based on row numbers or some condition that user defines. Operations "Make dataset" and "Reshape dataset" affect the entire dataset.

![Available function list](/static/images/documentation/functionlist.png)
<p align="center">List of available functions</p>

 For each operation you can see a short documentation with simple illustrated example by clicking "show/hide documentation" button. For every pipeline function you create you may leave a short description note in the "Comment" field. This information helps you and other users of your transformation to understand operations that are performed here. If you ignore this field, the note will be created automatically based on function parameters you have specified.
 
![Common operations for all pipe functions](/static/images/documentation/pipefunccommon1.png)
<p align="center">Common operations for all pipeline functions</p>

Once you have added a new function to the pipeline, it will instantly appear in the pipeline view. You are free to change function parameters any time you need it by simply clicking on the correspondent function icon. To get a short information about the actions performed by this function you may just hover mouse pointer over its name. In many cases function order significantly affects the transformation result. It is very simple to change this order by just dragging function icons along the pipeline. To remove a function click ![Remove function](/static/images/documentation/minus.png)  button next to the function you would like to remove.
 
In DataGraft you are able to see the partial preview of the transformation on each step. Last option makes it possible to see how the transformed data looks like for every stage of transformation.

![Partial preview](/static/images/documentation/steppreview.png)
<p align="center">Figure 20: Live preview of every stage of transformation</p>

The following sections provide you with detailed guidelines for each function usage.
 
####  <a name="make_dataset"></a>Make Dataset 

As its name suggests "Make dataset" function creates new dataset from its input. There are three options to make a dataset. First option is to specify column names that will be headers of a dataset.  By checking "move first row to header" option you get all the column names from the first row, whereas the first row will be removed from a dataset.   The last option fetches first n columns where column names will be given as a simple alphabetic sequence. 
####  <a name="group_and_aggregate"></a>Group and Aggregate

 "Group and aggregate" function groups dataset by given column or set of columns and creates specified aggregations on other columns. Aggregations return a single value, calculated from values in a group. The available aggregations are:
 * MIN returns minimum value in a group
 * MAX returns maximum value in a group
 * SUM returns summation of values in a group
 * AVG returns average value in a group
 * COUNT returns number of non-empty values in group
 * MERGE returns merge of all distinct values in group separated by user-specified separator

####  <a name="remove_duplicates"></a>Remove Duplicates

This function removes duplicates from a dataset. There are two possible ways to deduplicate a dataset:

* Remove full duplicates. Looks for records containing the same values across all columns and leaves only one instance from each set of such rows, other rows(duplicates) will be removed from a dataset

* Remove duplicates on column(set of columns) and leave only the first value. Looks for records having the same values in the specified field(s) and leaves only the first encountered row in this sequence. It is recommended that the dataset is sorted in appropriate order before this way of dataset deduplication is used.

####  <a name="melt"></a>Reshape Dataset
This function restructures a dataset. Two options are available:

* "Melt" option performs this sequence of actions:

   1. Using set of pivot keys as observation identifier, extract observation names from column headers;
   2. Take corresponding measurement value for each observation;
   3. Restructure a dataset in a such way that each observation for given unique combination of pivot keys is stored in a separate row. Each row gets a column named "Variable" that holds observation name and column named "Value" that holds measurement value.

* "Cast" option is reverse to melt. It forms column headers by identifying distinct observation variables and populates these columns by taking measurement values for each observation and performing specified aggregation on them. User therefore should specify column name that stores variables, and column name that stores values. Other columns will be treated as pivot keys. Set of available aggregations:

   1. MIN -- take minimum value for each observation
   2. MAX -- take maximum value for each observation
   3. SUM -- take summation of values for each observation
   4. AVG -- take average value for each observation
   5. COUNT -- take number of non-empty values for each observation
   6. COUNT-DISTINCT -- take number of distinct non-empty values for each observation
   7. MERGE -- merge together all distinct values for each observation separated by user-specified separator


####  <a name="sort"></a>Sort Dataset
This function sorts a dataset by given column in given order. There are four types of sorting:

* Alphabetical
* Numerical
* By length
* Date

It is possible to perform sorting in reverse order for each sorting type. Function supports sorting by multiple columns. The priority of "column - sorting type - order" triple in this case is determined by triple order -- from top to down



####  <a name="add_columns"></a>Add Columns

The "Add columns"  results in adding a new column(s) to a given dataset. To add a new column you should specify column name and a value for a new column. This value will be copied into every row within the dataset. Cells in new column may contain some custom values like current date, dataset filename, row index or custom Clojure code. You are able to add as many columns as you need with one operation. To add one more column simply click "Add more columns"


####  <a name="columns"></a>Take/Drop Columns

The "Take/Drop Columns" function narrows given dataset. It is possible to switch between taking only listed columns or to the opposite, removing listed columns from a dataset. You may explicitly define column names or specify their indexes. 

####  <a name="derive_column"></a>Derive Column

This function dds a new column to the end of the each row which is derived from existing column(s) with the help of specified function. To use this function you should specify a name for a new column, define one or several columns you are going to use to obtain new value and specify a function you apply to them. 

If you think that functionality ordered by standard provided functions is not enough to build your transformation, you may define custom utility functions by yourself using Clojure code (see [Defining Auxiliary Functions](#customfuns) section). 

![Tip](/static/images/documentation/magic.png)**_Tips and tricks:_**


*One powerful feature of derive-column and similar pipeline functions is possibility to combine functions you apply to columns in the same way you combine functions in pipelines. Essentially, these are pipelines inside your dataset manipulation pipeline. To add one more "internal" function into your pipeline function, click <span style="color:blue; font-family:Georgia; font-size:18pt;">"Compose with"</span>  button. Note, that function order is significant in this case. Functions are composed as they appear from top to down. To remove a function from composition pipeline click trash icon  ![Remove function](/static/images/documentation/trash.png) next to the function you wish to delete.*


Some of the functions may expect input arguments in addition to columns, they will operate on. If this is the case, you will be required to specify these arguments in the correspondent input fields that will appear.


####  <a name="merge_columns"></a>Merge Columns

Merges several columns in one using specified separator. New column gets name specified by user and is placed at the index of a first column in a list of columns to merge. If "New column name" parameter is ignored, the created column will get the same name as the first column in a list of columns to merge.



####  <a name="mapc"></a>Map Columns

This function allows you to apply some transformation to column and put the modified value back to the same column. In parameter list you must specify a column you wish to change and a function that will be used to perform this transformation. You may add as many column-function pairs as you need. 


####  <a name="rename_columns"></a>Rename Columns

This function allows you to rename columns in the dataset. To get new names for columns you may either apply function (or function pipeline) to current column names or assign mapping from old to new column names directly.

![Tip](/static/images/documentation/magic.png)**_Tips and tricks:_**

*You may see the function named "keyword" assigned by default as a function used to transform column names. This is done because the column names in Grafter DSL should be treated as keywords -- special symbolic identifiers used in Clojure language. Having this function as a first one in a list of functions used for column names conversion guarantees column names will be recognized as valid keywords.* 

####  <a name="shift"></a>Shift Column

This function changes a column position inside a dataset. It is possible to shift column either to the specified index or to the rightmost index. Other columns will be shifted appropriately.


####  <a name="split"></a>Split Column

This function allows to split a column into multiple by separator. New columns get names of a form [original-column-name]_splitted_0, [original-column-name]_splitted_1, ...

####  <a name="add_row"></a>Add Row

This function adds a new row to the dataset at the specified position. Input fields for each column should be filled in.

####  <a name="shift_row"></a>Shift Row

This function changes a row position inside a dataset. It is possible to shift row either to the specified index or to the end of the dataset. Other rows will be shifted appropriately.


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

To start creating RDF mapping of your dataset use switch "Map tabular data to RDF". (See Figure 20)
The first step here  would be to specify the base graph URI. To create and edit prefixes you are going to need for the RDF generation use "Edit RDF prefixes button". By pressing it you open a dialog, where you can as well see RDF vocabularies available by default.

![Map Tabular Data to RDF](/static/images/documentation/map_tabular_rdf.png)

Now you can start to create, edit and remove RDF nodes and their properties. The three groups of nodes that can be created here are URI nodes, literal nodes and blank nodes. To construct a URI node both as one obtained from dataset column and as some constant URI, you need to define some prefix. Prefixes are separated from values they complement with semicolon. Note, that dataset columns may be converted to the URI form during the tabular transformation step. In this case you don't have to specify prefixers to make them URI nodes in RDF schema. If you, however try to create a URI node from data column that is not recognized as a valid URI, and do not assign any prefix value to  this column, it would be automatically converted to column literal node. Literal nodes are represented just by their value in the resulted RDF file. An example  of RDF mapping skeleton is shown below.

![RDF mapping skeleton](/static/images/documentation/rdfexample.png)

The RDF mapping in DataGraft supports conditional mapping. This means that if you specify the condition, the node will be created only for the rows where this condition is satisfied. To assign a condition turn on "Specify condition" switch in the node creation/editing window.

![Conditional RDF mapping](/static/images/documentation/conditional_mapping.png)

When you create a literal node from the dataset column, you may convert given column value to the specified datatype. All the [built-in xsd primitive datatypes](https://www.w3.org/TR/xmlschema11-2/#built-in-primitive-datatypes) are supported. 

When converting a column value to a given datatypes, you have two optional parameters :

* "on-error" parameter specifies value, that should be used to replace non-valid arguments. By default function replaces all non-valid values with 0 for all numeric types, "false" for data type boolean and "31.12.2099" for dates;

* "on-empty" parameter specifies value, that should be used to replace empty(nil) arguments. By default function replaces all empty values with 0 for all numeric types, "false" for data type boolean and "31.12.2099" for dates, "Unknown" for strings.

It is possible to construct language-tagged string literals by filling in an input field labeled "Language tag".

To assign a datatype not mentioned on the list of available datatypes for conversion it is possible to use "custom" datatype option. In this case, the URI that defines a datatype should be specified in the input field labeled "Data type URI"

When converting to literals of data type "date", dates are validated and date format is recognized automatically. Different rows in a dataset may have different date formats. Recognized date formats(priority is defined by this order):

* "dd.MM.yyyy"
* "dd/MM/yyyy"
* "dd-MM-yyyy"
* "MM.dd.yyyy"
* "MM/dd/yyyy"
* "MM-dd-yyyy"
* "yyyy.MM.dd"
* "yyyy/MM/dd"
* "yyyy-MM-dd"

When converting to literals of data type "boolean", following values are recognized as false:

* "false" (as string);
* "0" (as string);
* "" (empty string);
* false (as java.lang.Boolean);
* 0 (as java.lang.Integer);
* nil.

Other values will be converted to the value true.

###  <a name="apply_tranformation"></a>Executing transformation    

After you've completed creating transformation either with or without RDF mapping part you may apply transformation to your data right in the transformation view. To do so press ![Apply transformation](/static/images/documentation/gear.png) icon. After you did this you can see a dialog, where you have two options:

 
![Apply transformation](/static/images/documentation/executedownload.png)

1. Execute and retreive. By pressing this button you can  download the results locally on your computer as rdf data(n-triples)
2. Download executable. By pressing this button you can  download the executable jar file on your computer. This file can then be used to transform datasets locally instead of in the cloud. The JAR file can be ran by using the command line interface from the location where the file is located as follows:

![jar](/static/images/documentation/jar.png)

## <a name="user_management"></a>User management
In the right top corner of the DataGraft home page you find a button that brings you to your profile page. Here you can edit your account information, change password or cancel your DataGraft account.
![Account information](/static/images/documentation/account_info.png)
###  <a name="quotas"></a>Quotas
In DataGraft there are assigned following usage quotas per user:

* Data Distributions: 4 GB
* Filestores: You can host up to 4 GB of delimiter-separated value or Excel data
* Data Pages: You can have up to 100 SPARQL endpoints, alltogether keeping up to 10 million RDF triples
* Data Transformations: You can have up to 1000 data transformations. If you find DataGraft useful and you are interested to use it beyond its current limitations please get in touch with us.

###  <a name="api_keys"></a>API keys
You can go to your API keys management by going to the correspondent option in the account information menu. Here you can update, delete or enable/disable your API keys.
![Account information](/static/images/documentation/api_keys.png)
###  <a name="authorized_applications"></a>Authorized applications
In its interaction with the platform, Grafterizer component enacts the role of the client application in the [OAuth2](https://oauth.net/2/) authorisation code flow. Thereby, when you run the Grafterizer for the first time you will be asked to authorize Grafterizer to use your account.
![Authorize Grafterizer](/static/images/documentation/authorization.png)

You can later find Grafterizer in the list of your authorized applications, where you can revoke the authorization any time.
![Authorized Grafterizer](/static/images/documentation/auth_apps.png)