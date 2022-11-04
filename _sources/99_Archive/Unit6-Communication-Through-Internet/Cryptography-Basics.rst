.. raw:: html 

   <div class="logo-header"  id="student-logo"  > <img class="align-center" src="../_static/Mobile_CSP_Logo_White_transparent.png" width="250px"/> </div>

Cryptography Basics
===================

.. raw:: html

        <div class="MCSP-lesson-content">
    <script>
      $(document).ready(function() {
        generateSummary(EKmapping['6.06']);
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
        "cipher" : "A cipher is a system for creating secret messages.",
        "cryptography":"Cryptography means, literally, 'secret writing'.  The art and science of writing secret messages.",
        "encryption": "Encryption is the process of using a secret key to convert plaintext into ciphertext.",
        "plaintext" : "Plaintext is the unencrypted, readable message.",
        "ciphertext" : "Ciphertext is an unreadable, secret message.",
        "decryption" : "Decryption is the process of using a secret key to convert ciphertext into plaintext.",
        "encryption key" : "The encryption key is a piece of secret data used in by encryption and decryption algorithms.",
        "encryption algorithm" : "The encryption algorithm uses a secret key to encrypt messages.",
        "symmetric encryption" : "In a symmetric encryption system the same key is used for both encryption and decryption.",
        "substitution cipher" : "In a substitution cipher letters from a ciphertext alphabet are substituted for the letters in a plaintext message in a systematic way.",
        "transposition cipher" : "In a transposition cipher letters in the plaintext are rearraged without substitution.",
        "brute force attack" : "In cryptography, a brute force attack attempts to try every possible encryption key to break a secret message.",
        "frequency analysis" : "Frequency analysis counts the occurrence of the letters in an encrypted message in an effort to discover patterns that might reveal the encryption key.",
        "polyalphabetic substitution" : "In a polyalphabetic substitution system multiple alphabets are used to encrypt a single message.", 
        "one time pad" : "The one time pad system is an example of perfect (unbreakable) encryption, which is achieved by using, only once, a random polyalphabetic key that is as long the message itself.",
        "key exchange problem" : "In cryptography, the key exchange problem is the problem of sharing a secret key between Alice and Bob, without Eve, an eavesdropper, being able to intercept it."
      };      */
    
    </script>
    <h3 id="est-length">Time Estimate: 90 minutes</h3>
    

Introduction and Goals
-----------------------

.. raw:: html

    <p>
    In the preceding lesson, you built a Caesar Cipher app and learned that <span class="hover vocab yui-wk-div" data-id='cryptography'>cryptography</span> means <i>secret writing</i>. It is the art and science of
    sending secret messages and it has been used by generals and governments and everyday people practically since the invention of written language. 
  
    </p><p>As we will see in this lesson, modern cryptographic techniques are essential to guaranteeing the security of our transactions on the Internet.  <span class="hover vocab yui-wk-div" data-id='cryptography'>Cryptography</span> plays a
    role whenever you make an online purchase at Amazon or provide your password to Google.  If we couldn't rely on those transactions being secure -- i.e., being encrypted using some cryptographic algorithm -- we wouldn't have the Internet as we know it today.
    </p>
	<p>
	<img style="float:right" width="250px" src="../_static/assets/img/AliceBobSymmetricEncryption.JPG"/>
	This lesson focuses on some of the classical <span class="hover vocab yui-wk-div" data-id='cipher'>ciphers</span> that followed the Caesar Cipher,
    which Julius Caesar used in 34 B.C.  Like the Caesar cipher, the other ciphers we will study in this lesson will use <span class="hover vocab yui-wk-div" data-id='symmetric encryption'>symmetric encryption</span>,
    which means that the same <i>key</i> is used both for <i>encrypting</i> and <i>decrypting</i> messages.   As we will also see, all ciphers consist of two parts,
    the <i>key</i> and their <i>algorithm</i>.  And it is the key, not the algorithm, that allows the <span class="hover vocab yui-wk-div" data-id='cipher'>cipher</span> to create secret messages. In fact, in modern <span class="hover vocab yui-wk-div" data-id='cryptography'>cryptography</span> the
    algorithms are all based on <i>open standards</i> that are created by teams of experts, discussed openly and adopted and maintained by standards organizations.

    </p>
	
    </p>
	
	<div><b>Learning Objectives:</b>&nbspI will learn to</div>
	<ul>
	<li>perform <span class="hover vocab yui-wk-div" data-id='frequency analysis'>frequency analyses</span> to identify <span class="hover vocab yui-wk-div" data-id='substitution cipher'>substitution</span> and <span class="hover vocab yui-wk-div" data-id='transposition cipher'>transposition</span> ciphers</li>
	<li>encrypt and decrypt messages using Vigenere Cipher</li>
	<li>describe the <span class="hover vocab yui-wk-div" data-id='key exchange problem'>key exchange problem</span></li>
	</ul>
	<div><b>Language Objectives:</b>&nbspI will be able to</div>
	<ul>
	<li>explain how <span class="hover vocab yui-wk-div" data-id='substitution cipher'>substitution ciphers</span> can be broken</li>
	<li>use target vocabulary, such as <span class="hover vocab yui-wk-div" data-id="frequency analysis">frequency analysis</span>, <span class="hover vocab yui-wk-div" data-id="polyalphabetic substitution">polyalphabetic substitution</span>, <span class="hover vocab yui-wk-div" data-id="one time pad">one time pad</span>, and <span class="hover vocab yui-wk-div" data-id="key exchange problem">key exchange problem</span> while describing symmetric encryption ciphers, with the support of concept definitions and <a href="https://docs.google.com/presentation/d/1qwoJ0sNiiLFbv1KN_xW7yLpXUQLfYD8lxxZWPYjqdIY/copy" target="_blank" title="">vocabulary notes</a> from this lesson</li>
	</ul>
    

Learning Activities
--------------------

.. raw:: html

    <ul align="center" style="list-style: none; margin: 0; padding: 0; background: lightgrey">
	<li style="display: inline"><a href="https://docs.google.com/presentation/d/1GOzrwChWLjWbYi_yqKpLi2T60dwM8Yv2CaX2qGPzuV8" target="_blank" title="">Slides</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://youtu.be/86sjWJXhixU" target="_blank">YouTube Video Part 1</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://youtu.be/kgFwFZQECFM" target="_blank">YouTube Video Part 2</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://youtu.be/cPiHgaLB8yY" target="_blank" title="">YouTube Video Part 3</a></li>
	<li style="display: inline"> | </li>
	<li style="display: inline"><a href="https://youtu.be/UkC233aGc8Y" target="_blank" title="">YouTube Video Part 4</a></li>
	</ul> 
	
	<br/>
	<p>Let's take a look at some of the classical ciphers and some of the basic principles of <span class="hover vocab yui-wk-div" data-id='cryptography'>cryptography</span>.  There are several hands-on activities in this lesson, where you'll have a chance to practice encrypting and decrypting messages and analyzing
    ciphers.
    </p>
	
    <!--
    &lt;h2&gt;Part 1: Caesar <span class="hover vocab yui-wk-div" data-id='Cipher'>Cipher</span>&lt;/h2&gt;
    &lt;p&gt;
      To refamiliarize yourself with the Caesar <span class="hover vocab yui-wk-div" data-id='Cipher'>Cipher</span>, use the widget below to do the exercises listed.
       
    &lt;/p&gt;
    
    &lt;h2&gt;Activity: Caesar <span class="hover vocab yui-wk-div" data-id='Cipher'>Cipher</span>&lt;/h2&gt;
    (&lt;a href=&quot;http://appinventor.trincoll.edu/csp/caesarcipher/&quot; target=&quot;_blank&quot;&gt;Open widget in separate window&lt;/a&gt;)
    
    &lt;gcb-iframe src=&quot;https://appinventor.trincoll.edu/csp/caesarcipher/&quot; title=&quot;Caesar <span class="hover vocab yui-wk-div" data-id='Cipher'>Cipher</span>&quot; height=&quot;300&quot; width=&quot;650&quot; instanceid=&quot;IBDTlyHm0G8e&quot;&gt;
    &lt;/gcb-iframe&gt;
    
    &lt;ol&gt;
    &lt;li&gt;Encode the word &quot;wisdom&quot; with a Caesar shift of 3.
    
    &lt;p&gt;&lt;/p&gt;&lt;/li&gt;
      &lt;li&gt;Take the word &quot;JVYYLJA&quot; and decrypt it using a Caesar shift of 7.
    &lt;/li&gt;&lt;/ol&gt;
    &lt;p&gt;
    Check with your partner to make sure you got the same results before proceeding with the 
      more complex ciphers discussed in this lesson.
    &lt;/p&gt;
    -->
	
	<p><h3>Part 1: Simple Substitution Cipher</h3>
    
.. youtube:: 86sjWJXhixU
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    <br/>
    <h3>Activity: Simple Substitution Cipher</h3>
    <p>(<a href="https://mobile-csp.org/webapps/crypto/simplesubstitution.html" target="_blank">Open widget in separate window</a>)</p>
    <iframe height="350" src="https://mobile-csp.org/webapps/crypto/simplesubstitution.html" style="border: 0;" title="" width="650"></iframe>
    <br/>
    <ol>
    <li style="margin-bottom: 5px;"><b>By Hand.</b> Use a simple <span class="hover vocab yui-wk-div" data-id='substitution cipher'>substitution cipher</span> to encrypt your name. 
    Choose your own keyword to create a <span class="hover vocab yui-wk-div" data-id='cipher'>cipher</span> alphabet. Then use the widget above to check your result.
    
    </li><li style="margin-bottom: 5px;"><b>Decrypt.</b> The following word,  <b><i>SIRTQSMTCKJ</i></b>, 
    was encrypted with the keyword <b><i>simple</i></b>.  Can you decrypt it?
    
    </li><li><b>Brute force attack.</b> How many keys (arrangements of the alphabet) 
    would you have to try to perform a <span class="hover vocab yui-wk-div" data-id='brute force attack'>brute force attack</span>?
    
    </li></ol>
    <h3>Part 2: Frequency Analysis</h3>
    
.. youtube:: kgFwFZQECFM
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    <h3>Activity: Frequency Analysis</h3>
    <p>(<a href="https://mobile-csp.org/webapps/crypto/freqanalyzer.html" target="_blank">Open widget in separate window</a>)</p>
    <iframe height="400" src="https://mobile-csp.org/webapps/crypto/freqanalyzer.html" style="border: 0;" title="" width="675"></iframe>
	<p>
	<p>	<b><span class="hover vocab yui-wk-div" data-id='frequency analysis'>Frequency analysis</span>.</b> One of the following messages was encrypted 
    using a <span class="hover vocab yui-wk-div" data-id='substitution cipher'>substitution cipher</span> and the other with a <span class="hover vocab yui-wk-div" data-id='transposition cipher'>transposition cipher</span>.
    Can you identify which is which? Paste the messages into the frequency analyzer tool (above) and observe their frequency histograms. 
    </p>
    <b>Text 1.</b>
    <div style="width:675px;overflow:auto">
	<pre> 
    nybfx ymjgj xytky nrjxn ybfxy mjbtw xytky nrjx nybfx ymjfl jtkbn xitrn ybfxy mjflj 
    tkktt qnxms jxxn ybfxy mjjut hmtkg jqnjk nybfx ymjju thmtk nshwj izqny dnyb fxymj 
    xjfxt stkqn lmyny bfxym jxjfx tstki fwpsj xxny bfxym jxuwn sltkm tujny bfxym jbnsy 
    jwtki jxufn wbjm fijaj wdymn slgjk twjzx bjmfi stymn slgjk twjzx bjbj wjfqq ltnsl inwjh 
    yytmj fajsb jbjwj fqqlt nslin wjhy ymjty mjwbf dnsxm twyym jujwn tibfx xtkfw qnpjy 
    mjuwj xjsy ujwnt iymfy xtrjt knyxs tnxnj xyfzy mtwny njxns xnxyj itsny xgjn slwjh jnaji 
    ktwlt titwk twjan qnsym jxzuj wqfyn ajijl wjjt khtru fwnxt stsqd
    </pre>
	</div>
    <br/><b>Text 2.</b>
    <div style="width:675px;overflow:auto">
	<pre>ttbti swhot istta osmwh gflhs tsecf liaho ondia henit ahena nwtpnf ewtie fpree rhbou 
    hnhbo uerli deovw rlode oeasr hrdsa itrei ttein ittie ntote gceoo rrits etegc psoya hsfmt 
    sesfm iahew dtseo oiewh pheet tecir uytss sohts ssoks isero oisen oeawa vtnee watne 
    ewagn rtenw egnit htwih tpiao reeet eoaoo sieuo tiiei ieidg dfvih pliee omrol setet wtese 
    iotao siaoo fwphe lwtof wtofs tsipt wtsid egfed gfweo gtaea grehn oeofl psrdm fssri 
    sdbnv foone avefi nweoi arowg fiaef nsteb isefc tieag ieare ahgha hrdhy irsoi rseli ceeli 
    ctryt ewskh nphst oahss nsrer oelur droan
    </pre>
	</div>
    
    <h3>Part 3: Vigenere Cipher</h3>
    
.. youtube:: cPiHgaLB8yY
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    <br/>
    <h3>Activity: Vigenere Cipher</h3>
    
    (<a href="https://mobile-csp.org/webapps/crypto/vigenere.html" target="_blank">Open widget in separate window</a>)
    <iframe height="400" src="https://mobile-csp.org/webapps/crypto/vigenere.html" style="border: 0;" title="" width="650"></iframe><br/>
    <ol>
    <li style="padding-bottom:5px"><b>By Hand.</b> Use the Vigenere cipher to encrypt your name. Choose your own keyword.</li>
	<li><b>Decrypt</b> the following message, which was encrypted using Vigenere Cipher, with the keyword <i>zebras</i>. 
    
    <blockquote><div style="width:250px;overflow:auto"><pre>SLJJ IK OSMPADOLBSELHG</pre></div></blockquote>
    </li>
    <li><b>Frequency Analysis.</b> Use the <i>Frequency Analyzer</i> tool (above) to count the letter frequencies in the following text, which is the same text that was encrypted in an earlier exercise.  In this case it was encrypted using Vigenere Cipher.  What differences do you observe from the histograms you used in the previous exercise?
    </li>
    </ol>
    <blockquote>
	<div style="width:650px;overflow:auto">
    <pre>sabjt zdffj tgexj dekhx xrslg ixfrk ssgki edwj kwsrx ivayd sgnik csnzt ozwuy esfip wfgnp 
    jjhfd wtzt ozwuy ewosd yoxai mzexh xxrsl gifgo ugsgz nuqie llasc jkws rxivs wzwpe 
    oxhki kilve tkhwr ibjof njbik fdwt ztozw uyeko vjegg elpge asabj tzdaj etwqs gueko ejiw 
    wgeev vwqcu yifff fwojd ytnez zhoft zhrhs exnvf lsod afies kphfi ffhji eusxp vandr xvwwq 
    ibcly nmoxd aqidk tzds uyejv ezznk gsskt zdtfi igcab jsgee scicd xivpj dwfet hdvj fdlge 
    ujoed sgztk msjji wrxbl tznvj kiwrm ojiks iefna swcv iffvf teaui ewojf spuoj essvv akmok 
    hwryq vrdzx jmevd ksve gegpd psqmt fngmp z</pre></div>
    </blockquote>

    <h3>Part 4: Perfect Secrecy and the Key Exchange Problem</h3>
    
.. youtube:: UkC233aGc8Y
        :width: 650
        :height: 415
        :align: center

.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    <br/>
    

Summary
--------

.. raw:: html

    <p>
    In this lesson, you learned how to:
      <div class="yui-wk-div" id="summarylist">
    </div>

Still Curious
--------------

.. raw:: html

    <p>
    <ul>
    <li>Read more about the historical evolution of <span class="hover vocab yui-wk-div" data-id='cipher'>ciphers</span> in <a href="http://www.bitsbook.com/wp-content/uploads/2008/12/chapter5.pdf" target="_blank">Chapter 5 of <i>Blown to Bits</i></a> (pg. 166+)</li>
    <li>You can find more <span class="hover vocab yui-wk-div" data-id='cryptography'>cryptography</span> challenges at <a href="https://cryptoclub.org" target="_blank">CryptoClub.org</a>.</li>
    <li>Here is a crypto challenge game at <a href="https://www.khanacademy.org/computing/computer-science/cryptography/cryptochallenge/a/cryptochallenge-introduction" target="_blank">Khan Academy</a>.</li>
    <li>If you want an additional challenge, try creating an app that does <i>Simple Substitution</i>. It will be similar to the Caesar Cipher App you made in Unit 5.  Or try incorporating an encryption scheme into one of your own apps. </li>
    </ul> 

Self-Check
-----------

.. raw:: html

    <p>
    Here is a table of some of the technical terms discussed in this lesson. Hover over the terms to review the definitions.
    <table align="center">
    <tbody>
    <tr>
    <td>
    <span class="hover vocab yui-wk-div" data-id="cipher">cipher</span>
    <br/><span class="hover vocab yui-wk-div" data-id="cryptography">cryptography</span>
    <br/><span class="hover vocab yui-wk-div" data-id="encryption">encryption</span>
    <br/><span class="hover vocab yui-wk-div" data-id="plaintext">plaintext</span>
    <br/><span class="hover vocab yui-wk-div" data-id="ciphertext">ciphertext</span>
    </td>
    <td>
    <span class="hover vocab yui-wk-div" data-id="decryption">decryption</span>
    <br/><span class="hover vocab yui-wk-div" data-id="encryption key">encryption key</span>
    <br/><span class="hover vocab yui-wk-div" data-id="encryption algorithm">encryption algorithm</span>
    <br/><span class="hover vocab yui-wk-div" data-id="symmetric encryption">symmetric encryption</span>
    <br/><span class="hover vocab yui-wk-div" data-id="substitution cipher">substitution cipher</span>
    </td>
    <td>
    <span class="hover vocab yui-wk-div" data-id="transposition cipher">transposition cipher</span>
    <br/><span class="hover vocab yui-wk-div" data-id="brute force attack">brute force attack</span>
    <br/><span class="hover vocab yui-wk-div" data-id="frequency analysis">frequency analysis</span>
    <br/><span class="hover vocab yui-wk-div" data-id="polyalphabetic substitution">polyalphabetic substitution</span>
    <br/><span class="hover vocab yui-wk-div" data-id="one time pad">one time pad</span>
    <br/><span class="hover vocab yui-wk-div" data-id="key exchange problem">key exchange problem</span>
    </td>
    </tr>
    </tbody>
    </table>
    
.. mchoice:: mcsp-6-6-1
    :random:
    :practice: T
    :answer_a: decryption
    :feedback_a: This is challenging, but rewarding! Decryption is actually the process of converting cipher text back into plain text. For example: khoor ----> hello
    :answer_b: frequency analysis
    :feedback_b: That's right! Frequency analysis is the technique whereby you count the letters in the secret message. In English, the letter with the highest frequency is 'e'. By counting letter frequencies you can identify the shift that was used to encrypt the message. That is why the Caesar cipher is not a secure cipher.
    :answer_c: encryption
    :feedback_c: This is challenging, but rewarding! Encryption is actually the process of converting plain text into cipher text. For example: hello ---->khoor
    :answer_d: cryptography analysis
    :feedback_d: This is challenging, but rewarding!
    :correct: b

    One technique that can be used to break a Caesar cipher is called _________________________. 


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    <br/>
    
.. fillintheblank:: mcsp-6-6-2
    :casei:

    .. raw:: html
    
    	<p>Suppose that the following word, <b>EAIWSQI</b>, was encrypted with a Caesar cipher and when you do a frequency analysis you learn that the most frequent letter was 'i'. What is the secret word? Type your answer into the Textbox.  (Make sure there are no extra spaces in your answer.)</p>

    - :awesome: That's right! The secret word is <i><b>awesome</i></b>. Given the information that the most frequent letter was the letter 'i', you would figure that the shift used in this case was 4. That means that 'a' is encrypted as 'e' and 'w' is encrypted as 'a', and 'e' is encrypted as 'i', and so on. Proceeding in this way you can break the cipher.
      :x: 


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>


    <br/>
    
.. mchoice:: mcsp-6-6-3
    :random:
    :practice: T
    :answer_a: Symmetric
    :feedback_a: This is part of the correct answer.
    :answer_b: Alphabetic
    :feedback_b: This is challenging, but rewarding!
    :answer_c: Transposition
    :feedback_c: This is challenging, but rewarding! Transposition ciphers rearrange the letters in the plaintext message. These ciphers do not do that.
    :answer_d: Substitution
    :feedback_d: Yes this is part of the correct answer.
    :correct: a,d

    .. raw:: html
    	
    	<p><i>Caesar cipher</i>, <i>simple substitution</i> cipher, and <i>Vigener</i> cipher are all examples of __________ ciphers.</p>


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

.. mchoice:: mcsp-6-6-4
    :random:
    :practice: T
    :answer_a: Uses the same alphabet over and over again
    :feedback_a: This is challenging, but rewarding! This description  would apply to simple substitution or Caesar cipher.
    :answer_b: Rearranges the plaintext alphabet using a keyword
    :feedback_b: This is challenging, but rewarding! A cipher that rearranges the plaintext alphabet would be a simple substitution cipher, including Caesar cipher.
    :answer_c: Rearranges the letters in the message according to some rule
    :feedback_c: This is challenging, but rewarding! A cipher that rearranges the letters in the message is known as a <i>transposition</i> cipher.
    :answer_d: Uses multiple alphabets
    :feedback_d: That is correct.  An example would be the <i>Vigenere</i> cipher, which uses a <i>keyword</i> to select several alphabets to use in encryption and decryption. 
    :correct: d

    .. raw:: html
    
    	<p>A <i>polyalphabetic</i> cipher is one that ______________.</p>


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>

    
.. mchoice:: mcsp-6-6-5
    :random:
    :practice: T
    :answer_a: the problem swapping Alice's key for Bob's key.
    :feedback_a: OK, so you didn’t get it right this time. Let’s look at this as an opportunity to learn. Try reviewing this. Alice and bob need to <i>share</i> the same key, not swap different keys.
    :answer_b: the problem of securely sharing a symmetric key between Alice and Bob.
    :feedback_b: Yes.  Alice and Bob need to share their symmetric key in order to send secret messages to each other. How can that be done without Eve getting it?
    :answer_c: the problem of securely sharing an asymmetric key.
    :feedback_c: No. Asymmetric keys are used in Diffie-Hellman and RSA to exchange symmetric keys.
    :answer_d: the challenge of setting up an exchange system where cryptographic keys can be stored securely.
    :feedback_d: OK, so you didn’t get it right this time. Let’s look at this as an opportunity to learn. Try reviewing this. There is no such effort.  It would be a bad idea to store everyone's keys in something like a central bank.
    :correct: b

    .. raw:: html
    
    	<p>The <i>key exchange problem</i> is ____</p>


.. raw:: html

    <div id="bogus-div">
    <p></p>
    </div>
    

Reflection: For Your Portfolio
-------------------------------

.. raw:: html

    <p><div class="yui-wk-div" id="portfolio">
    <p>Answer the following portfolio reflection questions as directed by your instructor. Questions are also available in this <a href="https://docs.google.com/document/d/1vRcg0qZ_LYjNgNkVK9nOkvbFl2h0C2bFagneMpNVehc/copy" target="_blank">Google Doc</a> where you may use File/Make a Copy to make your own editable copy.</p>
    <div style="align-items:center;"><iframe class="portfolioQuestions" scrolling="yes" src="https://docs.google.com/document/d/e/2PACX-1vSOv4tHOa7k4MuMPI8tsmzGPcLRIIhNLrSb0sB8xwzhgaP2QOqCjICbfIHCPUHXWlVvPLKmcGO5Si-2/pub?embedded=true" style="height:30em;width:100%"></iframe></div>
    </div>
    </div>