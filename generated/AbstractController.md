## AbstractController

#### <a name="org.jspresso.framework.application.AbstractController"></a>AbstractController

+ **Full name** : [`org.jspresso.framework.application.AbstractController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/AbstractController.html)
+ **Super-type** : `AbstractPropertyChangeCapable`
+ **Sub-types** : [`AbstractBackendController`](#org.jspresso.framework.application.backend.AbstractBackendController), [`AbstractFrontendController`](#org.jspresso.framework.application.frontend.controller.AbstractFrontendController)



Abstract base class for controllers. Controllers role is to adapt the
 application to its environment. Jspresso relies on two different types of
 controllers :
 <ul>
 <li>The frontend controller is responsible for managing UI interactions.
 Naturally, the type of frontend controller used depends on the UI channel.</li>
 <li>The backend controller is responsible for managing the application
 session as well as transactions and persistence operations.</li>
 </ul>



<table>
<caption>AbstractController properties</caption>
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
<td align="left"><p><strong>customExceptionHandler</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/exception/IExceptionHandler.html">IException&#x200B;Handler</a></code></p></td>
<td><p>Configures a custom exception handler on the controller. The controller
 itself is an exception handler and is used as such across most of the
 application layers. Jspresso philosophy is to use unchecked exceptions in
 services, business rules, and so on, so that, whenever an exception occurs,
 it climbs the call stack up to an exception handler (usually one of the
 controller). Whenever a custom exception handler is configured, the
 exception handling is delegated to it, allowing the exceptions to be
 refined or handled differently than for the built-in case. The exception
 handler can either :
 <ul>
 <li>return <code>true</code> if the exception was completely processed and
 does not need any further action.</li>
 <li>return <code>false</code> if the exception was either not or
 un-completely processed and needs to continue the built-in handling.</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.AbstractBackendController"></a>AbstractBackendController

+ **Full name** : [`org.jspresso.framework.application.backend.AbstractBackendController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/AbstractBackendController.html)
+ **Super-type** : [`AbstractController`](#org.jspresso.framework.application.AbstractController)
+ **Sub-types** : [`HibernateBackendController`](#org.jspresso.framework.application.backend.persistence.hibernate.HibernateBackendController)



Base class for backend application controllers. Backend controllers are
 responsible for :
 <ul>
 <li>keeping a reference to the application session</li>
 <li>keeping a reference to the application workspaces and their state</li>
 <li>keeping a reference to the application clipboard</li>
 <li>keeping a reference to the entity registry that guarantees the in-memory
 entity reference unicity in the user session</li>
 <li>keeping a reference to the entity dirt recorder that keeps track of
 entity changes to afterwards optimize the ORM operations</li>
 <li>keeping a reference to the Spring transaction template and its peer
 &quot;Unit of Work&quot; -aka UOW- that is responsible to manage application
 transactions and adapt the underlying transaction system (Hibernate, JTA,
 ...)</li>
 </ul>
 Moreover, the backend controller will provide several model related factories
 that can be configured to customize default, built-in behaviour. Most of
 these configured properties will be accessible using the corresponding
 getters. Those getters should be used by the service layer.



<table>
<caption>AbstractBackendController properties</caption>
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
<td align="left"><p><strong>applicationSession</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/session/IApplicationSession.html">IApplication&#x200B;Session</a></code></p></td>
<td><p>Assigns the application session to this backend controller. This property
 can only be set once and should only be used by the DI container. It will
 rarely be changed from built-in defaults unless you need to specify a
 custom implementation instance to be used.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>asyncActionsThreadGroup</strong></p><p><code>Thread&#x200B;Group</code></p></td>
<td><p>Sets async actions thread group.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>asyncExecutorsMaxCount</strong></p><p><code>int</code></p></td>
<td><p>Configures the maximum count of concurrent asynchronous action executors.
 It defaults to <code>10</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>carbonEntityCloneFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntityCloneFactory.html">IEntity&#x200B;Clone&#x200B;Factory</a></code></p></td>
<td><p>Configures the entity clone factory used to carbon-copy entities. An entity
 carbon-copy is an technical copy of an entity, including id and version but
 excluding relationship properties. This mechanism is used by the controller
 when duplicating entities into the UOW to allow for memory state aware
 transactions. This property should only be used by the DI container. It
 will rarely be changed from built-in defaults unless you need to specify a
 custom implementation instance to be used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>clientTimeZone</strong></p><p><code>Time&#x200B;Zone</code></p></td>
<td><p>Sets client time zone.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>collectionFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/component/IComponentCollectionFactory.html">IComponent&#x200B;Collection&#x200B;Factory</a></code></p></td>
<td><p>Configures the factory responsible for creating entities (or components)
 collections that are held by domain relationship properties. This property
 should only be used by the DI container. It will rarely be changed from
 built-in defaults unless you need to specify a custom implementation
 instance to be used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>customSecurityPlugin</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/security/ISecurityPlugin.html">ISecurity&#x200B;Plugin</a></code></p></td>
<td><p>Configures a custom security plugin on the controller. The controller
 itself is a security handler and is used as such across most of the
 application layers. Before delegating to the custom security handler, the
 controller will apply role-based security rules that cannot be disabled.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>customTranslationPlugin</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/i18n/ITranslationPlugin.html">ITranslation&#x200B;Plugin</a></code></p></td>
<td><p>Configures a custom translation plugin on the controller. The controller
 itself is a translation provider and is used as such across most of the
 application layers. The custom translation plugin is used to override the
 default static, bundle-based, i18n scheme.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>dirtyTrackingEnabled</strong></p><p><code>boolean</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>entityFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntityFactory.html">IEntity&#x200B;Factory</a></code></p></td>
<td><p>Configures the entity factory to use to create new entities. Backend
 controllers only accept instances of
 <code>ControllerAwareProxyEntityFactory</code> or a subclass. This is
 because the backend controller must keep track of created entities.
 Jspresso entity implementations also use the controller from which they
 were created behind the scene.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>modelConnectorFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/binding/model/IModelConnectorFactory.html">IModel&#x200B;Connector&#x200B;Factory</a></code></p></td>
<td><p>Configures the model connector factory to use to create new model
 connectors. Connectors are adapters used by the binding layer to access
 domain model values.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>referenceTimeZoneId</strong></p><p><code>String</code></p></td>
<td><p>Sets reference time zone id.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>slaveControllerFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/IBackendControllerFactory.html">IBackend&#x200B;Controller&#x200B;Factory</a></code></p></td>
<td><p>Sets the slaveControllerFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>throwExceptionOnBadUsage</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the backend controller to throw or not an exception whenever a
 bad usage is detected like manually merging a dirty entity from an ongoing
 UOW.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>transactionTemplate</strong></p><p><code>Transaction&#x200B;Template</code></p></td>
<td><p>Assigns the Spring transaction template to this backend controller. This
 property can only be set once and should only be used by the DI container.
 It will rarely be changed from built-in defaults unless you need to specify
 a custom implementation instance to be used.
 <p/>
 The configured instance is the one that will be returned by the
 controller's <code>getTransactionTemplate()</code> method that should be
 used by the service layer for transaction management.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>translationProvider</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/i18n/ITranslationProvider.html">ITranslation&#x200B;Provider</a></code></p></td>
<td><p>Configures the translation provider used to compute internationalized
 messages and labels.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>userPreferencesStore</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/preferences/IPreferencesStore.html">IPreferences&#x200B;Store</a></code></p></td>
<td><p>Sets the user preference store.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.backend.persistence.hibernate.HibernateBackendController"></a>HibernateBackendController

+ **Full name** : [`org.jspresso.framework.application.backend.persistence.hibernate.HibernateBackendController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/backend/persistence/hibernate/HibernateBackendController.html)
+ **Super-type** : [`AbstractBackendController`](#org.jspresso.framework.application.backend.AbstractBackendController)



This is the default Jspresso implementation of Hibernate-based backend
 controller.



<table>
<caption>HibernateBackendController properties</caption>
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
<td align="left"><p><strong>defaultTxFlushMode</strong></p><p><code>String</code></p></td>
<td><p>Sets the default Hibernate flush mode to apply to the Hibernate session
 when it is bound to a transaction. Defaults to {@link FlushMode#COMMIT}.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>entityFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/entity/IEntityFactory.html">IEntity&#x200B;Factory</a></code></p></td>
<td><p>Configures the entity factory to use to create new entities. Backend
 controllers only accept instances of
 <code>HibernateControllerAwareProxyEntityFactory</code> or a subclass.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>hibernateSessionFactory</strong></p><p><code>Session&#x200B;Factory</code></p></td>
<td><p>Sets the hibernateSessionFactory.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>noTxDataSource</strong></p><p><code>Data&#x200B;Source</code></p></td>
<td><p>Sets the noTxDataSource.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.controller.AbstractFrontendController"></a>AbstractFrontendController

+ **Full name** : [`org.jspresso.framework.application.frontend.controller.AbstractFrontendController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/controller/AbstractFrontendController.html)
+ **Super-type** : [`AbstractController`](#org.jspresso.framework.application.AbstractController)
+ **Sub-types** : [`AbstractRemoteController`](#org.jspresso.framework.application.frontend.controller.remote.AbstractRemoteController), [`DefaultSwingController`](#org.jspresso.framework.application.frontend.controller.swing.DefaultSwingController)



Base class for frontend application controllers. Frontend controllers are
 responsible for adapting the Jspresso application to the UI channel. Although
 this generic abstract class centralizes most of the controller's
 configuration, it will be subclassed by concrete, UI dependent subclasses to
 implement polymorphic behaviour.
 <p>
 More than a behavioural adapter, the frontend controller will also be the
 place where you define the top-level application structure like the workspace
 list, the name, the application-wide actions, ...



<table>
<caption>AbstractFrontendController properties</caption>
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
<td align="left"><p><strong>actionMap</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/ActionMap.html">Action&#x200B;Map</a></code></p></td>
<td><p>Configures an application-wide action map that will be installed in the
 main application frame. These actions are available at any time from the UI
 and thus, do not depend on the active workspace. General purpose actions
 like &quot;Change password&quot; action should be installed here.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>checkActionThreadSafety</strong></p><p><code>boolean</code></p></td>
<td><p>Sets the checkActionThreadSafety.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>clientPreferencesStore</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/preferences/IPreferencesStore.html">IPreferences&#x200B;Store</a></code></p></td>
<td><p>Sets the clientPreferenceStore.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>description</strong></p><p><code>String</code></p></td>
<td><p>Sets the application description i18n key. The way this description is
 actually leveraged depends on the UI channel.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>exitAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the exit action to be executed whenever the user wants to quit
 the application. The default installed exit action first checks for started
 module(s) dirty state(s), then notifies user of pending persistent changes.
 When no flush is needed or the user bypasses them, the actual exit is
 performed.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>forcedStartingLocale</strong></p><p><code>String</code></p></td>
<td><p>Configures the locale used to initiate the login process. Whenever the
 forced starting locale is <code>null</code>, the client host default locale
 is used.
 <p>
 As soon as the user logs-in, his locale is then used to translate the UI.
 Whenever the login process is disabled, then the forced starting locale is
 kept as the UI i18n locale.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>frameHeight</strong></p><p><code>Integer</code></p></td>
<td><p>Sets the preferred application frame height. How this dimension is
 leveraged depends on the UI channel.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>frameWidth</strong></p><p><code>Integer</code></p></td>
<td><p>Sets the preferred application frame width. How this dimension is leveraged
 depends on the UI channel.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>helpActionMap</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/ActionMap.html">Action&#x200B;Map</a></code></p></td>
<td><p>Configures the help action map. The help action map should contain actions
 that are related to helping the user (online help, reference manual,
 tutorial, version dialog...).
 <p>
 The help action map is visually distinguished from the regular application
 action map. For instance elp actions can be represented in a menu that is
 right-aligned in the menu bar.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconImageURL</strong></p><p><code>String</code></p></td>
<td><p>Sets the icon image URL that is used as the application icon. Supported URL
 protocols include :
 <ul>
 <li>all JVM supported protocols</li>
 <li>the <b>jar:/</b> pseudo URL protocol</li>
 <li>the <b>classpath:/</b> pseudo URL protocol</li>
 </ul></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>loginAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed just after the user has successfully
 logged-in but before any UI initialization has begun. An example of such an
 action would be constructing a map of dynamic user right based on some
 arbitrary data store so that the UI construction can actually depend on
 these extracted values.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>loginContextName</strong></p><p><code>String</code></p></td>
<td><p>Configures the name of the JAAS login context to use to authenticate users.
 It must reference a valid JAAS context that is installed in the JVM, either
 through setting the <code>java.security.auth.login.config</code> system
 property or through server-specific configuration.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>loginViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the view descriptor used to create the login dialog. The default
 built-in login view descriptor includes a standard login/password form.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>mvcBinder</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/binding/IMvcBinder.html">IMvc&#x200B;Binder</a></code></p></td>
<td><p>Configures the MVC binder used to apply model-view bindings. There is
 hardly any reason for the developer to change the default binder but it
 can be customized here.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>Sets the application name i18n key. The way this name is actually leveraged
 depends on the UI channel but it typically generates (part of the) frame
 title.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>navigationActionMap</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/ActionMap.html">Action&#x200B;Map</a></code></p></td>
<td><p>Configures the navigation action map. The navigation action map should
 contain actions that are related to navigating the modules and workspace
 history, e.g. previous, next, home, and so on.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>onModuleEnterAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed each time a module of the application
 is entered. The action is executed in the context of the module the user
 enters.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>onModuleExitAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed each time a module of the application
 is exited. The action is executed in the context of the module the user
 exits. Default frontend controller configuration installs an action that
 checks current module dirty state.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>onModuleStartupAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed each time a module of the application
 is started. The action is executed in the context of the module the user
 starts.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>secondaryActionMap</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/ActionMap.html">Action&#x200B;Map</a></code></p></td>
<td><p>Assigns the view secondary action map. Same rules as the primary action map
 apply except that actions in this map should be visually distinguished from
 the main action map, e.g. placed in another toolbar.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>startupAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures an action to be executed on an empty UI context when the
 application starts. The action executes once the user has logged-in and the
 main UI has been constructed based on its access rights.An example of such
 an action would be a default workspace/module opening and selection, a
 &quot;tip of the day&quot; like action, ...</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>viewFactory</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/IViewFactory.html">IView&#x200B;Factory</a>&#x200B;&lt;&#x200B;E&#x200B;,F&#x200B;,G&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the view factory used to create views from view descriptors.
 Using a custom view factory is typically needed for extending Jspresso to
 use custom view descriptors / UI components. Of course, there is a view
 factory concrete type per UI channel.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>workspaces</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/model/Workspace.html">Workspace</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the workspaces that are available in the application. Workspaces
 are application entry-points and are hierarchically composed of modules /
 sub-modules.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>workspacesMenuIconImageUrl</strong></p><p><code>String</code></p></td>
<td><p>Sets the icon image URL that is used as the workspace menu icon. Supported
 URL protocols include :
 <ul>
 <li>all JVM supported protocols</li>
 <li>the <b>jar:/</b> pseudo URL protocol</li>
 <li>the <b>classpath:/</b> pseudo URL protocol</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.controller.remote.AbstractRemoteController"></a>AbstractRemoteController

+ **Full name** : [`org.jspresso.framework.application.frontend.controller.remote.AbstractRemoteController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/controller/remote/AbstractRemoteController.html)
+ **Super-type** : [`AbstractFrontendController`](#org.jspresso.framework.application.frontend.controller.AbstractFrontendController)
+ **Sub-types** : [`DefaultRemoteController`](#org.jspresso.framework.application.frontend.controller.remote.DefaultRemoteController), [`MobileRemoteController`](#org.jspresso.framework.application.frontend.controller.remote.mobile.MobileRemoteController)



This is is the base implementation of all &quot;remotable&quot; frontend
 controller.



<table>
<caption>AbstractRemoteController properties</caption>
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
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>statusInfo</strong></p><p><code>String</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.controller.remote.DefaultRemoteController"></a>DefaultRemoteController

+ **Full name** : [`org.jspresso.framework.application.frontend.controller.remote.DefaultRemoteController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/controller/remote/DefaultRemoteController.html)
+ **Super-type** : [`AbstractRemoteController`](#org.jspresso.framework.application.frontend.controller.remote.AbstractRemoteController)



This is is the default implementation of a &quot;remotable&quot; frontend
 controller. It will implement a 3-tier architecture. The remote controller
 lives on server-side and communicates with generic UI engines that are
 deployed on client side. As of now, the remote frontend controller is used by
 the <b>Flex</b> and <b>qooxdoo</b> frontends. Communication happens through
 the use of generic UI commands that are produced/consumed on both sides of
 the network.



<table>
<caption>DefaultRemoteController properties</caption>
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
<td align="left"><p><strong>clipboardContent</strong></p><p><code>String</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.controller.remote.mobile.MobileRemoteController"></a>MobileRemoteController

+ **Full name** : [`org.jspresso.framework.application.frontend.controller.remote.mobile.MobileRemoteController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/controller/remote/mobile/MobileRemoteController.html)
+ **Super-type** : [`AbstractRemoteController`](#org.jspresso.framework.application.frontend.controller.remote.AbstractRemoteController)



This is is the mobile implementation of a &quot;remotable&quot; frontend
 controller.



<table>
<caption>MobileRemoteController properties</caption>
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
<td align="left"><p><strong>clipboardContent</strong></p><p><code>String</code></p></td>
<td><p>Not supported in mobile environment.
 <p/>
 {@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.application.frontend.controller.swing.DefaultSwingController"></a>DefaultSwingController

+ **Full name** : [`org.jspresso.framework.application.frontend.controller.swing.DefaultSwingController`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/application/frontend/controller/swing/DefaultSwingController.html)
+ **Super-type** : [`AbstractFrontendController`](#org.jspresso.framework.application.frontend.controller.AbstractFrontendController)



This is is the default implementation of the <b>Swing</b> frontend
 controller. It will implement a 2-tier architecture that is particularly
 useful for the development/debugging phases. Workspaces are displayed using
 an MDI UI using internal frames.



<table>
<caption>DefaultSwingController properties</caption>
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
<td align="left"><p><strong>clipboardContent</strong></p><p><code>String</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>name</strong></p><p><code>String</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>statusInfo</strong></p><p><code>String</code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


