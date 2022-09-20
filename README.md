# TSN_Database
Finding the optimal solution for parsing large amounts of data from news sites.
TSN is a large Ukrainian news portal, with news from 2007 to the present. More than 800,000 articles are located on it. And they were all processed.
For this project optimal solution is to use selectolax.parser and WGET command its up speed from 1 week to 5-7 hours of programs work.

1.I've been looking for different solutions to get a list of links to start getting data from each individual article. the main concepts were:

  -in the structure of news sats, it is common to store all articles in the archive by day. I tried to parse all the links to the article from this archive, but it took about a day, and it did not suit me very well
  
  -On tsn.ua/robots.txt, we find a link to an .xml file with links to .xml.gz files used by the Google bot to quickly search for news on the site.We parse the link https://tsn.ua/ru/sitemap_index.xml and with the help of bs4 we get the path to 199 links to the archived files, with the help of wget and the path variable we download them. Create a list with the names of each file and the path to it from 1 to 199.xml.gz. With the help of gzip, we open each of the xml files in turn and parse using selectolax.parser, receiving a result letter with ~ 800,000 links to articles and other data that have a general appearance:
  
['https://tsn.ua/ru/den-v-istorii-d/20-iyulya-v-istorii-mezhdunarodnyy-den-torta-nachalo-istorii-bmw-i-den-ledenca-na-palochke- 99780.html', '2021-07-20', 'daily', '0.7']

The result of the first task is that sometimes you need to look for other ways, it took 5 minutes to get links using the new method.


2.The next task was to get data on each page from the list. For this, I tried beautifulsoup, clean lxml, selectolax parser, but the main time was spent on requesting the server, various programs for getting html faster did not give significant results, and on average it took 80-100 hours to process such a number of links.

  -the solution that gave a speed increase of more than 10 times was the use of the Wget command for parallel downloading of a copy of the page in html format. running parallel lists of 20 evenly separated links, I received in 8-10 hours a complete set of .html files that needed to be cleaned and could be parsed.
  
  -also I compared parsing speed in beautifulsoup and selectolax.parser for local files and also got a 10x increase.
  
  -a typical dictionary was obtained for each link, which had the following form:
  
  
  
  
The second big step was cleaning the data. I used the pandas and numpy libraries for it. Each column in the dataframe has been data cleaned, applied the correct data type, and has been stripped of unnecessary text elements for further analysis.
  
  
  
  
  
  
