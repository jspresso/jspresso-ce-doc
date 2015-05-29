Reference for FrontendAction hierarchy
======================================

FrontendAction
--------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``, ``

This is the base class for frontend actions. To get a better understanding of how actions are organized in Jspresso, please refer to {@code AbstractAction} documentation.

This base class allows for visual (name, icon, toolTip) as well as accessibility (accelerator, mnemonic shortcuts) and actionability (using gates) parametrization.

A frontend action is to be executed by the frontend controller in the context of the UI. It can thus access the view structure, interact visually with the user, and so on. A frontend action can chain a backend action but the opposite will be prevented.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **acceleratorAsString**  | Configures a keyboard accelerator shortcut on    |
|                          | this action. Support of this feature depends on  |
| `String`                 | the UI execution platform. The syntax used       |
|                          | consists of listing keys that should be pressed  |
|                          | to trigger the action, i.e. {@code alt d} or     |
|                          | {@code ctrl c}. This is the syntax supported by  |
|                          | the {@code                                       |
|                          | javax.swing.KeyStroke\#getKeyStroke(...)} swing  |
|                          | static method.                                   |
+--------------------------+--------------------------------------------------+
| **actionabilityGates**   | Assigns a collection of gates to determine       |
|                          | action *actionability*. An action will be        |
| `Collection​<​​>​`       | considered actionable (enabled) if and only if   |
|                          | all gates are open. This mechanism is mainly     |
|                          | used for dynamic UI authorization based on model |
|                          | state, e.g. a validated invoice should not be    |
|                          | validated twice.                                 |
|                          |                                                  |
|                          | Action assigned gates will be cloned for each    |
|                          | concrete action instance created and bound to    |
|                          | its respective UI component (usually a button).  |
|                          | So basically, each action instance will have its |
|                          | own, unshared collection of actionability gates. |
|                          |                                                  |
|                          | Jspresso provides a useful set of gate types,    |
|                          | like the binary property gate that open/close    |
|                          | based on the value of a boolean property of the  |
|                          | view model the action is installed to.           |
|                          |                                                  |
|                          | By default, frontend actions are assigned a      |
|                          | generic gate that closes (disables the action)   |
|                          | when the view is not assigned any model.         |
+--------------------------+--------------------------------------------------+
| **collectionBased**      | Declares the action as working on a collection   |
|                          | of objects. Collection based actions will        |
| `boolean`                | typically be installed on selectable views       |
|                          | (table, list, tree) and will be enabled only     |
|                          | when the view selection is not empty (a default  |
|                          | gate is installed for this purpose). Moreover,   |
|                          | model gates that are configured on collection    |
|                          | based actions take their model from the view     |
|                          | selected components instead of the view model    |
|                          | itself. In case of multi-selection enabled UI    |
|                          | views, the actionability gates will actually     |
|                          | open if and only if their opening condition is   |
|                          | met for all the selected items.                  |
+--------------------------+--------------------------------------------------+
| **description**          | Sets the key used to compute the                 |
|                          | internationalized description of the action. The |
| `String`                 | translated description is then usually used as   |
|                          | toolTip for the action.                          |
+--------------------------+--------------------------------------------------+
| **icon**                 | Sets the icon.                                   |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **iconImageURL**         | Sets the icon image URL used to decorate the     |
|                          | action UI component peer.                        |
| `String`                 |                                                  |
|                          | Supported URL protocols include :                |
|                          |                                                  |
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
| **mnemonicAsString**     | Configures the mnemonic key used for this        |
|                          | action. Support of this feature depends on the   |
| `String`                 | UI execution platform. Mnemonics are typically   |
|                          | used in menu and menu items.                     |
+--------------------------+--------------------------------------------------+
| **multiSelectionEnabled* | Declares the action as being able to run on a    |
| *                        | collection containing more than 1 element. A     |
|                          | multiSelectionEnabled = false action will be     |
| `boolean`                | disabled when the selection contains no or more  |
|                          | than one element.                                |
+--------------------------+--------------------------------------------------+
| **name**                 | Sets the key used to compute the                 |
|                          | internationalized name of the action. The        |
| `String`                 | translated name is then usually used as label    |
|                          | for the action (button label, menu label, ...).  |
+--------------------------+--------------------------------------------------+
| **styleName**            | Assigns the style name to use for this view. The |
|                          | way it is actually leveraged depends on the UI   |
| `String`                 | channel. It will generally be mapped to some     |
|                          | sort of CSS style name.                          |
|                          |                                                  |
|                          | Default value is {@code null}, meaning that a    |
|                          | default style is used.                           |
+--------------------------+--------------------------------------------------+

: FrontendAction properties

AbstractChartAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This is the abstract base class for *Fusioncharts* (flash based charting library) display actions. It holds several common properties that are independent from the actual, concrete, implementations.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **actions**              | Configures a list of actions to install in the   |
|                          | chart modal dialog.                              |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+
| **chartDescriptor**      | This property describes the chart to compute and |
|                          | display. A chart descriptor is a simple data     |
| ``                       | structure that provides :                        |
|                          |                                                  |
|                          | -   the URL of the chart SWF archive (can be     |
|                          |     loaded by the classloader using a classpath  |
|                          |     pseudo URL)                                  |
|                          |                                                  |
|                          | -   the title of the chart                       |
|                          |                                                  |
|                          | -   the width/height of the chart area           |
|                          |                                                  |
|                          | -   an abstract method to implement in order to  |
|                          |     compute the chart XML data                   |
+--------------------------+--------------------------------------------------+
| **jdbcTemplate**         | Configures the JDBC template to be used by the   |
|                          | chart to compute its data.                       |
| `Jdbc​Template`          |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractChartAction properties

DisplayChartAction
------------------

-   **Full name** : ``

-   **Super-type** : ``

This is the concrete implementation of the Fusionchart display action. This action is specialized by UI channel, i.e. server based UI channels (Ajax, Flex, ULC) will use *{@code server}* {@code .DisplayChartAction} whereas standalone UI channels (Swing) will use *{@code standalone}*{@code .DisplayChartAction}.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : DisplayChartAction properties

AbstractEditComponentAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This action serves as a base class for actions that pop-pup a dialog to edit a component.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **complementaryActions** | Installs a list of complementary actions to      |
|                          | install between the ok and cancel actions.       |
| `List​<​?​>​`            |                                                  |
+--------------------------+--------------------------------------------------+
| **viewDescriptor**       | Configures the view descriptor to be used to     |
|                          | create the component editing view that will be   |
| ``                       | installed in the dialog.                         |
+--------------------------+--------------------------------------------------+

: AbstractEditComponentAction properties

EditComponentAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``

This action pulls a model out of the context (action parameter or selected model if action parameter is not filled), creates a view, binds it on the model and prepares for chaining with a modal dialog action to pop-up the result. The translated name of the action, whenever not empty, will be used as the dialog title. If the context extracted model is a collection, the first element of the collection is used. Custom actions ( {@code okAction} and {@code cancelAction}) can be configured to take care of user decision when closing the dialog.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cancelAction**         | Configures the action to be installed in the     |
|                          | dialog when the user cancels the component       |
| ``                       | edition.                                         |
+--------------------------+--------------------------------------------------+
| **okAction**             | Configures the action to be installed in the     |
|                          | dialog when the user confirms the component      |
| ``                       | edition.                                         |
+--------------------------+--------------------------------------------------+

: EditComponentAction properties

ChangePasswordAction
--------------------

-   **Full name** : ``

-   **Super-type** : ``

This is the frontend action to initiate the logged-in user password change. It will install a form view with a custom component designed to host :

1.  the current password

2.  the new password

3.  the confirmation for the new password

This action must be combined (setting {@code okAction}) with a concrete subclass of backend {@code AbstractChangePasswordAction} that performs the actual password change depending on the authentication backend. Jspresso offers two concrete implementations :

-   {@code LdapChangePasswordAction} for LDAP based authentication backend

-   {@code DatabaseChangePasswordAction} for JDBC based authentication backend

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ChangePasswordAction properties

EditBackendControllerAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a frontend action to display a view backed by the session backend controller itself. It is used, for instance, to display the running asynchronous actions.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditBackendControllerAction properties

EditFrontendControllerAction
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a frontend action to display a view backed by the session backend controller itself. It is used, for instance, to display the running asynchronous actions.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditFrontendControllerAction properties

EditReportParametersAction
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action takes a report ({@code IReport}) from the context ( {@code REPORT\_ACTION\_PARAM} key) and pops-up a form to allow for the report input parameters customization.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditReportParametersAction properties

MobileEditComponentAction
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is the mobile version of the edit component action. {@code okAction} and {@code cancelAction}) are added as page actions instead of dialog ones.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : MobileEditComponentAction properties

EditSelectedComponentAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action should be installed on collection views. It takes the selected component and edit it in a modal dialog. Editing happens in a "Unit of Work" meaning that it can be rolled-back when canceling.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cancelAction**         | Sets the cancelAction.                           |
|                          |                                                  |
| `​<​E​,F​,G​>​`          |                                                  |
+--------------------------+--------------------------------------------------+
| **okAction**             | Sets the okAction.                               |
|                          |                                                  |
| `​<​E​,F​,G​>​`          |                                                  |
+--------------------------+--------------------------------------------------+

: EditSelectedComponentAction properties

AbstractMessageAction
---------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``

This is the base class for all UI message based communication actions. This type of action generally opens a modal dialog to display an informational message, ask a question, and so on. It takes the message from the action context parameter and supports basic HTML formatting. In order for the message to be interpreted as HTML, it must be surrounded by {@code \<HTML\>} tags.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : AbstractMessageAction properties

InfoAction
----------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action pops-up an informational message to the user.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : InfoAction properties

StaticInfoAction
----------------

-   **Full name** : ``

-   **Super-type** : ``

This action pops-up an informational message to the user. The message, instead of being extracted out of the context, is parametrized statically into the action through its internationalization key.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **messageCode**          | Configures the i18n key used to translate the    |
|                          | message that is to be displayed to the user.     |
| `String`                 | When the action executes, the statically         |
|                          | configured message is first translated, then     |
|                          | placed into the action context to be popped-up.  |
+--------------------------+--------------------------------------------------+

