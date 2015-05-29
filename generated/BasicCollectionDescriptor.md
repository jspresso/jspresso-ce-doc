Reference for BasicCollectionDescriptor hierarchy
=================================================

BasicCollectionDescriptor
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This descriptor is used to describe a collection of components (entities, interfaces or components). This descriptor is mainly used to qualify the collection referenced by a collection property descriptor. As of now, Jspresso supports :

-   collections with {@code Set} semantic: do not allow for duplicates and do not preserve the order of the elements in the data store

-   collections with {@code List} semantic: allows for duplicates and preserves the order of the elements in the data store through an implicit index column

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
<td align="left"><p><strong>collectionInterface</strong></p>
<p><code>Class​&lt;​?​&gt;​</code></p></td>
<td align="left"><p>Allows to choose between the supported collection semantics. The incoming class property value must be one of :</p>
<ul>
<li><p>{@code java.util.Set}</p></li>
<li><p>{@code java.util.List}</p></li>
</ul>
<p>Any other value is not supported and make the descriptor fall back to its default. A {@code null} value (default) is equivalent to setting {@code java.util.Set}. Alternatively, you can use descriptor sub-types, i.e. {@code BasicSetDescriptor} and {@code BasicListDescriptor} that make this property usage useless since they enforce their collection interface.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>elementDescriptor</strong></p>
<p><code>​&lt;​?​&gt;​</code></p></td>
<td align="left"><p>Describes the elements contained in this collection. It can be any of entity, interface or component descriptor.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>nullElementAllowed</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures the collection to accept null element values or not. If the collection does not allows for null values, it forbids to have holes in lists, i.e. all elements have consecutive indices.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orderingProperties</strong></p>
<p><code>Map​&lt;​String​,?​&gt;​</code></p></td>
<td align="left"><p>Ordering properties are used to sort this collection if and only if it is un-indexed (not a {@code List}). The sort order set on the collection can refine the default one that might have been set on the element type level. This property consist of a {@code Map} whose entries are composed with :</p>
<ul>
<li><p>the property name as key</p></li>
<li><p>the sort order for this property as value. This is either a value of the {@code ESort} enum (<em>ASCENDING</em> or <em>DESCENDING</em>) or its equivalent string representation.</p></li>
</ul>
<p>Ordering properties are considered following their order in the map iterator. A {@code null} value (default) will not give any indication for the collection sort order and thus, will delegate to higher specification levels (e.g. the element type sort order).</p></td>
</tr>
</tbody>
</table>

BasicListDescriptor
-------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor is equivalent to a {@code BasicCollectionDescriptor} with its {@code collectionInterface} property set to {@code java.util.List}. Using this descriptor prevents messing up with technical implementation details.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicSetDescriptor
------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor is equivalent to a {@code BasicCollectionDescriptor} with its {@code collectionInterface} property set to {@code java.util.Set}. Using this descriptor prevents messing up with technical implementation details.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>


