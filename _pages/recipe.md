---
layout: page
title: recipe
permalink: /recipe/
description: A growing collection of your recipe that I cook.
nav: true
nav_order: 3
display_categories: [dessert, main, snack]
horizontal: false
---

<!-- pages/recipe.md -->
<div class="recipe">
{% if site.enable_recipe_categories and page.display_categories %}
  <!-- Display categorized recipe -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_recipe = site.recipe | where: "category", category %}
  {% assign sorted_recipe = categorized_recipe | sort: "importance" %}
  <!-- Generate cards for each recipe -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for recipe in sorted_recipe %}
      {% include recipe_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for recipe in sorted_recipe %}
      {% include recipe.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display recipe without categories -->

{% assign sorted_recipe = site.recipe | sort: "importance" %}

  <!-- Generate cards for each recipe -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for recipe in sorted_recipe %}
      {% include recipe_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for recipe in sorted_recipe %}
      {% include recipe.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