: StaticInfoAction properties

OkCancelAction
--------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action pops-up an Ok - Cancel confirmation option. Depending on user answer, another action is triggered. The Ok - Cancel alternative actions are parametrized statically.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cancelAction**         | Assigns the action to execute when the user      |
|                          | cancels the option.                              |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **okAction**             | Assigns the action to execute when the user      |
|                          | confirms the option.                             |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: OkCancelAction properties

StaticOkCancelAction
--------------------

-   **Full name** : ``

-   **Super-type** : ``

This action pops-up an Ok - Cancel confirmation option. The message, instead of being extracted out of the context, is parametrized statically into the action through its internationalization key.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **messageCode**          | Configures the i18n key used to translate the    |
|                          | message that is to be displayed to the user.     |
| `String`                 | When the action executes, the statically         |
|                          | configured message is first translated, then     |
|                          | placed into the action context to be popped-up.  |
+--------------------------+--------------------------------------------------+

: StaticOkCancelAction properties

YesNoAction
-----------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action pops-up a binary question. Depending on user answer, another action is triggered. The Yes - No alternative actions are parametrized statically.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **noAction**             | Assigns the action to execute when the user      |
|                          | answers negatively to the question.              |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **yesAction**            | Assigns the action to execute when the user      |
|                          | answers positively to the question.              |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: YesNoAction properties

StaticYesNoAction
-----------------

-   **Full name** : ``

-   **Super-type** : ``

This action pops-up a binary question. The message, instead of being extracted out of the context, is parametrized statically into the action through its internationalization key.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **messageCode**          | Configures the i18n key used to translate the    |
|                          | message that is to be displayed to the user.     |
| `String`                 | When the action executes, the statically         |
|                          | configured message is first translated, then     |
|                          | placed into the action context to be popped-up.  |
+--------------------------+--------------------------------------------------+

: StaticYesNoAction properties

YesNoCancelAction
-----------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action pops-up a binary question with Cancel option. Depending on user answer, another action is triggered. The Yes - No - Cancel alternative actions are parametrized statically.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cancelAction**         | Assigns the action to execute when the user      |
|                          | cancels the option.                              |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **noAction**             | Assigns the action to execute when the user      |
|                          | answers negatively to the question.              |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **yesAction**            | Assigns the action to execute when the user      |
|                          | answers positively to the question.              |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: YesNoCancelAction properties

StaticYesNoCancelAction
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

This action pops-up a binary question with Cancel option. The message, instead of being extracted out of the context, is parametrized statically into the action through its internationalization key.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **messageCode**          | Configures the i18n key used to translate the    |
|                          | message that is to be displayed to the user.     |
| `String`                 | When the action executes, the statically         |
|                          | configured message is first translated, then     |
|                          | placed into the action context to be popped-up.  |
+--------------------------+--------------------------------------------------+

: StaticYesNoCancelAction properties

AbstractModuleDirtyStateAction
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This is the base abstract class for actions that are responsible for checking module dirty state. *Dirty* is taken in the sense of an entity needing to be flushed to the persistent store. Among modules that are to be checked, a collection module is marked dirty if and only if one of its module objects is an entity which is dirty. On the other hand, a bean module is marked dirty if and only if its (single) module object is an entity and is dirty.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : AbstractModuleDirtyStateAction properties

CheckAllModulesDirtyStateAction
-------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action recomputes all application modules dirty state. All the workspaces are traversed as well as, for each workspace, the whole module hierarchy. This action is typically triggered before a user exists the application to bring up a notification of potentially lost pending changes.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : CheckAllModulesDirtyStateAction properties

CheckModuleDirtyStateAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action recomputes the dirty state of the current selected module. It is typically triggered when the user navigates (leaves) out of the module to compute a visual notification of a pending change.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : CheckModuleDirtyStateAction properties

AnimateAction
-------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

Selects animates current page.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **animation**            | Sets animation.                                  |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **callbackAction**       | Sets callback action.                            |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **direction**            | Sets direction.                                  |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **duration**             | Sets duration.                                   |
|                          |                                                  |
| `int`                    |                                                  |
+--------------------------+--------------------------------------------------+
| **hideView**             | Sets hide view.                                  |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **reverse**              | Sets reverse.                                    |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: AnimateAction properties

BackPageAction
--------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

Triggers back navigation of current page.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BackPageAction properties

ChooseFileAction
----------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

-   **Sub-types** : ``, ``

