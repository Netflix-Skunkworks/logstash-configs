# logstash-configs
Logstash configuration files used by Netflix.

The Netflix Security Team uses the ELK stack (Elasticsearch, Logstash, Kibana) for log aggregation. We collect logs from a variety of security appliances and have written custom Grok filters for Logstash to parse them. We figured we'd save everyone else the time and effort and release them here.

Other teams within Netflix may add their configs here if there's interest.

#Grok Filters
All filters are for parsing logs via syslog unless otherwise noted.

###Cyphort
* File Download
* File Submission
* CNC Traffic
* Exploit
* Data Theft
* Cyphort's custom timestamp

###Palo Alto Networks (BSD Syslog)
* Threat Log
* PAN's custom timestamp

###Sophos AV Reporting Log Writer (via Logstash-Forwarder)
* EventsWebData (Web.log)
* ThreatEventData (DefaultThreats.log)

###Riverbed SteelApp Traffic Manager (Formerly Stingray Traffic Manager)
* Default Slave Log
* Pagespeed

###Generic CEF Logs (With and without Syslog)

#Config Files
###logstash.conf
Main Logstash config. It references patterns.conf, which holds all of the Grok filters.

Note: We're in the Pacific time zone. You'll want to modify the "timezone" lines to match your time zone.

###patterns.conf
The Grok filters mentioned at the start of this document.

###logstash-forwarder.conf
Config for sending logs from a Windows Sophos AV server to logstash via logstash-forwarder.

#Coming Soon
* Carbon Black and SentinelOne Grok filters
* Configs for hoziontally scaling Logstash in AWS via ELBs, rsyslog, and Redis.
