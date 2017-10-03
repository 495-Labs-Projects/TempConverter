<h2 class="titleh">Lab 2: TempConverter; Using Foundation</h2>

<p><strong>Due Date:</strong> January 28</p>

<p>
  <strong>Objectives</strong>
  <div class="markdown-body">
      <ul>
<li>Learn the basics of Ruby programming</li>
<li>Learn how to work with Time class in Ruby</li>
<li>Learn to use irb command prompt</li>
<li>Improve familiarity with basic git commands</li>
<li>Review HTML and use Foundation CSS framework</li>
<li>Be able to submit project code to a remote repo</li>
</ul>
  </div>
</p>


  </section>
</div>


<div id="wrapper">
  <section id="content">
  <div class="titlebar"><span class="mini-icon mini-icon-readme"></span> README.md</div>
  <div class="markdown-body padded">
        <h1>Part 1: Ruby Introduction</h1>

<p>Some students have had prior exposure to Ruby, but others in the class may have little or no experience with the language. This part of the lab will get everyone familiar with some Ruby basics and provide review of other key concepts. This is a short introduction, but there are some 'on your own' exercises at the very end that students are strongly encouraged to try to solidify their understanding of Ruby.</p>

<ol>
<li><p>We are going to begin by writing a simple program for Ruby to convert temperatures and then modify it several times.  To begin, create a new file called <code>temp_conversions.rb</code> using your preferred editor/IDE.</p></li>
<li>
<p>In this file, create a method called <code>convert</code> as follows:</p>

<div class="highlight highlight-ruby"><pre><span class="k">def</span> <span class="nf">convert</span><span class="p">(</span><span class="n">temp</span><span class="p">)</span>

<span class="k">end</span>
</pre></div>

<p>Between these two lines, add in the following line of code to convert Fahrenheit to Celsius:</p>

<div class="highlight highlight-ruby"><pre><span class="mi">5</span> <span class="o">*</span> <span class="p">(</span><span class="n">temp</span> <span class="o">-</span> <span class="mi">32</span><span class="p">)</span><span class="o">/</span><span class="mi">9</span>
</pre></div>

<p>After the end statement, create some simple tests for this method with the code below:</p>

<div class="highlight highlight-ruby"><pre><span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="mi">32</span><span class="p">)</span>          
<span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="mi">50</span><span class="p">)</span>          
<span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="mi">212</span><span class="p">)</span>
</pre></div>

<p>Run this code from the command line by changing to the same directory as the file and typing <code>ruby temp_conversions.rb</code>.  You should get the output 0, 10, 100 as a result.  Once this is running, set up a git repository and add this file to it.  (Ask the TA if you don't remember how to do this from the previous labs.)</p>
</li>
<li><p>Now go into the method and remove the parentheses to the right of 32 and rerun this code.  Note the error returned.  Fix the error and rerun the code with <code>ruby –c -w temp_conversions.rb</code>.  The <code>–c</code> flag means 'check syntax only' and the <code>–w</code> flag activates higher warnings.  When you run this time, you should see a new message.</p></li>
<li>
<p>Add the test <code>puts convert("zero")</code> to the tests and rerun the code normally.  Why did you get an error?  To correct this, we will limit all temperatures to integers by adding a line before the calculation in our method: </p>

<div class="highlight highlight-ruby"><pre><span class="k">return</span> <span class="s2">"Temperature must be an integer"</span> <span class="k">unless</span> <span class="n">temp</span><span class="o">.</span><span class="n">class</span> <span class="o">==</span> <span class="no">Fixnum</span>
</pre></div>

<p>Rerun these tests after adding this line.  If the tests pass, add the revision to the git repository.  Also notice that if I want to return before the end of method, I need to use the return keyword, but if the method runs its course, the last value is automatically returned by the method.  Finally, notice that I can place the condition at the end of the line in Ruby, not just at the beginning (as we are used to in other languages).</p>
</li>
<li>
<p>Add the test <code>puts convert(-500)</code> to the tests and rerun.  Of course, remembering your basic physics leaves you distressed at this point because you know this answer is in error – Absolute Zero is at –474 degrees Fahrenheit  or -270 degrees Celsius, making this result impossible.  To make sure our program doesn't give silly answers, we will add another line after the last correction (and before the calculation): </p>

<div class="highlight highlight-ruby"><pre><span class="k">return</span> <span class="s2">"Temperature below Absolute Zero"</span> <span class="k">if</span> <span class="n">temp</span> <span class="o">&lt;</span> <span class="o">-</span><span class="mi">474</span> 
</pre></div>

<p>Rerun the tests; assuming they pass, save the revision to the git repository.</p>
</li>
<li>
<p>Of course, we have only half the temperature conversion problem – converting Fahrenheit to Celsius – and have no capability to convert Celsius to Fahrenheit.  Create a new branch in git called <code>exp</code> (Again, ask a TA if you don't remember this from previous labs).  Now in your code, add another argument called <code>measure</code> and using an <code>if ... else ... end</code> construct, correct the code so that either a Fahrenheit or Celsius temperature is converted.  Set up the <code>measure</code> argument so its default value is "F".  Add the test below:</p>

<div class="highlight highlight-ruby"><pre><span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="s2">"C"</span><span class="p">)</span>
<span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="s2">"C"</span><span class="p">)</span>
<span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="mi">100</span><span class="p">,</span> <span class="s2">"C"</span><span class="p">)</span>
<span class="nb">puts</span> <span class="n">convert</span><span class="p">(</span><span class="o">-</span><span class="mi">280</span><span class="p">,</span> <span class="s2">"C"</span><span class="p">)</span>
</pre></div>

