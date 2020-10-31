# Outreachy_Application
Enable CI/CD of content to fedora-docs site.  

## My Contributions during application period:

- I added Code of conduct link to footer of each page on fedora-docs and fixed this [issue](https://pagure.io/fedora-docs/docs-fp-o/issue/132). 

  Contribution URL- https://pagure.io/fedora-docs/fedora-docs-ui/pull-request/12
  
- Many people were confused that the local preview of this repository should look like the actual fedora site as discussed in 
  [this](https://pagure.io/fedora-docs/fedora-docs-ui/issue/29) issue. They need to be informed that the local preview of this repository will build only the UI of the project.   The actual fedora site is build using the   [builder repository](https://pagure.io/fedora-docs/docs-fp-o). So I added a note in README which will clarify this point to those   who try to setup this repository. Since this   repository currently needs node version 10 and gulp version 3, so I mentioned this point also in README file.

  Contribution URL- https://pagure.io/fedora-docs/fedora-docs-ui/pull-request/42
  
- The container image for this repository is not updated. To figure out the problem I created a container from this image using podman. There I founded that pre installed node   version is 12 in this image due to which it is giving Assertion error. When I downgraded the node version to 10, it runs successfully. Thus the image needs to be modified as   builder script is using this image to build this repository. So I created an issue an fedora-docs-ui

  Contribution URL- https://pagure.io/fedora-docs/fedora-docs-ui/issue/44
  
- Some commands in antora-ui-builder script is wrong due to which it is not giving the desired results. So I changed the commands which fixed this issue. I also changed the       commands in README file which were wrongly mentioned. This will help people who want to setup this repository using script.

  Contribute URL: https://pagure.io/fedora-docs/fedora-docs-ui/pull-request/45
  
## Research Work during application period: 

  Since fedora-docs is built using antora, I researched on how antora is building whole website using [antora docs](https://docs.antora.org/antora/2.3/navigation/). 
  
  - Firstly I figured that the whole website is not placed in a single repository. There is a seperate repository for each component of the website such as [fedora-docs-ui](https://pagure.io/fedora-docs/fedora-docs-ui) for ui componenet, [install guide](https://pagure.io/fedora-docs/install-guide) etc. 
  - By placing components in multiple repository, we can defined different versions of each component. 
  - Antora took all these repositories and build a website for us. It gives us a feature to switch between different versions of a component. 
  - To tell Antora which repositories should it look, we specifed a [antora playbook in builder repository](https://pagure.io/fedora-docs/docs-fp-o/blob/prod/f/site.yml). The       playbook contains information on what versions of repository should it take, what should be the title of the site, ui bundle information. 
  - Antora builds only the content placed in modules folder. It ignores any content placed out of modules folder. Each antora.yml file placed in the repository tells antora the     version of the content. The antora uses antora.yml file to get the version of a component.
  - Antora also builds nav bar automatically. The content to be placed inside a nav bar is specified through nav.adoc file placed inside modules directory. 
  - Taking an example of one component. The nav bar described [here](https://pagure.io/fedora-docs/install-guide/blob/master/f/modules/install-guide), will only be the nav bar     for this component, used to display it's sub components. This component is described in other nav bar placed this repository(https://pagure.io/fedora-docs/release-docs-         home). 
  - Most of the repository contains a build.sh and preview.sh scripts to locally preview the content of each one of them. To build the whole website you need to setup the           builder repository that contains antora playbook. 
  - To build the website, one need to install nodejs and gulp on their system. 
 
## Openshift progress report: 

During the contribution period, I learned

- What is S2I builder in openshift.
- Build process of S2I builder. 
- What is openshift cli 
- How to create, delete, update resources using openshift cli
- How to connect database using port forwarding
- what is argocd and use argocd for GitOps with Openshift  
- How to create multi-cluster GitOps application with Openshift
- Persistant storage in Openshift.
- Get started with Openshift Pipelines. 

I have sum up all my learnings for openshift in google docs. Here is the link. Please have a look at that also. 
https://docs.google.com/document/d/1vlFSjK1WS3cE-WkyT6UhYeCSIGWUujmMQOztWXtVGvQ/edit?usp=sharing

Apart from these learnings, I have also done an Introduction to Openshift applications course from redhat few months ago. Here is the link of my certificate 
https://drive.google.com/file/d/1d6wUemtNLaILBG73bkE4KnU7q6bUS2ic/view?usp=sharing
