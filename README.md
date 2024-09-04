



biblio
================================================================================

Publish a bibliography online  
using Zotero bibliography manager  
and Hugo web content manager  
to write semantic HTML5 with schema.org metadata.


Work in Progress
--------------------------------------------------------------------------------

1. Input: Clean up my messy data
2. Output: Make a working example of a web page



Storing Bibliography in Zotero
===============================================================================


Item Type
--------------------------------------------------------------------------------

As far as I know, no major citation style, including humanities styles like MHRA, Chicago, and MLA, talk about special rules for citing these. Moreover, for referencing, and thus a reference manager the form of publication is typically more important than a genre. A Poem in the New Yorker, for example, is a magazine article; a poem in an anthology is a book section; a poem in a more academically oriented journal may be a journal article; a poem you find in an archive is a manuscript. I don't see how adding a new item type helps with this type of thing -- if anything it confuses it.


Fields
--------------------------------------------------------------------------------

When deciding how to cite your source, start by consulting the list of core elements. These are the general pieces of information that MLA suggests including in each Works Cited entry. In your citation, the elements should be listed in the following order:

  - Author.
  - Title of source.
  - Title of container,
  - Other contributors,
  - Version,
  - Number,
  - Publisher,
  - Publication date,
  - Location.


Each element should be followed by the corresponding punctuation mark shown above.

https://owl.purdue.edu/owl/research_and_citation/mla_style/mla_formatting_and_style_guide/mla_formatting_and_style_guide.html


How to Refactor to Page Bundles
--------------------------------------------------------------------------------

`refactor-pages-to-page-bundles`
Refactor all Markdown page files to page bundles (each page gets a portable, self contained folder with its assets)
https://github.com/HugoBlox/awesome-hugo


Lots of Zotero Resources
--------------------------------------------------------------------------------

Awesome Zotero
A reference to all awesome additional tweaks that make Zotero better.
https://github.com/MohamedElashri/awesome-zotero


Bibliography in Notion
--------------------------------------------------------------------------------

official github for the Notero plugin for Zotero
https://github.com/dvanoni/notero

how-to guide:
https://sciquest.netlify.app/posts/notion_literature/

example notion database:
https://dvanoni.notion.site/79b17005bc374209b0f373b1a3cde0ae?v=cbaca2dbd8044d468414609838c91da7



BibLaTeX Overview
===============================================================================

BibLaTeX offers a comprehensive and flexible set of entry types to accommodate a wide range of sources for bibliographies and citations. These entry types are more extensive and detailed compared to traditional BibTeX, allowing for better customization and accuracy in referencing.

### Strategies for Citing Arts and Humanities Works in BibLaTeX

1. **Adapting Existing Entry Types:**

    - **`@misc`:** This is the most flexible entry type and can be adapted for almost any source that doesn't fit neatly into other categories.
    - **`@unpublished` or `@manuscript`:** These can be used for works that are not formally published, such as live performances or artworks.
    - **`@online`:** Suitable for digital media works like videos, podcasts, or websites.
    - **`@audio`, `@video`, `@artwork`:** Some communities or individual users create custom entry types, though these are not officially supported by BibLaTeX.
2. **Using the `type` or `howpublished` Fields:**

    - The `type` field can be used to specify the type of work (e.g., "Painting," "Live Performance," "Video Installation").
    - The `howpublished` field can provide details about the medium (e.g., "Oil on canvas," "Sculpture," "Digital video").

    **Example:**

    ```
    bibtexCopy code

    `@misc{Kinnett2023Painting,
      author = {Dylan Kinnett},
      title = {Untitled Artwork},
      year = {2023},
      type = {Oil on canvas},
      howpublished = {Exhibited at the XYZ Gallery, New York, NY}
    }
    `

    ```

3. **Using the `note` or `abstract` Fields:**

    - These fields can be used to include additional information about the work, such as context, details about the performance, or descriptions of the medium.
4. **Extending BibLaTeX with Custom Styles:**

    - Some users create custom BibLaTeX styles or extend existing ones to better accommodate the needs of humanities and arts citation practices. This involves modifying the `.bst` file or using a LaTeX package that allows for more customization.
    - **Better BibTeX for Zotero** can be configured to support custom citation keys and fields, making it easier to manage non-traditional sources.
