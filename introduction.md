---
layout: doc
title:  "Introduction" 
permalink: /docs/index.html
---

### Welcome to Apache Eagle (incubating)

> Apache Eagle (incubating, called Eagle in the following) is an open source analytics solution for identifying security and performance issues instantly on big data platforms e.g. Hadoop, Spark, NoSQL etc. It analyzes data activities, yarn applications, jmx metrics, and daemon logs etc., provides state-of-the-art alert engine to identify security breach, performance issues and shows insights.

### Basic Analytics and Monitoring Flow

Normally 3 basic steps are involved in Eagle platform: Data Integration, Alerting Engine and Insights. 

* Data Integration normally is streaming process application, for example Apache Storm topology or Spark streaming application. During data integration, raw data can be transformed, normalized, analyzed etc. The output of data integration will be streamed into Alerting Engine and Insights.

* Alerting Engine is highly scalable rule execution engine, which is embedded into Data Integration application as of Eagle 0.4.0. With alerting engine, user can create/update comprehensive policies on the fly.

* Insights is for correlating alerts with raw data for user to explore root causes.

Depending on data source, data integrations may use pull or push methods to stream data into Eagle platform, for example HDFS audit log can be pushed by logstash, but Hive query log can be pulled by Hive Integration application.  

### Key Qualities

* **Real Time**: We understand the importance of timing and acting fast in case of a security breach or performance issue. So we designed Eagle to make sure the alerts are generated immediately even for very high volume streaming data. This is achieved by running Eagle alert engine on top of streaming framework, e.g. Apache Storm with high performance CEP engine e.g. WSO2 Siddhi etc.

* **Scalability**: At eBay we operate one of world's largest big data platforms Hadoop, Spark etc. The volume of operational logs and user activities generated by big data platforms is very huge. Eagle alert engine is well designed to evaluate polices against data in motion at cloud scale.This is achieved by dynamically partitioning data and policies based on policy semantics.

* **Metadata Driven**: Eagle understands what policies are evaluated for what data source in what physical boxes. This thanks to Eagle metadata design and master/slave distributed computing architecture. Eagle alert engine's coordinator listens to metadata change, calculates snapshot for mapping policy to resource and then dynamically deploys snapshot onto storm spouts and bolts.

* **Extensibility**: Eagle is designed with extensibility in mind. You can integrate many different data sources into Eagle platform with a few clicks.
