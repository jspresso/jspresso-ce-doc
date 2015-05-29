Reference for AbstractActionContextAware hierarchy
==================================================

AbstractActionContextAware
--------------------------

-   **Full name** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``

Abstract class for all objects that need to manipulate an action
context. It contains helper methods that takes the developer away from
the standard context internal knowledge. Action developers can (should)
use these helper methods (for reference manual readers, give an eye to
the linked javadoc).

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : AbstractActionContextAware properties

AbstractAction
--------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

This is the base class for all application actions. It establishes the
foundation of the Jspresso action framework, i.e. each action can link :

-   a *wrapped* action that will execute a return back to the caller
    action

-   a *next* action that will execute after the caller

The action chaining described above supports the separation of concerns
that consists in splitting the actions in two distinct categories :

-   *frontend* actions that deal with user interaction. They are
    typically used to bootstrap a service request from th UI, update the
    UI state, trigger the display of information, errors, ...

-   *backend* actions that are faceless, UI agnostic and deal with the
    manipulation of the domain model, backend services, ...

Conceptually, a frontend action can call a backend action or another
frontend action but a backend action should stay on the backend, thus
should only reference another backend action. In other words, the
backend layer should never explicitly reference the frontend layer.

That's the main reason for having a *wrapped* and a *next* action in the
action chain. The *wrapped* action is perfectly suited to call the
backend layer (a backend action) and give the flow back to the frontend
layer. The *next* action is perfectly suited to chain 2 actions of the
same type (i.e. 2 frontend actions or 2 backend actions). Using this
scheme helps keeping layer dependencies clear. Of course, this dual
chaining mechanism is completely recursive thus allowing to compose
small (generic) actions into larger composite ones and promoting
reusability.

Actions execute on a context (an arbitrary map of objects keyed by
"well-known" character strings) that is initialized by the controller
when the action is triggered. The context passes along the action chain
and is thus the perfect medium for actions to loosely communicate
between each other. There are some framework standard elements placed in
the action context that depend on the application state, but nothing
prevents action developers to synchronize on arbitrary custom context
elements that would be produced/consumed to/from the context.

Regarding framework-standard context elements, an action developer can
(should) leverage the utility methods declared in the {@code
AbstractActionContextAware} super class instead of relying on the
element keys in the map. Take a look to the {@code
AbstractActionContextAware} documentation to get your hands on action
context exploration.

Last but not least, you should be aware that actions should be coded
with thread-safety in mind. Actual action instances are generally
singleton-like (unless explicitly stated which is extremely rare) and
thus, might be used by multiple sessions (threads) at once. You should
**never** use action class attributes for argument passing along the
action chain, but use the thread-owned action execution context instead.
The action context is a data structure that is local to an action chain
execution thus not shared across threads (users). It is the perfect
place for exchanging data between actions. Of course, different
instances of the same action can be used and configured differently
through their class attributes (refer to it as static configuration),
but this is all for using in different places in the application.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **grantedRoles**         | Assigns the roles that are authorized to execute |
|                          | this action. It supports "**!**" prefix to       |
| `Collection​<​String​>​` | negate the role(s). This will directly influence |
|                          | the UI behaviour since unauthorized actions      |
|                          | won't be displayed. Setting the collection of    |
|                          | granted roles to {@code null} (default value)    |
|                          | disables role based authorization on this        |
|                          | action. Note that this authorization enforcement |
|                          | does not prevent programmatic access that is of  |
|                          | the developer responsibility.                    |
+--------------------------+--------------------------------------------------+
| **nextAction**           | Registers an action to be executed after this    |
|                          | action and after the *wrapped* one. This is      |
| ``                       | perfectly suited to chain an action of the same  |
|                          | type (frontend or backend) as this one.          |
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
| **wrappedAction**        | Registers an action to be executed after this    |
|                          | action but before the *next* one. This is        |
| ``                       | perfectly suited to chain a backend action from  |
|                          | a frontend action since the control flow will    |
|                          | return back to the calling layer (the frontend). |
+--------------------------+--------------------------------------------------+

: AbstractAction properties

AbstractLovResultViewDescriptorFactory
--------------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

The base abstract implementation for lov result view factories.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **queryComponentDescript | Sets the queryComponentDescriptorFactory.        |
| orFactory**              |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractLovResultViewDescriptorFactory properties

AbstractLovViewDescriptorFactory
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

The base abstract implementation for lov view factories.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
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
| **resultViewDescriptorFa | Sets the resultViewDescriptorFactory.            |
| ctory**                  |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractLovViewDescriptorFactory properties

ConnectorValueGetterCallback
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

Default handler implementation to deal with getting binary properties
storing them in files.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : ConnectorValueGetterCallback properties

DefaultCriteriaFactory
----------------------

-   **Full name** : ``

-   **Super-type** : ``

Default implementation of a criteria factory.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **triStateBooleanSupport | Sets the triStateBooleanSupported.               |
| ed**                     |                                                  |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+

: DefaultCriteriaFactory properties

FileToByteArrayCallback
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``

Default handler implementation to fully read the file input stream into
a byte array and setting it in the context.

  -------------------------------------------------------------------------
  Property                 Description
  ------------------------ ------------------------------------------------
  This class does not have
  any specific property.
  -------------------------------------------------------------------------

  : FileToByteArrayCallback properties


