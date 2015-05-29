Reference for Module hierarchy
==============================

Module
------

-   **Full name** : ``

-   **Super-type** : `AbstractPropertyChangeCapable`

-   **Sub-types** : ``, ``

A module is an entry point in the application. Modules are organized in
bi-directional, parent-children hierarchy. As such, they can be viewed
(and they are materialized in the UI) as trees. Modules can be
(re)organized dynamically by changing their parent-children relationship
and their owning workspace UI will reflect the change seamlessly, as
with any Jspresso model (in fact workspaces and modules are regular
beans that are used as model in standard Jspresso views). Modules, among
other features, are capable of providing a view to be installed in the
UI wen they are selected. This makes Jspresso applications really
modular and their architecture flexible enough to embed and run a large
variety of different module types. A module can also be as simple as a
grouping structure for other modules (intermediary nodes).

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **description**          | Configures the key used to translate actual      |
|                          | internationalized module description. The        |
| `String`                 | resulting translation will generally be          |
|                          | leveraged as a toolTip on the UI side but its    |
|                          | use may be extended for online help.             |
+--------------------------+--------------------------------------------------+
| **entryAction**          | Configures an action to be executed every time   |
|                          | the module becomes the current selected module   |
| ``                       | (either through a user explicit navigation or a  |
|                          | programmatic selection). The action will execute |
|                          | in the context of the current workspace, this    |
|                          | module being the current selected module.        |
+--------------------------+--------------------------------------------------+
| **exitAction**           | Configures an action to be executed every time   |
|                          | the module becomes unselected (either through a  |
| ``                       | user explicit navigation or a programmatic       |
|                          | deselection). The action will execute in the     |
|                          | context of the current workspace, this module    |
|                          | being the current selected module (i.e. the      |
|                          | action occurs before the module is actually      |
|                          | left).                                           |
+--------------------------+--------------------------------------------------+
| **grantedRoles**         | Assigns the roles that are authorized to start   |
|                          | this module. It supports "**!**" prefix to       |
| `Collection​<​String​>​` | negate the role(s). Whenever the user is not     |
|                          | granted sufficient privileges, the module is     |
|                          | simply not installed in the workspace. Setting   |
|                          | the collection of granted roles to {@code null}  |
|                          | (default value) disables role based              |
|                          | authorization on this module. Some specific      |
|                          | modules that are component/entity model based    |
|                          | i.e. {@code Bean(Collection)Module} also inherit |
|                          | their authorizations from their model.           |
+--------------------------+--------------------------------------------------+
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
| **iconPreferredHeight**  | Sets the icon preferred width.                   |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **iconPreferredWidth**   | Sets the icon preferred width.                   |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **name**                 | Configures the key used to translate actual      |
|                          | internationalized module name. The resulting     |
| `String`                 | translation will be leveraged as the module      |
|                          | label on the UI side.                            |
+--------------------------+--------------------------------------------------+
| **permId**               | Sets the permanent identifier to this            |
|                          | application element. Permanent identifiers are   |
| `String`                 | used by different framework parts, like dynamic  |
|                          | security or record/replay controllers to         |
|                          | uniquely identify an application element.        |
|                          | Permanent identifiers are generated by the SJS   |
|                          | build based on the element id but must be        |
|                          | explicitly set if Spring XML is used.            |
+--------------------------+--------------------------------------------------+
| **projectedViewDescripto | Configures the view descriptor used to construct |
| r**                      | the view that will be displayed when this module |
|                          | is selected.                                     |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **startupAction**        | Configures an action to be executed the first    |
|                          | time the module is "started" by the user. The    |
| ``                       | action will execute in the context of the        |
|                          | current workspace, this module being the current |
|                          | selected module. It will help initializing       |
|                          | module values, notify user, ....                 |
+--------------------------+--------------------------------------------------+

: Module properties

BeanCollectionModule
--------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This type of module keeps a reference on a beans collection. There is no
assumption made on whether these beans are actually persistent entities
or any other type of java beans.