This is the abstract base class for actions dealing with client file system operations. It holds several parametrizations that are common to all file operations. Please, be aware that these FS actions heavily depend on the UI channel, i.e. you have different implementation classes (but registered under the same Spring name) for all supported UI technologies. For instance, {@code SaveFileAction} will have as many implementations as the number of supported UIs, each in a specific package :

{@code org.jspresso.framework.application.frontend.action.}**{@code [ui]}**{@code .file.SaveFileAction}

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **defaultFileName**      | Configures a default file name to be used        |
|                          | whenever a file needs to be chosen. Subclasses   |
| `String`                 | ma use their specific callback to override this  |
|                          | name with a more dynamically computed one.       |
+--------------------------+--------------------------------------------------+
| **fileFilter**           | Configures the file filters to be used whenever  |
|                          | the UI technology supports it in the file        |
| `Map​<​String​,List​>​`  | choosing dialog. Filter file types are a map of  |
|                          | descriptions keying file extension lists.        |
|                          |                                                  |
|                          | For instance, an entry in this map could be :    |
|                          |                                                  |
|                          | -   key : {@code "images"}                       |
|                          |                                                  |
|                          | -   value : {@code                               |
|                          |     [".png",".jpg",".gif",".bmp"]}               |
+--------------------------+--------------------------------------------------+

: ChooseFileAction properties

OpenFileAction
--------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action lets the user browse his local file system and choose a file to read some content from. What is done with the file content is determined by the configured {@code fileOpenCallback} instance.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **fileOpenCallback**     | Configures the file open callback instance that  |
|                          | will be used to deal with the file dialog        |
| ``                       | events. Two methods must be implemented :        |
|                          |                                                  |
|                          | -   {@code fileChosen(InputStream,               |
|                          |     IActionHandler, Map[String, Object])} that   |
|                          |     is called whenever a file has been chosen.   |
|                          |     The input stream that is passed as parameter |
|                          |     allows for reading from the chosen file. The |
|                          |     developer doesn't have to cope with closing  |
|                          |     the stream.                                  |
|                          |                                                  |
|                          | -   {@code cancel(IActionHandler, Map[String,    |
|                          |     Object])} that is called whenever the file   |
|                          |     selection is cancelled. It is perfectly      |
|                          |     legal not to do anything.                    |
+--------------------------+--------------------------------------------------+

: OpenFileAction properties

OpenFileAsBinaryPropertyAction
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action lets the user browse the local file system and choose a file to update the content of a binary property. Files are filtered based on the file filter defined in the binary property descriptor. This file action must be installed on a property view. A suitable (built-in) file open callback is installed upon action instantiation and thus, nothing has to be configured for the action to be immediately operational.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : OpenFileAsBinaryPropertyAction properties

SaveFileAction
--------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action lets the user browse his local file system and choose a file to write some content to. What is done with the file content is determined by the configured {@code fileSaveCallback} instance.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **contentType**          | Configures the content type to be used whenever  |
|                          | the UI technology used requires a download. The  |
| `String`                 | content type defaults to {@code                  |
|                          | "application/octet-stream"}.                     |
+--------------------------+--------------------------------------------------+
| **fileSaveCallback**     | Configures the file save callback instance that  |
|                          | will be used to deal with the file dialog        |
| ``                       | events. Three methods must be implemented :      |
|                          |                                                  |
|                          | -   {@code fileChosen(OutputStream,              |
|                          |     IActionHandler, Map[String, Object])} that   |
|                          |     is called whenever a file has been chosen.   |
|                          |     The output stream that is passed as          |
|                          |     parameter allows for writing to the chosen   |
|                          |     file. The developer doesn't have to cope     |
|                          |     with flushing nor closing the stream.        |
|                          |                                                  |
|                          | -   {@code getFileName(Map[String, Object])}     |
|                          |     that is called to give a chance top the      |
|                          |     callback to compute a file name dynamically  |
|                          |     depending on the action context. Whenever    |
|                          |     the callback returns a {@code null} or empty |
|                          |     file name, the default file name             |
|                          |     parametrized in the application is used.     |
|                          |                                                  |
|                          | -   {@code cancel(IActionHandler, Map[String,    |
|                          |     Object])} that is called whenever the file   |
|                          |     selection is cancelled. It is perfectly      |
|                          |     legal not to do anything.                    |
+--------------------------+--------------------------------------------------+

: SaveFileAction properties

SaveBinaryPropertyAsFileAction
------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action lets the user browse the local file system and choose a file to save the content of a binary property to. Files are filtered based on the file filter defined in the binary property descriptor. This file action must be installed on a property view. A suitable (built-in) file open callback is installed upon action instantiation and thus, nothing has to be configured for the action to be immediately operational.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : SaveBinaryPropertyAsFileAction properties

CleanModuleAndGoBackIfTransientAction
-------------------------------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

Check current selected module object. If it is transient, removes it from the current module and go back.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : CleanModuleAndGoBackIfTransientAction properties

DisplayJasperReportAction
-------------------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

This action will take a {@code JasperPrint} (a processed Jasper report instance), produce a PDF output and open a browser window (tab) to display it.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : DisplayJasperReportAction properties

