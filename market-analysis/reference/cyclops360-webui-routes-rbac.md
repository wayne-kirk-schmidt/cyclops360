# CyclOps360: Web Admin UI Routes and RBAC Design Initial

## Web Admin Route Structure

### Public Access & Entry

```
/landing
/landing/signup
/landing/signin
/landing/contact
```

### Core Platform Modules (with RBAC subroutes)

```
/dashboard
/dashboard/viewer
/dashboard/editor
/dashboard/admin

/discovery
/discovery/viewer
/discovery/editor
/discovery/admin

/topology
/topology/viewer
/topology/editor
/topology/admin

/cmdb
/cmdb/viewer
/cmdb/editor
/cmdb/admin

/snapshots
/snapshots/viewer
/snapshots/editor
/snapshots/admin

/alerts
/alerts/viewer
/alerts/editor
/alerts/admin

/automation
/automation/viewer
/automation/editor
/automation/admin

/response
/response/viewer
/response/editor
/response/admin

/events
/events/viewer
/events/editor
/events/admin
```

### User Management and Settings

```
/user
/user/settings
/user/account
/user/history
```

## Role-Based Access Control (RBAC)

CyclOps360 defines three user roles:

| Role   | Access Level                   |
| ------ | ------------------------------ |
| viewer | Read-only access               |
| editor | Power user, limited actions    |
| admin  | Full control and configuration |

Each module supports these access levels via route segmentation (`/viewer`, `/editor`, `/admin`).

## Route Design Principles

* All modules route through a top-level entry (e.g., `/cmdb`) that links to its role-based subroutes
* `/user/settings` covers all preferences and account configuration
* `/user` namespace is reserved for future expansions (e.g., `/user/roles`, `/user/security`)
* `/automation` and `/response` are distinct:

  * `/automation`: proactive workflows
  * `/response`: reactive actions and playbooks

