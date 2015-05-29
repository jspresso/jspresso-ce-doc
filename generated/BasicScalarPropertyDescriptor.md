Reference for BasicScalarPropertyDescriptor hierarchy
=====================================================

BasicScalarPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``, ``, ``, ``

This is the root abstract descriptor for all property descriptors that are not relationship end properties. This includes, for instance, strings, numbers, dates, binary content, and so on.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **defaultValue**         | Sets the property default value. When a          |
|                          | component owning this property is instantiated,  |
| `Object`                 | its properties are initialized using their       |
|                          | default values. By default, a property default   |
|                          | value is {@code null}.                           |
|                          |                                                  |
|                          | This incoming value can be either the actual     |
|                          | property default value (as an {@code Object}) or |
|                          | its string representation whose parsing will be  |
|                          | delegated to the property descriptor.            |
+--------------------------+--------------------------------------------------+

: BasicScalarPropertyDescriptor properties

AbstractEnumerationPropertyDescriptor
-------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

Abstract base descriptor for properties whose values are enumerated strings. An example of such a property is *gender* whose value can be *M* (for "Male") or *F* (for "Female"). Actual property values can be codes that are translated for inclusion in the UI. Such properties are usually rendered as combo-boxes.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **enumerationName**      | This property allows to customize the i18n keys  |
|                          | used to translate the enumeration values, thus   |
| `String`                 | keeping the actual values shorter. For instance  |
|                          | consider the *gender* enumeration, composed of   |
|                          | the *M* (for "Male") and *F* (for "Female")      |
|                          | values. Setting an enumeration name to "GENDER"  |
|                          | will instruct Jspresso to look for translations  |
|                          | named "GENDER\_M" and "GENDER\_F". This would    |
|                          | allow for using *M* and *F* in other enumeration |
|                          | domains with different semantics and             |
|                          | translations.                                    |
+--------------------------+--------------------------------------------------+
| **maxLength**            | Sets the maxLength.                              |
|                          |                                                  |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+
| **queryMultiselect**     | This property allows to control if the           |
|                          | enumeration property view should be transformed  |
| `boolean`                | into a multi-selectable property view in order   |
|                          | to allow for value disjunctions in filters.      |
|                          | Default value is {@code false}.                  |
+--------------------------+--------------------------------------------------+

: AbstractEnumerationPropertyDescriptor properties

BasicEnumerationPropertyDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Describes an enumerated property containing arbitrary values.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **values**               | Defines the list of values this enumeration      |
|                          | contains.                                        |
| `List​<​String​>​`       |                                                  |
|                          | Enumeration values are translated in the UI      |
|                          | using the following scheme :                     |
|                          | *[enumerationName]\_[value]*.                    |
+--------------------------+--------------------------------------------------+
| **valuesAndIconImageUrls | Defines the list of values as well as an icon    |
| **                       | image URL per value this enumeration contains.   |
|                          | The incoming {@code Map} is keyed by the actual  |
| `Map​<​String​,String​>​ | enumeration values and valued by the icon image  |
| `                        | URLs.                                            |
|                          |                                                  |
|                          | Enumeration values are translated in the UI      |
|                          | using the following scheme :                     |
|                          | *[enumerationName]\_[value]*.                    |
+--------------------------+--------------------------------------------------+

: BasicEnumerationPropertyDescriptor properties

TypeEnumerationPropertyDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a special enumeration descriptor that allows to build the enumeration out of a list of component descriptors. Enumeration values and icons are the names and icons of the registered component descriptors. For instance, this can be useful in the UI if you want to visually indicate the actual type of a element contained in a polymorphic collection.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **componentDescriptors** | Registers the list of component descriptors to   |
|                          | build the enumeration values/icons from their    |
| `List​<​​>​`             | names and icons.                                 |
+--------------------------+--------------------------------------------------+

: TypeEnumerationPropertyDescriptor properties

RangeEnumerationPropertyDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a special enumeration descriptor that allows to build the enumeration values out of a list of integer values. Obviously, no icon is provided for a given value.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **maxValue**             | The enumeration maximum bound. Default value is  |
|                          | *10*.                                            |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+
| **minValue**             | The enumeration minimum bound. Default value is  |
|                          | *0*.                                             |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+
| **rangeStep**            | The step to use for constructing the enumeration |
|                          | values, starting from {@code minValue} up to     |
| `Integer`                | {@code maxValue}. Default value is *1*.          |
+--------------------------+--------------------------------------------------+

