## BasicPropertyDescriptor

#### <a name="org.jspresso.framework.model.descriptor.basic.BasicPropertyDescriptor"></a>BasicPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicPropertyDescriptor.html)
+ **Super-type** : [`DefaultIconDescriptor`](#org.jspresso.framework.util.descriptor.DefaultIconDescriptor)
+ **Sub-types** : [`BasicRelationshipEndPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicRelationshipEndPropertyDescriptor), [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)



This is the abstract base class for all property descriptors. It mainly
 serves for factorizing all commons properties for property descriptors.
 <p/>
 A property descriptor is used for describing a component/entity/interface
 property (<i>Java Beans</i> semantic).
 <p/>
 You will never use <code>BasicPropertyDescriptor</code> as such but rather
 use its concrete descendants.
 <p/>
 Please note that <code>BasicPropertyDescriptor</code> enforces its name to
 start with a lower case letter, following the JavaBean convention. So even if
 you name it &quot;MyProperty&quot;, it will actually end up to
 &quot;myProperty&quot;.



<table>
<caption>BasicPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>cacheable</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the fact that this property can be cached. This is only used for
 computed properties. Note that the cached value will be reset whenever a
 firePropertyChange regarding this property is detected to be fired.
 <p/>
 Default value is <code>false</code> in order to prevent un-desired
 side-effects if computed property change notification is not correctly
 wired.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>computed</strong></p><p><code>boolean</code></p></td>
<td><p>Forces a property to be considered as a computed property by the framework.
 A computed property will be completely ignored by the persistence layer and
 its management is left to the developer.
 <p/>
 Properties declared with a delegate computing class are considered computed
 by default so there is no need to explicitly set them
 <code>computed=true</code>. However, there is sometimes a need to declare a
 property at some level (e.g. in an interface descriptor) and let lower
 level implementation decide how to handle this common property concretely
 (either computing it or handling it as a real persistent property). In that
 case, you can declare this property <code>computed=true</code> in the super
 type and refine the actual implementation (computed or not) in the
 sub-types.
 <p/>
 Default value is <code>false</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>delegateClassName</strong></p><p><code>String</code></p></td>
<td><p>Instructs the framework that this property is computed by a delegate
 attached to the owning component. The <code>delegateClassName</code>
 property must be set with the fully qualified class name of the delegate
 instance to use.
 <p/>
 Delegate instances are stateful. This allows for some caching of computing
 intensive properties. There is exactly one delegate of a certain class per
 owning component instance. Delegate instances are lazily created when
 needed, i.e. whe the computed property is accessed either programmatically
 or by the binding layer.
 <p/>
 The delegate class must implement the
 <code>IComponentExtension&lt;T&gt;</code> interface (where &lt;T&gt; is
 assignable from the owning component class) and provide a public
 constructor taking exactly 1 parameter : the component instance. Jspresso
 provides an adapter class to inherit from :
 <code>AbstractComponentExtension&lt;T&gt;</code>. This helper class
 provides the methods to access the enclosing component from the delegate
 implementation as well as the Spring context it comes from, when needed.
 <p/>
 A delegate-computed property is most of the time read-only but it can be
 made writable by setting the property descriptor
 <code>delegateWritable=true</code>. In that case the delegate class must
 also provide a setter for the computed property.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>delegateWritable</strong></p><p><code>boolean</code></p></td>
<td><p>Instructs the framework that a delegate-computed property is writable. Most
 of the time, a computed property is read-only. Whenever a computed property
 is made writable through the use of <code>delegateWritable=true</code>, the
 delegate class must also provide a setter for the computed property.
 <p/>
 Default value is <code>false</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>filterComparable</strong></p><p><code>Boolean</code></p></td>
<td><p>Sets filter comparable.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>grantedRoles</strong></p><p><code>Collection&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns the roles that are authorized to manipulate the property backed by
 this descriptor. It supports &quot;<b>!</b>&quot; prefix to negate the
 role(s). This will directly influence the UI behaviour and even composition
 (e.g. show/hide columns or fields). Setting the collection of granted roles
 to <code>null</code> (default value) disables role based authorization on
 this property level. Note that this authorization enforcement does not
 prevent programmatic access that is of the developer responsibility.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>integrityProcessorBeanNames</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers a list of property processor instances that will be triggered on
 the different phases of the property modification, i.e. :
 <ul>
 <li><i>before</i> the property is modified, usually for controlling the
 incoming value</li>
 <li><i>while</i> (actually just before the actual assignment) the property
 is modified, allowing to intercept and change the incoming value</li>
 <li><i>after</i> the property is modified, allowing to trigger some
 post-modification behaviour (e.g. tracing, domain integrity management,
 ...)</li>
 </ul>
 This property must be set with Spring bean names (i.e. Spring ids). When
 needed, Jspresso will query the Spring application context to retrieve the
 processor instances. This property is equivalent to setting
 <code>integrityProcessorClassNames</code> except that it allows to register
 processor instances that are configured externally in the Spring context.
 <p/>
 Property processor instances must implement the
 <code>IPropertyProcessor&lt;E, F&gt;</code> interface where &lt;E, F&gt;
 represent respectively the type of the owning component and the type of the
 property. Since there are 3 methods to implement in the interface (1 for
 each of the phase described above), Jspresso provides an adapter class with
 empty implementations to override :
 <code>EmptyPropertyProcessor&lt;E, F&gt;</code>.
 <p/>
 Whenever the underlying property is a collection property, the interface to
 implement is <code>ICollectionPropertyProcessor&lt;E, F&gt;</code> (or
 extend <code>EmptyCollectionPropertyProcessor&lt;E, F&gt;</code>) with 4
 new phases introduced :
 <ul>
 <li><i>before</i> an element is <i>added</i> to the collection property</li>
 <li><i>after</i> an element is <i>added</i> to the collection property</li>
 <li><i>before</i> an element is <i>removed</i> from the collection property
 </li>
 <li><i>after</i> an element is <i>removed</i> from the collection property</li>
 </ul></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>integrityProcessorClassNames</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Much the same as <code>integrityProcessorBeanNames</code> except that
 instead of providing a list of Spring bean names, you provide a list of
 fully qualified class names. These classes must :
 <ul>
 <li>provide a default constructor</li>
 <li>implement the <code>ILifecycleInterceptor&lt;E&gt;</code> interface.</li>
 </ul>
 When needed, Jspresso will create lifecycle interceptor instances.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>mandatory</strong></p><p><code>boolean</code></p></td>
<td><p>Declare a property as mandatory. This will enforce mandatory checks when
 the owning component is persisted as well as when the property is updated
 individually. Moreover, this information allows the views bound to the
 property to be configured accordingly, e.g. display the property with a
 slightly modified label indicating it is mandatory. This constraint is also
 enforced programmatically.
 <p/>
 Default value is false.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>Enforces its name to start with a lower case letter, following the JavaBean
 convention. So even if you name it &quot;MyProperty&quot;, it will actually
 end up to &quot;myProperty&quot;.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>permId</strong></p><p><code>String</code></p></td>
<td><p>A property permanent id is forced to be its name. Trying to set it to
 another value will raise an exception.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>preferredWidth</strong></p><p><code>Integer</code></p></td>
<td><p>This property allows for setting an indication of width for representing
 this property in a view.
 <p/>
 Default value is <code>null</code>, so that the view factory will make its
 decision based on the type and/or other characteristics of the property
 (e.g. max length).</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>readOnly</strong></p><p><code>boolean</code></p></td>
<td><p>Enforces a property to be read-only. This is only enforced at the UI level,
 i.e. the property can still be updated programmatically. The UI may take
 decisions like changing text fields into labels if it knows the underlying
 property is read-only.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>sortable</strong></p><p><code>boolean</code></p></td>
<td><p>Enforces a property sortability. This is only enforced at the UI level,
 i.e. the property can still be used for sorting programmatically.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>sqlName</strong></p><p><code>String</code></p></td>
<td><p>Instructs Jspresso to use this name when translating this property name to
 the data store namespace. This includes , but is not limited to, database
 column names.
 <p/>
 Default value is <code>null</code> so that Jspresso uses its default naming
 policy.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>unicityScope</strong></p><p><code>String</code></p></td>
<td><p>Makes this property part of a unicity scope. All tuples of properties
 belonging to the same unicity scope are enforced to be unique in the
 component type scope. This concretely translates to unique constraints in
 the data store spanning the properties composing the unicity scope.
 <p/>
 Note that, for performance reasons, unicity scopes are only enforced by the
 persistence layer.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>versionControl</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to fine tune whether this component property
 participates in optimistic versioning. It mainly allows to declare some
 properties that should be ignored regarding optimistic versioning thus
 lowering the risk of version conflicts between concurrent users. Of course,
 this feature has to be used with care since it may generate phantom updates
 to the data store.
 <p/>
 Default value is <code>true</code> so that any change in the described
 property increases the owning component version.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>writabilityGates</strong></p><p><code>Collection&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gate/IGate.html">IGate</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns a collection of gates to determine property <i>writability</i>. A
 property will be considered writable if and only if all gates are open.
 This mechanism is mainly used for dynamic UI authorization based on model
 state, e.g. a validated invoice should not be editable anymore.
 <p/>
 Descriptor assigned gates will be cloned for each property instance created
 and backed by this descriptor. So basically, each property instance will
 have its own, unshared collection of writability gates.
 <p/>
 Jspresso provides a useful set of gate types, like the binary property gate
 that open/close based on the value of a boolean property of owning
 component.
 <p/>
 By default, property descriptors are not assigned any gates collection,
 i.e. there is no writability restriction. Note that gates do not enforce
 programmatic writability of a property; only UI is impacted.</p></td>
</tr>
</tbody>
</table>

---


