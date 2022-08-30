---
title: Publications Export
section: Dev and devops docs
category: Features Guide
audiences:
  - Developer
chips:
  - developer
authors:
  - Angal, Shivoham
---

## Publications Export for Developers

- Just like the entity export drop-down, the drop-down for publications also allows the user to export the data in following formats with two more formats for bibliography -
  - CSV
  - TSV
  - TXT
  - TTL
  - RDF-JSON
  - JSON
  - BibTex
  - RIS

- For publications, this drop-down is also on the publication single view page. The drop-down looks like this - <br>
![publication drop-down](/cdli-docs/images/publication-dd.png)

- The bibliographical data can also be downloaded from the `"Cite this Publication"` section at the bottom of the page. The single view drop-down can be found in the `app/cake/templates/Publications/view.php` file.

- The only exception here is the index page drop-down. It has two columns `"Download current page"` and `"Download all results"`. This is done to handle the fact that in most cases the user will not be able to download all the results as the data would be too large.

- To download more data, the user can narrow down the results by searching in the form.

- Now, upon searching if the number of results is less than or equal to 1000 the user can download data from both the columns of the drop=down which looks like this - <br>
![publications index drop-down](/cdli-docs/images/publications-dd-1.png)

- But, if the results are more than 1000, the `"Download all results"` column is changed and the drop-down looks like this - <br>
![publications drop-down with GitHub link](/cdli-docs/images/publications-dd-2.png)

- The column now shows a link to the GitHub data repository from where the users can download more data.

- For the index-page drop-down, the element in `app/cake/templates/element/entityExport.php` was re-used and modified to show the two columns along with the publications index specific Bibliography export options.
