## Module

#### <a name="org.jspresso.framework.application.model.Module"></a>Module

+ **Full name** : [`org.jspresso.framework.application.model.Module`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/Module.html)
+ **Super-type** : `AbstractPropertyChangeCapable`
+ **Sub-types** : [`BeanCollectionModule`](#org.jspresso.framework.application.model.BeanCollectionModule), [`BeanModule`](#org.jspresso.framework.application.model.BeanModule)



A module is an entry point in the application. Modules are organized in
 bi-directional, parent-children hierarchy. As such, they can be viewed (and
 they are materialized in the UI) as trees. Modules can be (re)organized
 dynamically by changing their parent-children relationship and their owning
 workspace UI will reflect the change seamlessly, as with any Jspresso model
 (in fact workspaces and modules are regular beans that are used as model in
 standard Jspresso views).
 <p/>
 Modules, among other features, are capable of providing a view to be
 installed in the UI wen they are selected. This makes Jspresso applications
 really modular and their architecture flexible enough to embed and run a
 large variety of different module types.
 <p/>
 A module can also be as simple as a grouping structure for other modules
 (intermediary nodes).



<table>
<caption>Module properties</caption>
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
<td align="left"><p><strong>description</strong></p><p><code>String</code></p></td>
<td><p>Configures the key used to translate actual internationalized module
 description. The resulting translation will generally be leveraged as a
 toolTip on the UI side but its use may be extended for online help.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>entryAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed every time the module becomes the
 current selected module (either through a user explicit navigation or a
 programmatic selection). The action will execute in the context of the
 current workspace, this module being the current selected module.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>exitAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed every time the module becomes
 unselected (either through a user explicit navigation or a programmatic
 deselection). The action will execute in the context of the current
 workspace, this module being the current selected module (i.e. the action
 occurs before the module is actually left).</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>grantedRoles</strong></p><p><code>Collection&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns the roles that are authorized to start this module. It supports
 &quot;<b>!</b>&quot; prefix to negate the role(s). Whenever the user is not
 granted sufficient privileges, the module is simply not installed in the
 workspace. Setting the collection of granted roles to <code>null</code>
 (default value) disables role based authorization on this module.
 <p/>
 Some specific modules that are component/entity model based i.e.
 <code>Bean(Collection)Module</code> also inherit their authorizations from
 their model.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>icon</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/Icon.html">Icon</a></code></p></td>
<td><p>Sets the icon.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconImageURL</strong></p><p><code>String</code></p></td>
<td><p>Sets the icon image URL of this descriptor. Supported URL protocols include
 :
 <ul>
 <li>all JVM supported protocols</li>
 <li>the <b>jar:/</b> pseudo URL protocol</li>
 <li>the <b>classpath:/</b> pseudo URL protocol</li>
 </ul></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>iconPreferredHeight</strong></p><p><code>int</code></p></td>
<td><p>Sets the icon preferred width.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconPreferredWidth</strong></p><p><code>int</code></p></td>
<td><p>Sets the icon preferred width.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>Configures the key used to translate actual internationalized module name.
 The resulting translation will be leveraged as the module label on the UI
 side.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>permId</strong></p><p><code>String</code></p></td>
<td><p>Sets the permanent identifier to this application element. Permanent
 identifiers are used by different framework parts, like dynamic security or
 record/replay controllers to uniquely identify an application element.
 Permanent identifiers are generated by the SJS build based on the element
 id but must be explicitly set if Spring XML is used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>projectedViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the view descriptor used to construct the view that will be
 displayed when this module is selected.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>startupAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed the first time the module is
 &quot;started&quot; by the user. The action will execute in the context of
 the current workspace, this module being the current selected module. It
 will help initializing module values, notify user, ....</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.model.BeanCollectionModule"></a>BeanCollectionModule

+ **Full name** : [`org.jspresso.framework.application.model.BeanCollectionModule`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/BeanCollectionModule.html)
+ **Super-type** : [`Module`](#org.jspresso.framework.application.model.Module)
+ **Sub-types** : [`FilterableBeanCollectionModule`](#org.jspresso.framework.application.model.FilterableBeanCollectionModule), [`MobileBeanCollectionModule`](#org.jspresso.framework.application.model.mobile.MobileBeanCollectionModule)



This type of module keeps a reference on a beans collection. There is no
 assumption made on whether these beans are actually persistent entities or any
 other type of java beans.
 <p/>
 Simple bean collection modules must have their collection of referenced beans
 initialized somehow. There is no standard built-in action to do so, since it
 is highly dependent on what's needed. So it's rather common to have the
 module content initialized through a startup action depending on the session
 state.



<table>
<caption>BeanCollectionModule properties</caption>
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
<td align="left"><p><strong>elementComponentDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;Object&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the type of bean element this collection module manages. A bunch
 of default values are inferred from this element component descriptor. For
 instance, paging size (if used) will default to the component one unless
 explicitly set. Same goes for icon image URL, default ordering properties
 or even granted roles. The latter means that bean collection modules based
 on forbidden entities will automatically be excluded from the workspace of
 the logged-in user.
 <p/>
 if not explicitly configured, the element component descriptor can be
 inferred from the collection view descriptor configured as projected view
 descriptor.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>elementViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>This property is not used by the module itself, but by built-in actions
 that maybe registered on this module. One of these actions is
 <code>AddBeanAsSubModuleAction</code>.
 <p/>
 This property indicates the view to use whenever the user requests a
 &quot;form-like&quot; view on a collection element. Naturally the
 configured element view descriptor must be backed by a model matching the
 type of the module managed beans.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>moduleObjects</strong></p><p><code>List&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns the list of beans this module manages. The projected view will
 automatically reflect this change since a &quot;moduleObjects&quot;
 property change will be fired.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.model.FilterableBeanCollectionModule"></a>FilterableBeanCollectionModule

+ **Full name** : [`org.jspresso.framework.application.model.FilterableBeanCollectionModule`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/FilterableBeanCollectionModule.html)
+ **Super-type** : [`BeanCollectionModule`](#org.jspresso.framework.application.model.BeanCollectionModule)
+ **Sub-types** : [`MobileFilterableBeanCollectionModule`](#org.jspresso.framework.application.model.mobile.MobileFilterableBeanCollectionModule)



This is a specialized type of bean collection module that provides a filter (
 an instance of <code>IQueryComponent</code> ). This type of module, coupled
 with a generic, built-in, action map is perfectly suited for CRUD-like
 operations.



<table>
<caption>FilterableBeanCollectionModule properties</caption>
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
<td align="left"><p><strong>displayPageIndex</strong></p><p><code>Integer</code></p></td>
<td><p>Delegates to filter.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>filter</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/component/IQueryComponent.html">IQuery&#x200B;Component</a></code></p></td>
<td><p>Assigns the filter to this module instance. It is by default assigned by
 the module startup action (see <code>InitModuleFilterAction</code>). So if
 you ever want to change the default implementation of the filter, you have
 to write and install you own custom startup action or explicitly inject a
 specific instance.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>filterComponentDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/component/IComponent.html">IComponent</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to configure a custom filter model descriptor. If not
 set, which is the default value, the filter model is built out of the
 element component descriptor (QBE filter model).</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>filterExtraViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicTabViewDescriptor.html">Basic&#x200B;Tab&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>This property allow to refine the filter view. If this field is not empty
 the filter view will be replaced by a tab view containing this view and the
 view defined bu the {@link #setFilterViewDescriptor(IViewDescriptor)} method.

 If the extra filter view or the filter view is already a tab view, then tab
 views will be merged to a single tab view.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>filterViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>This property allows to refine the default filter view to re-arrange the
 filter fields. Custom filter view descriptors assigned here must not be
 assigned a model descriptor since they will be at runtime. This is because
 the filter component descriptor must be reworked - to adapt comparable
 field structures for instance.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orderingProperties</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/collection/ESort.html">ESort</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures a custom map of ordering properties for the result set. If not
 set, which is the default, the elements ordering properties is used.
 <p>
 This property consist of a <code>Map</code> whose entries are composed with
 :
 <ul>
 <li>the property name as key</li>
 <li>the sort order for this property as value. This is either a value of
 the <code>ESort</code> enum (<i>ASCENDING</i> or <i>DESCENDING</i>) or its
 equivalent string representation.</li>
 </ul>
 Ordering properties are considered following their order in the map
 iterator.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>page</strong></p><p><code>Integer</code></p></td>
<td><p>Delegates to filter.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageSize</strong></p><p><code>Integer</code></p></td>
<td><p>Configures a custom page size for the result set. If not set, which is the
 default, the elements default page size is used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>paginationViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicViewDescriptor.html">Basic&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the sub view used to navigate between the pages.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pagingAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/action/BackendAction.html">Backend&#x200B;Action</a></code></p></td>
<td><p>Sets the pagingAction.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>queryComponentDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IQueryComponentDescriptorFactory.html">IQuery&#x200B;Component&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Sets the queryComponentDescriptorFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryExtraViewDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IQueryExtraViewDescriptorFactory.html">IQuery&#x200B;Extra&#x200B;View&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Sets the queryExtraViewDescriptorFactory.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>queryViewDescriptorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IQueryViewDescriptorFactory.html">IQuery&#x200B;View&#x200B;Descriptor&#x200B;Factory</a></code></p></td>
<td><p>Sets the queryViewDescriptorFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>recordCount</strong></p><p><code>Integer</code></p></td>
<td><p>Delegates to filter.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>selectedRecordCount</strong></p><p><code>Integer</code></p></td>
<td><p>Delegates to filter.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>stickyResults</strong></p><p><code>List&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Delegates to filter. {@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.model.mobile.MobileFilterableBeanCollectionModule"></a>MobileFilterableBeanCollectionModule

+ **Full name** : [`org.jspresso.framework.application.model.mobile.MobileFilterableBeanCollectionModule`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/mobile/MobileFilterableBeanCollectionModule.html)
+ **Super-type** : [`FilterableBeanCollectionModule`](#org.jspresso.framework.application.model.FilterableBeanCollectionModule)



This is a specialized type of filterable bean collection module that provides a filter (
 an instance of <code>IQueryComponent</code> ). This type of module, coupled
 with a generic, built-in, action map is perfectly suited for CRUD-like
 operations.



<table>
<caption>MobileFilterableBeanCollectionModule properties</caption>
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
<td align="left"><p><strong>elementViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Mobile filterable bean collection module views only support page views as element views
 descriptors.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>filterViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Mobile filterable bean collection module views only support mobile component views as filter views
 descriptors.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>paginationViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicViewDescriptor.html">Basic&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>Not supported in mobile environment.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>projectedViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Mobile filter bean collection module views only support list views as projected view
 descriptors.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>queryModuleFilterAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets query module filter action.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.model.mobile.MobileBeanCollectionModule"></a>MobileBeanCollectionModule

+ **Full name** : [`org.jspresso.framework.application.model.mobile.MobileBeanCollectionModule`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/mobile/MobileBeanCollectionModule.html)
+ **Super-type** : [`BeanCollectionModule`](#org.jspresso.framework.application.model.BeanCollectionModule)



This type of module keeps a reference on a beans collection. There is no
 assumption made on whether these beans are actually persistent entities or any
 other type of java beans.
 <p/>
 Simple bean collection modules must have their collection of referenced beans
 initialized somehow. There is no standard built-in action to do so, since it
 is highly dependent on what's needed. So it's rather common to have the
 module content initialized through a startup action depending on the session
 state.



<table>
<caption>MobileBeanCollectionModule properties</caption>
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
<td align="left"><p><strong>elementViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Mobile bean collection module views only support page views as element views
 descriptors.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>projectedViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Mobile bean collection module views only support list views as projected view
 descriptors.
 <p/>
 {@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.model.BeanModule"></a>BeanModule

+ **Full name** : [`org.jspresso.framework.application.model.BeanModule`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/BeanModule.html)
+ **Super-type** : [`Module`](#org.jspresso.framework.application.model.Module)
+ **Sub-types** : [`MobileBeanModule`](#org.jspresso.framework.application.model.mobile.MobileBeanModule)



This type of module keeps a reference on a single bean. There is no
 assumption made on whether this bean is actually a persistent entity or any
 other type of java bean.
 <p>
 Bean modules must have their referenced bean initialized somehow. So it's
 rather common to have the module content initialized through a startup action
 depending on the session state or dynamically constructed by a standard
 action like <code>AddBeanAsSubModuleAction</code>.
 <p>
 This type of module is definitely the one that offers maximum flexibility to
 handle arbitrary models.



<table>
<caption>BeanModule properties</caption>
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
<td align="left"><p><strong>componentDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;Object&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the type of bean this module manages. A bunch of default values
 are inferred from this component descriptor. For instance, icon image URL
 or even granted roles can be inferred from the configured component
 descriptor. The latter means that bean modules based on forbidden entities
 will automatically be excluded from the workspace of the logged-in user.
 <p>
 However, when not set, the component descriptor it self can be inferred from
 the configured projected view descriptor model.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>moduleObject</strong></p><p><code>Object</code></p></td>
<td><p>Assigns the bean this module manages. The projected view will automatically
 reflect this change since a &quot;moduleObject&quot; property change will
 be fired.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.model.mobile.MobileBeanModule"></a>MobileBeanModule

+ **Full name** : [`org.jspresso.framework.application.model.mobile.MobileBeanModule`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/mobile/MobileBeanModule.html)
+ **Super-type** : [`BeanModule`](#org.jspresso.framework.application.model.BeanModule)



This type of module keeps a reference on a single bean. There is no
 assumption made on whether this bean is actually a persistent entity or any
 other type of java bean.
 <p/>
 Bean modules must have their referenced bean initialized somehow. So it's
 rather common to have the module content initialized through a startup action
 depending on the session state or dynamically constructed by a standard
 action like <code>AddBeanAsSubModuleAction</code>.
 <p/>
 This type of module is definitely the one that offers maximum flexibility to
 handle arbitrary models.



<table>
<caption>MobileBeanModule properties</caption>
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
<td align="left"><p><strong>projectedViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Mobile bean module only support page views as projected views
 descriptors.
 <p/>
 {@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