EditCurrentPageAction
---------------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

Triggers editing of current page.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditCurrentPageAction properties

NearElementAction
-----------------

-   **Full name** : ``

-   **Super-type** : `AbstractRemoteAction`

Selects next / previous element.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **onFailureAction**      | Sets on failure action.                          |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **onSuccessAction**      | Sets on success action.                          |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **reverse**              | Sets reverse.                                    |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: NearElementAction properties

AbstractReportAction
--------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Abstract base class for Jasper report actions.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **reportFactory**        | Configures the report factory to use. The report |
|                          | factory is responsible for creating an {@code    |
| ``                       | IReport} (a concrete report instance) from a     |
|                          | report descriptor ({@code IReportDescriptor}).   |
+--------------------------+--------------------------------------------------+

: AbstractReportAction properties

ReportAction
------------

-   **Full name** : ``

-   **Super-type** : ``

This action allows the user to select a report to generate on the collection view where it has been installed. The collection backing the view can either be a collection of {@code IReport} or {@code IReportDescriptor}. In the latter situation, the corresponding {@code IReport} instances are created on the fly using the configured report factory.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ReportAction properties

StaticReportAction
------------------

-   **Full name** : ``

-   **Super-type** : ``

This action generates and displays a report that is statically configured through the {@code reportDescriptor} parameter. The report context is augmented with the identifier of the entity that is selected in the view were the action is installed, under the key {@code ENTITY\_ID}.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **reportDescriptor**     | Configures the report to execute.                |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: StaticReportAction properties

ActionParamToSelectedModelAction
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

A very simple frontend action that uses the puts the context action param as selected model.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ActionParamToSelectedModelAction properties

AddBeanAsSubModuleFrontAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action can be installed on any collection view and will take the selected elements in the underlying model collection and create a bean module out of them.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **childModuleProjectedVi | Sets the childModuleProjectedViewDescriptor.     |
| ewDescriptor**           |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **parentModuleName**     | Sets the parent module where to add components   |
|                          | to.                                              |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **parentWorkspaceName**  | Sets the WorkspaceName where to add components   |
|                          | to.                                              |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **referencePath**        | Allows to configure a property path to extract   |
|                          | the bean(s) to add from the selected models. If  |
| `String`                 | {@code null}, which is the default value, the    |
|                          | selected models are used themselves.             |
+--------------------------+--------------------------------------------------+

: AddBeanAsSubModuleFrontAction properties

AddCollectionToMasterAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action is designed to wrap a backend action that will create and add a (collection of) component(s) to the model collection of the view it's installed on. Its objective is to complete the action context with the descriptor of the component (or entity) to be added so that the backend action explicitly knows what to create. Moreover, the name, description and icon used for the graphical representation are all computed out of the configured {@code elementEntityDescriptor}.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **elementEntityDescripto | Configures the descriptor of the entities that   |
| r**                      | are to be added by the action to the underlying  |
|                          | model collection. Setting this property serves   |
| `​<​​>​`                 | multiple objectives :                            |
|                          |                                                  |
|                          | -   complete the application context with the    |
|                          |     {@code                                       |
|                          |     AddComponentCollectionToMasterAction.ELEMENT |
|                          | \_DESCRIPTOR}                                    |
|                          |     key so that the chained backend action knows |
|                          |     what type of entity to create.               |
|                          |                                                  |
|                          | -   customize the name, description and icon     |
|                          |     used to represent the action in the UI. All  |
|                          |     three are derived from the configured        |
|                          |     element entity descriptor.                   |
+--------------------------+--------------------------------------------------+

: AddCollectionToMasterAction properties

AddPageAction
-------------

-   **Full name** : ``

-   **Super-type** : ``

A special mobile pagination action that adds a page to the current results.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : AddPageAction properties

BinaryPropertyInfoAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action displays information about a binary property content. The displayed information mainly consists in the content size. The action must be installed on a property view and supports textual and binary properties.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : BinaryPropertyInfoAction properties

ChooseActionAction
------------------

-   **Full name** : ``

-   **Super-type** : ``

This action displays a list of frontend actions so that the user can choose and launch one of them. This action is meant to be chained with the generic {@code ChooseComponentAction} so that the action list is actually displayed.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **actions**              | Configures the list of actions to choose from.   |
|                          |                                                  |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+

: ChooseActionAction properties

ChooseComponentAction
---------------------

-   **Full name** : ``

-   **Super-type** : ``

This action takes an arbitrary model collection connector from the action context parameter and binds it to a newly created table view. This action is meant to be chained to the generic {@code ModalDialogAction} so that the table is actually popped-up in a dialog. Two actions ({@code okAction} and {@code cancelAction}) can be configured to react to the user decision.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cancelAction**         | Configures the action that will be triggered     |
|                          | when the user cancels the component choice.      |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **collectionViewDescript | Sets the collectionViewDescriptor.               |
| or**                     |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **componentDescriptor**  | Sets the componentDescriptor.                    |
|                          |                                                  |
| `​<​?​>​`                |                                                  |
+--------------------------+--------------------------------------------------+
| **okAction**             | Configures the action that will be triggered     |
|                          | when the user confirms the component choice. the |
| ``                       | chosen component will then be retrieved from the |
|                          | selected view item.                              |
+--------------------------+--------------------------------------------------+

