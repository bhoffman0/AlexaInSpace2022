.. raw:: html 

   <div class="logo-header"  id="student-logo"  > <img class="align-center" src="../_static/Mobile_CSP_Logo_White_transparent.png" width="250px"/> </div>

Data Map App
============

.. raw:: html

        <div class="MCSP-lesson-content">
    <script>
      $(document).ready(function() {
        generateSummary(EKmapping['7.05']);
        generateHovers();
        Tipped.create('.vocab', function(element) {
        var vocab = $(element).data('id');
        return vocabulary[vocab];
          }, {
            cache: false,
              position: 'topleft'
              });
      });
    
    /*  var vocabulary = { 
        "CSV files":"CSV stands for comma-separated values. A simple text format for data files is to put each row on a separate line with the column separated by commas.",
        "JSON":"Javascript Object Notation (JSON) is a standard data file format used widely on the web where data objects are represented using lists and attribute-value pairs.",
             "GeoJSON":"GeoJSON is a standard data file format to represent geographical data.",
        "API":"The Application Programming Interface (API) for a program or web service defines how other programs can communicate with it and use it. ",
      };      */
    </script>
    <h3 id="est-length">Time Estimate: 45 minutes</h3>
    

Introduction and Goals
-----------------------

.. raw:: html

    <p>
    <table>
    <tbody>
	<tr>
		<td colspan=2>In this lesson, you will build an App Inventor app that visualizes data in a map. The Data Map app uses a <span class="hover vocab yui-wk-div" data-id='GeoJSON'>GeoJSON</span> data file to draw states on the map. Then, a spreadsheet <span class="hover vocab yui-wk-div" data-id='CSV files'>CSV</span> file of data about the states is read in and displayed when each state is clicked.</td>
	</tr>
    <tr>
		<td valign="top">
		<iframe allowfullscreen="" frameborder="0" height="250" src="https://www.youtube.com/embed/ug6NxkEP7_I?rel=0" width="225"></iframe>
         (<span class="yui-non"><a href="https://www.teachertube.com/video/data-map-app-preview-476360" target="_blank">TeacherTube Version</a></span>)
        </td>
		<td valign="top">   
			<div><b>Learning Objectives:</b>&nbspI will learn to</div>
			<ul>
			<li>read data from a file into an app</li>
			<li>store data into and manipulate a list of lists</li>
			<li>use data visualization on a map to represent different data values</li>
			<li>use <span class="hover vocab yui-wk-div" data-id='GeoJSON'>GeoJSON</span> files to draw polygons on a map</li>
			<li>use an <span class="hover vocab yui-wk-div" data-id='API'>API</span> to read in real-time weather data</li>			
			</ul>
			<div><b>Language Objectives:</b>&nbspI will be able to</div>
			<ul>
			<li>use target vocabulary, such as <span class="hover vocab yui-wk-div" data-id="JSON">JSON</span> and <span class="hover vocab yui-wk-div" data-id="API">API</span> while describing app features and User Interface with the support of concept definitions from this lesson</li>
			</ul>
		</td>
    </tr>
    </tbody>
    </table>
    

Learning Activities
--------------------

