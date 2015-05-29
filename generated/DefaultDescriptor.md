Reference for DefaultDescriptor hierarchy
=========================================

DefaultDescriptor
-----------------

-   **Full name** : ``

-   **Sub-types** : ``, ``

This is a utility class from which most named descriptors inherit for factorization purpose. It provides translatable name and description.

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
<td align="left"><p><strong>description</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the description of this descriptor. Most of the descriptor descriptions are used in conjunction with the Jspresso i18n layer so that the description property set here is actually an i18n key used for translation. Description is mainly used for UI (in toolTips for instance) but may also be used for project technical documentation, contextual help, and so on.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>i18nNameKey</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the I18N key used for translation if it differs from the name itself.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the name of this descriptor. Most of the descriptor names are used in conjunction with the Jspresso i18n layer so that the name property set here is actually an i18n key used for translation. The descriptor name property semantic may vary depending on the actual descriptor type. For instance, a property descriptor name is the name of the property and a component descriptor name is the fully qualified name of the underlying class.</p></td>
</tr>
</tbody>
</table>

DefaultIconDescriptor
---------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``

This is a utility class from which most displayable descriptors inherit for factorization purpose. It provides an icon image URL.

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
<td align="left"><p><strong>icon</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the icon.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconImageURL</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets the icon image URL of this descriptor. Supported URL protocols include :</p>
<ul>
<li><p>all JVM supported protocols</p></li>
<li><p>the <strong>jar:/</strong> pseudo URL protocol</p></li>
<li><p>the <strong>classpath:/</strong> pseudo URL protocol</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>iconPreferredHeight</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>Sets the icon preferred height.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconPreferredWidth</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>Sets the icon preferred width.</p></td>
</tr>
</tbody>
</table>


