---
title: Bulk Update
section: Dev and devops docs
category: Features Guide
audiences:
  - Developer
chips:
  - developer
authors:
  - Angal, Shivoham
---

## Bulk Update for Developers

- At times, there are a large number of artifacts that have common attributes and we need to group them by these and update them. But, this cannot be done in Filemaker because pulling the data for so many artifacts in relational form is tedious.

- This is where the Bulk Update functionality comes in. Bulk update will allow the user to update some of the attributes of the artifacts with the same values for all of them.

- For this the user can search the artifacts with the search functionality and click on `"Update Search Results Metadata"` at the bottom of the `"Advanced Features"` section on the search results page. The section looks like this - <br>
![Advanced Features Section](/cdli-docs/images/adv_features_section.png)

- On clicking this link, the user will be prompted with a modal to select the fields they want to update. The modal should look something like this - <br>
![Bulk Update Modal](/cdli-docs/images/bulk_update_modal.png)

- After selecting the fields, the user is redirected to the bulk update index. This index page is in the `BulkUpdate/index.php` file. Here users can fill in the values in the master form at the top. And upon clicking on save, the user is redirected to the artifact updates page to confirm the changes.

- The bulk update functionality uses the same logic as when uploading a csv file to the artifact updates form, and only a check is added to check whether the input is from the bulk upload form or the csv upload and treat the data accordingly. This check is added in the `add()` method of the `Controller/ArtifactsUpdatesController.php` file.