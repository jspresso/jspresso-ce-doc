Reference for Workspace hierarchy
=================================

Workspace
---------

-   **Full name** : ``

-   **Super-type** : `AbstractPropertyChangeCapable`

-   **Sub-types** : ``

A workspace is an group of functional application modules. You may decide arbitrarily how to group modules into workspaces but a good approach might be to design the workspaces based on roles (i.e. business activities). This helps to clearly separates tasks-unrelated modules and eases authorization management since a workspace can be granted or forbidden as a whole by Jspresso security. Workspaces might be graphically represented differently depending on the UI technology used. For instance, the Swing and ULC channels use a MDI UI in which each workspace is represented as an internal frame (document). On the other hand, Flex and qooxdoo channels represent workspaces stacked in an accordion. Whatever the graphical representation is, there is at most one workspace active at a time for a user session - either the active (focused) internal frame or the expanded accordion section.

<table>
<caption>Workspace properties</caption>
<colgroup>
<col width="33%" />
<col width="66%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Property</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>description</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the key used to translate actual internationalized workspace description. The resulting translation will generally be leveraged as a toolTip on the UI side but its use may be extended for online help.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>grantedRoles</strong></p>
<p><code>Collection​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Assigns the roles that are authorized to start this workspace. It supports &quot;<strong>!</strong>&quot; prefix to negate the role(s). Whenever the user is not granted sufficient privileges, the workspace is not installed at all in the application frame. Setting the collection of granted roles to {@code null} (default value) disables role based authorization on this workspace.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>headerDescription</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the key used to translate actual internationalized workspace header description. The resulting translation will generally be leveraged as a text header on the UI side.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>i18nHeaderDescription</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets i 18 n header description.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>iconImageURL</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the icon image URL of this workspace. Supported URL protocols include :</p>
<ul>
<li><p>all JVM supported protocols</p></li>
<li><p>the <strong>jar:/</strong> pseudo URL protocol</p></li>
<li><p>the <strong>classpath:/</strong> pseudo URL protocol</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconPreferredHeight</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>Sets the icon preferred width.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>iconPreferredWidth</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>Sets the icon preferred width.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconProvider</strong></p>
<p><code></code></p></td>
<td align="left"><p>Since a workspace is represented as a tree view of modules, this property can be used to customize an icon image URL provider on the created tree view (see {@code BasicTreeViewDescriptor.iconImageURLProvider}). However, the workspace built-in icon image URL provider ( {@code WorkspaceIconImageURLProvider}) will setup sensible defaults so that it unlikely has to be changed.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>itemSelectionAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the action to be installed as item selection action on the rendered module tree view - see {@code BasicTreeViewDescriptor.itemSelectionAction}. The configured action will then be executed each time a module selection changes in the workspace.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>modules</strong></p>
<p><code>List​&lt;​​&gt;​</code></p></td>
<td align="left"><p>Installs a list of module(s) into this workspace. Each module may own sub-modules that form a (potentially complex and dynamic) hierarchy, that is visually rendered as a tree view.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the key used to translate actual internationalized workspace name. The resulting translation will be leveraged as the workspace label on the UI side.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>permId</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the permanent identifier to this application element. Permanent identifiers are used by different framework parts, like dynamic security or record/replay controllers to uniquely identify an application element. Permanent identifiers are generated by the SJS build based on the element id but must be explicitly set if Spring XML is used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>startupAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures an action to be executed the first time the workspace is &quot;started&quot; by the user. The action will execute in the context of the workspace but with no specific module selected. It will help initializing workspace values, notify user, ...</p></td>
</tr>
</tbody>
</table>

MobileWorkspace
---------------

-   **Full name** : ``

-   **Super-type** : ``

A workspace is an group of functional application modules. You may decide arbitrarily how to group modules into workspaces but a good approach might be to design the workspaces based on roles (i.e. business activities). This helps to clearly separates tasks-unrelated modules and eases authorization management since a workspace can be granted or forbidden as a whole by Jspresso security.

Workspaces might be graphically represented differently depending on the UI technology used. For instance, the Swing and ULC channels use a MDI UI in which each workspace is represented as an internal frame (document). On the other hand, Flex and qooxdoo channels represent workspaces stacked in an accordion. Whatever the graphical representation is, there is at most one workspace active at a time for a user session - either the active (focused) internal frame or the expanded accordion section.

<table>
<caption>MobileWorkspace properties</caption>
<colgroup>
<col width="33%" />
<col width="66%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Property</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>


