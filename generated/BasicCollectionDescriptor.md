Reference for BasicCollectionDescriptor hierarchy
=================================================

BasicCollectionDescriptor
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This descriptor is used to describe a collection of components
(entities, interfaces or components). This descriptor is mainly used to
qualify the collection referenced by a collection property descriptor.
As of now, Jspresso supports :

-   collections with {@code Set} semantic: do not allow for duplicates
    and do not preserve the order of the elements in the data store

-   collections with {@code List} semantic: allows for duplicates and
    preserves the order of the elements in the data store through an
    implicit index column

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **collectionInterface**  | Allows to choose between the supported           |
|                          | collection semantics. The incoming class         |
| `Class​<​?​>​`           | property value must be one of :                  |
|                          |                                                  |
|                          | -   {@code java.util.Set}                        |
|                          |                                                  |
|                          | -   {@code java.util.List}                       |
|                          |                                                  |
|                          | Any other value is not supported and make the    |
|                          | descriptor fall back to its default. A {@code    |
|                          | null} value (default) is equivalent to setting   |
|                          | {@code java.util.Set}. Alternatively, you can    |
|                          | use descriptor sub-types, i.e. {@code            |
|                          | BasicSetDescriptor} and {@code                   |
|                          | BasicListDescriptor} that make this property     |
|                          | usage useless since they enforce their           |
|                          | collection interface.                            |
+--------------------------+--------------------------------------------------+
| **elementDescriptor**    | Describes the elements contained in this         |
|                          | collection. It can be any of entity, interface   |
| `​<​?​>​`                | or component descriptor.                         |
+--------------------------+--------------------------------------------------+
| **nullElementAllowed**   | Configures the collection to accept null element |
|                          | values or not. If the collection does not allows |
| `boolean`                | for null values, it forbids to have holes in     |
|                          | lists, i.e. all elements have consecutive        |
|                          | indices.                                         |
+--------------------------+--------------------------------------------------+
| **orderingProperties**   | Ordering properties are used to sort this        |
|                          | collection if and only if it is un-indexed (not  |
| `Map​<​String​,?​>​`     | a {@code List}). The sort order set on the       |
|                          | collection can refine the default one that might |
|                          | have been set on the element type level. This    |
|                          | property consist of a {@code Map} whose entries  |
|                          | are composed with :                              |
|                          |                                                  |
|                          | -   the property name as key                     |
|                          |                                                  |
|                          | -   the sort order for this property as value.   |
|                          |     This is either a value of the {@code ESort}  |
|                          |     enum (*ASCENDING* or *DESCENDING*) or its    |
|                          |     equivalent string representation.            |
|                          |                                                  |
|                          | Ordering properties are considered following     |
|                          | their order in the map iterator. A {@code null}  |
|                          | value (default) will not give any indication for |
|                          | the collection sort order and thus, will         |
|                          | delegate to higher specification levels (e.g.    |
|                          | the element type sort order).                    |
+--------------------------+--------------------------------------------------+

: BasicCollectionDescriptor properties

BasicListDescriptor
-------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor is equivalent to a {@code BasicCollectionDescriptor}
with its {@code collectionInterface} property set to {@code
java.util.List}. Using this descriptor prevents messing up with
technical implementation details.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicListDescriptor properties

BasicSetDescriptor
------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor is equivalent to a {@code BasicCollectionDescriptor}
with its {@code collectionInterface} property set to {@code
java.util.Set}. Using this descriptor prevents messing up with technical
implementation details.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicSetDescriptor properties


