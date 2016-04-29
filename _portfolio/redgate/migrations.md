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

## Working with Migration scripts

### What are migration scripts?

When you deploy changes committed to version control, the SQL Compare
engine generates a deployment script to update the target database.You
can use a migration script to add custom SQL to a specific point in this
deployment script.

Migration scripts are necessary to avoid data loss when making certain
schema changes. To achieve this, the migration script intervenes to make
data changes occur at the right point of the deployment.

In most cases, you only need to write SQL for the data changes in the
migration script. Schema changes are committed separately and deployed
as normal. 

### Creating a migration script

To create a new migration script:

1.  From the **Object Explorer**, select the database you want to add a
    migration script to.

2.  From the toolbar, select **SQL Source Control**.  
The SQL Source Control window opens.

3.  Go to the **Migrations** tab.

4.  Select the type of migration script, depending on your development
    process and the changes you're making.

5.  In the **Name** field, enter a name for the script.

6.  In the editor window, write SQL to make the required changes.

7.  Click **Save & Close**.

8.  Commit the changes to version control.

 Always commit a new migration script immediately after saving it.
 Making changes to your database schema between saving and committing
 migration scripts can cause errors during deployment. 

When you deploy this revision from version control, or use **Get
latest** in SQL Source Control on another machine, the migration script
will run as part of the deployment. 

For more information, see [How migration scripts work](https://documentation.red-gate.com/display/SOC5/How+migration+scripts+work).

#### Editing migration scripts

You can edit or delete existing migration scripts from
the **Migrations** tab in SQL Source Control:

1.  From the **Object Explorer**, select a database with
    migration scripts.

2.  From the toolbar, select **SQL Source Control**.  
    The SQL Source Control window opens.

3.  Go to the **Migrations** tab.

4.  Expand **Existing migration scripts.**  
    Migration scripts on the remote repository are listed. 

5.  In the **Actions** column, click **View / Edit** next to a
    migration script.

6.  Edit the script to make the required changes.

7.  Click **Save & Close**.

8.  Go to the **Commit changes** tab and commit the updated
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

#### Deploying with migration scripts

We recommend using SQL Compare to deploy changes to production, as you
have the opportunity to review the deployment script before it's
deployed. It is possible to use the **Get latest** function in SQL
Source Control to deploy these changes, however we don't recommend
linking your production database directly to source control.

**Dependencies**

When you create a migration script that includes uncommitted schema
changes, SQL Source Control automatically includes any dependencies.
Deselecting any of these dependencies during the deployment stage will
cause the deployment to fail. 

[PDF](portfolio/redgate/SOC5-Workingwithmigrationscripts.pdf){: .btn .btn--small} [Confluence](https://documentation.red-gate.com/display/SOC5/Working+with+migration+scripts){: .btn .btn--small}