# Banana

__NOTE__: You have reached the Banana repository. 
The Banana project is a fork of Kibana 3, which can be found at [http://three.kibana.org](http://three.kibana.org)
The goal is to port the code to work with Apache Solr as a backend storage. 
 
## IMPORTANT

All recent development has taken place on the "develop" branch. So pull the repo from the "develop" branch or the "release1.0" branch that will be created soon.

## Overview

Banana is Apache Licensed and serves as a visualizer and search interface to timestamped data sets stored in Solr, such as log files, Twitter streams, etc. Banana is designed to be easy to start-up with (just like Kibana from which it is forked). Data can be ingested into Solr through a variety of ways, including Solr Output Plug-in for LogStash, Flume and other connectors.

### Requirements
* A modern web browser. The latest version of Chrome, Safari and Firefox have all been tested to 
work.
* A webserver. So far, we have tested it with Jetty embedded with Solr, but it should work with other webservers.
* A browser reachable Solr server. The Solr endpoint must be open, or a proxy configured to allow 
access to it.

### Installation and QuickStart

#### Banana Web App run within existing Solr instance
1. Run Solr once to create the webapp directories  
		1. cd $SOLR_HOME/example
		2. java -jar start.jar
2. Copy banana folder to $SOLR_HOME/example/solr-webapp/webapp/  
3. Browse to http://localhost:8983/solr/banana/src/index.html#/dashboard  

If your Solr port is different, edit banana/src/config.js and enter the port you are using.

If you have not created the data collections and ingested data into Solr, you will see an error messaging saying "No Index found at .." Go to the Solr Output Plug-in for LogStash QucickStart page to learn how to import data into your Solr instance

If you want to save and load dashboards from Solr, copy either solr-4.4.0/kibana-int or solr-4.5.0/kibana-int directories (as appropriate) into $SOLR_HOME/example/solr in order to setup the required core and restart Solr.

#### Installing and Running the Complete SLK Stack

We have packaged Solr, the open Source LogStash with Solr Output Plug-in and Banana, along with default collections and dashboards to make it easy for you to get started. The package is available here  (Link to be added). Unzip the package and:  
1. Run Solr  
		1. cd slk4.7.0/solr-4.7.0/example-logs  
		2. java -jar start.jar   
2. Browse to http://localhost:8983/banana 
 
You will see example dashboards which you can use as a starting point for your applications.
Once again, if you choose to run Solr on a different port, please edit the config.js file.

#### Running from a war file
1.Pull the develop or release1.0 branch. Run "ant" from within the banana directory to build the war file.
		1. cd $BANANA_REPO_HOME   
		2. ant  
The war file will be called banana-<build number>.war and will be located in $BANANA_REPO_HOME/build  


1. Copy $BANANA_REPO_HOME/build/banana-<build number>.war to $SOLR_HOME/example/webapps/  
2. Copy $BANANA_REPO_HOME/jetty/banana-context.xml  to $SOLR_HOME/example/contexts/  
3  Run Solr:  
		1. cd $SOLR_HOME/example/    
		2. java -jar start.jar    
4. Browse to http://localhost:8983/banana  

	
#### Banana Web App run in a WebServer

1. Edit config.js to point to the Solr server that will store the Kibana dashboards. You will need to make sure that a collection is created with the appropriate conf directory and schema.xml. Conf directories are available at banana/solr-4.4.0	(for Solr 4.4) and banana/solr-4.5.0 (for 4.5 and later).
2. The Solr server configured in config.js will serve as the default node for each dashboard; you can configure each dashboard to point to a different Solr endpoint as long as your webserver puts out the correct CORS headers.
3. Point your browser at your installation based on the contexts you have configured.



## FAQ

__Q__: How do I secure my solr endpoint so that users do not have access to it? 
__A__: The simplest solution is to use a nginx reverse proxy (See for example https://groups.google.com/forum/#!topic/ajax-solr/pLtYfm83I98).

### Support

Banana preserves most of the features of Kibana (from which it is forked).

Introduction videos on Kibana can be found at [http://three.kibana.org/about.html](http://three.kibana.org/about.html)  


###Trademarks

Kibana is a trademark of Elasticsearch BV
Logstash is a trademark of Elasticsearch BV



