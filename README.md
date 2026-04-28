# Test-Webpage-for-Scrollytelling
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Three-Chart Scrollytelling Story</title>

<script src="https://public.flourish.studio/resources/embed.js"></script>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
font-family:Georgia,serif;
background:#fafafa;
color:#222;
line-height:1.6;
overflow-x:hidden;
}

/* Full screen narrative chapters */
.chapter{
min-height:100vh;
display:flex;
align-items:center;
justify-content:center;
padding:8vw;
}

.chapter-text{
max-width:760px;
font-size:1.35rem;
}

h1{
font-size:4rem;
margin-bottom:1rem;
}

h2{
font-size:2.8rem;
margin-bottom:1rem;
}

.scrolly{
display:flex;
max-width:1500px;
margin:auto;
}

.steps{
width:45%;
padding:0 5vw;
}

.step{
min-height:100vh;
display:flex;
align-items:center;
opacity:.28;
transition:.35s;
}

.step.active{
opacity:1;
}

.card{
background:white;
padding:2rem;
border-radius:18px;
box-shadow:0 10px 30px rgba(0,0,0,.08);
}

.card h3{
font-size:2rem;
margin-bottom:1rem;
}

.graphic{
width:55%;
height:100vh;
position:sticky;
top:0;
display:flex;
align-items:center;
justify-content:center;
background:#f2f2f2;
padding:3vw;
}

.chart-box{
width:100%;
max-width:900px;
background:white;
padding:20px;
border-radius:16px;
box-shadow:0 12px 30px rgba(0,0,0,.1);
}

.annotation{
position:absolute;
right:50px;
bottom:50px;
max-width:320px;
background:rgba(255,255,255,.95);
padding:1rem 1.2rem;
border-radius:10px;
box-shadow:0 6px 18px rgba(0,0,0,.1);
}

footer{
padding:140px 8vw;
text-align:center;
font-size:1.2rem;
}

@media(max-width:900px){

.scrolly{
display:block;
}

.steps,
.graphic{
width:100%;
}

.graphic{
position:relative;
height:auto;
min-height:70vh;
}

.annotation{
position:relative;
right:auto;
bottom:auto;
margin-top:20px;
max-width:100%;
}

h1{
font-size:2.6rem;
}

}
</style>
</head>
<body>

<!-- INTRO -->
<section class="chapter">
<div class="chapter-text">
<h1>Headline Placeholder</h1>
<p>
TODO:
Opening narrative introducing your investigation or story.
Set up the argument across three charts.
</p>
</div>
</section>

<!-- CHART 1 -->
<section class="scrolly">

<div class="steps">

<div class="step active"
data-note="Chart 1 annotation placeholder">
<div class="card">
<h3>Chart 1 Step 1</h3>
<p>TODO narrative while chart scrolls.</p>
</div>
</div>

<div class="step"
data-note="Chart 1 second annotation">
<div class="card">
<h3>Chart 1 Step 2</h3>
<p>TODO explain pattern or change.</p>
</div>
</div>

<div class="step"
data-note="Chart 1 concluding annotation">
<div class="card">
<h3>Chart 1 Conclusion</h3>
<p>TODO summarize first chart insight.</p>
</div>
</div>

</div>

<div class="graphic">
<div class="chart-box">

<div class="flourish-embed flourish-chart"
data-src="visualisation/28733470"></div>

</div>

<div class="annotation note">
Chart annotations update here.
</div>
</div>

</section>

<!-- TRANSITION -->
<section class="chapter">
<div class="chapter-text">
<h2>Transition Placeholder</h2>
<p>
TODO:
Bridge from chart one into chart two.
Introduce new question or tension.
</p>
</div>
</section>

<!-- CHART 2 -->
<section class="scrolly">

<div class="steps">

<div class="step active"
data-note="Chart 2 opening annotation">
<div class="card">
<h3>Chart 2 Step 1</h3>
<p>TODO scroll explanation.</p>
</div>
</div>

<div class="step"
data-note="Chart 2 comparison annotation">
<div class="card">
<h3>Chart 2 Step 2</h3>
<p>TODO interpret second pattern.</p>
</div>
</div>

<div class="step"
data-note="Chart 2 takeaway annotation">
<div class="card">
<h3>Chart 2 Conclusion</h3>
<p>TODO summarize second chart.</p>
</div>
</div>

</div>

<div class="graphic">
<div class="chart-box">

<div class="flourish-embed flourish-chart"
data-src="visualisation/28733871"></div>

</div>

<div class="annotation note">
Chart annotations update here.
</div>
</div>

</section>

<!-- TRANSITION -->
<section class="chapter">
<div class="chapter-text">
<h2>Second Transition Placeholder</h2>
<p>
TODO:
Connect chart two to chart three.
Raise final argument or synthesis.
</p>
</div>
</section>

<!-- CHART 3 -->
<section class="scrolly">

<div class="steps">

<div class="step active"
data-note="Chart 3 opening annotation">
<div class="card">
<h3>Chart 3 Step 1</h3>
<p>TODO narrative while third chart scrolls.</p>
</div>
</div>

<div class="step"
data-note="Chart 3 highlight annotation">
<div class="card">
<h3>Chart 3 Step 2</h3>
<p>TODO emphasize final major finding.</p>
</div>
</div>

<div class="step"
data-note="Final chart takeaway annotation">
<div class="card">
<h3>Chart 3 Conclusion</h3>
<p>TODO conclude third visualization.</p>
</div>
</div>

</div>

<div class="graphic">
<div class="chart-box">

<div class="flourish-embed flourish-chart"
data-src="visualisation/28733804"></div>

</div>

<div class="annotation note">
Chart annotations update here.
</div>
</div>

</section>

<footer>
TODO:
Final conclusion, sources, methodology, credits.
</footer>

<script>
document.querySelectorAll('.scrolly').forEach(section=>{

const steps=section.querySelectorAll('.step');
const note=section.querySelector('.note');

const observer=new IntersectionObserver(
(entries)=>{
entries.forEach(entry=>{
if(entry.isIntersecting){

steps.forEach(s=>s.classList.remove('active'));
entry.target.classList.add('active');

note.textContent=
entry.target.dataset.note;

}
});
},
{
threshold:0.6
}
);

steps.forEach(step=>{
observer.observe(step);
});

});
</script>

</body>
</html>
