Reference for BackendAction hierarchy
=====================================

BackendAction
-------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``

This class should serve as base class for implementing actions that execute on the backend (domain model) of the application. It provides accessors on the context elements that are generally used through the action execution process.

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
<td align="left"><p><strong>badFrontendAccessChecked</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets the badFrontendAccessChecked.</p></td>
</tr>
</tbody>
</table>

AbstractChangePasswordAction
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

This is the base class for implementing an action that performs actual modification of a logged-in user password. This implementation delegates to subclasses the actual change in the concrete JAAS store. This backend action expects a Map\<String,Object\> in as action parameter in the context. This map must contain :

-   {@code password\_current} entry containing current password. Entry key can be referred to as PASSWD\_CURRENT static constant.

-   {@code password\_typed} entry containing the new password. Entry key can be referred to as PASSWD\_TYPED static constant.

-   {@code password\_retyped} entry containing the new password retyped. Entry key can be referred to as PASSWD\_RETYPED static constant.

For the action to succeed, {@code current\_password} must match the logged-in user current password and {@code password\_typed} and {@code password\_retyped} mut match between each other. The only method to be implemented by concrete subclasses is :

     protected abstract boolean changePassword(UserPrincipal userPrincipal,
               String currentPassword, String newPassword)
     

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
<td align="left"><p><strong>allowEmptyPasswords</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures the possibility to choose an empty password.</p>
<p>Default value is {@code true}, i.e. allow for empty passwords.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>allowLoginPasswords</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures the possibility to choose a password that equals the login.</p>
<p>Default value is {@code true}, i.e. allow for password equals login.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>digestAlgorithm</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the digestAlgorithm to use to hash the password before storing it (MD5 for instance).</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>hashEncoding</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the hashEncoding to encode the password hash before storing it. You may choose between :</p>
<ul>
<li><p>{@code BASE64} for base 64 encoding.</p></li>
<li><p>{@code HEX} for base 16 encoding.</p></li>
</ul>
<p>Default encoding is {@code BASE64}.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>passwordRegex</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures a regex that new passwords must match.</p>
<p>Default value is {@code null}, i.e. no regex is enforced.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>passwordRegexSample</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures an example of a valid password to explain the regex rules.</p></td>
</tr>
</tbody>
</table>

DatabaseChangePasswordAction
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

Concrete backend implementation of a change password action where password is stored in a relational database.

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
<td align="left"><p><strong>jdbcTemplate</strong></p>
<p><code>Jdbc​Template</code></p></td>
<td align="left"><p>Configures the Spring jdbcTemplate to use to issue the update statement.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>updateQuery</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the update query to execute to change the password. The prepared statement parameters that will be bound are, in order :</p>
<ol style="list-style-type: decimal">
<li><p><strong>&quot;new password&quot;</strong> potentially hashed.</p></li>
<li><p><strong>&quot;user name&quot;</strong>.</p></li>
<li><p><strong>&quot;current password&quot;</strong> potentially hashed.</p></li>
</ol></td>
</tr>
</tbody>
</table>

LdapChangePasswordAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

