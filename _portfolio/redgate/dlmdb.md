---
title: "DLM Dashboard"
layout: single
excerpt: "Owen Priestley"
sitemap: true
permalink: /portfolio/redgate/dlmdb/
sidebar:
  nav: "portfolio"
---

I joined the SQL Source Control team to help document the overhaul of the migrations feature in the software. 

Migration scripts are a particularly difficult feature to document, as each user approaches the task with a different mental model, and often has a different understanding of when and how to use the feature.

    <None version="1">
    <Include>True</Include>
    <Expression>TRUE</Expression>
    </None>

<div markdown="1" class="notice"><h2 class="inside">Working with migration scripts</h2>

You can ignore changes to objects you're not interested in by adding a filter file to your pipeline. The file contains rules to ignore objects by name or type. Filtered objects won't trigger updates or drift, and aren't included in email notifications or reported on the Review page.

The filter file must contain valid XML and have a .scpf extension. You can create filters using SQL Compare or SQL Source Control, write your own, or download and edit this [.scpf example file][35]. 

Some changes are [ignored by default][36] and aren't affected by custom filters.

### Create a filter in SQL Compare or SQL Source Control

DLM Dashboard supports filters created using SQL Compare or SQL Source Control:

* to create filters using SQL Compare, see [Using filters][37]
* to create filters using SQL Source Control, see [Using filters to exclude objects][38]

### Use an example filter

We've provided a .scpf example file for you to download, and details of how to customize it. 

#### **Ignore objects by name**

In this example, you'll update the filter file to ignore changes to objects called `IGNORE`, or that start with `TEMP`.
<ol>
<li>Download the .scpf example file.</li>
<li>Open the file in a text editor.</li>
<li>At lines 12 to 15, replace:</li>
</ol>

    <None version="1">
    <Include>True</Include>
    <Expression>TRUE</Expression>
    </None>
    
with:

    <None version="1">
    <Include>False</Include>
    <Expression>(@NAME = 'IGNORE') OR (@NAME LIKE 'TEMP%')</Expression> <!-- Excludes objects called IGNORE and objects beginning with TEMP -->
    </None>

The `%` is a wildcard. Ignore multiple objects using the boolean operators `AND` / `OR `

<ol start="4">
<li>Save the filter with the extension .scpf, then add it to DLM Dashboard.</li>
</ol>

#### **Ignore objects by type**

In this example, you'll update the filter file to include or ignore changes to stored procedures.
<ol>
<li>Download the .scpf example file.</li>
<li>Open the file in a text editor.</li>
<li>At lines 108 to 111, replace:</li>
</ol>
    <StoredProcedure version="1">
    <Include>True</Include>
    <Expression>TRUE</Expression>
    </StoredProcedure>

with:

    <StoredProcedure version="1">
    <Include>True</Include>
    <Expression /> <!-- Excludes changes to stored procedures -->
    </StoredProcedure>
<ol start="4">
<li>Save the filter with the extension .scpf, then add it to DLM Dashboard.</li>
</ol>

### Add a filter

1. On the pipeline you want to apply the filter to, click **Filter objects**:  
![image-left](/images/dlmdb_fo.png)
2. Click **Choose file** and select the .scpf file.   
By default, SQL Compare stores filter files in _%USERPROFILE%DocumentsSQL CompareFilters_
3. Click **Apply**.  
DLM Dashboard uploads the filter and applies it to the databases in your pipeline.   

When you add a filter, DLM Dashboard detects a schema change, takes a snapshot, and compares it with the previous schema version. This may take a few minutes. 
Once you apply the filter, the change may show as database drift.

### Edit a filter

To change the filter file that already applies to a pipeline:

1. Click **Download**.
2. Open the file in a text editor and update the rules.   
For examples, see Ignore objects by name and Ignore objects by type
3. Save the filter with the extension .scpf.
4. Remove the filter file that's currently applied to the pipeline. To do this, on the dashboard, click **Remove**. 
5. Add the edited filter to DLM Dashboard. See Add a filter.

When you remove and then add a filter, DLM Dashboard detects a schema change, takes a snapshot, and compares it with the previous schema version. This may take a few minutes.

Once you apply the filter, the change may show as database drift.

### Creating new pipelines

When you move a database from a filtered pipeline to a newly created pipeline, the filter file is applied to the new pipeline. When you move a database to an existing pipeline, this won't affect any filters on it - the database will use any filter on to the pipeline it moves to.

[<i class="fa fa-file-pdf-o" aria-hidden="true"></i>  PDF](portfolio/redgate/dlmdb_filters.pdf){: .btn .btn--small}
</div>
