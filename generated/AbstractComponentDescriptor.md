Reference for AbstractComponentDescriptor hierarchy
===================================================

AbstractComponentDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

This is the abstract base descriptor for all component-like part of the
domain model. All the properties included in this base descriptor can of
course be used in concrete sub-types. These sub-types include :

-   *BasicEntityDescriptor* for defining a persistent entity

-   *BasicInterfaceDescriptor* for defining a common interface that will
    be implemented by other entities, components or even sub-interfaces.

-   *BasicComponentDescriptor* for defining reusable structures that can
    be inline in an entity. It also allows to describe an arbitrary POJO
    and make use of it in Jspresso UIs.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **ancestorDescriptors**  | Registers this descriptor with a collection of   |
|                          | ancestors. It directly translates the components |
| `List​<​​>​`             | inheritance hierarchy since the component        |
|                          | property descriptors are the union of the        |
|                          | declared property descriptors of the component   |
|                          | and of its ancestors one. A component may have   |
|                          | multiple ancestors which means that complex      |
|                          | multiple-inheritance hierarchy can be mapped.    |
+--------------------------+--------------------------------------------------+
| **autoCompleteProperty** | Allows to customize the property used to         |
|                          | autocomplete reference fields on this component. |
| `String`                 | Whenever this property is {@code null}, the      |
|                          | following rule apply to determine the            |
|                          | *lovProperty* :                                  |
|                          |                                                  |
|                          | 1.  the toString property if not a computed one  |
|                          |                                                  |
|                          | 2.  the first string property from the rendered  |
|                          |     property                                     |
|                          |                                                  |
|                          | 3.  the first rendered property if no string     |
|                          |     property is found among them                 |
|                          |                                                  |
|                          | Note that this property is not inherited by      |
|                          | children descriptors, i.e. even if an ancestor   |
|                          | defines an explicit *lovProperty*, its children  |
|                          | ignore this setting.                             |
+--------------------------+--------------------------------------------------+
| **componentTranslationsD | Sets component translations descriptor template. |
| escriptorTemplate**      |                                                  |
|                          |                                                  |
| `​<​​>​`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **grantedRoles**         | Assigns the roles that are authorized to         |
|                          | manipulate components backed by this descriptor. |
| `Collection​<​String​>​` | It supports "**!**" prefix to negate the         |
|                          | role(s). This will directly influence the UI     |
|                          | behaviour and even composition. Setting the      |
|                          | collection of granted roles to {@code null}      |
|                          | (default value) disables role based              |
|                          | authorization on this component level. Note that |
|                          | this authorization enforcement does not prevent  |
|                          | programmatic access that is of the developer     |
|                          | responsibility.                                  |
+--------------------------+--------------------------------------------------+
| **lifecycleInterceptorBe | Registers a list of lifecycle interceptor        |
| anNames**                | instances that will be triggered on the          |
|                          | different phases of the component lifecycle,     |
| `List​<​String​>​`       | i.e. :                                           |
|                          |                                                  |
|                          | -   when the component is *instantiated* in      |
|                          |     memory                                       |
|                          |                                                  |
|                          | -   when the component is *created* in the data  |
|                          |     store                                        |
|                          |                                                  |
|                          | -   when the component is *updated* in the data  |
|                          |     store                                        |
|                          |                                                  |
|                          | -   when the component is *loaded* from the data |
|                          |     store                                        |
|                          |                                                  |
|                          | -   when the component is *deleted* from the     |
|                          |     data store                                   |
|                          |                                                  |
|                          | This property must be set with Spring bean names |
|                          | (i.e. Spring ids). When needed, Jspresso will    |
|                          | query the Spring application context to retrieve |
|                          | the interceptors instances. This property is     |
|                          | equivalent to setting {@code                     |
|                          | lifecycleInterceptorClassNames} except that it   |
|                          | allows to register interceptor instances that    |
|                          | are configured externally in the Spring context. |
|                          | lifecycle interceptor instances must implement   |
|                          | the {@code ILifecycleInterceptor\<E\>} interface |
|                          | where \<E\> is a type assignable from the        |
|                          | component type.                                  |
+--------------------------+--------------------------------------------------+
| **lifecycleInterceptorCl | Much the same as {@code                          |
| assNames**               | lifecycleInterceptorBeanNames} except that       |
|                          | instead of providing a list of Spring bean       |
| `List​<​String​>​`       | names, you provide a list of fully qualified     |
|                          | class names. These classes must :                |
|                          |                                                  |
|                          | -   provide a default constructor                |
|                          |                                                  |
|                          | -   implement the {@code IPropertyProcessor\<E,  |
|                          |     F\>} interface.                              |
|                          |                                                  |
|                          | When needed, Jspresso will create the property   |
|                          | processor instances.                             |
+--------------------------+--------------------------------------------------+
| **orderingProperties**   | Ordering properties are used to sort un-indexed  |
|                          | collections of instances of components backed by |
| `Map​<​String​,?​>​`     | this descriptor. This sort order can be          |
|                          | overridden on the finer collection property      |
|                          | level to change the way a specific collection is |
|                          | sorted. This property consist of a {@code Map}   |
|                          | whose entries are composed with :                |
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
|                          | the collection sort order.                       |
+--------------------------+--------------------------------------------------+
| **pageSize**             | Whenever a collection of this component type is  |
|                          | presented in a pageable UI, this property gives  |
| `Integer`                | the size (number of component instances) of one  |
|                          | page. This size can usually be refined at a      |
|                          | lower level (e.g. at reference property          |
|                          | descriptor for "lists of values"). A {@code      |
|                          | null} value (default) disables paging for this   |
|                          | component.                                       |
+--------------------------+--------------------------------------------------+
| **permId**               | A component permanent id is forced to be its     |
|                          | fully-qualified class name. Trying to set it to  |
| `String`                 | another value will raise an exception.           |
|                          | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **propertyDescriptors**  | This property allows to describe the properties  |
|                          | of the components backed by this descriptor.     |
| `Collection​<​​>​`       | Like in classic OO programming, the actual set   |
|                          | of properties available to a component is the    |
|                          | union of its properties and of its ancestors'    |
|                          | ones. Jspresso also allows you to refine a       |
|                          | property descriptor in a child component         |
|                          | descriptor exactly as you would do it in a       |
|                          | subclass. In that case, the attributes of the    |
|                          | property defined in the child descriptor         |
|                          | prevails over the definition of its ancestors.   |
|                          | Naturally, properties are keyed by their names.  |
+--------------------------+--------------------------------------------------+
| **queryableProperties**  | This property allows to define which of the      |
|                          | component properties are to be used in the       |
| `List​<​String​>​`       | filter UIs that are based on this component      |
|                          | family (a QBE screen for instance). Since this   |
|                          | is a {@code List} queryable properties are       |
|                          | rendered in the same order. Whenever this this   |
|                          | property is {@code null} (default value),        |
|                          | Jspresso chooses the default set of queryable    |
|                          | properties based on their type. For instance,    |
|                          | collection properties and binary properties are  |
|                          | not used but string, numeric, reference, ...     |
|                          | properties are. A computed property cannot be    |
|                          | used since it has no data store existence and    |
|                          | thus cannot be queried upon. Note that this      |
|                          | property is not inherited by children            |
|                          | descriptors, i.e. even if an ancestor defines an |
|                          | explicit set of queryable properties, its        |
|                          | children ignore this setting.                    |
+--------------------------+--------------------------------------------------+
| **renderedProperties**   | This property allows to define which of the      |
|                          | component properties are to be rendered by       |
| `List​<​String​>​`       | default when displaying a UI based on this       |
|                          | component family. For instance, a table will     |
|                          | render 1 column per rendered property of the     |
|                          | component. Any type of property can be used      |
|                          | except collection properties. Since this is a    |
|                          | {@code List} queryable properties are rendered   |
|                          | in the same order. Whenever this property is     |
|                          | {@code null} (default value) Jspresso determines |
|                          | the default set of properties to render based on |
|                          | their types, e.g. ignores collection properties. |
|                          | Note that this property is not inherited by      |
|                          | children descriptors, i.e. even if an ancestor   |
|                          | defines an explicit set of rendered properties,  |
|                          | its children ignore this setting.                |
+--------------------------+--------------------------------------------------+
| **serviceDelegateBeanNam | Registers the collection of service delegate     |
| es**                     | instances attached to this component. These      |
|                          | delegate instances will automatically be         |
| `Map​<​String​,String​>​ | triggered whenever a method of the service       |
| `                        | interface it implements get executed. For        |
|                          | instance :                                       |
|                          |                                                  |
|                          | -   the component interface is {@code            |
|                          |     MyBeanClass}. It implements the service      |
|                          |     interface {@code MyService}.                 |
|                          |                                                  |
|                          | -   the service interface {@code MyService}      |
|                          |     contains method {@code int foo(String)}.     |
|                          |                                                  |
|                          | -   the service delegate class, e.g. {@code      |
|                          |     MyServiceImpl} must implement the method     |
|                          |     {@code int foo(MyBeanClass,String)}. Note    |
|                          |     that the parameter list is augmented with    |
|                          |     the owing component type as 1st parameter.   |
|                          |     This allows to have stateless implementation |
|                          |     for delegates, thus sharing instances of     |
|                          |     delegates among instances of components.     |
|                          |                                                  |
|                          | -   when {@code foo(String)} is executed on an   |
|                          |     instance of {@code MyBeanClass}, the         |
|                          |     framework will trigger the delegate          |
|                          |     implementation, passing the instance of the  |
|                          |     component itself as parameter.               |
|                          |                                                  |
|                          | This property must be set with a map keyed by    |
|                          | service interfaces and valued by Spring bean     |
|                          | names (i.e. Spring ids). Each bean name          |
|                          | corresponds to an instance of service delegate.  |
|                          | When needed, Jspresso will query the Spring      |
|                          | application context to retrieve the delegate     |
|                          | instances. This property is equivalent to        |
|                          | setting {@code serviceDelegateClassNames} except |
|                          | that it allows to register delegate instances    |
|                          | that are configured externally in the Spring     |
|                          | context. lifecycle interceptor instances must    |
|                          | implement the {@code IComponentService} marker   |
|                          | interface.                                       |
+--------------------------+--------------------------------------------------+
| **serviceDelegateClassNa | Much the same as {@code                          |
| mes**                    | serviceDelegateBeanNames} except that instead of |
|                          | providing a map valued with Spring bean names,   |
| `Map​<​String​,String​>​ | you provide a map valued with fully qualified    |
| `                        | class names. These class must :                  |
|                          |                                                  |
|                          | -   provide a default constructor                |
|                          |                                                  |
|                          | -   implement the {@code IComponentService}      |
|                          |     marker interface.                            |
|                          |                                                  |
|                          | When needed, Jspresso will create service        |
|                          | delegate instances.                              |
+--------------------------+--------------------------------------------------+
| **sqlName**              | Instructs Jspresso to use this name when         |
|                          | translating this component type name to the data |
| `String`                 | store namespace. This includes , but is not      |
|                          | limited to, database table names. Default value  |
|                          | is {@code null} so that Jspresso uses its        |
|                          | default naming policy.                           |
+--------------------------+--------------------------------------------------+
| **toHtmlProperty**       | Allows to customize the HTML representation of a |
|                          | component instance. The property name assigned   |
| `String`                 | will be used when displaying the component       |
|                          | instance as HTML. It may be a computed property  |
|                          | that composes several other properties in a      |
|                          | human friendly format. Whenever this property is |
|                          | {@code null}, the {@code toStringProperty} is    |
|                          | used. Note that this property is not inherited   |
|                          | by children descriptors, i.e. even if an         |
|                          | ancestor defines an explicit *toHtmlProperty*    |
|                          | property, its children ignore this setting.      |
+--------------------------+--------------------------------------------------+
| **toStringProperty**     | Allows to customize the string representation of |
|                          | a component instance. The property name assigned |
| `String`                 | will be used when displaying the component       |
|                          | instance as a string. It may be a computed       |
|                          | property that composes several other properties  |
|                          | in a human friendly format. Whenever this        |
|                          | property is {@code null}, the following rule     |
|                          | apply to determine the *toString* property :     |
|                          |                                                  |
|                          | 1.  the first string property from the rendered  |
|                          |     property                                     |
|                          |                                                  |
|                          | 2.  the first rendered property if no string     |
|                          |     property is found among them                 |
|                          |                                                  |
|                          | Note that this property is not inherited by      |
|                          | children descriptors, i.e. even if an ancestor   |
|                          | defines an explicit *toString* property, its     |
|                          | children ignore this setting.                    |
+--------------------------+--------------------------------------------------+
| **unclonedProperties**   | Configures the properties that must not be       |
|                          | cloned when this component is duplicated. For    |
| `Collection​<​String​>​` | instance, tracing information like a created     |
|                          | timestamp should not be cloned; a SSN neither.   |
|                          | For a given component, the uncloned properties   |
|                          | are the ones it defines augmented by the ones    |
|                          | its ancestors define. There is no mean to make a |
|                          | component property cloneable if one of the       |
|                          | ancestor declares it un-cloneable.               |
+--------------------------+--------------------------------------------------+
| **writabilityGates**     | Assigns a collection of gates to determine       |
|                          | component *writability*. A component will be     |
| `Collection​<​​>​`       | considered writable if and only if all gates are |
|                          | open. This mechanism is mainly used for dynamic  |
|                          | UI authorization based on model state, e.g. a    |
|                          | validated invoice should not be editable         |
|                          | anymore. Descriptor assigned gates will be       |
|                          | cloned for each component instance created and   |
|                          | backed by this descriptor. So basically, each    |
|                          | component instance will have its own, unshared   |
|                          | collection of writability gates. Jspresso        |
|                          | provides a useful set of gate types, like the    |
|                          | binary property gate that open/close based on    |
|                          | the value of a boolean property of owning        |
|                          | component. By default, component descriptors are |
|                          | not assigned any gates collection, i.e. there is |
|                          | no writability restriction. Note that gates do   |
|                          | not enforce programmatic writability of a        |
|                          | component; only UI is impacted.                  |
+--------------------------+--------------------------------------------------+

