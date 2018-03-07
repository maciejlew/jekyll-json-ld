{% if page.reviews %}
{% for r in page.reviews %}
<script type="application/ld+json">
    {
        "@context": "http://schema.org",
        "@type": "Review",
        "itemReviewed":
        {
            "@type": "{{ r.type }}",
            "name": "{{ r.name }}",
            {% if r.type == 'Book' %}"isbn": "{{ r.isbn }}",
            "author": 
            {
                "@type": "Person",
                "name": "{{ r.author }}",
                "sameAs": "{{ r.author_url }}"
            },{% endif %}
            "url": "{{ r.url }}"
        },
        "reviewBody": "{{ r.content }}",
        "reviewRating":
        {
            "@type": "Rating",
            "ratingValue": "{{ r.rating }}"
        },
        {% if page.author or site.author %}"author": 
        {
            "@type": "Person",
            "name": "{% if page.author %}{{ page.author }}{% else %}{{ site.author }}{% endif %}",
            "sameAs": "{{ site.url }}"
        },{% endif %}
        {% if page.date %}"datePublished": "{{ page.date }}",{% endif %}
        {% if site.name %}"publisher": "{{ site.name }}",{% endif %}
        "description": "{{ r.description }}",
        "url": "{{ site.url }}{{ page.url }}"
    }
</script>
{% endfor %}
{% endif %}
