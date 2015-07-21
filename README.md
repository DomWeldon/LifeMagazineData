# Life Magazine Data

## Introduction 
This has been published to help any researchers in a similar position to mine, studying *Life* magazine. The whole of *Life* has been digitized and is [available on Google Books](https://books.google.co.uk/books?id=N0EEAAAAMBAJ&source=gbs_all_issues_r&cad=1), however, scrolling through individual issues can be a bit of a pain. The CSV file in this repository has the date and Google Books ID of every issue of *Life* available on Google at present. 

## Example 
With this data you can easily link to any issue of *Life* magazine that you wish. For example, [the first issue of *Life* was published on 23 Nov 1936](http://www.google.com/books?id=N0EEAAAAMBAJ) and its Google Books ID is `N0EEAAAAMBAJ`. To look at this issue, go to one of the URLs below (the top link will display details of the issue, the bottom link will open straight away in Google Books preview).

    http://www.google.com/books?id=N0EEAAAAMBAJ
    http://www.google.com/books?id=N0EEAAAAMBAJ&printsec=frontcover

Replace the id variable to any value in the file for any other issue of life. 

## RegEx
Google Books [displays a scrolling list of front covers for a number of magazines](http://www.google.com/books?id=N0EEAAAAMBAJ). This section of the page looks like this.

    <div id="allissues_scrollview" style="width: 100%;">
    	<div id="allissues_gallery" style="width: 21000px;">
    		<div class="allissues_gallerycell">
    			<center>
    				<a href="https://books.google.co.uk/books?id=j1AEAAAAMBAJ&amp;source=gbs_all_issues_r&amp;cad=1">
    					<img class="img_issue" src="https://books.google.co.uk/books/content?id=j1AEAAAAMBAJ&amp;printsec=frontcover&amp;img=1&amp;zoom=1&amp;edge=curl" alt="9 Jan 1970" title="9 Jan 1970" id="https://books.google.co.uk/books/content?id=j1AEAAAAMBAJ&amp;printsec=frontcover&amp;img=1&amp;zoom=1&amp;edge=curl" border="1">
    				</a>
    				<br>
    				<a href="https://books.google.co.uk/books?id=j1AEAAAAMBAJ&amp;source=gbs_all_issues_r&amp;cad=1">
    					<span class="caption_issue">9 Jan 1970</span>
    				</a>
    			</center>
    		</div>
    	</div>
    	
    	...
    </div>
    

If you copy this from the page (e.g. using Chrome Developer tools), then the RegEx below should help you strip out the data you might need to do this with other magazines.

    <div class="allissues_gallerycell"><center><a[^>]+><img class="img_issue" src="[^"]+" alt="([0-9 A-Za-z]+)" title="[^"]+" id="https://books.google.co.uk/books/content\?id=([^&]+)[^>]+></a><br><a[^>]+><span[^>]+>[a-zA-Z0-9 ]+</span></a></center></div>


## License
[Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/)
