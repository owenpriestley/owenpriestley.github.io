---
title: "Reference Data Manager"
layout: single
excerpt: "Owen Priestley"
sitemap: true
permalink: /portfolio/redgate/ssdt/
sidebar:
  nav: "portfolio"
---
Reference Data Manager started life as a research project, with the goal of discovering whether users of Visual Studio Database Projects experienced significant pain when managing reference data (or static data), and whether it was feasible to build a tool that solved this problem.

I joined shortly after an alpha version of the tool was developed, at which point the team expanded from three to ten. This was the first time I’d worked on a tool in such an embryonic state. 

I worked closely with the UX designer on the team to develop various interfaces and workflows, testing them with different users. This usually involved screen sharing sessions with experienced Visual Studio users, observing as they attempted to perform various tasks with our tool.

I was solely responsible for preparing supporting documentation for the tool, building up a space from scratch in Confluence. I also worked with the product marketing manager to prepare copy for blog posts and newsletters, and wrote and recorded a promotional video to demonstrate the tool.
<div markdown="1" class="notice">
# How Reference Data Manager works
<h2 class="subtitle">A technical explanation sent to beta users</h2>
<h3> </h3>
<hr>

Reference Data Manager is installed in two parts: a Visual Studio extension and the essential build components. The extension allows you to create and edit database projects with reference data, whilst the essential build components are required to build and deploy those projects.

With the extension installed, you'll have the option to **Add New Reference Data File** when right-clicking a table in the solution explorer. You can create a reference data file based on the contents of a CSV file, or create an empty reference data file and manually specify data using `INSERT` statements.

When you build the project, Reference Data Manager uses the build components to incorporate any reference data files into the DACPAC, along with the other database objects.

### Reference data files

A reference data file uses `INSERT` statements to specify reference data for the table it depends upon. When you create a new reference data file (_.refdata.sql_) for a table in SSDT, Reference Data Manager updates the project file (_.sqlproj_) with a dependency to reflect this:

![image-left](/images/ssdt.png)

During deployment, Reference Data Manager compares the contents of the reference data file to the target table, and updates the target accordingly. Any rows that aren't present in the reference data file will be deleted from the target table.

Reference Data Manager uses three components to process your reference data and add it to a DACPAC for deployment. These components are installed separately, and must be present in addition to the Visual Studio extension on the build machine:</span>

#### Build task

The build task takes the project file (_.sqlproj_) and looks for reference data files (_.refdata.sql_) and their corresponding table files. It produces a build catalog, containing a list of table filenames and their associated reference data filenames.

#### Build contributor

The build contributor takes the build catalog, produced by the build task, and replaces table filenames with table names. The result is a new deployment catalog file, for the deployment contributor. This removes any discrepancies between table filenames and table names.

#### Deployment contributor

The deployment contributor uses the deployment catalog to add reference data files to the DACPAC, along with the name of the table that the data belongs to.

During deployment, the deployment contributor adds `INSERT`, `UPDATE` and `DELETE` statements to the deployment script, based on the differences between reference data in the source (the DACPAC) and the target database.

[<i class="fa fa-file-pdf-o" aria-hidden="true"></i>  PDF](portfolio/redgate/ssdt.pdf){: .btn .btn--large}
</div>

<div markdown="1" class="notice">
# How to add reference data to your database project in Visual Studio
<h2 class="subtitle">Video demonstration of the tool in practice</h2>
<h3> </h3>
<hr>
<p>I produced this video as both an instructional resource for user testing, and as a way to attract more users to the tool. Including a common use case, I hoped to pique the interest of SSDT users experiencing pain when trying to import reference data.
<iframe width="560" height="315" src="https://www.youtube.com/embed/XYY4LFyNTws" frameborder="1" allowfullscreen> </iframe>
<br/>

[<i class="fa fa-youtube" aria-hidden="true"></i>  YouTube](https://www.youtube.com/embed/XYY4LFyNTws){: .btn .btn--large}

</div>
