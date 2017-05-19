## BasicScalarPropertyDescriptor

#### <a name="org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor"></a>BasicScalarPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicScalarPropertyDescriptor.html)
+ **Super-type** : [`BasicPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicPropertyDescriptor)
+ **Sub-types** : [`AbstractEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractEnumerationPropertyDescriptor), [`BasicBinaryPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicBinaryPropertyDescriptor), [`BasicBooleanPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicBooleanPropertyDescriptor), [`BasicColorPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicColorPropertyDescriptor), [`BasicNumberPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicNumberPropertyDescriptor), [`BasicStringPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicStringPropertyDescriptor), [`BasicTimeAwarePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTimeAwarePropertyDescriptor)



This is the root abstract descriptor for all property descriptors that are
 not relationship end properties. This includes, for instance, strings,
 numbers, dates, binary content, and so on.



<table>
<caption>BasicScalarPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>defaultValue</strong></p><p><code>Object</code></p></td>
<td><p>Sets the property default value. When a component owning this property is
 instantiated, its properties are initialized using their default values. By
 default, a property default value is <code>null</code>.
 <p>
 This incoming value can be either the actual property default value (as an
 <code>Object</code>) or its string representation whose parsing will be
 delegated to the property descriptor.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.AbstractEnumerationPropertyDescriptor"></a>AbstractEnumerationPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.AbstractEnumerationPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/AbstractEnumerationPropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)
+ **Sub-types** : [`BasicEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicEnumerationPropertyDescriptor), [`RangeEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.RangeEnumerationPropertyDescriptor), [`TimeZoneEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.TimeZoneEnumerationPropertyDescriptor)



Abstract base descriptor for properties whose values are enumerated strings.
 An example of such a property is <i>gender</i> whose value can be <i>M</i>
 (for &quot;Male&quot;) or <i>F</i> (for &quot;Female&quot;). Actual property
 values can be codes that are translated for inclusion in the UI. Such
 properties are usually rendered as combo-boxes.



<table>
<caption>AbstractEnumerationPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>enumerationName</strong></p><p><code>String</code></p></td>
<td><p>This property allows to customize the i18n keys used to translate the
 enumeration values, thus keeping the actual values shorter. For instance
 consider the <i>gender</i> enumeration, composed of the <i>M</i> (for
 &quot;Male&quot;) and <i>F</i> (for &quot;Female&quot;) values. Setting an
 enumeration name to &quot;GENDER&quot; will instruct Jspresso to look for
 translations named &quot;GENDER_M&quot; and &quot;GENDER_F&quot;. This
 would allow for using <i>M</i> and <i>F</i> in other enumeration domains
 with different semantics and translations.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>maxLength</strong></p><p><code>Integer</code></p></td>
<td><p>Sets the maxLength.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>queryMultiselect</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to control if the enumeration property view should be
 transformed into a multi-selectable property view in order to allow for
 value disjunctions in filters. Default value is <code>false</code>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicEnumerationPropertyDescriptor"></a>BasicEnumerationPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicEnumerationPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicEnumerationPropertyDescriptor.html)
+ **Super-type** : [`AbstractEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractEnumerationPropertyDescriptor)
+ **Sub-types** : [`TypeEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.TypeEnumerationPropertyDescriptor)



Describes an enumerated property containing arbitrary values.



<table>
<caption>BasicEnumerationPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>values</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Defines the list of values this enumeration contains.
 <p>
 Enumeration values are translated in the UI using the following scheme :
 <i>[enumerationName]_[value]</i>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>valuesAndIconImageUrls</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Defines the list of values as well as an icon image URL per value this
 enumeration contains. The incoming <code>Map</code> is keyed by the actual
 enumeration values and valued by the icon image URLs.
 <p>
 Enumeration values are translated in the UI using the following scheme :
 <i>[enumerationName]_[value]</i>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.TypeEnumerationPropertyDescriptor"></a>TypeEnumerationPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.TypeEnumerationPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/TypeEnumerationPropertyDescriptor.html)
+ **Super-type** : [`BasicEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicEnumerationPropertyDescriptor)



This is a special enumeration descriptor that allows to build the enumeration
 out of a list of component descriptors. Enumeration values and icons are the
 names and icons of the registered component descriptors. For instance, this
 can be useful in the UI if you want to visually indicate the actual type of a
 element contained in a polymorphic collection.



