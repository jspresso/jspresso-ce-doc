## BasicCollectionDescriptor

#### <a name="org.jspresso.framework.model.descriptor.basic.BasicCollectionDescriptor"></a>BasicCollectionDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicCollectionDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicCollectionDescriptor.html)
+ **Super-type** : [`DefaultDescriptor`](#org.jspresso.framework.util.descriptor.DefaultDescriptor)
+ **Sub-types** : [`BasicListDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicListDescriptor), [`BasicSetDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicSetDescriptor)



This descriptor is used to describe a collection of components (entities,
 interfaces or components). This descriptor is mainly used to qualify the
 collection referenced by a collection property descriptor. As of now,
 Jspresso supports :
 <ul>
 <li>collections with <code>Set</code> semantic: do not allow for duplicates
 and do not preserve the order of the elements in the data store</li>
 <li>collections with <code>List</code> semantic: allows for duplicates and
 preserves the order of the elements in the data store through an implicit
 index column</li>
 </ul>



<table>
<caption>BasicCollectionDescriptor properties</caption>
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
<td align="left"><p><strong>collectionInterface</strong></p><p><code>Class&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Allows to choose between the supported collection semantics. The incoming
 class property value must be one of :
 <ul>
 <li><code>java.util.Set</code></li>
 <li><code>java.util.List</code></li>
 </ul>
 Any other value is not supported and make the descriptor fall back to its
 default. A <code>null</code> value (default) is equivalent to setting
 <code>java.util.Set</code>. Alternatively, you can use descriptor
 sub-types, i.e. <code>BasicSetDescriptor</code> and
 <code>BasicListDescriptor</code> that make this property usage useless
 since they enforce their collection interface.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>elementDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&lt;&#x200B;?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Describes the elements contained in this collection. It can be any of
 entity, interface or component descriptor.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>nullElementAllowed</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the collection to accept null element values or not. If the collection does not allows for null
 values, it forbids to have holes in lists, i.e. all elements have consecutive indices.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orderingProperties</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,?&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Ordering properties are used to sort this collection if and only if it is
 un-indexed (not a <code>List</code>). The sort order set on the collection
 can refine the default one that might have been set on the element type
 level. This property consist of a <code>Map</code> whose entries are
 composed with :
 <ul>
 <li>the property name as key</li>
 <li>the sort order for this property as value. This is either a value of
 the <code>ESort</code> enum (<i>ASCENDING</i> or <i>DESCENDING</i>) or its
 equivalent string representation.</li>
 </ul>
 Ordering properties are considered following their order in the map
 iterator. A <code>null</code> value (default) will not give any indication
 for the collection sort order and thus, will delegate to higher
 specification levels (e.g. the element type sort order).</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicListDescriptor"></a>BasicListDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicListDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicListDescriptor.html)
+ **Super-type** : [`BasicCollectionDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicCollectionDescriptor)



This descriptor is equivalent to a <code>BasicCollectionDescriptor</code>
 with its <code>collectionInterface</code> property set to
 <code>java.util.List</code>. Using this descriptor prevents messing up with
 technical implementation details.



<table>
<caption>BasicListDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicSetDescriptor"></a>BasicSetDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicSetDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicSetDescriptor.html)
+ **Super-type** : [`BasicCollectionDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicCollectionDescriptor)



This descriptor is equivalent to a <code>BasicCollectionDescriptor</code>
 with its <code>collectionInterface</code> property set to
 <code>java.util.Set</code>. Using this descriptor prevents messing up with
 technical implementation details.



<table>
<caption>BasicSetDescriptor properties</caption>
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