<p>Rerun the code; if all tests pass, save to the repository.</p>
</li>
<li>
<p>Looking at the results, we see that the code is still problematic: we get a result for –280 oC even though we know that value is below Absolute Zero.  There are a number of ways to correct this, but for learning purposes here, we are going to create a new method called <code>below_absolute_zero?</code> which has two arguments: temp and measure.  This method will simply return a boolean of true if the temperature for the measurement system is below the critical value; this is why this method will end in a question mark. Create the basic structure for this method now.</p>

<p>Add the following code so your complete method looks like this:</p>

<div class="highlight highlight-ruby"><pre><span class="k">def</span> <span class="nf">below_absolute_zero?</span><span class="p">(</span><span class="n">temp</span><span class="p">,</span> <span class="n">measure</span><span class="p">)</span>
    <span class="p">(</span><span class="n">temp</span> <span class="o">&lt;</span> <span class="o">-</span><span class="mi">454</span> <span class="ow">and</span> <span class="n">measure</span> <span class="o">==</span> <span class="s2">"F"</span><span class="p">)</span> <span class="ow">or</span> <span class="p">(</span><span class="n">temp</span> <span class="o">&lt;</span> <span class="o">-</span><span class="mi">270</span> <span class="ow">and</span> <span class="n">measure</span> <span class="o">==</span> <span class="s2">"C"</span><span class="p">)</span>
<span class="k">end</span>
</pre></div>

<p>A couple of things to note here: (1) we have used the words <code>and</code> and <code>or</code> to demonstrate that Ruby does understand these words, but most times we will use the programming standards of <code>&amp;&amp;</code> and <code>||</code> for these conjunctions, (2) if we provide Ruby a statement like <code>temp &lt; -454</code>, the statement is evaluated as either true or false and that result is returned.</p>