: ChooseComponentAction properties

CloseDialogAction
-----------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This is a very generic action that closes (disposes) the currently opened dialog. The dialog is actually closed between the *wrapped* action and the *next* action if and only if the wrapped action succeeds.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : CloseDialogAction properties

EditSelectedComponentAction.DefaultOkAction
-------------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

Default OK action.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditSelectedComponentAction.DefaultOkAction properties

DisplayNextPinnedModuleAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action triggers a *"forward"* navigation in the recorded module history. The frontend controller automatically keeps track of the traversed modules so that a user can go back and forward his navigation history, much like for a web navigation.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : DisplayNextPinnedModuleAction properties

DisplayPreviousPinnedModuleAction
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action triggers a *"backward"* navigation in the recorded module history. The frontend controller automatically keeps track of the traversed modules so that a user can go back and forward his navigation history, much like for a web navigation.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : DisplayPreviousPinnedModuleAction properties

DisplayUrlAction
----------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This action opens a browser (or a browser tab) targeted at a URL. The actual URL is a composition of a static parametrized prefix ({@code baseUrl}) and a dynamic part taken from the action context parameter.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **baseUrl**              | Configures the static prefix that is prepended   |
|                          | (if not {@code null}) to the opened URL.         |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **target**               | Sets the target window.                          |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: DisplayUrlAction properties

DisplayStaticUrlAction
----------------------

-   **Full name** : ``

-   **Super-type** : ``

Like its parent, this action opens a URL in a browser (or a browser tab). But instead of taking the URL out of the context, it uses a statically parametrized URL, or rather a key ({@code urlKey}) used to translate the URL based on the logged-in user language. This is particularly useful for linking to static internationalized content, like an online manual. Be aware that once the URL is translated, it is still appended to the {@code baseUrl}.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **urlKey**               | Configures the translation key used to           |
|                          | internationalize the URL to open.                |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: DisplayStaticUrlAction properties

EditSelectionAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

This action is meant to trigger editing on the current collection view whenever a single element is selected.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditSelectionAction properties

ExecuteActionAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

This generic action takes another arbitrary action out of the context parameter and executes it.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ExecuteActionAction properties

ExitAction
----------

-   **Full name** : ``

-   **Super-type** : ``

This action exits the application. Before doing so, user activated application modules are traversed ton check that no pending changes need to be forwarded to the persistent store. Whenever the dirty checking is positive, then the user is notified and given a chance to cancel the exit.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **checkCurrentModuleDirt | Configures the action used to perform dirty      |
| yStateAction**           | checking on current module to update its dirty   |
|                          | state. It will be triggered just before a global |
| ``                       | iteration is performed on all the application    |
|                          | modules to be able to notify the user that       |
|                          | pending changes are not yet flushed to the       |
|                          | persistent store.                                |
+--------------------------+--------------------------------------------------+

: ExitAction properties

ListApplicationElementsAction
-----------------------------

-   **Full name** : ``

-   **Super-type** : ``

This is a special frontend action to list all application metamodel elements available along with their permIds. This is particularly useful to set-up the base of security referential setup.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ListApplicationElementsAction properties

LoginAction
-----------

-   **Full name** : ``

-   **Super-type** : ``

This is the frontend action to trigger the application login using the current credential in the frontend controller. If the action is configured with {@code anonymous = true}, then an anonymous login is attempted. If not, a normal login is performed.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **anonymous**            | Sets anonymous.                                  |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: LoginAction properties

