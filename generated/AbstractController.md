Reference for AbstractController hierarchy
==========================================

AbstractController
------------------

-   **Full name** : ``

-   **Super-type** : `AbstractPropertyChangeCapable`

-   **Sub-types** : ``, ``

Abstract base class for controllers. Controllers role is to adapt the application to its environment. Jspresso relies on two different types of controllers :

-   The frontend controller is responsible for managing UI interactions. Naturally, the type of frontend controller used depends on the UI channel.

-   The backend controller is responsible for managing the application session as well as transactions and persistence operations.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **customExceptionHandler | Configures a custom exception handler on the     |
| **                       | controller. The controller itself is an          |
|                          | exception handler and is used as such across     |
| ``                       | most of the application layers. Jspresso         |
|                          | philosophy is to use unchecked exceptions in     |
|                          | services, business rules, and so on, so that,    |
|                          | whenever an exception occurs, it climbs the call |
|                          | stack up to an exception handler (usually one of |
|                          | the controller). Whenever a custom exception     |
|                          | handler is configured, the exception handling is |
|                          | delegated to it, allowing the exceptions to be   |
|                          | refined or handled differently than for the      |
|                          | built-in case. The exception handler can either  |
|                          | :                                                |
|                          |                                                  |
|                          | -   return {@code true} if the exception was     |
|                          |     completely processed and does not need any   |
|                          |     further action.                              |
|                          |                                                  |
|                          | -   return {@code false} if the exception was    |
|                          |     either not or un-completely processed and    |
|                          |     needs to continue the built-in handling.     |
+--------------------------+--------------------------------------------------+

: AbstractController properties

AbstractBackendController
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

Base class for backend application controllers. Backend controllers are responsible for :

-   keeping a reference to the application session

-   keeping a reference to the application workspaces and their state

-   keeping a reference to the application clipboard

-   keeping a reference to the entity registry that guarantees the in-memory entity reference unicity in the user session

-   keeping a reference to the entity dirt recorder that keeps track of entity changes to afterwards optimize the ORM operations

-   keeping a reference to the Spring transaction template and its peer "Unit of Work" -aka UOW- that is responsible to manage application transactions and adapt the underlying transaction system (Hibernate, JTA, ...)

