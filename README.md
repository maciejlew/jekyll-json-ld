# jekyll-json-ld

Copy content from **_includes** to yours project **_includes** directory.

## site json-ld snippet

To add site json-ld include **_includes/json-ld-site.md** to your HTML layout body section.

You can specify site properties in project **_config.yml** file.

Supported site properties:

* date - site creation date
* name - site name
* description - site description
* url - site url
* author - site author name

## page/post json-ld snippet

To add page json-ld include **_includes/json-ld-page.md** to your HTML layout body section.

You can specify site properties in page/post front matter section.

Supported page/post properties:

* type - page/post type, [see schema.org WebPage and more specific types][1]
* title - page/post title
* description - page/post description
* author - page/post author name
* date - page/post creation date
* breadcrumbs - path to this page/post, see this README *breadcrumbs* section.

### breadcrumbs

Path to page/post can be described with array of breadcrumbs.

Supported breadcrumb properties:

* url - relative URL to page/post
* title - page/post title
* type - page/post type, [see schema.org WebPage and more specific types][1]

#### examples:

Common blog post:

```
breadcrumbs:
  - url: /
    title: "Your Site Title"
    type: AboutPage
  - url: /blog/
    title: "Blog"
    type: CollectionPage
  - url: page.url
    title: page.title
    type: BlogPosting
```

About author page:

```
breadcrumbs:
  - url: /
    title: "Your Site Title"
    type: AboutPage
  - url: page.url
    title: page.title
    type: ProfilePage
```

## all-in-one json-ld

To add all json-ld snippets to your page just include **_includes/json-ld.md** to your HTML layout body section.

[1]: http://schema.org/WebPage
