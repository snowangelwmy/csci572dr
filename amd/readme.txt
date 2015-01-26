URL seed list:
	seed.txt
	
nutch_trunk
	nutch-site.xml
	regex-normalize.xml
	regex-urlfilter.txt 
	solrindex-mapping.xml
	httpclient-auth.xml
	parse-plugins.xml
	tika-mimetypes.xml

solr-4.10.2
	schema.xml

Some statistics about the crawled data:
Totally 29642 documents have been crawled, including text/html (30166), application/xhtml+xml (1449), image/png (513), image/gif (515), application/rss+xml (69), text/css (34), application/javascript (29), application/atom+xml (22), image/jpeg (17), application/xml (13), and text/x-java-source (3).

Problems of the crawled data:
1: Robot denied problem due to the "robots.txt" file in the AMD website (http://gcmd.gsfc.nasa.gov/robots.txt), which could be solved by following the "Nutch Tutorial for ACADIS Website.docx" to disable robot checks, and recrawl the AMD website to get a number of science data.
2: Currently, the Nutch may not do very well in parsing dynamic javascript webpages, please try nutch-selenium (https://github.com/momer/nutch-selenium) to crawl dynamic javascript websites, such as the AMD.

How to get the crawled data?
The crawled data has been uploaded to the Amazon S3.
[username@nsfpolardata ~]$ $ s3cmd ls s3://nsf-issue-1
                       DIR   s3://nsf-issue-1/apache-nutch-1.9/
2014-12-06 12:02 970081940   s3://nsf-issue-1/nutch_trunk.zip
2014-12-06 12:42       762   s3://nsf-issue-1/readme.txt
2014-12-06 12:13 205924992   s3://nsf-issue-1/solr-4.10.2.zip
2014-12-06 12:13 344402705   s3://nsf-issue-1/solr-4.10.2_2.zip

Of which, the nutch_trunk.zip and solr-4.10.2_2.zip are for the NASA AMD website. 

To get the data, first, you need to "ssh nsfpolardata.dyndns.org" with your own username and password. And then, download the nutch and solr directory from the Amazon s3 to the machine nsfpolardata.dyndns.org using the command "s3cmd get", e.g., "s3cmd get s3://nsf-issue-1/solr-4.10.2.zip". Finally, download the nutch and solr directory from the machine nsfpolardata.dyndns.org to your local machine using the command "scp", e.g., "scp username@nsfpolardata.dyndns.org:/home/username/download/solr-4.10.2.zip ." Thanks.	