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

<hr>

<h1>Part 3: HTML Review</h1>

<p>We will be using <a href="http://foundation.zurb.com/">Foundation</a> later this semester in lab and possibly in the course project.  Today we will build a static site with Foundation to gain some familiarity and to review HTML and CSS. Normally we would have you clone the full repository, but in this case we have provided you with starter code on github.  It would also be wise to open up the <a href="http://foundation.zurb.com/docs/">documentation provided for Foundation</a> as you will want to look up additional information about Foundation and become more familiar with this framework.</p>

<ol>
<li>Clone the starter code from github:</li>
</ol>

<pre><code>  git clone git://github.com/melfree/67272_lab2_starter.git
</code></pre>

<p><strong>NOTE</strong> If you are on a VM, It is suggested that you clone this into your /vagrant directory</p>

<ol>
<li><p>Create a new directory on your machine called "pmr_project" and copy the contents of <code>67272_lab2_starter</code> into it.</p></li>
<li>
<p>Inside the "pmr_project" directory, open the <code>home.html</code> in your text editor and add a <code>&lt;meta&gt;</code> tag indicating you're the author of this project in the <code>&lt;head&gt;</code> section:</p>

<div class="highlight highlight-html"><pre>  <span class="nt">&lt;meta</span> <span class="na">name=</span><span class="s">"author"</span> <span class="na">content=</span><span class="s">"YOUR NAME HERE"</span><span class="nt">&gt;</span>
</pre></div>
</li>
<li>
<p>In that same file, add links to our stylesheets (in the <code>&lt;head&gt;</code> section):</p>

<div class="highlight highlight-html"><pre>  <span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"stylesheet"</span> <span class="na">href=</span><span class="s">"css/foundation.css"</span> <span class="na">type=</span><span class="s">"text/css"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"stylesheet"</span> <span class="na">href=</span><span class="s">"css/normalize.css"</span> <span class="na">type=</span><span class="s">"text/css"</span><span class="nt">&gt;</span>
</pre></div>
</li>
<li>
<p>Create a git repository from "pmr_project", add all the files, and make your initial commit:</p>

<pre><code>  git init .
  git add .
  git commit -m "Initial commit - added head materials to home.html"
</code></pre>
</li>
<li>
<p>We are going to start with the body (the part the user sees directly in the browser) by building a simple navigation bar. To position our navigation content within the default grid that Foundation uses (rather than let the navigation span the entire page), we can build the navigation with the following:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"contain-to-grid"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;nav</span> <span class="na">class=</span><span class="s">"top-bar"</span> <span class="na">data-topbar</span><span class="nt">&gt;</span>
    <span class="nt">&lt;ul</span> <span class="na">class=</span><span class="s">"title-area"</span><span class="nt">&gt;</span>
      <span class="nt">&lt;li</span> <span class="na">class=</span><span class="s">"name"</span><span class="nt">&gt;</span>
        <span class="nt">&lt;h1&gt;&lt;a</span> <span class="na">href=</span><span class="s">"home.html"</span><span class="nt">&gt;</span>PGH Movie Reviews<span class="nt">&lt;/a&gt;&lt;/h1&gt;</span>
      <span class="nt">&lt;/li&gt;</span>
    <span class="nt">&lt;/ul&gt;</span>

   <span class="c">&lt;!-- navigation options go here --&gt;</span>

  <span class="nt">&lt;/nav&gt;</span>
<span class="nt">&lt;/div&gt;</span>
</pre></div>
</li>
<li>
<p>Time to add two navigation options in the commented area. The follow code will suffice:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;section</span> <span class="na">class=</span><span class="s">"top-bar-section"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;ul</span> <span class="na">class=</span><span class="s">"left"</span><span class="nt">&gt;</span>
    <span class="nt">&lt;li&gt;&lt;a</span> <span class="na">href=</span><span class="s">"theaters.html"</span><span class="nt">&gt;</span>In Theaters<span class="nt">&lt;/a&gt;&lt;/li&gt;</span>
    <span class="nt">&lt;li&gt;&lt;a</span> <span class="na">href=</span><span class="s">"report.html"</span><span class="nt">&gt;</span>Report a Movie<span class="nt">&lt;/a&gt;&lt;/li&gt;</span>
  <span class="nt">&lt;/ul&gt;</span>
