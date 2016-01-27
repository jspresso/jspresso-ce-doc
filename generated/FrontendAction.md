## FrontendAction

#### <a name="org.jspresso.framework.application.frontend.action.FrontendAction"></a>FrontendAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.FrontendAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/FrontendAction.html)
+ **Super-type** : [`AbstractAction`](#org.jspresso.framework.application.action.AbstractAction)
+ **Sub-types** : [`AbstractChartAction`](#org.jspresso.framework.application.charting.frontend.action.AbstractChartAction), [`AbstractEditComponentAction`](#org.jspresso.framework.application.frontend.action.std.AbstractEditComponentAction), [`AbstractMessageAction`](#org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction), [`AbstractModuleDirtyStateAction`](#org.jspresso.framework.application.backend.action.module.AbstractModuleDirtyStateAction), [`AbstractReportAction`](#org.jspresso.framework.application.printing.frontend.action.AbstractReportAction), [`ActionParamToSelectedModelAction`](#org.jspresso.framework.application.frontend.action.ActionParamToSelectedModelAction), [`AddBeanAsSubModuleFrontAction`](#org.jspresso.framework.application.frontend.action.AddBeanAsSubModuleFrontAction), [`AddCollectionToMasterAction`](#org.jspresso.framework.application.frontend.action.std.AddCollectionToMasterAction), [`AddPageAction`](#org.jspresso.framework.application.frontend.action.std.mobile.AddPageAction), [`BinaryPropertyInfoAction`](#org.jspresso.framework.application.frontend.action.std.BinaryPropertyInfoAction), [`ChooseActionAction`](#org.jspresso.framework.application.frontend.action.flow.ChooseActionAction), [`ChooseComponentAction`](#org.jspresso.framework.application.frontend.action.lov.ChooseComponentAction), [`CloseDialogAction`](#org.jspresso.framework.application.frontend.action.CloseDialogAction), [`CreateEntityFromLovPersistAction`](#org.jspresso.framework.application.frontend.action.lov.CreateEntityFromLovPersistAction), [`DisplayNextPinnedModuleAction`](#org.jspresso.framework.application.frontend.action.module.DisplayNextPinnedModuleAction), [`DisplayPreviousPinnedModuleAction`](#org.jspresso.framework.application.frontend.action.module.DisplayPreviousPinnedModuleAction), [`DisplayUrlAction`](#org.jspresso.framework.application.frontend.action.std.DisplayUrlAction), [`EditSelectionAction`](#org.jspresso.framework.application.frontend.action.EditSelectionAction), [`ExecuteActionAction`](#org.jspresso.framework.application.frontend.action.std.ExecuteActionAction), [`ExitAction`](#org.jspresso.framework.application.frontend.action.workspace.ExitAction), [`ListApplicationElementsAction`](#org.jspresso.framework.application.frontend.action.controller.ListApplicationElementsAction), [`LoginAction`](#org.jspresso.framework.application.frontend.action.security.LoginAction), [`LovAction`](#org.jspresso.framework.application.frontend.action.lov.LovAction), [`ModalDialogAction`](#org.jspresso.framework.application.frontend.action.ModalDialogAction), [`ModuleRestartAction`](#org.jspresso.framework.application.frontend.action.module.ModuleRestartAction), [`ModuleSelectionAction`](#org.jspresso.framework.application.frontend.action.module.ModuleSelectionAction), [`OkChooseComponentAction`](#org.jspresso.framework.application.frontend.action.lov.OkChooseComponentAction), [`OkLovAction`](#org.jspresso.framework.application.frontend.action.lov.OkLovAction), [`PageOffsetAction`](#org.jspresso.framework.application.frontend.action.std.PageOffsetAction), [`ParentModuleConnectorSelectionAction`](#org.jspresso.framework.application.frontend.action.module.ParentModuleConnectorSelectionAction), [`PrintAction`](#org.jspresso.framework.application.printing.frontend.action.PrintAction), [`SaveModuleObjectFrontAction`](#org.jspresso.framework.application.frontend.action.module.SaveModuleObjectFrontAction), [`SelectedModelToActionParamAction`](#org.jspresso.framework.application.frontend.action.SelectedModelToActionParamAction), [`SetConnectorValueAction`](#org.jspresso.framework.application.frontend.action.std.SetConnectorValueAction), [`TransferToClipboardAction`](#org.jspresso.framework.application.frontend.action.std.TransferToClipboardAction), [`EditSelectedComponentAction.UowRollbackerAction`](#org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction.UowRollbackerAction), [`WizardAction`](#org.jspresso.framework.application.frontend.action.wizard.WizardAction), [`WorkspaceSelectionAction`](#org.jspresso.framework.application.frontend.action.workspace.WorkspaceSelectionAction)



This is the base class for frontend actions. To get a better understanding of
 how actions are organized in Jspresso, please refer to
 <code>AbstractAction</code> documentation.
 <p>
 This base class allows for visual (name, icon, toolTip) as well as
 accessibility (accelerator, mnemonic shortcuts) and actionability (using
 gates) parametrization.
 <p>
 A frontend action is to be executed by the frontend controller in the context
 of the UI. It can thus access the view structure, interact visually with the
 user, and so on. A frontend action can chain a backend action but the
 opposite will be prevented.



<table>
<caption>FrontendAction properties</caption>
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
<td align="left"><p><strong>acceleratorAsString</strong></p><p><code>String</code></p></td>
<td><p>Configures a keyboard accelerator shortcut on this action. Support of this
 feature depends on the UI execution platform. The syntax used consists of
 listing keys that should be pressed to trigger the action, i.e.
 <code>alt d</code> or <code>ctrl c</code>. This is the syntax supported by
 the <code>javax.swing.KeyStroke#getKeyStroke(...)</code> swing static
 method.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>actionabilityGates</strong></p><p><code>Collection&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gate/IGate.html">IGate</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns a collection of gates to determine action <i>actionability</i>. An
 action will be considered actionable (enabled) if and only if all gates are
 open. This mechanism is mainly used for dynamic UI authorization based on
 model state, e.g. a validated invoice should not be validated twice.
 <p>
 Action assigned gates will be cloned for each concrete action instance
 created and bound to its respective UI component (usually a button). So
 basically, each action instance will have its own, unshared collection of
 actionability gates.
 <p>
 Jspresso provides a useful set of gate types, like the binary property gate
 that open/close based on the value of a boolean property of the view model
 the action is installed to.
 <p>
 By default, frontend actions are assigned a generic gate that closes
 (disables the action) when the view is not assigned any model.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>collectionBased</strong></p><p><code>boolean</code></p></td>
<td><p>Declares the action as working on a collection of objects. Collection based
 actions will typically be installed on selectable views (table, list, tree)
 and will be enabled only when the view selection is not empty (a default
 gate is installed for this purpose). Moreover, model gates that are
 configured on collection based actions take their model from the view
 selected components instead of the view model itself. In case of
 multi-selection enabled UI views, the actionability gates will actually
 open if and only if their opening condition is met for all the selected
 items.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>description</strong></p><p><code>String</code></p></td>
<td><p>Sets the key used to compute the internationalized description of the
 action. The translated description is then usually used as toolTip for the
 action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>icon</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/Icon.html">Icon</a></code></p></td>
<td><p>Sets the icon.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconImageURL</strong></p><p><code>String</code></p></td>
<td><p>Sets the icon image URL used to decorate the action UI component peer.
 <p>
 Supported URL protocols include :
 <ul>
 <li>all JVM supported protocols</li>
 <li>the <b>jar:/</b> pseudo URL protocol</li>
 <li>the <b>classpath:/</b> pseudo URL protocol</li>
 </ul></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>iconPreferredHeight</strong></p><p><code>int</code></p></td>
<td><p>Sets the icon preferred height.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconPreferredWidth</strong></p><p><code>int</code></p></td>
<td><p>Sets the icon preferred width.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>mnemonicAsString</strong></p><p><code>String</code></p></td>
<td><p>Configures the mnemonic key used for this action. Support of this feature
 depends on the UI execution platform. Mnemonics are typically used in menu
 and menu items.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>multiSelectionEnabled</strong></p><p><code>boolean</code></p></td>
<td><p>Declares the action as being able to run on a collection containing more
 than 1 element. A multiSelectionEnabled = false action will be disabled
 when the selection contains no or more than one element.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>Sets the key used to compute the internationalized name of the action. The
 translated name is then usually used as label for the action (button label,
 menu label, ...).</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>styleName</strong></p><p><code>String</code></p></td>
<td><p>Assigns the style name to use for this view. The way it is actually
 leveraged depends on the UI channel. It will generally be mapped to some
 sort of CSS style name.
 <p>
 Default value is <code>null</code>, meaning that a default style is used.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.charting.frontend.action.AbstractChartAction"></a>AbstractChartAction

+ **Full name** : [`org.jspresso.framework.application.charting.frontend.action.AbstractChartAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/charting/frontend/action/AbstractChartAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`DisplayChartAction`](#org.jspresso.framework.application.charting.frontend.action.server.DisplayChartAction)



This is the abstract base class for <i>Fusioncharts</i> (flash based charting
 library) display actions. It holds several common properties that are
 independent from the actual, concrete, implementations.



<table>
<caption>AbstractChartAction properties</caption>
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
<td align="left"><p><strong>actions</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures a list of actions to install in the chart modal dialog.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>chartDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/charting/descriptor/IChartDescriptor.html">IChart&#x200B;Descriptor</a></code></p></td>
<td><p>This property describes the chart to compute and display. A chart
 descriptor is a simple data structure that provides :
 <ul>
 <li>the URL of the chart SWF archive (can be loaded by the classloader
 using a classpath pseudo URL)</li>
 <li>the title of the chart</li>
 <li>the width/height of the chart area</li>
 <li>an abstract method to implement in order to compute the chart XML data</li>
 </ul></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>jdbcTemplate</strong></p><p><code>Jdbc&#x200B;Template</code></p></td>
<td><p>Configures the JDBC template to be used by the chart to compute its data.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.charting.frontend.action.server.DisplayChartAction"></a>DisplayChartAction

+ **Full name** : [`org.jspresso.framework.application.charting.frontend.action.server.DisplayChartAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/charting/frontend/action/server/DisplayChartAction.html)
+ **Super-type** : [`AbstractChartAction`](#org.jspresso.framework.application.charting.frontend.action.AbstractChartAction)



This is the concrete implementation of the Fusionchart display action. This
 action is specialized by UI channel, i.e. server based UI channels (Ajax,
 Flex, ULC) will use <i><code>server</code></i>
 <code>.DisplayChartAction</code> whereas standalone UI channels (Swing) will
 use <i><code>standalone</code></i><code>.DisplayChartAction</code>.



<table>
<caption>DisplayChartAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.AbstractEditComponentAction"></a>AbstractEditComponentAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.AbstractEditComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/AbstractEditComponentAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction), [`EditSelectedComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction)



This action serves as a base class for actions that pop-pup a dialog to edit
 a component.



<table>
<caption>AbstractEditComponentAction properties</caption>
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
<td align="left"><p><strong>complementaryActions</strong></p><p><code>List&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Installs a list of complementary actions to install between the ok and
 cancel actions.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>viewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the view descriptor to be used to create the component editing
 view that will be installed in the dialog.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.EditComponentAction"></a>EditComponentAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.EditComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/EditComponentAction.html)
+ **Super-type** : [`AbstractEditComponentAction`](#org.jspresso.framework.application.frontend.action.std.AbstractEditComponentAction)
+ **Sub-types** : [`ChangePasswordAction`](#org.jspresso.framework.application.frontend.action.security.ChangePasswordAction), [`CreateEntityFromLovAction`](#org.jspresso.framework.application.frontend.action.lov.CreateEntityFromLovAction), [`EditBackendControllerAction`](#org.jspresso.framework.application.frontend.action.controller.EditBackendControllerAction), [`EditFrontendControllerAction`](#org.jspresso.framework.application.frontend.action.controller.EditFrontendControllerAction), [`EditReportParametersAction`](#org.jspresso.framework.application.printing.frontend.action.EditReportParametersAction), [`MobileEditComponentAction`](#org.jspresso.framework.application.frontend.action.std.mobile.MobileEditComponentAction)



This action pulls a model out of the context (action parameter or selected
 model if action parameter is not filled), creates a view, binds it on the
 model and prepares for chaining with a modal dialog action to pop-up the
 result. The translated name of the action, whenever not empty, will be used
 as the dialog title. If the context extracted model is a collection, the
 first element of the collection is used. Custom actions (
 <code>okAction</code> and <code>cancelAction</code>) can be configured to
 take care of user decision when closing the dialog.



<table>
<caption>EditComponentAction properties</caption>
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
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action to be installed in the dialog when the user cancels
 the component edition.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>okAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action to be installed in the dialog when the user confirms
 the component edition.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.security.ChangePasswordAction"></a>ChangePasswordAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.security.ChangePasswordAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/security/ChangePasswordAction.html)
+ **Super-type** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction)



This is the frontend action to initiate the logged-in user password change.
 It will install a form view with a custom component designed to host :
 <ol>
 <li>the current password</li>
 <li>the new password</li>
 <li>the confirmation for the new password</li>
 </ol>
 This action must be combined (setting <code>okAction</code>) with a concrete
 subclass of backend <code>AbstractChangePasswordAction</code> that performs
 the actual password change depending on the authentication backend. Jspresso
 offers two concrete implementations :
 <ul>
 <li><code>LdapChangePasswordAction</code> for LDAP based authentication
 backend</li>
 <li><code>DatabaseChangePasswordAction</code> for JDBC based authentication
 backend</li>
 </ul>



<table>
<caption>ChangePasswordAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.CreateEntityFromLovAction"></a>CreateEntityFromLovAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.CreateEntityFromLovAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/CreateEntityFromLovAction.html)
+ **Super-type** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction)



The type Create entity from lov action.



<table>
<caption>CreateEntityFromLovAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.controller.EditBackendControllerAction"></a>EditBackendControllerAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.controller.EditBackendControllerAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/controller/EditBackendControllerAction.html)
+ **Super-type** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction)



This is a frontend action to display a view backed by the session backend
 controller itself. It is used, for instance, to display the running
 asynchronous actions.



<table>
<caption>EditBackendControllerAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.controller.EditFrontendControllerAction"></a>EditFrontendControllerAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.controller.EditFrontendControllerAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/controller/EditFrontendControllerAction.html)
+ **Super-type** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction)



This is a frontend action to display a view backed by the session backend
 controller itself. It is used, for instance, to display the running
 asynchronous actions.



<table>
<caption>EditFrontendControllerAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.printing.frontend.action.EditReportParametersAction"></a>EditReportParametersAction

+ **Full name** : [`org.jspresso.framework.application.printing.frontend.action.EditReportParametersAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/frontend/action/EditReportParametersAction.html)
+ **Super-type** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction)



This action takes a report (<code>IReport</code>) from the context (
 <code>REPORT_ACTION_PARAM</code> key) and pops-up a form to allow for the
 report input parameters customization.



<table>
<caption>EditReportParametersAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.mobile.MobileEditComponentAction"></a>MobileEditComponentAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.mobile.MobileEditComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/mobile/MobileEditComponentAction.html)
+ **Super-type** : [`EditComponentAction`](#org.jspresso.framework.application.frontend.action.std.EditComponentAction)



This is the mobile version of the edit component action.
 <code>okAction</code> and <code>cancelAction</code>) are added as page actions instead of dialog ones.



<table>
<caption>MobileEditComponentAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction"></a>EditSelectedComponentAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/EditSelectedComponentAction.html)
+ **Super-type** : [`AbstractEditComponentAction`](#org.jspresso.framework.application.frontend.action.std.AbstractEditComponentAction)



This action should be installed on collection views. It takes the selected
 component and edit it in a modal dialog. Editing happens in a &quot;Unit of
 Work&quot; meaning that it can be rolled-back when canceling.



<table>
<caption>EditSelectedComponentAction properties</caption>
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
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/FrontendAction.html">Frontend&#x200B;Action</a>&#x200B;&lt;&#x200B;E&#x200B;,F&#x200B;,G&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets the cancelAction.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>okAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/FrontendAction.html">Frontend&#x200B;Action</a>&#x200B;&lt;&#x200B;E&#x200B;,F&#x200B;,G&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets the okAction.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction"></a>AbstractMessageAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/AbstractMessageAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`InfoAction`](#org.jspresso.framework.application.frontend.action.flow.InfoAction), [`OkCancelAction`](#org.jspresso.framework.application.frontend.action.flow.OkCancelAction), [`YesNoAction`](#org.jspresso.framework.application.frontend.action.flow.YesNoAction), [`YesNoCancelAction`](#org.jspresso.framework.application.frontend.action.flow.YesNoCancelAction)



This is the base class for all UI message based communication actions. This
 type of action generally opens a modal dialog to display an informational
 message, ask a question, and so on. It takes the message from the action
 context parameter and supports basic HTML formatting. In order for the
 message to be interpreted as HTML, it must be surrounded by
 <code>&lt;HTML&gt;</code> tags.



<table>
<caption>AbstractMessageAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.InfoAction"></a>InfoAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.InfoAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/InfoAction.html)
+ **Super-type** : [`AbstractMessageAction`](#org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction)
+ **Sub-types** : [`StaticInfoAction`](#org.jspresso.framework.application.frontend.action.flow.StaticInfoAction)



This action pops-up an informational message to the user.



<table>
<caption>InfoAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.StaticInfoAction"></a>StaticInfoAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.StaticInfoAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/StaticInfoAction.html)
+ **Super-type** : [`InfoAction`](#org.jspresso.framework.application.frontend.action.flow.InfoAction)



This action pops-up an informational message to the user. The message,
 instead of being extracted out of the context, is parametrized statically
 into the action through its internationalization key.



<table>
<caption>StaticInfoAction properties</caption>
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
<td align="left"><p><strong>messageCode</strong></p><p><code>String</code></p></td>
<td><p>Configures the i18n key used to translate the message that is to be
 displayed to the user. When the action executes, the statically configured
 message is first translated, then placed into the action context to be
 popped-up.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.OkCancelAction"></a>OkCancelAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.OkCancelAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/OkCancelAction.html)
+ **Super-type** : [`AbstractMessageAction`](#org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction)
+ **Sub-types** : [`StaticOkCancelAction`](#org.jspresso.framework.application.frontend.action.flow.StaticOkCancelAction)



This action pops-up an Ok - Cancel confirmation option. Depending on user
 answer, another action is triggered. The Ok - Cancel alternative actions are
 parametrized statically.



<table>
<caption>OkCancelAction properties</caption>
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
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user cancels the option.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>okAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user confirms the option.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.StaticOkCancelAction"></a>StaticOkCancelAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.StaticOkCancelAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/StaticOkCancelAction.html)
+ **Super-type** : [`OkCancelAction`](#org.jspresso.framework.application.frontend.action.flow.OkCancelAction)



This action pops-up an Ok - Cancel confirmation option. The message, instead
 of being extracted out of the context, is parametrized statically into the
 action through its internationalization key.



<table>
<caption>StaticOkCancelAction properties</caption>
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
<td align="left"><p><strong>messageCode</strong></p><p><code>String</code></p></td>
<td><p>Configures the i18n key used to translate the message that is to be
 displayed to the user. When the action executes, the statically configured
 message is first translated, then placed into the action context to be
 popped-up.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.YesNoAction"></a>YesNoAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.YesNoAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/YesNoAction.html)
+ **Super-type** : [`AbstractMessageAction`](#org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction)
+ **Sub-types** : [`StaticYesNoAction`](#org.jspresso.framework.application.frontend.action.flow.StaticYesNoAction)



This action pops-up a binary question. Depending on user answer, another
 action is triggered. The Yes - No alternative actions are parametrized
 statically.



<table>
<caption>YesNoAction properties</caption>
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
<td align="left"><p><strong>noAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user answers negatively to the
 question.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>yesAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user answers positively to the
 question.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.StaticYesNoAction"></a>StaticYesNoAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.StaticYesNoAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/StaticYesNoAction.html)
+ **Super-type** : [`YesNoAction`](#org.jspresso.framework.application.frontend.action.flow.YesNoAction)



This action pops-up a binary question. The message, instead of being
 extracted out of the context, is parametrized statically into the action
 through its internationalization key.



<table>
<caption>StaticYesNoAction properties</caption>
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
<td align="left"><p><strong>messageCode</strong></p><p><code>String</code></p></td>
<td><p>Configures the i18n key used to translate the message that is to be
 displayed to the user. When the action executes, the statically configured
 message is first translated, then placed into the action context to be
 popped-up.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.YesNoCancelAction"></a>YesNoCancelAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.YesNoCancelAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/YesNoCancelAction.html)
+ **Super-type** : [`AbstractMessageAction`](#org.jspresso.framework.application.frontend.action.flow.AbstractMessageAction)
+ **Sub-types** : [`StaticYesNoCancelAction`](#org.jspresso.framework.application.frontend.action.flow.StaticYesNoCancelAction)



This action pops-up a binary question with Cancel option. Depending on user
 answer, another action is triggered. The Yes - No - Cancel alternative
 actions are parametrized statically.



<table>
<caption>YesNoCancelAction properties</caption>
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
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user cancels the option.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>noAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user answers negatively to the
 question.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>yesAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Assigns the action to execute when the user answers positively to the
 question.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.StaticYesNoCancelAction"></a>StaticYesNoCancelAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.StaticYesNoCancelAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/StaticYesNoCancelAction.html)
+ **Super-type** : [`YesNoCancelAction`](#org.jspresso.framework.application.frontend.action.flow.YesNoCancelAction)



This action pops-up a binary question with Cancel option. The message,
 instead of being extracted out of the context, is parametrized statically
 into the action through its internationalization key.



<table>
<caption>StaticYesNoCancelAction properties</caption>
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
<td align="left"><p><strong>messageCode</strong></p><p><code>String</code></p></td>
<td><p>Configures the i18n key used to translate the message that is to be
 displayed to the user. When the action executes, the statically configured
 message is first translated, then placed into the action context to be
 popped-up.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.module.AbstractModuleDirtyStateAction"></a>AbstractModuleDirtyStateAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.AbstractModuleDirtyStateAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/AbstractModuleDirtyStateAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`CheckAllModulesDirtyStateAction`](#org.jspresso.framework.application.backend.action.module.CheckAllModulesDirtyStateAction), [`CheckModuleDirtyStateAction`](#org.jspresso.framework.application.backend.action.module.CheckModuleDirtyStateAction)



This is the base abstract class for actions that are responsible for checking
 module dirty state. <i>Dirty</i> is taken in the sense of an entity needing
 to be flushed to the persistent store. Among modules that are to be checked,
 a collection module is marked dirty if and only if one of its module objects
 is an entity which is dirty. On the other hand, a bean module is marked dirty
 if and only if its (single) module object is an entity and is dirty.



<table>
<caption>AbstractModuleDirtyStateAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.module.CheckAllModulesDirtyStateAction"></a>CheckAllModulesDirtyStateAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.CheckAllModulesDirtyStateAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/CheckAllModulesDirtyStateAction.html)
+ **Super-type** : [`AbstractModuleDirtyStateAction`](#org.jspresso.framework.application.backend.action.module.AbstractModuleDirtyStateAction)



This action recomputes all application modules dirty state. All the
 workspaces are traversed as well as, for each workspace, the whole module
 hierarchy. This action is typically triggered before a user exists the
 application to bring up a notification of potentially lost pending changes.



<table>
<caption>CheckAllModulesDirtyStateAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.module.CheckModuleDirtyStateAction"></a>CheckModuleDirtyStateAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.CheckModuleDirtyStateAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/CheckModuleDirtyStateAction.html)
+ **Super-type** : [`AbstractModuleDirtyStateAction`](#org.jspresso.framework.application.backend.action.module.AbstractModuleDirtyStateAction)



This action recomputes the dirty state of the current selected module. It is
 typically triggered when the user navigates (leaves) out of the module to
 compute a visual notification of a pending change.



<table>
<caption>CheckModuleDirtyStateAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.mobile.AnimateAction"></a>AnimateAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.mobile.AnimateAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/mobile/AnimateAction.html)
+ **Super-type** : `AbstractRemoteAction`



Selects animates current page.



<table>
<caption>AnimateAction properties</caption>
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
<td align="left"><p><strong>animation</strong></p><p><code>String</code></p></td>
<td><p>Sets animation.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>callbackAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Sets callback action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>direction</strong></p><p><code>String</code></p></td>
<td><p>Sets direction.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>duration</strong></p><p><code>int</code></p></td>
<td><p>Sets duration.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>hideView</strong></p><p><code>boolean</code></p></td>
<td><p>Sets hide view.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>reverse</strong></p><p><code>boolean</code></p></td>
<td><p>Sets reverse.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.mobile.BackPageAction"></a>BackPageAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.mobile.BackPageAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/mobile/BackPageAction.html)
+ **Super-type** : `AbstractRemoteAction`



Triggers back navigation of current page.



<table>
<caption>BackPageAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.file.ChooseFileAction"></a>ChooseFileAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.file.ChooseFileAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/file/ChooseFileAction.html)
+ **Super-type** : `AbstractRemoteAction`
+ **Sub-types** : [`OpenFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.OpenFileAction), [`SaveFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.SaveFileAction)



This is the abstract base class for actions dealing with client file system
 operations. It holds several parametrizations that are common to all file
 operations. Please, be aware that these FS actions heavily depend on the UI
 channel, i.e. you have different implementation classes (but registered under
 the same Spring name) for all supported UI technologies. For instance,
 <code>SaveFileAction</code> will have as many implementations as the number
 of supported UIs, each in a specific package :
 <p>
 <code>org.jspresso.framework.application.frontend.action.</code><b>
 <code>[ui]</code></b><code>.file.SaveFileAction</code>



<table>
<caption>ChooseFileAction properties</caption>
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
<td align="left"><p><strong>defaultFileName</strong></p><p><code>String</code></p></td>
<td><p>Configures a default file name to be used whenever a file needs to be
 chosen. Subclasses ma use their specific callback to override this name
 with a more dynamically computed one.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fileFilter</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,List&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the file filters to be used whenever the UI technology supports
 it in the file choosing dialog. Filter file types are a map of descriptions
 keying file extension lists.
 <p>
 For instance, an entry in this map could be :
 <ul>
 <li>key : <code>&quot;images&quot;</code></li>
 <li>value :
 <code>[&quot;.png&quot;,&quot;.jpg&quot;,&quot;.gif&quot;,&quot;.bmp&quot;]</code>
 </li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.file.OpenFileAction"></a>OpenFileAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.file.OpenFileAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/file/OpenFileAction.html)
+ **Super-type** : [`ChooseFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.ChooseFileAction)
+ **Sub-types** : [`OpenFileAsBinaryPropertyAction`](#org.jspresso.framework.application.frontend.action.remote.file.OpenFileAsBinaryPropertyAction)



This action lets the user browse his local file system and choose a file to
 read some content from. What is done with the file content is determined by
 the configured <code>fileOpenCallback</code> instance.



<table>
<caption>OpenFileAction properties</caption>
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
<td align="left"><p><strong>fileOpenCallback</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/file/IFileOpenCallback.html">IFile&#x200B;Open&#x200B;Callback</a></code></p></td>
<td><p>Configures the file open callback instance that will be used to deal with
 the file dialog events. Two methods must be implemented :
 <ul>
 <li>
 <code>fileChosen(InputStream, IActionHandler, Map[String, Object])</code>
 that is called whenever a file has been chosen. The input stream that is
 passed as parameter allows for reading from the chosen file. The developer
 doesn't have to cope with closing the stream.</li>
 <li><code>cancel(IActionHandler, Map[String, Object])</code> that is
 called whenever the file selection is cancelled. It is perfectly legal not
 to do anything.</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.file.OpenFileAsBinaryPropertyAction"></a>OpenFileAsBinaryPropertyAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.file.OpenFileAsBinaryPropertyAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/file/OpenFileAsBinaryPropertyAction.html)
+ **Super-type** : [`OpenFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.OpenFileAction)



This action lets the user browse the local file system and choose a file to
 update the content of a binary property. Files are filtered based on the file
 filter defined in the binary property descriptor. This file action must be
 installed on a property view. A suitable (built-in) file open callback is
 installed upon action instantiation and thus, nothing has to be configured
 for the action to be immediately operational.



<table>
<caption>OpenFileAsBinaryPropertyAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.file.SaveFileAction"></a>SaveFileAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.file.SaveFileAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/file/SaveFileAction.html)
+ **Super-type** : [`ChooseFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.ChooseFileAction)
+ **Sub-types** : [`SaveBinaryPropertyAsFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.SaveBinaryPropertyAsFileAction)



This action lets the user browse his local file system and choose a file to
 write some content to. What is done with the file content is determined by
 the configured <code>fileSaveCallback</code> instance.



<table>
<caption>SaveFileAction properties</caption>
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
<td align="left"><p><strong>contentType</strong></p><p><code>String</code></p></td>
<td><p>Configures the content type to be used whenever the UI technology used
 requires a download. The content type defaults to
 <code>&quot;application/octet-stream&quot;</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fileSaveCallback</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/file/IFileSaveCallback.html">IFile&#x200B;Save&#x200B;Callback</a></code></p></td>
<td><p>Configures the file save callback instance that will be used to deal with
 the file dialog events. Three methods must be implemented :
 <ul>
 <li>
 <code>fileChosen(OutputStream, IActionHandler, Map[String, Object])</code>
 that is called whenever a file has been chosen. The output stream that is
 passed as parameter allows for writing to the chosen file. The developer
 doesn't have to cope with flushing nor closing the stream.</li>
 <li><code>getFileName(Map[String, Object])</code> that is called to
 give a chance top the callback to compute a file name dynamically depending
 on the action context. Whenever the callback returns a <code>null</code> or
 empty file name, the default file name parametrized in the application is
 used.</li>
 <li><code>cancel(IActionHandler, Map[String, Object])</code> that is
 called whenever the file selection is cancelled. It is perfectly legal not
 to do anything.</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.file.SaveBinaryPropertyAsFileAction"></a>SaveBinaryPropertyAsFileAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.file.SaveBinaryPropertyAsFileAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/file/SaveBinaryPropertyAsFileAction.html)
+ **Super-type** : [`SaveFileAction`](#org.jspresso.framework.application.frontend.action.remote.file.SaveFileAction)



This action lets the user browse the local file system and choose a file to
 save the content of a binary property to. Files are filtered based on the
 file filter defined in the binary property descriptor. This file action must
 be installed on a property view. A suitable (built-in) file open callback is
 installed upon action instantiation and thus, nothing has to be configured
 for the action to be immediately operational.



<table>
<caption>SaveBinaryPropertyAsFileAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.mobile.CleanModuleAndGoBackIfTransientAction"></a>CleanModuleAndGoBackIfTransientAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.mobile.CleanModuleAndGoBackIfTransientAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/mobile/CleanModuleAndGoBackIfTransientAction.html)
+ **Super-type** : `AbstractRemoteAction`



Check current selected module object. If it is transient, removes it from the current module and go back.



<table>
<caption>CleanModuleAndGoBackIfTransientAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.printing.frontend.action.remote.DisplayJasperReportAction"></a>DisplayJasperReportAction

+ **Full name** : [`org.jspresso.framework.application.printing.frontend.action.remote.DisplayJasperReportAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/frontend/action/remote/DisplayJasperReportAction.html)
+ **Super-type** : `AbstractRemoteAction`



This action will take a <code>JasperPrint</code> (a processed Jasper report
 instance), produce a PDF output and open a browser window (tab) to display
 it.



<table>
<caption>DisplayJasperReportAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.mobile.EditCurrentPageAction"></a>EditCurrentPageAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.mobile.EditCurrentPageAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/mobile/EditCurrentPageAction.html)
+ **Super-type** : `AbstractRemoteAction`



Triggers editing of current page.



<table>
<caption>EditCurrentPageAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.remote.mobile.NearElementAction"></a>NearElementAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.remote.mobile.NearElementAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/remote/mobile/NearElementAction.html)
+ **Super-type** : `AbstractRemoteAction`



Selects next / previous element.



<table>
<caption>NearElementAction properties</caption>
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
<td align="left"><p><strong>onFailureAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Sets on failure action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>onSuccessAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Sets on success action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>reverse</strong></p><p><code>boolean</code></p></td>
<td><p>Sets reverse.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.printing.frontend.action.AbstractReportAction"></a>AbstractReportAction

+ **Full name** : [`org.jspresso.framework.application.printing.frontend.action.AbstractReportAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/frontend/action/AbstractReportAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`ReportAction`](#org.jspresso.framework.application.printing.frontend.action.ReportAction), [`StaticReportAction`](#org.jspresso.framework.application.printing.frontend.action.StaticReportAction)



Abstract base class for Jasper report actions.



<table>
<caption>AbstractReportAction properties</caption>
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
<td align="left"><p><strong>reportFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/model/IReportFactory.html">IReport&#x200B;Factory</a></code></p></td>
<td><p>Configures the report factory to use. The report factory is responsible for
 creating an <code>IReport</code> (a concrete report instance) from a report
 descriptor (<code>IReportDescriptor</code>).</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.printing.frontend.action.ReportAction"></a>ReportAction

+ **Full name** : [`org.jspresso.framework.application.printing.frontend.action.ReportAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/frontend/action/ReportAction.html)
+ **Super-type** : [`AbstractReportAction`](#org.jspresso.framework.application.printing.frontend.action.AbstractReportAction)



This action allows the user to select a report to generate on the collection
 view where it has been installed. The collection backing the view can either
 be a collection of <code>IReport</code> or <code>IReportDescriptor</code>. In
 the latter situation, the corresponding <code>IReport</code> instances are
 created on the fly using the configured report factory.



<table>
<caption>ReportAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.printing.frontend.action.StaticReportAction"></a>StaticReportAction

+ **Full name** : [`org.jspresso.framework.application.printing.frontend.action.StaticReportAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/frontend/action/StaticReportAction.html)
+ **Super-type** : [`AbstractReportAction`](#org.jspresso.framework.application.printing.frontend.action.AbstractReportAction)



This action generates and displays a report that is statically configured
 through the <code>reportDescriptor</code> parameter. The report context is
 augmented with the identifier of the entity that is selected in the view were
 the action is installed, under the key <code>ENTITY_ID</code>.



<table>
<caption>StaticReportAction properties</caption>
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
<td align="left"><p><strong>reportDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/model/descriptor/IReportDescriptor.html">IReport&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the report to execute.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.ActionParamToSelectedModelAction"></a>ActionParamToSelectedModelAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.ActionParamToSelectedModelAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/ActionParamToSelectedModelAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



A very simple frontend action that uses the puts the context
 action param as selected model.



<table>
<caption>ActionParamToSelectedModelAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.AddBeanAsSubModuleFrontAction"></a>AddBeanAsSubModuleFrontAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.AddBeanAsSubModuleFrontAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/AddBeanAsSubModuleFrontAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action can be installed on any collection view and will take the
 selected elements in the underlying model collection and create a bean module
 out of them.



<table>
<caption>AddBeanAsSubModuleFrontAction properties</caption>
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
<td align="left"><p><strong>childModuleProjectedViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the childModuleProjectedViewDescriptor.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>parentModuleName</strong></p><p><code>String</code></p></td>
<td><p>Sets the parent module where to add components to.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>parentWorkspaceName</strong></p><p><code>String</code></p></td>
<td><p>Sets the WorkspaceName where to add components to.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>referencePath</strong></p><p><code>String</code></p></td>
<td><p>Allows to configure a property path to extract the bean(s) to add from the selected models. If <code>null</code>,
 which is the default value, the selected models are used themselves.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.AddCollectionToMasterAction"></a>AddCollectionToMasterAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.AddCollectionToMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/AddCollectionToMasterAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action is designed to wrap a backend action that will create and add a
 (collection of) component(s) to the model collection of the view it's
 installed on. Its objective is to complete the action context with the
 descriptor of the component (or entity) to be added so that the backend
 action explicitly knows what to create. Moreover, the name, description and
 icon used for the graphical representation are all computed out of the
 configured <code>elementEntityDescriptor</code>.



<table>
<caption>AddCollectionToMasterAction properties</caption>
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
<td align="left"><p><strong>elementEntityDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntity.html">IEntity</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the descriptor of the entities that are to be added by the
 action to the underlying model collection. Setting this property serves
 multiple objectives :
 <ul>
 <li>complete the application context with the
 <code>AddComponentCollectionToMasterAction.ELEMENT_DESCRIPTOR</code> key so
 that the chained backend action knows what type of entity to create.</li>
 <li>customize the name, description and icon used to represent the action
 in the UI. All three are derived from the configured element entity
 descriptor.</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.mobile.AddPageAction"></a>AddPageAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.mobile.AddPageAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/mobile/AddPageAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



A special mobile pagination action that adds a page to the current results.



<table>
<caption>AddPageAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.BinaryPropertyInfoAction"></a>BinaryPropertyInfoAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.BinaryPropertyInfoAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/BinaryPropertyInfoAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action displays information about a binary property content. The
 displayed information mainly consists in the content size. The action must be
 installed on a property view and supports textual and binary properties.



<table>
<caption>BinaryPropertyInfoAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.flow.ChooseActionAction"></a>ChooseActionAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.flow.ChooseActionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/flow/ChooseActionAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action displays a list of frontend actions so that the user can choose
 and launch one of them. This action is meant to be chained with the generic
 <code>ChooseComponentAction</code> so that the action list is actually
 displayed.



<table>
<caption>ChooseActionAction properties</caption>
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
<td align="left"><p><strong>actions</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the list of actions to choose from.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.ChooseComponentAction"></a>ChooseComponentAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.ChooseComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/ChooseComponentAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action takes an arbitrary model collection connector from the action
 context parameter and binds it to a newly created table view. This action is
 meant to be chained to the generic <code>ModalDialogAction</code> so that the
 table is actually popped-up in a dialog. Two actions (<code>okAction</code>
 and <code>cancelAction</code>) can be configured to react to the user
 decision.



<table>
<caption>ChooseComponentAction properties</caption>
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
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action that will be triggered when the user cancels the
 component choice.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>collectionViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ICollectionViewDescriptor.html">ICollection&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the collectionViewDescriptor.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>componentDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets the componentDescriptor.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>okAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action that will be triggered when the user confirms the
 component choice. the chosen component will then be retrieved from the
 selected view item.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.CloseDialogAction"></a>CloseDialogAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.CloseDialogAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/CloseDialogAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`EditSelectedComponentAction.DefaultOkAction`](#org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction.DefaultOkAction)



This is a very generic action that closes (disposes) the currently opened
 dialog. The dialog is actually closed between the <i>wrapped</i> action and
 the <i>next</i> action if and only if the wrapped action succeeds.



<table>
<caption>CloseDialogAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction.DefaultOkAction"></a>EditSelectedComponentAction.DefaultOkAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction.DefaultOkAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/EditSelectedComponentAction/DefaultOkAction.html)
+ **Super-type** : [`CloseDialogAction`](#org.jspresso.framework.application.frontend.action.CloseDialogAction)



Default OK action.



<table>
<caption>EditSelectedComponentAction.DefaultOkAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.CreateEntityFromLovPersistAction"></a>CreateEntityFromLovPersistAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.CreateEntityFromLovPersistAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/CreateEntityFromLovPersistAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



The type Create entity from lov persist action.



<table>
<caption>CreateEntityFromLovPersistAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.module.DisplayNextPinnedModuleAction"></a>DisplayNextPinnedModuleAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.module.DisplayNextPinnedModuleAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/module/DisplayNextPinnedModuleAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action triggers a <i>&quot;forward&quot;</i> navigation in the recorded
 module history. The frontend controller automatically keeps track of the
 traversed modules so that a user can go back and forward his navigation
 history, much like for a web navigation.



<table>
<caption>DisplayNextPinnedModuleAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.module.DisplayPreviousPinnedModuleAction"></a>DisplayPreviousPinnedModuleAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.module.DisplayPreviousPinnedModuleAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/module/DisplayPreviousPinnedModuleAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action triggers a <i>&quot;backward&quot;</i> navigation in the recorded
 module history. The frontend controller automatically keeps track of the
 traversed modules so that a user can go back and forward his navigation
 history, much like for a web navigation.



<table>
<caption>DisplayPreviousPinnedModuleAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.DisplayUrlAction"></a>DisplayUrlAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.DisplayUrlAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/DisplayUrlAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`DisplayStaticUrlAction`](#org.jspresso.framework.application.frontend.action.std.DisplayStaticUrlAction)



This action opens a browser (or a browser tab) targeted at a URL. The actual
 URL is a composition of a static parametrized prefix (<code>baseUrl</code>)
 and a dynamic part taken from the action context parameter.



<table>
<caption>DisplayUrlAction properties</caption>
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
<td align="left"><p><strong>baseUrl</strong></p><p><code>String</code></p></td>
<td><p>Configures the static prefix that is prepended (if not <code>null</code>)
 to the opened URL.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>target</strong></p><p><code>String</code></p></td>
<td><p>Sets the target window.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.DisplayStaticUrlAction"></a>DisplayStaticUrlAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.DisplayStaticUrlAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/DisplayStaticUrlAction.html)
+ **Super-type** : [`DisplayUrlAction`](#org.jspresso.framework.application.frontend.action.std.DisplayUrlAction)



Like its parent, this action opens a URL in a browser (or a browser tab). But
 instead of taking the URL out of the context, it uses a statically
 parametrized URL, or rather a key (<code>urlKey</code>) used to translate
 the URL based on the logged-in user language. This is particularly useful for
 linking to static internationalized content, like an online manual. Be aware
 that once the URL is translated, it is still appended to the
 <code>baseUrl</code>.



<table>
<caption>DisplayStaticUrlAction properties</caption>
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
<td align="left"><p><strong>urlKey</strong></p><p><code>String</code></p></td>
<td><p>Configures the translation key used to internationalize the URL to open.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.EditSelectionAction"></a>EditSelectionAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.EditSelectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/EditSelectionAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action is meant to trigger editing on the current collection view
 whenever a single element is selected.



<table>
<caption>EditSelectionAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.ExecuteActionAction"></a>ExecuteActionAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.ExecuteActionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/ExecuteActionAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This generic action takes another arbitrary action out of the context
 parameter and executes it.



<table>
<caption>ExecuteActionAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.workspace.ExitAction"></a>ExitAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.workspace.ExitAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/workspace/ExitAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action exits the application. Before doing so, user activated application
 modules are traversed ton check that no pending changes need to be forwarded
 to the persistent store. Whenever the dirty checking is positive, then the
 user is notified and given a chance to cancel the exit.



<table>
<caption>ExitAction properties</caption>
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
<td align="left"><p><strong>checkCurrentModuleDirtyStateAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures the action used to perform dirty checking on current module to
 update its dirty state. It will be triggered just before a global iteration
 is performed on all the application modules to be able to notify the user
 that pending changes are not yet flushed to the persistent store.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.controller.ListApplicationElementsAction"></a>ListApplicationElementsAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.controller.ListApplicationElementsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/controller/ListApplicationElementsAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This is a special frontend action to list all application metamodel elements
 available along with their permIds. This is particularly useful to set-up the
 base of security referential setup.



<table>
<caption>ListApplicationElementsAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.security.LoginAction"></a>LoginAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.security.LoginAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/security/LoginAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This is the frontend action to trigger the application login using the current credential in the frontend controller.
 If the action is configured with <code>anonymous = true</code>, then an anonymous login is attempted. If not,
 a normal login is performed.



<table>
<caption>LoginAction properties</caption>
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
<td align="left"><p><strong>anonymous</strong></p><p><code>boolean</code></p></td>
<td><p>Sets anonymous.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.LovAction"></a>LovAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.LovAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/LovAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)
+ **Sub-types** : [`MobileLovAction`](#org.jspresso.framework.application.frontend.action.lov.mobile.MobileLovAction)



This is a standard &quot;List Of Values&quot; action for reference property
 views. Although this action is used by default in view factories on reference
 fields, it can also be used in a more standard way, i.e. registered as a view
 action. In the latter, the <code>okAction</code> must be configured to
 perform a custom treatment once the entity is chosen from the LOV.
 Additionally you can statically configure the descriptor of the searched
 entities using the <code>entityDescriptor</code> parameter so that the LOV
 will act on this type of entities.
 <p/>
 The LOV action prepares a QBE view (filter / result list) along with 3
 actions that can be further refined : <code>findAction</code>,
 <code>okAction</code> and <code>cancelAction</code>. It must the be linked to
 a <code>ModalDialogAction</code> so that the LOV actually pops up.



<table>
<caption>LovAction properties</caption>
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
<td align="left"><p><strong>autoquery</strong></p><p><code>boolean</code></p></td>
<td><p>Whenever setting autoquery to <code>true</code>, the LOV action will
 trigger the query as soon as it gets executed and the initial query filter
 is not empty (e.g. the user typed something in the reference field). This
 brings autocomplete feature to reference fields since, whenever the initial
 filter limits to exactly 1 result, the LOV dialog won't even open. Defaults
 to true.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action to be executed whenever the user cancels the LOV
 dialog.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>componentDescriptorRegistry</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptorRegistry.html">IComponent&#x200B;Descriptor&#x200B;Registry</a></code></p></td>
<td><p>Sets component descriptor registry.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>createAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets create action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>createQueryComponentAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CreateQueryComponentAction.html">Create&#x200B;Query&#x200B;Component&#x200B;Action</a></code></p></td>
<td><p>Configures the action used to create the filter query component based on
 the type of entities backing the LOV.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>defaultIconImageURL</strong></p><p><code>String</code></p></td>
<td><p>Sets the defaultIconImageURL.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>entityDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures explicitly the type of entities the LOV relies on. This is
 automatically determined when installed on a reference field but must be set
 in any other case.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>findAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action to be executed whenever the user queries the
 persistent store, either explicitly when using the action installed in the
 LOV dialog or implicitly through the auto query feature.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>initializationMapping</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,Object&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Whenever the LOV action is not used on a reference field, in which case the
 filter initialization mapping is taken from the reference field descriptor
 (see <code>BasicReferencePropertyDescriptor</code> documentation), this
 property allows to initialize some of the LOV filter properties.
 Initialization is computed dynamically by transferring property values from
 the view model to the filter.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>lovViewDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/ILovViewDescriptorFactory.html">ILov&#x200B;View&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Configures the factory to be used to create the QBE view used in the
 dialog.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>okAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action to be executed whenever the user validates the LOV
 selection.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageSize</strong></p><p><code>Integer</code></p></td>
<td><p>Sets page size.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>pagingAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Sets the pagingAction.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>selectionMode</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ESelectionMode.html">ESelection&#x200B;Mode</a></code></p></td>
<td><p>Allows to force the result view selection mode.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>staticComponentStore</strong></p><p><code>List&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets static component store.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.mobile.MobileLovAction"></a>MobileLovAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.mobile.MobileLovAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/mobile/MobileLovAction.html)
+ **Super-type** : [`LovAction`](#org.jspresso.framework.application.frontend.action.lov.LovAction)



This is a standard &quot;List Of Values&quot; action for mobile environment.



<table>
<caption>MobileLovAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.ModalDialogAction"></a>ModalDialogAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.ModalDialogAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/ModalDialogAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This is a very generic action that takes its specifications out of the action
 context, creates and pops-up a modal dialog based on these specs. The action
 is meant to be chained after another frontend action that produce the dialog
 specs into the action context. Context entries that are used are :
 <ul>
 <li><code>DIALOG_VIEW</code> : the view to be used as the dialog content
 pane.</li>
 <li><code>DIALOG_TITLE</code> : the title of the dialog.</li>
 <li><code>DIALOG_ACTIONS</code> : the actions to be installed at the bottom
 of the dialog.</li>
 <li><code>DIALOG_SIZE</code> : the dialog preferred size. Whenever the dialog
 size is <code>null</code>, the dialog size is determined from the preferred
 size of the content view.</li>
 </ul>



<table>
<caption>ModalDialogAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.module.ModuleRestartAction"></a>ModuleRestartAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.module.ModuleRestartAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/module/ModuleRestartAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action is used to restart a module. It cleans its children and executes
 its startup action.



<table>
<caption>ModuleRestartAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.module.ModuleSelectionAction"></a>ModuleSelectionAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.module.ModuleSelectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/module/ModuleSelectionAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



Displays a module, and the corresponding workspace if necessary based on
 their names. It can be used as startup action to select and display a module
 when the application launches.



<table>
<caption>ModuleSelectionAction properties</caption>
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
<td align="left"><p><strong>moduleName</strong></p><p><code>String</code></p></td>
<td><p>Configures the name (untranslated) of the module to be displayed.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>workspaceName</strong></p><p><code>String</code></p></td>
<td><p>Configures the name (untranslated) of the workspace to be displayed.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.OkChooseComponentAction"></a>OkChooseComponentAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.OkChooseComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/OkChooseComponentAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action augments the context by setting the action parameter to the
 selected component of the collection view (or null if none is selected).



<table>
<caption>OkChooseComponentAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.OkLovAction"></a>OkLovAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.OkLovAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/OkLovAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action augments the context by setting the action parameter to the
 selected entity of the LOV result list (or null if none is selected).



<table>
<caption>OkLovAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.PageOffsetAction"></a>PageOffsetAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.PageOffsetAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/PageOffsetAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action simply augment the context with a page offset integer (
 <code>PAGE_OFFSET</code>). It is meant to be linked to a find/query action
 that will further leverage this offset to navigate a pageable result set.



<table>
<caption>PageOffsetAction properties</caption>
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
<td align="left"><p><strong>pageOffset</strong></p><p><code>Integer</code></p></td>
<td><p>Configures the page offset to be set to the action context.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.module.ParentModuleConnectorSelectionAction"></a>ParentModuleConnectorSelectionAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.module.ParentModuleConnectorSelectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/module/ParentModuleConnectorSelectionAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action simply displays the parent of the currently selected module; i.e.
 it goes up one level in the module hierarchy of the current workspace.



<table>
<caption>ParentModuleConnectorSelectionAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.printing.frontend.action.PrintAction"></a>PrintAction

+ **Full name** : [`org.jspresso.framework.application.printing.frontend.action.PrintAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/frontend/action/PrintAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action allows the user to choose a report among a list and print it. The
 list of available reports is statically configured into the action.



<table>
<caption>PrintAction properties</caption>
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
<td align="left"><p><strong>reportDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/model/descriptor/IReportDescriptor.html">IReport&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the available report descriptors the user will be allowed to
 choose.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>reportFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/model/IReportFactory.html">IReport&#x200B;Factory</a></code></p></td>
<td><p>Configures the report factory to use. The report factory is responsible for
 creating an <code>IReport</code> (a concrete report instance) from a report
 descriptor (<code>IReportDescriptor</code>).</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.module.SaveModuleObjectFrontAction"></a>SaveModuleObjectFrontAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.module.SaveModuleObjectFrontAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/module/SaveModuleObjectFrontAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action is used to save module and sub-modules objects.



<table>
<caption>SaveModuleObjectFrontAction properties</caption>
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
<td align="left"><p><strong>dirtyTrackingEnabled</strong></p><p><code>boolean</code></p></td>
<td><p>Set dirty tracking enabled.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.SelectedModelToActionParamAction"></a>SelectedModelToActionParamAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.SelectedModelToActionParamAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/SelectedModelToActionParamAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



A very simple frontend action that puts the selected model(s) as context
 action param.



<table>
<caption>SelectedModelToActionParamAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.SetConnectorValueAction"></a>SetConnectorValueAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.SetConnectorValueAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/SetConnectorValueAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action retrieves the action parameter from the action context and
 assigns it as value to the targeted connector. The connector to target is
 itself retrieved from the action context using a parametrized key.



<table>
<caption>SetConnectorValueAction properties</caption>
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
<td align="left"><p><strong>connectorActionContextKey</strong></p><p><code>String</code></p></td>
<td><p>Configures the key to look for the target connector in the context, e.g.
 VIEW_CONNECTOR.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.TransferToClipboardAction"></a>TransferToClipboardAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.TransferToClipboardAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/TransferToClipboardAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



An action used to transfer textual representation(s) of selected models to
 the system clipboard.



<table>
<caption>TransferToClipboardAction properties</caption>
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
<td align="left"><p><strong>clipboardTransferHandler</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/IClipboardTransferHandler.html">IClipboard&#x200B;Transfer&#x200B;Handler</a></code></p></td>
<td><p>Sets the clipboardTransferHandler.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction.UowRollbackerAction"></a>EditSelectedComponentAction.UowRollbackerAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.std.EditSelectedComponentAction.UowRollbackerAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/std/EditSelectedComponentAction/UowRollbackerAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



A wrapper action that roll backs the current UOW before delegating to its
 delegate.



<table>
<caption>EditSelectedComponentAction.UowRollbackerAction properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.wizard.WizardAction"></a>WizardAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.wizard.WizardAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/wizard/WizardAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action implements a &quot;wizard&quot;. It can be configured from the
 simplest use-case (as for a value entering) to the most complex, multi-step
 wizard. Here are a usage directions :
 <ol>
 <li>The generic wizard front-end action is registered in the Spring context
 under the name wizardAction. So you will typically inherit the bean
 definition using the parent="wizardAction" when declaring yours.</li>
 <li>The goal of the wizard action is to work on a map - the wizard model -
 (potentially containing other maps) that represents a hierarchical data
 structure that can be used seamlessly as model for any Jspresso view. In your
 case, the map will only contain 1 key-value pair (the property you want your
 user to enter). When finishing the wizard, the action context will contain
 the map with all the key-value pairs the user has created/modified through
 the wizard steps. It will be accessible in the action context under the
 ActionContextConstants.ACTION_PARAM key and will typically serve as input for
 the finish chained action.</li>
 <li>The wizard action is configured using chained
 org.jspresso.framework.application
 .frontend.action.wizard.IWizardStepDescriptor. A concrete, directly usable,
 implementation of this interface is
 org.jspresso.framework.application.frontend
 .action.wizard.StaticWizardStepDescriptor. Each wizard step is highly
 configurable (name, description, icon, ...) but its most important properties
 are :
 <ol>
 <li><code>viewDescriptor</code> : the Jspresso view descriptor to be shown in
 the wizard GUI when the user enters this step. It can be arbitrarily complex
 (even with master-detail like views, inner actions, constraints, security
 enforcements, ...). Of course, the view descriptor needs a model descriptor.
 So you must describe the wizard model as you would do for persistent entities
 or components (so that step views can configure themselves). You will
 typically use a BasicComponentDescriptor without name so that it is
 automatically excluded from code generation. Note that your actual model
 object will be a map (and not Jspresso generated java bean) but Jspresso
 connectors are "smart" enough to detect the situation and work with the
 hierarchy of maps as if it was a hierarchy of java beans.</li>
 <li>optional <code>onEnterAction</code> and <code>onLeaveAction</code> :
 actions that will respectively be executed when entering and when exiting the
 wizard step.</li>
 <li>optional <code>nextLabelKey</code> and <code>previousLabelKey</code> :
 i18n keys for next and previous buttons if you want to change the default
 ones.</li>
 <li>optional <code>nextStepDescriptor</code> : the next wizard step. If null,
 the wizard GUI will enable the finish action.</li>
 </ol>
 </li>
 <li>The first wizard step is registered on the wizard action using the
 <code>firstWizardStep</code> property.</li>
 <li>When the user leaves the last wizard step (clicking the finish action
 button), the finish action is triggered. The finish action can be registered
 on the wizard action using the <code>finishAction</code> property. This is
 typically the place where you explore the wizard map model -
 <code>ACTION_PARAM</code> - to get back all the data the user has worked on.
 Note that the finish button is entirely configured from the finish action
 (label and icon).</li>
 </ol>



<table>
<caption>WizardAction properties</caption>
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
<td align="left"><p><strong>cancelAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action that will be executed whenever the user cancels the
 wizard.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>finishAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action that will be executed whenever the user validates the
 wizard.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>firstWizardStep</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/wizard/IWizardStepDescriptor.html">IWizard&#x200B;Step&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the first wizard step to display.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>height</strong></p><p><code>Integer</code></p></td>
<td><p>Configures explicitly the height of the wizard dialog. It prevents the
 dialog from resizing dynamically depending on the displayed wizard step.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>width</strong></p><p><code>Integer</code></p></td>
<td><p>Configures explicitly the width of the wizard dialog. It prevents the
 dialog from resizing dynamically depending on the displayed wizard step.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.workspace.WorkspaceSelectionAction"></a>WorkspaceSelectionAction

+ **Full name** : [`org.jspresso.framework.application.frontend.action.workspace.WorkspaceSelectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/workspace/WorkspaceSelectionAction.html)
+ **Super-type** : [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This action displays a workspace using its (untranslated) name.



<table>
<caption>WorkspaceSelectionAction properties</caption>
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
<td align="left"><p><strong>workspaceName</strong></p><p><code>String</code></p></td>
<td><p>Configures the name of the workspace to display.</p></td>
</tr>
</tbody>
</table>

---


