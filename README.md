# ELK-watcher

Elasticsearch Logstash Kibana Filebeat 

For details on how an elasticsearch watcher works - https://www.elastic.co/guide/en/kibana/current/watcher-ui.html

# Info

The watchers are demonstration of how you can integrate a logging, indexing and webhook action of Elasticsearch to a watcher. Here the webhook used in 3rd watcher is an OTRS endpoint for creating OTRS tickets. More info on OTRS - https://otrs.com/ 

# Build

Install Elasticsearch and kibana first. 


--->  watcher_logging_action.json


1. The watcher catches log entries in which the field 'message' consists of search strings Query 1 / Query 2 / Query 3. Change accordingly.

2. Right now watcher looks for all indices. For changing the watcher to look for particular index or indices, change '*' in indices field to name of the indices.

3. Check /var/log/elasticsearch/elastic.log for log entries that will be created with header 'Watcher executed perfectly'.

4. Change 'gte' and 'ite' to suit your requirements. Check range query - https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-range-query.html

5. You can change log level to 'info', 'warn' etc according to your requirement. 




--->  watcher_index_action.json


1. The watcher catches log entries in which the field 'message' consists of search strings Query 1 / Query 2 / Query 3. Change accordingly.

2. Right now watcher looks for all indices. For changing the watcher to look for particular index or indices, change '*' in indices field to name of the indices.

3. Check "watcher-index-2023.05.30-000001" for log entries that will be created with header 'watcher action'. Creating index POST request has been provided.

4. Change 'gte' and 'ite' to suit your requirements. Check range query - https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-range-query.html

5. You can change log level to 'info', 'warn' etc according to your requirement. 



   
--->  watcher_OTRS_action.json


1. The watcher catches log entries in which the field 'message' consists of search strings Query 1 / Query 2 / Query 3. Change accordingly. 

2. Right now watcher looks for all indices. For changing the watcher to look for particular index or indices, change '*' in indices field to name of the indices. 

3. Check the webhook body and change the needful like ip, username and password accordingly.

4. This is a http webhook. You might need to change the setting if you have an ssl certified OTRS instance.

5. Change 'gte' and 'ite' to suit your requirements. Check range query - https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-range-query.html


--->  ingest_pipelines.json

Pipeline for automatically applying Grok filters for parsing Network log data

Example 
1. Nov  21 00:00:30 localhost abc[1211]: 21-Nov 00:00  Message delivery ERROR: Message delivery error: Unable to store data in database.
2. 168 <164>1 2001-02-24T08:35:51-05:00 65/49 %CST-1-14452 - - - Deny tcp src wan:112.112.112.112/53345 dst wan:112.112.112.112/3332 by access-group \"acess_list\" [0x1, 1x1]
3. 00:00:46: %LINK-3-UPDOWN: Interface Port-channel1, changed state to up
4. 0:00:48: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed 



