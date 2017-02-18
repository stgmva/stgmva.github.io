---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: header_unsplash_12.jpg
widget1:
  title: "Blog & Portfolio"
  url: 'http://phlow.github.io/feeling-responsive/blog/'
  image: widget-1-302x182.jpg
  text: 'Every good portfolio website has a blog with fresh news, thoughts and develop&shy;ments of your activities. <em>Feeling Responsive</em> offers you a fully functional blog with an archive page to give readers a quick overview of all your posts.'
widget2:
  title: "Why use this theme?"
  url: 'http://phlow.github.io/feeling-responsive/info/'
  text: '<em>Feeling Responsive</em> is heavily customizable.<br/>1. Language-Support :)<br/>2. Optimized for speed and it&#39;s responsive.<br/>3. Built on <a href="http://foundation.zurb.com/">Foundation Framework</a>.<br/>4. Seven different Headers.<br/>5. Customizable navigation, footer,...'
  video: '<a href="#" data-reveal-id="videoModal"><img src="http://phlow.github.io/feeling-responsive/images/start-video-feeling-responsive-302x182.jpg" width="302" height="182" alt=""/></a>'
widget3:
  title: "Download Theme"
  url: 'https://github.com/Phlow/feeling-responsive'
  image: widget-github-303x182.jpg
  text: '<em>Feeling Responsive</em> is free and licensed under a MIT License. Make it your own and start building. Grab the <a href="https://github.com/Phlow/feeling-responsive/tree/bare-bones-version">Bare-Bones-Version</a> for a fresh start or learn how to use it with the <a href="https://github.com/Phlow/feeling-responsive/tree/gh-pages">education-version</a> with sample posts and images. Then tell me via Twitter <a href="http://twitter.com/phlow">@phlow</a>.'
#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
callforaction:
  url: https://tinyletter.com/feeling-responsive
  text: Inform me about new updates and features ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

headpasdf

<div class="medium-8 medium-centered columns">

{% for post in site.posts limit:2 %}

        {% if post.video %}
        <div{% if post.embed_height %} style="padding-bottom: {{ post.embed_height }}"{% endif %} class="flex-video">
        <iframe width="1280" height="720" src="{% if post.video contains 'youtu' %}https://www.youtube.com/embed/{{ post.video | remove: "https://www.youtube.com/watch?v=" | remove: "https://youtu.be/" }}{% elsif post.video contains 'vimeo.com' %}https://player.vimeo.com/video/{{ post.video | remove: "https://vimeo.com/" }}{% else %}{{ post.video }}{% endif %}{{ post.embed }}" frameborder="0" allowfullscreen></iframe>
        </div>
        {% endif %}


        {% if post.embed %}
        <div{% if post.embed_height %} style="padding-bottom: {{ post.embed_height }}"{% endif %} class="flex-video">
        {{ post.embed }}
        </div>
        {% endif %}


        {% if post.video or post.embed %}
        {% elsif post.image %}
        <figure>
            <a href="{{ post.url | absolute_url }}" title="{{ post.title | escape_once }}"><img src="{{ "/images/" | absolute_url }}{{ post.image }}" alt="{{ post.title | escape_once }}"></a>

            {% if post.caption_url and post.caption %}
            <figcaption>
                <a href="{{ post.caption_url }}">{{ post.caption }}</a>
            </figcaption>
            {% elsif post.caption %}
            <figcaption>
                {{ post.caption }}
            </figcaption>
            {% endif %}
        </figure>
        {% endif %}


        {% if post.link %}
            <p class="subheadline">{{ post.subheadline }} Link</p>
            <h1><a href="{{ post.link }}" target="_blank">{{ post.title }}</a></h1>
            <p class="teaser">
                {{ post.excerpt  | replace: '<p>', '' | replace: '</p>', ''}}
                <a href="{{ post.link }}">Visit Link ›</a>
            </p>
        {% elsif post.quote %}
            {% if post.subheadline %}<p class="subheadline">{{ post.subheadline }}</p>{% endif %}
            {% if post.quote_url %}
                <a href="{{ post.quote_url | absolute_url }}" target="_blank"><blockquote>{{ post.quote }}</blockquote></a>
            {% else %}
                <blockquote>{{ post.quote }}</blockquote>
            {% endif %}
        {% else %}
            {% if post.subheadline %}<p class="subheadline">{{ post.subheadline }}</p>{% endif %}
            <h1><a href="{{ post.url | absolute_url }}">{{ post.title }}</a></h1>
            <p class="teaser">
                {{ post.excerpt  | replace: '<p>', '' | replace: '</p>', ''}}
                <a href="{{ post.url | absolute_url }}">{{ site.data.ui[site.lang].read_more }}</a>
            </p>
        {% endif %}

    <div class="tem2 bem2">&nbsp;</div>
{% endfor %}
</div>


{% if paginator.total_pages > 1 %}
<ul class="pager main-pager">
  {% if paginator.previous_page %}
  <li class="previous">
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&larr; Newer Posts</a>
  </li>
  {% endif %}
  {% if paginator.next_page %}
  <li class="next">
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Older Posts &rarr;</a>
  </li>
  {% endif %}
</ul>
{% endif %}
