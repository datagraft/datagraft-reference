---
layout: default
title: News
permalink: /news/
weight: -12
---
<div class="mdl-grid newspost-grid">

{% for post in site.posts offset %}

    <div class="mdl-card mdl-shadow--2dp mdl-cell mdl-cell--4-col mdl-cell--4-col-desktop mdl-cell--4-col-tablet  mdl-cell--12-col-phone">
      <div class="mdl-card__title" {% if post.image %} style="background: url('{{ post.image }}') center/cover;" {% endif %}>
        <h2 class="mdl-card__title-text">{{ post.title }}</h2>
      </div>
      <div class="mdl-card__supporting-text">
        {{ post.content | strip_html | truncatewords:50 }}
      </div>
      <button class="post-button mdl-button mdl-js-button mdl-button--fab mdl-js-ripple-effect mdl-button--colored" onclick="location.href='{{ post.url | prepend: site.baseurl }}'">
        <i class="material-icons">keyboard_arrow_right</i>
      </button>
      <div class="mdl-card__actions mdl-card--border">
        <a class="mdl-button mdl-button--colored mdl-js-button mdl-js-ripple-effect" href="{{ post.url | prepend: site.baseurl }}">
          {{ post.date | date: "%b %-d, %Y" }}
        </a>
      </div>
    </div>

    {% endfor %}

</div>

{% include footer.html %}