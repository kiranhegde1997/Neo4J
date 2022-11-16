OWB : Pipeline lineage for DataOps tool for enabling automated upload of lineage relationships in Neo4J graph DB 
----------------------------------------------------------------------------------------------------------------
An automated upload of lineage relationships to Neo4J graph DB is made possible by a Python application/utility that reads MySQL lineage-related tables.


CONTENTS OF THIS FILE
---------------------

 * Introduction
 * Installation
 * Configuration
 * Troubleshooting
 * Pending
 * Maintainers
 

INTRODUCTION
------------

This tool extracts data from MySQL tables, and then uses neo4j cypher queries to generate nodes and relationships between them to form a graph in the neo4j database.
Further, the OWB UI uses that graph to show a lineage graph.


INSTALLATION
------------
1.For Python Libraries :

pip install -r requirements.txt


2.Steps to install apoc library for neo4j browser

* Download the apoc-<version>.jar into the /neo4j/plugins directory.
* Open the neo4j.conf at /neo4j/conf/ and replace the line #dbms.security.procedures... with
  dbms.security.procedures.allowlist=apoc.coll.*,apoc.load.*,gds.*,apoc.*
* Restart the Neo4j service.
* You can run the following query to see whether the installation was successful " RETURN apoc.version() ".



CONFIGURATION
-------------

* Configuration settings of the mysql and neo4j credentials in lineage_properties.toml file


1. [mysql]

A database dialect is a configuration setting for platform independent software (JPA, Hibernate, etc) which allows such software to translate its generic SQL statements into vendor specific DDL, DML.

dialect  : is the RDBMS used(in small case).
username : Name of the user to connect with.
password : passwords are stored within a Windows Credential Vault, keyring module provides a way to store, lookup and delete passwords in various backends supported by Python-Keyring.
hostname : Name or IP address of the server host.
db_name  : The schema to use as default schema.
service_name : If a service name is given, it can be followed by a single option.


2. [neo4j]

![Alt text](C:\Users\kiran.hegde\Desktop\URI.png?raw=true "Optional Title")

uri : is picked up from neo4j console stating " Remote interface available at  http://localhost:7474/" 
username :user name of the neo4j database
password : password of the neo4j database




TROUBLESHOOTING
---------------
* If the code fails to execute sucessufully, mysql-neo4j-log gets created capturing the type of error occured while running 
the code.
* Check the log file to see what kind of error there is, fix it, and then rerun the code.


PENDING POINTS
--------------
 * Delta lineage refresh approach
     	The present utility uploads all the data to MySQL at once, however it does not append the new records when further data is added to MySQL.



MAINTAINERS
-----------

Current maintainers:

* Chennapai Yashwanth
* Kiran Hegde