: RangeEnumerationPropertyDescriptor properties

TimeZoneEnumerationPropertyDescriptor
-------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a special enumeration descriptor that holds all available timezones.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : TimeZoneEnumerationPropertyDescriptor properties

BasicBinaryPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Describes a property used to store a binary value in the form of a byte array.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **contentType**          | Configures the default content type to use when  |
|                          | downloading the property content as a file.      |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **fileFilter**           | This property allows to configure the file       |
|                          | filter that has to be displayed whenever a file  |
| `Map​<​String​,List​>​`  | system operation is initiated from the UI to     |
|                          | operate on this property. This includes :        |
|                          |                                                  |
|                          | -   setting the property binary value from a     |
|                          |     file loaded from the file system             |
|                          |                                                  |
|                          | -   saving the property binary value to a file   |
|                          |     on the file system                           |
|                          |                                                  |
|                          | Jspresso provides built-in actions that do the   |
|                          | above and configure their UI automatically based |
|                          | on the {@code fileFilter} property.              |
|                          |                                                  |
|                          | The incoming {@code Map} must be structured like |
|                          | following :                                      |
|                          |                                                  |
|                          | -   keys are translation keys that will be       |
|                          |     translated by Jspresso i18n layer and        |
|                          |     presented to the user as the group name of   |
|                          |     the associated extensions, e.g. *"JPEG       |
|                          |     images"*                                     |
|                          |                                                  |
|                          | -   values are the extension list associated to  |
|                          |     a certain group name, e.g. a list containing |
|                          |     *[".jpeg",".jpg"]*                           |
+--------------------------+--------------------------------------------------+
| **fileName**             | Configures the default file name to use when     |
|                          | downloading the property content as a file.      |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **maxLength**            | Sets the max size (in bytes) of the property     |
|                          | value.                                           |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+

: BasicBinaryPropertyDescriptor properties

BasicImageBinaryPropertyDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to store an image binary value. This type of descriptor instructs Jspresso to use an image component to interact with this type of property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **formatName**           | Sets format name. When set to something not null |
|                          | (e.g. PNG, JPG, ...), the image is transformed   |
| `String`                 | to the specified format before being stored.     |
+--------------------------+--------------------------------------------------+
| **scaledHeight**         | Sets scaled height. This property, when set to a |
|                          | positive integer will force the image height to  |
| `Integer`                | be resized to the target value. If only one of   |
|                          | the 2 scaled dimensions is set, then the image   |
|                          | is scaled by preserving its aspect ratio.        |
+--------------------------+--------------------------------------------------+
| **scaledWidth**          | Sets scaled width. This property, when set to a  |
|                          | positive integer will force the image width to   |
| `Integer`                | be resized to the target value. If only one of   |
|                          | the 2 scaled dimensions is set, then the image   |
|                          | is scaled by preserving its aspect ratio.        |
+--------------------------+--------------------------------------------------+

: BasicImageBinaryPropertyDescriptor properties

BasicJavaSerializablePropertyDescriptor
---------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to store any java {@code Serializable} object. The property value is serialized/de-serialized to/from the data store. The operation is completely transparent to the developer, i.e. the developer never plays with the serialized form.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicJavaSerializablePropertyDescriptor properties

BasicBooleanPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a boolean property.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicBooleanPropertyDescriptor properties

BasicColorPropertyDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used for storing a color. Color values are stored in the property as their string hexadecimal representation (*0xargb* encoded). Jspresso cleanly handles color properties in views for both visually displaying and editing them without any extra effort. Moreover the {@code ColorHelper} helper class eases colors manipulation and helps converting to/from their hexadecimal representation.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicColorPropertyDescriptor properties

BasicDatePropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a date based property. Whether the date property should include time information or not, can be configured using the type property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **formatPattern**        | Sets format pattern. Allows to override the      |
|                          | default one.                                     |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **secondsAware**         | Should this time information include seconds.    |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **timeZoneAware**        | Sets whether this date property should have its  |
|                          | string representation vary depending on the      |
| `boolean`                | client timezone.                                 |
|                          |                                                  |
|                          | Default value is {@code false}, meaning that the |
|                          | date is considered as a string. It is in fact    |
|                          | expressed in the server timezone.                |
+--------------------------+--------------------------------------------------+
| **type**                 | Sets whether this property should contain time   |
|                          | information or not. The incoming value must be   |
| ``                       | part of the {@code EDateType} enum, i.e. :       |
|                          |                                                  |
|                          | -   {@code DATE} if the property should only     |
|                          |     contain the date information                 |
|                          |                                                  |
|                          | -   {@code DATE\_TIME} if the property should    |
|                          |     contain both date and time information       |
|                          |                                                  |
|                          | Default value is {@code EDateType.DATE}.         |
+--------------------------+--------------------------------------------------+