<table>
<caption>TypeEnumerationPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>componentDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IComponentDescriptor.html">IComponent&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the list of component descriptors to build the enumeration
 values/icons from their names and icons.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.RangeEnumerationPropertyDescriptor"></a>RangeEnumerationPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.RangeEnumerationPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/RangeEnumerationPropertyDescriptor.html)
+ **Super-type** : [`AbstractEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractEnumerationPropertyDescriptor)



This is a special enumeration descriptor that allows to build the enumeration
 values out of a list of integer values. Obviously, no icon is provided for a
 given value.



<table>
<caption>RangeEnumerationPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>maxValue</strong></p><p><code>Integer</code></p></td>
<td><p>The enumeration maximum bound. Default value is <i>10</i>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>minValue</strong></p><p><code>Integer</code></p></td>
<td><p>The enumeration minimum bound. Default value is <i>0</i>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rangeStep</strong></p><p><code>Integer</code></p></td>
<td><p>The step to use for constructing the enumeration values, starting from
 <code>minValue</code> up to <code>maxValue</code>. Default value is
 <i>1</i>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.TimeZoneEnumerationPropertyDescriptor"></a>TimeZoneEnumerationPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.TimeZoneEnumerationPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/TimeZoneEnumerationPropertyDescriptor.html)
+ **Super-type** : [`AbstractEnumerationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.AbstractEnumerationPropertyDescriptor)



This is a special enumeration descriptor that holds all available timezones.



<table>
<caption>TimeZoneEnumerationPropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicBinaryPropertyDescriptor"></a>BasicBinaryPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicBinaryPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicBinaryPropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)
+ **Sub-types** : [`BasicImageBinaryPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicImageBinaryPropertyDescriptor), [`BasicJavaSerializablePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicJavaSerializablePropertyDescriptor)



Describes a property used to store a binary value in the form of a byte
 array.



<table>
<caption>BasicBinaryPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>contentType</strong></p><p><code>String</code></p></td>
<td><p>Configures the default content type to use when downloading the property
 content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fileFilter</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,List&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to configure the file filter that has to be displayed
 whenever a file system operation is initiated from the UI to operate on
 this property. This includes :
 <ul>
 <li>setting the property binary value from a file loaded from the file
 system</li>
 <li>saving the property binary value to a file on the file system</li>
 </ul>
 Jspresso provides built-in actions that do the above and configure their UI
 automatically based on the <code>fileFilter</code> property.
 <p>
 The incoming <code>Map</code> must be structured like following :
 <ul>
 <li>keys are translation keys that will be translated by Jspresso i18n
 layer and presented to the user as the group name of the associated
 extensions, e.g. <i>&quot;JPEG images&quot;</i></li>
 <li>values are the extension list associated to a certain group name, e.g.
 a list containing <i>[&quot;.jpeg&quot;,&quot;.jpg&quot;]</i></li>
 </ul></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>fileName</strong></p><p><code>String</code></p></td>
<td><p>Configures the default file name to use when downloading the property
 content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>maxLength</strong></p><p><code>Integer</code></p></td>
<td><p>Sets the max size (in bytes) of the property value.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicImageBinaryPropertyDescriptor"></a>BasicImageBinaryPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicImageBinaryPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicImageBinaryPropertyDescriptor.html)
+ **Super-type** : [`BasicBinaryPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicBinaryPropertyDescriptor)



Describes a property used to store an image binary value. This type of
 descriptor instructs Jspresso to use an image component to interact with this
 type of property.



<table>
<caption>BasicImageBinaryPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>formatName</strong></p><p><code>String</code></p></td>
<td><p>Sets format name. When set to something not null (e.g. PNG, JPG, ...), the image is transformed to the specified
 format before being stored.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scaledHeight</strong></p><p><code>Integer</code></p></td>
<td><p>Sets scaled height. This property, when set to a positive integer will force the image height to be resized to the
 target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect
 ratio.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>scaledWidth</strong></p><p><code>Integer</code></p></td>
<td><p>Sets scaled width. This property, when set to a positive integer will force the image width to be resized to the
 target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect
 ratio.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicJavaSerializablePropertyDescriptor"></a>BasicJavaSerializablePropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicJavaSerializablePropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicJavaSerializablePropertyDescriptor.html)
+ **Super-type** : [`BasicBinaryPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicBinaryPropertyDescriptor)



Describes a property used to store any java <code>Serializable</code> object.
 The property value is serialized/de-serialized to/from the data store. The
 operation is completely transparent to the developer, i.e. the developer
 never plays with the serialized form.



<table>
<caption>BasicJavaSerializablePropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicBooleanPropertyDescriptor"></a>BasicBooleanPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicBooleanPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicBooleanPropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)



Describes a boolean property.



<table>
<caption>BasicBooleanPropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicColorPropertyDescriptor"></a>BasicColorPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicColorPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicColorPropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)



Describes a property used for storing a color. Color values are stored in the
 property as their string hexadecimal representation (<i>0xargb</i> encoded).
 Jspresso cleanly handles color properties in views for both visually
 displaying and editing them without any extra effort. Moreover the
 <code>ColorHelper</code> helper class eases colors manipulation and helps
 converting to/from their hexadecimal representation.



<table>
<caption>BasicColorPropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicNumberPropertyDescriptor"></a>BasicNumberPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicNumberPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicNumberPropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)
+ **Sub-types** : [`BasicDecimalPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicDecimalPropertyDescriptor), [`BasicIntegerPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicIntegerPropertyDescriptor)



This is the abstract base descriptor of all numeric based properties.



<table>
<caption>BasicNumberPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>maxValue</strong></p><p><code>Big&#x200B;Decimal</code></p></td>
<td><p>Configures the upper bound of the allowed values. Default value is
 <code>null</code>, meaning unbound.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>minValue</strong></p><p><code>Big&#x200B;Decimal</code></p></td>
<td><p>Configures the lower bound of the allowed values. Default value is
 <code>null</code>, meaning unbound.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>thousandsGroupingUsed</strong></p><p><code>boolean</code></p></td>
<td><p>Sets thousands grouping used.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicDecimalPropertyDescriptor"></a>BasicDecimalPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicDecimalPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicDecimalPropertyDescriptor.html)
+ **Super-type** : [`BasicNumberPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicNumberPropertyDescriptor)
+ **Sub-types** : [`BasicPercentPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicPercentPropertyDescriptor)



Describes a decimal property. Property value is either stored as a
 <code>Double</code> or as a <code>BigDecimal</code> depending on the
 <code>usingBigDecimal</code> property.



<table>
<caption>BasicDecimalPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>maxFractionDigit</strong></p><p><code>Integer</code></p></td>
<td><p>Configures the precision of the decimal property. Default value is
 <code>2</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>usingBigDecimal</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the property to be managed using
 <code>java.math.BigDecimal</code>. Default value is <code>false</code>
 which means <code>java.lang.Double</code> will be used.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicPercentPropertyDescriptor"></a>BasicPercentPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicPercentPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicPercentPropertyDescriptor.html)
+ **Super-type** : [`BasicDecimalPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicDecimalPropertyDescriptor)



This is a specialization of decimal descriptor to handle percentage values.
 The impact of using this descriptor is only on the UI level that will be
 configured accordingly, i.e. displaying/editing properties as percentage
 instead of their raw decimal values.



<table>
<caption>BasicPercentPropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicIntegerPropertyDescriptor"></a>BasicIntegerPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicIntegerPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicIntegerPropertyDescriptor.html)
+ **Super-type** : [`BasicNumberPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicNumberPropertyDescriptor)



Describes an integer property. The property is either represented as an
 <code>Integer</code> or a <code>Long</code> depending on the
 <code>usingLong</code> property.



<table>
<caption>BasicIntegerPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>usingLong</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the property to be managed using <code>java.lang.Long</code>.
 Default value is <code>false</code> which means
 <code>java.lang.Integer</code> will be used.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicStringPropertyDescriptor"></a>BasicStringPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicStringPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicStringPropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)