Simple bean collection modules must have their collection of referenced
beans initialized somehow. There is no standard built-in action to do
so, since it is highly dependent on what's needed. So it's rather common
to have the module content initialized through a startup action
depending on the session state.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **elementComponentDescri | Configures the type of bean element this         |
| ptor**                   | collection module manages. A bunch of default    |
|                          | values are inferred from this element component  |
| `​<​Object​>​`           | descriptor. For instance, paging size (if used)  |
|                          | will default to the component one unless         |
|                          | explicitly set. Same goes for icon image URL,    |
|                          | default ordering properties or even granted      |
|                          | roles. The latter means that bean collection     |
|                          | modules based on forbidden entities will         |
|                          | automatically be excluded from the workspace of  |
|                          | the logged-in user.                              |
|                          |                                                  |
|                          | if not explicitly configured, the element        |
|                          | component descriptor can be inferred from the    |
|                          | collection view descriptor configured as         |
|                          | projected view descriptor.                       |
+--------------------------+--------------------------------------------------+
| **elementViewDescriptor* | This property is not used by the module itself,  |
| *                        | but by built-in actions that maybe registered on |
|                          | this module. One of these actions is {@code      |
| ``                       | AddBeanAsSubModuleAction}.                       |
|                          |                                                  |
|                          | This property indicates the view to use whenever |
|                          | the user requests a "form-like" view on a        |
|                          | collection element. Naturally the configured     |
|                          | element view descriptor must be backed by a      |
|                          | model matching the type of the module managed    |
|                          | beans.                                           |
+--------------------------+--------------------------------------------------+
| **moduleObjects**        | Assigns the list of beans this module manages.   |
|                          | The projected view will automatically reflect    |
| `List​<​?​>​`            | this change since a "moduleObjects" property     |
|                          | change will be fired.                            |
+--------------------------+--------------------------------------------------+

: BeanCollectionModule properties

FilterableBeanCollectionModule
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This is a specialized type of bean collection module that provides a
filter ( an instance of {@code IQueryComponent} ). This type of module,
coupled with a generic, built-in, action map is perfectly suited for
CRUD-like operations.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **displayPageIndex**     | Delegates to filter.                             |
|                          |                                                  |
| `Integer`                | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **filter**               | Assigns the filter to this module instance. It   |
|                          | is by default assigned by the module startup     |
| ``                       | action (see {@code InitModuleFilterAction}). So  |
|                          | if you ever want to change the default           |
|                          | implementation of the filter, you have to write  |
|                          | and install you own custom startup action or     |
|                          | explicitly inject a specific instance.           |
+--------------------------+--------------------------------------------------+
| **filterComponentDescrip | This property allows to configure a custom       |
| tor**                    | filter model descriptor. If not set, which is    |
|                          | the default value, the filter model is built out |
| `​<​​>​`                 | of the element component descriptor (QBE filter  |
|                          | model).                                          |
+--------------------------+--------------------------------------------------+
| **filterViewDescriptor** | This property allows to refine the default filer |
|                          | view to re-arrange the filter fields. Custom     |
| ``                       | filter view descriptors assigned here must not   |
|                          | be assigned a model descriptor since they will   |
|                          | be at runtime. This is because the filter        |
|                          | component descriptor must be reworked - to adapt |
|                          | comparable field structures for instance.        |
+--------------------------+--------------------------------------------------+
| **orderingProperties**   | Configures a custom map of ordering properties   |
|                          | for the result set. If not set, which is the     |
| `Map​<​String​,​>​`      | default, the elements ordering properties is     |
|                          | used.                                            |
|                          |                                                  |
|                          | This property consist of a {@code Map} whose     |
|                          | entries are composed with :                      |
|                          |                                                  |
|                          | -   the property name as key                     |
|                          |                                                  |
|                          | -   the sort order for this property as value.   |
|                          |     This is either a value of the {@code ESort}  |
|                          |     enum (*ASCENDING* or *DESCENDING*) or its    |
|                          |     equivalent string representation.            |
|                          |                                                  |
|                          | Ordering properties are considered following     |
|                          | their order in the map iterator.                 |
+--------------------------+--------------------------------------------------+
| **page**                 | Delegates to filter.                             |
|                          |                                                  |
| `Integer`                | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **pageSize**             | Configures a custom page size for the result     |
|                          | set. If not set, which is the default, the       |
| `Integer`                | elements default page size is used.              |
+--------------------------+--------------------------------------------------+
| **paginationViewDescript | Configures the sub view used to navigate between |
| or**                     | the pages.                                       |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **pagingAction**         | Sets the pagingAction.                           |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **queryComponentDescript | Sets the queryComponentDescriptorFactory.        |
| orFactory**              |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **queryViewDescriptorFac | Sets the queryViewDescriptorFactory.             |
| tory**                   |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **recordCount**          | Delegates to filter.                             |
|                          |                                                  |
| `Integer`                | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **selectedRecordCount**  | Delegates to filter.                             |
|                          |                                                  |
| `Integer`                | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **stickyResults**        | Delegates to filter. {@inheritDoc}               |
|                          |                                                  |
| `List​<​?​>​`            |                                                  |
+--------------------------+--------------------------------------------------+

