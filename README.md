# FactSE
Fact Search Engine

This is a project to see how finding facts using a search based algorithm will work, as opposed to using direct lookups or hierarchial definitions based on location of keys.

In this theory, we weight each "Fact" based on a fact heirarchy.

First formula tested:
Each fact is weighted bottom to top, using 2x+1
Facts at the top are weighted higher
If a fact has the key, and it equals the fact sent, the result is a positive number.
If the key is there and different (or missing), the result is a negative number.
We then sum the key results together to get the total suitability rating.

Example

Key hierarchy:
- hostname
- rack
- site

Weighting:
hostname = 7
rack = 3
site = 1

Example
Fact1:
  factname: nameservers
  value: [8.8.8.8, 8.8.4.4]
keys:
  site: dallas
  rack: dal22

Fact2:
  factname: nameservers
  value: [4.4.4.4]
keys:
  site: dallas

Fact3:
  factname: nameservers
  value: [8.8.8.8]
keys:
  hostname: dal-myhost.mydomain.com

Query:
request: nameservers
mykeys:
  site: dallas

Answer:
Fact2 = 1
Fact1 = -2
Fact3 = -7

Instead of worrying about different combinations of a hierarchy like /site/<site>/rack/<rack>/hostname/<hostname> etc., we can just specify the key hierarchy and let the maths figure it out.

Code to test this theory out coming soon
