Reference for BasicRelationshipEndPropertyDescriptor hierarchy
==============================================================

BasicRelationshipEndPropertyDescriptor
--------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This is the abstract base descriptor for all relationship properties. relationship properties include :

-   *reference* properties, i.e. "N to 1" or "1 to 1" properties

-   *collection* properties, i.e. "1 to N" or "N to N" properties

Other type of properties are named *scalar* properties.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **batchSize**            | This property allows to finely tune batching     |
|                          | strategy of the ORM on this relationship end.    |
| `Integer`                | Whenever possible, the ORM will use a IN clause  |
|                          | in order to fetch multiple instances             |
|                          | relationships at once. The batch size determines |
|                          | the size of th IN clause.                        |
+--------------------------+--------------------------------------------------+
| **composition**          | Instructs the framework that this property has   |
|                          | to be treated as a *composition*, in the UML     |
| `boolean`                | terminology. This implies that reachable         |
|                          | entities that are referenced by this property    |
|                          | follow the owning entity lifecycle. For          |
|                          | instance, when the owning entity is deleted, the |
|                          | referenced entities in composition properties    |
|                          | are also deleted.                                |
|                          |                                                  |
|                          | Whenever this property is not explicitly set by  |
|                          | the developer, Jspresso uses sensible defaults : |
|                          |                                                  |
|                          | -   *collection properties* are compositions     |
|                          |     **unless** they are bidirectional "N to N"   |
|                          |                                                  |
|                          | -   *reference properties* are not composition   |
|                          |                                                  |
|                          | This property is strictly behavioural and does   |
|                          | not impact the domain state itself.              |
+--------------------------+--------------------------------------------------+
| **fetchType**            | This property allows to finely tune fetching     |
|                          | strategy of the ORM on this relationship end.    |
| ``                       | This is either a value of the {@code EFetchType} |
|                          | enum or its equivalent string representation :   |
|                          |                                                  |
|                          | -   {@code SELECT} for default 2nd select        |
|                          |     strategy (lazy)                              |
|                          |                                                  |
|                          | -   {@code SUBSELECT} for default 2nd select     |
|                          |     strategy (lazy) using an IN clause           |
|                          |                                                  |
|                          | -   {@code JOIN} for a join select strategy (not |
|                          |     lazy)                                        |
|                          |                                                  |
|                          | Default value is {@code EFetchType.SELECT}, i.e. |
|                          | 2nd select strategy.                             |
+--------------------------+--------------------------------------------------+
| **fkName**               | Gives the developer the opportunity to customize |
|                          | the generated foreign key (if any) name.         |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **name**                 | Assign reverse temp relation end if set.         |
|                          |                                                  |
| `String`                 | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **reverseRelationEnd**   | Allows to make a relationship bi-directional. By |
|                          | default, when a relationship end is defined, it  |
| ``                       | is only navigable from the owning component to   |
|                          | the described end (default value is {@code       |
|                          | null}). Assigning a reverse relationship ends    |
|                          | instructs the framework that the relationship is |
|                          | bi-directional. This implies several             |
|                          | complementary features :                         |
|                          |                                                  |
|                          | -   When one of the relationship ends is         |
|                          |     updated, the other side is automatically     |
|                          |     maintained by Jspresso, i.e. you never have  |
|                          |     to worry about reverse state. For instance,  |
|                          |     considering a {@code Invoice} - {@code       |
|                          |     InvoiceLine} bi-directional relationship,    |
|                          |     {@code InvoiceLine.setInvoice(Invoice)} and  |
|                          |     {@code                                       |
|                          |     Invoice.addToInvoiceLines(InvoiceLine)} are  |
|                          |     strictly equivalent.                         |
|                          |                                                  |
|                          | -   You can qualify a "N-N" relationship (thus   |
|                          |     creating an association table in the data    |
|                          |     store behind the scene) by assigning 2       |
|                          |     collection property descriptors as reverse   |
|                          |     relation ends of each other.                 |
|                          |                                                  |
|                          | -   You can qualify a "1-1" relationship (thus   |
|                          |     enforcing some unicity constraint in the     |
|                          |     data store behind the scene) by assigning 2  |
|                          |     reference property descriptors as reverse    |
|                          |     relation ends of each other.                 |
|                          |                                                  |
|                          | Setting the reverse relation end operation is    |
|                          | commutative so that it automatically assigns bot |
|                          | ends as reverse, i.e. you only have to set the   |
|                          | property on one side of the relationship.        |
+--------------------------+--------------------------------------------------+

: BasicRelationshipEndPropertyDescriptor properties

BasicCollectionPropertyDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor is used to describe collection properties that are used either as "1-N" or "N-N" "N" relationship end.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **manyToMany**           | Forces the collection property to be considered  |
|                          | as a many to many ("N-N") end. When a            |
| `boolean`                | relationship is bi-directional, setting both     |
|                          | ends as being collection properties turns {@code |
|                          | manyToMany=true} automatically. But when the     |
|                          | relationship is not bi-directional, Jspresso has |
|                          | no mean to determine if the collection property  |
|                          | is "1-N" or "N-N". Setting this property allows  |
|                          | to inform Jspresso about it.                     |
|                          |                                                  |
|                          | Default value is {@code false}.                  |
+--------------------------+--------------------------------------------------+
| **orderingProperties**   | Ordering properties are used to sort this        |
|                          | collection property if and only if it is         |
| `Map​<​String​,?​>​`     | un-indexed (not a {@code List}). The sort order  |
|                          | set on the collection property can refine the    |
|                          | default one that might have been set on the      |
|                          | referenced collection level. This property       |
|                          | consist of a {@code Map} whose entries are       |
|                          | composed with :                                  |
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
|                          | the collection property sort order and thus,     |
|                          | will delegate to higher specification levels     |
|                          | (i.e. the referenced collection sort order).     |
+--------------------------+--------------------------------------------------+
| **referencedDescriptor** | Qualifies the type of collection this property   |
|                          | refers to. As of now, Jspresso supports :        |
| `​<​E​>​`                |                                                  |
|                          | -   collections with {@code Set} semantic: do    |
|                          |     not allow for duplicates and do not preserve |
|                          |     the order of the elements in the data store  |
|                          |                                                  |
|                          | -   collections with {@code List} semantic:      |
|                          |     allows for duplicates and preserves the      |
|                          |     order of the elements in the data store      |
|                          |     through an implicit index column             |
+--------------------------+--------------------------------------------------+

: BasicCollectionPropertyDescriptor properties

BasicReferencePropertyDescriptor
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Default implementation of a reference descriptor.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **initializationMapping* | This property allows to pre-initialize UI        |
| *                        | filters that are based on this reference         |
|                          | property. This includes :                        |
| `Map​<​String​,Object​>​ |                                                  |
| `                        | -   explicit filters that are displayed for      |
|                          |     "list of values"                             |
|                          |                                                  |
|                          | -   implicit filters that are use behind the     |
|                          |     scene for UI auto-completion                 |
|                          |                                                  |
|                          | The initialization mapping property is a {@code  |
|                          | Map} keyed by referenced type property names     |
|                          | (the properties to be initialized).              |
|                          |                                                  |
|                          | Values in this map can be either :               |
|                          |                                                  |
|                          | -   a **constant value**. In that case, the      |
|                          |     filter property is initialize with this      |
|                          |     constant value.                              |
|                          |                                                  |
|                          | -   a owning component **property name**. In     |
|                          |     that case, the filter property is initialize |
|                          |     with the value of the owning component       |
|                          |     property.                                    |
+--------------------------+--------------------------------------------------+
| **oneToOne**             | Forces the reference property to be considered   |
|                          | as a one to one ("1-1") end. When a relationship |
| `boolean`                | is bi-directional, setting both ends as being    |
|                          | reference properties turns {@code oneToOne=true} |
|                          | automatically. But when the relationship is not  |
|                          | bi-directional, Jspresso has no mean to          |
|                          | determine if the reference property is "N-1" or  |
|                          | "1-1". Setting this property allows to inform    |
|                          | Jspresso about it.                               |
|                          |                                                  |
|                          | Default value is {@code false}.                  |
+--------------------------+--------------------------------------------------+
| **pageSize**             | This property allows for defining the page size  |
|                          | of "lists of values" that are built by the UI    |
| `Integer`                | for this reference property. Whenever the {@code |
|                          | pageSize} property is set to {@code null} on the |
|                          | reference property level, Jspresso falls back to |
|                          | the element type default page size or turns off  |
|                          | paging if the former is also not set.            |
+--------------------------+--------------------------------------------------+
| **queryableProperties**  | This property allows to define which of the      |
|                          | component properties are to be used in the list  |
| `List​<​String​>​`       | of value filter that are based on this component |
|                          | family. Since this is a {@code List} queryable   |
|                          | properties are rendered in the same order.       |
|                          |                                                  |
|                          | Whenever this this property is {@code null}      |
|                          | (default value), Jspresso chooses the default    |
|                          | set of queryable properties based on the         |
|                          | referenced component descriptor.                 |
+--------------------------+--------------------------------------------------+
| **referencedDescriptor** | Qualifies the type of element this property      |
|                          | refers to. It may point to any type of component |
| `​<​?​>​`                | descriptor, i.e. entity, interface or component  |
|                          | descriptor.                                      |
+--------------------------+--------------------------------------------------+
| **renderedProperties**   | This property allows to define which of the      |
|                          | component properties are to be rendered by       |
| `List​<​String​>​`       | default when displaying a list of value on this  |
|                          | component family. For instance, a table will     |
|                          | render 1 column per rendered property of the     |
|                          | component. Any type of property can be used      |
|                          | except collection properties. Since this is a    |
|                          | {@code List} queryable properties are rendered   |
|                          | in the same order.                               |
|                          |                                                  |
|                          | Whenever this property is {@code null} (default  |
|                          | value) Jspresso determines the default set of    |
|                          | properties to render based on the referenced     |
|                          | component descriptor.                            |
+--------------------------+--------------------------------------------------+

: BasicReferencePropertyDescriptor properties

EnumQueryStructureDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

A query structure used to implement enumeration disjunctions in filters.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EnumQueryStructureDescriptor properties


