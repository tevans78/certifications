# Certifications
This repository will be used to house the Jakarta EE TCK Results for the Certification Requests.
The TCK Results need to be in a publicly accessible website via a defined URL.
These TCK Results are not indexed and, therefore, will not appear in search results.
All TCK Results (all pages with `:page-layout: certification` to be exact) can be viewed on [openliberty.io/certifications/](https://openliberty.io/certifications/), which is also not indexed.

## File Format
The TCK Results will be asciidoc (<runtimeVersion>TCKResults.adoc) files.
This format will allow for easy rendering onto the openliberty.io site.
Shortly after PRs are merged into this repo, the results will be accessible via https://openliberty.io/certifications/...

## Directory Structure
The following directory structure will be used to house these TCK Results:

```https://openliberty.io/certifications/<spec/architecture>/<specVersion>/<optional: subSpec>/<optional: subSpecVersion>/<runtimeVersion>TCKResults```
For example,
```
https://openliberty.io/certifications/jakartaee/8/webprofile/19.0.0.6-TCKResults.html
https://openliberty.io/certifications/jakartaee/9.1/platform/21.0.0.2-beta-Java11-TCKResults.html

https://openliberty.io/certifications/microprofile/5.0/21.0.0.12-beta-TCKResults.html
https://openliberty.io/certifications/microprofile/5.0/config/3.0/21.0.0.12-beta-TCKResults.html

https://openliberty.io/certifications/microprofile/restclient/ccr/2.0/TCKResults.html
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

5. Push the file to GitHub (if you're a member of this org, feel free to push your branch to the certification repo instead of using a fork), then create a pull request (PR) into the `draft` branch.

6. Request a code review.  The code review can be from anyone, however, you should consider including @mbroz2, @Emily-Jiang (for MicroProfile), @jhanders34 (for Jakarta EE), or @tevans78 (for MicroProfile/Jakarta EE).  Once the PR has been approved, merge it into `draft`.

6. All the builds and deployments of non-prod sites are on IBM Cloud and build automatically whenever the a PR is merged into their respective branch. These builds are private and, therefore, their detailed build/deploy progress can't be tracked. However, if you have access to the [Slack channel](https://app.slack.com/client/T15GKHBT4/C01G7N292RH), you can at least track when the builds start and finish.  

7. When the build is finished, check that the TCK result page renders correctly on either the [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications) or the [full draft site](https://draft-openlibertyio.mybluemix.net/certifications).  

   In addition to the existing [full draft site](https://draft-openlibertyio.mybluemix.net/certifications) we now have a [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications), which contains only the certifications content, allowing it to build and deploy much quicker. However, since this site contains only the certifications content, any links to other parts of openliberty.io will not resolve. In general, use the certifications-draft site to review content because it updates much quicker than the full site. However, if you need to review content that links to pages on openliberty.io that are not under /certifications/, use the full draft site.

   If you see any problems, such as formatting issues or typos, resolve them first in your branch. Then, create another PR into `draft` branch, and get it reviewed and merge. Wait for IBM Cloud to rebuild [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications) or [draft site](https://draft-openlibertyio.mybluemix.net/certifications) and verify the change.

8. When you're happy with the change, create a PR from your branch (_not_ from the `draft` branch) to the `staging` branch.

   Link the PR to the issue.
 
   In the PR, provide a link to your page on the [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications) or [draft site](https://draft-openlibertyio.mybluemix.net/certifications). Ideally, also paste a screenshot of the entire Certification/TCK Result page as this will allow reviewers to see the rendered content even while the sites are innaccessible (e.g. during redeploys).
   
   Add @mbroz2 or another admin to get their final approval for both content and format.
   
   As before, make any changes in your feature branch, create a PR `draft` branch, get it reviewed and merged, and once the site rebuilds, check that everything is correct on the [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications) or [draft site](https://draft-openlibertyio.mybluemix.net/certifications).

   This automatically updates the PR to `staging`.
   
## Admins: Editing and Publishing TCK Results
These steps are completed by the admins of this repo. They might ask questions or make suggestions regarding the content. They might also make edits directly to the file before publishing.

1. Review the page on the [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications) or [draft site](https://draft-openlibertyio.mybluemix.net/certifications) as linked from the PR.

   Ask the author to make changes by adding review comments to the PR.

   Alternatively, if the branch was created in the OpenLiberty/certifications, or the admin has access to the fork, the editor can make the edits directly in the author's branch and push the changes to `draft` branch, which automatically rebuilds the [certifications-draft site](https://certifications-draft-openlibertyio.mybluemix.net/certifications) and [draft site](https://draft-openlibertyio.mybluemix.net/certifications) where you can verify the changes.
   
   To check out the author's branch locally: `git fetch origin` then `git checkout -b branch_name origin/branch_name`, which creates a new local branch that's linked to their remote branch. When you've made changes, push them back to `origin/branch_name`.
   
2. Approve the PR and merge it into `staging` branch.

4. IBM Cloud will automatically rebuild the [certifications-staging site](https://certifications-staging-openlibertyio.mybluemix.net/certifications) and [staging site](https://staging-openlibertyio.mybluemix.net/certifications). If you have access, you can track the progress in the [Slack channel](https://app.slack.com/client/T15GKHBT4/C01G7N292RH).  

5. When the build has finished, check to make sure the page render correctly on the [certifications-staging site](https://certifications-staging-openlibertyio.mybluemix.net/certifications) or [staging site](https://staging-openlibertyio.mybluemix.net/certifications). The latter includes the entire site, while the former just has the /certifications/ content.  If you need to verify links to other parts of the site (outside of the /certifications/ content) then you'll need to wait for the full [staging site](https://staging-openlibertyio.mybluemix.net/) to build.  

   This is the final check before the page is published live on the [production site](https://openliberty.io/).

   If there are any problems found on the [staging site](https://staging-openlibertyio.mybluemix.net/), you must resolve them quickly or revert the PR.
   
   Make any changes in the author's branch, and push to both `draft` and `staging`.
   
6. To publish the content, create a PR from `staging` branch to `prod` branch and add @mbroz2 (or other admin) as approver.

7. When the PR is approved, merge it into `prod`.

12. Rebuild the [production site from the IBM Cloud console](https://console.bluemix.net/devops/pipelines/fcc7c3e9-9c40-4a58-8a7f-09c08413ab7d?env_id=ibm:yp:us-south).

    When the build has finished, check that the page looks as expected on [openliberty.io/](https://openliberty.io/).

13. When the page is published, and any changes you made are in all three branches (`draft`, `staging`, and `prod`), delete the author's branch.
