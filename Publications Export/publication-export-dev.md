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

- The bibliographical data can be downloaded from the `"Cite this Publication"` section at the bottom of the page. But, on the index page this is included in the drop-down. The single view drop-down can be found in the `app/cake/templates/Publications/view.php` file.

- The only exception here is that on the index page, all the results cannot be downloaded at the same time as the data is very large. The user can only download data for the publications on the current page.

- To download more data, the user can narrow down the results by searching in the form.

- Now, upon searching if the number of results is less than or equal to 1000 the user can download data for all the results from the drop-down which looks like the one mentioned above.

- But, if the results are more than 1000, the drop-down is changed into a button and on clicking this a modal like this is shown: <br>
![Github link modal](/cdli-docs/images/publications-modal.png)

- The modal gives the link of the github data repository to the user so that they can download more data from there.

- For the index-page drop-down, the element in `app/cake/templates/element/entityExport.php` was re-used and modified to show the Bibliography export options for the publications page. It was also modified so as to allow export of data according to the number of results as mentioned above.
