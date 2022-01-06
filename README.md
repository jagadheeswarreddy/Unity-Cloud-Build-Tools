

Its a tool to trigger cloud builds from within the unity editor directly. We can also define from which branch to trigger a new build.



Refresh

    There is a refresh button at the top which can be used to reload the editor UI in case it hasn't loaded automatically.
    If current project is not linked to any git repo, then you will see the warning as shown in the right pic.

Custom Build
Current Branch

    This is read-only field and will display current branch to which project is switched currently.

Selected Branch

    This is a drop-down field and will display all the branches available in the project.
    Prune or fetch from remote in git client if you don't see the branch you are looking for or you see extra branches which doesn't exist anymore.

Reset

    This will reset the selected branch to same as current branch.

Create Build

    This will first check if any build target exists for selected branch.
    If not, then it will create a new build target with same name as selected branch.
    If build target already exists, it will retrieve the build target info and trigger a new build

Cancel Build

    This will cancel any running builds for selected branch

List of All Build Targets

This will display the list of all build targets that are available on Unity Cloud dashboard.

It will take few seconds to display as the list is fetched thru unity cloud api realtime.

For each build target, there are few GUI controls as follows:
Create Build

    It will trigger a new build for selected build target

Get Logs

    It will download the log file for last build triggered from the selected build target.
    Log file will be around 3-4mb on average, so it might take some to download.
    As there is no progress bar UI for showing download, please wait for sometime until log is printed in console.
    This will automatically save the logs file downloaded at project root directory (outside assets folder) with same name as build target.
    Saved file will also mention build number in filename to avoid any confusion.

Cancel Build

    This will cancel any running builds for selected build target

Delete Build Target

    This will delete the selected build target.
    Remember to delete unnecessary build targets periodically which are not needed anymore.

Cloud Build Settings
Org Id & Project Id

    These are specific to the project you are working on.
    Obtained from the Unity account for which cloud access has been given.
    Organization id will likely remain same across all the projects but project id will be unique for each project.

Base Url and Other Api Urls

    Those are http urls which will be pinged for each respective api.
    Urls are provided by cloud itself (refer here)

Basic Token

    This will be sent along with each request to Unity Cloud.
    This is needed for authentication purpose and can be obtained from Unity Dashboard (Settings → API Settings → API key).
    This will not change until revoked from Unity dashboard settings
    Its value should be Basic [YOUR API KEY]

Android/IOS Credential Id

    These are signing credentials required to sign each build.
    For IOS, we need to provide provisioning certificate and p12 file
    For Android, we need to provide keystore.
    These credentials we can create during cloud build configuration.
    Once created, each credential will be linked to unique credential id.
    List of all credentials can be retrieved using this api (refer here)

Refresh Image

    Just an image to be displayed on top of refresh button.

Build Params

    This is a part of body that will be sent along with each request to cloud to trigger new build.
    We are sending default values here for the time being.
    If required,
        we can add delay 
        we can also enable clean build which will reimport entire library folder once again on cloud.
        we can specify exactly which commit id to make build from.

Build Target Info

    This is a part of body that will be sent along with each request to cloud to create new build target.
    We are sending default values here for the time being.
    If required,
        we can change unity version,
        we can change xcode version for iOS build
        we can set whether it should be development build or not.
        we can append scripting symbols
        we can define pre export method to execute before creating cloud build.
        we can enable app bundle or auto build
    Read the documentation for more details.

