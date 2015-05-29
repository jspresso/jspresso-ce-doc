Reference for ActionMap hierarchy
=================================

ActionMap
---------

-   **Full name** : ``

An action map is used to structure a set of actions. The actions are not
directly registered but are placed into action lists that in turn are
assigned to the action map. Action maps can be merged together, i.e. an
action map can have multiple parent action maps. In that case, Action
lists that have the same name are merged together. The way action maps
are rendered depends on the place where they are declared. For instance
an action map that is assigned to a view might be rendered as a toolbar
with each action list separated into its own group. On the other hand,
an action map declared on the frontend controller might be represented
as a menu bar on the main application frame.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **actionLists**          | Assigns the action lists that are directly owned |
|                          | by this action map. The action lists that will   |
| `List​<​​>​`             | actually be rendered will be the merge of the    |
|                          | directly owned action lists and of the parent    |
|                          | action maps. Action lists that have the same     |
|                          | name are merged together and into a merged       |
|                          | action list, local actions will replace parent   |
|                          | actions with the same name.                      |
+--------------------------+--------------------------------------------------+
| **grantedRoles**         | Assigns the roles that are authorized to use     |
|                          | this action map. It supports "**!**" prefix to   |
| `Collection​<​String​>​` | negate the role(s). Whenever the user is not     |
|                          | granted sufficient privileges, the action map is |
|                          | simply not displayed at runtime. Setting the     |
|                          | collection of granted roles to {@code null}      |
|                          | (default value) disables role based              |
|                          | authorization, then access is granted to anyone. |
+--------------------------+--------------------------------------------------+
| **parentActionMaps**     | Assigns the parent action maps. The action lists |
|                          | that will actually be rendered will be the merge |
| `List​<​​>​`             | of the directly owned action lists and of the    |
|                          | parent action maps. Action lists that have the   |
|                          | same name are merged together and into a merged  |
|                          | action list, local actions will replace parent   |
|                          | actions with the same name.                      |
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
| **renderingOptions**     | Indicates how the actions should be rendered.    |
|                          | This is either a value of the {@code             |
| ``                       | ERenderingOptions} enum or its equivalent string |
|                          | representation :                                 |
|                          |                                                  |
|                          | -   {@code LABEL\_ICON} for label and icon       |
|                          |                                                  |
|                          | -   {@code LABEL} for label only                 |
|                          |                                                  |
|                          | -   {@code ICON} for icon only.                  |
|                          |                                                  |
|                          | Default value is {@code null}, i.e. determined   |
|                          | from outside, e.g. the view factory.             |
+--------------------------+--------------------------------------------------+

: ActionMap properties

