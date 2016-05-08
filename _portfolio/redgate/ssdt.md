---
title: "SSDT Reference Data Manager"
layout: single
excerpt: "Owen Priestley"
sitemap: true
permalink: /portfolio/redgate/ssdt/
sidebar:
  nav: "portfolio"
---

I joined the SQL Source Control team to help document the overhaul of the migrations feature in the software. 

Migration scripts are a particularly difficult feature to document, as each user approaches the task with a different mental model, and often has a different understanding of when and how to use the feature.

<div markdown="1" class="notice">
# How Reference Data Manager works
<h2 class="subtitle">Technical explanation sent to beta users</h2>
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

[<i class="fa fa-file-pdf-o" aria-hidden="true"></i>  PDF](portfolio/redgate/ssdt.pdf){: .btn .btn--small}
</div>