## AbstractComponentDescriptor

#### <a name="org.jspresso.framework.model.descriptor.basic.AbstractComponentDescriptor"></a>AbstractComponentDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.AbstractComponentDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/AbstractComponentDescriptor.html)
+ **Super-type** : [`DefaultIconDescriptor`](#org.jspresso.framework.util.descriptor.DefaultIconDescriptor)
+ **Sub-types** : [`BasicComponentDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicComponentDescriptor), [`BasicEntityDescriptor`](#org.jspresso.framework.model.descriptor.entity.basic.BasicEntityDescriptor), [`BasicInterfaceDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicInterfaceDescriptor)



This is the abstract base descriptor for all component-like part of the
 domain model. All the properties included in this base descriptor can of
 course be used in concrete sub-types.
 <p/>
 These sub-types include :
 <ul>
 <li><i>BasicEntityDescriptor</i> for defining a persistent entity</li>
 <li><i>BasicInterfaceDescriptor</i> for defining a common interface that will
 be implemented by other entities, components or even sub-interfaces.</li>
 <li><i>BasicComponentDescriptor</i> for defining reusable structures that can
 be inline in an entity. It also allows to describe an arbitrary POJO and
 make use of it in Jspresso UIs.</li>
 </ul>



<table>
<caption>AbstractComponentDescriptor properties</caption>
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
<td align="left"><p><strong>ancestorDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers this descriptor with a collection of ancestors. It directly
 translates the components inheritance hierarchy since the component
 property descriptors are the union of the declared property descriptors of
 the component and of its ancestors one. A component may have multiple
 ancestors which means that complex multiple-inheritance hierarchy can be
 mapped.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>autoCompleteProperty</strong></p><p><code>String</code></p></td>
<td><p>Allows to customize the property used to autocomplete reference fields on
 this component.
 <p/>
 Whenever this property is <code>null</code>, the following rule apply to
 determine the <i>lovProperty</i> :
 <ol>
 <li>the toString property if not a computed one</li>
 <li>the first string property from the rendered property</li>
 <li>the first rendered property if no string property is found among them</li>
 </ol>
 Note that this property is not inherited by children descriptors, i.e. even
 if an ancestor defines an explicit <i>lovProperty</i>, its children ignore
 this setting.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>componentTranslationsDescriptorTemplate</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicCollectionPropertyDescriptor.html">Basic&#x200B;Collection&#x200B;Property&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/component/IComponent.html">IComponent</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets component translations descriptor template.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>grantedRoles</strong></p><p><code>Collection&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns the roles that are authorized to manipulate components backed by
 this descriptor. It supports &quot;<b>!</b>&quot; prefix to negate the
 role(s). This will directly influence the UI behaviour and even
 composition. Setting the collection of granted roles to <code>null</code>
 (default value) disables role based authorization on this component level.
 Note that this authorization enforcement does not prevent programmatic
 access that is of the developer responsibility.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>lifecycleInterceptorBeanNames</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers a list of lifecycle interceptor instances that will be triggered
 on the different phases of the component lifecycle, i.e. :
 <ul>
 <li>when the component is <i>instantiated</i> in memory</li>
 <li>when the component is <i>created</i> in the data store</li>
 <li>when the component is <i>updated</i> in the data store</li>
 <li>when the component is <i>loaded</i> from the data store</li>
 <li>when the component is <i>deleted</i> from the data store</li>
 </ul>
 This property must be set with Spring bean names (i.e. Spring ids). When
 needed, Jspresso will query the Spring application context to retrieve the
 interceptors instances. This property is equivalent to setting
 <code>lifecycleInterceptorClassNames</code> except that it allows to
 register interceptor instances that are configured externally in the Spring
 context. lifecycle interceptor instances must implement the
 <code>ILifecycleInterceptor&lt;E&gt;</code> interface where &lt;E&gt; is a
 type assignable from the component type.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>lifecycleInterceptorClassNames</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Much the same as <code>lifecycleInterceptorBeanNames</code> except that
 instead of providing a list of Spring bean names, you provide a list of
 fully qualified class names. These classes must :
 <ul>
 <li>provide a default constructor</li>
 <li>implement the <code>IPropertyProcessor&lt;E, F&gt;</code> interface.</li>
 </ul>
 When needed, Jspresso will create the property processor instances.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>orderingProperties</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Ordering properties are used to sort un-indexed collections of instances of
 components backed by this descriptor. This sort order can be overridden on
 the finer collection property level to change the way a specific collection
 is sorted. This property consist of a <code>Map</code> whose entries are
 composed with :
 <ul>
 <li>the property name as key</li>
 <li>the sort order for this property as value. This is either a value of
 the <code>ESort</code> enum (<i>ASCENDING</i> or <i>DESCENDING</i>) or its
 equivalent string representation.</li>
 </ul>
 Ordering properties are considered following their order in the map
 iterator. A <code>null</code> value (default) will not give any indication
 for the collection sort order.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageSize</strong></p><p><code>Integer</code></p></td>
<td><p>Whenever a collection of this component type is presented in a pageable UI,
 this property gives the size (number of component instances) of one page.
 This size can usually be refined at a lower level (e.g. at reference
 property descriptor for &quot;lists of values&quot;). A <code>null</code>
 value (default) disables paging for this component.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>permId</strong></p><p><code>String</code></p></td>
<td><p>A component permanent id is forced to be its fully-qualified class name.
 Trying to set it to another value will raise an exception.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>propertyDescriptors</strong></p><p><code>Collection&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IPropertyDescriptor.html">IProperty&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to describe the properties of the components backed by
 this descriptor. Like in classic OO programming, the actual set of
 properties available to a component is the union of its properties and of
 its ancestors' ones. Jspresso also allows you to refine a property
 descriptor in a child component descriptor exactly as you would do it in a
 subclass. In that case, the attributes of the property defined in the child
 descriptor prevails over the definition of its ancestors. Naturally,
 properties are keyed by their names.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>queryableProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to define which of the component properties are to be
 used in the filter UIs that are based on this component family (a QBE
 screen for instance). Since this is a <code>List</code> queryable
 properties are rendered in the same order.
 <p/>
 Whenever this this property is <code>null</code> (default value), Jspresso
 chooses the default set of queryable properties based on their type. For
 instance, collection properties and binary properties are not used but
 string, numeric, reference, ... properties are. A computed property cannot
 be used since it has no data store existence and thus cannot be queried
 upon.
 <p/>
 Note that this property is not inherited by children descriptors, i.e. even
 if an ancestor defines an explicit set of queryable properties, its
 children ignore this setting.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderedProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to define which of the component properties are to be
 rendered by default when displaying a UI based on this component family.
 For instance, a table will render 1 column per rendered property of the
 component. Any type of property can be used except collection properties.
 Since this is a <code>List</code> queryable properties are rendered in the
 same order.
 <p/>
 Whenever this property is <code>null</code> (default value) Jspresso
 determines the default set of properties to render based on their types,
 e.g. ignores collection properties.
 <p/>
 Note that this property is not inherited by children descriptors, i.e. even
 if an ancestor defines an explicit set of rendered properties, its children
 ignore this setting.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>serviceDelegateBeanNames</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the collection of service delegate instances attached to this
 component. These delegate instances will automatically be triggered
 whenever a method of the service interface it implements get executed. For
 instance :
 <ul>
 <li>the component interface is <code>MyBeanClass</code>. It implements the
 service interface <code>MyService</code>.</li>
 <li>the service interface <code>MyService</code> contains method
 <code>int foo(String)</code>.</li>
 <li>the service delegate class, e.g. <code>MyServiceImpl</code> must
 implement the method <code>int foo(MyBeanClass,String)</code>. Note that
 the parameter list is augmented with the owing component type as 1st
 parameter. This allows to have stateless implementation for delegates, thus
 sharing instances of delegates among instances of components.</li>
 <li>when <code>foo(String)</code> is executed on an instance of
 <code>MyBeanClass</code>, the framework will trigger the delegate
 implementation, passing the instance of the component itself as parameter.</li>
 </ul>
 This property must be set with a map keyed by service interfaces and valued
 by Spring bean names (i.e. Spring ids). Each bean name corresponds to an
 instance of service delegate. When needed, Jspresso will query the Spring
 application context to retrieve the delegate instances. This property is
 equivalent to setting <code>serviceDelegateClassNames</code> except that it
 allows to register delegate instances that are configured externally in the
 Spring context. lifecycle interceptor instances must implement the
 <code>IComponentService</code> marker interface.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>serviceDelegateClassNames</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Much the same as <code>serviceDelegateBeanNames</code> except that instead
 of providing a map valued with Spring bean names, you provide a map valued
 with fully qualified class names. These class must :
 <ul>
 <li>provide a default constructor</li>
 <li>implement the <code>IComponentService</code> marker interface.</li>
 </ul>
 When needed, Jspresso will create service delegate instances.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>sqlName</strong></p><p><code>String</code></p></td>
<td><p>Instructs Jspresso to use this name when translating this component type
 name to the data store namespace. This includes , but is not limited to,
 database table names.
 <p/>
 Default value is <code>null</code> so that Jspresso uses its default naming
 policy.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>toHtmlProperty</strong></p><p><code>String</code></p></td>
<td><p>Allows to customize the HTML representation of a component instance. The
 property name assigned will be used when displaying the component instance
 as HTML. It may be a computed property that composes several other
 properties in a human friendly format.
 <p/>
 Whenever this property is <code>null</code>, the
 <code>toStringProperty</code> is used. Note that this property is not
 inherited by children descriptors, i.e. even if an ancestor defines an
 explicit <i>toHtmlProperty</i> property, its children ignore this setting.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>toStringProperty</strong></p><p><code>String</code></p></td>
<td><p>Allows to customize the string representation of a component instance. The
 property name assigned will be used when displaying the component instance
 as a string. It may be a computed property that composes several other
 properties in a human friendly format.
 <p/>
 Whenever this property is <code>null</code>, the following rule apply to
 determine the <i>toString</i> property :
 <ol>
 <li>the first string property from the rendered property</li>
 <li>the first rendered property if no string property is found among them</li>
 </ol>
 Note that this property is not inherited by children descriptors, i.e. even
 if an ancestor defines an explicit <i>toString</i> property, its children
 ignore this setting.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>unclonedProperties</strong></p><p><code>Collection&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the properties that must not be cloned when this component is
 duplicated. For instance, tracing information like a created timestamp
 should not be cloned; a SSN neither. For a given component, the uncloned
 properties are the ones it defines augmented by the ones its ancestors
 define. There is no mean to make a component property cloneable if one of
 the ancestor declares it un-cloneable.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>writabilityGates</strong></p><p><code>Collection&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gate/IGate.html">IGate</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns a collection of gates to determine component <i>writability</i>. A
 component will be considered writable if and only if all gates are open.
 This mechanism is mainly used for dynamic UI authorization based on model
 state, e.g. a validated invoice should not be editable anymore.
 <p/>
 Descriptor assigned gates will be cloned for each component instance
 created and backed by this descriptor. So basically, each component
 instance will have its own, unshared collection of writability gates.
 <p/>
 Jspresso provides a useful set of gate types, like the binary property gate
 that open/close based on the value of a boolean property of owning
 component.
 <p/>
 By default, component descriptors are not assigned any gates collection,
 i.e. there is no writability restriction. Note that gates do not enforce
 programmatic writability of a component; only UI is impacted.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicComponentDescriptor"></a>BasicComponentDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicComponentDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicComponentDescriptor.html)
+ **Super-type** : [`AbstractComponentDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractComponentDescriptor)
+ **Sub-types** : 



This type of descriptor is used to describe :
 <ul>
 <li>structures that are to be reused but don't have enough focus for being
 considered as entities. For instance <code>MoneyAmount</code> component could
 be composed of a decimal and a reference to a <code>Money</code> entity. This
 structure could then be reused in other elements of the domain like an
 <code>Invoice</code> or an <code>Article</code>. Jspresso terminology for
 these type of structures is <i>&quot;Inline Component&quot;</i>.</li>
 <li>arbitrary models, that even come from outside of Jspresso (an external
 library for instance). Describing an arbitrary component allows for seamless
 usage in the Jspresso view binding architecture. Note that in that case, all
 behavioural properties like lifecycle interceptors or service delegates are
 ignored since none of the model behaviour is handled by Jspresso.</li>
 </ul>
 Both types of components described above must conform to the <i>Java
 Beans</i> standard so that its property changes can be followed by the
 classic <code>add/removePropertyChangeListener</code> methods since Jspresso
 binding architecture leverages this behaviour. Jspresso managed components
 implement it automatically but the developer must ensure it for other types
 of components.



<table>
<caption>BasicComponentDescriptor properties</caption>
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
<td align="left"><p><strong>ancestorDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.entity.basic.BasicEntityDescriptor"></a>BasicEntityDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.entity.basic.BasicEntityDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/entity/basic/BasicEntityDescriptor.html)
+ **Super-type** : [`AbstractComponentDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractComponentDescriptor)



This descriptor key to the description of the application model. It is used
 to describe a model entity. A Jspresso managed entity has a synthetic
 identifier (<i>id</i>) and is versioned (<i>version</i>) to cope with
 concurrent access conflicts through optimistic locking. It conforms to the
 <i>Java Beans</i> standard so that its property changes can be followed by
 the classic <code>add/removePropertyChangeListener</code> methods; Jspresso
 binding architecture leverages this behaviour.



<table>
<caption>BasicEntityDescriptor properties</caption>
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
<td align="left"><p><strong>ancestorDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>purelyAbstract</strong></p><p><code>boolean</code></p></td>
<td><p>This property is used to indicate that the entity type described is to be
 considered <b>abstract</b>. Jspresso will prevent any instantiation through
 its generic actions or internal mechanisms. Trying to do so will result in a
 low level exception and reveals a coding (assembling) error.
 <p>
 However, an abstract entity will have a concrete representation in the data
 store that depends on the inheritance mapping strategy used. As of now,
 Jspresso uses the <i>join-subclass</i> inheritance mapping strategy when
 generating the Hibernate mapping so an abstract entity will end up as a
 table in the data store.
 <p>
 An abstract entity descriptor differs from an interface descriptor mainly
 because of its concrete representation in the data store as formerly
 described.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rootEntityDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntity.html">IEntity</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the root entity descriptor to use globally for the application.
 Jspresso will ensure that all entity descriptors have this root descriptor
 as ancestor.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicInterfaceDescriptor"></a>BasicInterfaceDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicInterfaceDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicInterfaceDescriptor.html)
+ **Super-type** : [`AbstractComponentDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractComponentDescriptor)



This descriptor is a mean of factorizing state/behaviour among components,
 entities or even sub-interfaces. This is a much less coupling mechanism than
 actual entity inheritance and can be used across entities that don't belong
 the the same inheritance hierarchy, or even across types (entities,
 components, interfaces).
 <p>
 Please note that interface descriptor is not a way for domain elements to
 implement arbitrary interfaces coming from external libraries unless they
 only contain property accessors. The latter can be achieved using service
 delegates and the <code>serviceDelegates[Bean|Class]Names</code> property.



<table>
<caption>BasicInterfaceDescriptor properties</caption>
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


