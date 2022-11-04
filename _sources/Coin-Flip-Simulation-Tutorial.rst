.. raw:: html 

   <div class="logo-header"  id="student-logo"  > <img class="align-center" src="../_static/Mobile_CSP_Logo_White_transparent.png" width="250px"/> </div>

Coin Flip Simulation Tutorial
=============================

.. raw:: html

        <div class="MCSP-lesson-content">
    <script>
      $(document).ready(function() {
        generateSummary(EKmapping['4.05']);
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
        "model":"A model is an abstraction that provides a simplified representation of some complex object or phenomenon.",
        "random":"Randomness is the lack of pattern or regularity.  A random sequence of events has no order or patten.",
        "random event": "A random event is an event that cannot be predicted with certainty. Examples would include flipping a fair coin, rolling a die, picking a card from a well shuffled deck.",
        "random number generator":"A random number generator (PRNG) is an algorithm that generates a sequence of numbers that seem to occur in random order.", 
      };      */
    </script>
    <h3 id="est-length">Time Estimate: 45 minutes</h3>
    

Introduction and Goals
-----------------------

.. raw:: html

    <p>
    <table><tbody>
	<tr>
		<td colspan=2>
			<p><b><i>Coin Flip</i></b> is an app that simulates a coin flip. In fact, because it uses App Inventor's <span class="hover vocab yui-wk-div" data-id='random number generator'>random number generator</span>,
			it may actually be fairer than a real coin flip. That is, it may come closer than a real coin flip to producing "heads" 50% of the time.</p>
			<p>This tutorial has two parts.  In the first part we will build a simple app that simulates
			a coin flip.  The coin will be represented by a global variable.  Heads will be represented
			by 1 and tails by 2, and flipping the coin will be a matter of randomly assigning 1 or 2 to 
			that variable.  The result will be displayed as an image depicting either the heads or tails
			of a coin.</p>
			<p>In part two, we will extend the app to perform the coin flip many times in order to experiment with the idea of "randomness" or "fairness".  If 
			you flip a real coin lots of times, it should come up heads close to 50% of the time.  If 
			you simulate a coin flip lots of times, it should also come up heads close to 50% of the time
			-- unless the "randomness" that's built into App Inventor is not a very good <span class="hover vocab yui-wk-div" data-id='model'>model</span> of true
			randomness. We'll explore the idea of randomness later in this Unit. </p>
		</td>
	</tr>
    <tr>
		<td valign="top">
			<iframe allowfullscreen="" frameborder="0" height="375" src="https://www.youtube.com/embed/YOGEBNeA8tA" width="275"></iframe>
		</td>
		<td valign="top">
			<div><b>Learning Objectives:</b>&nbspI will learn to</div>
			<ul>
			<li>create an artifact that uses randomness and simulates a <span class="hover vocab yui-wk-div" data-id='model'>model</span></li>
			<li>create a simple <span class="hover vocab yui-wk-div" data-id='model'>model</span> of a coin flip</li>
			<li>use the <span class="hover vocab yui-wk-div" data-id='random'>random</span> number block to generate <span class="hover vocab yui-wk-div" data-id='random'>random</span> values in a specific range</li>
			<li>use a conditional statement, <i>IF/Else</i>, to evaluate a variable and follow an algorithm based on the value of a variable</li>
			<li>use a <i>For each number</i> loop to repeatedly simulate the flipping of the coin</li>
			</ul>
			<div><b>Language Objectives:</b>&nbspI will be able to</div>
			<ul>
			<li>use target vocabulary, such as <span class="hover vocab yui-wk-div" data-id="model">model</span>, <span class="hover vocab yui-wk-div" data-id="random">random</span>, <span class="hover vocab yui-wk-div" data-id="random event">random event</span>, and <span class="hover vocab yui-wk-div" data-id="random number generator">random number generator</span> while describing app features and User Interface with the support of concept definitions and <a href="https://docs.google.com/presentation/d/1YsJJ7IwEEpQGLqSizFhIFJVIw5TfDc5LqDtCSD-o42E/copy" target="_blank" title="">vocabulary notes</a> from this lesson</li>
			</ul>		
		</td>
    </tr>
	</tbody></table>
    

Learning Activities
--------------------

.. raw:: html

    <ul align="center" style="list-style: none; margin: 0; padding: 0; background: lightgrey">
	<li style="display: inline"><a href="https://docs.google.com/document/d/1FEGO2E98mg10euV4HQsJlZcqYKlFjcQtyzELQkxe-68" target="_blank" title="">text-version</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://docs.google.com/document/d/1W8qqxSIrTE8abfO_UPksL1lzxKQb84BSrgqoag9CrsA/edit?usp=sharing" target="_blank">short handout</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://www.youtube.com/watch?v=4TwtOnrTCiA" target="_blank">YouTube video Part I</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://www.youtube.com/watch?v=7ifaRGDWHEU" target="_blank" title="">YouTube video Part II</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://docs.google.com/document/d/1AKHpiQ87bE4W1YzHlAFh2uNAHuEtdMOCQVV6HfxfDzc" target="_blank" title="">project extensions</a></li>
	</ul> 
	
	<p><h3>A Short Experiment</h3>
    Before getting started on the Coin Flip app, try this simple experiment:
    
    <blockquote style="font-size: 1.0em;">
    <ul>
    <li>If you flip a <b><i>fair coin</i></b> 20 times -- any type of coin will do -- how many heads would you expect to get?  Write down your answer.
    
    </li><li>Now flip the coin 20 times and count the number of heads. Write down the count.
    
    </li><li>Did the count match your explanation?  Based on this experiment, could you conclude that your coin is fair or <i>biased</i> (not fair).
    </li></ul>
    </blockquote>
    <p>If you perform this experiment, heads will often come up 10 times, but not always, even though, supposedly, the probability of getting a head on a fair coin toss is 50%.  
    
    </p><p>The problem with this experiment is you didn't perform enough trials to draw any conclusion about the <i><b>hypothesis</b></i> that this is a fair coin. 
    </p>
    <h3>The Random Block</h3>
    
    In App Inventor, we will use the <span class="hover vocab yui-wk-div" data-id='random'>random</span> block to get pseudo-<span class="hover vocab yui-wk-div" data-id='random'>random</span> numbers. In the AP CSP exam, the function <span class="hover vocab yui-wk-div" data-id='RANDOM'>RANDOM</span>(1,3) is used to return a <span class="hover vocab yui-wk-div" data-id='random'>random</span> number from 1 to 3 (including 1, 2, or 3). 
    <table border="">
    <tbody><tr><th>AP Pseudocode</th> <th>App Inventor</th></tr>
    <tr><td>x = <span class="hover vocab yui-wk-div" data-id='random'>RANDOM</span>(1,3)</td> <td><img src="../_static/assets/img/setxtorandomint.png" width="350px"/></td></tr>
    </tbody></table>
    <h3>Tutorial Part I: Simulating a Coin Flip</h3>
    <p>To get started, <a href="http://ai2.appinventor.mit.edu/?repo=templates.appinventor.mit.edu/trincoll/csp/unit4/templates/CoinFlipMediaOnly/CoinFlipMediaOnly.asc" target="_blank">
    open App Inventor with the Coin Flip Media Only template</a>. If the template does not open, download the <a href="http://templates.appinventor.mit.edu/trincoll/csp/unit4/templates/CoinFlipMediaOnly/CoinFlipMediaOnly.aia" target="_blank">.aia file</a>, go to <a href="http://ai2.appinventor.mit.edu" target="_blank">App Inventor</a> and do File/Import and import in the downloaded .aia file.
     
    This will open a project that contains the images you will need in this lesson. Then use the <i>Projects --> Save Project As</i> option to rename your project to <i>CoinFlip</i>.  
    </p>
    <p>You can either watch the <i>video tutorial</i>, <i>read the text tutorial</i> or use the <i>short handout</i>.</p>
    
.. youtube:: 4TwtOnrTCiA
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    <h3>Optional Enhancements for Part I</h3> 
    
    <p>Before you begin these optional enhancements, use the <i>Projects --> Save Project As</i> option to save your app from Part I as "Coin Flip Enhancements" so that you don't lose the original code which is needed for Part II.</p>
	
	<p>Here are some optional creative enhancements to enhance the <i>CoinFlip</i> app and help build your programming skills. (<a href="https://docs.google.com/document/d/1AKHpiQ87bE4W1YzHlAFh2uNAHuEtdMOCQVV6HfxfDzc" target="_blank">text version</a>)
    
    <ol>
    <li style="margin-bottom: 5px;">Modify the app so that the user can also shake the phone to flip the coin. 
    (HINT: Use the <a href="http://ai2.appinventor.mit.edu/reference/components/sensors.html#AccelerometerSensor" target="_blank">
      Accelerometer Sensor</a>.)  NOTE: Instead of copying and pasting the coin-flip
      algorithm, you'll want to use a <i><b>procedure</b></i> to reduce complexity in 
      your code.  
    </li>
    <li style="margin-bottom: 5px;"> Modify your app so that “heads” or “tails” is spoken when the coin is flipped. (HINT: Use the
    <a href="http://ai2.appinventor.mit.edu/reference/components/media.html#TextToSpeech" target="_blank">
    TextToSpeech</a> component.)
    </li>
    <li style="margin-bottom: 5px;">Modify the event handler in the Coin Flip app to use a <span class="hover vocab yui-wk-div" data-id='random'>random</span> fraction block instead of 
    <span class="hover vocab yui-wk-div" data-id='random'>random</span> integer. (HINT: A <i><span class="hover vocab yui-wk-div" data-id='random'>random</span> fraction</i> is a decimal number between 
    0 and 1, not including 1.  Some examples: 0, 0.25, 0.33, 0.5, 0.66, 0,75, 0.99.)
    </li>
    <li style="margin-bottom: 5px;"> <b>If/else Algorithm</b> You now have an app that can flip a two-sided coin. 
    Modify your app that so that it can flip a 
    <a href="http://www.statisticool.com/3sided.htm" target="_blank">three-sided coin</a>. 
    (Hint: You will need an if/else block with three conditions.   You’ll need a third image 
    for this problem; here’s one that is openly licensed: 
    <a href="../_static/assets/img/Coin-edge.gif" target="_blank">coin on edge</a>.)
    </li>
    <li style="margin-bottom: 5px;">According to 
    <a href="http://mathtourist.blogspot.com/2011/02/penny-bias.html" target="_blank">this report</a>, if you stand a 
    bunch of Lincoln pennies on their edge and then bang the table, 
    they have a strong bias toward coming up heads. Let’s suppose 
    the coin has a 70% chance of coming up heads (30% tails) in this 
    experiment.  Create a <span class="hover vocab yui-wk-div" data-id='model'>model</span> to simulate this biased coin. Hint: You will need to use the <span class="hover vocab yui-wk-div" data-id='random'>random</span> fraction block and use a &lt; in your if block.
    </li>
    <li><b>Real World Statistical Simulations:</b> use <span class="hover vocab yui-wk-div" data-id='random'>random</span> numbers to predict or simulate real world situations. For example, Mobile CSP teacher Ingrid Roche has her students in Boston Public Schools look at <a href="https://www.aclum.org/en/ending-racist-stop-and-frisk" target="_blank">racial profiling in Boston police-civilian encounters</a> to see if the <a href="https://www.census.gov/quickfacts/fact/table/US/RHI125217" target="_blank">racial demographics of the U.S. or state population</a> match <a href="https://openpolicing.stanford.edu/findings/" target="_blank">the racial demographics of police stop rates</a>. 
    
    </li></ol>

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    <h3>Tutorial Part II:  Repeating the Coin Flip N Times</h3>
    <p>Open your original app from Part I (without the enhancements) and use the <i>Projects --> Save Project As</i> option to save your app from part I as <i>CoinFlipExperiment</i> before continuing with this part of the tutorial.  In this part, we will revise the User Interface and use a loop to repeat the coin flip <i><b>N</b></i> times, keeping count of the number of times it comes up heads.  This will allow us to calculate the percentage of heads, which should be close to 50%.  Let's see how it goes!
    <br/><br/>
	
.. youtube:: 7ifaRGDWHEU
        :width: 650
        :height: 415
        :align: center
    
Summary
--------

.. raw:: html

    <p>
    In this lesson, you learned how to:
      <div class="yui-wk-div" id="summarylist">
    </div><br/>

Still Curious?
---------------

.. raw:: html

    <p>
    <p>Are coin flips fair?  While it might be the case that the coin itself is fair — i.e., it favors neither heads nor tails — perhaps the act of flipping a coin is not fair.  This <a href="http://www.npr.org/templates/story/story.php?storyId=1697475" target="_blank">NPR story</a> reports on experiments that suggest that coin flips are slightly biased towards heads.</p>
    

Self-Check
-----------

.. raw:: html

    <p>
    
    Here is a table of the technical terms introduced in this lesson. Hover over the terms to review the definitions.
    <table align="center">
    <tbody>
    <tr>
    <td><span class="hover vocab yui-wk-div" data-id="model">model</span>
    <br/><span class="hover vocab yui-wk-div" data-id="random">random</span>
    <br/><span class="hover vocab yui-wk-div" data-id="random event">random event</span>
    <br/><span class="hover vocab yui-wk-div" data-id="random number generator">random number generator</span>
    </td>
    </tr>
    </tbody>
    </table>
    
.. mchoice:: mcsp-4-5-1
    :random:
    :practice: T
    :answer_a: Choosing a ball from a black jar filled with red and green balls. 
    :feedback_a: Choosing a ball from a jar is a random event.
    :answer_b: Rolling a 12-sided die. 
    :feedback_b: Rolling a single die is a random event.
    :answer_c: Counting by 2s up to 20. 
    :feedback_c: We’re in the learning zone today. Mistakes are our friends!
    :answer_d: Flipping a coin that has 3 sides. 
    :feedback_d: It may be difficult to imagine a 3-sided coin, but we will see one in the next lesson.
    :answer_e: Dealing a hand of poker.
    :feedback_e: Assuming the deck is properly shuffled, dealing a poker hand is random.
    :correct: a,b,d,e

    Which of the following would be examples of random events? 


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. mchoice:: mcsp-4-5-2
    :random:
    :practice: T
    :answer_a: 1 or 3
    :feedback_a: This is challenging, but rewarding! 1 and 3 are two of the possible values, but not all of them.
    :answer_b: 1, 2, or 3
    :feedback_b: This <i>random integer</i> block will return a random value between 1 and 3, inclusive.
    :answer_c: 1 or 2
    :feedback_c: This is challenging, but rewarding! 1 and 2 are two of the possible values but not all of them.
    :answer_d: 1
    :feedback_d: This is challenging, but rewarding! 1 is one of the possible values but not all of them.
    :correct: b

    For the following block what possible values would be assigned to X? 

    .. raw:: html

        <img class="yui-img" src="../_static/assets/img/setxtorandomint.png"/>


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. fillintheblank:: mcsp-4-5-3
    :casei:

    For the following block what value would be assigned to Label1? Type your answer into the text box. (Spelling counts. Don't use quotes.). 

    .. raw:: html

        <img class="yui-img" src="../_static/assets/img/buggyif.png"/> |blank|

      :Tails: Don’t worry, it’s hard! Let’s go back and try it again...
    - :Heads: Correct!
      :x: This code segment is a bit strange.  It will always produce "Heads" because the random integer will always be 1.


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


.. mchoice:: mcsp-4-5-4
    :random:
    :practice: T
    :answer_a: A. 0
    :feedback_a: 
    :answer_b: B. 0.99
    :feedback_b: 
    :answer_c: C. 0.5
    :feedback_c: 
    :answer_d: D. 1
    :feedback_d: That's right! The random-fraction block cannot generate the value 1.
    :correct: d

    Which of the following values could NOT be generated by the random-fraction block?


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. fillintheblank:: mcsp-4-5-5
    :casei:

    For the following block what value would be assigned to Label1? Type your answer into the textbox. (Spelling counts. Don't use quotes.). 

    .. raw:: html

        <img class="yui-img" src="../_static/assets/img/buggyif2.png"/> |blank|

      :Heads: If it were easy, you wouldn’t be learning anything!
    - :Tails: Correct!
      :x: Try again.


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

 
.. mchoice:: mcsp-4-5-6
    :random:
    :practice: T
    :answer_a:  Step 3: Increase the value of <i>position</i> by <i>1</i>. <br>Step 4: Repeat steps 2 and 3 until the value of <i>count</i> is greater than <i>100</i>.
    :feedback_a: 
    :answer_b:  Step 3: Increase the value of <i>position </i>by <i>1</i>. <br>Step 4: Repeat steps 2 and 3 until the value of <i>position</i> is greater than <i>n</i>.
    :feedback_b: 
    :answer_c:  Step 3: Repeat step 2 until the value of <i>count</i> is greater than <i>100</i>. <br>Step 4: Increase the value of <i>position</i> by <i>1</i>.
    :feedback_c: 
    :answer_d:  Step 3: Repeat step 2 until the value of <i>position</i> is greater than <i>n</i>. <br>Step 4: Increase the value of <i>count</i> by <i>1</i>.
    :feedback_d: 
    :correct: b

    .. raw:: html
    
	    <p><b>AP 2021 Sample Question</b>:  A list of numbers has <i>n</i> elements, indexed from <i>1</i> to <i>n</i>. The following algorithm is intended to display the number of elements in the list that have a value greater than <i>100</i>. The algorithm uses the variables <i>count</i> and <i>position</i>. Steps 3 and 4 are missing.</p>
	    <pre>
	    Step 1: Set count to 0 and position to 1.
	    Step 2: If the value of the element at index position is greaterthan 100, increase the value of count by 1.
	    Step 3: (missing step)
	    Step 4: (missing step)
	    Step 5: Display the value of count.
	    </pre>
	    
	    <p>Which of the following could be used to replace steps 3 and 4 so that the algorithm works as intended?</p>


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. quizly:: mscp-4-5-7
    
    
    :quizname: quiz_if_x_greater_than_y
    
    
.. quizly:: mscp-4-5-8
    
    
    :quizname: quiz_scrambled_sum_loop
    
    

Reflection: For Your Portfolio
-------------------------------

.. raw:: html

    <p><div class="yui-wk-div" id="portfolio">
    <p>Answer the following portfolio reflection questions as directed by your instructor. Questions are also available in this <a href="https://docs.google.com/document/d/1kTL-xQo6lbw3YLrxri7qoWUGpoENe3wIuo0lm_XrSA4/copy" target="_blank">Google Doc</a> where you may use File/Make a Copy to make your own editable copy.</p>
    <div style="align-items:center;"><iframe class="portfolioQuestions" scrolling="yes" src="https://docs.google.com/document/d/e/2PACX-1vT8mrTtDcv5qm8wJVZOyuL-pu4ZodaR6BgUugWTCDtiZ5pr1_MwII752bDgek_GTkK5tXJgIT2lFivK/pub?embedded=true" style="height:30em;width:100%"></iframe></div>
    <!--&lt;p&gt;Create a page named &lt;b&gt;&lt;i&gt;Coin Flip Simulation&lt;/i&gt;&lt;/b&gt; under the &lt;i&gt;Reflections&lt;/i&gt; category of your portfolio and answer the following questions.&lt;/p&gt; 
      &lt;ol&gt;
        &lt;li&gt;Write an &lt;i&gt;if/else statement&lt;/i&gt; to express the following real life situation. Mary likes ice cream and always chooses chocolate unless there is no chocolate in which case she chooses strawberry.  But if there’s no strawberry either then she settles for vanilla, which, for some reason, is always available.  (HINT: You may need to put together more than 1 if/else statement to do this.)&lt;/li&gt;
        &lt;li&gt;&lt;img src=&quot;assets/img/Sum1To4.png&quot; width=&quot;375&quot; align=&quot;left&quot;&gt;We didn’t need it for the loop in this lesson, but the &lt;i&gt;&lt;b&gt;number&lt;/b&gt;&lt;/i&gt; element in the &lt;i&gt;&lt;b&gt;For each number&lt;/b&gt;&lt;/i&gt; loop is a local variable whose value changes automatically on each iteration of the loop.  For example, in this loop number would start at 1 and then go to 2, 3 and 4.   And this value can be used in the body of the loop, as shown in this example.  Given that, trace through this loop and figure out what value global &lt;i&gt;&lt;b&gt;sum&lt;/b&gt;&lt;/i&gt; would have when the loop finishes.&lt;br&gt; 
    &lt;/li&gt;
      &lt;br&gt;  &lt;li&gt;App Inventor’s random-integer block is an abstract model of randomness -- i.e., an abstraction of real randomness such as flipping a real coin. What would you say about the random-integer block if you ran the coin flipping simulation 10,000 times and the result was that it came up heads 55% of the time?&lt;/li&gt;
    
      &lt;/ol&gt;-->
    </div>
    </div>