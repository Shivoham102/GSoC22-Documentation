```
title: Retired Artifacts for Editors
section: User guides
category: Features Guide
audiences:
  - Content contributor
chips:
  - editor
authors:
  - Angal, Shivoham
```
<h2>Retired Artifacts for Editors</h2>

* First, you will need to login with your credentials so that you have proper access.

* To retire or un-retired an artifacts you will need to visit the artifact edit form. This can be achieved in three ways - 
    * You can search the artifact you want in the search bar and then click on `"edit artifact"` on the search card of the particular artifact.
    * Or, the same can be achieved by clicking on `"edit metadata"` on the single artifact page.
    * You may also directly visit https://cdli.ucla.edu/artifacts/edit/1, here you can replace '1' with the id of the artifact that you want to edit.
    
* When you visit the edit form of an artifact that is not yet retired and scroll down a bit, the retired section will look something like this -
![toggle off](toggle_off.png) <br>
  Here, the toggle is off and hence the fields are disabled. When the toggle is clicked, the two fields will be enabled as in the image below, and you can enter the values that you want. <br>
![toggle on](toggle_on.png)

  Then finally, when you hit the save button, you will be redirected to artifacts-updates/add view for the changes you made. Here you can confirm your changes or discard them.

* To un-retire an artifact you simply need to turn off the toggle and the artifact will be un-retired. Rest of the process is same as above.

* Whenever an artifact is retired, it will not appear in search results.

* Also, when you link to the single view of a retired artifact(e.g. https://cdli.ucla.edu/artifacts/462) you will be redirected to the home page if that artifact doens't have a redirect_artifact_id. If it has one, you will be redirected to the single view of the artifact with that particular id.

* The flash message after linking to the single view of artifact P0000462(a retired artifact) would look like this <br>
 ![flash for redirect to view](redirect_view.png)
 