: BasicDatePropertyDescriptor properties

BasicDurationPropertyDescriptor
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to store a duration value. Duration is stored in the form of a number of milliseconds. duration properties are cleanly handled by Jspresso UI layer for both displaying / editing duration properties in a convenient human format.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **maxMillis**            | Configures the maximum duration value this       |
|                          | property accepts in milliseconds. Default value  |
| `Long`                   | is {@code null}, meaning unbound.                |
+--------------------------+--------------------------------------------------+

: BasicDurationPropertyDescriptor properties

BasicNumberPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This is the abstract base descriptor of all numeric based properties.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **maxValue**             | Configures the upper bound of the allowed        |
|                          | values. Default value is {@code null}, meaning   |
| `Big​Decimal`            | unbound.                                         |
+--------------------------+--------------------------------------------------+
| **minValue**             | Configures the lower bound of the allowed        |
|                          | values. Default value is {@code null}, meaning   |
| `Big​Decimal`            | unbound.                                         |
+--------------------------+--------------------------------------------------+
| **thousandsGroupingUsed* | Sets thousands grouping used.                    |
| *                        |                                                  |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: BasicNumberPropertyDescriptor properties

BasicDecimalPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Describes a decimal property. Property value is either stored as a {@code Double} or as a {@code BigDecimal} depending on the {@code usingBigDecimal} property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **maxFractionDigit**     | Configures the precision of the decimal          |
|                          | property. Default value is {@code 2}.            |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+
| **usingBigDecimal**      | Configures the property to be managed using      |
|                          | {@code java.math.BigDecimal}. Default value is   |
| `boolean`                | {@code false} which means {@code                 |
|                          | java.lang.Double} will be used.                  |
+--------------------------+--------------------------------------------------+

: BasicDecimalPropertyDescriptor properties

BasicPercentPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a specialization of decimal descriptor to handle percentage values. The impact of using this descriptor is only on the UI level that will be configured accordingly, i.e. displaying/editing properties as percentage instead of their raw decimal values.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicPercentPropertyDescriptor properties

BasicIntegerPropertyDescriptor
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes an integer property. The property is either represented as an {@code Integer} or a {@code Long} depending on the {@code usingLong} property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **usingLong**            | Configures the property to be managed using      |
|                          | {@code java.lang.Long}. Default value is {@code  |
| `boolean`                | false} which means {@code java.lang.Integer}     |
|                          | will be used.                                    |
+--------------------------+--------------------------------------------------+

: BasicIntegerPropertyDescriptor properties

BasicStringPropertyDescriptor
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

Describes a string based property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **maxLength**            | Configures the maximum string length this        |
|                          | property allows. Default value is {@code null}   |
| `Integer`                | which means unlimited.                           |
+--------------------------+--------------------------------------------------+
| **regexpPattern**        | Configures the regular expression pattern this   |
|                          | string property allows. Default is {@code null}  |
| `String`                 | which means constraint free.                     |
+--------------------------+--------------------------------------------------+
| **regexpPatternSample**  | Allows for providing a conforming sample for the |
|                          | regular expression pattern. This human-readable  |
| `String`                 | example is used when the end-user has to be      |
|                          | notified that the incoming property value does   |
|                          | not match the pattern constraint.                |
+--------------------------+--------------------------------------------------+
| **translatable**         | Configures the string property to be             |
|                          | translatable. Jspresso will then implement a     |
| `boolean`                | translation store for the property so that it    |
|                          | can be displayed in the connected user language. |
|                          | This is particularly useful for non-european     |
|                          | character sets like chinese, indian, and so on.  |
|                          | In that case, only the "raw" untranslated        |
|                          | property value is stored in the object itself.   |
|                          | the various translations are stored in an extra  |
|                          | store. translated properties support searching,  |
|                          | ordering, ... exactly like non-translatable      |
|                          | properties.                                      |
+--------------------------+--------------------------------------------------+
| **upperCase**            | This is a shortcut to implement the common       |
|                          | use-case of handling upper-case only properties. |
| `boolean`                | all incoming values will be transformed to       |
|                          | uppercase as if a property processor was         |
|                          | registered to perform the transformation.        |
+--------------------------+--------------------------------------------------+