LovAction
---------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This is a standard "List Of Values" action for reference property views. Although this action is used by default in view factories on reference fields, it can also be used in a more standard way, i.e. registered as a view action. In the latter, the {@code okAction} must be configured to perform a custom treatment once the entity is chosen from the LOV. Additionally you can statically configure the descriptor of the searched entities using the {@code entityDescriptor} parameter so that the LOV will act on this type of entities. The LOV action prepares a QBE view (filter / result list) along with 3 actions that can be further refined : {@code findAction}, {@code okAction} and {@code cancelAction}. It must the be linked to a {@code ModalDialogAction} so that the LOV actually pops up.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **autoquery**            | Whenever setting autoquery to {@code true}, the  |
|                          | LOV action will trigger the query as soon as it  |
| `boolean`                | gets executed and the initial query filter is    |
|                          | not empty (e.g. the user typed something in the  |
|                          | reference field). This brings autocomplete       |
|                          | feature to reference fields since, whenever the  |
|                          | initial filter limits to exactly 1 result, the   |
|                          | LOV dialog won't even open. Defaults to true.    |
+--------------------------+--------------------------------------------------+
| **cancelAction**         | Configures the action to be executed whenever    |
|                          | the user cancels the LOV dialog.                 |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **componentDescriptorReg | Sets component descriptor registry.              |
| istry**                  |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **createQueryComponentAc | Configures the action used to create the filter  |
| tion**                   | query component based on the type of entities    |
|                          | backing the LOV.                                 |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **defaultIconImageURL**  | Sets the defaultIconImageURL.                    |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **entityDescriptor**     | Configures explicitly the type of entities the   |
|                          | LOV relies on. This is automatically determined  |
| `​<​?​>​`                | when installed on a reference field but must be  |
|                          | set in any other case.                           |
+--------------------------+--------------------------------------------------+
| **findAction**           | Configures the action to be executed whenever    |
|                          | the user queries the persistent store, either    |
| ``                       | explicitly when using the action installed in    |
|                          | the LOV dialog or implicitly through the auto    |
|                          | query feature.                                   |
+--------------------------+--------------------------------------------------+
| **initializationMapping* | Whenever the LOV action is not used on a         |
| *                        | reference field, in which case the filter        |
|                          | initialization mapping is taken from the         |
| `Map​<​String​,Object​>​ | reference field descriptor (see {@code           |
| `                        | BasicReferencePropertyDescriptor}                |
|                          | documentation), this property allows to          |
|                          | initialize some of the LOV filter properties.    |
|                          | Initialization is computed dynamically by        |
|                          | transferring property values from the view model |
|                          | to the filter.                                   |
+--------------------------+--------------------------------------------------+
| **lovViewDescriptorFacto | Configures the factory to be used to create the  |
| ry**                     | QBE view used in the dialog.                     |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **okAction**             | Configures the action to be executed whenever    |
|                          | the user validates the LOV selection.            |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **pageSize**             | Sets page size.                                  |
|                          |                                                  |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+
| **pagingAction**         | Sets the pagingAction.                           |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **selectionMode**        | Allows to force the result view selection mode.  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **staticComponentStore** | Sets static component store.                     |
|                          |                                                  |
| `List​<​?​>​`            |                                                  |
+--------------------------+--------------------------------------------------+

: LovAction properties

MobileLovAction
---------------

-   **Full name** : ``

-   **Super-type** : ``

This is a standard "List Of Values" action for mobile environment.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : MobileLovAction properties

ModalDialogAction
-----------------

-   **Full name** : ``

-   **Super-type** : ``

This is a very generic action that takes its specifications out of the action context, creates and pops-up a modal dialog based on these specs. The action is meant to be chained after another frontend action that produce the dialog specs into the action context. Context entries that are used are :

-   {@code DIALOG\_VIEW} : the view to be used as the dialog content pane.

-   {@code DIALOG\_TITLE} : the title of the dialog.

-   {@code DIALOG\_ACTIONS} : the actions to be installed at the bottom of the dialog.

-   {@code DIALOG\_SIZE} : the dialog preferred size. Whenever the dialog size is {@code null}, the dialog size is determined from the preferred size of the content view.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ModalDialogAction properties

ModuleRestartAction
-------------------

-   **Full name** : ``

-   **Super-type** : ``

This action is used to restart a module. It cleans its children and executes its startup action.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ModuleRestartAction properties

ModuleSelectionAction
---------------------

-   **Full name** : ``

-   **Super-type** : ``

Displays a module, and the corresponding workspace if necessary based on their names. It can be used as startup action to select and display a module when the application launches.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **moduleName**           | Configures the name (untranslated) of the module |
|                          | to be displayed.                                 |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **workspaceName**        | Configures the name (untranslated) of the        |
|                          | workspace to be displayed.                       |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: ModuleSelectionAction properties

OkChooseComponentAction
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

This action augments the context by setting the action parameter to the selected component of the collection view (or null if none is selected).

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : OkChooseComponentAction properties

OkLovAction
-----------

-   **Full name** : ``

-   **Super-type** : ``

This action augments the context by setting the action parameter to the selected entity of the LOV result list (or null if none is selected).

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : OkLovAction properties

PageOffsetAction
----------------

-   **Full name** : ``

-   **Super-type** : ``

This action simply augment the context with a page offset integer ( {@code PAGE\_OFFSET}). It is meant to be linked to a find/query action that will further leverage this offset to navigate a pageable result set.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **pageOffset**           | Configures the page offset to be set to the      |
|                          | action context.                                  |
| `Integer`                |                                                  |
+--------------------------+--------------------------------------------------+

: PageOffsetAction properties

ParentModuleConnectorSelectionAction
------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action simply displays the parent of the currently selected module; i.e. it goes up one level in the module hierarchy of the current workspace.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ParentModuleConnectorSelectionAction properties

PrintAction
-----------

-   **Full name** : ``

-   **Super-type** : ``