: AbstractComponentDescriptor properties

BasicComponentDescriptor
------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** :

This type of descriptor is used to describe :

-   structures that are to be reused but don't have enough focus for
    being considered as entities. For instance {@code MoneyAmount}
    component could be composed of a decimal and a reference to a {@code
    Money} entity. This structure could then be reused in other elements
    of the domain like an {@code Invoice} or an {@code Article}.
    Jspresso terminology for these type of structures is *"Inline
    Component"*.

-   arbitrary models, that even come from outside of Jspresso (an
    external library for instance). Describing an arbitrary component
    allows for seamless usage in the Jspresso view binding architecture.
    Note that in that case, all behavioural properties like lifecycle
    interceptors or service delegates are ignored since none of the
    model behaviour is handled by Jspresso.

Both types of components described above must conform to the *Java
Beans* standard so that its property changes can be followed by the
classic {@code add/removePropertyChangeListener} methods since Jspresso
binding architecture leverages this behaviour. Jspresso managed
components implement it automatically but the developer must ensure it
for other types of components.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **ancestorDescriptors**  | {@inheritDoc}                                    |
|                          |                                                  |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+

: BasicComponentDescriptor properties

BasicEntityDescriptor
---------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor key to the description of the application model. It is
used to describe a model entity. A Jspresso managed entity has a
synthetic identifier (*id*) and is versioned (*version*) to cope with
concurrent access conflicts through optimistic locking. It conforms to
the *Java Beans* standard so that its property changes can be followed
by the classic {@code add/removePropertyChangeListener} methods;
Jspresso binding architecture leverages this behaviour.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **ancestorDescriptors**  | {@inheritDoc}                                    |
|                          |                                                  |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+
| **purelyAbstract**       | This property is used to indicate that the       |
|                          | entity type described is to be considered        |
| `boolean`                | **abstract**. Jspresso will prevent any          |
|                          | instantiation through its generic actions or     |
|                          | internal mechanisms. Trying to do so will result |
|                          | in a low level exception and reveals a coding    |
|                          | (assembling) error.                              |
|                          |                                                  |
|                          | However, an abstract entity will have a concrete |
|                          | representation in the data store that depends on |
|                          | the inheritance mapping strategy used. As of     |
|                          | now, Jspresso uses the *join-subclass*           |
|                          | inheritance mapping strategy when generating the |
|                          | Hibernate mapping so an abstract entity will end |
|                          | up as a table in the data store.                 |
|                          |                                                  |
|                          | An abstract entity descriptor differs from an    |
|                          | interface descriptor mainly because of its       |
|                          | concrete representation in the data store as     |
|                          | formerly described.                              |
+--------------------------+--------------------------------------------------+
| **rootEntityDescriptor** | Configures the root entity descriptor to use     |
|                          | globally for the application. Jspresso will      |
| `​<​​>​`                 | ensure that all entity descriptors have this     |
|                          | root descriptor as ancestor.                     |
+--------------------------+--------------------------------------------------+

: BasicEntityDescriptor properties

BasicInterfaceDescriptor
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This descriptor is a mean of factorizing state/behaviour among
components, entities or even sub-interfaces. This is a much less
coupling mechanism than actual entity inheritance and can be used across
entities that don't belong the the same inheritance hierarchy, or even
across types (entities, components, interfaces).

Please note that interface descriptor is not a way for domain elements
to implement arbitrary interfaces coming from external libraries unless
they only contain property accessors. The latter can be achieved using
service delegates and the {@code serviceDelegates[Bean|Class]Names}
property.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BasicInterfaceDescriptor properties


