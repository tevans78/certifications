# Certifications
This repository will be used to house the Jakarta EE TCK Results for the Certification Requests.
The TCK Results need to be in a publicly accessible website via a defined URL.
These TCK Results do not need to be accessible from the main [openliberty.io](https://openliberty.io) site.

## File Format
The TCK Results will be asciidoc (TCKResults.adoc) files.
This format will allow for easy rendering onto the openliberty.io site.
Shortly after PRs are merged into this repo, the results will be accessible via https://openliberty.io/certifications/...

## Directory Structure
The following directory structure will be used to house these TCK Results:

```https://openliberty.io/certifications/jakartaee/<specification>/<specification version>/TCKResults```
For example,
```
https://openliberty.io/certifications/jakartaee/platform/8/TCKResults.html
https://openliberty.io/certifications/jakartaee/webprofile/8/TCKResults.html
https://openliberty.io/certifications/jakartaee/servlet/4.0/TCKResults.html
```
## TCKResults Content
Reference the [sample TCKResults](./TCKResults.adoc) file for an example of the content.

# Instructions for making changes to this repo

## Authors: Creating & Updating TCK Results
1. Clone the repo and create your feature branch off of the default `prod` branch. From the `prod` branch, run: `git branch -b branch_name`, where `branch_name` is a name you give your new branch.

    Do _all_ your editing in this branch.

2. Create your TCK result using [Asciidoc](https://asciidoctor.org/docs/asciidoc-syntax-quick-reference/) markup (use an editor such as [VSCode with the Asciidoc plugin](https://marketplace.visualstudio.com/items?itemName=joaompinto.asciidoctor-vscode)):

    * Reference the [sample TCKResults](./TCKResults.adoc) file for an example of the content.

3. If you are not employed by IBM, in at least one of your commits, sign off the commit using [the Developer Certificate process](./CONTRIBUTING.md).

4. When you have finished, check that the content renders correctly. If you have a preview function in your editor, use that (eg the Asciidoc plugin in VSCode).  Browser plugins exist as well.

5. Push the file to GitHub, then create a pull request (PR) into the `draft` branch.

6. Request a build of the [draft openliberty.io site](https://draft-openlibertyio.mybluemix.net/):
    1. Sign in to [Travis CI](https://travis-ci.com/github/OpenLiberty/openliberty.io) with your GitHub account.
    2. Click **More Options > Trigger Build**. Make sure the `master` branch is selected, then click **Trigger custom build**.
    
          The draft site build starts running.

7. When the build is finished, check that the TCK result page renders correctly on the [draft site](https://draft-openlibertyio.mybluemix.net/).  The URL path mimics the directory structure of this repo.

    If you see any problems (e.g. formatting or typos), resolve them first in your branch, create another PR into `draft` branch, then run the [draft site build from Travis CI](https://travis-ci.com/github/OpenLiberty/openliberty.io) again.

8. When you're happy with the changes, create a PR from your branch (_not_ from the `draft` branch) to the `staging` branch.

   In the PR, provide a link to your page on the [draft site](https://draft-openlibertyio.mybluemix.net/).  A screenshot of the page is also helpful, but not necessary.
   
   Add @mbroz2 or another admin to get their final approval for both content and format.
   
   As before, make any changes in your branch, push the changes to the `draft` branch, then run the [draft site build from Travis CI](https://travis-ci.com/github/OpenLiberty/openliberty.io) again to check that they are fine on the [draft site](https://draft-openlibertyio.mybluemix.net/).

   This automatically updates the PR to `staging`.
   
## Admins: Editing and Publishing TCK Results
These steps are completed by the admins of this repo. They might ask questions or make suggestions regarding the content. They might also make edits directly to the file before publishing.

1. Review the page on the [draft site](https://draft-openlibertyio.mybluemix.net//) as linked from the PR.

   Ask the author to make changes by adding review comments to the PR.

   For edits such as punctuation, formatting, highlighting, or larger changes discussed with the author, the editor can make the edits directly in the author's branch and push the changes to `draft` branch, then rebuild the [draft site from Travis CI](https://travis-ci.com/github/OpenLiberty/openliberty.io) to check them.
   
   To check out the author's branch locally: `git fetch origin` then `git checkout -b branch_name origin/branch_name`, which creates a new local branch that's linked to their remote branch. When you've made changes, push them back to `origin/branch_name`.
   
2. Approve the PR and merge it into `staging` branch.

4. Request a build of the [staging openliberty.io site from Travis CI](https://travis-ci.com/github/OpenLiberty/openliberty.io).

5. When the build has finished, check to make sure the page renders correctly on the [staging site](https://staging-openlibertyio.mybluemix.net/). 

   This is the final check before the page is published live on the [production site](https://openliberty.io/).

   If there are any problems found on the [staging site](https://staging-openlibertyio.mybluemix.net/), you must resolve them quickly or revert the PR.
   
   Make any changes in the author's branch, and push to both `draft` and `staging`.
   
6. To publish the content, create a PR from `staging` branch to `prod` branch and add @mbroz2 (or other admin) as approver.

7. When the PR is approved, merge it into `prod`.

12. Rebuild the [production site from the IBM Cloud console](https://console.bluemix.net/devops/pipelines/fcc7c3e9-9c40-4a58-8a7f-09c08413ab7d?env_id=ibm:yp:us-south).

    When the build has finished, check that the page looks as expected on [openliberty.io/](https://openliberty.io/).

13. When the page is published, and any changes you made are in all three branches (`draft`, `staging`, and `prod`), delete the author's branch.