: FilterableBeanCollectionModule properties

MobileFilterableBeanCollectionModule
------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a specialized type of filterable bean collection module that
provides a filter ( an instance of {@code IQueryComponent} ). This type
of module, coupled with a generic, built-in, action map is perfectly
suited for CRUD-like operations.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **elementViewDescriptor* | Mobile filterable bean collection module views   |
| *                        | only support page views as element views         |
|                          | descriptors. {@inheritDoc}                       |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **filterViewDescriptor** | Mobile filterable bean collection module views   |
|                          | only support mobile component views as filter    |
| ``                       | views descriptors. {@inheritDoc}                 |
+--------------------------+--------------------------------------------------+
| **paginationViewDescript | Not supported in mobile environment.             |
| or**                     | {@inheritDoc}                                    |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **projectedViewDescripto | Mobile filter bean collection module views only  |
| r**                      | support list views as projected view             |
|                          | descriptors. {@inheritDoc}                       |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **queryModuleFilterActio | Sets query module filter action.                 |
| n**                      |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: MobileFilterableBeanCollectionModule properties

MobileBeanCollectionModule
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

This type of module keeps a reference on a beans collection. There is no
assumption made on whether these beans are actually persistent entities
or any other type of java beans. Simple bean collection modules must
have their collection of referenced beans initialized somehow. There is
no standard built-in action to do so, since it is highly dependent on
what's needed. So it's rather common to have the module content
initialized through a startup action depending on the session state.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **elementViewDescriptor* | Mobile bean collection module views only support |
| *                        | page views as element views descriptors.         |
|                          | {@inheritDoc}                                    |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **projectedViewDescripto | Mobile bean collection module views only support |
| r**                      | list views as projected view descriptors.        |
|                          | {@inheritDoc}                                    |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: MobileBeanCollectionModule properties

BeanModule
----------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This type of module keeps a reference on a single bean. There is no
assumption made on whether this bean is actually a persistent entity or
any other type of java bean.

Bean modules must have their referenced bean initialized somehow. So
it's rather common to have the module content initialized through a
startup action depending on the session state or dynamically constructed
by a standard action like {@code AddBeanAsSubModuleAction}.

This type of module is definitely the one that offers maximum
flexibility to handle arbitrary models.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **componentDescriptor**  | Configures the type of bean this module manages. |
|                          | A bunch of default values are inferred from this |
| `​<​Object​>​`           | component descriptor. For instance, icon image   |
|                          | URL or even granted roles can be inferred from   |
|                          | the configured component descriptor. The latter  |
|                          | means that bean modules based on forbidden       |
|                          | entities will automatically be excluded from the |
|                          | workspace of the logged-in user.                 |
|                          |                                                  |
|                          | However, when not set, the component descriptor  |
|                          | it self can be inferred from the configured      |
|                          | projected view descriptor model.                 |
+--------------------------+--------------------------------------------------+
| **moduleObject**         | Assigns the bean this module manages. The        |
|                          | projected view will automatically reflect this   |
| `Object`                 | change since a "moduleObject" property change    |
|                          | will be fired.                                   |
+--------------------------+--------------------------------------------------+

: BeanModule properties

MobileBeanModule
----------------

-   **Full name** : ``

-   **Super-type** : ``

This type of module keeps a reference on a single bean. There is no
assumption made on whether this bean is actually a persistent entity or
any other type of java bean. Bean modules must have their referenced
bean initialized somehow. So it's rather common to have the module
content initialized through a startup action depending on the session
state or dynamically constructed by a standard action like {@code
AddBeanAsSubModuleAction}. This type of module is definitely the one
that offers maximum flexibility to handle arbitrary models.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **projectedViewDescripto | Mobile bean module only support page views as    |
| r**                      | projected views descriptors. {@inheritDoc}       |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: MobileBeanModule properties


