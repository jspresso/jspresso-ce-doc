## BasicRelationshipEndPropertyDescriptor

#### <a name="org.jspresso.framework.model.descriptor.basic.BasicRelationshipEndPropertyDescriptor"></a>BasicRelationshipEndPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicRelationshipEndPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicRelationshipEndPropertyDescriptor.html)
+ **Super-type** : [`BasicPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicPropertyDescriptor)
+ **Sub-types** : [`BasicCollectionPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicCollectionPropertyDescriptor), [`BasicReferencePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicReferencePropertyDescriptor)



This is the abstract base descriptor for all relationship properties.
 relationship properties include :
 <ul>
 <li><i>reference</i> properties, i.e. &quot;N to 1&quot; or &quot;1 to
 1&quot; properties</li>
 <li><i>collection</i> properties, i.e. &quot;1 to N&quot; or &quot;N to
 N&quot; properties</li>
 </ul>
 Other type of properties are named <i>scalar</i> properties.



<table>
<caption>BasicRelationshipEndPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>batchSize</strong></p><p><code>Integer</code></p></td>
<td><p>This property allows to finely tune batching strategy of the ORM on this
 relationship end. Whenever possible, the ORM will use a IN clause in order
 to fetch multiple instances relationships at once. The batch size
 determines the size of th IN clause.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>composition</strong></p><p><code>boolean</code></p></td>
<td><p>Instructs the framework that this property has to be treated as a
 <i>composition</i>, in the UML terminology. This implies that reachable
 entities that are referenced by this property follow the owning entity
 lifecycle. For instance, when the owning entity is deleted, the referenced
 entities in composition properties are also deleted.
 <p>
 Whenever this property is not explicitly set by the developer, Jspresso
 uses sensible defaults :
 <ul>
 <li><i>collection properties</i> are compositions <b>unless</b> they are
 bidirectional &quot;N to N&quot;</li>
 <li><i>reference properties</i> are not composition</li>
 </ul>
 <p>
 This property is strictly behavioural and does not impact the domain state
 itself.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>fetchType</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/EFetchType.html">EFetch&#x200B;Type</a></code></p></td>
<td><p>This property allows to finely tune fetching strategy of the ORM on this
 relationship end. This is either a value of the <code>EFetchType</code>
 enum or its equivalent string representation :
 <ul>
 <li><code>SELECT</code> for default 2nd select strategy (lazy)</li>
 <li><code>SUBSELECT</code> for default 2nd select strategy (lazy) using an
 IN clause</li>
 <li><code>JOIN</code> for a join select strategy (not lazy)</li>
 </ul>
 <p>
 Default value is <code>EFetchType.SELECT</code>, i.e. 2nd select strategy.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fkName</strong></p><p><code>String</code></p></td>
<td><p>Gives the developer the opportunity to customize the generated foreign key
 (if any) name.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>Assign reverse temp relation end if set.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>reverseRelationEnd</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IRelationshipEndPropertyDescriptor.html">IRelationship&#x200B;End&#x200B;Property&#x200B;Descriptor</a></code></p></td>
<td><p>Allows to make a relationship bi-directional. By default, when a
 relationship end is defined, it is only navigable from the owning component
 to the described end (default value is <code>null</code>). Assigning a
 reverse relationship ends instructs the framework that the relationship is
 bi-directional. This implies several complementary features :
 <ul>
 <li>When one of the relationship ends is updated, the other side is
 automatically maintained by Jspresso, i.e. you never have to worry about
 reverse state. For instance, considering a <code>Invoice</code> -
 <code>InvoiceLine</code> bi-directional relationship,
 <code>InvoiceLine.setInvoice(Invoice)</code> and
 <code>Invoice.addToInvoiceLines(InvoiceLine)</code> are strictly
 equivalent.</li>
 <li>You can qualify a &quot;N-N&quot; relationship (thus creating an
 association table in the data store behind the scene) by assigning 2
 collection property descriptors as reverse relation ends of each other.</li>
 <li>You can qualify a &quot;1-1&quot; relationship (thus enforcing some
 unicity constraint in the data store behind the scene) by assigning 2
 reference property descriptors as reverse relation ends of each other.</li>
 </ul>
 Setting the reverse relation end operation is commutative so that it
 automatically assigns bot ends as reverse, i.e. you only have to set the
 property on one side of the relationship.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicCollectionPropertyDescriptor"></a>BasicCollectionPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicCollectionPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicCollectionPropertyDescriptor.html)
+ **Super-type** : [`BasicRelationshipEndPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicRelationshipEndPropertyDescriptor)



This descriptor is used to describe collection properties that are used
 either as &quot;1-N&quot; or &quot;N-N&quot; &quot;N&quot; relationship end.



