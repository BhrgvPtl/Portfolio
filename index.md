---
layout: default
title: Home
---

<div class="desktop">
  <div class="dock">
    <button data-win="about">About</button>
    <button data-win="projects">Projects</button>
    <button data-win="resume">Resume</button>
    <button data-win="contact">Contact</button>
  </div>

  <!-- ABOUT WINDOW -->
  <div class="window front" id="about" style="left:40px; top:120px;">
    <div class="bar"><span>about.md</span><div class="dots"><b></b><b></b><b></b></div></div>
    <div class="content">
      <h1>$ whoami</h1>
      <p>Bhargav Patel — data/ML engineer shipping measurable impact.</p>
      <pre class="term">> skills --show python sql pytorch transformers mlops analytics</pre>
      <p>I build data products end-to-end: pipelines → models → dashboards → outcomes.</p>
    </div>
  </div>

  <!-- PROJECTS WINDOW -->
  <div class="window" id="projects" style="left:420px; top:160px;">
    <div class="bar"><span>projects.json</span><div class="dots"><b></b><b></b><b></b></div></div>
    <div class="content grid">
      {% for p in site.data.projects %}
      <a class="card" href="{{ p.url }}" target="_blank" rel="noopener">
        <img src="{{ p.img | relative_url }}" alt="{{ p.title }}" loading="lazy" width="1200" height="675">
        <h3>{{ p.title }}</h3>
        <code>{{ p.tags | join: ', ' }}</code>
        <p class="lede">{{ p.blurb }}</p>
        <span class="btn">Check it out</span>
      </a>
      {% endfor %}
    </div>
  </div>

  <!-- RESUME WINDOW -->
  <div class="window" id="resume" style="left:180px; top:380px;">
    <div class="bar"><span>resume.pdf</span><div class="dots"><b></b><b></b><b></b></div></div>
    <div class="content">
      <p><a class="btn" href="{{ '/pdf/resume.pdf' | relative_url }}" target="_blank" rel="noopener">Open resume</a></p>
      <ul class="bullets">
        <li>Reduced inference cost <b>32%</b> via quantization + batching</li>
        <li>Built GCP ELT; freshness from <b>24h → 30m</b></li>
        <li>Deployed transformer prototype end-to-end</li>
      </ul>
    </div>
  </div>

  <!-- CONTACT WINDOW -->
  <div class="window" id="contact" style="left:720px; top:360px;">
    <div class="bar"><span>contact.txt</span><div class="dots"><b></b><b></b><b></b></div></div>
    <div class="content">
      <p><a href="mailto:you@example.com">you@example.com</a></p>
      <p><a href="https://www.linkedin.com/in/<your-handle>/" target="_blank" rel="noopener">LinkedIn</a> · <a href="https://github.com/BhrgvPtl" target="_blank" rel="noopener">GitHub</a></p>
      <pre class="term">> say-hi --subject "Project ideas or roles"</pre>
    </div>
  </div>
</div>

<!-- ========================= -->
<!--  My Hobby (polished grid) -->
<!-- ========================= -->

## My Hobby {#my-hobby}

<p class="lede">Outside work, I explore football analytics and shoot match moments & training sessions. A few snaps:</p>

<ul class="gallery">
  <li>
    <a href="{{ '/images/hobby-1.jpg' | relative_url }}" class="lightbox" data-caption="Training drill — passing lanes">
      <figure>
        <img src="{{ '/images/hobby-1.jpg' | relative_url }}" alt="Training drill — passing lanes" loading="lazy" width="1200" height="900">
        <figcaption>Training drill — passing lanes</figcaption>
      </figure>
    </a>
  </li>
  <li>
    <a href="{{ '/images/hobby-2.jpg' | relative_url }}" class="lightbox" data-caption="Matchday — build-up shape">
      <figure>
        <img src="{{ '/images/hobby-2.jpg' | relative_url }}" alt="Matchday — build-up shape" loading="lazy" width="1200" height="900">
        <figcaption>Matchday — build-up shape</figcaption>
      </figure>
    </a>
  </li>
  <li>
    <a href="{{ '/images/hobby-3.jpg' | relative_url }}" class="lightbox" data-caption="Pressing trigger — minute 63">
      <figure>
        <img src="{{ '/images/hobby-3.jpg' | relative_url }}" alt="Pressing trigger — minute 63" loading="lazy" width="1200" height="900">
        <figcaption>Pressing trigger — minute 63</figcaption>
      </figure>
    </a>
  </li>
</ul>

<!-- Lightweight lightbox -->
<div id="lb" class="lb" hidden>
  <button class="lb-close" aria-label="Close">×</button>
  <img id="lb-img" alt="">
  <p id="lb-cap"></p>
</div>

<script>
  // Dock toggles
  document.querySelectorAll('.dock button').forEach(b=>{
    b.addEventListener('click', ()=>{
      const win = document.getElementById(b.dataset.win);
      win.classList.toggle('front');
    });
  });

  // Drag windows
  document.querySelectorAll('.window').forEach(win=>{
    let dx=0,dy=0,drag=false,bar=win.querySelector('.bar');
    bar.addEventListener('mousedown',e=>{drag=true; dx=e.clientX-win.offsetLeft; dy=e.clientY-win.offsetTop; win.classList.add('front');});
    document.addEventListener('mousemove',e=>{ if(!drag) return; win.style.left=(e.clientX-dx)+'px'; win.style.top=(e.clientY-dy)+'px'; });
    document.addEventListener('mouseup',()=>drag=false);
  });

  // Hobby lightbox
  (function(){
    const lb = document.getElementById('lb');
    const img = document.getElementById('lb-img');
    const cap = document.getElementById('lb-cap');
    function open(src, caption){ img.src = src; cap.textContent = caption || ''; lb.hidden = false; }
    function close(){ lb.hidden = true; img.src = ''; cap.textContent=''; }
    document.querySelectorAll('a.lightbox').forEach(a=>{
      a.addEventListener('click', e=>{
        e.preventDefault();
        open(a.href, a.dataset.caption);
      });
    });
    lb.addEventListener('click', e=>{ if(e.target === lb) close(); });
    document.querySelector('.lb-close').addEventListener('click', close);
    document.addEventListener('keydown', e=>{ if(e.key === 'Escape') close(); });
  })();
</script>
