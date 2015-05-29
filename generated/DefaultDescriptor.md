Reference for DefaultDescriptor hierarchy
=========================================

DefaultDescriptor
-----------------

-   **Full name** : ``

-   **Sub-types** : ``, ``

This is a utility class from which most named descriptors inherit for
factorization purpose. It provides translatable name and description.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **description**          | Sets the description of this descriptor. Most of |
|                          | the descriptor descriptions are used in          |
| `String`                 | conjunction with the Jspresso i18n layer so that |
|                          | the description property set here is actually an |
|                          | i18n key used for translation. Description is    |
|                          | mainly used for UI (in toolTips for instance)    |
|                          | but may also be used for project technical       |
|                          | documentation, contextual help, and so on.       |
+--------------------------+--------------------------------------------------+
| **i18nNameKey**          | Sets the I18N key used for translation if it     |
|                          | differs from the name itself.                    |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **name**                 | Sets the name of this descriptor. Most of the    |
|                          | descriptor names are used in conjunction with    |
| `String`                 | the Jspresso i18n layer so that the name         |
|                          | property set here is actually an i18n key used   |
|                          | for translation. The descriptor name property    |
|                          | semantic may vary depending on the actual        |
|                          | descriptor type. For instance, a property        |
|                          | descriptor name is the name of the property and  |
|                          | a component descriptor name is the fully         |
|                          | qualified name of the underlying class.          |
+--------------------------+--------------------------------------------------+

: DefaultDescriptor properties

DefaultIconDescriptor
---------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``

This is a utility class from which most displayable descriptors inherit
for factorization purpose. It provides an icon image URL.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **icon**                 | Sets the icon.                                   |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **iconImageURL**         | Sets the icon image URL of this descriptor.      |
|                          | Supported URL protocols include :                |
| `String`                 |                                                  |
|                          | -   all JVM supported protocols                  |
|                          |                                                  |
|                          | -   the **jar:/** pseudo URL protocol            |
|                          |                                                  |
|                          | -   the **classpath:/** pseudo URL protocol      |
+--------------------------+--------------------------------------------------+
| **iconPreferredHeight**  | Sets the icon preferred height.                  |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **iconPreferredWidth**   | Sets the icon preferred width.                   |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+

: DefaultIconDescriptor properties