<span class="nt">&lt;/section&gt;</span>
</pre></div>

<p>View the results in a browser.  Assuming all is well, add and commit these changes to git with an appropriate commit message.</p>
</li>
<li><p>Before writing content, please read the <a href="http://foundation.zurb.com/docs/components/grid.html">Foundation Grid docs</a>. If you have any questions, please ask a TA.</p></li>
<li>
<p>We want to divide the main body into two columns -- a main content section and a sidebar -- with a spacer in between.  To do that, add the following:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"row"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"small-7 columns"</span><span class="nt">&gt;</span>
    <span class="c">&lt;!-- MAIN CONTENT GOES HERE --&gt;</span>
  <span class="nt">&lt;/div&gt;</span>

  <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"small-1 columns"</span><span class="nt">&gt;</span>
    <span class="ni">&amp;nbsp;</span>
  <span class="nt">&lt;/div&gt;</span>

  <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"small-4 columns"</span><span class="nt">&gt;</span>
    <span class="c">&lt;!-- SIDEBAR CONTENT GOES HERE --&gt;</span>
  <span class="nt">&lt;/div&gt;</span>
<span class="nt">&lt;/div&gt;</span>
</pre></div>
</li>
<li>
<p>Add the content provided to the scaffolding created in the previous step.</p>

<p>Review the results in a browser.</p>

<p>Add and commit the results to git.</p>
</li>
<li>
<p>On the bottom of the page, we want to create a footer. Still inside the container div, add the following:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;footer</span> <span class="na">class=</span><span class="s">"footer"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"row"</span><span class="nt">&gt;</span>

    <span class="c">&lt;!-- footer content goes here --&gt;</span>

  <span class="nt">&lt;/div&gt;</span>
<span class="nt">&lt;/footer&gt;</span>
</pre></div>

<p>Use the content from <code>home_page_materials.txt</code> to populate the rest of this snippet.</p>
</li>
<li>
<p>As a finishing touch on the home page, let's use <a href="http://foundation.zurb.com/docs/components/labels.html">Foundations's inline labels</a>. Since the <em>Dark Knight Rises</em> is Prof. H's favorite of this bunhc, add an "Fav" label after the movie:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;span</span> <span class="na">class=</span><span class="s">"label success"</span><span class="nt">&gt;</span>Favorite<span class="nt">&lt;/span&gt;</span>
</pre></div>

<p>Since <em>Smart People</em>, <em>Wonder Boys</em>, and <em>The Mothman Prophecies</em> were all filmed at CMU, add a special label to each of those movies:</p>

<div class="highlight highlight-html"><pre>  <span class="nt">&lt;span</span> <span class="na">class=</span><span class="s">"label alert"</span><span class="nt">&gt;</span>CMU<span class="nt">&lt;/span&gt;</span>
</pre></div>

<p>Confirm these changes in the browser.</p>

<p>Add and commit the changes to git.</p>
</li>
<li><p>Moving onto the <code>theaters.html</code> page, our goal here is to add a <a href="http://foundation.zurb.com/docs/components/tables.html">Foundation table</a>. This is not too fancy, but the documentation is there to help you spruce it up if you wish. Replace the comment on line 34 with an HTML table that has a <code>&lt;thead&gt;</code> with two columns.</p></li>
<li>
<p>Add the content from the four rows in <code>theater_page_materials.txt</code>.</p>

<p>Confirm these changes in the browser.</p>

