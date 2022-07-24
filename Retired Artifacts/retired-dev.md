---
title: Retired Artifacts for Developers
section: Dev and devops docs
category: Features Guide
audiences:
  - Developer
chips:
  - developer
authors:
  - Angal, Shivoham
---
<h2>Retired Artifacts for Developers</h2>

When an artifact is retired it means either of the following two things
  - The particular entry is not valid anymore or,
  - If duplicate artifacts are found then we keep the old one and new one is retired.

The following list mentions the new features that were added to address the retired artifacts, along with the file changes -

1. First to get started, the tables being used for these functionalities are the `artifacts` table and the `artifacts_updates` table. Both of these tables have the three fields - `retired`, `redirect_artifact_id`, and `retired_comments` which are being used for this feature.

2. The entity files `Artifact.php` and `ArtifactsUpdate.php` are updated to address the two newly added columns.

3. The index page for the retired artifacts is in the `Admin/Artifacts/retired.php` file and can be viewed at - http://127.0.0.1:2354/admin/artifacts/retired. It uses the route -<br> 

        $routes->connect('/artifacts/retired', ['controller'=> 'Artifacts', 'action' => 'retired']);

    This route can be found in the `routes.php` file. It also uses the public functon `retired()` defined in the `Admin/ArtifacsController.php` file.

4. Next comes the redirect functionality where users linking to retired artifacts are redirected to the appropriate view. The logic for this can be found in the `ArtifacsController.php` file. It includes 2 cases -

    - If the artifact entry is now invalid i.e., it doesn't have a redirect_artifact_id then the user is redirected to the home page.<br>
    e.g. If a user links to http://127.0.0.1:2354/artifacts/119, then they will be redirected to the home page with the following flash mesage:
    ![flash for redirect to home](redirect_home.png)

    - If the artifact has a redirect_artifact_id then the user is redirected to the view of the artifact with that particular id.<br>
    e.g. If a user links to http://127.0.0.1:2354/artifacts/462, then they will be redirected the single view of the redirect_artifact_id - http://127.0.0.1:2354/artifacts/461 with the following flash message: <br>
    ![flash for redirect to view](redirect_view.png)

    If there is no comment as to why the artifact was retired, then the flash mesage would just say "The artifact PXXXXXX has been retired."

6. Finally comes the retired section in the artifact edit form. The form can be viewed at - http://127.0.0.1:2354/artifacts/edit/1 and the id '1' can be changed as per need. The view for the same is located in the `Artifacts/edit.php` file. In the form, the 2 fields "Redirect Artifact ID" and "Retired Comments" were added under the "Is this artifact retired" toggle. These 2 new fields are always displayed in the form but are disabled if the artifact is not retired.<br>
![toggle off](toggle_off.png) <br>
When toggle is on these 2 fields are no more disabled.  
![toggle on](toggle_on.png)

    To retire an artifact, the toggle is switched on and the 2 fields are updated as necessary. Finally, the user can save these changes.
