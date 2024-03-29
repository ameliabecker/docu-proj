# Level of Effort with Documentation Project
> Amelia Becker Aug 9 2019
## Goal of this project
For all of our engagements, we at Secunetics desire to ultimately transition our solutions to the clients to manage, grow, and make their own. This is only successful with a good way to transfer our knowledge. Without a system already in place company-wide, sometimes systems are never documented, which can lead to degradation and inconsistency in the solutions we are designing.

Our current system at DOT is a good starting point, but it could use streamlining and automation. Currently, content creators approach Dave when there is a need to write an SOP to acquire the most recent template for formatting the documents. This is a word template, which is not a format in which all of our team members have proficiency. Word has also been noted for having poor formatting for code-block instructions and in-line pictures. Once the content has been added and reviewed, the document goes back to Dave for QA for the layout and content. These are delivered as PDFs and Word documents to DOT maintained share-point sites, which are not the most flexible for tracking multiple versions of documentation.

We need a solution which will be less work at each step of the process:
- creating content
- editing content
- formatting consistently
- delivering
- revising documentation for new versions
- accessing and using the documents

## Breakdown of Tasks

| Task/goal | Description/Notes | Tasks associated | Priority | Level of Effort |
|--|--|--|--|--|
|Documents written in plain text (eg md) | This is something that we are used to doing as we document our code! We can have a discussion about markdown or ReStructured Text (md, rst) | Formalize the formatting procedure and documentation expectations. Potentially create a "sublime" plugin for consistency. | High | 0 |
|Version controlled documents| Utilize a git repo. This is important for maintaining our shared knowledge and keeping documentation up to date with new software releases and new procedures.| Utilize gitlab. Containerize and integrate with the document creation system. | High | 0/.5 day to setup a new repo |
|Separate content and design| This is crucial for being able to make quick content edits without going through QC every time. The goal is "consistency by design" |templatize the content, automate the build process| High |  |
|output formats: PDF, HTML, Word| This depends on the delivery format. Will this be a web accessible, structured presentation? Or will the outputs just be these documents. **Is Word delivery necessary?**| pdf and html are easy with sphinx. Discuss with Dave about the requirements. | High | 
|Automated build process| This would enable more consistent formatting with little human involvement	| test sphinx.| high
|- With human review (qc)| get editing and approval for the template, ensure that the following created documents are created as expected. | ask dave | high | 
|Easily modifiable design (which will propagate to all docs)| This is crucial for maintaining consistency. Even if the content stays the same, if a new version of the template is released, all of the documents should be easy to update| re-write sphinx templates, very easy with automated builds | high | 1 day, intrinsic
|Easy image integration| Once the image store is decided, the integration of images is an important capability, which should be intrinsic to the formatting we choose | | high | 1day
|- Ability to rebuild the same content into a new design| Tailor for a non-DOT deployment | change the sphinx template | medium | 1 day + review process
|- Access to past tagged revisions | Potentially necessary if running an old version. Or if there are various deployments with different images or SOPs |n/a| Medium | Intrinsic with version control |
|Supports versioned images and media files| With different versions of text, there may be different screenshots associated with the SOPs. | Determine what the best storage method is (independent object store, git repo) and implement it | Medium | same git repo, or ~3 days
|Templates/shell documents for content consistency|  | Jinja templating | Medium | 3 days
|Portability of the solutions to other clients| | | Medium | intrinsic
|RBAC to control who can edit docs| | | Low | ~2 days
|RBAC to control who can view docs| | | Low | same as above
|Web-based WYSIWYG editor|This would be helpful if the clients needed to edit this after deliver without having to download another software. Eg. [StackEdit](https://stackedit.io/app#)| apache license open source, integration and some customization with adding templates. Or use tools like github webui which renders previews live. | low |  |

## Recommendations
Given the amount of workstreams that are wrapping up now, and needing lots of continuing documentation support, I suggest that we at least adopt a few of these workflow enhancements.

### Easiest solution
- Content authors use markdown
- These are versioned in a git repo
- Text is built into PDFs by sphinx locally--built with DOT specific branding
- These PDFs etc are delivered by current methods (eg. to Sharepoint)

### Deliverable solution
- Different templates for SOPs and other documents
- Cloud hosted solution for accessing the
- pulls from git repos with webhooks
- Text is auto-built and deployed after QA

### Very nice to have solution
- On-prem hosted solution
- Full authentication integration
- Editable by client users after delivery
- Image/media file versioning is tracked (more efficiently than in git solution)
