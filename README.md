# TSN_Database
Finding the optimal solution for parsing large amounts of data from news sites.
TSN is a large Ukrainian news portal, with news from 2007 to the present. more than 800,000 states are located on it. and they were all processed.
For this project optimal solution is to use selectolax.parser and WGET command its up speed from 1 week to 5-7 hours of programs work.

1. On tsn.ua/robots.txt, we find a link to an .xml file with links to .xml.gz files used by the Google bot to quickly search for news on the site.
2. We parse the link https://tsn.ua/ru/sitemap_index.xml and with the help of bs4 we get the path to 199 links to the archived files, with the help of wget and the path variable we download them to the \data database
3*. Create a list with the names of each file and the path to it from 1 to 199.xml.gz. With the help of gzip, we open each of the xml files in turn and parse using selectolax.parser, receiving a result letter with ~ 800,000 links to articles and other data that have a general appearance:
['https://tsn.ua/ru/den-v-istorii-d/20-iyulya-v-istorii-mezhdunarodnyy-den-torta-nachalo-istorii-bmw-i-den-ledenca-na-palochke- 99780.html', '2021-07-20', 'daily', '0.7']
4. We find all elements in the list where the list does not have a length of 4 elements, and delete them, a total of 8 elements
5. I create a new directory in which files with links will be stored, divided into 20 text files for parallel execution
6. I take all the links from the result list and divide them into 20 parts for recording in 20 text files for 100,000 links because they take up a lot of space
