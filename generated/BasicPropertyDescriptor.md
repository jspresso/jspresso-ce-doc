Reference for BasicPropertyDescriptor hierarchy
===============================================

BasicPropertyDescriptor
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This is the abstract base class for all property descriptors. It mainly
serves for factorizing all commons properties for property descriptors.
A property descriptor is used for describing a
component/entity/interface property (*Java Beans* semantic). You will
never use {@code BasicPropertyDescriptor} as such but rather use its
concrete descendants. Please note that {@code BasicPropertyDescriptor}
enforces its name to start with a lower case letter, following the
JavaBean convention. So even if you name it "MyProperty", it will
actually end up to "myProperty".

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cacheable**            | Configures the fact that this property can be    |
|                          | cached. This is only used for computed           |
| `boolean`                | properties. Note that the cached value will be   |
|                          | reset whenever a firePropertyChange regarding    |
|                          | this property is detected to be fired. Default   |
|                          | value is {@code false} in order to prevent       |
|                          | un-desired side-effects if computed property     |
|                          | change notification is not correctly wired.      |
+--------------------------+--------------------------------------------------+
| **computed**             | Forces a property to be considered as a computed |
|                          | property by the framework. A computed property   |
| `boolean`                | will be completely ignored by the persistence    |
|                          | layer and its management is left to the          |
|                          | developer. Properties declared with a delegate   |
|                          | computing class are considered computed by       |
|                          | default so there is no need to explicitly set    |
|                          | them {@code computed=true}. However, there is    |
|                          | sometimes a need to declare a property at some   |
|                          | level (e.g. in an interface descriptor) and let  |
|                          | lower level implementation decide how to handle  |
|                          | this common property concretely (either          |
|                          | computing it or handling it as a real persistent |
|                          | property). In that case, you can declare this    |
|                          | property {@code computed=true} in the super type |
|                          | and refine the actual implementation (computed   |
|                          | or not) in the sub-types. Default value is       |
|                          | {@code false}.                                   |
+--------------------------+--------------------------------------------------+
| **delegateClassName**    | Instructs the framework that this property is    |
|                          | computed by a delegate attached to the owning    |
| `String`                 | component. The {@code delegateClassName}         |
|                          | property must be set with the fully qualified    |
|                          | class name of the delegate instance to use.      |
|                          | Delegate instances are stateful. This allows for |
|                          | some caching of computing intensive properties.  |
|                          | There is exactly one delegate of a certain class |
|                          | per owning component instance. Delegate          |
|                          | instances are lazily created when needed, i.e.   |
|                          | whe the computed property is accessed either     |
|                          | programmatically or by the binding layer. The    |
|                          | delegate class must implement the {@code         |
|                          | IComponentExtension\<T\>} interface (where \<T\> |
|                          | is assignable from the owning component class)   |
|                          | and provide a public constructor taking exactly  |
|                          | 1 parameter : the component instance. Jspresso   |
|                          | provides an adapter class to inherit from :      |
|                          | {@code AbstractComponentExtension\<T\>}. This    |
|                          | helper class provides the methods to access the  |
|                          | enclosing component from the delegate            |
|                          | implementation as well as the Spring context it  |
|                          | comes from, when needed. A delegate-computed     |
|                          | property is most of the time read-only but it    |
|                          | can be made writable by setting the property     |
|                          | descriptor {@code delegateWritable=true}. In     |
|                          | that case the delegate class must also provide a |
|                          | setter for the computed property.                |
+--------------------------+--------------------------------------------------+
| **delegateWritable**     | Instructs the framework that a delegate-computed |
|                          | property is writable. Most of the time, a        |
| `boolean`                | computed property is read-only. Whenever a       |
|                          | computed property is made writable through the   |
|                          | use of {@code delegateWritable=true}, the        |
|                          | delegate class must also provide a setter for    |
|                          | the computed property. Default value is {@code   |
|                          | false}.                                          |
+--------------------------+--------------------------------------------------+
| **filterComparable**     | Sets filter comparable.                          |
|                          |                                                  |
| `Boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **grantedRoles**         | Assigns the roles that are authorized to         |
|                          | manipulate the property backed by this           |
| `Collection​<​String​>​` | descriptor. It supports "**!**" prefix to negate |
|                          | the role(s). This will directly influence the UI |
|                          | behaviour and even composition (e.g. show/hide   |
|                          | columns or fields). Setting the collection of    |
|                          | granted roles to {@code null} (default value)    |
|                          | disables role based authorization on this        |
|                          | property level. Note that this authorization     |
|                          | enforcement does not prevent programmatic access |
|                          | that is of the developer responsibility.         |
+--------------------------+--------------------------------------------------+
| **integrityProcessorBean | Registers a list of property processor instances |
| Names**                  | that will be triggered on the different phases   |
|                          | of the property modification, i.e. :             |
| `List​<​String​>​`       |                                                  |
|                          | -   *before* the property is modified, usually   |
|                          |     for controlling the incoming value           |
|                          |                                                  |
|                          | -   *while* (actually just before the actual     |
|                          |     assignment) the property is modified,        |
|                          |     allowing to intercept and change the         |
|                          |     incoming value                               |
|                          |                                                  |
|                          | -   *after* the property is modified, allowing   |
|                          |     to trigger some post-modification behaviour  |
|                          |     (e.g. tracing, domain integrity management,  |
|                          |     ...)                                         |
|                          |                                                  |
|                          | This property must be set with Spring bean names |
|                          | (i.e. Spring ids). When needed, Jspresso will    |
|                          | query the Spring application context to retrieve |
|                          | the processor instances. This property is        |
|                          | equivalent to setting {@code                     |
|                          | integrityProcessorClassNames} except that it     |
|                          | allows to register processor instances that are  |
|                          | configured externally in the Spring context.     |
|                          | Property processor instances must implement the  |
|                          | {@code IPropertyProcessor\<E, F\>} interface     |
|                          | where \<E, F\> represent respectively the type   |
|                          | of the owning component and the type of the      |
|                          | property. Since there are 3 methods to implement |
|                          | in the interface (1 for each of the phase        |
|                          | described above), Jspresso provides an adapter   |
|                          | class with empty implementations to override :   |
|                          | {@code EmptyPropertyProcessor\<E, F\>}. Whenever |
|                          | the underlying property is a collection          |
|                          | property, the interface to implement is {@code   |
|                          | ICollectionPropertyProcessor\<E, F\>} (or extend |
|                          | {@code EmptyCollectionPropertyProcessor\<E,      |
|                          | F\>}) with 4 new phases introduced :             |
|                          |                                                  |
|                          | -   *before* an element is *added* to the        |
|                          |     collection property                          |
|                          |                                                  |
|                          | -   *after* an element is *added* to the         |
|                          |     collection property                          |
|                          |                                                  |
|                          | -   *before* an element is *removed* from the    |
|                          |     collection property                          |
|                          |                                                  |
|                          | -   *after* an element is *removed* from the     |
|                          |     collection property                          |
+--------------------------+--------------------------------------------------+
| **integrityProcessorClas | Much the same as {@code                          |
| sNames**                 | integrityProcessorBeanNames} except that instead |
|                          | of providing a list of Spring bean names, you    |
| `List​<​String​>​`       | provide a list of fully qualified class names.   |
|                          | These classes must :                             |
|                          |                                                  |
|                          | -   provide a default constructor                |
|                          |                                                  |
|                          | -   implement the {@code                         |
|                          |     ILifecycleInterceptor\<E\>} interface.       |
|                          |                                                  |
|                          | When needed, Jspresso will create lifecycle      |
|                          | interceptor instances.                           |
+--------------------------+--------------------------------------------------+
| **mandatory**            | Declare a property as mandatory. This will       |
|                          | enforce mandatory checks when the owning         |
| `boolean`                | component is persisted as well as when the       |
|                          | property is updated individually. Moreover, this |
|                          | information allows the views bound to the        |
|                          | property to be configured accordingly, e.g.      |
|                          | display the property with a slightly modified    |
|                          | label indicating it is mandatory. This           |
|                          | constraint is also enforced programmatically.    |
|                          | Default value is false.                          |
+--------------------------+--------------------------------------------------+
| **name**                 | Enforces its name to start with a lower case     |
|                          | letter, following the JavaBean convention. So    |
| `String`                 | even if you name it "MyProperty", it will        |
|                          | actually end up to "myProperty". {@inheritDoc}   |
+--------------------------+--------------------------------------------------+
| **permId**               | A property permanent id is forced to be its      |
|                          | name. Trying to set it to another value will     |
| `String`                 | raise an exception. {@inheritDoc}                |
+--------------------------+--------------------------------------------------+
| **preferredWidth**       | This property allows for setting an indication   |
|                          | of width for representing this property in a     |
| `Integer`                | view. Default value is {@code null}, so that the |
|                          | view factory will make its decision based on the |
|                          | type and/or other characteristics of the         |
|                          | property (e.g. max length).                      |
+--------------------------+--------------------------------------------------+
| **readOnly**             | Enforces a property to be read-only. This is     |
|                          | only enforced at the UI level, i.e. the property |
| `boolean`                | can still be updated programmatically. The UI    |
|                          | may take decisions like changing text fields     |
|                          | into labels if it knows the underlying property  |
|                          | is read-only.                                    |
+--------------------------+--------------------------------------------------+
| **sortable**             | Enforces a property sortability. This is only    |
|                          | enforced at the UI level, i.e. the property can  |
| `boolean`                | still be used for sorting programmatically.      |
+--------------------------+--------------------------------------------------+
| **sqlName**              | Instructs Jspresso to use this name when         |
|                          | translating this property name to the data store |
| `String`                 | namespace. This includes , but is not limited    |
|                          | to, database column names. Default value is      |
|                          | {@code null} so that Jspresso uses its default   |
|                          | naming policy.                                   |
+--------------------------+--------------------------------------------------+
| **unicityScope**         | Makes this property part of a unicity scope. All |
|                          | tuples of properties belonging to the same       |
| `String`                 | unicity scope are enforced to be unique in the   |
|                          | component type scope. This concretely translates |
|                          | to unique constraints in the data store spanning |
|                          | the properties composing the unicity scope. Note |
|                          | that, for performance reasons, unicity scopes    |
|                          | are only enforced by the persistence layer.      |
+--------------------------+--------------------------------------------------+
| **versionControl**       | This property allows to fine tune whether this   |
|                          | component property participates in optimistic    |
| `boolean`                | versioning. It mainly allows to declare some     |
|                          | properties that should be ignored regarding      |
|                          | optimistic versioning thus lowering the risk of  |
|                          | version conflicts between concurrent users. Of   |
|                          | course, this feature has to be used with care    |
|                          | since it may generate phantom updates to the     |
|                          | data store. Default value is {@code true} so     |
|                          | that any change in the described property        |
|                          | increases the owning component version.          |
+--------------------------+--------------------------------------------------+
| **writabilityGates**     | Assigns a collection of gates to determine       |
|                          | property *writability*. A property will be       |
| `Collection​<​​>​`       | considered writable if and only if all gates are |
|                          | open. This mechanism is mainly used for dynamic  |
|                          | UI authorization based on model state, e.g. a    |
|                          | validated invoice should not be editable         |
|                          | anymore. Descriptor assigned gates will be       |
|                          | cloned for each property instance created and    |
|                          | backed by this descriptor. So basically, each    |
|                          | property instance will have its own, unshared    |
|                          | collection of writability gates. Jspresso        |
|                          | provides a useful set of gate types, like the    |
|                          | binary property gate that open/close based on    |
|                          | the value of a boolean property of owning        |
|                          | component. By default, property descriptors are  |
|                          | not assigned any gates collection, i.e. there is |
|                          | no writability restriction. Note that gates do   |
|                          | not enforce programmatic writability of a        |
|                          | property; only UI is impacted.                   |
+--------------------------+--------------------------------------------------+

: BasicPropertyDescriptor properties

