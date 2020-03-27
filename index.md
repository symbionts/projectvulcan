
<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  }
  div.output_wrapper {
    display: block;
    page-break-inside: avoid;
  }
  div.output {
    display: block;
    page-break-inside: avoid;
  }
}
</style>

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
<!-- MathJax configuration -->
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [ ['$','$'], ["\\(","\\)"] ],
        displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
        processEscapes: true,
        processEnvironments: true
    },
    // Center justify equations in code and markdown cells. Elsewhere
    // we use CSS to left justify single line equations in code cells.
    displayAlign: 'center',
    "HTML-CSS": {
        styles: {'.MathJax_Display': {"margin": 0}},
        linebreaks: { automatic: true }
    }
});
</script>
<!-- End of mathjax configuration -->

<style>
        .cell.nbinteract-left {
            width: 50%;
            float: left;
        }

        .cell.nbinteract-right {
            width: 50%;
            float: right;
        }

        .cell.nbinteract-hide_in > .input {
            display: none;
        }

        .cell.nbinteract-hide_out > .output_wrapper {
            display: none;
        }

        .cell:after {
          content: "";
          display: table;
          clear: both;
        }

        div.output_subarea {
            max-width: initial;
        }

        .jp-OutputPrompt {
            display: none;
        }
    </style>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container">
      



  <div class="cell text_cell">
    <button class="js-nbinteract-widget">
      Loading widgets...
    </button>
  </div>




  
<center>
  <div class="nbinteract-hide_in
      cell border-box-sizing code_cell rendered">
    <div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#nbi:hide_in</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span> 
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span> 
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">string</span>
<span class="kn">from</span> <span class="nn">ipywidgets</span> <span class="kn">import</span> <span class="n">widgets</span>
<span class="kn">from</span> <span class="nn">ipywidgets</span> <span class="kn">import</span> <span class="n">interact</span><span class="p">,</span> <span class="n">interactive</span>
<span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">display</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">requests</span>
<span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

  </div>

  

  <div class="nbinteract-hide_in
      cell border-box-sizing code_cell rendered">
    <div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#nbi:hide_in</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_html</span><span class="p">(</span><span class="s2">&quot;data.html&quot;</span><span class="p">)[</span><span class="mi">0</span><span class="p">]</span>
