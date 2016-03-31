<div class="featured-event-bg" style="background-image: url(https://www.interworks.com/sites/default/files/blog/SurvivalCruvesFeat.jpg)">
<div class="dots">
<div class="black-grad gradient">
<div class="mw table-height">
<div class="row remove-margins">
<div class="content-title col-xs-12 col-sm-12">

This repository is for exploratory code used to inform the following blog originally posted on the <a href="https://www.interworks.com/blog/alentz/2016/01/05/survival-curves-how-quickly-do-nfl-players-get-arrested"> InterWorks Blog</a>. The blog references an <a href='http://datasci.interworks.com/nfl'> interactive application</a> built on Python-Flask using Tableau for the visualizations. 

<h1>Survival Curves: How Quickly Do NFL Players Get Arrested?</h1>
</div>
</div>
</div>
</div>
</div>
</div>
 
 
<div class="mw">
<div class="row remove-margins">
<div class="content-area col-md-12 col-lg-12 col-sm-12">
 
<div class="main-content col-sm-12 col-md-12">
<div class="row remove-margins">
<div class="content-title col-xs-12 col-sm-12">
<div class="region region-content">
<div id="block-system-main" class="block block-system block-odd first clearfix">
<div id="node-9925" class="node node-blog-entry">
<span class="submitted">By <a href="https://www.interworks.com/blog/alentz">Alex Lentz</a> 1.5.16</span>

<div class="field field-name-body field-type-text-with-summary field-label-hidden"><div class="field-items"><div class="field-item even"><p><span style="line-height: 1.6em;">Recently, our own <a href="https://www.interworks.com/about-us/people/dan-murray#profile-public" target="_blank">Dan Murray</a> blogged about </span><a href="https://www.interworks.com/blog/dmurray/2015/12/21/nfl-player-arrests-visualized-tableau" style="line-height: 1.6em;" target="_blank">NFL Players and their arrests</a><span style="line-height: 1.6em;">. This got me thinking about the risk of a newly drafted NFL Player being arrested, which of course also got me thinking about survival analysis. Wait. What did I just say?</span></p>
<h2><span style="line-height: 1.6em;">Survival Analysis Explained</span></h2>
<p>Survival analysis is most closely associated with medical and recidivism studies – think of it as analyzing the time to an event. In medical studies, it’s the time until someone dies. In prisoner recidivism studies, it’s the time until a former inmate returns to prison. <strong>Survival curves</strong> can help look at the risk facing a given population, and predictive models can even be built to estimate when an event will happen.</p>
<p>To keep things simple, I wanted to look at what the curve would look like for players drafted to the NFL. To do this, I took the data from Dan’s article and joined in some outside data on all NFL players. I brought in the outside data in order to get the entire population of NFL players – not just the ones who committed crimes. I limited the data to only players who have been drafted since 2000 as the arrest data only included arrests back to 2000.</p>
<p>Then, I looked at <strong>Kaplan-Meier </strong>curves. Kaplan-Meier curves are actually quite intuitive as they are plotted with the function:</p>
<p align="center" >KM(<em>t</em>) = Individuals Left at Time<em> t </em>/ Total Individuals</p>
<p>Essentially, at any given time <em>t</em>, what is the % of individuals who have <em>not</em> had the event occur. In our case, it is the % of Drafted NFL Players who have not been arrested. Here is a quick look at some output from the <a href="http://lifelines.readthedocs.org/en/latest/index.html"><strong>Lifelines</strong></a> package in Python. Timeline is in years:</p>
<p align="center"><img alt="KM_estimate" src="https://www.interworks.com/sites/default/files/blog-content/SurvivalCurves1.png" style="border-width: 0px; border-style: solid;"/></p>
<p>Looking at the chart, the blue line is the estimate with light blue confidence bands around the line. The bands get larger as we get further out in years as we have less data.</p>
<p>Looking at the curve for the entire population, about 93% of draftees have not been arrested within four years of being drafted – meaning 7% have. Interesting. But what about players with different backgrounds?</p>
<h2>Does College&nbsp;Make a Difference?</h2>
<p>Being the huge college football fan that I am (Go Nittany Lions and Wolfpack!), I wondered if the college program that the player was drafted out of mattered. One way to look at whether or not college is relevant is to plot two separate curves (one for players from a particular college and one for all other colleges). Here is an example using USC (Southern Cal):</p>
<p align="center"><img alt="Survival curve: USC vs. everyone else" height="357" src="https://www.interworks.com/sites/default/files/blog-content/SurvivalCurves2.png" style="border-width: 0px; border-style: solid;" width="532"/></p>
<p>A little more interesting. But are these curves <em>that</em> different from one another? Well, we can measure this statistically with hypothesis testing! Using the LogRank test (since we’re comparing two curves – for those nerds out there), we can test if the difference between the curves is statistically significant. Sorry, Trojan fans – your curve is statistically different from the other colleges in aggregate.</p>
<h2>Visualizing the Results in Tableau</h2>
<p>To make this a little more entertaining than static images from Python, I thought I’d use Python Flask,&nbsp;a Postgres database&nbsp;and a Tableau dashboard to give you an interactive app to compare the curve of the college of your choice to all other colleges. Beware Trojans, Mountaineers, Terrapins and Cowboys.</p>
<p><a class="portal-link" href="http://datasci.interworks.com/nfl" style="border: 1px solid #dedede; max-width: 800px; height: auto; width: 100%; display: block; margin: 40px auto;" target="_blank"><img alt="" src="https://www.interworks.com/sites/default/files/college-tableau-arrests.jpg"/></a></p>
<p>While the NFL data is interesting for sports fans, this problem of analyzing time to an event is very common in the business world. How likely are my employees to leave in the next two years? Are certain groups of customers leaving at faster rates than others? There are many problems that involve analyzing events, and survival analysis is one way to approach it. Beyond survival curves, we can use hazard functions and regression models to help us not only look at the probability of an event but also get a prediction based on different factors. More on that at a later date ...</p>
</div></div></div>
</div>  
</div>  