Moreover, the backend controller will provide several model related factories that can be configured to customize default, built-in behaviour. Most of these configured properties will be accessible using the corresponding getters. Those getters should be used by the service layer.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **applicationSession**   | Assigns the application session to this backend  |
|                          | controller. This property can only be set once   |
| ``                       | and should only be used by the DI container. It  |
|                          | will rarely be changed from built-in defaults    |
|                          | unless you need to specify a custom              |
|                          | implementation instance to be used.              |
+--------------------------+--------------------------------------------------+
| **asyncActionsThreadGrou | Sets async actions thread group.                 |
| p**                      |                                                  |
|                          |                                                  |
| `Thread​Group`           |                                                  |
+--------------------------+--------------------------------------------------+
| **asyncExecutorsMaxCount | Configures the maximum count of concurrent       |
| **                       | asynchronous action executors. It defaults to    |
|                          | {@code 10}.                                      |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **carbonEntityCloneFacto | Configures the entity clone factory used to      |
| ry**                     | carbon-copy entities. An entity carbon-copy is   |
|                          | an technical copy of an entity, including id and |
| ``                       | version but excluding relationship properties.   |
|                          | This mechanism is used by the controller when    |
|                          | duplicating entities into the UOW to allow for   |
|                          | memory state aware transactions. This property   |
|                          | should only be used by the DI container. It will |
|                          | rarely be changed from built-in defaults unless  |
|                          | you need to specify a custom implementation      |
|                          | instance to be used.                             |
+--------------------------+--------------------------------------------------+
| **clientTimeZone**       | Sets client time zone.                           |
|                          |                                                  |
| `Time​Zone`              |                                                  |
+--------------------------+--------------------------------------------------+
| **collectionFactory**    | Configures the factory responsible for creating  |
|                          | entities (or components) collections that are    |
| ``                       | held by domain relationship properties. This     |
|                          | property should only be used by the DI           |
|                          | container. It will rarely be changed from        |
|                          | built-in defaults unless you need to specify a   |
|                          | custom implementation instance to be used.       |
+--------------------------+--------------------------------------------------+
| **customSecurityPlugin** | Configures a custom security plugin on the       |
|                          | controller. The controller itself is a security  |
| ``                       | handler and is used as such across most of the   |
|                          | application layers. Before delegating to the     |
|                          | custom security handler, the controller will     |
|                          | apply role-based security rules that cannot be   |
|                          | disabled.                                        |
+--------------------------+--------------------------------------------------+
| **customTranslationPlugi | Configures a custom translation plugin on the    |
| n**                      | controller. The controller itself is a           |
|                          | translation provider and is used as such across  |
| ``                       | most of the application layers. The custom       |
|                          | translation plugin is used to override the       |
|                          | default static, bundle-based, i18n scheme.       |
+--------------------------+--------------------------------------------------+
| **dirtyTrackingEnabled** | {@inheritDoc}                                    |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **entityFactory**        | Configures the entity factory to use to create   |
|                          | new entities. Backend controllers only accept    |
| ``                       | instances of {@code                              |
|                          | ControllerAwareProxyEntityFactory} or a          |
|                          | subclass. This is because the backend controller |
|                          | must keep track of created entities. Jspresso    |
|                          | entity implementations also use the controller   |
|                          | from which they were created behind the scene.   |
+--------------------------+--------------------------------------------------+
| **modelConnectorFactory* | Configures the model connector factory to use to |
| *                        | create new model connectors. Connectors are      |
|                          | adapters used by the binding layer to access     |
| ``                       | domain model values.                             |
+--------------------------+--------------------------------------------------+
| **referenceTimeZoneId**  | Sets reference time zone id.                     |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **slaveControllerFactory | Sets the slaveControllerFactory.                 |
| **                       |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **throwExceptionOnBadUsa | Configures the backend controller to throw or    |
| ge**                     | not an exception whenever a bad usage is         |
|                          | detected like manually merging a dirty entity    |
| `boolean`                | from an ongoing UOW.                             |
+--------------------------+--------------------------------------------------+
| **transactionTemplate**  | Assigns the Spring transaction template to this  |
|                          | backend controller. This property can only be    |
| `Transaction​Template`   | set once and should only be used by the DI       |
|                          | container. It will rarely be changed from        |
|                          | built-in defaults unless you need to specify a   |
|                          | custom implementation instance to be used. The   |
|                          | configured instance is the one that will be      |
|                          | returned by the controller's {@code              |
|                          | getTransactionTemplate()} method that should be  |
|                          | used by the service layer for transaction        |
|                          | management.                                      |
+--------------------------+--------------------------------------------------+
| **translationProvider**  | Configures the translation provider used to      |
|                          | compute internationalized messages and labels.   |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **userPreferencesStore** | Sets the user preference store.                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractBackendController properties