+ **Sub-types** : [`BasicImageUrlPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicImageUrlPropertyDescriptor), [`BasicPasswordPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicPasswordPropertyDescriptor), [`BasicTextPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTextPropertyDescriptor)



Describes a string based property.



<table>
<caption>BasicStringPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>maxLength</strong></p><p><code>Integer</code></p></td>
<td><p>Configures the maximum string length this property allows. Default value is
 <code>null</code> which means unlimited.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>regexpPattern</strong></p><p><code>String</code></p></td>
<td><p>Configures the regular expression pattern this string property allows.
 Default is <code>null</code> which means constraint free.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>regexpPatternSample</strong></p><p><code>String</code></p></td>
<td><p>Allows for providing a conforming sample for the regular expression
 pattern. This human-readable example is used when the end-user has to be
 notified that the incoming property value does not match the pattern
 constraint.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>translatable</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the string property to be translatable. Jspresso will then implement a translation store for the
 property so that it can be displayed in the connected user language. This is particularly useful for
 non-european character sets like chinese, indian, and so on. In that case,
 only the &quot;raw&quot; untranslated property value is stored in the object itself. the various translations
 are stored in an extra store. translated properties support searching, ordering,
 ... exactly like non-translatable properties.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>upperCase</strong></p><p><code>boolean</code></p></td>
<td><p>This is a shortcut to implement the common use-case of handling upper-case
 only properties. all incoming values will be transformed to uppercase as if
 a property processor was registered to perform the transformation.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicImageUrlPropertyDescriptor"></a>BasicImageUrlPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicImageUrlPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicImageUrlPropertyDescriptor.html)
+ **Super-type** : [`BasicStringPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicStringPropertyDescriptor)



Describes an image URL property. This type of descriptor instructs Jspresso
 to use an image component to interact with this type of property.



<table>
<caption>BasicImageUrlPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>scaledHeight</strong></p><p><code>Integer</code></p></td>
<td><p>Sets scaled height. This property, when set to a positive integer will force the image height to be resized to the
 target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect
 ratio.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scaledWidth</strong></p><p><code>Integer</code></p></td>
<td><p>Sets scaled width. This property, when set to a positive integer will force the image width to be resized to the
 target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect
 ratio.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicPasswordPropertyDescriptor"></a>BasicPasswordPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicPasswordPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicPasswordPropertyDescriptor.html)
+ **Super-type** : [`BasicStringPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicStringPropertyDescriptor)



Describes a property used for password values. For obvious security reasons,
 this type of properties will hardly be part of a persistent entity. However
 it is useful for defining transient view models, e.g. for implementing a
 change password action. Jspresso will automatically adapt view fields
 accordingly, using password fields, to interact with password properties.



<table>
<caption>BasicPasswordPropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicTextPropertyDescriptor"></a>BasicTextPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicTextPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicTextPropertyDescriptor.html)
+ **Super-type** : [`BasicStringPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicStringPropertyDescriptor)
+ **Sub-types** : [`BasicHtmlPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicHtmlPropertyDescriptor), [`BasicSourceCodePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicSourceCodePropertyDescriptor)



Describes a multi-line text property. This type of descriptor instructs
 Jspresso to use a multi-line text component to interact with this type of
 property.



<table>
<caption>BasicTextPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>contentType</strong></p><p><code>String</code></p></td>
<td><p>Configures the default content type to use when downloading the property
 content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fileFilter</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,List&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to configure the file filter that has to be displayed
 whenever a file system operation is initiated from the UI to operate on
 this property. This includes :
 <ul>
 <li>setting the property value from a text file loaded from the file system
 </li>
 <li>saving the property text value to a file on the file system</li>
 </ul>
 Jspresso provides built-in actions that do the above and configure their UI
 automatically based on the <code>fileFilter</code> property.
 <p>
 The incoming <code>Map</code> must be structured like following :
 <ul>
 <li>keys are translation keys that will be translated by Jspresso i18n
 layer and presented to the user as the group name of the associated
 extensions, e.g. <i>&quot;HTML files&quot;</i></li>
 <li>values are the extension list associated to a certain group name, e.g.
 a list containing <i>[&quot;.html&quot;,&quot;.htm&quot;]</i></li>
 </ul></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>fileName</strong></p><p><code>String</code></p></td>
<td><p>Configures the default file name to use when downloading the property
 content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryMultiline</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to control if the text property view should be
 transformed into a multi-line text view in order to allow for multi-line
 text in filters. Default value is <code>false</code>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicHtmlPropertyDescriptor"></a>BasicHtmlPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicHtmlPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicHtmlPropertyDescriptor.html)
+ **Super-type** : [`BasicTextPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTextPropertyDescriptor)



Describes a property as handing HTML content. This instructs Jspresso to
 display the property value as HTML instead of raw text content.



<table>
<caption>BasicHtmlPropertyDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicSourceCodePropertyDescriptor"></a>BasicSourceCodePropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicSourceCodePropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicSourceCodePropertyDescriptor.html)
+ **Super-type** : [`BasicTextPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTextPropertyDescriptor)



