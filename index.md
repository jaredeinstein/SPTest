---
layout: page
title: Treats by Heather
image_sliders:
  - slider1
image_sliders_load_all: true
---

<div id="main">

    <nav><ul>
      {% for node in site.posts reversed %}
        {% capture id %}{{ node.id | remove:'/' | downcase }}{% endcapture %}
        <li class="p-{{id}}"><a href="#{{id}}">{{node.title}}</a></li>
      {% endfor %}
    </ul></nav>
  

    {% for page in site.posts reversed %}
      {% capture id %}{{ page.id | remove:'/' | downcase }}{% endcapture %}
      <div id="{{id}}" class="section p-{{id}}">
        {% if page.icon %}
        <div class="subtlecircle sectiondivider imaged">
          <img src="{{page.icon}}" alt="section icon" />
          <h5 class="icon-title">{{ page.title }}</h5>
        </div>
        {% elsif page.fa-icon %}
        <div class="subtlecircle sectiondivider faicon">
          <span class="fa-stack">
            <i class="fas fa-circle fa-stack-2x"></i>
            <i class="fas fa-{{ page.fa-icon }} fa-stack-1x"></i>
          </span>
          <h5 class="icon-title">{{ page.title }}</h5>
        </div>
        {% endif %}
        <div class="container {{ page.style }}">
          {{ page.content }}
        </div>
      </div>
    {% endfor %}


    <div id="footer" class="section text-white">
      <div class="container">
        {% capture foottext %} {% include footer.md %} {% endcapture %}
        {{ foottext | markdownify }}
      </div>
    </div>
  </div>
