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

<div class="notice"><h2 class="inside">Working with migration scripts</h2>
<h3>What are migration scripts?</h3>
<p>When you deploy changes committed to version control, the SQL Compare
engine generates a deployment script to update the target database.You
can use a migration script to add custom SQL to a specific point in this
deployment script.</p>

<p>Migration scripts are necessary to avoid data loss when making certain
schema changes. To achieve this, the migration script intervenes to make
data changes occur at the right point of the deployment.</p>

<p>In most cases, you only need to write SQL for the data changes in the
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
 <p>Always commit a new migration script immediately after saving it.</p>
 <p>Making changes to your database schema between saving and committing
 migration scripts can cause errors during deployment.</p>

<p>When you deploy this revision from version control, or use <strong>Get
latest</strong> in SQL Source Control on another machine, the migration script
will run as part of the deployment.</p>

For more information, see <a style="color: #52adc8" href="https://documentation.red-gate.com/display/SOC5/How+migration+scripts+work">How migration scripts work</a><br/>

<h3>Editing migration scripts</h3>
<p>You can edit or delete existing migration scripts from
the <strong>Migrations</strong> tab in SQL Source Control:</p>
<ol>
<li>From the <strong>Object Explorer</strong>, select a database with
    migration scripts.</li>
<li>From the toolbar, select <strong>SQL Source Control</strong>.  
    The SQL Source Control window opens.</li>
<li>Go to the <strong>Migrations</strong> tab.</li>
<li>Expand <strong>Existing migration scripts</strong>. 
    Migration scripts on the remote repository are listed.</li> 
<li>In the <strong>Actions</strong> column, click <strong>View / Edit</strong> next to a migration script.</li>
<li>Edit the script to make the required changes.</li>
<li>Click <strong>Save & Close</strong>.</li>
<li>Go to the <strong>Commit changes</strong> tab and commit the updated
    migration script.</li>
</ol>
<p>Once committed, the updated migration script is used in all future
deployments.</p>

  <strong>Guidelines for editing migration scripts:</strong>
  <p><ul>
   <li>Don't create new object dependencies. This is likely to cause errors during deployment.</li> 
   <li>Don't add/remove DDL changes. This might create an invalid state in version control.</li>
   <li>If you edit the syntax of DDL changes, the resulting schema must stay the same.</li>
  </ul></p>

<h3>Deploying with migration scripts</h3>

<p>We recommend using SQL Compare to deploy changes to production, as you
have the opportunity to review the deployment script before it's
deployed. </p>

<p>It is possible to use the <strong>Get latest</strong> function in SQL
Source Control to deploy these changes, however we don't recommend
linking your production database directly to source control.</p>

<strong>Dependencies</strong>

<p>When you create a migration script that includes uncommitted schema
changes, SQL Source Control automatically includes any dependencies.</p>
<p>Deselecting any of these dependencies during the deployment stage will
cause the deployment to fail.</p>
</div>
[PDF](portfolio/redgate/SOC5-Workingwithmigrationscripts.pdf){: .btn .btn--small} [Confluence](https://documentation.red-gate.com/display/SOC5/Working+with+migration+scripts){: .btn .btn--small}