Describes a property as handing sourcecode content. This instructs Jspresso
 to display the property value as sourcecode, using syntax coloring for
 instance, instead of displaying un-formatted raw content. The language used to
 format the property text content may be defined explicitly using the
 <code>language</code> property.



<table>
<caption>BasicSourceCodePropertyDescriptor properties</caption>
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
<td align="left"><p><strong>language</strong></p><p><code>String</code></p></td>
<td><p>Explicitly sets the language this sourcecode property should contain. This
 is only a hint fo Jspresso to configure the UI components accordingly to
 interact with this property.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicTimeAwarePropertyDescriptor"></a>BasicTimeAwarePropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicTimeAwarePropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicTimeAwarePropertyDescriptor.html)
+ **Super-type** : [`BasicScalarPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicScalarPropertyDescriptor)
+ **Sub-types** : [`BasicDatePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicDatePropertyDescriptor), [`BasicDurationPropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicDurationPropertyDescriptor), [`BasicTimePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTimePropertyDescriptor)



Abstract superclass for time-aware property descriptors.



<table>
<caption>BasicTimeAwarePropertyDescriptor properties</caption>
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
<td align="left"><p><strong>millisecondsAware</strong></p><p><code>boolean</code></p></td>
<td><p>Should this time information include milliseconds.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>secondsAware</strong></p><p><code>boolean</code></p></td>
<td><p>Should this time information include seconds.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicDatePropertyDescriptor"></a>BasicDatePropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicDatePropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicDatePropertyDescriptor.html)
+ **Super-type** : [`BasicTimeAwarePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTimeAwarePropertyDescriptor)



Describes a date based property. Whether the date property should include time
 information or not, can be configured using the type property.



<table>
<caption>BasicDatePropertyDescriptor properties</caption>
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
<td align="left"><p><strong>formatPattern</strong></p><p><code>String</code></p></td>
<td><p>Sets format pattern. Allows to override the default one.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>timeZoneAware</strong></p><p><code>boolean</code></p></td>
<td><p>Sets whether this date property should have its string representation vary
 depending on the client timezone.
 <p/>
 Default value is <code>false</code>, meaning that the date is considered as
 a string. It is in fact expressed in the server timezone.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>type</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/EDateType.html">EDate&#x200B;Type</a></code></p></td>
<td><p>Sets whether this property should contain time information or not. The
 incoming value must be part of the <code>EDateType</code> enum, i.e. :
 <ul>
 <li><code>DATE</code> if the property should only contain the date
 information</li>
 <li><code>DATE_TIME</code> if the property should contain both date and
 time information</li>
 </ul>
 Default value is <code>EDateType.DATE</code>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicDurationPropertyDescriptor"></a>BasicDurationPropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicDurationPropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicDurationPropertyDescriptor.html)
+ **Super-type** : [`BasicTimeAwarePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTimeAwarePropertyDescriptor)



Describes a property used to store a duration value. Duration is stored in
 the form of a number of milliseconds. duration properties are cleanly handled
 by Jspresso UI layer for both displaying / editing duration properties in a
 convenient human format.



<table>
<caption>BasicDurationPropertyDescriptor properties</caption>
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
<td align="left"><p><strong>maxMillis</strong></p><p><code>Long</code></p></td>
<td><p>Configures the maximum duration value this property accepts in
 milliseconds. Default value is <code>null</code>, meaning unbound.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.model.descriptor.basic.BasicTimePropertyDescriptor"></a>BasicTimePropertyDescriptor

+ **Full name** : [`org.jspresso.framework.model.descriptor.basic.BasicTimePropertyDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/basic/BasicTimePropertyDescriptor.html)
+ **Super-type** : [`BasicTimeAwarePropertyDescriptor`](#org.jspresso.framework.model.descriptor.basic.BasicTimeAwarePropertyDescriptor)



Describes a property used to hold time only values. These properties use a
 <code>Date</code> to store their value but only the time part of the value is
 relevant.



<table>
<caption>BasicTimePropertyDescriptor properties</caption>
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
<td align="left"><p><strong>formatPattern</strong></p><p><code>String</code></p></td>
<td><p>Sets format pattern. Allows to override the default one.</p></td>
</tr>
</tbody>
</table>

---


