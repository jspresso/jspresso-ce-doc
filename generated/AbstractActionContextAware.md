## AbstractActionContextAware

#### <a name="org.jspresso.framework.application.action.AbstractActionContextAware"></a>AbstractActionContextAware

+ **Full name** : [`org.jspresso.framework.application.action.AbstractActionContextAware`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/action/AbstractActionContextAware.html)
+ **Sub-types** : [`AbstractAction`](#org.jspresso.framework.application.action.AbstractAction), [`AbstractLovResultViewDescriptorFactory`](#org.jspresso.framework.application.frontend.action.lov.AbstractLovResultViewDescriptorFactory), [`AbstractLovViewDescriptorFactory`](#org.jspresso.framework.application.frontend.action.lov.AbstractLovViewDescriptorFactory), [`ConnectorValueGetterCallback`](#org.jspresso.framework.application.frontend.file.ConnectorValueGetterCallback), [`DefaultCriteriaFactory`](#org.jspresso.framework.model.persistence.hibernate.criterion.DefaultCriteriaFactory), [`FileToByteArrayCallback`](#org.jspresso.framework.application.frontend.file.FileToByteArrayCallback)



Abstract class for all objects that need to manipulate an action context. It
 contains helper methods that takes the developer away from the standard
 context internal knowledge. Action developers can (should) use these helper
 methods (for reference manual readers, give an eye to the linked javadoc).



<table>
<caption>AbstractActionContextAware properties</caption>
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


#### <a name="org.jspresso.framework.application.action.AbstractAction"></a>AbstractAction

+ **Full name** : [`org.jspresso.framework.application.action.AbstractAction`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/action/AbstractAction.html)
+ **Super-type** : [`AbstractActionContextAware`](#org.jspresso.framework.application.action.AbstractActionContextAware)
+ **Sub-types** : [`BackendAction`](#org.jspresso.framework.application.backend.action.BackendAction), [`FrontendAction`](#org.jspresso.framework.application.frontend.action.FrontendAction)



This is the base class for all application actions. It establishes the
 foundation of the Jspresso action framework, i.e. each action can link :
 <ul>
 <li>a <i>wrapped</i> action that will execute a return back to the caller
 action</li>
 <li>a <i>next</i> action that will execute after the caller</li>
 </ul>
 The action chaining described above supports the separation of concerns that
 consists in splitting the actions in two distinct categories :
 <ul>
 <li><i>frontend</i> actions that deal with user interaction. They are
 typically used to bootstrap a service request from th UI, update the UI
 state, trigger the display of information, errors, ...</li>
 <li><i>backend</i> actions that are faceless, UI agnostic and deal with the
 manipulation of the domain model, backend services, ...</li>
 </ul>
 Conceptually, a frontend action can call a backend action or another frontend
 action but a backend action should stay on the backend, thus should only
 reference another backend action. In other words, the backend layer should
 never explicitly reference the frontend layer.
 <p>
 That's the main reason for having a <i>wrapped</i> and a <i>next</i> action
 in the action chain. The <i>wrapped</i> action is perfectly suited to call
 the backend layer (a backend action) and give the flow back to the frontend
 layer. The <i>next</i> action is perfectly suited to chain 2 actions of the
 same type (i.e. 2 frontend actions or 2 backend actions). Using this scheme
 helps keeping layer dependencies clear. Of course, this dual chaining
 mechanism is completely recursive thus allowing to compose small (generic)
 actions into larger composite ones and promoting reuse.
 <p>
 Actions execute on a context (an arbitrary map of objects keyed by
 "well-known" character strings) that is initialized by the controller when
 the action is triggered. The context passes along the action chain and is
 thus the perfect medium for actions to loosely communicate between each
 other. There are some framework standard elements placed in the action
 context that depend on the application state, but nothing prevents action
 developers to synchronize on arbitrary custom context elements that would be
 produced/consumed to/from the context.
 <p>
 Regarding framework-standard context elements, an action developer can
 (should) leverage the utility methods declared in the
 <code>AbstractActionContextAware</code> super class instead of relying on the
 element keys in the map. Take a look to the
 <code>AbstractActionContextAware</code> documentation to get your hands on
 action context exploration.
 <p>
 Last but not least, you should be aware that actions should be coded with
 thread-safety in mind. Actual action instances are generally singleton-like
 (unless explicitly stated which is extremely rare) and thus, might be used by
 multiple sessions (threads) at once. You should <b>never</b> use action class
 attributes for argument passing along the action chain, but use the
 thread-owned action execution context instead. The action context is a data
 structure that is local to an action chain execution thus not shared across
 threads (users). It is the perfect place for exchanging data between actions.
 Of course, different instances of the same action can be used and configured
 differently through their class attributes (refer to it as static
 configuration), but this is all for using in different places in the
 application.



<table>
<caption>AbstractAction properties</caption>
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
<td align="left"><p><strong>grantedRoles</strong></p><p><code>Collection&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns the roles that are authorized to execute this action. It supports
 &quot;<b>!</b>&quot; prefix to negate the role(s). This will directly
 influence the UI behaviour since unauthorized actions won't be displayed.
 Setting the collection of granted roles to <code>null</code> (default
 value) disables role based authorization on this action. Note that this
 authorization enforcement does not prevent programmatic access that is of
 the developer responsibility.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>nextAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Registers an action to be executed after this action and after the
 <i>wrapped</i> one. This is perfectly suited to chain an action of the same
 type (frontend or backend) as this one.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>permId</strong></p><p><code>String</code></p></td>
<td><p>Sets the permanent identifier to this application element. Permanent
 identifiers are used by different framework parts, like dynamic security or
 record/replay controllers to uniquely identify an application element.
 Permanent identifiers are generated by the SJS build based on the element
 id but must be explicitly set if Spring XML is used.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>wrappedAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Registers an action to be executed after this action but before the
 <i>next</i> one. This is perfectly suited to chain a backend action from a
 frontend action since the control flow will return back to the calling
 layer (the frontend).</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.AbstractLovResultViewDescriptorFactory"></a>AbstractLovResultViewDescriptorFactory

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.AbstractLovResultViewDescriptorFactory`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/AbstractLovResultViewDescriptorFactory.html)
+ **Super-type** : [`AbstractActionContextAware`](#org.jspresso.framework.application.action.AbstractActionContextAware)
+ **Sub-types** : [`BasicLovResultViewDescriptorFactory`](#org.jspresso.framework.application.frontend.action.lov.BasicLovResultViewDescriptorFactory), [`MobileLovResultViewDescriptorFactory`](#org.jspresso.framework.application.frontend.action.lov.mobile.MobileLovResultViewDescriptorFactory)



The base abstract implementation for lov result view factories.



<table>
<caption>AbstractLovResultViewDescriptorFactory properties</caption>
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
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.action.lov.AbstractLovViewDescriptorFactory"></a>AbstractLovViewDescriptorFactory

+ **Full name** : [`org.jspresso.framework.application.frontend.action.lov.AbstractLovViewDescriptorFactory`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/AbstractLovViewDescriptorFactory.html)
+ **Super-type** : [`AbstractActionContextAware`](#org.jspresso.framework.application.action.AbstractActionContextAware)
+ **Sub-types** : [`BasicLovViewDescriptorFactory`](#org.jspresso.framework.application.frontend.action.lov.BasicLovViewDescriptorFactory), [`MobileLovViewDescriptorFactory`](#org.jspresso.framework.application.frontend.action.lov.mobile.MobileLovViewDescriptorFactory)



The base abstract implementation for lov view factories.



<table>
<caption>AbstractLovViewDescriptorFactory properties</caption>
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
<td align="left"><p><strong>queryViewDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IQueryViewDescriptorFactory.html">IQuery&#x200B;View&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Sets the queryViewDescriptorFactory.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>resultViewDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/action/lov/ILovResultViewDescriptorFactory.html">ILov&#x200B;Result&#x200B;View&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Sets the resultViewDescriptorFactory.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.file.ConnectorValueGetterCallback"></a>ConnectorValueGetterCallback

+ **Full name** : [`org.jspresso.framework.application.frontend.file.ConnectorValueGetterCallback`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/file/ConnectorValueGetterCallback.html)
+ **Super-type** : [`AbstractActionContextAware`](#org.jspresso.framework.application.action.AbstractActionContextAware)



Default handler implementation to deal with getting binary properties storing
 them in files.



<table>
<caption>ConnectorValueGetterCallback properties</caption>
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


#### <a name="org.jspresso.framework.model.persistence.hibernate.criterion.DefaultCriteriaFactory"></a>DefaultCriteriaFactory

+ **Full name** : [`org.jspresso.framework.model.persistence.hibernate.criterion.DefaultCriteriaFactory`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/persistence/hibernate/criterion/DefaultCriteriaFactory.html)
+ **Super-type** : [`AbstractActionContextAware`](#org.jspresso.framework.application.action.AbstractActionContextAware)



Default implementation of a criteria factory.



<table>
<caption>DefaultCriteriaFactory properties</caption>
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
<td align="left"><p><strong>triStateBooleanSupported</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the criteria factory whether to consider use 3-states booleans, i.e. true, false or undefined. If
 <strong>triStateBooleanSupported</strong> is set to false, then a <code>false</code> boolean value will simply be
 ignored in the generated criteria.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>useAliasesForJoins</strong></p><p><code>boolean</code></p></td>
<td><p>Sets use aliases for joins.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.file.FileToByteArrayCallback"></a>FileToByteArrayCallback

+ **Full name** : [`org.jspresso.framework.application.frontend.file.FileToByteArrayCallback`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/file/FileToByteArrayCallback.html)
+ **Super-type** : [`AbstractActionContextAware`](#org.jspresso.framework.application.action.AbstractActionContextAware)
+ **Sub-types** : [`ActionExecutorCallback`](#org.jspresso.framework.application.frontend.file.ActionExecutorCallback), [`ConnectorValueSetterCallback`](#org.jspresso.framework.application.frontend.file.ConnectorValueSetterCallback)



Default handler implementation to fully read the file input stream into a byte
 array and setting it in the context.



<table>
<caption>FileToByteArrayCallback properties</caption>
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


