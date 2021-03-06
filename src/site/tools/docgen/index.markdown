---
layout: default
title: "docgen: The API Documentation Generator"
short-title: "docgen"
description: "A Dart tool that generates documentation and serves it to
dartdoc-viewer."
---

{% include toc.html %}
{% include breadcrumbs.html %}

# {{ page.title }} 

---
Use _docgen_ to generate, and serve,
the documentation for your Dart package.

## Basic usage {#basic-usage}

Docgen generates documentation from Dart code in the `lib` directory
and creates the output in JSON format.
When using the `--serve` option, docgen serves your files so you can
see them locally in a browser.
To deploy your documentation to the web,
host the viewer on your server, compiled to JavaScript,
along with your generated files.

### Generate documentation {#generate}

Here is a simple example of using docgen to generate docs
on the command line. The docs are generated from the source
code in the `lib` directory.

Run this command from the top-level directory of your Dart package,
after you have run `pub get` to get the dependencies:

{% prettify lang-sh %}
docgen .
{% endprettify %}

This command generates documentation, in the JSON
file format, and places it in a top-level directory named `docs`.
See [options](#options) for information on how to configure
this command.

### View docs locally {#view-locally}

Here is a simple example of using docgen to generate, and then serve,
the generated docs to the viewer.

{% prettify lang-sh %}
docgen --serve .
{% endprettify %}

After generating the documentation,
this command puts `dartdoc-viewer` in a top-level directory
(if not already present), and starts it up.
The generated docs can now be viewed in your browser at
`localhost:8080`.

### Deploy docs {#deploy}

To deploy your documentation to the web, do the following:

* Host dartdoc-viewer on your server, compiled to JavaScript.
* Host the generated files, which must be in a directory
  named `docs` under the main URL.

<aside class="alert alert-warning" markdown="1">
Docgen replaces the _dartdoc_ tool, which was removed in revision
[32387](https://code.google.com/p/dart/source/detail?r=32387).
</aside>

## Options {#options}

<aside class="alert alert-info" markdown="1">
**Note:**
To run docgen from the command line, you might want to
[add the SDK's bin directory to your system path](/tools/pub/installing.html).
</aside>

Common command-line options for docgen include:

`--compile`
: Clone the dartdoc-viewer locally, if needed, and compile with dart2js.
  Use this version when you [deploy](#deploy) your documentation.

`-h` or `--help`
: Display help.

`--out=<directory>`
: Generate the output to `<directory>`.
  If not specified, the default is `docs`.
  
`--package-root`
: Specifiy the package root of the library.

`--serve`
: After generating the docs, start the dartdoc-viewer.
  You can view the documentation in the browser at `localhost:8080`.

`-v` or `--verbose`
: Provide logging information.

Some other handy options include:

`--include-private`
: Include private declarations, which are specified with a leading
  underscore (`_`). For more information on private
  identifiers, see
  [Important Concepts](/docs/dart-up-and-running/contents/ch02.html#ch02-concepts)
  in the [Dart language tour](/docs/dart-up-and-running/contents/ch02.html).

`--introduction=<markdown file>`
: Use the specified file as the introduction page for the generated
  documentation.

`--no-docs`
: Do not generate new documentation. If you have previously
  generated your docs, use this option in conjunction with
  `--compile` or `--serve` for faster start-up.

`--no-include-dependent-packages`
: Do not generate the documentation for dependent packages.

`--start-page=<package>`
: Use the documentation for the specified package as the starting page.

`--exclude-lib=<library>`
: Exclude the specified library from the generated documentation.

Docgen includes a number of options that apply only to generating
the Dart SDK documentation. Those are not documented here, but
you can obtain a list by using the `docgen -h` command.

