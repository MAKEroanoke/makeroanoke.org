---
layout: page
title: Archived Events
permalink: /past-events/
---

{% assign upcoming_events = site.events | where_exp: "event", "event.event_date < site.time" %} 
{% for event in upcoming_events %}
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