.. raw:: html

    <p><h3>Data Sources</h3></p>
    Data sources can be included and used in App Inventor apps in 3 different ways.
    </p><ol><li style="padding-bottom:5px"><b>Manually constructing lists of data.</b> Create a list and add each item of data as an element to the list. This is good for small amounts of data, but not a good option if there is a lot of data or the data changes frequently (such as weather, sports statistics, or stock prices).</li>
    <li style="padding-bottom:5px"><b>Uploading data files into the Media section.</b> This is a good option for larger amounts of data, especially if you can find a file that has the data you need already in it. It is not a good option if the data changes frequently.</li>
	<li style="padding-bottom:5px"><b>Using a web <span class="hover vocab yui-wk-div" data-id='API'>API</span> to read in the data.</b> This is a good option if the data changes frequently.</li>
	</ol>
    
    <p>Often a single data source does not contain the necessary data to draw a conclusion. It may be required to combine data from a variety of sources to formulate a conclusion. This app uses 2 data files which are already uploaded into the app template in its Media section. The first data file is a <a href="https://en.wikipedia.org/wiki/Comma-separated_values" target="_blank">Comma-Separated-Values (<span class="hover vocab yui-wk-div" data-id='CSV files'>CSV</span>) file</a>. Any spreadsheet in Excel or Google Sheets can be saved as a .csv file which just has the text separated by commas, which is a great format for importing into App Inventor. The .csv file in this app contains state data from the <a href="https://www.cdc.gov/nchs/pressroom/stats_of_the_states.htm" target="_blank">Center for Disease Control (CDC)</a> that includes data about each state's population, non-insured rate, firearms death rates, drug overdose death rates, and a URL for state information at the CDC website.</p>
    
    
    <p>
      The second file, <a href="https://docs.google.com/document/d/18zBz7OfIgiDXdhe8JWMQhHyxCRsrUbLsfjE2oGpbFEM/edit?usp=sharing" target="_blank">US States <span class="hover vocab yui-wk-div" data-id='GeoJSON'>GeoJSON</span></a>, loads in the polygon shapes of each state to overlay on the map so that we can click on them. <a href="http://GeoJSON.org/" target="_blank"><span class="hover vocab yui-wk-div" data-id='GeoJSON'>GeoJSON</span>.org</a> (pronounced geo-jay-sun) is a standard agreed-upon format for geographical information used on the web and in data files. <a href="https://www.json.org/"><span class="hover vocab yui-wk-div" data-id='JSON'>JSON</span>.org</a> is a general format that describes features and values for any object that many web servers use to communicate and store data. If you open this <a href="https://docs.google.com/document/d/18zBz7OfIgiDXdhe8JWMQhHyxCRsrUbLsfjE2oGpbFEM/edit?usp=sharing" target="_blank">us_states.geojson</a> file, you'll see that it has a set of latitude and longitude pairs that describe the points of the polygon to draw each of the state shapes.
    You can create your own <span class="hover vocab yui-wk-div" data-id='GeoJSON'>GeoJSON</span> files at <a href="http://GeoJSON.io" target="_blank">http://geojson.io</a> and find free public ones online for example at <a href="https://geojson-maps.ash.ms/" target="_blank">https://geojson-maps.ash.ms/</a>.
    </p>
    <p><span class="hover vocab yui-wk-div" data-id='API'>APIs</span> are very useful for real-time data that changes frequently. In the projects for this app, you can use the OpenWeatherMap <span class="hover vocab yui-wk-div" data-id='API'>API</span> to read in and display weather data for each state. Here’s a list of different public <span class="hover vocab yui-wk-div" data-id='API'>APIs</span> that you can use in apps: <a href="https://github.com/toddmotto/public-apis">https://github.com/toddmotto/public-apis</a>.</p>
    <p>Using and processing data sets in programs can have certain challenges. For example, the data may be incomplete or invalid or it may not have been entered in a uniform way with variations in spelling and capitalization. <span class="hover vocab yui-wk-div" data-id='cleaning data'>Cleaning data</span> is a process that makes the data uniform without changing its meaning, for example, replacing all equivalent abbreviations, spellings, and capitalizations with the same word. Sometimes data translation and transformation is necessary to convert data from one format to another. When data is transformed using tools and programs, patterns can emerge, allowing us to gain insight and knowledge. More complex data operations such as clustering similar data or categorizing and labeling data can also help us to gain knowledge. However, the ability to process data depends on the capabilities of the users and their tools.
      
    </p><h3>Tutorial</h3>
    <p>Start App Inventor with <a href="http://ai2.appinventor.mit.edu/?repo=templates.appinventor.mit.edu/trincoll/csp/unit7/templates/DataMap/DataMapTemplate.asc" target="_blank">Data Map App Template</a>.  Once the project opens use Save As to rename your project. 
    </p><p>
    Follow the video tutorial below or the <a href="https://docs.google.com/document/d/1B7XFoyVv8Dk6Ek-xlYzNkZCfCfc4RQ4yFQq6pmpv9Ps/edit?usp=sharing" target="_blank">text tutorial</a> or the <a href="https://docs.google.com/document/d/1wdxBIXOzXy9bAqy1hYF5-SZ7xfPnAK7UZKwz4HK8wbQ/edit?usp=sharing" target="_blank">short handout</a> to complete this app:<br/>
    <iframe allow="autoplay; encrypted-media" allowfullscreen="" frameborder="0" height="470" src="https://www.youtube.com/embed/09NqjxdEvvo?rel=0" width="730"></iframe> <br/>
        (<span class="yui-non"><a href="https://teachertube.com/video/data-map-app-tutorial-476361" target="_blank">TeacherTube Version</a></span>)
     </p><h3>Projects/Enhancements:</h3>
      Your instructor may ask you to do some or all of the following  enhancement projects.
    <ol>
    <li style="margin-bottom: 5px;">
	<img src="../_static/assets/img/usmap3color.png" width="300" style="float:right"/>
    <b>Data Visualization with Colors:</b> Create a map visualization with 3 color shades for the states to show the differences in one of the data columns in the <a href="https://drive.google.com/open?id=1JbW50ohaUMmZl3h3fo4ntlxW5g8P8NCnuSoBbeCg3J8" target="_blank">data spreadsheet</a>. For example, in the preview video at the top of this lesson and the map image to the right, the states that had less than 10 death rate by firearms for every 100K people in 2016 are shown in light blue, the states that had between 10 and 20 deaths in medium blue, and the states that had the greater than 20 death rate by firearms in dark blue. To create a similar color scheme based on the data, add an if block and use the blue mutator to make it into a three-way choice: <i>if/else-if/else</i> block and set up the 3 ranges and use the <i>Any Component</i> block for set <i>Polygon.FillColor</i>. <br/><b>Cite Your Source.</b> When working with data, it is important to reference when and where the data comes from. If you haven't already, be sure to change the label's text property to say "Click on each state to see 2016 CDC Data". <br/><b>Error Checking: </b>You may run into errors with the data in this spreadsheet. Often we have to clean data or check for special conditions before we use it. Some of the values are empty in the spreadsheet which may cause errors. You should first save the data in a local variable and check that it is not empty text to avoid errors.
        
    </li>
    <li style="margin-bottom: 5px;">
    <b>Procedure with Parameters:</b> Our app would be even more useful if it let the user decide which data to present. 
    Add 3 buttons to choose between different columns of data in the spreadsheet, for example Uninsured Rate, Firearms Death Rate, Overdose Rate.  
    Refactor your code to add a procedure with parameters for the column number and the label of that column and have button click event handlers call this procedure. 
    This procedure will update the map data (and color code it if you did extension 1) using a loop through the states like in File.GotText (except for the first two lines of code that set up the global data variable) but using your parameter variables. 
    In fact, you can refactor your code so that File.GotText also calls this procedure with some default variables after setting up the global data variable in the first two lines of code. 
    Note that if you choose data columns where the data is not in the same ranges (for example population), you may need more parameters to adjust the limit values where the color shades change in your if statements. 
    You can also change the spreadsheet to include other data, see <a href="https://www.cdc.gov/nchs/pressroom/stats_of_the_states.htm" target="_blank">CDC State Data</a>.  
    Note that this procedure with parameters meets the requirements of the AP Performance task. Thank you to Mobile CSP teacher Jocelyn Humphries from John Jay High School in NY for this awesome coding idea!
    </li>
    <li style="margin-bottom: 5px;">
    <b>WebViewer:</b> Note the last column in the <a href="https://drive.google.com/open?id=1JbW50ohaUMmZl3h3fo4ntlxW5g8P8NCnuSoBbeCg3J8" target="_blank">data spreadsheet</a>, contains a url for more information about the state on the CDC site. Use a webviewer to display a url that joins the base url <a href="https://www.cdc.gov" target="_blank">https://www.cdc.gov</a> with the url in the last column (#8) when each state is clicked by using the <i>Map.FeatureClick</i> event handler.  To get the URL data, you can find the index of the state feature that is clicked by using an <a href="http://appinventor.mit.edu/explore/ai2/support/blocks/lists.html#indexinlist" target="_blank">Index in List block</a> with the feature that is clicked and the list <i>FeatureCollectionStates.Features</i>. Once you have this index, you can use it to select that state’s data from the global data list. Remember that this is a list of lists, so once you find the correct list of data for that state, you will need to use select again to find the URL data which is at index 8. 
      </li>
    <li style="margin-bottom: 5px;">
    <b>Weather <span class="hover vocab yui-wk-div" data-id='API'>API</span> (Optional, requires registration to get a free <span class="hover vocab yui-wk-div" data-id='API'>API</span> key):</b> <a href="https://en.wikipedia.org/wiki/Application_programming_interface" target="_blank">APIs</a> can be used to read in real-time current data, for example the current weather report for a clicked state.  Read about the OpenWeatherMap <span class="hover vocab yui-wk-div" data-id='API'>API</span> here: <a href="https://openweathermap.org/current" target="_blank">https://openweathermap.org/current</a>. Try clicking on this example: <a href="https://samples.openweathermap.org/data/2.5/weather?q=London,uk&amp;appid=b6907d289e10d714a6e88b30761fae22" target="_blank">London Sample</a> to get the current weather data in <span class="hover vocab yui-wk-div" data-id='JSON'>JSON</span> format for London. OpenWeatherMap requires a registration key called appid. To get this free key, your instructor should follow the directions at  <a href="https://openweathermap.org/appid" target="_blank">https://openweathermap.org/appid</a> and then tell you the key, for example appid=8bb5e8bedfe6fe3f1a44e0a2c04b6540.
        <br/><br/>To build the app, we need to build a url for each clicked state and pull out the main weather description.  To make an <span class="hover vocab yui-wk-div" data-id='API'>API</span> request, you will need a <a href="http://ai2.appinventor.mit.edu/reference/components/connectivity.html#Web" target="_blank">Connectivity/Web component</a> in your UI (this is different than the WebViewer component).
		<ul>
			<li style="margin-bottom: 5px;">Use a <i>Map.FeatureClick</i> event handler and set the Web.url to the <span class="hover vocab yui-wk-div" data-id='API'>API</span> url like <b>http://api.openweathermap.org/data/2.5/weather?q=<em>state</em>\&amp;appid=<em>yourAppId</em></b> using a join to put in the state name which is the title of the clicked feature (using an Any Feature Component) and the appid (<span class="hover vocab yui-wk-div" data-id='API'>API</span> key) that you got from your instructor (you can try the Mobile CSP one appid=8bb5e8bedfe6fe3f1a44e0a2c04b6540 but it may be blocked if too many people are using it).</li>
			<li style="margin-bottom: 5px;">Then, call <i>Web1.get</i>. This will fetch that webpage and then go to the event-handler <i>When Web1.GotText</i>.</li>
			<li>In the <i>GotText</i> event handler, you will need to parse the result to find the weather main description, for example “clouds” below:
			{"coord":{"lon":-78.39,"lat":43.1},"weather":[{"id":804,"main":"Clouds","description":"overcast clouds","icon":"04n"}. The <a href="http://appinventor.mit.edu/explore/ai2/support/blocks/lists.html#lookupinpairs" target="_blank">List/Lookup in pairs block</a> can pull out the weather key and then the main key in the result text. The following code will pull out this part of the <span class="hover vocab yui-wk-div" data-id='JSON'>JSON</span> data returned from this <span class="hover vocab yui-wk-div" data-id='API'>API</span> which you can then display in a label:<br/>
			<img src="../_static/assets/img/lookupinpairs.png" width="700px"/></li>
		</ul>
    </li>
    </ol>

Summary
--------

.. raw:: html

    <p>
    In this lesson, you learned how to:
      <div class="yui-wk-div" id="summarylist">
    </div>
    
Still Curious
-------------
.. raw:: html

    <ul>
    <li>
    If you are curious about other APIs, here’s a list of different public APIs that you can use in apps: <a href="https://github.com/toddmotto/public-apis">https://github.com/toddmotto/public-apis</a>.</li>
    <li>
    Here is a great map visualization of <a href="https://native-land.ca/" target="_blank">Native Lands (https://native-land.ca/)</a> and an <a href="https://native-land.ca/api-docs/" target="_blank"><span class="hover vocab yui-wk-div" data-id='API'>API</span></a> to use it.</li>
    </ul>


Self-Check
-----------

.. raw:: html

    <p>
    <p>Review the following vocabulary.</p>
    <table align="center">
    <tbody>
    <tr>
    <td><span class="hover vocab yui-wk-div" data-id="CSV files">CSV Files</span>
    <br/><span class="hover vocab yui-wk-div" data-id="JSON">JSON</span>
    <br/><span class="hover vocab yui-wk-div" data-id="GeoJSON">GeoJSON</span>
    <br/><span class="hover vocab yui-wk-div" data-id="API">API</span>
    <br/><span class="hover vocab yui-wk-div" data-id="cleaning data">cleaning data</span>
    </td>
    </tr>
    </tbody>
    </table>
    

Reflection: For Your Portfolio
-------------------------------

.. raw:: html

    <p><div class="yui-wk-div" id="portfolio">
    <p>Answer the following portfolio reflection questions as directed by your instructor. Questions are also available in this <a href="https://docs.google.com/document/d/1LyloPyUcCJ6aLVjh4Ybjyj9AcFODEuT-Rvl-VtiQVjw/copy" target="_blank" title="">Google Doc</a> where you may use File/Make a Copy to make your own editable copy.</p>
    <div style="align-items:center;"><iframe class="portfolioQuestions" scrolling="yes" src="https://docs.google.com/document/d/e/2PACX-1vRKcE7yejaQb6xRPcQjO4TUPkW6TbYVySG2naxoTmUl5J_r7XABwn0izcfvUyiz7M7ZH2FvKKwJl3vT/pub?embedded=true" style="height:30em;width:100%"></iframe></div>
    </div>
    </div>