Concrete backend implementation of a change password action where password is stored in an LDAP directory. The user DN to use to connect to the LDAP directory is the one stored in the user principal from the login process.

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
<td align="left"><p><strong>ldapUrl</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the LDAP url (e.g. <em>http://localhost:389</em>) of the LDAP directory. The user must be authorized to change its own password in the LDAP backend.</p></td>
</tr>
</tbody>
</table>

MockChangePasswordAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

AbstractCloneAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

An action used duplicate a domain object. the cloned domain object is set as model for the current view.

     protected abstract Object cloneElement(Object element,
         Map<String, Object> context)
     

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

CloneComponentAction
--------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used duplicate an entity or a component. This action is parametrized with a clone factory ({@code IEntityCloneFactory}) to perform the actual component cloning. Executing this action will result in setting the cloned component to the underlying view.

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
<td align="left"><p><strong>entityCloneFactory</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the entity clone factory to use to clone the components or entities.</p></td>
</tr>
</tbody>
</table>

AbstractCollectionAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``, ``

Base class for backend actions acting on collection models. This class is just used to refine certain protected methods return types.

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
<td align="left"><p><strong>viewPath</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>Sets view path.</p></td>
</tr>
</tbody>
</table>

AbstractAddCollectionToMasterAction
-----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``

An action used in master/detail views to create and add a new detail to a master domain object. The only method to be implemented by concrete subclasses to retrieve the instances to be added to the master is :

     protected abstract List<?>
               getAddedComponents(Map<String, Object> context)
     

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
<td align="left"><p><strong>initializationMapping</strong></p>
<p><code>Map​&lt;​String​,Object​&gt;​</code></p></td>
<td align="left"><p>Sets initialization mapping.</p></td>
</tr>
</tbody>
</table>

AbstractCloneCollectionAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

An action used duplicate a collection of domain objects. Cloning an entity should result in adding it to the collection the action was triggered on. Components to clone are retrieved from the context using the selected indices of the model collection connector. Actual cloning of components is left to concrete implementations that must implement :

     protected abstract Object cloneElement(Object element,
         Map<String, Object> context)
     

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

CloneComponentCollectionAction
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used duplicate a collection of entities or components. This action is parametrized with a clone factory ({@code IEntityCloneFactory}) to perform the actual component cloning. Executing this action will result in adding the cloned component(s) to the underlying model collection.

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
<td align="left"><p><strong>entityCloneFactory</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the entity clone factory to use to clone the components or entities.</p></td>
</tr>
</tbody>
</table>

AddAnyCollectionToMasterAction
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used in master/detail views to add new detail(s) to a master domain object. The details to add are taken from the action context through the {@code ActionParameter} context value.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

AddComponentCollectionToMasterAction
------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used in master/detail views to create and add a new detail to a master domain object. Entity (or component) to add are actually created by the entity factory retrieved from the action context. The class of entity (component) to create is either taken :

1.  from the action context under the key {@code ELEMENT\_DESCRIPTOR}

2.  or, if it does not exist, taken from the view model descriptor. In this case, the component descriptor to use is the element descriptor of the underlying collection descriptor.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

AddMapToMasterAction
--------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

An action used in master/detail views where models are backed by maps to create and add a new detail to a master domain object. The new instance created is an instance of {@code org.jspresso.framework.util.collection.ObjectEqualityMap}. Default property values as well as {@code onCreate} lifecycle interceptors registered on the component descriptor are supported.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

CloneMapCollectionAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used duplicate a collection of domain objects implemented as maps. Newly created maps are instances of {@code org.jspresso.framework.util.collection.ObjectEqualityMap} that contains the same key/value pairs as the maps to clone. Executing this action will result in adding the cloned map to the underlying model collection.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

PasteCollectionToMasterAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used in master/detail views to paste previously copied or cut detail(s) to a master domain object. The application clipboard is used to retrieve the entities (or components) to paste. Whenever the components have been previously *copied* to the clipboard, the paste action will clone them when executed using the configured entity clone factory. Whenever the components have been previously *cut*, the paste action will simply use the exact same instances as the one placed on the clipboard.

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
<td align="left"><p><strong>entityCloneFactory</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the entity clone factory to use when the paste action is triggered after a copy.</p></td>
</tr>
</tbody>
</table>

CollectionElementMoveAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action can be declared on views that are backed by collections with list semantics (indexed collections). It allows to take a the selected elements and move them in the collection using a configured offset. It allows for re-ordering the list.

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
<td align="left"><p><strong>offset</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>Configures the offset to use when moving the selected elements inside the list. A configured offset of <strong>1</strong> will increase (move down) by one the selected elements indices whereas an offset of <strong>-1</strong> will decrease (move up) the selected elements indices.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>toBottom</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures this action to move the selected elements to the bottom of the list.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>toTop</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures this action to move the selected elements to the top of the list.</p></td>
</tr>
</tbody>
</table>

RemoveCollectionFromMasterAction
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used in master/detail views to remove selected details from a master domain object. No further operation (like actual removal from a persistent store) is performed by this action.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

RemoveCollectionFromMasterAction
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used in master/detail views to remove selected details from a master domain object. More than just removing the selected details from their owning collection, this action "*cuts*" the existing links between the entities to remove and the rest of the domain then registers them for deletion on next save operation. Note that cleaning of relationships is a 2 pass process. The 1st one is a dry run that checks that no functional exception is thrown by the business rules. The second one performs the actual cleaning.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

RemoveFromModuleObjectsAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action, which is to be used on bean collection modules, removes the selected objects from the module's projected collection. If one (or more) of the removed objects are also used in children bean modules, the corresponding children bean modules are also removed accordingly.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

RemoveModuleObjectAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action, which is to be used on bean modules, **deletes the module object from the persistent store**. The bean module is also removed from it's parent accordingly.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

SetActionParamFromSelectedComponentsAction
------------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

A trivial backend action that updates the action context by setting the {@code ActionParameter} with the selected components of the underlying model.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

AbstractLdapAction
------------------

-   **Full name** : ``

-   **Super-type** : ``

Root abstract class of actions that deal with LDAP directory. It's only purpose is to standardize the use of Spring {@code LdapTemplate}.

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
<td align="left"><p><strong>ldapTemplate</strong></p>
<p><code>Ldap​Template</code></p></td>
<td align="left"><p>Configures the Spring LDAP template to use with this action.</p></td>
</tr>
</tbody>
</table>

AbstractQbeAction
-----------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

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
<td align="left"><p><strong>queryAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the query action used to actually perform the entity query.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>sortOnly</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets the sortOnly.</p></td>
</tr>
</tbody>
</table>

FindAction
----------

-   **Full name** : ``

-   **Super-type** : ``

This action will climb the model connector hierarchy to retrieve a query component used as QBE filter. It will then tailor paging status on this query component before continuing execution. This action is meant to be chained with an actual backend action to perform the query (like {@code QueryEntitiesAction}).

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

QueryModuleFilterAction
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

Retrieves the filter of a module and queries the persistent store to populate the module objects. The actual query is delegated to another backend action (defaulted to {@code QueryEntitiesAction}) that can be configured through the {@code queryAction} property.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

AbstractQueryComponentsAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This action is the base abstract class to query components by example. It is used behind the scene in several places in Jspresso based applications, as in filtered bean collection modules, list of values, ... The principles are to perform a search based on the Jspresso "{@code IQueryComponent} ". A Jspresso query component is a hierarchical data structure that mimics a portion of the domain model headed by an entity. It is essentially a set of property/value pairs where values can be :

1.  a scalar value

2.  a comparable query structure (operator, inf and sup value) to place a constraint on a comparable property (date, number, ...)

3.  a sub query component

Whenever the query is successful, the result is merged back to the application session and assigned to the query component {@code queriedComponents} property. Note that there is 1 hook that can be configured by injection to fine-tune the performed query : {@code queryComponentRefiner}.

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
<td align="left"><p><strong>mergeMode</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the mergeMode to use when assigning the queried components to the filter query component. A {@code null} value means that the queried components will assigned without being merged at all. In that case, the merging has to be performed later on in the action chain. Forgetting to do so will lead to unexpected results. Default value is {@code EMergeMode.MERGE_CLEAN_LAZY}.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryComponentRefiner</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures a query component refiner that will be called before the query component is processed to extract the Hibernate detached criteria. This allows for instance to force query values.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>useCountForPagination</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets use count for pagination.</p></td>
</tr>
</tbody>
</table>

QueryEntitiesAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

This action is used to Hibernate query entities by example. It is used behind the scene in several places in Jspresso based applications, as in filtered bean collection modules, list of values, ... The principles are to tailor an Hibernate Criterion based on the Jspresso "{@code IQueryComponent} ". A Jspresso query component is a hierarchical data structure that mimics a portion of the domain model headed by an entity. It is essentially a set of property/value pairs where values can be :

1.  a scalar value

2.  a comparable query structure (operator, inf and sup value) to place a constraint on a comparable property (date, number, ...)

3.  a sub query component

Out of this query component, the action will build an Hibernate detached criteria by constructing all join sub-criteria whenever necessary. Once the detached criteria is complete, the action will perform the Hibernate query while using paging information taken from the query component as well as custom sorting properties. Whenever the query is successful, the result is merged back to the application session and assigned to the query component {@code queriedComponents} property. Note that there are 2 hooks that can be configured by injection to fine-tune the performed query : {@code queryComponentRefiner} and {@code criteriaRefiner}.

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
<td align="left"><p><strong>criteriaFactory</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the criteriaFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>criteriaRefiner</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures a criteria refiner that will be called before the Hibernate detached criteria is actually used to perform the query. It allows to complement the criteria with arbitrary complex clauses that cannot be simply expressed in a &quot;<em>Query by Example</em>&quot; semantics.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>useInListForPagination</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets the useInListForPagination.</p></td>
</tr>
</tbody>
</table>

StaticQueryComponentsAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

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
<td align="left"><p><strong>componentStore</strong></p>
<p><code>List​&lt;​?​&gt;​</code></p></td>
<td align="left"><p>Sets component store.</p></td>
</tr>
</tbody>
</table>

AddBeanAsSubModuleAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action can be installed on any collection view and will :

1.  take the selected elements in the underlying model collection,

2.  create bean modules out of them, using the {@code childModuleProjectedViewDescriptor} as projected view if it has been configured,

3.  add the created bean modules as children of the currently selected module, visualizing them in the workspace navigation tree.

Whenever there is no {@code childModuleProjectedViewDescriptor} configured, and the currently selected module is a bean collection module, the created modules projected view descriptor is taken from the bean collection module ({@code elementViewDescriptor}).

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
<td align="left"><p><strong>childModuleProjectedViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the childModuleProjectedViewDescriptor.</p></td>
</tr>
</tbody>
</table>

CreateQueryComponentAction
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

Creates a query component to be used in filters or list of values. The created query component is stored in the context under the key {@code IQueryComponent.QUERY\_COMPONENT}. Further explanations are given about query components in the {@code QueryEntitiesAction} documentation.

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
<td align="left"><p><strong>queryComponentDescriptorFactory</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the queryComponentDescriptorFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryComponentRefiner</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the queryComponentRefiner.</p></td>
</tr>
</tbody>
</table>

DeleteEntityAction
------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used to delete the entity that is model of the view. Note that cleaning of relationships is a 2 pass process. The 1st one is a dry run that checks that no functional exception is thrown by the business rules. The second one performs the actual cleaning.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

GenerateJasperReportAction
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action performs the actual Jasper report generation using a JDBC data source. The report design is retrieved from the action context (under the key {@code IReport.REPORT\_ACTION\_PARAM}). The report context used during the generation includes the action context so that all Jspresso managed objects can be leveraged in the report itself. The logged-in user locale is used as the report locale.

The resulting {@code JasperPrint} report is then placed into the action context as action parameter for further processing (like PDF production for instance).

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
<td align="left"><p><strong>jdbcTemplate</strong></p>
<p><code>Jdbc​Template</code></p></td>
<td align="left"><p>Configures the JDBC template (wrapping a data source) to use for filling the report.</p></td>
</tr>
</tbody>
</table>

InitModuleFilterAction
----------------------

-   **Full name** : ``

-   **Super-type** : ``

Initialize a module filter with a brand new query component and resets the module objects collection.

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
<td align="left"><p><strong>createQueryComponentAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the createQueryComponentAction.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryComponentRefiner</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the queryComponentRefiner.</p></td>
</tr>
</tbody>
</table>

PurgeCompletedAsynExecutorsAction
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

ReloadAction
------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Reloads the entities provided by the context {@code ActionParameter}. The whole entities graphs are reloaded from the persistent store.

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
<td align="left"><p><strong>transactional</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets transactional.</p></td>
</tr>
</tbody>
</table>

ReloadModuleObjectAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

Reloads all the module entities as well as all its sub-modules entities recursively. The whole entities graphs are reloaded from the persistent store.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

RemoveFromModuleObjectsAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action, which is to be used on bean collection modules, removes the selected objects from the module's projected collection **and deletes them from the persistent store**. If one (or more) of the removed objects are also used in children bean modules, the corresponding children bean modules are also removed accordingly. It is versatile enough to work on mobile collection module details.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

ResetConnectorValueAction
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

SaveAction
----------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Saves the entities provided by the context {@code ActionParameter}. All previously registered persistence operations are also performed.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

SaveModuleObjectAction
----------------------

-   **Full name** : ``

-   **Super-type** : ``

Saves all the module entities as well as all its sub-modules entities recursively. All previously registered persistence operations are also performed.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

ScriptedBackendAction
---------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

A scripted backend action. The action takes the script to execute (an {@code IScript} implementation) out of its context (using {@code ActionParameter}) and delegates the actual script execution to a {@code IScriptHandler} configured through the {@code scriptHandler} property.

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
<td align="left"><p><strong>scriptHandler</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the script handler to use to perform the script execution.</p></td>
</tr>
</tbody>
</table>

StaticScriptedBackendAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

A statically scripted backend action. The script and the scripting language are statically configured in the action itself.

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
<td align="left"><p><strong>script</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the script source code.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scriptLanguage</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the script language this scripted action is written in.</p></td>
</tr>
</tbody>
</table>

SelectEntityPropertyAction
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

A generic action to fill-in the context {@code ActionParameter} with the value of an entity property.

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
<td align="left"><p><strong>property</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the property to extract out of the underlying model.</p></td>
</tr>
</tbody>
</table>

TransferCollectionAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used to register a collection of domain objects into the application's clipboard along with a transfer mode semantics.

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
<td align="left"><p><strong>transferMode</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the transferMode to use when pasting will be requested, i.e. :</p>
<ul>
<li><p>{@code ETransferMode.COPY} for copy semantics.</p></li>
<li><p>{@code ETransferMode.MOVE} for move/cut semantics.</p></li>
</ul></td>
</tr>
</tbody>
</table>


