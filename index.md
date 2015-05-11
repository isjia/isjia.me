---
layout: page
---
{% include JB/setup %}
<div class="row">
    <div class="col-lg-8 col-lg-offset-2 col-md-10 col-md-offset-1">
        {% for post in site.posts limit 20 %}
        <div class="post-preview">
          <h1>{{ post.title }} {% if post.subtitle %}
            <span class="text-muted">
              {{ post.date | date_to_string }}
            </span>
          <br />
          <small>{{ post.subtitle}}</small>{% endif %}</h1>
          {% if post.bg-image %}
            <img src="/assets/posts/images/{{ post.bg-image }}" alt="">
          {% endif %}
          {% if post.content.size < 300 %}
              {{ post.content }}
          {% else %}
              <p>{{ post.content | split: '<!-- break -->' | first  }}</p>
              <a href="{{ BASE_PATH }}{{ post.url }}">
                <button class="btn btn-primary pull-right">
                    阅读全文 ...
                </button>
              </a>
          {% endif %}
          <div class="clearfix"></div>
        </div>
        <hr>
        {% endfor %}
    </div>
</div>