<span class="n">pd</span><span class="o">.</span><span class="n">set_option</span><span class="p">(</span><span class="s1">&#39;display.max_rows&#39;</span><span class="p">,</span> <span class="kc">None</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">set_option</span><span class="p">(</span><span class="s1">&#39;display.max_columns&#39;</span><span class="p">,</span> <span class="kc">None</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">set_option</span><span class="p">(</span><span class="s1">&#39;display.width&#39;</span><span class="p">,</span> <span class="kc">None</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">set_option</span><span class="p">(</span><span class="s1">&#39;display.max_colwidth&#39;</span><span class="p">,</span> <span class="o">-</span><span class="mi">1</span><span class="p">)</span>

<span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;HOSTEL_ROOM&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">,</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">drop_duplicates</span><span class="p">(</span><span class="n">keep</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span><span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;STUDENT_ID&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="s1">&#39;B1&#39;</span><span class="p">)]</span>

<span class="n">df</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">subset</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;HOSTEL&#39;</span><span class="p">],</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">HOSTEL</span> <span class="o">!=</span> <span class="s1">&#39;Withdrawl&#39;</span><span class="p">]</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">HOSTEL</span> <span class="o">!=</span> <span class="s1">&#39;Withdrawal&#39;</span><span class="p">]</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">HOSTEL</span> <span class="o">!=</span> <span class="s1">&#39;Temporary Withdrawal&#39;</span><span class="p">]</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">HOSTEL</span> <span class="o">!=</span> <span class="s1">&#39;Permanent Withdrawal&#39;</span><span class="p">]</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">HOSTEL</span> <span class="o">!=</span> <span class="s1">&#39;PERMANENT WITHDRAWAL&#39;</span><span class="p">]</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="o">.</span><span class="n">HOSTEL</span> <span class="o">!=</span> <span class="s1">&#39;Registration Cancelled&#39;</span><span class="p">]</span>
<span class="c1">#df = df[df.HOSTEL != &#39;Thesis submission&#39;]</span>
<span class="c1">#df = df[df.HOSTEL != &#39;Thesis&#39;]</span>
<span class="c1">#df = df[df.HOSTEL != &#39;PS2&#39;]</span>
<span class="c1">#df = df[df.HOSTEL != &#39;Graduate&#39;]</span>
<span class="n">df</span><span class="o">.</span><span class="n">index</span> <span class="o">=</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="n">df</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span><span class="o">+</span><span class="mi">1</span><span class="p">)</span>

<span class="n">year</span><span class="o">=</span> <span class="p">[]</span>
<span class="k">for</span> <span class="n">ID</span> <span class="ow">in</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;STUDENT_ID&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">tolist</span><span class="p">():</span>
    <span class="n">year</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">ID</span><span class="p">[:</span><span class="mi">4</span><span class="p">])</span>
<span class="n">df</span><span class="p">[</span><span class="s1">&#39;BATCH&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">year</span>

<span class="n">hostel_items</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;All&#39;</span><span class="p">]</span><span class="o">+</span><span class="nb">sorted</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;HOSTEL&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">unique</span><span class="p">()</span><span class="o">.</span><span class="n">tolist</span><span class="p">())</span>
<span class="n">year_items</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;All&#39;</span><span class="p">]</span><span class="o">+</span><span class="nb">sorted</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;BATCH&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">unique</span><span class="p">()</span><span class="o">.</span><span class="n">tolist</span><span class="p">())</span>
<span class="nd">@interact</span><span class="p">(</span>
    <span class="n">Hostel</span><span class="o">=</span><span class="n">hostel_items</span><span class="p">,</span> 
    <span class="n">Show</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]),</span> 
    <span class="n">Year</span><span class="o">=</span><span class="n">year_items</span><span class="p">,</span> <span class="n">Name</span><span class="o">=</span><span class="s1">&#39;&#39;</span><span class="p">)</span>

<span class="k">def</span> <span class="nf">view</span><span class="p">(</span><span class="n">Hostel</span><span class="o">=</span><span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="n">Year</span><span class="o">=</span><span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="n">Name</span><span class="o">=</span><span class="s1">&#39;All&#39;</span><span class="p">,</span> <span class="n">Show</span><span class="o">=</span><span class="s1">&#39;15&#39;</span><span class="p">):</span>
    <span class="k">if</span> <span class="n">Hostel</span><span class="o">==</span><span class="s2">&quot;All&quot;</span> <span class="ow">and</span> <span class="n">Year</span><span class="o">==</span><span class="s2">&quot;All&quot;</span><span class="p">:</span>
        <span class="k">return</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;NAME&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="n">Name</span><span class="o">.</span><span class="n">upper</span><span class="p">())]</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">Show</span><span class="p">)</span>
    <span class="k">elif</span> <span class="n">Hostel</span><span class="o">==</span><span class="s2">&quot;All&quot;</span> <span class="ow">and</span> <span class="n">Year</span><span class="o">!=</span><span class="s2">&quot;All&quot;</span><span class="p">:</span>
        <span class="k">return</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;BATCH&#39;</span><span class="p">]</span><span class="o">==</span><span class="n">Year</span><span class="p">][</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;NAME&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="n">Name</span><span class="o">.</span><span class="n">upper</span><span class="p">())]</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">Show</span><span class="p">)</span>
    <span class="k">elif</span> <span class="n">Hostel</span><span class="o">!=</span><span class="s2">&quot;All&quot;</span> <span class="ow">and</span> <span class="n">Year</span><span class="o">==</span><span class="s2">&quot;All&quot;</span><span class="p">:</span>
        <span class="k">return</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;HOSTEL&#39;</span><span class="p">]</span><span class="o">==</span><span class="n">Hostel</span><span class="p">][</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;NAME&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="n">Name</span><span class="o">.</span><span class="n">upper</span><span class="p">())]</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">Show</span><span class="p">)</span>
    <span class="k">elif</span> <span class="n">Hostel</span><span class="o">!=</span><span class="s2">&quot;All&quot;</span> <span class="ow">and</span> <span class="n">Year</span><span class="o">!=</span><span class="s2">&quot;All&quot;</span><span class="p">:</span>
        <span class="k">return</span> <span class="n">df</span><span class="p">[</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;HOSTEL&#39;</span><span class="p">]</span><span class="o">==</span><span class="n">Hostel</span><span class="p">][</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;BATCH&#39;</span><span class="p">]</span><span class="o">==</span><span class="n">Year</span><span class="p">][</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;NAME&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="n">Name</span><span class="o">.</span><span class="n">upper</span><span class="p">())]</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">Show</span><span class="p">)</span>
   
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    



  <div class="output_subarea output_widget_view ">
    <button class="js-nbinteract-widget">
      Loading widgets...
    </button>
  </div>

</div>

</div>
</div>

  </div>

  
<!--
  <div class="
      cell border-box-sizing code_cell rendered">
    <div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>

    </div>
</div>
</div>

  </div> -->


<!-- Loads nbinteract package -->
<script src="https://unpkg.com/nbinteract-core" async></script>
<script>
  (function setupNbinteract() {
    // If NbInteract hasn't loaded, wait one second and try again
    if (window.NbInteract === undefined) {
      setTimeout(setupNbinteract, 1000)
      return
    }

    var interact = new window.NbInteract({
      spec: 'symbionts/notebooks/master',
      baseUrl: 'https://mybinder.org',
      provider: 'gh',
    })
    interact.prepare()

    window.interact = interact
  })()
</script>
    </div>
  </div>
</center>
