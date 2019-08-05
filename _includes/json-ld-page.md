<script type="application/ld+json">
    {
        "@context": "http://schema.org",
        "@type": "{% if page.type %}{{ page.type }}{% elsif page.is_post %}BlogPosting{% else %}WebPage{% endif %}",
        {% if page.title %}"name": "{{ page.title }}",{% endif %}
        {% if page.description %}"description": "{{ page.description }}",{% endif %}
        {% if page.author or site.author %}"author": 
            {
                "@type": "Person",
                "name": "{% if page.author %}{{ page.author }}{% else %}{{ site.author }}{% endif %}"
            },{% endif %}
        {% if page.date %}"dateCreated": "{{ page.date }}",{% endif %}
        {% if page.breadcrumbs %}"breadcrumb":
            {
                "@type": "BreadcrumbList",
                "itemListElement": [{% for breadcrumb in page.breadcrumbs %}
                    {
                        "@type": "ListItem",
                        "position": {{ forloop.index }},
                        "item": {
                            "@type": "{% if breadcrumb.type %}{{ breadcrumb.type }}{% else %}WebPage{% endif %}",
                            "@id": "{{ site.url }}{{ site.baseurl }}{% if breadcrumb.url == 'page.url' %}{{ page.url }}{% else %}{{ breadcrumb.url }}{% endif %}",
                            "name": "{% if breadcrumb.title == 'page.title' %}{{ page.title }}{% else %}{{ breadcrumb.title }}{% endif %}"
                        }
                    }{% unless forloop.last %},{% endunless %}
                {% endfor %}]
            },{% endif %}
        "url": "{{ site.url }}{{ site.baseurl }}{{ page.url }}"
    }
</script>
