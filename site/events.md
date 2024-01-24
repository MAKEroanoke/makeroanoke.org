---
layout: page
title: Upcoming Events
permalink: /events/
---

[Archived Events](/past-events/)

{% assign current_events = site.events | where_exp: "event", "event.date >= site.time" %}

{% for event in current_events %}
  <article class="entry">
    <header class="entry-header">
      <h3><a href="{{ event.url }}">{{ event.title }}</a></h3>
      {% if event.image.thumbnail %}
        {% assign entry_image = post.image.thumbnail | relative_url | escape %}
        <img class="entry-image u-photo" src="{{ entry_image }}" alt="">
      {% endif %}
    </header>
    <p class="author">
      {% if event.event_date %}
        <span class="icon">{% include icon-calendar.svg %}</span> 
        <time class="entry-time" datetime="{{ event.event_date | date_to_xmlschema }}">
          {{ event.event_date | date: "%B %-d, %Y" }}
        </time>
      {% endif %}
    </p>
    <div class="content">
      {{ event.excerpt }}
      <a href="{{ event.url }}">... read more</a>
    </div>
  </article>
{% endfor %}
