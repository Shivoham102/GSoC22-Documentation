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

Every entity needs the following in order for the export to work, and these were added as per need - 

- The `getTableRow()` and `getCidocCrm()` functions in the entity files to get the rows for flat data export and linked data export respectively.

- The data needs to be serialized in the controller, e.g. in the Abbreviations entity, it would look like-<br>

        $this->set('_serialize', 'abbreviations');

- In the `initialize()` function of the controller the linked data and flat data features of the ApiComponent are included to get the export working - <br>

        $this->loadComponent('Api', ['features' => ['LinkedData','TableExport']]);

- An element for displaying the export drop-down which can be found here - `app/cake/templates/element/entityExport.php`. Thr drop-down looks like this - INSERT IMAGE
This element is then displayed in the index page of all entities.