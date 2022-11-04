.. raw:: html 

   <div class="logo-header"  id="student-logo"  > <img class="align-center" src="../_static/Mobile_CSP_Logo_White_transparent.png" width="250px"/> </div>

Pseudo Random Numbers
=====================

.. raw:: html

        <div class="MCSP-lesson-content">
    <script>
      $(document).ready(function() {
        generateSummary(EKmapping['4.07']);
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
        "deterministic":"A process is deterministic if it is completely predictable. A PRNG is deterministic. An example would be a PRNG.",
        "PRNG": "A pseudo random number generator (PRNG) is an algorithm that generates a sequence of numbers that appears to be random but is completely determined by the algorithm.  As such, a PRNG is a model or representation of randomness.",
        "modular arithmetic":"Modular arithmetic is a system of arithmetic for whole numbers where the numbers 'wrap around' upon reaching a certain value known as the modulus. An example would be clock arithmetic. On a 12-hour clock, the time wraps around to 1 after 12 o'clock.",
        
      };      */
    </script>
    <h3 id="est-length">Time Estimate: 45 minutes</h3>
    

Introduction and Goals
-----------------------

.. raw:: html

    <p>
    
    As we saw in the <i>Coin Flip App</i>, App Inventor contains blocks
    that will generate random numbers and we can use those random numbers
    to <span class="hover vocab yui-wk-div" data-id="simulate">simulate</span> real-world events.
    
    But how does App Inventor create those numbers? How does a computer do
    randomness?
    
    <p>This <a href="https://www.khanacademy.org/computing/computer-science/cryptography/crypt/v/random-vs-pseudorandom-number-generators" target="_blank">
    Khan Academy video by Brit Cruise</a> provides a nice conceptual overview of
    <i>pseudorandomness</i> and how it differs from true randomness. The type 
    of <span class="hover vocab yui-wk-div" data-id='PRNG'>pseudorandom number generator (PRNG)</span> described in the video is different
    from the type described in the lessons below.  But the general principles are very much the
    same.
    </p>
	<p>
		<div><b>Learning Objectives:</b>&nbspI will learn to</div>
		<ul>
		<li>use <span class="hover vocab yui-wk-div" data-id="modular arithmetic">modular arithmetic</span> to produce a remainder, which can be used to create pseudorandom numbers</li>
		<li>recognize the difference between random and pseduorandom numbers, and the implciations of this difference on real world applications</li>
		</ul>
		<div><b>Language Objectives:</b>&nbspI will be able to</div>
		<ul>
		<li>examine a series of numbers and discuss whether or not they look random</li> 
		<li>use target vocabulary, such as <span class="hover vocab yui-wk-div" data-id="PRNG">random number generator</span>, <span class="hover vocab yui-wk-div" data-id="modular arithmetic">modular arithmetic</span>, and <span class="hover vocab yui-wk-div" data-id="mod operator">mod operator</span> while considering how a computer models randomness, with the support of concept definitions and <a href="https://docs.google.com/presentation/d/1YsJJ7IwEEpQGLqSizFhIFJVIw5TfDc5LqDtCSD-o42E/copy" target="_blank" title="">vocabulary notes</a> from this lesson</li>
		</ul>
	</p>
    

Learning Activities
--------------------

.. raw:: html

    <ul align="center" style="list-style: none; margin: 0; padding: 0; background: lightgrey">
	<li style="display: inline"><a href="https://docs.google.com/document/d/1lYZj_SvHICcmrhKsE6mM--k_lubcBOeHHy33XhJ62fA/" target="_blank" title="">text-version</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://docs.google.com/presentation/d/1VWdfhZcI20fjG9koi6hkJnW5eiA85vnoeO6RVJGD9j4" target="_blank">slides</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://www.youtube.com/watch?v=IZ56vqQZux4" target="_blank">YouTube video Part I</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://youtu.be/BLSdUYtQmeo" target="_blank" title="">YouTube video Part II</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://youtu.be/FLdjrnXHajY" target="_blank" title="">YouTube video Part III</a></li>
	</ul>
	<ul align="center" style="list-style: none; margin: 0; padding: 0; background: lightgrey">
	<li style="display: inline"><a href="https://www.youtube.com/watch?v=7Wkubf1PrWg&feature=emb_imp_woyt" target="_blank">Slot Machine Video</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="http://www-math.ucdenver.edu/~wcherowi/clockar.html" target="_blank">Exercises</a></li>
	</ul> 
	
	<p><h3>Computer Randomness</h3>
    <p>It is difficult for a computer to create a truly random event.
    Therefore, computers use a form of randomness known as <i><b>pseudo                                                                          
    randomness</b></i> -- that is, they <span class="hover vocab yui-wk-div" data-id="simulate">simulate</span> randomness.
    </p>
    <p>A pseudo random event looks random but is completely predictable -- 
    we say it is <span class="hover vocab yui-wk-div" data-id='deterministic'>deterministic</span> because its output can be known by someone 
    who knows how the event was programmed. What looks random to the 
    user is actually the result of a completely predictable mathematical algorithm.
    </p>
    <h3>How does a PRNG Work</h3>
    
.. youtube:: IZ56vqQZux4
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    (<a href="http://www.teachertube.com/video/358492" target="_blank">
    Teacher Tube version</a>)
  
    <p>
    
.. fillintheblank:: mcsp-4-7-1

    .. raw:: html
    
    	<p>Suppose our PRNG generates the following sequence of numbers and suppose you seeded it with the value 11:</p>
    	<pre>... 14 11 5 24 2 0 17 15 8 4 ...</pre>
    	<br />
    	<p>What would be the next number after 11 generated by the PRNG?</p>
    	</pre>

    - :5: That's right! The <i>seed</i> tells the PRNG where to begin in the sequence ... 14 11 5 24 2 0 17 15 8 4 ... If the PRNG begins at 11, the next value after 11 will be 5 and then the next will be 24, and so on.
      :x: Try again. What's the next value generated after 11 in the sequence?


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


.. fillintheblank:: mcsp-4-7-2

    .. raw:: html
    
    	<p>Suppose your PRNG uses the following formula:</p>
    	<p><i><span style="font-size: +1;">X</span><sub>i+1</i></sub> = <span style="font-size: +1;">X</span><sub>i</sub> * 2 + 1</i></p>
    	<p>And suppose that <i><span style="font-size: +1;">X</span><sub>1</sub></i> is 12.  What value will <i><span style="font-size: +1;">X</span><sub>2</sub></i> have?</p>

    - :25: Yes. 12 * 2 + 1 equals 25.
      :x: Try again. What's 12 * 2 + 1?


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. fillintheblank:: mcsp-4-7-3

    .. raw:: html
    
    	<p>Suppose your PRNG uses the following formula:</p>
    	<p><i><span style="font-size: +1;">X</span><sub>i+1</i></sub> = <span style="font-size: +1;">X</span><sub>i</sub> * 2 + 1</i></p>
    	<p>And suppose that <i><span style="font-size: +1;">X</span><sub>1</sub></i> is 10. What are the <b>next three numbers</b> that the formula would generate? Type your answers into the text box, separating the numbers by a single comma.</p>

    - :21,43,87: Good job. Now you see how we can use a simple mathematical formula to generate a sequence of numbers. But does the sequence look random enough?
      :21, 43, 87: Good job. Now you see how we can use a simple mathematical formula to generate a sequence of numbers. But does the sequence look random enough?
      :21 43 87: Good job. Now you see how we can use a simple mathematical formula to generate a sequence of numbers. But does the sequence look random enough?
      :x: Try again. What's 10 * 2 + 1?


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

	<h3>Clock Arithmetic and the MOD operator</h3>

    <p>
    
    The <span class="hover vocab yui-wk-div" data-id="mod operator">MOD operator</span> gives the remainder when one number is divided by another. For example, 3 MOD 2 is 1 because 3 can be divided by 2 once with a remainder of 1. In the AP CSP exam, the a MOD b operator is defined as the remainder of a divided by b for positive numbers a and b. App Inventor also has a "Modulo of" block. In arithmetic expressions, the <span class="hover vocab yui-wk-div" data-id='mod operator'>MOD operator</span> has the same precedence as the * and / operators which means that MOD, *, and / are evaluated before + and - unless there are parentheses. 
    
    <p>We use <b>modulo</b> 12 arithmetic every day when we read clocks with 12 hours.
    
    
    
.. youtube:: BLSdUYtQmeo
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    </p>

    <p>
    
.. fillintheblank:: mcsp-4-7-4

    Evaluate the following expression: (8 + 14) mod 13. |blank|

    - :9: That's right! (8 + 14) mod 13 = 22 mod 13 = 9
      :x: Try again.


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


.. fillintheblank:: mcsp-4-7-5

    Evaluate the following expression: (8 + 34) mod 13. |blank|

    - :3: That's right! (8 + 34) mod 13 = 42 mod 13 = 3. This is the same as subtracting 13 from 42 three times: 42 - 13 = 29 - 13 = 16 - 13 = 3.
      :x: Try again.


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


.. fillintheblank:: mcsp-4-7-6
    :casei:

    .. raw:: html
    	
    	<p>Evaluate the following expression.</p>
    	<p>3<sup>3</sup> mod 5</p>

    - :2: 
    	.. raw:: html
    		
    		<p>3<sup>3</sup> mod 5 = 27 mod 5 = 2</p>
      :x: Try again.


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. fillintheblank:: mcsp-4-7-7
	
	.. raw:: html
	
		<p>Suppose your PRNG uses the following formula:</p>
		<p><span style="font-size: +1;">X</span><sub>i+1</sub> = (<span style="font-size: +1;">X</span><sub>i</sub> * 2 + 1) <i>mod</i> 13</p>
		<p>What would the next number be if the current number is 10?</p>
		
	- :8: Yes, the value of (10 * 2 + 1) mod 13 is 21 mod 13, which is 21 -13, which is 8.
	  :x: Try again. What's 21 mod 13?
	  

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    
.. fillintheblank:: mcsp-4-7-8

    .. raw:: html
    
    	<p>Suppose your PRNG uses the following formula:</p>
    	<p><span style="font-size: +1;">X</span><sub>i+1</sub> = (<span style="font-size: +1;">X</span><sub>i</sub> * 2 + 1) <i>mod</i> 13</p>
    	<p>What would the next five numbers be if the current number is 10? Separate the numbers in your sequence by commas.</p>

    - :8,4,9,6,0: Good. As you can see, this PRNG is a better model than our first try, at least in the sense the numbers in the sequence jump around more rather than always increasing.
      :8, 4, 9, 6, 0: Good. As you can see, this PRNG is a better model than our first try, at least in the sense the numbers in the sequence jump around more rather than always increasing.   
      :8 4 9 6 0: Good. As you can see, this PRNG is a better model than our first try, at least in the sense the numbers in the sequence jump around more rather than always increasing.
      :x: Try again.


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    <p></p><p>If you want to practice your <span class="hover vocab yui-wk-div" data-id='modular arithmetic'>modular arithmetic</span> before moving on, 
    here are some 
    <a href="http://www-math.ucdenver.edu/~wcherowi/clockar.html" target="_blank">nice exercises</a>, with links to the answers.</p>
    <h3>An Improved PRNG</h3><br/><br/>
.. youtube:: FLdjrnXHajY
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    <h3>How Does a Slot Machine Work</h3>
    Slot machines are <i>special purpose computers</i> that contain a 
    <i>random number generator</i> chip.  This no-nonsense video explains
    how they work and dispels some of the many myths that surround them. 
    The bottom line: what is the only way to win on a slot machine?.
    
    
.. youtube:: 7Wkubf1PrWg
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    

Summary
--------

.. raw:: html

    <p>
    In this lesson, you learned how to:
      <div class="yui-wk-div" id="summarylist">
    </div>
   

Still Curious?
---------------

.. raw:: html

    <p>
    <p>Learn about how a Russian crew was able to figure out how <i>not</i> to lose at slot machines in this <a href="https://www.npr.org/sections/money/2017/05/24/529865107/episode-773-slot-flaw-scofflaws" target="_blank">Planet Money podcast</a>.</p>
    <p>Read more about <a href="http://en.wikipedia.org/wiki/Linear_congruential_generator" target="_blank">linear congruential generators</a> on Wikipedia. </p>
    <br/><br/><span class="hover vocab yui-wk-div" data-id="PRNG">PRNG</span>s are also useful when securing the Internet, which is covered later in the course. For now, you can watch this video about CloudFlare and how lava lamps are helping to keep the Internet secure.<br/>
.. youtube:: 1cUUfMeOijg
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

Self-Check
-----------

.. raw:: html

    <p>
    
    Here is a table of the technical terms introduced in this lesson. Hover over the terms to review the definitions.
    <table align="center">
    <tbody>
    <tr>
    <td><span class="hover vocab yui-wk-div" data-id="deterministic">deterministic</span>
    <br/><span class="hover vocab yui-wk-div" data-id="PRNG">PRNG</span>
    <br/><span class="hover vocab yui-wk-div" data-id="modular arithmetic">modular arithmetic</span>
    <br/><span class="hover vocab yui-wk-div" data-id="mod operator">mod operator</span>
    </td>
    </tr>
    </tbody>
    </table>
    
.. quizly:: mscp-4-7-9
    
    
    :quizname: quiz_loop_sum_even_numbers
    <br/>

Reflection: For Your Portfolio
-------------------------------

.. raw:: html

    <p><div class="yui-wk-div" id="portfolio">
    <p>Answer the following portfolio reflection questions as directed by your instructor. Questions are also available in this <a href="https://docs.google.com/document/d/1RWTQYEtf5O8aDqB3PuZLR4fwTz4tNpfXabTZCmuG-8k/copy" target="_blank">Google Doc</a> where you may use File/Make a Copy to make your own editable copy.</p>
    <div style="align-items:center;"><iframe class="portfolioQuestions" scrolling="yes" src="https://docs.google.com/document/d/e/2PACX-1vQUAF9tceieNqix0Ege3-afklwB-jESOLLP-Gz09kOLfbtLwhRagDDaNRNEoxLiKURIcxO0Hgsj4Cpn/pub?embedded=true" style="height:30em;width:100%"></iframe></div>
    <!--&lt;p&gt;Create a page named &lt;b&gt;&lt;i&gt;PRNGs&lt;/i&gt;&lt;/b&gt; under the
    &lt;i&gt;Reflections&lt;/i&gt; category of your portfolio and answer the following questions.
    &lt;/p&gt; 
    
    &lt;ol&gt;
    &lt;li&gt;Consider the following Dilbert cartoon?  Would it be possible for a PRNG 
    to spit out 6 &lt;i&gt;NINE&lt;/i&gt;s in a row?  
    
    &lt;br&gt;
    &lt;img src=&quot;assets/img/dilbert.jpg&quot;&gt;
    &lt;/li&gt;
    &lt;li&gt;Are slot machines fair? Why or why not?
    &lt;/li&gt;&lt;li&gt;Is it possible to devise a method that would allow you to win consistently on a
    slot machine?
    &lt;/li&gt;&lt;/ol&gt;-->
    </div>
    </div>
