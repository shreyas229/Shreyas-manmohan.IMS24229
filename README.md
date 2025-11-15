<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Modularity on the Karate Club Graph - README</title>
<style>
    body {
        font-family: Arial, sans-serif;
        line-height: 1.6;
        padding: 20px;
        max-width: 900px;
        margin: auto;
        background: #fafafa;
    }
    h1, h2, h3, h4 {
        color: #2b3a55;
    }
    code {
        background: #eee;
        padding: 2px 4px;
        border-radius: 4px;
    }
    pre {
        background: #eee;
        padding: 10px;
        border-radius: 6px;
        overflow-x: auto;
    }
</style>
</head>

<body>

<h1>📘 <strong>MODULARITY ON THE KARATE CLUB GRAPH</strong></h1>
<h3><strong>DSC212 — GRAPH THEORY ASSIGNMENT</strong></h3>

<p>
This repository contains the full implementation of <strong>spectral modularity maximization</strong> on 
<strong>Zachary’s Karate Club graph</strong>, following <strong>Newman’s spectral method</strong> for community detection.
</p>

<p>The notebook performs:</p>
<ul>
    <li>✔️ <strong>Modularity matrix construction</strong></li>
    <li>✔️ <strong>Spectral bipartition (leading eigenvector)</strong></li>
    <li>✔️ <strong>Recursive multi-community detection</strong></li>
    <li>✔️ <strong>Graph visualizations at each split</strong></li>
    <li>✔️ <strong>Centrality metric computation</strong></li>
    <li>✔️ <strong>Metric evolution plots</strong></li>
    <li>✔️ <strong>Discussion and interpretation</strong></li>
</ul>

<hr>

<h2>📂 <strong>REPOSITORY STRUCTURE</strong></h2>

<pre>
📁 Karate-Modularity/
│── karate_modularity.ipynb     # Main Jupyter Notebook (runs top-to-bottom)
│── README.md                   # Project description and usage guide
</pre>

<hr>

<h2>🧠 <strong>BACKGROUND</strong></h2>

<p>
Zachary’s Karate Club is a well-known social network of <strong>34 members</strong> whose real-world 
split into two factions makes it ideal for testing <strong>community detection</strong> algorithms.
</p>

<p>We use <strong>modularity</strong>, which compares:</p>

<ul>
<li><strong>Actual within-community edges</strong></li>
<li>vs.</li>
<li><strong>Expected edges under a random graph preserving node degrees</strong></li>
</ul>

<p>
The modularity matrix is:
</p>

<pre>
B = A - (k kᵀ) / (2m)
</pre>

<p>
The <strong>leading eigenvector</strong> of <code>B</code> provides a statistically meaningful bipartition:
</p>

<ul>
<li>positive entries → <strong>Community 1</strong></li>
<li>negative entries → <strong>Community 2</strong></li>
</ul>

<hr>

<h2>🔍 <strong>ALGORITHM SUMMARY</strong></h2>

<h3><strong>1. Compute Global Modularity Matrix</strong></h3>
<p>Based on adjacency, degrees, and total edge count.</p>

<h3><strong>2. Spectral Bipartition</strong></h3>
<ul>
    <li>Compute the <strong>largest eigenvalue</strong> and eigenvector</li>
    <li>Split nodes by sign</li>
</ul>

<h3><strong>3. Recursive Bisection</strong></h3>
<p>For each community:</p>

<ul>
    <li>Extract <strong>restricted modularity matrix</strong></li>
    <li>Compute its <strong>largest eigenvalue</strong></li>
    <li><strong>If λ > 0</strong> → splitting increases modularity → continue splitting</li>
    <li><strong>If λ ≤ 0</strong> → community is indivisible</li>
</ul>

<p>Recursion stops when all communities have <strong>non-positive leading eigenvalues</strong>.</p>

<hr>

<h2>🎨 <strong>VISUALIZATIONS</strong></h2>

<p>Each iteration includes:</p>
<ul>
    <li><strong>Color-coded communities</strong></li>
    <li><strong>Fixed spring layout</strong> for consistent visualisation</li>
    <li><strong>Node labels</strong> for clarity</li>
    <li><strong>Split progression grid</strong> over iterations</li>
</ul>

<hr>

<h2>📊 <strong>CENTRALITY METRICS</strong></h2>

<p>After each split, we compute:</p>

<h3><strong>Degree Centrality</strong></h3>
<p>How many neighbors a node has.</p>

<h3><strong>Betweenness Centrality</strong></h3>
<p>How often a node lies on shortest paths.</p>

<h3><strong>Closeness Centrality</strong></h3>
<p>How close a node is to all others in the network.</p>

<h3><strong>Clustering Coefficient</strong></h3>
<p>How interconnected a node’s neighbors are.</p>

<h3><strong>Metric Evolution Plots</strong></h3>
<p>These visualize:</p>
<ul>
    <li><strong>Stable hubs</strong></li>
    <li><strong>Bridge nodes</strong></li>
    <li><strong>Core community nodes</strong></li>
    <li><strong>Role changes caused by splitting</strong></li>
</ul>

<hr>

<h2>▶️ <strong>HOW TO RUN</strong></h2>

<h3><strong>1. Clone the repository</strong></h3>
<pre>
git clone &lt;your-repo-url&gt;
</pre>

<h3><strong>2. Install dependencies</strong></h3>
<pre>
pip install numpy networkx matplotlib
</pre>

<h3><strong>3. Open the notebook</strong></h3>
<pre>
jupyter notebook karate_modularity.ipynb
</pre>

<h3><strong>4. Run it top-to-bottom</strong></h3>
<p>No manual edits required.</p>

<hr>

<h2>📝 <strong>DISCUSSION (SUMMARY)</strong></h2>

<ul>
    <li>The initial spectral split matches the <strong>real-world faction divide</strong>.</li>
    <li>Nodes with high degree/betweenness act as <strong>bridges</strong>.</li>
    <li>Recursive splitting reveals <strong>natural subgroups</strong>.</li>
    <li>Metric evolution highlights how node roles shift during splitting.</li>
</ul>

<hr>

<h2>📚 <strong>REFERENCE</strong></h2>

<p>
Newman, M. E. J. (2006).<br>
<strong>Modularity and community structure in networks.</strong><br>
<i>Proceedings of the National Academy of Sciences</i>, 103(23), 8577–8582.
</p>

<hr>

<h2>✍️ <strong>AUTHOR</strong></h2>
<p><strong>Shreyas Manmohan</strong><br>
<strong>Roll No: IMS24229</strong></p>

<hr>

</body>
</html>
