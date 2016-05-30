## BackendAction

#### <a name="org.jspresso.framework.application.backend.action.BackendAction"></a>BackendAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.BackendAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/BackendAction.html)
+ **Super-type** : [`AbstractAction`](#org.jspresso.framework.application.action.AbstractAction)
+ **Sub-types** : [`AbstractChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.AbstractChangePasswordAction), [`AbstractCloneAction`](#org.jspresso.framework.application.backend.action.AbstractCloneAction), [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction), [`AbstractLdapAction`](#org.jspresso.framework.application.backend.action.AbstractLdapAction), [`AbstractQbeAction`](#org.jspresso.framework.application.backend.action.AbstractQbeAction), [`AbstractQueryComponentsAction`](#org.jspresso.framework.application.backend.action.AbstractQueryComponentsAction), [`AddBeanAsSubModuleAction`](#org.jspresso.framework.application.backend.action.module.AddBeanAsSubModuleAction), [`CreateQueryComponentAction`](#org.jspresso.framework.application.backend.action.CreateQueryComponentAction), [`DeleteEntityAction`](#org.jspresso.framework.application.backend.action.persistence.DeleteEntityAction), [`GenerateJasperReportAction`](#org.jspresso.framework.application.printing.backend.action.GenerateJasperReportAction), [`InitModuleFilterAction`](#org.jspresso.framework.application.backend.action.module.InitModuleFilterAction), [`PurgeCompletedAsynExecutorsAction`](#org.jspresso.framework.application.backend.action.PurgeCompletedAsynExecutorsAction), [`ReloadAction`](#org.jspresso.framework.application.backend.action.persistence.ReloadAction), [`RemoveFromModuleObjectsAction`](#org.jspresso.framework.application.backend.action.persistence.module.RemoveFromModuleObjectsAction), [`ResetConnectorValueAction`](#org.jspresso.framework.application.backend.action.ResetConnectorValueAction), [`SaveAction`](#org.jspresso.framework.application.backend.action.persistence.SaveAction), [`ScriptedBackendAction`](#org.jspresso.framework.application.backend.action.ScriptedBackendAction), [`SelectEntityPropertyAction`](#org.jspresso.framework.application.backend.action.SelectEntityPropertyAction), [`TransferCollectionAction`](#org.jspresso.framework.application.backend.action.TransferCollectionAction)



This class should serve as base class for implementing actions that execute
 on the backend (domain model) of the application. It provides accessors on
 the context elements that are generally used through the action execution
 process.



<table>
<caption>BackendAction properties</caption>
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
<td align="left"><p><strong>badFrontendAccessChecked</strong></p><p><code>boolean</code></p></td>
<td><p>Sets the badFrontendAccessChecked.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.security.AbstractChangePasswordAction"></a>AbstractChangePasswordAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.security.AbstractChangePasswordAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/security/AbstractChangePasswordAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`DatabaseChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.DatabaseChangePasswordAction), [`LdapChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.LdapChangePasswordAction), [`MockChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.MockChangePasswordAction)



This is the base class for implementing an action that performs actual
 modification of a logged-in user password. This implementation delegates to
 subclasses the actual change in the concrete JAAS store. This backend action
 expects a Map&lt;String,Object&gt; in as action parameter in the context.
 This map must contain :
 <p>
 <ul>
 <li><code>password_current</code> entry containing current password. Entry
 key can be referred to as PASSWD_CURRENT static constant.</li>
 <li><code>password_typed</code> entry containing the new password. Entry key
 can be referred to as PASSWD_TYPED static constant.</li>
 <li><code>password_retyped</code> entry containing the new password retyped.
 Entry key can be referred to as PASSWD_RETYPED static constant.</li>
 </ul>
 For the action to succeed, <code>current_password</code> must match the
 logged-in user current password and <code>password_typed</code> and
 <code>password_retyped</code> mut match between each other. The only method to
 be implemented by concrete subclasses is :
 <p>

 <pre>
 protected abstract boolean changePassword(UserPrincipal userPrincipal,
           String currentPassword, String newPassword)
 </pre>



<table>
<caption>AbstractChangePasswordAction properties</caption>
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
<td align="left"><p><strong>allowEmptyPasswords</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the possibility to choose an empty password.
 <p>
 Default value is <code>true</code>, i.e. allow for empty passwords.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>allowLoginPasswords</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the possibility to choose a password that equals the login.
 <p>
 Default value is <code>true</code>, i.e. allow for password equals login.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>digestAlgorithm</strong></p><p><code>String</code></p></td>
<td><p>Sets the digestAlgorithm to use to hash the password before storing it (MD5
 for instance).</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>hashEncoding</strong></p><p><code>String</code></p></td>
<td><p>Sets the hashEncoding to encode the password hash before storing it. You
 may choose between :
 <ul>
 <li><code>BASE64</code> for base 64 encoding.</li>
 <li><code>HEX</code> for base 16 encoding.</li>
 </ul>
 Default encoding is <code>BASE64</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>passwordRegex</strong></p><p><code>String</code></p></td>
<td><p>Configures a regex that new passwords must match.
 <p>
 Default value is <code>null</code>, i.e. no regex is enforced.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>passwordRegexSample</strong></p><p><code>String</code></p></td>
<td><p>Configures an example of a valid password to explain the regex rules.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.security.DatabaseChangePasswordAction"></a>DatabaseChangePasswordAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.security.DatabaseChangePasswordAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/security/DatabaseChangePasswordAction.html)
+ **Super-type** : [`AbstractChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.AbstractChangePasswordAction)



Concrete backend implementation of a change password action where password is
 stored in a relational database.



<table>
<caption>DatabaseChangePasswordAction properties</caption>
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
<td align="left"><p><strong>jdbcTemplate</strong></p><p><code>Jdbc&#x200B;Template</code></p></td>
<td><p>Configures the Spring jdbcTemplate to use to issue the update statement.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>updateQuery</strong></p><p><code>String</code></p></td>
<td><p>Configures the update query to execute to change the password. The prepared
 statement parameters that will be bound are, in order :
 <ol>
 <li><b>&quot;new password&quot;</b> potentially hashed.</li>
 <li><b>&quot;user name&quot;</b>.</li>
 <li><b>&quot;current password&quot;</b> potentially hashed.</li>
 </ol></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.security.LdapChangePasswordAction"></a>LdapChangePasswordAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.security.LdapChangePasswordAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/security/LdapChangePasswordAction.html)
+ **Super-type** : [`AbstractChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.AbstractChangePasswordAction)



Concrete backend implementation of a change password action where password is
 stored in an LDAP directory. The user DN to use to connect to the LDAP
 directory is the one stored in the user principal from the login process.



<table>
<caption>LdapChangePasswordAction properties</caption>
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
<td align="left"><p><strong>ldapUrl</strong></p><p><code>String</code></p></td>
<td><p>Configures the LDAP url (e.g. <i>http://localhost:389</i>) of the LDAP
 directory. The user must be authorized to change its own password in the
 LDAP backend.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.security.MockChangePasswordAction"></a>MockChangePasswordAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.security.MockChangePasswordAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/security/MockChangePasswordAction.html)
+ **Super-type** : [`AbstractChangePasswordAction`](#org.jspresso.framework.application.backend.action.security.AbstractChangePasswordAction)



Mocks up password change.



<table>
<caption>MockChangePasswordAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.AbstractCloneAction"></a>AbstractCloneAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractCloneAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractCloneAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`CloneComponentAction`](#org.jspresso.framework.application.backend.action.CloneComponentAction)



An action used duplicate a domain object. the cloned domain object is set as model for the current view.

 <pre>
 protected abstract Object cloneElement(Object element,
     Map&lt;String, Object&gt; context)
 </pre>



<table>
<caption>AbstractCloneAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.CloneComponentAction"></a>CloneComponentAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.CloneComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CloneComponentAction.html)
+ **Super-type** : [`AbstractCloneAction`](#org.jspresso.framework.application.backend.action.AbstractCloneAction)



An action used duplicate an entity or a component. This action
 is parametrized with a clone factory (<code>IEntityCloneFactory</code>) to
 perform the actual component cloning. Executing this action will result in
 setting the cloned component to the underlying view.



<table>
<caption>CloneComponentAction properties</caption>
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
<td align="left"><p><strong>entityCloneFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntityCloneFactory.html">IEntity&#x200B;Clone&#x200B;Factory</a></code></p></td>
<td><p>Configures the entity clone factory to use to clone the components or
 entities.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.AbstractCollectionAction"></a>AbstractCollectionAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractCollectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractCollectionAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`AbstractAddCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction), [`CollectionElementMoveAction`](#org.jspresso.framework.application.backend.action.CollectionElementMoveAction), [`RemoveCollectionFromMasterAction`](#org.jspresso.framework.application.backend.action.RemoveCollectionFromMasterAction), [`RemoveCollectionFromMasterAction`](#org.jspresso.framework.application.backend.action.persistence.RemoveCollectionFromMasterAction), [`RemoveFromModuleObjectsAction`](#org.jspresso.framework.application.backend.action.module.RemoveFromModuleObjectsAction), [`RemoveModuleObjectAction`](#org.jspresso.framework.application.backend.action.persistence.module.RemoveModuleObjectAction), [`SetActionParamFromSelectedComponentsAction`](#org.jspresso.framework.application.backend.action.SetActionParamFromSelectedComponentsAction)



Base class for backend actions acting on collection models. This class is
 just used to refine certain protected methods return types.



<table>
<caption>AbstractCollectionAction properties</caption>
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
<td align="left"><p><strong>viewPath</strong></p><p><code>int</code></p></td>
<td><p>Sets view path.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction"></a>AbstractAddCollectionToMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractAddCollectionToMasterAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)
+ **Sub-types** : [`AbstractCloneCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCloneCollectionAction), [`AddAnyCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AddAnyCollectionToMasterAction), [`AddComponentCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AddComponentCollectionToMasterAction), [`AddMapToMasterAction`](#org.jspresso.framework.application.backend.action.AddMapToMasterAction), [`PasteCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.PasteCollectionToMasterAction)



An action used in master/detail views to create and add a new detail to a
 master domain object. The only method to be implemented by concrete subclasses
 to retrieve the instances to be added to the master is :
 <p>

 <pre>
 protected abstract List&lt;?&gt;
           getAddedComponents(Map&lt;String, Object&gt; context)
 </pre>



<table>
<caption>AbstractAddCollectionToMasterAction properties</caption>
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
<td align="left"><p><strong>initializationMapping</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,Object&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets initialization mapping.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.AbstractCloneCollectionAction"></a>AbstractCloneCollectionAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractCloneCollectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractCloneCollectionAction.html)
+ **Super-type** : [`AbstractAddCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction)
+ **Sub-types** : [`CloneComponentCollectionAction`](#org.jspresso.framework.application.backend.action.CloneComponentCollectionAction)



An action used duplicate a collection of domain objects. Cloning an entity
 should result in adding it to the collection the action was triggered on.
 Components to clone are retrieved from the context using the selected indices
 of the model collection connector. Actual cloning of components is left to
 concrete implementations that must implement :

 <pre>
 protected abstract Object cloneElement(Object element,
     Map&lt;String, Object&gt; context)
 </pre>



<table>
<caption>AbstractCloneCollectionAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.CloneComponentCollectionAction"></a>CloneComponentCollectionAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.CloneComponentCollectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CloneComponentCollectionAction.html)
+ **Super-type** : [`AbstractCloneCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCloneCollectionAction)



An action used duplicate a collection of entities or components. This action
 is parametrized with a clone factory (<code>IEntityCloneFactory</code>) to
 perform the actual component cloning. Executing this action will result in
 adding the cloned component(s) to the underlying model collection.



<table>
<caption>CloneComponentCollectionAction properties</caption>
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
<td align="left"><p><strong>entityCloneFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntityCloneFactory.html">IEntity&#x200B;Clone&#x200B;Factory</a></code></p></td>
<td><p>Configures the entity clone factory to use to clone the components or
 entities.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.AddAnyCollectionToMasterAction"></a>AddAnyCollectionToMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AddAnyCollectionToMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AddAnyCollectionToMasterAction.html)
+ **Super-type** : [`AbstractAddCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction)



An action used in master/detail views to add new detail(s) to a master domain
 object. The details to add are taken from the action context through the
 <code>ActionParameter</code> context value.



<table>
<caption>AddAnyCollectionToMasterAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.AddComponentCollectionToMasterAction"></a>AddComponentCollectionToMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AddComponentCollectionToMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AddComponentCollectionToMasterAction.html)
+ **Super-type** : [`AbstractAddCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction)



An action used in master/detail views to create and add a new detail to a
 master domain object. Entity (or component) to add are actually created by
 the entity factory retrieved from the action context. The class of entity
 (component) to create is either taken :
 <ol>
 <li>from the action context under the key <code>ELEMENT_DESCRIPTOR</code></li>
 <li>or, if it does not exist, taken from the view model descriptor. In this
 case, the component descriptor to use is the element descriptor of the
 underlying collection descriptor.</li>
 </ol>



<table>
<caption>AddComponentCollectionToMasterAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.AddMapToMasterAction"></a>AddMapToMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AddMapToMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AddMapToMasterAction.html)
+ **Super-type** : [`AbstractAddCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction)
+ **Sub-types** : [`CloneMapCollectionAction`](#org.jspresso.framework.application.backend.action.CloneMapCollectionAction)



An action used in master/detail views where models are backed by maps to
 create and add a new detail to a master domain object. The new instance
 created is an instance of
 <code>org.jspresso.framework.util.collection.ObjectEqualityMap</code>.
 Default property values as well as <code>onCreate</code> lifecycle
 interceptors registered on the component descriptor are supported.



<table>
<caption>AddMapToMasterAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.CloneMapCollectionAction"></a>CloneMapCollectionAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.CloneMapCollectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CloneMapCollectionAction.html)
+ **Super-type** : [`AddMapToMasterAction`](#org.jspresso.framework.application.backend.action.AddMapToMasterAction)



An action used duplicate a collection of domain objects implemented as maps.
 Newly created maps are instances of
 <code>org.jspresso.framework.util.collection.ObjectEqualityMap</code> that
 contains the same key/value pairs as the maps to clone. Executing this action
 will result in adding the cloned map to the underlying model collection.



<table>
<caption>CloneMapCollectionAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.PasteCollectionToMasterAction"></a>PasteCollectionToMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.PasteCollectionToMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/PasteCollectionToMasterAction.html)
+ **Super-type** : [`AbstractAddCollectionToMasterAction`](#org.jspresso.framework.application.backend.action.AbstractAddCollectionToMasterAction)



An action used in master/detail views to paste previously copied or cut
 detail(s) to a master domain object. The application clipboard is used to
 retrieve the entities (or components) to paste. Whenever the components have
 been previously <i>copied</i> to the clipboard, the paste action will clone
 them when executed using the configured entity clone factory. Whenever the
 components have been previously <i>cut</i>, the paste action will simply use
 the exact same instances as the one placed on the clipboard.



<table>
<caption>PasteCollectionToMasterAction properties</caption>
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
<td align="left"><p><strong>entityCloneFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntityCloneFactory.html">IEntity&#x200B;Clone&#x200B;Factory</a></code></p></td>
<td><p>Configures the entity clone factory to use when the paste action is
 triggered after a copy.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.CollectionElementMoveAction"></a>CollectionElementMoveAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.CollectionElementMoveAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CollectionElementMoveAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)



This action can be declared on views that are backed by collections with list
 semantics (indexed collections). It allows to take a the selected elements
 and move them in the collection using a configured offset. It allows for
 re-ordering the list.



<table>
<caption>CollectionElementMoveAction properties</caption>
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
<td align="left"><p><strong>offset</strong></p><p><code>int</code></p></td>
<td><p>Configures the offset to use when moving the selected elements inside the
 list. A configured offset of <b>1</b> will increase (move down) by one the
 selected elements indices whereas an offset of <b>-1</b> will decrease
 (move up) the selected elements indices.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>toBottom</strong></p><p><code>boolean</code></p></td>
<td><p>Configures this action to move the selected elements to the bottom of the
 list.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>toTop</strong></p><p><code>boolean</code></p></td>
<td><p>Configures this action to move the selected elements to the top of the
 list.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.RemoveCollectionFromMasterAction"></a>RemoveCollectionFromMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.RemoveCollectionFromMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/RemoveCollectionFromMasterAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)



An action used in master/detail views to remove selected details from a
 master domain object. No further operation (like actual removal from a
 persistent store) is performed by this action.



<table>
<caption>RemoveCollectionFromMasterAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.persistence.RemoveCollectionFromMasterAction"></a>RemoveCollectionFromMasterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.RemoveCollectionFromMasterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/RemoveCollectionFromMasterAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)



An action used in master/detail views to remove selected details from a
 master domain object. More than just removing the selected details from their
 owning collection, this action &quot;<i>cuts</i>&quot; the existing links
 between the entities to remove and the rest of the domain then registers them
 for deletion on next save operation.
 <p/>
 Note that cleaning of relationships is a 2 pass process. The 1st one is a dry
 run that checks that no functional exception is thrown by the business rules.
 The second one performs the actual cleaning.



<table>
<caption>RemoveCollectionFromMasterAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.module.RemoveFromModuleObjectsAction"></a>RemoveFromModuleObjectsAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.RemoveFromModuleObjectsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/RemoveFromModuleObjectsAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)



This action, which is to be used on bean collection modules, removes the
 selected objects from the module's projected collection. If one (or more) of
 the removed objects are also used in children bean modules, the corresponding
 children bean modules are also removed accordingly.



<table>
<caption>RemoveFromModuleObjectsAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.persistence.module.RemoveModuleObjectAction"></a>RemoveModuleObjectAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.module.RemoveModuleObjectAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/module/RemoveModuleObjectAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)



This action, which is to be used on bean modules, <b>deletes the module
 object from the persistent store</b>. The bean module is also removed from
 it's parent accordingly.



<table>
<caption>RemoveModuleObjectAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.SetActionParamFromSelectedComponentsAction"></a>SetActionParamFromSelectedComponentsAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.SetActionParamFromSelectedComponentsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/SetActionParamFromSelectedComponentsAction.html)
+ **Super-type** : [`AbstractCollectionAction`](#org.jspresso.framework.application.backend.action.AbstractCollectionAction)



A trivial backend action that updates the action context by setting the
 <code>ActionParameter</code> with the selected components of the underlying
 model.



<table>
<caption>SetActionParamFromSelectedComponentsAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.AbstractLdapAction"></a>AbstractLdapAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractLdapAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractLdapAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



Root abstract class of actions that deal with LDAP directory. It's only
 purpose is to standardize the use of Spring <code>LdapTemplate</code>.



<table>
<caption>AbstractLdapAction properties</caption>
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
<td align="left"><p><strong>ldapTemplate</strong></p><p><code>Ldap&#x200B;Template</code></p></td>
<td><p>Configures the Spring LDAP template to use with this action.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.AbstractQbeAction"></a>AbstractQbeAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractQbeAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractQbeAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`FindAction`](#org.jspresso.framework.application.backend.action.FindAction), [`QueryModuleFilterAction`](#org.jspresso.framework.application.backend.action.module.QueryModuleFilterAction)



Abstract base class for QBE find actions.



<table>
<caption>AbstractQbeAction properties</caption>
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
<td align="left"><p><strong>queryAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures the query action used to actually perform the entity query.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>sortOnly</strong></p><p><code>boolean</code></p></td>
<td><p>Sets the sortOnly.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.FindAction"></a>FindAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.FindAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/FindAction.html)
+ **Super-type** : [`AbstractQbeAction`](#org.jspresso.framework.application.backend.action.AbstractQbeAction)



This action will climb the model connector hierarchy to retrieve a query
 component used as QBE filter. It will then tailor paging status on this query
 component before continuing execution. This action is meant to be chained
 with an actual backend action to perform the query (like
 <code>QueryEntitiesAction</code>).



<table>
<caption>FindAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.module.QueryModuleFilterAction"></a>QueryModuleFilterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.QueryModuleFilterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/QueryModuleFilterAction.html)
+ **Super-type** : [`AbstractQbeAction`](#org.jspresso.framework.application.backend.action.AbstractQbeAction)



Retrieves the filter of a module and queries the persistent store to populate
 the module objects. The actual query is delegated to another backend action
 (defaulted to <code>QueryEntitiesAction</code>) that can be configured
 through the <code>queryAction</code> property.



<table>
<caption>QueryModuleFilterAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.AbstractQueryComponentsAction"></a>AbstractQueryComponentsAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.AbstractQueryComponentsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/AbstractQueryComponentsAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`QueryEntitiesAction`](#org.jspresso.framework.application.backend.action.persistence.hibernate.QueryEntitiesAction), [`StaticQueryComponentsAction`](#org.jspresso.framework.application.backend.action.StaticQueryComponentsAction)



This action is the base abstract class to query components by example. It is used behind
 the scene in several places in Jspresso based applications, as in filtered
 bean collection modules, list of values, ... The principles are to perform a search
 based on the Jspresso &quot;<code>IQueryComponent</code>
 &quot;. A Jspresso query component is a hierarchical data structure that
 mimics a portion of the domain model headed by an entity. It is essentially a
 set of property/value pairs where values can be :
 <ol>
 <li>a scalar value</li>
 <li>a comparable query structure (operator, inf and sup value) to place a
 constraint on a comparable property (date, number, ...)</li>
 <li>a sub query component</li>
 </ol>
 <p/>
 Whenever the query is successful, the result is merged back to the
 application session and assigned to the query component
 <code>queriedComponents</code> property.
 <p/>
 Note that there is 1 hook that can be configured by injection to fine-tune
 the performed query : <code>queryComponentRefiner</code>.



<table>
<caption>AbstractQueryComponentsAction properties</caption>
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
<td align="left"><p><strong>mergeMode</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/session/EMergeMode.html">EMerge&#x200B;Mode</a></code></p></td>
<td><p>Sets the mergeMode to use when assigning the queried components to the
 filter query component. A <code>null</code> value means that the queried
 components will assigned without being merged at all. In that case, the
 merging has to be performed later on in the action chain. Forgetting to do
 so will lead to unexpected results. Default value is
 <code>EMergeMode.MERGE_CLEAN_LAZY</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryComponentRefiner</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/IQueryComponentRefiner.html">IQuery&#x200B;Component&#x200B;Refiner</a></code></p></td>
<td><p>Configures a query component refiner that will be called before the query
 component is processed to extract the Hibernate detached criteria. This
 allows for instance to force query values.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>useCountForPagination</strong></p><p><code>boolean</code></p></td>
<td><p>Sets use count for pagination.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.persistence.hibernate.QueryEntitiesAction"></a>QueryEntitiesAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.hibernate.QueryEntitiesAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/hibernate/QueryEntitiesAction.html)
+ **Super-type** : [`AbstractQueryComponentsAction`](#org.jspresso.framework.application.backend.action.AbstractQueryComponentsAction)



This action is used to Hibernate query entities by example. It is used behind
 the scene in several places in Jspresso based applications, as in filtered
 bean collection modules, list of values, ... The principles are to tailor an
 Hibernate Criterion based on the Jspresso &quot;<code>IQueryComponent</code>
 &quot;. A Jspresso query component is a hierarchical data structure that
 mimics a portion of the domain model headed by an entity. It is essentially a
 set of property/value pairs where values can be :
 <ol>
 <li>a scalar value</li>
 <li>a comparable query structure (operator, inf and sup value) to place a
 constraint on a comparable property (date, number, ...)</li>
 <li>a sub query component</li>
 </ol>
 <p/>
 Out of this query component, the action will build an Hibernate detached
 criteria by constructing all join sub-criteria whenever necessary.
 <p/>
 Once the detached criteria is complete, the action will perform the Hibernate
 query while using paging information taken from the query component as well
 as custom sorting properties.
 <p/>
 Whenever the query is successful, the result is merged back to the
 application session and assigned to the query component
 <code>queriedComponents</code> property.
 <p/>
 Note that there are 2 hooks that can be configured by injection to fine-tune
 the performed query : <code>queryComponentRefiner</code> and
 <code>criteriaRefiner</code>.



<table>
<caption>QueryEntitiesAction properties</caption>
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
<td align="left"><p><strong>criteriaFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/persistence/hibernate/criterion/ICriteriaFactory.html">ICriteria&#x200B;Factory</a></code></p></td>
<td><p>Sets the criteriaFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>criteriaRefiner</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/hibernate/ICriteriaRefiner.html">ICriteria&#x200B;Refiner</a></code></p></td>
<td><p>Configures a criteria refiner that will be called before the Hibernate
 detached criteria is actually used to perform the query. It allows to
 complement the criteria with arbitrary complex clauses that cannot be
 simply expressed in a &quot;<i>Query by Example</i>&quot; semantics.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>useInListForPagination</strong></p><p><code>boolean</code></p></td>
<td><p>Sets the useInListForPagination.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.StaticQueryComponentsAction"></a>StaticQueryComponentsAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.StaticQueryComponentsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/StaticQueryComponentsAction.html)
+ **Super-type** : [`AbstractQueryComponentsAction`](#org.jspresso.framework.application.backend.action.AbstractQueryComponentsAction)



This action filters an arbitrary component list against the query component using a query component matcher.



<table>
<caption>StaticQueryComponentsAction properties</caption>
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
<td align="left"><p><strong>componentStore</strong></p><p><code>List&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets component store.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.module.AddBeanAsSubModuleAction"></a>AddBeanAsSubModuleAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.AddBeanAsSubModuleAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/AddBeanAsSubModuleAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



This action can be installed on any collection view and will :
 <ol>
 <li>take the selected elements in the underlying model collection,</li>
 <li>create bean modules out of them, using the
 <code>childModuleProjectedViewDescriptor</code> as projected view if it has
 been configured,</li>
 <li>add the created bean modules as children of the currently selected
 module, visualizing them in the workspace navigation tree.</li>
 </ol>
 Whenever there is no <code>childModuleProjectedViewDescriptor</code>
 configured, and the currently selected module is a bean collection module,
 the created modules projected view descriptor is taken from the bean
 collection module (<code>elementViewDescriptor</code>).



<table>
<caption>AddBeanAsSubModuleAction properties</caption>
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
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.CreateQueryComponentAction"></a>CreateQueryComponentAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.CreateQueryComponentAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CreateQueryComponentAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



Creates a query component to be used in filters or list of values. The
 created query component is stored in the context under the key
 <code>IQueryComponent.QUERY_COMPONENT</code>. Further explanations are given
 about query components in the <code>QueryEntitiesAction</code> documentation.



<table>
<caption>CreateQueryComponentAction properties</caption>
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
<td align="left"><p><strong>queryComponentDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IQueryComponentDescriptorFactory.html">IQuery&#x200B;Component&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Sets the queryComponentDescriptorFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryComponentRefiner</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/IQueryComponentRefiner.html">IQuery&#x200B;Component&#x200B;Refiner</a></code></p></td>
<td><p>Sets the queryComponentRefiner.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.persistence.DeleteEntityAction"></a>DeleteEntityAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.DeleteEntityAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/DeleteEntityAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



An action used to delete the entity that is model of the view.
 <p/>
 Note that cleaning of relationships is a 2 pass process. The 1st one is a dry
 run that checks that no functional exception is thrown by the business rules.
 The second one performs the actual cleaning.



<table>
<caption>DeleteEntityAction properties</caption>
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


#### <a name="org.jspresso.framework.application.printing.backend.action.GenerateJasperReportAction"></a>GenerateJasperReportAction

+ **Full name** : [`org.jspresso.framework.application.printing.backend.action.GenerateJasperReportAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/printing/backend/action/GenerateJasperReportAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



This action performs the actual Jasper report generation using a JDBC
 data source. The report design is retrieved from the action context (under the
 key <code>IReport.REPORT_ACTION_PARAM</code>). The report context used during
 the generation includes the action context so that all Jspresso managed
 objects can be leveraged in the report itself. The logged-in user locale is
 used as the report locale.
 <p>
 The resulting <code>JasperPrint</code> report is then placed into the action
 context as action parameter for further processing (like PDF production for
 instance).



<table>
<caption>GenerateJasperReportAction properties</caption>
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
<td align="left"><p><strong>jdbcTemplate</strong></p><p><code>Jdbc&#x200B;Template</code></p></td>
<td><p>Configures the JDBC template (wrapping a data source) to use for filling the
 report.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.module.InitModuleFilterAction"></a>InitModuleFilterAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.module.InitModuleFilterAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/module/InitModuleFilterAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



Initialize a module filter with a brand new query component and resets the
 module objects collection.



<table>
<caption>InitModuleFilterAction properties</caption>
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
<td align="left"><p><strong>createQueryComponentAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/CreateQueryComponentAction.html">Create&#x200B;Query&#x200B;Component&#x200B;Action</a></code></p></td>
<td><p>Sets the createQueryComponentAction.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryComponentRefiner</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/IQueryComponentRefiner.html">IQuery&#x200B;Component&#x200B;Refiner</a></code></p></td>
<td><p>Sets the queryComponentRefiner.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.PurgeCompletedAsynExecutorsAction"></a>PurgeCompletedAsynExecutorsAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.PurgeCompletedAsynExecutorsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/PurgeCompletedAsynExecutorsAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



Purges completed asynchronous action executors.



<table>
<caption>PurgeCompletedAsynExecutorsAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.persistence.ReloadAction"></a>ReloadAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.ReloadAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/ReloadAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`ReloadModuleObjectAction`](#org.jspresso.framework.application.backend.action.persistence.ReloadModuleObjectAction)



Reloads the entities provided by the context <code>ActionParameter</code>.
 The whole entities graphs are reloaded from the persistent store.



<table>
<caption>ReloadAction properties</caption>
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
<td align="left"><p><strong>transactional</strong></p><p><code>boolean</code></p></td>
<td><p>Sets transactional.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.persistence.ReloadModuleObjectAction"></a>ReloadModuleObjectAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.ReloadModuleObjectAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/ReloadModuleObjectAction.html)
+ **Super-type** : [`ReloadAction`](#org.jspresso.framework.application.backend.action.persistence.ReloadAction)



Reloads all the module entities as well as all its sub-modules entities
 recursively. The whole entities graphs are reloaded from the persistent
 store.



<table>
<caption>ReloadModuleObjectAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.persistence.module.RemoveFromModuleObjectsAction"></a>RemoveFromModuleObjectsAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.module.RemoveFromModuleObjectsAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/module/RemoveFromModuleObjectsAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



This action, which is to be used on bean collection modules, removes the
 selected objects from the module's projected collection <b>and deletes them
 from the persistent store</b>. If one (or more) of the removed objects are
 also used in children bean modules, the corresponding children bean modules
 are also removed accordingly. It is versatile enough to work on mobile collection module
 details.



<table>
<caption>RemoveFromModuleObjectsAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.ResetConnectorValueAction"></a>ResetConnectorValueAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.ResetConnectorValueAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/ResetConnectorValueAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



Resets the model connector value to null.



<table>
<caption>ResetConnectorValueAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.persistence.SaveAction"></a>SaveAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.SaveAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/SaveAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`SaveModuleObjectAction`](#org.jspresso.framework.application.backend.action.persistence.SaveModuleObjectAction)



Saves the entities provided by the context <code>ActionParameter</code>. All
 previously registered persistence operations are also performed.



<table>
<caption>SaveAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.persistence.SaveModuleObjectAction"></a>SaveModuleObjectAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.persistence.SaveModuleObjectAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/persistence/SaveModuleObjectAction.html)
+ **Super-type** : [`SaveAction`](#org.jspresso.framework.application.backend.action.persistence.SaveAction)



Saves all the module entities as well as all its sub-modules entities
 recursively. All previously registered persistence operations are also
 performed.



<table>
<caption>SaveModuleObjectAction properties</caption>
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


#### <a name="org.jspresso.framework.application.backend.action.ScriptedBackendAction"></a>ScriptedBackendAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.ScriptedBackendAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/ScriptedBackendAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)
+ **Sub-types** : [`StaticScriptedBackendAction`](#org.jspresso.framework.application.backend.action.StaticScriptedBackendAction)



A scripted backend action. The action takes the script to execute (an
 <code>IScript</code> implementation) out of its context (using
 <code>ActionParameter</code>) and delegates the actual script execution to a
 <code>IScriptHandler</code> configured through the <code>scriptHandler</code>
 property.



<table>
<caption>ScriptedBackendAction properties</caption>
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
<td align="left"><p><strong>scriptHandler</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/scripting/IScriptHandler.html">IScript&#x200B;Handler</a></code></p></td>
<td><p>Configures the script handler to use to perform the script execution.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.StaticScriptedBackendAction"></a>StaticScriptedBackendAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.StaticScriptedBackendAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/StaticScriptedBackendAction.html)
+ **Super-type** : [`ScriptedBackendAction`](#org.jspresso.framework.application.backend.action.ScriptedBackendAction)



A statically scripted backend action. The script and the scripting language
 are statically configured in the action itself.



<table>
<caption>StaticScriptedBackendAction properties</caption>
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
<td align="left"><p><strong>script</strong></p><p><code>String</code></p></td>
<td><p>Sets the script source code.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scriptLanguage</strong></p><p><code>String</code></p></td>
<td><p>Sets the script language this scripted action is written in.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.SelectEntityPropertyAction"></a>SelectEntityPropertyAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.SelectEntityPropertyAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/SelectEntityPropertyAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



A generic action to fill-in the context <code>ActionParameter</code> with the
 value of an entity property.



<table>
<caption>SelectEntityPropertyAction properties</caption>
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
<td align="left"><p><strong>property</strong></p><p><code>String</code></p></td>
<td><p>Configures the property to extract out of the underlying model.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.action.TransferCollectionAction"></a>TransferCollectionAction

+ **Full name** : [`org.jspresso.framework.application.backend.action.TransferCollectionAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/TransferCollectionAction.html)
+ **Super-type** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction)



An action used to register a collection of domain objects into the
 application's clipboard along with a transfer mode semantics.



<table>
<caption>TransferCollectionAction properties</caption>
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
<td align="left"><p><strong>transferMode</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/datatransfer/ETransferMode.html">ETransfer&#x200B;Mode</a></code></p></td>
<td><p>Configures the transferMode to use when pasting will be requested, i.e. :
 <ul>
 <li><code>ETransferMode.COPY</code> for copy semantics.</li>
 <li><code>ETransferMode.MOVE</code> for move/cut semantics.</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