<p>Add and commit the changes to git.</p>
</li>
<li>
<p>Moving onto the <code>report.html</code> page, our goal here is to add a <a href="http://foundation.zurb.com/docs/components/forms.html">Foundation form</a>. Create an HTML form with <code>method="post"</code>. Within the form, create a <code>&lt;fieldset&gt;</code> and <code>&lt;legend&gt;</code>:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;form</span> <span class="na">method=</span><span class="s">"post"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;fieldset&gt;</span>
    <span class="nt">&lt;legend&gt;</span>Tell Us What You Think<span class="nt">&lt;/legend&gt;</span>
  <span class="nt">&lt;/fieldset&gt;</span>
<span class="nt">&lt;/form&gt;</span>
</pre></div>
</li>
<li><p>Add a text field for the person to record their name.  Read the documentation to make sure this is formatted properly.</p></li>
<li>
<p>Add a drop-down list to specify what the area the feedback relates to. Below is suggested content:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"row"</span><span class="nt">&gt;</span>
 <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"small-12 columns"</span><span class="nt">&gt;</span>
 <span class="nt">&lt;label&gt;</span>Report about<span class="nt">&lt;/label&gt;</span>
 <span class="nt">&lt;select</span> <span class="na">name=</span><span class="s">"report_item"</span><span class="nt">&gt;</span>
   <span class="nt">&lt;option&gt;&lt;/option&gt;</span>
   <span class="nt">&lt;option&gt;</span>Movies<span class="nt">&lt;/option&gt;</span>
   <span class="nt">&lt;option&gt;</span>Theaters<span class="nt">&lt;/option&gt;</span>
   <span class="nt">&lt;option&gt;</span>Other Patrons<span class="nt">&lt;/option&gt;</span>
   <span class="nt">&lt;option&gt;</span>Unintelligible Gibberish<span class="nt">&lt;/option&gt;</span>
 <span class="nt">&lt;/select&gt;</span>
 <span class="nt">&lt;/div&gt;</span>
<span class="nt">&lt;/div&gt;</span>
</pre></div>
</li>
<li>
<p>Add a series of checkboxes with options for the user to choose from that relate to the feedback they are giving. Below is some suggested content:</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"row"</span><span class="nt">&gt;</span>
 <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"small-12 columns"</span><span class="nt">&gt;</span>
 <span class="nt">&lt;label&gt;</span>Check all that apply:<span class="nt">&lt;/label&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"great"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>I had an enjoyable experience.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"rabid_ducks"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>I would rather been pecked to death by rabid ducks.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"clueless"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>I had no idea what this movie was about.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"best_movie"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>It was one of the best movies I've ever seen.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"pittsburgh"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>At least this one involved Pittsburgh in some fashion.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"confused"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>I feel stunned and confused by what I observed at the movie theater.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">name=</span><span class="s">"optionsCheckboxes"</span> <span class="na">value=</span><span class="s">"lollipop"</span> <span class="nt">/&gt;</span>
   <span class="nt">&lt;label&gt;</span>I'd like a lollipop.<span class="nt">&lt;/label&gt;&lt;br</span> <span class="nt">/&gt;</span>
 <span class="nt">&lt;/div&gt;</span>
<span class="nt">&lt;/div&gt;</span>
</pre></div>
</li>
<li><p>Add in a textarea input to allow free-form feedback from the user.</p></li>
<li><p>Add a submit button and a reset button.  Verify everything is working in the browser and then add and commit the changes to git.</p></li>
</ol>

<hr>

<h1>
<span class="mega-icon mega-icon-issue-opened"></span> Stop</h1>

<p>Show a TA that you have completed the first part. Make sure the TA initials your sheet.</p>

<hr>

<h1>On Your Own</h1>

<p>This week the "on your own" assignment is to go to <a href="http://rubymonk.com/learning/books/1">RubyMonk's free Ruby Primer</a> and complete the following exercises:</p>

<ul>
<li><p>Introduction To Ruby Objects</p></li>
<li><p>Arrays in Ruby</p></li>
<li><p>Introduction to Ruby Methods</p></li>
</ul>
  </div>
