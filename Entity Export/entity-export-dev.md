---
title: Entity Export for Developers
section: Dev and devops docs
category: Features Guide
audiences:
  - Developer
chips:
  - developer
authors:
  - Angal, Shivoham
---

## Entity Export for Developers

- The entity export drop-down allows for a user to export all the rows of an entity in any of the following formats -
  - CSV
  - TSV
  - TXT
  - TTL
  - RDF-JSON
  - JSON

- CSV, TSV and TXT are flat data formats and need the `getTableRow()` function to work whereas, TTL and RDF-JSON are linked data formats and need the `getCicocCrm()` function to work and JSON is an expanded data format. . These functions need to be included in any entity that needs the export functionality for the particular data formats.

- The linked data and flat data features of the ApiComponent are also included in the controllers like so- <br>

        $this->loadComponent('Api', ['features' => ['LinkedData','TableExport']]);

- The element made for displaying the export drop-down can be found here - `app/cake/templates/element/entityExport.php`. This element is dispalyed on all entity index pages. For example, the drop-down on the Abbreviations entity index page would look like this - <br>
![abbreviations drop-down](entity_dd_sample.png)
