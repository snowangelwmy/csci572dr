# URL seed list:
	seed.txt
	
apache-nutch-1.9
	nutch-site.xml
	regex-normalize.xml
	regex-urlfilter.txt 
	solrindex-mapping.xml

solr-4.10.2
	schema.xml

Some statistics about the crawled data:
Totally 2929 documents have been crawled, including application/xhtml+xml (2374), application/zip(554), application/vnd.openxmlformats-officedocument.wordprocessingml.document(1), application/pdf (1), image/jpeg (1), application/atom+xml(1). 

Problems of the crawled data:
Actually there should be more document types in the ACADIS website, e.g., *.xlsx, *.xls, *.doc, *.docx, *.csv, *.m, *.png, etc. However, in my crawling process, only a few document types were indexed into the Solr. Finally, I figured out the reason: there is a "robots.txt" file in the ACADIS website (https://www.aoncadis.org/robots.txt), which doesn't allow the Nutch to crawl the datafile download urls. Please follow the "Nutch Tutorial for ACADIS Website.docx", and recrawl the ACADIS website to get a number of science data.

How to get the crawled data?
The crawled data has been uploaded to the Amazon S3.
[username@nsfpolardata ~]$ $ s3cmd ls s3://nsf-issue-1
                       DIR   s3://nsf-issue-1/apache-nutch-1.9/
2014-12-06 12:02 970081940   s3://nsf-issue-1/nutch_trunk.zip
2014-12-06 12:42       762   s3://nsf-issue-1/readme.txt
2014-12-06 12:13 205924992   s3://nsf-issue-1/solr-4.10.2.zip
2014-12-06 12:13 344402705   s3://nsf-issue-1/solr-4.10.2_2.zip

Of which, the apache-nutch-1.9 and solr-4.10.2.zip are for the NSF ACADIS website. 

To get the data, first, you need to "ssh nsfpolardata.dyndns.org" with your own username and password. And then, download the nutch and solr directory from the Amazon s3 to the machine nsfpolardata.dyndns.org using the command "s3cmd get", e.g., "s3cmd get s3://nsf-issue-1/solr-4.10.2.zip". Finally, download the nutch and solr directory from the machine nsfpolardata.dyndns.org to your local machine using the command "scp", e.g., "scp username@nsfpolardata.dyndns.org:/home/username/download/solr-4.10.2.zip ." Thanks.
