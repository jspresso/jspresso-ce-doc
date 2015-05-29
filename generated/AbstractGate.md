Reference for AbstractGate hierarchy
====================================

AbstractGate
------------

-   **Full name** : ``

-   **Super-type** : `AbstractPropertyChangeCapable`

-   **Sub-types** : ``, ``, ``

This is the base abstract class of all Jspresso built-in gates. Open/close rule is delegated to concrete implementations.

<table>
<caption>AbstractGate properties</caption>
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

AbstractModelGate
-----------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This is the base abstract implementation for gates that are model-based.

<table>
<caption>AbstractModelGate properties</caption>
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
<td align="left"><p><strong>collectionBased</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets the collectionBased.</p></td>
</tr>
</tbody>
</table>

AbstractPropertyModelGate
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

This is the base abstract class of gates whose opening rules are based on a single model property value.

<table>
<caption>AbstractPropertyModelGate properties</caption>
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
<td align="left"><p><strong>accessorFactory</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the accessor factory to use to access the underlying model property.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>grantedRoles</strong></p>
<p><code>Collection​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Configures the roles for which the gate is installed. It supports &quot;<strong>!</strong>&quot; prefix to negate the role(s).</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>openOnTrue</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>This property allows to revert the standard behaviour of the gate, i.e. close when it should normally have opened and the other way around.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>propertyName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the model property name to which this gate is attached. How the property value is actually linked to the gate state is delegated to the concrete implementations.</p></td>
</tr>
</tbody>
</table>

BooleanPropertyModelGate
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This gate opens and closes based on the value of a boolean property of the assigned model.

<table>
<caption>BooleanPropertyModelGate properties</caption>
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
<td align="left"><p><strong>propertyName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the boolean property name to use. Unless the {@code openOnTrue} property is set to {@code false}, the state of the gate will follow the boolean property value. It supports &quot;<strong>!</strong>&quot; prefix to negate the property value. It also supports non-boolean properties. In that case, the test is performed against the {@code property != null} condition.</p></td>
</tr>
</tbody>
</table>

EnumerationPropertyModelGate
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This gate opens and closes based on the value of an enumeration property matching a set of allowed values.

<table>
<caption>EnumerationPropertyModelGate properties</caption>
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
<td align="left"><p><strong>openingValues</strong></p>
<p><code>Collection​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Configures the enumeration values for which the gate is to be open, unless the {@code openOnTrue} property is set to {@code false}.</p></td>
</tr>
</tbody>
</table>

RegexPropertyModelGate
----------------------

-   **Full name** : ``

-   **Super-type** : ``

This gate opens and closes based on the value of a string property matching a regular expression.

<table>
<caption>RegexPropertyModelGate properties</caption>
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
<td align="left"><p><strong>regexpPattern</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Configures the regular expression to match the property value against. The gate will open if the property value matches the regex unless the {@code openOnTrue} property has been set to false.</p></td>
</tr>
</tbody>
</table>

ClosedGate
----------

-   **Full name** : ``

-   **Super-type** : ``

An always closed gate.

<table>
<caption>ClosedGate properties</caption>
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

GrantedRolesGate
----------------

-   **Full name** : ``

-   **Super-type** : ``

This is a role based gate. The gate depends only on the roles of the logged-in user. The difference between using a roles gate and directly assigning the granted roles on the authorized artifact, is that the gate only disables the artifact whereas the artifact granted roles prevent the artifact from being created at all.

<table>
<caption>GrantedRolesGate properties</caption>
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
<td align="left"><p><strong>grantedRoles</strong></p>
<p><code>Collection​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Configures the roles for which the gate is open. It supports &quot;<strong>!</strong>&quot; prefix to negate the role(s). If at least one of the role is satisfied, then the gate is open.</p></td>
</tr>
</tbody>
</table>


