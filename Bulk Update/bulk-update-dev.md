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

- For this the user can search the artifacts with the search functionality and click on the `"Bulk Update"` button. Then they will be prompted with a modal to select the fields they want to update. The modal should look something like this - [INSERT IMAGE]

- After selecting the fields, the user is redirected to the bulk update index where they can fill in the values in the master form at the top. And upon clicking on save, the user is redirected to the artifact updates page to confirm the changes.

- The bulk update functionality uses the same logic as when uploading a csv file to the artifact updates form, and only a check is added to check whether the input is from the bulk upload form or the csv upload.