---
layout: page
title: Archived Events
permalink: /past-events/
---
[Current Events](/events/)

{% assign archived_events = site.events | where_exp: "event", "event.date <= site.time" %}
{% for event in archived_events %}
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
{% for event in archived_events %}
  <h1><a href="{{ event.url }}">{{ event.title }}</a></h1>
  <p class="author">
    {% if event.event_date %}
      <span class="icon">{% include icon-calendar.svg %}</span> <time class="entry-time" datetime="{{ event.event_date | date_to_xmlschema }}">{{ event.event_date | date: "%B %-d, %Y" }}</time>
    {% endif %}
  </p>
  <div class="content">
    {{ event.excerpt }}
  </div>
{% endfor %}
