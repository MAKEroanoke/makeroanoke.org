---
title:  MAKE Roanoke Posts
layout: default
permalink:  /post-posts/
---

{% include page-intro.html %}

<main id="main" class="page-content" aria-label="Content">
  <div class="index inner">
    
    {% if site.posts.size > 0 %}
      <div>
        <header class="section-title">
          <h2>{{ site.data.theme.t.posts | default: 'Posts' }}{% if paginator.page > 1 %}{{ site.data.theme.t.page | default: 'Page' | prepend: ' - ' | append: ' ' }}{{ paginator.page }} {{ site.data.theme.t.of | default: 'of' }} {{ paginator.total_pages }}{% endif %}</h2>
        </header>

        {%- comment -%}
        The following division CSS class will fail if page.entries_layout is set.
        We only have post-card-list.  We will need to add more if we start using
        more layouts for the post-cards.
        {%- endcomment -%}
        <div class="post-card-{{ page.entries_layout | default: 'list' }}">
          {% if site.plugins contains 'jekyll-paginate' and page.paginate or site.gems contains 'jekyll-paginate' and page.paginate %}
            {% comment %}
              Add paginator.posts loop if jekyll-paginate plugin is enabled
              and page.paginate == true
            {% endcomment %}
            {% include posts-paginated.html %}
          {% else %}
            {% include posts-all.html %}
          {% endif %}
        </div>
      </div>    
    {% endif %}
    
  </div>
</main>
