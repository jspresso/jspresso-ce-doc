Reference for Workspace hierarchy
=================================

Workspace
---------

-   **Full name** : ``

-   **Super-type** : `AbstractPropertyChangeCapable`

-   **Sub-types** : ``

A workspace is an group of functional application modules. You may
decide arbitrarily how to group modules into workspaces but a good
approach might be to design the workspaces based on roles (i.e. business
activities). This helps to clearly separates tasks-unrelated modules and
eases authorization management since a workspace can be granted or
forbidden as a whole by Jspresso security. Workspaces might be
graphically represented differently depending on the UI technology used.
For instance, the Swing and ULC channels use a MDI UI in which each
workspace is represented as an internal frame (document). On the other
hand, Flex and qooxdoo channels represent workspaces stacked in an
accordion. Whatever the graphical representation is, there is at most
one workspace active at a time for a user session - either the active
(focused) internal frame or the expanded accordion section.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **description**          | Configures the key used to translate actual      |
|                          | internationalized workspace description. The     |
| `String`                 | resulting translation will generally be          |
|                          | leveraged as a toolTip on the UI side but its    |
|                          | use may be extended for online help.             |
+--------------------------+--------------------------------------------------+
| **grantedRoles**         | Assigns the roles that are authorized to start   |
|                          | this workspace. It supports "**!**" prefix to    |
| `Collection​<​String​>​` | negate the role(s). Whenever the user is not     |
|                          | granted sufficient privileges, the workspace is  |
|                          | not installed at all in the application frame.   |
|                          | Setting the collection of granted roles to       |
|                          | {@code null} (default value) disables role based |
|                          | authorization on this workspace.                 |
+--------------------------+--------------------------------------------------+
| **headerDescription**    | Configures the key used to translate actual      |
|                          | internationalized workspace header description.  |
| `String`                 | The resulting translation will generally be      |
|                          | leveraged as a text header on the UI side.       |
+--------------------------+--------------------------------------------------+
| **i18nHeaderDescription* | Sets i 18 n header description.                  |
| *                        |                                                  |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **iconImageURL**         | Sets the icon image URL of this workspace.       |
|                          | Supported URL protocols include :                |
| `String`                 |                                                  |
|                          | -   all JVM supported protocols                  |
|                          |                                                  |
|                          | -   the **jar:/** pseudo URL protocol            |
|                          |                                                  |
|                          | -   the **classpath:/** pseudo URL protocol      |
+--------------------------+--------------------------------------------------+
| **iconPreferredHeight**  | Sets the icon preferred width.                   |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **iconPreferredWidth**   | Sets the icon preferred width.                   |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **iconProvider**         | Since a workspace is represented as a tree view  |
|                          | of modules, this property can be used to         |
| ``                       | customize an icon image URL provider on the      |
|                          | created tree view (see {@code                    |
|                          | BasicTreeViewDescriptor.iconImageURLProvider}).  |
|                          | However, the workspace built-in icon image URL   |
|                          | provider ( {@code                                |
|                          | WorkspaceIconImageURLProvider}) will setup       |
|                          | sensible defaults so that it unlikely has to be  |
|                          | changed.                                         |
+--------------------------+--------------------------------------------------+
| **itemSelectionAction**  | Configures the action to be installed as item    |
|                          | selection action on the rendered module tree     |
| ``                       | view - see {@code                                |
|                          | BasicTreeViewDescriptor.itemSelectionAction}.    |
|                          | The configured action will then be executed each |
|                          | time a module selection changes in the           |
|                          | workspace.                                       |
+--------------------------+--------------------------------------------------+
| **modules**              | Installs a list of module(s) into this           |
|                          | workspace. Each module may own sub-modules that  |
| `List​<​​>​`             | form a (potentially complex and dynamic)         |
|                          | hierarchy, that is visually rendered as a tree   |
|                          | view.                                            |
+--------------------------+--------------------------------------------------+
| **name**                 | Configures the key used to translate actual      |
|                          | internationalized workspace name. The resulting  |
| `String`                 | translation will be leveraged as the workspace   |
|                          | label on the UI side.                            |
+--------------------------+--------------------------------------------------+
| **permId**               | Sets the permanent identifier to this            |
|                          | application element. Permanent identifiers are   |
| `String`                 | used by different framework parts, like dynamic  |
|                          | security or record/replay controllers to         |
|                          | uniquely identify an application element.        |
|                          | Permanent identifiers are generated by the SJS   |
|                          | build based on the element id but must be        |
|                          | explicitly set if Spring XML is used.            |
+--------------------------+--------------------------------------------------+
| **startupAction**        | Configures an action to be executed the first    |
|                          | time the workspace is "started" by the user. The |
| ``                       | action will execute in the context of the        |
|                          | workspace but with no specific module selected.  |
|                          | It will help initializing workspace values,      |
|                          | notify user, ...                                 |
+--------------------------+--------------------------------------------------+

: Workspace properties

MobileWorkspace
---------------

-   **Full name** : ``

-   **Super-type** : ``

A workspace is an group of functional application modules. You may
decide arbitrarily how to group modules into workspaces but a good
approach might be to design the workspaces based on roles (i.e. business
activities). This helps to clearly separates tasks-unrelated modules and
eases authorization management since a workspace can be granted or
forbidden as a whole by Jspresso security.

Workspaces might be graphically represented differently depending on the
UI technology used. For instance, the Swing and ULC channels use a MDI
UI in which each workspace is represented as an internal frame
(document). On the other hand, Flex and qooxdoo channels represent
workspaces stacked in an accordion. Whatever the graphical
representation is, there is at most one workspace active at a time for a
user session - either the active (focused) internal frame or the
expanded accordion section.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : MobileWorkspace properties


