---
title: "SQL Source Control"
layout: single
excerpt: "Owen Priestley"
sitemap: true
permalink: /portfolio/redgate/migrations/
sidebar:
  nav: "portfolio"
---

I joined the SQL Source Control team to help document the overhaul of the migrations feature in the software. 

Migration scripts are a particularly difficult feature to document, as each user approaches the task with a different mental model, and often has a different understanding of when and how to use the feature.

<div class="notice"><h2 class="inside">Working with migration scripts</h2>
<h3>What are migration scripts?</h3>
<p>When you deploy changes committed to version control, the SQL Compare
engine generates a deployment script to update the target database.You
can use a migration script to add custom SQL to a specific point in this
deployment script.<br/>

Migration scripts are necessary to avoid data loss when making certain
schema changes. To achieve this, the migration script intervenes to make
data changes occur at the right point of the deployment.<br/>

In most cases, you only need to write SQL for the data changes in the
migration script. Schema changes are committed separately and deployed
as normal.</p>

<h3>Creating a migration script</h3>

To create a new migration script:<br/>
<ol>
<li>From the <strong>Object Explorer</strong>, select the database you want to add a
    migration script to.</li>

<li>From the toolbar, select <strong>SQL Source Control</strong>.<br/> 
The SQL Source Control window opens.</li>

<li>Go to the <strong>Migrations</strong> tab.</li>

<li>Select the type of migration script, depending on your development
    process and the changes you're making.</li>

<li>In the <strong>Name</strong> field, enter a name for the script.</li>

<li>In the editor window, write SQL to make the required changes.</li>

<li>Click <strong>Save & Close</strong>.</li>

<li>Commit the changes to version control.</li>
</ol>
 Always commit a new migration script immediately after saving it.</br></br>
 Making changes to your database schema between saving and committing
 migration scripts can cause errors during deployment. </br>

When you deploy this revision from version control, or use <strong>Get
latest</strong> in SQL Source Control on another machine, the migration script
will run as part of the deployment. </br>

For more information, see <a href="https://documentation.red-gate.com/display/SOC5/How+migration+scripts+work">How migration scripts work</a><br/>

<h3>Editing migration scripts</h3>

You can edit or delete existing migration scripts from
the <strong>Migrations</strong> tab in SQL Source Control:

1.  From the <strong>Object Explorer</strong>, select a database with
    migration scripts.

2.  From the toolbar, select <strong>SQL Source Control</strong>.  
    The SQL Source Control window opens.

3.  Go to the <strong>Migrations</strong> tab.

4.  Expand <strong>Existing migration scripts</strong>. 
    Migration scripts on the remote repository are listed. 

5.  In the <strong>Actions</strong> column, click <strong>View / Edit</strong> next to a migration script.

6.  Edit the script to make the required changes.

7.  Click <strong>Save & Close</strong>.

8.  Go to the <strong>Commit changes</strong> tab and commit the updated
    migration script.

Once committed, the updated migration script is used in all future
deployments.

<div class="notice--info">
  <h4>Guidelines for editing migration scripts:</h4>
  <ul>
   <li>Don't create new object dependencies. This is likely to cause errors during deployment.</li> 
   <li>Don't add/remove DDL changes. This might create an invalid state in version control.</li>
   <li>If you edit the syntax of DDL changes, the resulting schema must stay the same.</li>
  </ul>
</div>

<h3>Deploying with migration scripts</h3>

We recommend using SQL Compare to deploy changes to production, as you
have the opportunity to review the deployment script before it's
deployed. It is possible to use the <strong>Get latest</strong> function in SQL
Source Control to deploy these changes, however we don't recommend
linking your production database directly to source control.

<p style="text-weight: strong">Dependencies</p>

When you create a migration script that includes uncommitted schema
changes, SQL Source Control automatically includes any dependencies.
Deselecting any of these dependencies during the deployment stage will
cause the deployment to fail. 

</p></div>

[PDF](portfolio/redgate/SOC5-Workingwithmigrationscripts.pdf){: .btn .btn--small} [Confluence](https://documentation.red-gate.com/display/SOC5/Working+with+migration+scripts){: .btn .btn--small}