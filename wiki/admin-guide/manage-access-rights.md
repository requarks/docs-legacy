<!-- TITLE: Manage Access Rights -->
<!-- SUBTITLE: How to manage user access rights -->

# What are access rights?
When you create or authorize a user in the system, that user has read-only permissions on all pages. Access rights is a list of permissions that are assigned to a user which define what he can or cannot do.

# View access rights
From the **Users** page, click on the **name** of the account you want to view.

A section is titled **Access Rights**, which lists the current access rights of the user:

![User Access Rights](/uploads/screenshots/ss-users-acl.jpg "User Access Rights")

# Manage access rights
A user can have as many access rights as needed. For example, you may want the user to be able to read any page but only create / edit a few. An access right rule consists of 4 parts:

- **Permission**: Defines what the user can do.
- **Path precision**: Whether the path entered should match precisly (Path match exactly) or only match the beginning (Path starts with).
- **Path**: The actual path
- **Allow / Deny**: Allow means the rule will be applied. Deny means the user will not be able to access the page.

By default, a user has `Read Only` (permission) to all pages that `starts with` (path precision) the path `/` (path).

To allow a user to create and edit any page on the site, simply change that permission to **Read and Write**.

## Add a new rule
To provide granular access to a user, you can add as many rules as you need. Rules are additive, with the Deny action having priority.

Given this example:

![Users ACL example](/uploads/screenshots/ss-users-acl-example.jpg "Users ACL example")

- The user can read any page, with the exception of all pages that starts with `/violin`.
- The user can edit (and create) the page `/piano`, but not `/pianos` or `/piano/studio-grand`
- The user cannot read, create or edit any page that begins with `/violin`. Therefor, he can read the page `/viola` but not `/violin/strings`

Click **Save Changes** to save the new rules.

## Remove a rule
Simply click the red **X** button next to the rule to delete.

Click **Save Changes** to save the updated rules.