5. **Referencing Manuals and Guides:**

    - Scholars often consult citation manuals specific to their field, such as the *MLA Handbook* or *Chicago Manual of Style*, and then adapt BibLaTeX entries accordingly.
    - In cases where BibLaTeX does not natively support a citation format, these manuals can provide guidance on how to structure citations using the available fields.

### Example Adaptations for Various Works

  - **Live Performance:**

    ```
    bibtexCopy code

    `@misc{Kinnett2023LivePerformance,
      author = {Dylan Kinnett},
      title = {Performance Title},
      year = {2023},
      type = {Live Performance},
      venue = {XYZ Theater, Baltimore, MD},
      howpublished = {Part of the "Performance Art Series"},
      abstract = {Description of the performance, setlist, etc.}
    }
    `

    ```

  - **Physical Artwork:**

    ```
    bibtexCopy code

    `@misc{Kinnett2023Artwork,
      author = {Dylan Kinnett},
      title = {Artwork Title},
      year = {2023},
      type = {Sculpture},
      howpublished = {Bronze, 6 ft. x 3 ft., exhibited at ABC Gallery, New York, NY},
      abstract = {Description of the artwork, exhibition details, etc.}
    }
    `

    ```

  - **Media Work (Video/Audio):**

    ```
    bibtexCopy code

    `@online{Kinnett2023Video,
      author = {Dylan Kinnett},
      title = {Title of the Video},
      year = {2023},
      url = {http://example.com/video},
      type = {Digital Video},
      howpublished = {Published on Vimeo, part of XYZ series},
      abstract = {Description of the video content, duration, etc.}
    }
    `

    ```

### Conclusion

While BibLaTeX may not have dedicated entry types for all arts and humanities works, it is flexible enough to allow authors to adapt existing types to meet their needs. By using fields like `type`, `howpublished`, and `abstract`, along with custom styles and plugins, scholars can effectively manage and cite a wide range of creative works.

4o


Below is the complete list of standard entry types supported by BibLaTeX, along with brief descriptions for each:

---


**Standard Entry Types**
--------------------------------------------------------------------------------

### 1. `@article`

**Description:**
An article from a journal, magazine, newspaper, or other periodical publication.

**Fields:**
  - *Required:* `author`, `title`, `journal`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `editor`, `translator`, `annotator`, `commentator`, `journalsubtitle`, `issuetitle`, `issuesubtitle`, `language`, `origlanguage`, `series`, `volume`, `number`, `eid`, `issue`, `month`, `pages`, `version`, `note`, `issn`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 2. `@book`

**Description:**
A complete, published book.

**Fields:**
  - *Required:* `author`/`editor`, `title`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `maintitle`, `mainsubtitle`, `maintitleaddon`, `language`, `origlanguage`, `volume`, `part`, `edition`, `volumes`, `series`, `number`, `note`, `publisher`, `location`, `isbn`, `chapter`, `pages`, `pagetotal`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 3. `@mvbook`

**Description:**
A multi-volume **book**. Use this type for citing the entire work as a whole.

**Fields:**
Same as `@book` with additional handling for multiple volumes.

---

### 4. `@inbook`

**Description:**
A part of a book, which may be a chapter, section, or other subdivision that is titled and/or numbered.

**Fields:**
  - *Required:* `author`/`editor`, `title`, `booktitle`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `maintitle`, `mainsubtitle`, `maintitleaddon`, `booksubtitle`, `booktitleaddon`, `language`, `origlanguage`, `volume`, `part`, `edition`, `volumes`, `series`, `number`, `note`, `publisher`, `location`, `chapter`, `pages`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 5. `@bookinbook`

**Description:**
A part of a book which forms a self-contained unit and is also separately published as a book.

**Fields:**
Same as `@inbook`.

---

### 6. `@suppbook`

**Description:**
Supplemental material in a book.

**Fields:**
Same as `@inbook`.

---

### 7. `@booklet`

**Description:**
A printed and bound work without a named publisher or sponsoring institution.

**Fields:**
  - *Required:* `author`, `title`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `language`, `howpublished`, `type`, `note`, `location`, `chapter`, `pages`, `pagetotal`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 8. `@collection`

**Description:**
A collection of works (such as articles) published as a single book, where the works have no individual authors but the collection has an editor.

**Fields:**
  - *Required:* `editor`, `title`, `year`/`date`
  - *Optional:* Similar to `@book`

---

### 9. `@mvcollection`

**Description:**
A multi-volume **collection**. Use for citing the entire collection as a whole.

**Fields:**
Same as `@collection` with additional handling for multiple volumes.

---

### 10. `@incollection`

**Description:**
A contribution to a collection, which can be a chapter in an edited book.

**Fields:**
  - *Required:* `author`, `title`, `booktitle`, `year`/`date`
  - *Optional:* Similar to `@inbook`

---

### 11. `@suppcollection`

**Description:**
Supplemental material in a collection.

**Fields:**
Same as `@incollection`.

---

### 12. `@manual`

**Description:**
Technical or other documentation.

**Fields:**
  - *Required:* `title`
  - *Optional:* `author`, `editor`, `subtitle`, `titleaddon`, `language`, `edition`, `type`, `series`, `number`, `version`, `note`, `organization`, `publisher`, `location`, `month`, `year`/`date`, `isbn`, `chapter`, `pages`, `pagetotal`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 13. `@misc`

**Description:**
A fallback type for entries which do not fit into any other type.

**Fields:**
  - *Required:* `author`/`editor`, `title`, `year`/`date`
  - *Optional:* All optional fields from other types as applicable.

---

### 14. `@online`

**Description:**
An online resource.

**Fields:**
  - *Required:* `author`/`editor`, `title`, `year`/`date`, `url`
  - *Optional:* `subtitle`, `titleaddon`, `language`, `version`, `note`, `organization`, `month`, `urldate`, `addendum`, `pubstate`

---

### 15. `@patent`

**Description:**
A patent or patent request.

**Fields:**
  - *Required:* `author`, `title`, `number`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `type`, `version`, `location`, `note`, `month`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 16. `@periodical`

**Description:**
An entire issue of a periodical, such as a special issue.

**Fields:**
  - *Required:* `editor`, `title`, `year`/`date`
  - *Optional:* `subtitle`, `issuetitle`, `issuesubtitle`, `language`, `series`, `volume`, `number`, `issue`, `month`, `note`, `issn`, `publisher`, `location`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 17. `@suppperiodical`

**Description:**
Supplemental material in a periodical.

**Fields:**
Same as `@article`.

---

### 18. `@proceedings`

**Description:**
A conference proceedings as a whole.

**Fields:**
  - *Required:* `title`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `editor`, `eventtitle`, `eventdate`, `venue`, `language`, `volume`, `part`, `series`, `number`, `note`, `organization`, `publisher`, `location`, `month`, `isbn`, `chapter`, `pages`, `pagetotal`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 19. `@mvproceedings`

**Description:**
A multi-volume conference proceedings.

**Fields:**
Same as `@proceedings` with additional handling for multiple volumes.

---

### 20. `@inproceedings`

**Description:**
An article in a conference proceedings.

**Fields:**
  - *Required:* `author`, `title`, `booktitle`, `year`/`date`
  - *Optional:* Similar to `@incollection`

---

### 21. `@reference`

**Description:**
A work of reference, such as an encyclopedia or dictionary.

**Fields:**
Same as `@collection`.

---

### 22. `@mvreference`

**Description:**
A multi-volume work of reference.

**Fields:**
Same as `@reference` with additional handling for multiple volumes.

---

### 23. `@inreference`

**Description:**
An article in a work of reference.

**Fields:**
Same as `@incollection`.

---

### 24. `@report`

**Description:**
A technical report, white paper, or other report issued by an institution.

**Fields:**
  - *Required:* `author`, `title`, `type`, `institution`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `number`, `version`, `series`, `location`, `month`, `note`, `isbn`, `issn`, `chapter`, `pages`, `pagetotal`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 25. `@set`

**Description:**
A set of entries that are related and should be treated as a single reference.

**Fields:**
  - *Required:* `entryset`
  - *Optional:* All optional fields as applicable.

---

### 26. `@thesis`

**Description:**
A thesis or dissertation.

**Fields:**
  - *Required:* `author`, `title`, `type`, `institution`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `language`, `location`, `month`, `note`, `isbn`, `chapter`, `pages`, `pagetotal`, `addendum`, `pubstate`, `doi`, `eprint`, `eprintclass`, `eprinttype`, `url`, `urldate`

---

### 27. `@unpublished`

**Description:**
A work with an author and title, but not formally published.

**Fields:**
  - *Required:* `author`, `title`, `year`/`date`
  - *Optional:* `subtitle`, `titleaddon`, `language`, `howpublished`, `note`, `location`, `month`, `addendum`, `pubstate`, `url`, `urldate`

---


**Legacy Entry Types**
--------------------------------------------------------------------------------

BibLaTeX also supports legacy BibTeX entry types for compatibility purposes:

### 1. `@conference`

**Description:**
Treated as an alias for `@inproceedings`.

---

### 2. `@electronic`

**Description:**
Treated as an alias for `@online`.

---

### 3. `@mastersthesis`

**Description:**
Treated as an alias for `@thesis` with `type = {Master's thesis}`.

---

### 4. `@phdthesis`

**Description:**
Treated as an alias for `@thesis` with `type = {PhD thesis}`.

---

### 5. `@techreport`

**Description:**
Treated as an alias for `@report`.

---

### 6. `@www`

**Description:**
Treated as an alias for `@online`.

---


**Custom Entry Types**
--------------------------------------------------------------------------------

BibLaTeX allows the creation of custom entry types if needed. You can define your own types and corresponding fields to suit specific referencing requirements by modifying the BibLaTeX configuration.

---

**Note:**
  - The **required fields** are those necessary for the entry to be processed correctly.
  - **Optional fields** provide additional information and can improve the completeness and accuracy of the citation.
  - The availability and use of fields may also depend on the bibliography style you are using.

**References for Further Reading:**
  - For a detailed explanation of each field and type, refer to the official BibLaTeX documentation: [BibLaTeX Documentation](http://mirror.ox.ac.uk/sites/ctan.org/macros/latex/contrib/biblatex/doc/biblatex.pdf)
  - For guidance on choosing the correct entry type, consider the nature of the source material and consult any specific style guidelines relevant to your work.

**Example Usage:**
Here is how you might cite an online article:

```bibtex
@online{Smith2021,
  author = {John Smith},
  title = {Understanding Quantum Computing},
  year = {2021},
  url = {https://example.com/quantum-computing},
  urldate = {2021-06-15},
  note = {Accessed: 2021-06-15}
}
```

---



OLD README
================================================================================

HTML5 Bibliography with Schema.org Metadata


I wanted to publish a bibliography of my writings to the web. I wanted that page to have good, semantic markup, according to the schema.org standards and examples. While my bibliography manager, Zotero, has an excellent HTML export ability, the HTML wasn't exactly what I had in mind, so I rolled my own.


Ingredients
--------------------------------------------------------------------------------

  - Zotero bibliography manager
  - Jekyll static web generator
  - familiarity with [schema.org microdata](http://schema.org/docs/gs.html#microdata_why) and
  - familiarity with JSON and YAML


Procedure
--------------------------------------------------------------------------------

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


```liquid
<main>
  {% for publication in site.data.publications %}
  <article itemscope itemtype="http://schema.org/CreativeWork">
    <meta itemprop="author" content="{{ publication.author }}" />
    <a href="{{ publication.URL }}" itemprop="url">
      <cite itemprop="name">{{ publication.title }}.</cite>
    </a>
    {% if publication.genre %}
      <span itemprop="genre">{{ publication.genre }}</span>.
    {% endif %}
    {% if publication.event_place %}
      <span itemprop="contentLocation">
        {{ publication.event_place }}
      </span>.
    {% endif %}
    <date itemprop="datePublished">
      {% for item in publication.issued %}
        {{ item | join: '-' }}
      {% endfor %}
    </date>.
  </article>
  {% endfor %}
</main>```
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
