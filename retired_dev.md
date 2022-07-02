<h1 style="text-align: center">Retired Artifacts for Developers</h1>

When an artifact is retired it means that it is either permanently deleted or, say if there are 2 same artifacts then we keep the old one and new one is retired.

The following list mentions the new features that were added to address the retired artifacts, along with the file and database changes -

1. First to get started, update the database. The retired_artifacts table was deleted and its two columns retired_for and new_artifact_id were moved to the corresponding rows of the artifacts table with their names as redirect_artifact_id and retired_comments. To update the database, do the following steps -

    * First, you will have to add the two columns `redirect_artifact_id` (type: varchar) and `retired_comments` (type: text) to artifacts table. Collation: `utf8mb4_unicode_ci` and make both columns default to `NULL`. 

            UPDATE artifacts, retired_artifacts
            SET artifacts.retired_comments = retired_artifacts.retired_for,
            artifacts.redirect_artifact_id = retired_artifacts.new_artifact_id
            WHERE artifacts.id = retired_artifacts.artifact_id;

    * Then, some of the fields of both new columns might not be NULL just blank. So run these two queries:

            UPDATE artifacts SET retired_comments = NULL WHERE retired_comments = '';
            UPDATE artifacts SET redirect_artifact_id = NULL WHERE redirect_artifact_id = '';
    
    * Now, the next step is to update the artifacts_updates table. For this, run the following command similar to the first one - 

            UPDATE artifacts_updates, artifacts
            SET artifacts_updates.retired_comments = artifacts.retired_comments,
            artifacts_updates.redirect_artifact_id = artifacts.redirect_artifact_id
            WHERE artifacts_updates.artifact_id = artifacts.id

2. For the next step, the entity files `Artifact.php` and `ArtifactsUpdate.php` are updated to address the newly added columns.

3. Then to make the index page, a route is added to the `routes.php` file as -

        $routes->connect('/artifacts/retired', ['controller'=> 'Artifacts', 'action' => 'retired']);
        

4. Then the code for the index page is added in `Admin/Artifacts/retired.php` in the templates folder, and a public function `retired()` is added to the `Admin/ArtifacsController.php` file.

5. Next comes the redirect functionality where users linking to retired artifacts are redirected to the appropriate view. The logic for this can be found in the `ArtifacsController.php` file. It includes 2 cases -

    * If the artifact is deleted i.e., it doesn't have a redirect_artifact_id then the user is redirected to the home page.<br>
    e.g. If a user links to http://127.0.0.1:2354/artifacts/119, then they will be redirected to the home page with the following flash mesage:
    ![](redirect_home.png)

    * If the artifact has a redirect_artifact_id then the user is redirected to the view of the artifact with that particular id.<br>
    e.g. If a user links to http://127.0.0.1:2354/artifacts/462, then they will be redirected the single view of the redirect_artifact_id - http://127.0.0.1:2354/artifacts/461 with the following flash message: <br>
    ![](redirect_view.png)

    If there is no comment as to why the artifact was retired, then the flash mesage would just say "The artifact PXXXXXX has been retired."

6. Finally comes the retired section in the artifact edit form. Here, the 2 fields "Redirect Artifact ID" and "Retired Comments" were added under the "Is this artifact retired" toggle. If an artifact is not retired, then the toggle is off and the 2 new fields are displayed but are disabled.
![](toggle_off.png) <br>
When toggle is on these 2 fields are no more disabled.  
![](toggle_on.png)

    Finally the user can save these changes.