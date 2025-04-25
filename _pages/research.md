---
layout: archive
title: "Research Work"
permalink: /research/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% assign sorted_research = site.research | sort: 'date' | reverse %}
{% for post in sorted_research %}
<div class="research-item">
  <h3>
    <a href="{{ post.paper_link }}" target="_blank">{{ post.title }}</a>
  </h3>
  <p>
    Coauthors: 
    {% for coauthor in post.coauthors %}
      <a href="{{ coauthor.link }}" target="_blank">{{ coauthor.name }}</a>{% if forloop.last == false %}, {% endif %}
    {% endfor %}
  </p>
  <p><strong>Year:</strong> {{ post.date | date: "%Y" }}</p>
  <p><strong>Status:</strong> {{ post.status }}</p>
  <button class="toggle-abstract">+ Abstract</button>
  <div class="abstract hidden">
    <p>{{ post.excerpt }}</p>
  </div>
</div>
{% endfor %}

<script>
document.addEventListener('DOMContentLoaded', () => {
    const toggleButtons = document.querySelectorAll('.toggle-abstract');

    toggleButtons.forEach(button => {
        button.addEventListener('click', () => {
            const abstract = button.nextElementSibling;
            if (abstract.classList.contains('hidden')) {
                abstract.classList.remove('hidden');
                button.textContent = '- Abstract';
            } else {
                abstract.classList.add('hidden');
                button.textContent = '+ Abstract';
            }
        });
    });
});
</script>

<style>
.research-item {
    margin-bottom: 20px;
}

.research-item h3 {
    margin: 0;
}

.research-item p {
    margin: 5px 0;
}

.abstract {
    margin-top: 10px;
    padding: 10px;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
}

.hidden {
    display: none;
}

.toggle-abstract {
    margin-top: 5px;
    cursor: pointer;
    background-color: transparent;
    color: #007bff;
    border: 1px solid #007bff;
    padding: 5px 10px;
    border-radius: 3px;
}

.toggle-abstract:hover {
    background-color: #e6f2ff;
}
</style>
