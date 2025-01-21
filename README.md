



biblio
================================================================================

This project is very much a **work in progress**.

goals:
  - manage bibliographic data / citations in a citation manager
  - learn to cite "unusual" sources like performance art, digital media, etc.
  - efficient workflow for publishing to the web, using citation manger data

I've experimeted toward these goals variously. My current solution seems to be:
  - manage a `.bib` file using JabRef
  - convert the .bib file to YAML (or export to [.cff](https://citation-file-format.github.io/))
  - hugo CMS can parse the data into web content

Along the way, I experimented with Jekyll, Zotero, and even Notion.



Managing Bibliography Data with a Citaion Manager
===============================================================================

Zotero and JabRef are both free and popular applications for keeping track of a bibliography/citations.

I'm starting to prefer JabRef but they're both easy enough to get started with. I prefer JabRef because it stores my data as a `.bib` file (see below), which is much easier to work with in many other contexts.

[Getting started with JabRef](https://docs.jabref.org/getting-started)
: JabRef is open source software to manage references and the full text of papers. The native file
format used by JabRef is BibTeX, the standard LaTeX bibliography format. [A guide](https://www.mcgill.ca/library/files/library/jabref_guide_2016.pdf).

[Awesome Zotero](https://github.com/MohamedElashri/awesome-zotero)
: A reference to all awesome additional tweaks that make Zotero better.



Storing Bibliography Data in BibLaTex Database Files
===============================================================================

A BibLaTex database file (`.bib` file) is a plain text file [format](https://www.bibtex.com/g/bibtex-format/) used to store bibliographic information for references, such as books, articles, and other sources. It follows a structured format where each entry is assigned a unique identifier and contains fields like `author`, `title`, `year`, and more.

When used with a citation manager application or an authoring environment, the `.bib` file provides a versatile and efficient way to manage references for documents and to quickly present those references in various formats.

Example entry:

```bibtex
@book{Doe2023Example,
  author = "Jane Doe",
  title = "Introduction to Example Studies",
  year = 2023
}
```

  - `@book`: This is the **entry type**. Specifies that this entry is a book. Other entry types are described below.

  - `Doe2023Example`: This is the **citation key**. It _uniquely identifies_ the entry in the .bib file and is used when citing the source. Citation keys should be concise, descriptive, and _unique_.

  - `author = "Jane Doe",`: This is the **author** field. Specifies the author(s) of the book. If there are multiple authors, separate them with and (e.g., `Jane Doe and John Smith`).

  - `title = "Introduction to Example Studies"`: This is the **title** field. Specifies the title of the book. Titles should be in title case, and special characters should be enclosed in curly braces to preserve formatting.

  - `year = 2023`: This is the **year** field. It specifies the publication year of the book. This field is required unless the date field is used.

  - `date = "2023-01-21"` (alternative to year): This is the **date** field. It specifies the publication date in ISO format (e.g., "2023-01-21") and allows for more precision if needed.

This is just a [minimal working example](https://stackoverflow.com/help/minimal-reproducible-example). There's a lot more you can do, by mnixing and matching different types and fields.


BibLaTeX Entry Fields
-------------------------------------------------------------------------------

Many [other fields](https://www.bibtex.com/format/fields/) are available.

The **required fields** for each type are those necessary for the entry to be processed correctly. **Optional fields** provide additional information and can improve the completeness and accuracy of the citation. The availability and use of fields may also depend on the bibliography style you are using.


BibLaTeX Entry Types
-------------------------------------------------------------------------------

When using BibLaTeX to manage bibliographies, each reference source is assigned a `type`. Below is an overview of the "regular entry types" supported by the default BibLaTeX data model. While "non-standard types" can also be used, some environments may treat them as the `@misc` type, which can lead to inconsistent results. To ensure consistency, choose one of the regular entry types. Consider the nature of each source and select the type that most closely matches it.

  - [List of BibTeX entry types [with examples]](https://www.bibtex.com/e/entry-types/)
  - [BibLaTex Cheat Sheet](https://tug.ctan.org/info/biblatex-cheatsheet/biblatex-cheatsheet.pdf)
  - [Page 7 of biblatex documentation](https://mirrors.ibiblio.org/pub/mirrors/CTAN/macros/latex/contrib/biblatex/doc/biblatex.pdf#page=7)


Below is the complete list of standard entry types supported by BibLaTeX, along with brief descriptions for each:

Material from journals, magazines & newspapers:

  - `@article` journal, magazine or newspaper article
  - `@periodical` whole issue of a periodical
  - `@suppperiodical` supplemental material in periodical

Material from single-authored or co-authored books:

  - `@inbook` book part with own title
  - `@suppbook` supplemental material in book
  - `@bookinbook` originally published as standalone book
  - `@book` single-volume book by author(s) of whole
  - `@mvbook` multi-volume book

Material from edited anthologies:
  - `@incollection` contribution to anthology
  - `@suppcollection` supplemental material in anthology
  - `@collection` single-volume edited anthology
  - `@mvcollection` multi-volume collection

Material from conference proceedings:

  - `@inproceedings` article in conference proceedings
  - `@proceedings` single-volume conference proceedings
  - `@mvproceedings` multi-volume conference proceedings

Material from works of reference:

  - `@inreference` article in a reference work
  - `@reference` single-volume work of reference
  - `@mvreference` multi-volume reference work

Material from technical & institutional publications:

  - `@manual` technical or other documentation
  - `@report` institutional report or white paper
  - `@patent` patent or patent request
  - `@thesis` work completed to fulfil degree requirement

Material from online, informal & other sources:

  - `@online` inherently online source
  - `@booklet` informally published book
  - `@unpublished` work not formally published
  - `@misc` last resort (check manual first!)

Other types, variously supported:

  - `@artwork`
  - `@audio`
  - `@bibnote`
  - `@commentary`
  - `@image`
  - `@jurisdiction`
  - `@legislation`
  - `@legal`
  - `@letter`
  - `@movie`
  - `@music`
  - `@performance`
  - `@review`
  - `@standard`
  - `@video`


Strategies for Citing Arts and Humanities Works in BibLaTeX
--------------------------------------------------------------------------------

> As far as I know, no major citation style, including humanities styles like MHRA, Chicago, and MLA, talk about special rules for citing these. Moreover, for referencing, and thus a reference manager the form of publication is typically more important than a genre. A Poem in the New Yorker, for example, is a magazine article; a poem in an anthology is a book section; a poem in a more academically oriented journal may be a journal article; a poem you find in an archive is a manuscript. I don't see how adding a new item type helps with this type of thing -- if anything it confuses it.

-- [Short Story as Item Type](https://forums.zotero.org/discussion/69097/short-story-as-item-type)


The selection of BibLaTeX "regular" types and fields shows some preference for _printed_ or _physical_ works, as these are most often referenced in a bibliography. That doesn't mean you cannot cite a performance, conceptual artwork or a mixed-media VR experience.

Below are strategies and examples for effectively citing diverse creative works:


### Adapt Entry Types

  - `@misc`: A versatile entry type for sources that don't fit standard categories.
  - `@unpublished`: For works not formally published, such as live performances or artworks.
  - `@online`: Best for digital media like videos, podcasts, or websites.
  - Custom Types: You can define unofficial types, though support may vary across tools. For example [the JabRef citation manager has settings for creating custom types](https://docs.jabref.org/setup/customentrytypes).


### Adapt Data Fields

  - `type`: Specify the nature of the work (e.g., "Painting," "Live Performance").
  - `howpublished`: Provide details about the medium or venue (e.g., "Oil on canvas," "Exhibited at XYZ Gallery").
  - `note` or `abstract`: Add contextual details, performance descriptions, or medium specifics.



Managing Bibliography Data with Notion
===============================================================================

Notion is a tool for building databases, and a bibliography is essentially a database. You can even integrate a Notion database with a citation manager like Zotero.

official github for the Notero plugin for Zotero
https://github.com/dvanoni/notero

how-to guide:
https://sciquest.netlify.app/posts/notion_literature/

example notion database:
https://dvanoni.notion.site/79b17005bc374209b0f373b1a3cde0ae?v=cbaca2dbd8044d468414609838c91da7



Presenting Bibliography Data with Hugo
===============================================================================

Hugo can read from data and display it on a website. A bibliography is data. Why not combine the two?

references:

  - [Create Bibliographies in Hugo with a shortcode](https://lucidmanager.org/productivity/hugo-bibliography/)
  - [Convert bibtex file to YAML with pandoc](https://kevcaz.insileco.io/notes/2021/09/2021-09-02_convert_bibtex_file/)
  - [Hugo Data sources](https://gohugo.io/content-management/data-sources/)


From JabRef / BibLaTex
--------------------------------------------------------------------------------

A very standard way to store bibliographic data is within a .bib file. Many publishers rely on this format, and it's easy to keep under version control.

Hugo, however, cannot read from this format. It can read from YAML though. A simple fix is to convert your `.bib` file to YAML, using `pandoc`

```bash
pandoc "input file.bib" -s -f biblatex -t markdown > "output file.yaml"
```

Once you have YAML data, you can use it as a [Hugo data source](https://gohugo.io/content-management/data-sources/).


From Zotero / JSON
--------------------------------------------------------------------------------

Hugo can read your Zotero data via the Zotero API. This way, you don't have to manage any special files in your hugo project, and your bibliography is up-to-date with Zotero every time you rebuild your hugo site. It's a nice way to go, if you use Zotero.

Here's a basic example of a hugo template that can do this. Note the need for the zoero API key, and `<USERID>` which you shoudl store in a hugo config file.

```html
  <main id="zotero_bibliography" class="mt-100">
    <h1>Bibliography</h1>
    {{ $data := dict }}
    {{ $zoteroKey := .Site.Params.zotero_api_key }}
    {{ $url := printf "https://api.zotero.org/users/<USERID>/publications/items/top?direction=asc&format=json&sort=title&key=%s" $zoteroKey }}
    {{ with resources.GetRemote $url }}
    {{ with .Err }}
    <p>Bibliography data is currently unavailable.</p>
    {{ else }}
    {{ $data = .Content | transform.Unmarshal }}
    {{ end }}
    {{ else }}
    <p>Unable to get remote resource.</p>
    {{ end }}

    {{ if $data }}
    <!-- Normalize dates -->
    {{ $normalizedData := slice }}
    {{ range $data }}
    {{ $date := .data.date }}
    {{ if eq (len $date) 4 }}
    <!-- Handle year-only date (e.g., "1998") -->
    {{ $date = printf "%s-01-01" $date }}
    {{ end }}
    {{ $normalizedData = $normalizedData | append (dict "item" . "normalizedDate" $date) }}
    {{ end }}

    <!-- Sort by normalized date in descending order -->
    {{ $sortedData := sort $normalizedData "normalizedDate" "desc" }}

    <!-- Render the sorted data -->
    {{ range $index, $entry := $sortedData }}
    {{ $entry := .item }}
    <article class="biblio-item">
      <p>
        <!-- Author -->
        <span class="author">
          {{ range $entry.data.creators }}
          {{ if eq .creatorType "author" }}
          {{ .lastName }}, {{ .firstName }}
          {{ break }}
          {{ end }}
          {{ end }}
        </span>

        <!-- Title with link to source -->
        <span class="title">
          {{ if $entry.data.url }}
          <cite><a href="{{ $entry.data.url }}">{{ $entry.data.title }}</a></cite>.
          {{ else }}
          <cite>{{ $entry.data.title }}</cite>.
          {{ end }}
        </span>

        <!-- Title of container -->
        {{ if $entry.data.publicationTitle }}
        <span class="container-title">
          <cite>{{ $entry.data.publicationTitle }}</cite>,
        </span>
        {{ end }}

        <!-- Other contributors -->
        {{ $contributors := slice }}
        {{ range $entry.data.creators }}
        {{ if eq .creatorType "contributor" }}with
        {{ $contributors = $contributors | append (printf "%s %s" .firstName .lastName) }}
        {{ end }}
        {{ end }}
        {{ if $contributors }}
        <span class="contributors">
          with {{ delimit $contributors ", " }}.
        </span>
        {{ end }}

        <!-- Number -->
        {{ if $entry.data.volume }}
        <span class="volume">vol. {{ $entry.data.volume }}, </span>
        {{ end }}
        {{ if $entry.data.issue }}
        <span class="issue">no. {{ $entry.data.issue }}, </span>
        {{ end }}

        <!-- Publisher -->
        {{ if $entry.data.publisher }}
        <span class="publisher">{{ $entry.data.publisher }}, </span>
        {{ end }}

        <!-- Place -->
        {{ if $entry.data.place }}
        <span class="place">{{ $entry.data.place }}, </span>
        {{ end }}


        <!-- Publication date -->
        {{ if $entry.data.date }}
        <span class="date">{{ substr $entry.data.date 0 4 }}.</span>
        {{ end }}

        <!-- Location -->
        {{ if $entry.data.pages }}
        <span class="pages">pp. {{ $entry.data.pages }}, </span>
        {{ end }}
      </p>
    </article>
    {{ end }}
    {{ end }}
  </main>
```



Presenting Bibliography Data with Jekyll
================================================================================

Using Jekyll static CMS, you can create an HTML5 Bibliography with Schema.org Metadata


  - Step 1: Create a bibliography  
  Use Zotero, or whatever you like to create a bibliography. It shouldn't really matter what you use, so long as you can do...

  - Step 2: Create a JSON or YAML file that contains the bibliography
  - 
Most citation managers can export to `json`, and increasingly to `cff` a newer [YAML-compatible file format for citations](https://citation-file-format.github.io/). You can also convert  e.g. jsontoyaml.com

put your YAML in a file like biblios.yml in the _data directory (see also: http://www.madhur.co.in/blog/2013/11/05/makingmostdatadirectory.html)

  - Step 3: Create a Jekyll Template for Your Bibliography

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
