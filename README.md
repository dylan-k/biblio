# biblio
HTML5 Bibliography with Schema.org Metadata


I wanted to publish a bibliography of my writings to the web. I wanted that page to have good, semantic markup, according to the schema.org standards and examples. While my bibliography manager, Zotero, has an excellent HTML export ability, the HTML wasn't exactly what I had in mind, so I rolled my own.

## Ingredients

- Zotero bibliography manager
- Jekyll static web generator
- familiarity with [schema.org microdata](http://schema.org/docs/gs.html#microdata_why) and 
- familiarity with JSON and YAML

## Procedure

### Step 1: Create a bibliography

Use Zotero, or whatever you like to create a bibliography. It shouldn't really matter what you use, so long as you can do...

### Step 2: Create a YAML version of the bibliography

I would prefer to say "export bibliography to YAML" except for two things. First, YAML and JSON are essentially the same thing and second, it's easy to convert from the JSON that Zotero provides into YAML with things like jsontoyaml.com

so do this:
- export JSON bibliography from Zotero
- convert JSON into YAML
- check your YAML with a validator just to be sure it's good.
- put your YAML in a file like biblios.yml in the _data directory (see also: http://www.madhur.co.in/blog/2013/11/05/makingmostdatadirectory.html)

### Step 3: Create a Jekyll Template for Your Bibliography

Duplicate Jekyll's built-in "default.html" file in the _layouts directory. Name it something like biblio.html instead. 

Then replace the line `{{ content }}` in the file you just created. Replace it with something like:
```
        <article>
          {% for biblio in site.data.biblios %}
            <p itemscope itemtype="http://schema.org/CreativeWork">
              <meta itemprop="author" content="{{ biblio.author }}" /> 
              <a href="{{ biblio.URL }}" itemprop="url">
                <cite itemprop="name">{{ biblio.title }}</cite> 
              </a>.
              {% if biblio.genre %}
                <span itemprop="genre">{{ biblio.genre }}</span>. 
              {% endif %}
              {% if biblio.event-place %}
                <span itemprop="contentLocation">{{ biblio.event-place }}</span>. 
              {% endif %}
              <date itemprop="datePublished"> {% for item in biblio.issued %} {{  item[1] item[2] item[3] | join: '-' | append: '.' }} {% endfor %}</date>
            </p>
          {% endfor %}
        </article>
```

note: I wrote the above to configure the output according to my own needs, but yours may vary. You might want to tinker with the markup there, but there should be enough in this example to get you started. 

Here are some resources that I found useful when learning how to write this:

- https://github.com/shopify/liquid/wiki/liquid-for-designers
- http://docs.shopify.com/themes/liquid-documentation/basics
- http://stackoverflow.com/questions/17466362/how-to-get-sub-items-from-an-array-in-liquid


Then, edit the index.html file. You want the template to be the one you just made, so change the top of the file so that it reads like so:

```
---
layout: biblio
---
```

### Step 4: Bob's Your Uncle

from the command line, change to the directory where you've installed Jekyll and made all the edits above. Then do ``jekyll serve`` and if everything went well you should see a nicely formatted HTML bibliography based on the YAML data you started with.

You can test the HTML that was generated with [Google's Structured Data Testing Tool](https://developers.google.com/structured-data/testing-tool/) to see how it came out.

Once you're happy with the HTML, you can publish it wherever you like: by adding it to an existing web page, entering it into a WordPress entry, etc.

