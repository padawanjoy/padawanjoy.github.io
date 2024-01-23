---
layout: page
gallery_title: Gallery
gallery_subtitle: My design works and the photos I've captured
permalink: /gallery/
gallery_path: "images/pexels"
---

<div class="container">
    <div class="row">
        <div class="col col-12">
            <div class="hero__inner">
                <h1 class="hero__title">{{page.gallery_title}}</h1>
                <p class="hero__description">{{page.gallery_subtitle}}</p>
            </div>
        </div>
    </div>
</div>


<div class="gallery-box">
  <div class="gallery gallery--post">
    {% for image in site.static_files %}
      {% if image.path contains page.gallery_path %}
        {% unless image.path contains '.md' %}
            <img src="{{ image.path | relative_url }}" loading="lazy" alt="">
        {% endunless %}
      {% endif %}
    {% endfor %}
  </div>
</div>