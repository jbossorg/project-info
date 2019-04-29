# project-info

### Syntax of the project property file

If you want your project information to be added to our search engine you must raise a PR for this file [project-info.json](https://github.com/jbossorg/project-info/blob/master/project-info.json). This article describes the content of the file entry.

The JSON file entry contains several required fields and the rest is optional.

### Required fields

*   **nodePath** - this field is used for two things: sorting in the project matrix and determining, whether the discribed project is "project" or "sub-project". It must start with "/" (followed by project name (only characters and numbers are allowed)). If it is a subproject, it will contain the project name followed by another "/" and the subproject name.  
      
    Example: Let us imagine we have a project called Hibernate and under this project we have two subprojects called "Hibernate Tools" and "Hibernate Shards". To describe this structure, you would need to have three project property files (one for each of the projects). The first one will have nodePath="/hibernate" (let us call this project "master project"), the other two will have nodePath="/hibernate/tools" and "/hibernate/shards"  
      
    The reason, why the projects in the project matrix are ordered by this field and not by the _projectName_ field is to allow the projects to be grouped by their master project. The master project is displayed first and after that come all subprojects. The subprojects have their name aligned a little bit more to the right than the master project. In case you do not have any subproject you will have only the "master project".  
      
    Never use "/project/subproject", unless you also specified "/project"! If you do, it will appear as if your project was the part of the project, that is before your project in the table.  
     
*   **projectName**  - this is a human readable name of your project. It is rendered as a link to your home page. If you use " - " in the name, this hyphen and everything after it will be cut from the name (have you seen the spaces around the hyphen?). However if you use something like "My-great-tools", the hyphen is considered to be the part of the name and will remain present.  
     
*   **homePage** - the URL of the home page of your project. The project name is displayed as the link and this field specifies its target. In case you do not enter this field, Magnolia tries to use _downloadsLink_ and _docsLink_ fields instead, but you really should enter this field. If neither of those fields are present, your project will NOT be displayed on the project matrix page at all.

### Downloads and Documentation links

*   **downloadsLink** - the link to your downloads page.  
     
*   **docsLink** - the link to your main documentation page (usually the overview or the table of contents)

### Community links

Only four links from this category will be displayed, if you enter more of them

*   **communityLink** - rendered as a link with the text "Community"
*   **knowledgeBaseLink** - rendered as "Wiki"
*   **userForumLink** - rendered as "User forum"
*   **devForumLink** - rendered as "Dev. forum"
*   **mailingListLink** - rendered as "Mailing list"
*   **chatLink** - rendered as "Chat". Some projects have a link to irc some to a html page. Both is correct.
*   **blogLink** - rendered as "Blog"
*   **twitterLink** - rendered as "Twitter"

### Issue tracking

Only one link will be displayed. In both cases (**issueTrackerLink** or **jiraLink**) the same text will be rendered = "Issue tracking". _jiraLink_ is the link to Jira and issueTrackerLink should be used in case of  any other issue tracking system. They are present both, because those fields are present in the project navigation Magnolia paragraph (and they are distinguished there). I suggest you to use the proper one in case someone decides to distinguish them in the project matrix too. 

### Source code

Only two links are displayed for this category. Git(hub) links take precedence over SVN (many of the projects moved from SVN to Github or some other Git, so there is high chance the Git repositories have newer code).

*   **srcLink** - rendered as the link with text "Source"
*   **anonymousLink** - the SVN repository for anonymous access.
*   **committerLink** - the SVN repository for people participating on the project
*   **fisheyeLink** - the link to Fish Eye
*   **viewvcLink** - the link to View VC
*   **githubLink** - the link to GitHub
*   **anonymousGitLink** - anonymous access to GIT repository
*   **committerGitLink** - like commiterLink but for GIT

### Miscellaneous fields

*   **description** - a short description of a project. It will be shown as a hint, when the user hovers above project title. Do not use html tags, they will be escaped.  
     
*   **license** - at this moment following values are allowed: "ASL" (Appache Software License v. 2.0), "EPL" (Elipse Public License), "LGPL" (Lesser General Public License version 2.1), LGPL2 (Lesser General Public License version 2.0), "LGPL3" (Lesser General Public License version 3.0) and "other". If you fill other, you must also fill **otherLicenseLink** field, because unlike in case of the known licenses project matrix does not know where the license page is located. The values ARE CASE SENSITIVE.  
     
*   **subProjects** - you can specify a list of URLs to project property files of subprojects of your project. Only master project is checked for this field, so it is not possible to reffer the subprojects indirectly. So let us say you report the project.properties file to help@jboss.org. We add this master project to Magnolia and it will check it. Magnolia finds the _subProjects_ field in this property file.  with several URLs to project.properties files of your subprojects. These will be added in the project matrix. However if you specify _subProjects_ field in the property files of the sub-projects it will be ignored.  
     
*    **specialIcon** - there is an icon before the name of the project. It is used by applying a CSS class name. The default value is calculated from nodePath parameter - if your _nodePath_ is /project/subproject, the style would be "project\_icon\_16x". You can change the part before "\_icon\_16x" by using this field. If your class is not in the list of the known icons, a blue bullet will be displayed before the name of your project by default. If you want to have your project specific icon, you must ask us by sending an e-mail to [help@jboss.org](mailto:help@jboss.org?subject=Request%20for%20adding%20an%20icon%20style%20into%20the%20project%20matrix%20paragraph%20in%20Magnolia). Our team will add the icon to the list. We will need to know the class name and to have the icon (picture 16x16 px.).  
     
*   **archived** - set this field to true, if your project is no longer active, but you let it available for general public. The project will be moved to "Archived" section of the project matrix. All links should still be valid. We do not want to have dead links in the project matrix even in the case of the dead projects.  
     
*   **excludeInProjectMatrix** - in case you want to remove your project from the project matrix, you can use this field (set its value to true). Your project will disappear from the project matrix, but Magnolia will still search for changes in the property file.  
      
    Please, if you use this field and it is not a temporary thing, let us know so we can remove your project property file destination from the list of parsed property files.  
     
*   For future use (at this moment unused in the project matrix) there are **buildLink** and **hudsonLink** available.