<table>
<caption>BasicCollectionPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>manyToMany</strong></p><p><code>boolean</code></p></td>
<td><p>Forces the collection property to be considered as a many to many
 (&quot;N-N&quot;) end. When a relationship is bi-directional, setting both
 ends as being collection properties turns <code>manyToMany=true</code>
 automatically. But when the relationship is not bi-directional, Jspresso
 has no mean to determine if the collection property is &quot;1-N&quot; or
 &quot;N-N&quot;. Setting this property allows to inform Jspresso about it.
 <p>
 Default value is <code>false</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orderingProperties</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Ordering properties are used to sort this collection property if and only
 if it is un-indexed (not a <code>List</code>). The sort order set on the
 collection property can refine the default one that might have been set on
 the referenced collection level. This property consist of a
 <code>Map</code> whose entries are composed with :
 <ul>
 <li>the property name as key</li>
 <li>the sort order for this property as value. This is either a value of
 the <code>ESort</code> enum (<i>ASCENDING</i> or <i>DESCENDING</i>) or its
 equivalent string representation.</li>
 </ul>
 Ordering properties are considered following their order in the map
 iterator. A <code>null</code> value (default) will not give any indication
 for the collection property sort order and thus, will delegate to higher
 specification levels (i.e. the referenced collection sort order).</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>referencedDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/ICollectionDescriptor.html">ICollection&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;E&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Qualifies the type of collection this property refers to. As of now,
 Jspresso supports :
 <ul>
 <li>collections with <code>Set</code> semantic: do not allow for duplicates
 and do not preserve the order of the elements in the data store</li>
 <li>collections with <code>List</code> semantic: allows for duplicates and
 preserves the order of the elements in the data store through an implicit
 index column</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicReferencePropertyDescriptor"></a>BasicReferencePropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicReferencePropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicReferencePropertyDescriptor.html)
+ **Super-type** : [`BasicRelationshipEndPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicRelationshipEndPropertyDescriptor)
+ **Sub-types** : [`EnumQueryStructureDescriptor`](#org.jspresso.framework.model.descriptor.query.EnumQueryStructureDescriptor)



Default implementation of a reference descriptor.



<table>
<caption>BasicReferencePropertyDescriptor properties</caption>
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
<td><p>This property allows to pre-initialize UI filters that are based on this
 reference property. This includes :
 <ul>
 <li>explicit filters that are displayed for &quot;list of values&quot;</li>
 <li>implicit filters that are use behind the scene for UI auto-completion</li>
 </ul>
 <p>
 The initialization mapping property is a <code>Map</code> keyed by
 referenced type property names (the properties to be initialized).
 <p>
 Values in this map can be either :
 <ul>
 <li>a <b>constant value</b>. In that case, the filter property is
 initialize with this constant value.</li>
 <li>a owning component <b>property name</b>. In that case, the filter
 property is initialize with the value of the owning component property.</li>
 </ul></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>oneToOne</strong></p><p><code>boolean</code></p></td>
<td><p>Forces the reference property to be considered as a one to one
 (&quot;1-1&quot;) end. When a relationship is bi-directional, setting both
 ends as being reference properties turns <code>oneToOne=true</code>
 automatically. But when the relationship is not bi-directional, Jspresso
 has no mean to determine if the reference property is &quot;N-1&quot; or
 &quot;1-1&quot;. Setting this property allows to inform Jspresso about it.
 <p>
 Default value is <code>false</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>pageSize</strong></p><p><code>Integer</code></p></td>
<td><p>This property allows for defining the page size of &quot;lists of
 values&quot; that are built by the UI for this reference property. Whenever
 the <code>pageSize</code> property is set to <code>null</code> on the
 reference property level, Jspresso falls back to the element type default
 page size or turns off paging if the former is also not set.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryableProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to define which of the component properties are to be
 used in the list of value filter that are based on this component family.
 Since this is a <code>List</code> queryable properties are rendered in the
 same order.
 <p>
 Whenever this this property is <code>null</code> (default value), Jspresso
 chooses the default set of queryable properties based on the referenced
 component descriptor.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>referencedDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Qualifies the type of element this property refers to. It may point to any
 type of component descriptor, i.e. entity, interface or component
 descriptor.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderedProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to define which of the component properties are to be
 rendered by default when displaying a list of value on this component
 family. For instance, a table will render 1 column per rendered property of
 the component. Any type of property can be used except collection
 properties. Since this is a <code>List</code> queryable properties are
 rendered in the same order.
 <p>
 Whenever this property is <code>null</code> (default value) Jspresso
 determines the default set of properties to render based on the referenced
 component descriptor.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.query.EnumQueryStructureDescriptor"></a>EnumQueryStructureDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.query.EnumQueryStructureDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/query/EnumQueryStructureDescriptor.html)
+ **Super-type** : [`BasicReferencePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicReferencePropertyDescriptor)



A query structure used to implement enumeration disjunctions in filters.



<table>
<caption>EnumQueryStructureDescriptor properties</caption>
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


