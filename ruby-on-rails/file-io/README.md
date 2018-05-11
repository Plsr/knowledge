# File I/O

Things regarding the input and output in a rials application.

## Table of Contents
* [Importing CSV Files](#importing-csv-files)

## Importing CSV Files

Rails has a lot of support built on for handling CSV (both, in- and output),
have a look at the [CSV
Class](https://ruby-doc.org/stdlib-2.0.0/libdoc/csv/rdoc/CSV.html).

While importing CSV Files, the most memory-efficient method is to use
`CSV.foreach()`, which reads the file line per line (see [this
article](https://dalibornasevic.com/posts/68-processing-large-csv-files-with-ruby)
for more information about the performance of importing CSV files).