This action allows the user to choose a report among a list and print it. The list of available reports is statically configured into the action.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **reportDescriptors**    | Configures the available report descriptors the  |
|                          | user will be allowed to choose.                  |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+
| **reportFactory**        | Configures the report factory to use. The report |
|                          | factory is responsible for creating an {@code    |
| ``                       | IReport} (a concrete report instance) from a     |
|                          | report descriptor ({@code IReportDescriptor}).   |
+--------------------------+--------------------------------------------------+

: PrintAction properties

SaveModuleObjectFrontAction
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action is used to save module and sub-modules objects.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **dirtyTrackingEnabled** | Set dirty tracking enabled.                      |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: SaveModuleObjectFrontAction properties

SelectedModelToActionParamAction
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

A very simple frontend action that puts the selected model(s) as context action param.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : SelectedModelToActionParamAction properties

SetConnectorValueAction
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

This action retrieves the action parameter from the action context and assigns it as value to the targeted connector. The connector to target is itself retrieved from the action context using a parametrized key.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **connectorActionContext | Configures the key to look for the target        |
| Key**                    | connector in the context, e.g. VIEW\_CONNECTOR.  |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: SetConnectorValueAction properties

TransferToClipboardAction
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

An action used to transfer textual representation(s) of selected models to the system clipboard.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **clipboardTransferHandl | Sets the clipboardTransferHandler.               |
| er**                     |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: TransferToClipboardAction properties

EditSelectedComponentAction.UowRollbackerAction
-----------------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

A wrapper action that roll backs the current UOW before delegating to its delegate.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : EditSelectedComponentAction.UowRollbackerAction properties

WizardAction
------------

-   **Full name** : ``

-   **Super-type** : ``

This action implements a "wizard". It can be configured from the simplest use-case (as for a value entering) to the most complex, multi-step wizard. Here are a usage directions :

1.  The generic wizard front-end action is registered in the Spring context under the name wizardAction. So you will typically inherit the bean definition using the parent="wizardAction" when declaring yours.

2.  The goal of the wizard action is to work on a map - the wizard model - (potentially containing other maps) that represents a hierarchical data structure that can be used seamlessly as model for any Jspresso view. In your case, the map will only contain 1 key-value pair (the property you want your user to enter). When finishing the wizard, the action context will contain the map with all the key-value pairs the user has created/modified through the wizard steps. It will be accessible in the action context under the ActionContextConstants.ACTION\_PARAM key and will typically serve as input for the finish chained action.

3.  The wizard action is configured using chained org.jspresso.framework.application .frontend.action.wizard.IWizardStepDescriptor. A concrete, directly usable, implementation of this interface is org.jspresso.framework.application.frontend .action.wizard.StaticWizardStepDescriptor. Each wizard step is highly configurable (name, description, icon, ...) but its most important properties are :

    1.  {@code viewDescriptor} : the Jspresso view descriptor to be shown in the wizard GUI when the user enters this step. It can be arbitrarily complex (even with master-detail like views, inner actions, constraints, security enforcements, ...). Of course, the view descriptor needs a model descriptor. So you must describe the wizard model as you would do for persistent entities or components (so that step views can configure themselves). You will typically use a BasicComponentDescriptor without name so that it is automatically excluded from code generation. Note that your actual model object will be a map (and not Jspresso generated java bean) but Jspresso connectors are "smart" enough to detect the situation and work with the hierarchy of maps as if it was a hierarchy of java beans.

    2.  optional {@code onEnterAction} and {@code onLeaveAction} : actions that will respectively be executed when entering and when exiting the wizard step.

    3.  optional {@code nextLabelKey} and {@code previousLabelKey} : i18n keys for next and previous buttons if you want to change the default ones.

    4.  optional {@code nextStepDescriptor} : the next wizard step. If null, the wizard GUI will enable the finish action.

4.  The first wizard step is registered on the wizard action using the {@code firstWizardStep} property.

5.  When the user leaves the last wizard step (clicking the finish action button), the finish action is triggered. The finish action can be registered on the wizard action using the {@code finishAction} property. This is typically the place where you explore the wizard map model - {@code ACTION\_PARAM} - to get back all the data the user has worked on. Note that the finish button is entirely configured from the finish action (label and icon).

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cancelAction**         | Configures the action that will be executed      |
|                          | whenever the user cancels the wizard.            |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **finishAction**         | Configures the action that will be executed      |
|                          | whenever the user validates the wizard.          |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **firstWizardStep**      | Configures the first wizard step to display.     |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **height**               | Configures explicitly the height of the wizard   |
|                          | dialog. It prevents the dialog from resizing     |
| `Integer`                | dynamically depending on the displayed wizard    |
|                          | step.                                            |
+--------------------------+--------------------------------------------------+
| **width**                | Configures explicitly the width of the wizard    |
|                          | dialog. It prevents the dialog from resizing     |
| `Integer`                | dynamically depending on the displayed wizard    |
|                          | step.                                            |
+--------------------------+--------------------------------------------------+

: WizardAction properties

WorkspaceSelectionAction
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This action displays a workspace using its (untranslated) name.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **workspaceName**        | Configures the name of the workspace to display. |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+

: WorkspaceSelectionAction properties


