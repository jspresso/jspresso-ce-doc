Reference for AbstractGate hierarchy
====================================

AbstractGate
------------

-   **Full name** : ``

-   **Super-type** : `AbstractPropertyChangeCapable`

-   **Sub-types** : ``, ``, ``

This is the base abstract class of all Jspresso built-in gates.
Open/close rule is delegated to concrete implementations.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : AbstractGate properties

AbstractModelGate
-----------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This is the base abstract implementation for gates that are model-based.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **collectionBased**      | Sets the collectionBased.                        |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractModelGate properties

AbstractPropertyModelGate
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

This is the base abstract class of gates whose opening rules are based
on a single model property value.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **accessorFactory**      | Configures the accessor factory to use to access |
|                          | the underlying model property.                   |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **grantedRoles**         | Configures the roles for which the gate is       |
|                          | installed. It supports "**!**" prefix to negate  |
| `Collection​<​String​>​` | the role(s).                                     |
+--------------------------+--------------------------------------------------+
| **openOnTrue**           | This property allows to revert the standard      |
|                          | behaviour of the gate, i.e. close when it should |
| `boolean`                | normally have opened and the other way around.   |
+--------------------------+--------------------------------------------------+
| **propertyName**         | Configures the model property name to which this |
|                          | gate is attached. How the property value is      |
| `String`                 | actually linked to the gate state is delegated   |
|                          | to the concrete implementations.                 |
+--------------------------+--------------------------------------------------+

: AbstractPropertyModelGate properties

BooleanPropertyModelGate
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This gate opens and closes based on the value of a boolean property of
the assigned model.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **propertyName**         | Configures the boolean property name to use.     |
|                          | Unless the {@code openOnTrue} property is set to |
| `String`                 | {@code false}, the state of the gate will follow |
|                          | the boolean property value. It supports "**!**"  |
|                          | prefix to negate the property value. It also     |
|                          | supports non-boolean properties. In that case,   |
|                          | the test is performed against the {@code         |
|                          | property != null} condition.                     |
+--------------------------+--------------------------------------------------+

: BooleanPropertyModelGate properties

EnumerationPropertyModelGate
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This gate opens and closes based on the value of an enumeration property
matching a set of allowed values.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **openingValues**        | Configures the enumeration values for which the  |
|                          | gate is to be open, unless the {@code            |
| `Collection​<​String​>​` | openOnTrue} property is set to {@code false}.    |
+--------------------------+--------------------------------------------------+

: EnumerationPropertyModelGate properties

RegexPropertyModelGate
----------------------

-   **Full name** : ``

-   **Super-type** : ``

This gate opens and closes based on the value of a string property
matching a regular expression.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **regexpPattern**        | Configures the regular expression to match the   |
|                          | property value against. The gate will open if    |
| `String`                 | the property value matches the regex unless the  |
|                          | {@code openOnTrue} property has been set to      |
|                          | false.                                           |
+--------------------------+--------------------------------------------------+

: RegexPropertyModelGate properties

ClosedGate
----------

-   **Full name** : ``

-   **Super-type** : ``

An always closed gate.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ClosedGate properties

GrantedRolesGate
----------------

-   **Full name** : ``

-   **Super-type** : ``

This is a role based gate. The gate depends only on the roles of the
logged-in user. The difference between using a roles gate and directly
assigning the granted roles on the authorized artifact, is that the gate
only disables the artifact whereas the artifact granted roles prevent
the artifact from being created at all.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **grantedRoles**         | Configures the roles for which the gate is open. |
|                          | It supports "**!**" prefix to negate the         |
| `Collection​<​String​>​` | role(s). If at least one of the role is          |
|                          | satisfied, then the gate is open.                |
+--------------------------+--------------------------------------------------+

: GrantedRolesGate properties