HibernateBackendController
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is the default Jspresso implementation of Hibernate-based backend controller.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **defaultTxFlushMode**   | Sets the default Hibernate flush mode to apply   |
|                          | to the Hibernate session when it is bound to a   |
| `String`                 | transaction. Defaults to {@link                  |
|                          | FlushMode\#COMMIT}.                              |
+--------------------------+--------------------------------------------------+
| **entityFactory**        | Configures the entity factory to use to create   |
|                          | new entities. Backend controllers only accept    |
| ``                       | instances of {@code                              |
|                          | HibernateControllerAwareProxyEntityFactory} or a |
|                          | subclass.                                        |
+--------------------------+--------------------------------------------------+
| **hibernateSessionFactor | Sets the hibernateSessionFactory.                |
| y**                      |                                                  |
|                          |                                                  |
| `Session​Factory`        |                                                  |
+--------------------------+--------------------------------------------------+
| **noTxDataSource**       | Sets the noTxDataSource.                         |
|                          |                                                  |
| `Data​Source`            |                                                  |
+--------------------------+--------------------------------------------------+

: HibernateBackendController properties

AbstractFrontendController
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Base class for frontend application controllers. Frontend controllers are responsible for adapting the Jspresso application to the UI channel. Although this generic abstract class centralizes most of the controller's configuration, it will be subclassed by concrete, UI dependent subclasses to implement polymorphic behaviour.

More than a behavioural adapter, the frontend controller will also be the place where you define the top-level application structure like the workspace list, the name, the application-wide actions, ...

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **actionMap**            | Configures an application-wide action map that   |
|                          | will be installed in the main application frame. |
| ``                       | These actions are available at any time from the |
|                          | UI and thus, do not depend on the active         |
|                          | workspace. General purpose actions like "Change  |
|                          | password" action should be installed here.       |
+--------------------------+--------------------------------------------------+
| **checkActionThreadSafet | Sets the checkActionThreadSafety.                |
| y**                      |                                                  |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **clientPreferencesStore | Sets the clientPreferenceStore.                  |
| **                       |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **description**          | Sets the application description i18n key. The   |
|                          | way this description is actually leveraged       |
| `String`                 | depends on the UI channel.                       |
+--------------------------+--------------------------------------------------+
| **exitAction**           | Configures the exit action to be executed        |
|                          | whenever the user wants to quit the application. |
| ``                       | The default installed exit action first checks   |
|                          | for started module(s) dirty state(s), then       |
|                          | notifies user of pending persistent changes.     |
|                          | When no flush is needed or the user bypasses     |
|                          | them, the actual exit is performed.              |
+--------------------------+--------------------------------------------------+
| **forcedStartingLocale** | Configures the locale used to initiate the login |
|                          | process. Whenever the forced starting locale is  |
| `String`                 | {@code null}, the client host default locale is  |
|                          | used.                                            |
|                          |                                                  |
|                          | As soon as the user logs-in, his locale is then  |
|                          | used to translate the UI. Whenever the login     |
|                          | process is disabled, then the forced starting    |
|                          | locale is kept as the UI i18n locale.            |
+--------------------------+--------------------------------------------------+
| **frameHeight**          | Sets the preferred application frame height. How |
|                          | this dimension is leveraged depends on the UI    |
| `Integer`                | channel.                                         |
+--------------------------+--------------------------------------------------+
| **frameWidth**           | Sets the preferred application frame width. How  |
|                          | this dimension is leveraged depends on the UI    |
| `Integer`                | channel.                                         |
+--------------------------+--------------------------------------------------+
| **helpActionMap**        | Configures the help action map. The help action  |
|                          | map should contain actions that are related to   |
| ``                       | helping the user (online help, reference manual, |
|                          | tutorial, version dialog...).                    |
|                          |                                                  |
|                          | The help action map is visually distinguished    |
|                          | from the regular application action map. For     |
|                          | instance elp actions can be represented in a     |
|                          | menu that is right-aligned in the menu bar.      |
+--------------------------+--------------------------------------------------+
| **iconImageURL**         | Sets the icon image URL that is used as the      |
|                          | application icon. Supported URL protocols        |
| `String`                 | include :                                        |
|                          |                                                  |
|                          | -   all JVM supported protocols                  |
|                          |                                                  |
|                          | -   the **jar:/** pseudo URL protocol            |
|                          |                                                  |
|                          | -   the **classpath:/** pseudo URL protocol      |
+--------------------------+--------------------------------------------------+
| **loginAction**          | Configures an action to be executed just after   |
|                          | the user has successfully logged-in but before   |
| ``                       | any UI initialization has begun. An example of   |
|                          | such an action would be constructing a map of    |
|                          | dynamic user right based on some arbitrary data  |
|                          | store so that the UI construction can actually   |
|                          | depend on these extracted values.                |
+--------------------------+--------------------------------------------------+
| **loginContextName**     | Configures the name of the JAAS login context to |
|                          | use to authenticate users. It must reference a   |
| `String`                 | valid JAAS context that is installed in the JVM, |
|                          | either through setting the {@code                |
|                          | java.security.auth.login.config} system property |
|                          | or through server-specific configuration.        |
+--------------------------+--------------------------------------------------+
| **loginViewDescriptor**  | Configures the view descriptor used to create    |
|                          | the login dialog. The default built-in login     |
| ``                       | view descriptor includes a standard              |
|                          | login/password form.                             |
+--------------------------+--------------------------------------------------+
| **mvcBinder**            | Configures the MVC binder used to apply          |
|                          | model-view bindings. There is hardly any reason  |
| ``                       | for the developer to change the default binder   |
|                          | but it can be customized here.                   |
+--------------------------+--------------------------------------------------+
| **name**                 | Sets the application name i18n key. The way this |
|                          | name is actually leveraged depends on the UI     |
| `String`                 | channel but it typically generates (part of the) |
|                          | frame title.                                     |
+--------------------------+--------------------------------------------------+
| **navigationActionMap**  | Configures the navigation action map. The        |
|                          | navigation action map should contain actions     |
| ``                       | that are related to navigating the modules and   |
|                          | workspace history, e.g. previous, next, home,    |
|                          | and so on.                                       |
+--------------------------+--------------------------------------------------+
| **onModuleEnterAction**  | Configures an action to be executed each time a  |
|                          | module of the application is entered. The action |
| ``                       | is executed in the context of the module the     |
|                          | user enters.                                     |
+--------------------------+--------------------------------------------------+
| **onModuleExitAction**   | Configures an action to be executed each time a  |
|                          | module of the application is exited. The action  |
| ``                       | is executed in the context of the module the     |
|                          | user exits. Default frontend controller          |
|                          | configuration installs an action that checks     |
|                          | current module dirty state.                      |
+--------------------------+--------------------------------------------------+
| **onModuleStartupAction* | Configures an action to be executed each time a  |
| *                        | module of the application is started. The action |
|                          | is executed in the context of the module the     |
| ``                       | user starts.                                     |
+--------------------------+--------------------------------------------------+
| **secondaryActionMap**   | Assigns the view secondary action map. Same      |
|                          | rules as the primary action map apply except     |
| ``                       | that actions in this map should be visually      |
|                          | distinguished from the main action map, e.g.     |
|                          | placed in another toolbar.                       |
+--------------------------+--------------------------------------------------+
| **startupAction**        | Configures an action to be executed on an empty  |
|                          | UI context when the application starts. The      |
| ``                       | action executes once the user has logged-in and  |
|                          | the main UI has been constructed based on its    |
|                          | access rights.An example of such an action would |
|                          | be a default workspace/module opening and        |
|                          | selection, a "tip of the day" like action, ...   |
+--------------------------+--------------------------------------------------+
| **viewFactory**          | Configures the view factory used to create views |
|                          | from view descriptors. Using a custom view       |
| `​<​E​,F​,G​>​`          | factory is typically needed for extending        |
|                          | Jspresso to use custom view descriptors / UI     |
|                          | components. Of course, there is a view factory   |
|                          | concrete type per UI channel.                    |
+--------------------------+--------------------------------------------------+
| **workspaces**           | Configures the workspaces that are available in  |
|                          | the application. Workspaces are application      |
| `List​<​​>​`             | entry-points and are hierarchically composed of  |
|                          | modules / sub-modules.                           |
+--------------------------+--------------------------------------------------+
| **workspacesMenuIconImag | Sets the icon image URL that is used as the      |
| eUrl**                   | workspace menu icon. Supported URL protocols     |
|                          | include :                                        |
| `String`                 |                                                  |
|                          | -   all JVM supported protocols                  |
|                          |                                                  |
|                          | -   the **jar:/** pseudo URL protocol            |
|                          |                                                  |
|                          | -   the **classpath:/** pseudo URL protocol      |
+--------------------------+--------------------------------------------------+

: AbstractFrontendController properties

AbstractRemoteController
------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This is is the base implementation of all "remotable" frontend controller.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **statusInfo**           | {@inheritDoc}                                    |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractRemoteController properties

DefaultRemoteController
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

This is is the default implementation of a "remotable" frontend controller. It will implement a 3-tier architecture. The remote controller lives on server-side and communicates with generic UI engines that are deployed on client side. As of now, the remote frontend controller is used by the **Flex** and **qooxdoo** frontends. Communication happens through the use of generic UI commands that are produced/consumed on both sides of the network.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **clipboardContent**     | {@inheritDoc}                                    |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: DefaultRemoteController properties

MobileRemoteController
----------------------

-   **Full name** : ``

-   **Super-type** : ``

This is is the mobile implementation of a "remotable" frontend controller.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **clipboardContent**     | Not supported in mobile environment.             |
|                          | {@inheritDoc}                                    |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: MobileRemoteController properties

DefaultSwingController
----------------------

-   **Full name** : ``

-   **Super-type** : ``

This is is the default implementation of the **Swing** frontend controller. It will implement a 2-tier architecture that is particularly useful for the development/debugging phases. Workspaces are displayed using an MDI UI using internal frames.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **clipboardContent**     | {@inheritDoc}                                    |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **statusInfo**           | {@inheritDoc}                                    |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: DefaultSwingController properties