<p>Back to the code: go to the convert method and change the if statement for the Absolute Zero condition so that it references this new method rather than the simple statement of <code>temp &lt; -474</code>.  Rerun the code and make sure that everything is working properly.  If so, save this code to the git repository. Checkout the <code>master</code> branch, and then merge the <code>exp</code> branch onto the <code>master</code> branch.  (Again, ask a TA is you don't remember how to do this.)  </p>
</li>
</ol>

<hr>

<h1>
<span class="mega-icon mega-icon-issue-opened"></span> Stop</h1>

<p>Show a TA that you have completed the temp_conversion program and have properly saved the code to git. Make sure the TA initials your sheet.</p>

<hr>

<h1>Part 2: Interactive Ruby</h1>

<ol>
<li><p>We are going to switch gears now and start to interact with Ruby with irb [interactive ruby].  The irb prompt is a useful command line tool that can allow you to try out simple ruby constructs and methods.  To get to interactive ruby, just type <code>irb</code> on the command line.  </p></li>
<li>
<p>Once in irb, type </p>

<div class="highlight highlight-ruby"><pre><span class="n">a</span> <span class="o">=</span> <span class="no">Time</span><span class="o">.</span><span class="n">now</span>
</pre></div>

<p>This gives us an object a with a Ruby timestamp.  Now type in </p>

<div class="highlight highlight-ruby"><pre><span class="nb">require</span> <span class="s1">'date'</span>
<span class="n">b</span> <span class="o">=</span> <span class="no">Date</span><span class="o">.</span><span class="n">today</span>
</pre></div>

<p>Compare this result with the results of the first command.  What is the difference between these two objects?  Be sure you are clear on the difference before proceeding (ask a TA if you are unsure).</p>
</li>
<li><p>Now type <code>a.month</code> and note what is output is.  Now type <code>a.strftime("%B")</code> and note the output.  How would you find the year of <code>a</code>? (Guess ...)  Try your idea in irb now.</p></li>
<li>
<p>Now type the command </p>

<div class="highlight highlight-ruby"><pre><span class="n">a</span><span class="o">.</span><span class="n">month</span> <span class="o">==</span> <span class="n">b</span><span class="o">.</span><span class="n">month</span>
</pre></div>

<p>What was returned?  Type the command </p>

<div class="highlight highlight-ruby"><pre><span class="n">a</span><span class="o">.</span><span class="n">day</span> <span class="o">==</span> <span class="n">b</span><span class="o">.</span><span class="n">day</span> <span class="o">-</span> <span class="mi">1</span>
</pre></div>

<p>and see that result as well.  As we noted earlier in the temp conversion method, Ruby is evaluating these statements as either true or false and returning the result.</p>
</li>
<li><p>Use the <code>strftime</code> method to format the object <code>a</code> in the format of 99/99/9999.  To see the options with <code>strftime</code> we can take advantage of a gem Prof. H uses sometimes in class: cheat. (To install this gem, run <code>gem install cheat</code> in a terminal window that is not running irb; you can verify it is there by typing <code>gem list | grep cheat</code> which simply pipes your list of gems to grep so it can search for any gems with 'cheat' in its name.)  In that other terminal window/tab, type <code>cheat strftime</code> and see the output returned – this should guide you in reformatting the timestamp.  If you are having issues with this gem, you can also use an online reference <a href="http://strfti.me/">strfti.me</a>.</p></li>
<li>
<p>We are going to add three variables at once through multiple assignment (an option in Ruby).  To do this, type into irb: </p>

<div class="highlight highlight-ruby"><pre><span class="n">m1</span><span class="p">,</span> <span class="n">d1</span><span class="p">,</span> <span class="n">y1</span> <span class="o">=</span> <span class="mo">04</span><span class="p">,</span> <span class="mo">01</span><span class="p">,</span> <span class="mi">2014</span>
</pre></div>

<p>Now we will use these values to create a new timestamp in Ruby with the command:</p>

<div class="highlight highlight-ruby"><pre><span class="n">c</span> <span class="o">=</span> <span class="no">Time</span><span class="o">.</span><span class="n">mktime</span><span class="p">(</span><span class="n">y1</span><span class="p">,</span> <span class="n">m1</span><span class="p">,</span> <span class="n">d1</span><span class="p">)</span>
</pre></div>

<p>Now we have the timestamp for this year's April Fool's Day.  Let's change it a little bit by typing <code>d1 = 31</code> and rerunning the command: <code>c = Time.mktime(y1, m1, d1)</code>.  What did Ruby do with the date 04/31/2014?</p>
</li>
</ol>

<hr>

<h1>
<span class="mega-icon mega-icon-issue-opened"></span> Stop</h1>

<p>Show a TA that you have completed this part. Make sure the TA initials your sheet.</p>

<hr>

<p>You are technically done with this part of the lab. However if you want to stretch yourself a bit and put this new Ruby knowledge to the test, then try the following: write a method called <code>valid_date?</code> which takes year, month and day as arguments and returns true if the date is valid or false if not.  Below is a frame for the method as well as some test cases.</p>

<div class="highlight highlight-ruby"><pre>  <span class="k">def</span> <span class="nf">valid_date?</span><span class="p">(</span><span class="n">year</span><span class="p">,</span> <span class="n">month</span><span class="p">,</span> <span class="n">day</span><span class="p">)</span>
    <span class="c1"># your code goes here ...</span>

  <span class="k">end</span>

  <span class="c1"># Tests</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2013</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">29</span><span class="p">)</span> <span class="c1"># =&gt; true</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2013</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">28</span><span class="p">)</span> <span class="c1"># =&gt; true</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2013</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">29</span><span class="p">)</span> <span class="c1"># =&gt; false</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2014</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">29</span><span class="p">)</span> <span class="c1"># =&gt; false</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2014</span><span class="p">,</span> <span class="mi">9</span><span class="p">,</span> <span class="mi">29</span><span class="p">)</span> <span class="c1"># =&gt; true</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2014</span><span class="p">,</span> <span class="mi">9</span><span class="p">,</span> <span class="mi">31</span><span class="p">)</span> <span class="c1"># =&gt; false</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2013</span><span class="p">,</span> <span class="mi">12</span><span class="p">,</span> <span class="mi">31</span><span class="p">)</span> <span class="c1"># =&gt; true</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2013</span><span class="p">,</span> <span class="mi">12</span><span class="p">,</span> <span class="mi">32</span><span class="p">)</span> <span class="c1"># =&gt; false</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="mi">2013</span><span class="p">,</span> <span class="mi">13</span><span class="p">,</span> <span class="mi">31</span><span class="p">)</span> <span class="c1"># =&gt; false</span>
  <span class="n">valid_date?</span><span class="p">(</span><span class="s2">"2014"</span><span class="p">,</span> <span class="s2">"Jan"</span><span class="p">,</span> <span class="mi">31</span><span class="p">)</span> <span class="c1"># =&gt; false</span>
</pre></div>

<p>Hint: IMO it is a lot easier to deal with 'exceptional dates' with <a href="http://www.ruby-doc.org/docs/ProgrammingRuby/html/tut_exceptions.html">Ruby exceptions</a>.</p>

<h1>Part 3: Ruby Blocks</h1>

<ol>
<li><p>In this part of the lab, you will work through block problems from previous 67-272 exam. This section contains 4 problems, but you only need to complete the first 2 for full credit. However, you are encouraged to complete them all if time allows! They will be good practice for future exams and your projects.</p></li>
<li><p>In each problem you will be given an expected output, and your task is to write a block that will generate this output. You can complete the problems in a separate file, and run it the same way as TempConverter.</p></li>
<li><p>Add the following dictionaries to the top of your file, as these will be used in the problems.</p></li>
<div class="highlight highlight-ruby"><pre>
cast = {bob_parr: :incredibles, helen_parr: :incredibles, lucius: :incredibles, 
        edna: :incredibles, woody: :toy_story, buzz: :toy_story, bopeep: :toy_story, 
        andy: :toy_story, merida: :brave, marlin: :finding_nemo, dory: :finding_nemo, 
        nemo: :finding_nemo, sulley: :monsters_inc, mike: :monsters_inc, 
        randall: :monsters_inc, sally: :cars, mcqueen: :cars, doc: :cars, 
        mater: :cars, jessie: :toy_story_3, big_baby: :toy_story_3, remy: :ratatouille }
          
toys = [:woody, :bopeep, :buzz, :jessie, :big_baby]

females = [:helen_parr, :edna, :bopeep, :dory, :sally, :jessie, :merida]

super_heroes = { bob_parr: "Mr. Incredible", helen_parr: "Elastigirl", lucius: "Frozone" }

race_cars = [:mcqueen, :doc]

year_produced = {incredibles: 2004, toy_story: 1995, brave: 2012, finding_nemo: 2003, up: 2009, walle: 2008,
                 monsters_inc: 2001, cars: 2006, bugs_life: 1998, toy_story_3: 2010}
</pre></div>

<h2>Problem 1: </h2>
<div class="highlight highlight-ruby"><pre>
EXPECTED OUTPUT: 
  bopeep
  jessie
</pre></div>

<h2>Problem 2: </h2>
<div class="highlight highlight-ruby"><pre>
EXPECTED OUTPUT: 
  [:brave, :up, :walle, :toy_story_3]
</pre></div>

<h2>Problem 3: </h2>
<div class="highlight highlight-ruby"><pre>
EXPECTED OUTPUT: 
  Toy_story - 1995
  Monsters_inc - 2001
  Finding_nemo - 2003
  Incredibles - 2004
  Cars - 2006
  Toy_story_3 - 2010
  Brave - 2012
</pre></div>

<h2>Problem 4: </h2>
<div class="highlight highlight-ruby"><pre>
EXPECTED OUTPUT: 
  Cars
  Finding Nemo
  Incredibles
  Monsters Inc
  Toy Story
</pre></div>


<hr>

<h1>
<span class="mega-icon mega-icon-issue-opened"></span> Stop</h1>

<p>Show a TA that you have at least problems 1 and 2 completed. Make sure the TA initials your sheet.</p>


<h1>Practice HTML - Optional</h1>
<p>If you need a refresher on HTML basics, feel free to review the following labs from 67-250.</p>
<ul>
<li><a href="docs/Lab1.pdf">Lab 1</a></li>
<li><a href="docs/Lab2.pdf">Lab 2</a></li>
<li><a href="docs/Lab3.pdf">Lab 3</a></li>
</ul>

<h1>On Your Own</h1>

<p>This week the "on your own" assignment is to go to <a href="http://rubymonk.com/learning/books/1">RubyMonk's free Ruby Primer</a> and complete the following exercises:</p>

<ul>
<li><p>Introduction To Ruby Objects</p></li>
<li><p>Arrays in Ruby</p></li>
<li><p>Introduction to Ruby Methods</p></li>
</ul>
  </div>
