---
title: Global Permissions
weight: 1126
---

_Permissions_ are individual access rights that you can assign when selecting a custom permission for a user.

Global Permissions define user authorization outside the scope of any particular cluster. Out-of-the-box, there are two default global permissions: `Administrator` and `Standard User`.

- **Administrator:**

    These users have full control over the entire Rancher system and all clusters within it.

- <a id="user"></a>**Standard User:**

    These users can create new clusters and use them. Standard users can also assign other users permissions to their clusters.

>**Note:** You cannot create, update, or delete Global Permissions.

# Global Permission Assignment

Assignment of global permissions to a user depends on their authentication source: external or local.

- **External Authentication**

    When a user logs into Rancher using an external authentication provider for the first time, they are automatically assigned the `Standard User` global permission.

- **Local Authentication**

    When you create a new local user, you assign them a global permission as you complete the **Add User** form.

# Custom Global Permissions

Using custom permissions is convenient for providing users with narrow or specialized access to Rancher.

When a user from an [external authentication source]({{< baseurl >}}/rancher/v2.x/en/admin-settings/authentication/) signs into Rancher for the first time, they're automatically assigned a set of global permissions (hereafter, permissions). By default, after a user logs in from the first time, they are created as a user and assigned the default `user` permission. The standard `user` permission allows users to login and create clusters.

However, in some organizations, these permissions may extend too much access. Rather than assigning users the default global permissions of `Administrator` or `Standard User`, you can assign them a more restrictive set of custom global permissions.

The default roles, Administrator and Standard User, each come with multiple global permissions built into them. The Administrator role includes all global permissions, while the default user role includes three global permissions: Create Clusters, Use Catalog Templates, and User Base, which is equivalent to the minimum permission to log in to Rancher. In other words, the custom global permissions are modularized so that if you want to change the default user role permissions, you can choose which subset of global permissions are included in the new default user role.

Administrators can enforce custom global permissions in two ways:

- Changing the [default permissions for new users](#configuring-default-global-permissions)

- Editing the [permissions of an existing user](#configuring-global-permissions-for-individual-users)

### Custom Global Permissions Reference

The following table lists each custom global permission available and whether it is included in the default global permissions, `Administrator` and `Standard User`.

| Custom Global Permission           | Administrator | Standard User |
| ---------------------------------- | ------------- | ------------- |
| Create Clusters                    | ✓             | ✓             |
| Create RKE Templates               | ✓             | ✓             |
| Manage Authentication              | ✓             |               |
| Manage Catalogs                    | ✓             |               |
| Manage Cluster Drivers             | ✓             |               |
| Manage Node Drivers                | ✓             |               |
| Manage PodSecurityPolicy Templates | ✓             |               |
| Manage Roles                       | ✓             |               |
| Manage Settings                    | ✓             |               |
| Manage Users                       | ✓             |               |
| Use Catalog Templates              | ✓             | ✓             |
| User Base* (Basic log-in access)   | ✓             | ✓             |

> *This role has two names:
>
> - When you go to the <b>Users</b> tab and edit a user's global role, this role is called <b>Login Access</b> in the custom global permissions list.
> - When you go to the <b>Security</b> tab and edit the roles from the roles page, this role is called <b>User Base.</b>

For details on which Kubernetes resources correspond to each global permission, you can go to the **Global** view in the Rancher UI. Then click **Security > Roles** and go to the **Global** tab. If you click an individual role, you can refer to the **Grant Resources** table to see all of the operations and resources that are permitted by the role.

> **Notes:** 
>
>- Each permission listed above is comprised of multiple individual permissions not listed in the Rancher UI. For a full list of these permissions and the rules they are comprised of, access through the API at `/v3/globalRoles`.
>- When viewing the resources associated with default roles created by Rancher, if there are multiple Kuberenetes API resources on one line item, the resource will have `(Custom)` appended to it. These are not custom resources but just an indication that there are multiple Kubernetes API resources as one resource.

### Configuring Default Global Permissions

If you want to restrict the default permissions for new users, you can remove the `user` permission as default role and then assign multiple individual permissions as default instead. Conversely, you can also add administrative permissions on top of a set of other standard permissions.

>**Note:** Default roles are only assigned to users added from an external authentication provider. For local users, you must explicitly assign global permissions when adding a user to Rancher. You can customize these global permissions when adding the user.

To change the default global permissions that are assigned to external users upon their first log in, follow these steps:

1. From the **Global** view, select **Security > Roles** from the main menu. Make sure the **Global** tab is selected.

1. Find the permissions set that you want to add or remove as a default. Then edit the permission by selecting **Ellipsis > Edit**.

1. If you want to add the permission as a default, Select **Yes: Default role for new users** and then click **Save**.

1. If you want to remove a default permission, edit the permission and select **No** from **New User Default**.

<<<<<<< HEAD
**Result:** The default global permissions are configured based on your changes. Permissions assigned to new users display a check in the **New User Default** column.
=======
**Result:** The default global permissions are configured based on your changes. Permissions assigned to new users display a check in the **New User Default** column.

### Configuring Global Permissions for Individual Users

To configure permission for a user,

1. Go to the **Users** tab.

1. On this page, go to the user whose access level you want to change and click **Ellipsis (...) > Edit.**

1. In the **Global Permissions** section, click **Custom.**

1. Check the boxes for each subset of permissions you want the user to have access to.

1. Click **Save.**

> **Result:** The user's global permissions have been updated.

>>>>>>> Update and clarify docs on global and cluster permissions
