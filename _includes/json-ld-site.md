{% assign site_modified = site.date %}
{% if site.posts %}
    {% for post in site.posts %}
        {% if post.date %}
            {% assign site_modified = post.date | date: "%Y-%m-%d" %}
            {% break %}
        {% endif %}
    {% endfor %}
{% endif %}
{% if site.pages %}
    {% for page in site.pages %}
        {% if page.date and page.date > site_modified %}
            {% assign site_modified = page.date | date: "%Y-%m-%d" %}
        {% endif %}
    {% endfor %}
{% endif %}
<script type="application/ld+json">
    {
        "@context": "http://schema.org",
        "@type": "WebSite",
        {% if site.name %}"name": "{{ site.name }}",{% endif %}
        {% if site.description %}"description": "{{ site.description }}",{% endif %}
        {% if site.url %}"url": "{{ site.url }}",{% endif %}
        {% if site.author %}"author": 
            {
                "@type": "Person",
                "name": "{{ site.author }}"
            },{% endif %}
        {% if site.date %}"dateCreated": "{{ site.date }}",{% endif %}
        "dateModified": "{{ site_modified }}"
    }
</script>
