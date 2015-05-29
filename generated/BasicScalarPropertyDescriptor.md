Reference for BasicScalarPropertyDescriptor hierarchy
=====================================================

BasicScalarPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``, ``, ``, ``

This is the root abstract descriptor for all property descriptors that are not relationship end properties. This includes, for instance, strings, numbers, dates, binary content, and so on.

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
<td align="left"><p><strong>defaultValue</strong></p>
<p><code>Object</code></p></td>
<td align="left"><p>Sets the property default value. When a component owning this property is instantiated, its properties are initialized using their default values. By default, a property default value is {@code null}.</p>
<p>This incoming value can be either the actual property default value (as an {@code Object}) or its string representation whose parsing will be delegated to the property descriptor.</p></td>
</tr>
</tbody>
</table>

AbstractEnumerationPropertyDescriptor
-------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

Abstract base descriptor for properties whose values are enumerated strings. An example of such a property is *gender* whose value can be *M* (for "Male") or *F* (for "Female"). Actual property values can be codes that are translated for inclusion in the UI. Such properties are usually rendered as combo-boxes.

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
<td align="left"><p><strong>enumerationName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>This property allows to customize the i18n keys used to translate the enumeration values, thus keeping the actual values shorter. For instance consider the <em>gender</em> enumeration, composed of the <em>M</em> (for &quot;Male&quot;) and <em>F</em> (for &quot;Female&quot;) values. Setting an enumeration name to &quot;GENDER&quot; will instruct Jspresso to look for translations named &quot;GENDER_M&quot; and &quot;GENDER_F&quot;. This would allow for using <em>M</em> and <em>F</em> in other enumeration domains with different semantics and translations.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>maxLength</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Sets the maxLength.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>queryMultiselect</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>This property allows to control if the enumeration property view should be transformed into a multi-selectable property view in order to allow for value disjunctions in filters. Default value is {@code false}.</p></td>
</tr>
</tbody>
</table>

BasicEnumerationPropertyDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

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
<td align="left"><p><strong>values</strong></p>
<p><code>List​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Defines the list of values this enumeration contains.</p>
<p>Enumeration values are translated in the UI using the following scheme : <em>[enumerationName]_[value]</em>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>valuesAndIconImageUrls</strong></p>
<p><code>Map​&lt;​String​,String​&gt;​</code></p></td>
<td align="left"><p>Defines the list of values as well as an icon image URL per value this enumeration contains. The incoming {@code Map} is keyed by the actual enumeration values and valued by the icon image URLs.</p>
<p>Enumeration values are translated in the UI using the following scheme : <em>[enumerationName]_[value]</em>.</p></td>
</tr>
</tbody>
</table>

TypeEnumerationPropertyDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a special enumeration descriptor that allows to build the enumeration out of a list of component descriptors. Enumeration values and icons are the names and icons of the registered component descriptors. For instance, this can be useful in the UI if you want to visually indicate the actual type of a element contained in a polymorphic collection.

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
<td align="left"><p><strong>componentDescriptors</strong></p>
<p><code>List​&lt;​​&gt;​</code></p></td>
<td align="left"><p>Registers the list of component descriptors to build the enumeration values/icons from their names and icons.</p></td>
</tr>
</tbody>
</table>

RangeEnumerationPropertyDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a special enumeration descriptor that allows to build the enumeration values out of a list of integer values. Obviously, no icon is provided for a given value.

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
<td align="left"><p><strong>maxValue</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>The enumeration maximum bound. Default value is <em>10</em>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>minValue</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>The enumeration minimum bound. Default value is <em>0</em>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rangeStep</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>The step to use for constructing the enumeration values, starting from {@code minValue} up to {@code maxValue}. Default value is <em>1</em>.</p></td>
</tr>
</tbody>
</table>

TimeZoneEnumerationPropertyDescriptor
-------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicBinaryPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Describes a property used to store a binary value in the form of a byte array.

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
<td align="left"><p><strong>contentType</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the default content type to use when downloading the property content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fileFilter</strong></p>
<p><code>Map​&lt;​String​,List​&gt;​</code></p></td>
<td align="left"><p>This property allows to configure the file filter that has to be displayed whenever a file system operation is initiated from the UI to operate on this property. This includes :</p>
<ul>
<li><p>setting the property binary value from a file loaded from the file system</p></li>
<li><p>saving the property binary value to a file on the file system</p></li>
</ul>
<p>Jspresso provides built-in actions that do the above and configure their UI automatically based on the {@code fileFilter} property.</p>
<p>The incoming {@code Map} must be structured like following :</p>
<ul>
<li><p>keys are translation keys that will be translated by Jspresso i18n layer and presented to the user as the group name of the associated extensions, e.g. <em>&quot;JPEG images&quot;</em></p></li>
<li><p>values are the extension list associated to a certain group name, e.g. a list containing <em>[&quot;.jpeg&quot;,&quot;.jpg&quot;]</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>fileName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the default file name to use when downloading the property content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>maxLength</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Sets the max size (in bytes) of the property value.</p></td>
</tr>
</tbody>
</table>

BasicImageBinaryPropertyDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to store an image binary value. This type of descriptor instructs Jspresso to use an image component to interact with this type of property.

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
<td align="left"><p><strong>formatName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets format name. When set to something not null (e.g. PNG, JPG, ...), the image is transformed to the specified format before being stored.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scaledHeight</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Sets scaled height. This property, when set to a positive integer will force the image height to be resized to the target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect ratio.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>scaledWidth</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Sets scaled width. This property, when set to a positive integer will force the image width to be resized to the target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect ratio.</p></td>
</tr>
</tbody>
</table>

BasicJavaSerializablePropertyDescriptor
---------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to store any java {@code Serializable} object. The property value is serialized/de-serialized to/from the data store. The operation is completely transparent to the developer, i.e. the developer never plays with the serialized form.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicBooleanPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicColorPropertyDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used for storing a color. Color values are stored in the property as their string hexadecimal representation (*0xargb* encoded). Jspresso cleanly handles color properties in views for both visually displaying and editing them without any extra effort. Moreover the {@code ColorHelper} helper class eases colors manipulation and helps converting to/from their hexadecimal representation.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicDatePropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a date based property. Whether the date property should include time information or not, can be configured using the type property.

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
<td align="left"><p><strong>formatPattern</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets format pattern. Allows to override the default one.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>secondsAware</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Should this time information include seconds.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>timeZoneAware</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets whether this date property should have its string representation vary depending on the client timezone.</p>
<p>Default value is {@code false}, meaning that the date is considered as a string. It is in fact expressed in the server timezone.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>type</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets whether this property should contain time information or not. The incoming value must be part of the {@code EDateType} enum, i.e. :</p>
<ul>
<li><p>{@code DATE} if the property should only contain the date information</p></li>
<li><p>{@code DATE_TIME} if the property should contain both date and time information</p></li>
</ul>
<p>Default value is {@code EDateType.DATE}.</p></td>
</tr>
</tbody>
</table>

BasicDurationPropertyDescriptor
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to store a duration value. Duration is stored in the form of a number of milliseconds. duration properties are cleanly handled by Jspresso UI layer for both displaying / editing duration properties in a convenient human format.

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
<td align="left"><p><strong>maxMillis</strong></p>
<p><code>Long</code></p></td>
<td align="left"><p>Configures the maximum duration value this property accepts in milliseconds. Default value is {@code null}, meaning unbound.</p></td>
</tr>
</tbody>
</table>

BasicNumberPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

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
<td align="left"><p><strong>maxValue</strong></p>
<p><code>Big​Decimal</code></p></td>
<td align="left"><p>Configures the upper bound of the allowed values. Default value is {@code null}, meaning unbound.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>minValue</strong></p>
<p><code>Big​Decimal</code></p></td>
<td align="left"><p>Configures the lower bound of the allowed values. Default value is {@code null}, meaning unbound.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>thousandsGroupingUsed</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets thousands grouping used.</p></td>
</tr>
</tbody>
</table>

BasicDecimalPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Describes a decimal property. Property value is either stored as a {@code Double} or as a {@code BigDecimal} depending on the {@code usingBigDecimal} property.

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
<td align="left"><p><strong>maxFractionDigit</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Configures the precision of the decimal property. Default value is {@code 2}.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>usingBigDecimal</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures the property to be managed using {@code java.math.BigDecimal}. Default value is {@code false} which means {@code java.lang.Double} will be used.</p></td>
</tr>
</tbody>
</table>

BasicPercentPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a specialization of decimal descriptor to handle percentage values. The impact of using this descriptor is only on the UI level that will be configured accordingly, i.e. displaying/editing properties as percentage instead of their raw decimal values.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicIntegerPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes an integer property. The property is either represented as an {@code Integer} or a {@code Long} depending on the {@code usingLong} property.

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
<td align="left"><p><strong>usingLong</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures the property to be managed using {@code java.lang.Long}. Default value is {@code false} which means {@code java.lang.Integer} will be used.</p></td>
</tr>
</tbody>
</table>

BasicStringPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

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
<td align="left"><p><strong>maxLength</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Configures the maximum string length this property allows. Default value is {@code null} which means unlimited.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>regexpPattern</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the regular expression pattern this string property allows. Default is {@code null} which means constraint free.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>regexpPatternSample</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Allows for providing a conforming sample for the regular expression pattern. This human-readable example is used when the end-user has to be notified that the incoming property value does not match the pattern constraint.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>translatable</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Configures the string property to be translatable. Jspresso will then implement a translation store for the property so that it can be displayed in the connected user language. This is particularly useful for non-european character sets like chinese, indian, and so on. In that case, only the &quot;raw&quot; untranslated property value is stored in the object itself. the various translations are stored in an extra store. translated properties support searching, ordering, ... exactly like non-translatable properties.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>upperCase</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>This is a shortcut to implement the common use-case of handling upper-case only properties. all incoming values will be transformed to uppercase as if a property processor was registered to perform the transformation.</p></td>
</tr>
</tbody>
</table>

BasicImageUrlPropertyDescriptor
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes an image URL property. This type of descriptor instructs Jspresso to use an image component to interact with this type of property.

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
<td align="left"><p><strong>scaledHeight</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Sets scaled height. This property, when set to a positive integer will force the image height to be resized to the target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect ratio.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scaledWidth</strong></p>
<p><code>Integer</code></p></td>
<td align="left"><p>Sets scaled width. This property, when set to a positive integer will force the image width to be resized to the target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect ratio.</p></td>
</tr>
</tbody>
</table>

BasicPasswordPropertyDescriptor
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used for password values. For obvious security reasons, this type of properties will hardly be part of a persistent entity. However it is useful for defining transient view models, e.g. for implementing a change password action. Jspresso will automatically adapt view fields accordingly, using password fields, to interact with password properties.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicTextPropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Describes a multi-line text property. This type of descriptor instructs Jspresso to use a multi-line text component to interact with this type of property.

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
<td align="left"><p><strong>contentType</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the default content type to use when downloading the property content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>fileFilter</strong></p>
<p><code>Map​&lt;​String​,List​&gt;​</code></p></td>
<td align="left"><p>This property allows to configure the file filter that has to be displayed whenever a file system operation is initiated from the UI to operate on this property. This includes :</p>
<ul>
<li><p>setting the property value from a text file loaded from the file system</p></li>
<li><p>saving the property text value to a file on the file system</p></li>
</ul>
<p>Jspresso provides built-in actions that do the above and configure their UI automatically based on the {@code fileFilter} property.</p>
<p>The incoming {@code Map} must be structured like following :</p>
<ul>
<li><p>keys are translation keys that will be translated by Jspresso i18n layer and presented to the user as the group name of the associated extensions, e.g. <em>&quot;HTML files&quot;</em></p></li>
<li><p>values are the extension list associated to a certain group name, e.g. a list containing <em>[&quot;.html&quot;,&quot;.htm&quot;]</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>fileName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the default file name to use when downloading the property content as a file.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>queryMultiline</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>This property allows to control if the text property view should be transformed into a multi-line text view in order to allow for multi-line text in filters. Default value is {@code false}.</p></td>
</tr>
</tbody>
</table>

BasicHtmlPropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property as handing HTML content. This instructs Jspresso to display the property value as HTML instead of raw text content.

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
<tr class="odd">
<td align="left">This class does not have any specific property.</td>
</tr>
</tbody>
</table>

BasicSourceCodePropertyDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property as handing sourcecode content. This instructs Jspresso to display the property value as sourcecode, using syntax coloring for instance, instead of displaying un-formatted raw content. The language used to format the property text content may be defined explicitly using the {@code language} property.

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
<td align="left"><p><strong>language</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Explicitly sets the language this sourcecode property should contain. This is only a hint fo Jspresso to configure the UI components accordingly to interact with this property.</p></td>
</tr>
</tbody>
</table>

BasicTimePropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to hold time only values. These properties use a {@code Date} to store their value but only the time part of the value is relevant.

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
<td align="left"><p><strong>formatPattern</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets format pattern. Allows to override the default one.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>secondsAware</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Should this time information include seconds.</p></td>
</tr>
</tbody>
</table>


