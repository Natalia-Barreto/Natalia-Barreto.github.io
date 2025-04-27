---
layout: archive
title: "Policy Work"
permalink: /policy/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% assign sorted_policy = site.policy | sort: 'date' | reverse %}
{% for post in sorted_policy %}
<div class="policy-item">
  <h3>{{ post.title }}</h3>
  <div style="display: flex; align-items: center;">
    <div style="flex: 1;">
      <p>
        Coauthors: 
        {% for coauthor in post.coauthors %}
          <a href="{{ coauthor.link }}" target="_blank">{{ coauthor.name }}</a>{% if forloop.last == false %}, {% endif %}
        {% endfor %}
      </p>
      <p><strong>Year:</strong> {{ post.date | date: "%Y" }}</p>
      <!-- <p><strong>Status:</strong> {{ post.status }}</p> -->
      <p>
        <strong>Link:</strong> 
        {% for link in post.link %}
          <a href="{{ link.url }}" target="_blank">{{ link.download }}</a>{% if forloop.last == false %}, {% endif %}
        {% endfor %}
      </p>
      <button class="toggle-abstract">+ Abstract</button>
      <div class="abstract hidden">
        <p>{{ post.excerpt }}</p>
      </div>
    </div>
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
.policy-item {
    margin-bottom: 20px;
}

.policy-item h3 {
    margin: 0;
}

.policy-item p {
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
