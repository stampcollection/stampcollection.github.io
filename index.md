---
layout: default
title: My Stamp Collection
---

# My Stamp Collection

Select a letter:

{% assign countries = site.stamps | map: "country" | uniq | sort %}

{% assign current_letter = "" %}

{% for country in countries %}
  {% assign first_letter = country | slice: 0 | upcase %}
  
  {% if first_letter != current_letter %}
    {% assign current_letter = first_letter %}
    ## {{ first_letter }}
  {% endif %}
  
  - [{{ country }}](/countries/{{ country | downcase | replace: " ", "-" }}.html)
{% endfor %}
