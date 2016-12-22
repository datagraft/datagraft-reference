---
layout: page
title: FAQ
permalink: /faq/
weight: 12
---

#### What is DataGraft?

DataGraft is a cloud-based service for data transformation and data access.

#### Who are DataGraft's target users?

DataGraft is aimed at data workers and data developers interested in simplified and cost-effective solutions for managing their data, with a focus on data transformation, data hosting, and data access. Example users include open data publishers, linked data developers, data scientists.

#### Why DataGraft?

DataGraft was developed to provide better and easier to use tools for data workers and developers who consider existing approaches to data transformation, hosting, and access too costly and technically complex.

#### Why is DataGraft special?

DataGraft offers an integrated, flexible, and reliable cloud-based solution for data transformation and data access. Key features include flexible management of data transformations (e.g. interactive creation, execution, sharing, reuse) and reliable data services. DataGraft offers GUI and API access to data transformations and data services. 

#### Are all my data and/or transformations on DataGraft public?

When creating transformations or publishing data you are hosting them on DataGraft. You can choose whether you want to make them public (i.e. visible on the DataGraft portal) or private (i.e. only you have access to them).

#### What can I do with DataGraft?

The current version of DataGraft allows you to:

 * Transform tabular data and share transformations: Edit, host, execute, and share data transformations
 * Publish, share, and access data: Scalable data hosting and reliable data access / data querying


#### What data formats does DataGraft support?

The current version of DataGraft handles tabular data (CSV) and RDF data (i.e. you can upload CSV and RDF data to DataGraft). Data transformations (e.g. data cleaning) can be performed on tabular data, which in turn can be transformed to RDF data. For RDF data, live data services are created that allow programmatic querying. More data formats are expected to be supported in the future.

#### What querying languages does DataGraft support?

The current version of DataGraft allows querying the hosted RDF data via SPARQL.

#### What skills do I need to have to use DataGraft?

 * If you are interested in tabular data transformations (e.g. cleaning of tabular data, sharing of transformations, etc.), no special skills are required, depending on the complexity of the transformations you want to perform. Currently DataGraft supports an number of predefined data transformations, with more to be added in the near future.
 * If you are interested in publication of RDF data and access to RDF data, familiarity with RDF and SPARQL are needed.

#### Is there any documentation for DataGraft?

Yes, draft documentation is available [here](/documentation/). Documentation will be further improved in the upcoming period.

For background materials on technical aspects related to DataGraft you can check out the [DaPaaS technical reports](http://project.dapaas.eu/dapaas-reports). Useful presentations can be found [here](http://www.slideshare.net/dapaasproject/datagraft-dataasaservice-for-open-data) and  [here](http://www.slideshare.net/ruleml2012/industryruleml2015-datagraft).

#### I am a developer and interested to transform and host my transformations and data  with DataGraft. Do I have API access to DataGraft capabilities?

Yes, DataGraft capabilities are accessible at the API level. These include programmatic access to datasets and data transformation catalogues (adding, removing datasets and transformations), querying data, and executing data transformations. The capabilities offered through the DataGrat.net portal are a subset of capabilities offered at the API level. If you want to benefit from all the features of DataGraft, API level access is recommended. See the [API documentation](https://datagraft.net/api/) for further details.

#### Who developed DataGraft?

DataGraft has been primarily developed by [a consortium of 6 companies](http://project.dapaas.eu/dapaas-partners) as part of [the DaPaaS project](http://project.dapaas.eu/), but others have also contributed (see next question).

#### Who funded DataGraft?

DataGraft has been primarily funded by the European Commission (EC) through [the DaPaaS project](http://project.dapaas.eu/) under the Grant Agreement 610988. Other EC-funded projects such as [SmartOpenData](http://www.smartopendata.eu/),  [OpenCube](http://opencube-project.eu/), and [proDataMarket](http://prodatamarket.eu/) contributed to the development of some components.

#### Who maintains and operates DataGraft?

Currently DataGraft is maintained and operated by the DaPaaS consortium. Discussions are ongoing on future maintenance and development of DataGraft after the completion of the DaPaaS project at the end of October 2015 - the development will continue under the [proDataMarket project](http://prodatamarket.eu/) or a commercial entity will continue the maintenance and development.

#### Is it free to use DataGraft?

For now, yes. With the following limitations per account:

* Data upload: You can upload CSV files of up to 10MB each, and RDF files of up to 100MB each;
* Datapages: You can have up to 10 RDF datapages;
* Persistent storage: You can host up to 2 GB of CSV data, and 1 Million RDF triples for RDF data.

If you find DataGraft useful and you are interested to use it beyond its current limitations please [get in touch with us](https://datagraft.net/contact/). As the development progresses these limitations may be relaxed for all accounts.

#### What is a datapage?

A datapage is a way to organize data. You can think of a datapage as a Web page with information about a dataset (e.g. metadata, link to download data). Currently we support two types of datapages: CSV datapages and RDF datapages. For technical reasons, at this stage, a CSV datapage can accomodate one input CSV file, however an RDF datapage may accomodate more than one input RDF file (within the limintations mentioned in the previous question).

#### What is the status of the DataGraft development?

DataGraft is currently under iterative development. The current version of DataGraft is the first beta release.

#### Where can I report issues/bugs?

Since DataGraft is currently in beta, it contains bugs. There are [issues we know of](https://github.com/dapaas/datagraft/issues), and likely others that we don't yet know of. You can report issues [here](https://github.com/dapaas/datagraft/issues/new).

#### What features are planned for future releases?

Future releases of DataGraft will focus on improving or extending existing features. An unordered list of future feature enhancements includes:

* Read-only transformations
* Transformation history with undo/redo options
* Support for various data formats: e.g., JSON, geospatial (GML, Shapefile)
* Support for multiple files / join datasets
* Push/pull services for updating outputs in different frequency
* Better error reporting in transformations
* Improving functions on tables (vs in pipeline)
* Dynamic deployment of transformations (cloud-based)
* (Public/Private) sharing of utility function
* JavaScript transformation code
* Predictive transformations, i.e. learn from previous transformations
* Dealing with streams of data vs static files
* Better traceability: files, data pages, transformations
* Geospatial processing of data: radius around point, radius around polygon, data within polygon, squares, areas

Interested in any of the above issues? [Get in touch with us](https://datagraft.net/contact/)!

#### I need feature XYZ but it is not supported by DataGraft. What can I do?
[Contact us](https://datagraft.net/contact/) and we’ll be glad to assist!

#### Whom can I contact if I have further comments and questions about DataGraft?
We have a [Disqus page](https://datagraft.net/feedback/) where you can leave feedback and comments on DataGraft. And you can always [contact us directly](http://project.dapaas.eu/dapaas-contact-us)!
