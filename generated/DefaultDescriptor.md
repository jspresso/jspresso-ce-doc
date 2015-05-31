## DefaultDescriptor

#### <a name="org.jspresso.framework.util.descriptor.DefaultDescriptor"></a>DefaultDescriptor

+ **Full name** : [`org.jspresso.framework.util.descriptor.DefaultDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/descriptor/DefaultDescriptor.html)
+ **Sub-types** : [`BasicCollectionDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicCollectionDescriptor), [`DefaultIconDescriptor`](#org.jspresso.framework.util.descriptor.DefaultIconDescriptor)



This is a utility class from which most named descriptors inherit for
 factorization purpose. It provides translatable name and description.



<table>
<caption>DefaultDescriptor properties</caption>
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
<td><p>Sets the description of this descriptor. Most of the descriptor
 descriptions are used in conjunction with the Jspresso i18n layer so that
 the description property set here is actually an i18n key used for
 translation. Description is mainly used for UI (in toolTips for instance)
 but may also be used for project technical documentation, contextual help,
 and so on.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>i18nNameKey</strong></p><p><code>String</code></p></td>
<td><p>Sets the I18N key used for translation if it differs from the name itself.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>Sets the name of this descriptor. Most of the descriptor names are used in
 conjunction with the Jspresso i18n layer so that the name property set here
 is actually an i18n key used for translation. The descriptor name property
 semantic may vary depending on the actual descriptor type. For instance, a
 property descriptor name is the name of the property and a component
 descriptor name is the fully qualified name of the underlying class.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.util.descriptor.DefaultIconDescriptor"></a>DefaultIconDescriptor

+ **Full name** : [`org.jspresso.framework.util.descriptor.DefaultIconDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/descriptor/DefaultIconDescriptor.html)
+ **Super-type** : [`DefaultDescriptor`](#org.jspresso.framework.util.descriptor.DefaultDescriptor)
+ **Sub-types** : [`AbstractComponentDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractComponentDescriptor), [`ActionList`](#org.jspresso.framework.view.action.ActionList), [`BasicPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicPropertyDescriptor), [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)



This is a utility class from which most displayable descriptors inherit for
 factorization purpose. It provides an icon image URL.



<table>
<caption>DefaultIconDescriptor properties</caption>
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
<td><p>Sets the icon preferred height.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconPreferredWidth</strong></p><p><code>int</code></p></td>
<td><p>Sets the icon preferred width.</p></td>
</tr>
</tbody>
</table>

---