: BasicStringPropertyDescriptor properties

BasicImageUrlPropertyDescriptor
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes an image URL property. This type of descriptor instructs Jspresso to use an image component to interact with this type of property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **scaledHeight**         | Sets scaled height. This property, when set to a |
|                          | positive integer will force the image height to  |
| `Integer`                | be resized to the target value. If only one of   |
|                          | the 2 scaled dimensions is set, then the image   |
|                          | is scaled by preserving its aspect ratio.        |
+--------------------------+--------------------------------------------------+
| **scaledWidth**          | Sets scaled width. This property, when set to a  |
|                          | positive integer will force the image width to   |
| `Integer`                | be resized to the target value. If only one of   |
|                          | the 2 scaled dimensions is set, then the image   |
|                          | is scaled by preserving its aspect ratio.        |
+--------------------------+--------------------------------------------------+

: BasicImageUrlPropertyDescriptor properties

BasicPasswordPropertyDescriptor
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used for password values. For obvious security reasons, this type of properties will hardly be part of a persistent entity. However it is useful for defining transient view models, e.g. for implementing a change password action. Jspresso will automatically adapt view fields accordingly, using password fields, to interact with password properties.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicPasswordPropertyDescriptor properties

BasicTextPropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Describes a multi-line text property. This type of descriptor instructs Jspresso to use a multi-line text component to interact with this type of property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **contentType**          | Configures the default content type to use when  |
|                          | downloading the property content as a file.      |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **fileFilter**           | This property allows to configure the file       |
|                          | filter that has to be displayed whenever a file  |
| `Map​<​String​,List​>​`  | system operation is initiated from the UI to     |
|                          | operate on this property. This includes :        |
|                          |                                                  |
|                          | -   setting the property value from a text file  |
|                          |     loaded from the file system                  |
|                          |                                                  |
|                          | -   saving the property text value to a file on  |
|                          |     the file system                              |
|                          |                                                  |
|                          | Jspresso provides built-in actions that do the   |
|                          | above and configure their UI automatically based |
|                          | on the {@code fileFilter} property.              |
|                          |                                                  |
|                          | The incoming {@code Map} must be structured like |
|                          | following :                                      |
|                          |                                                  |
|                          | -   keys are translation keys that will be       |
|                          |     translated by Jspresso i18n layer and        |
|                          |     presented to the user as the group name of   |
|                          |     the associated extensions, e.g. *"HTML       |
|                          |     files"*                                      |
|                          |                                                  |
|                          | -   values are the extension list associated to  |
|                          |     a certain group name, e.g. a list containing |
|                          |     *[".html",".htm"]*                           |
+--------------------------+--------------------------------------------------+
| **fileName**             | Configures the default file name to use when     |
|                          | downloading the property content as a file.      |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **queryMultiline**       | This property allows to control if the text      |
|                          | property view should be transformed into a       |
| `boolean`                | multi-line text view in order to allow for       |
|                          | multi-line text in filters. Default value is     |
|                          | {@code false}.                                   |
+--------------------------+--------------------------------------------------+

: BasicTextPropertyDescriptor properties

BasicHtmlPropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property as handing HTML content. This instructs Jspresso to display the property value as HTML instead of raw text content.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicHtmlPropertyDescriptor properties

BasicSourceCodePropertyDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property as handing sourcecode content. This instructs Jspresso to display the property value as sourcecode, using syntax coloring for instance, instead of displaying un-formatted raw content. The language used to format the property text content may be defined explicitly using the {@code language} property.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **language**             | Explicitly sets the language this sourcecode     |
|                          | property should contain. This is only a hint fo  |
| `String`                 | Jspresso to configure the UI components          |
|                          | accordingly to interact with this property.      |
+--------------------------+--------------------------------------------------+

: BasicSourceCodePropertyDescriptor properties

BasicTimePropertyDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Describes a property used to hold time only values. These properties use a {@code Date} to store their value but only the time part of the value is relevant.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **formatPattern**        | Sets format pattern. Allows to override the      |
|                          | default one.                                     |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **secondsAware**         | Should this time information include seconds.    |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: BasicTimePropertyDescriptor properties


