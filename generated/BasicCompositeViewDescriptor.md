Reference for BasicCompositeViewDescriptor hierarchy
====================================================

BasicCompositeViewDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``

This is the abstract base class for all composite views. A composite
view is a view that arranges a collection of nested views in a
predefined layout. Nested views can also be composite views which makes
it possible to build complex UIs out of simple combinations. Composite
views are also the foundation of master-detail views by allowing a
nested view to take its model out of the selection of the previous one.
This behaviour can be activated using the {@code cascadingModels}
property that "cascades" the view models based on the selected elements.
Whenever this behaviour is not activated, all nested views share the
same model than their parent composite unless specified otherwise.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cascadingModels**      | Enables the model "cascading" behaviour. This    |
|                          | allows for instance to link 2 nested tables      |
| `boolean`                | where the 2nd table model is the selected row of |
|                          | the first table (or {@code null} if selection is |
|                          | empty). Using {@code cascadingModel=true} is     |
|                          | only necessary when tracking view selection on   |
|                          | the master nested view. You don't need it if,    |
|                          | for instance, the master nested view is a single |
|                          | model view like a component view. In the latter  |
|                          | case, you can bind a table detail view just by   |
|                          | adding it to the same composite without having   |
|                          | to set {@code cascadingModel=true}.              |
|                          |                                                  |
|                          | Default value is {@code false}, i.e. al nested   |
|                          | views share the same model than the outer        |
|                          | composite unless explicitly specified            |
|                          | differently.                                     |
+--------------------------+--------------------------------------------------+

: BasicCompositeViewDescriptor properties

AbstractMobilePageViewDescriptor
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

Abstract base class for mobile page view descriptors.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **backAction**           | Sets back action.                                |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **enterAction**          | Sets enter action.                               |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **forClientTypes**       | Sets for client types.                           |
|                          |                                                  |
| `List​<​String​>​`       |                                                  |
+--------------------------+--------------------------------------------------+
| **i18nDescription**      | Sets i 18 n description.                         |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **i18nName**             | Sets i 18 n name.                                |
|                          |                                                  |
| `String`                 |                                                  |
+--------------------------+--------------------------------------------------+
| **mainAction**           | Sets main action.                                |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **pageEndAction**        | Sets page end action.                            |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **position**             | Sets position.                                   |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **swipeLeftAction**      | Sets swipe left action.                          |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **swipeRightAction**     | Sets swipe right action.                         |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: AbstractMobilePageViewDescriptor properties

MobileCardPageViewDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

A card view descriptor that aggregates other pages as card.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cascadingModels**      | Sets cascading models. This operation is not     |
|                          | supported on mobile pages.                       |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **pagesCardViewDescripto | Sets pages.                                      |
| r**                      |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: MobileCardPageViewDescriptor properties

MobileCompositePageViewDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

A composite view descriptor that aggregates view sections on a single
page.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cascadingModels**      | Sets cascading models. This operation is not     |
|                          | supported on mobile pages.                       |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **editorPage**           | Sets editing page.                               |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **inlineEditing**        | Sets inline editing.                             |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **pageSectionDescriptors | Sets page sections.                              |
| **                       |                                                  |
|                          |                                                  |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+

: MobileCompositePageViewDescriptor properties

MobileNavPageViewDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Navigation page view descriptors that are able to navigate to another
page based on a selection component.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cascadingModels**      | Sets cascading models. This operation is not     |
|                          | supported on mobile lists.                       |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **headerSectionDescripto | Sets header section descriptors.                 |
| rs**                     |                                                  |
|                          |                                                  |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+
| **nextPageViewDescriptor | Sets next page.                                  |
| **                       |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **selectionViewDescripto | Sets selection view. Supports only tree or list. |
| r**                      |                                                  |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: MobileNavPageViewDescriptor properties

BasicBorderViewDescriptor
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

A border view is a composite view that arranges its children to the
*north*, *west*, *east*, *south* and *center*. Depending its position in
the container, the resizing rules apply differently :

-   *north* and *south* are resized horizontally and kept to their
    preferred size vertically

-   *west* and *east* are resized vertically and kept to their preferred
    size horizontally

-   *center* is resized both horizontally and vertically

Default cascading order for master-detail is :

north -\> west -\> center -\> east -\> south

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **centerViewDescriptor** | Sets the child view to layout in the *center*    |
|                          | zone. The child view will be resized both        |
| ``                       | horizontally and vertically.                     |
+--------------------------+--------------------------------------------------+
| **eastViewDescriptor**   | Sets the child view to layout in the *east*      |
|                          | zone. The child view will be resized vertically. |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **northViewDescriptor**  | Sets the child view to layout in the *north*     |
|                          | zone. The child view will be resized             |
| ``                       | horizontally.                                    |
+--------------------------+--------------------------------------------------+
| **southViewDescriptor**  | Sets the child view to layout in the *south*     |
|                          | zone. The child view will be resized             |
| ``                       | horizontally.                                    |
+--------------------------+--------------------------------------------------+
| **westViewDescriptor**   | Sets the child view to layout in the *west*      |
|                          | zone. The child view will be resized vertically. |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: BasicBorderViewDescriptor properties

MobileBorderViewDescriptor
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

A composite view descriptor that aggregates mobile views.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **backAction**           | Sets back action.                                |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **eastViewDescriptor**   | Not supported in mobile environment.             |
|                          |                                                  |
| ``                       | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+
| **enterAction**          | Sets enter action.                               |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **forClientTypes**       | Sets for client types.                           |
|                          |                                                  |
| `List​<​String​>​`       |                                                  |
+--------------------------+--------------------------------------------------+
| **mainAction**           | Sets main action.                                |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **pageEndAction**        | Sets page end action.                            |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **position**             | Sets position.                                   |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **swipeLeftAction**      | Sets swipe left action.                          |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **swipeRightAction**     | Sets swipe right action.                         |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **westViewDescriptor**   | Not supported in mobile environment.             |
|                          |                                                  |
| ``                       | {@inheritDoc}                                    |
+--------------------------+--------------------------------------------------+

: MobileBorderViewDescriptor properties

BasicConstrainedGridViewDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This composite view arranges its children in a grid where cell behaviour
and dimensions are configured using cell constraints. A cell constraint
is a simple data structure holding the following properties :

-   {@code row}: the row to which the cell belongs

-   {@code column}: the column to which the cell belongs

-   {@code width}: the number of columns the cell spans horizontally
    (default value is 1)

-   {@code height}: the number of rows the cell spans vertically
    (default value is 1)

-   {@code heightResizable}: whether the cell should be resized to take
    all the available space vertically

-   {@code widthResizable}: whether the cell should be resized to take
    all the available space horizontally

Default cascading order follows the order of nested view registrations
in the container.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cells**                | Registers the nested children views along with   |
|                          | their cell constraints. They are set as a {@code |
| `Map​<​​,​>​`            | Map} that is :                                   |
|                          |                                                  |
|                          | -   keyed by the children views                  |
|                          |                                                  |
|                          | -   valued by the cell constraints to apply to   |
|                          |     each nested view                             |
+--------------------------+--------------------------------------------------+

: BasicConstrainedGridViewDescriptor properties

BasicEvenGridViewDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This composite view arranges its children in a grid where cells are
distributed evenly. All cells are resized horizontally and vertically to
fill its available space.

The number of cells in a row / column is determined by the combination
of the {@code drivingDimension} and {@code drivingDimensionCellCount}
properties. the cells are spread along the driving dimension (row or
column) until the maximum number of cells in the dimension has been
reached. Then a new row (or column) is added. The process repeats until
all the cells have been added.

This container does not allow for individual cell configuration like
row/column spanning. Whenever cell disposition has to be customized more
finely, a {@code BasicConstrainedGridViewDescriptor} should be used
instead.

Default cascading order follows the order of nested view registrations
in the container.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **cells**                | Registers the nested views to display as grid    |
|                          | cells.                                           |
| `List​<​​>​`             |                                                  |
+--------------------------+--------------------------------------------------+
| **drivingDimension**     | Configures the driving dimension of the grid.    |
|                          | This is either a value of the {@code EAxis} enum |
| ``                       | or its equivalent string representation :        |
|                          |                                                  |
|                          | -   {@code ROW} for distributing cells along     |
|                          |     rows then columns                            |
|                          |                                                  |
|                          | -   {@code COLUMN} for distributing cells along  |
|                          |     columns then rows                            |
|                          |                                                  |
|                          | Default value is {@code EAxis.ROW}, i.e.         |
|                          | distribute cells along rows then columns.        |
+--------------------------+--------------------------------------------------+
| **drivingDimensionCellCo | This property configures the maximum number of   |
| unt**                    | cells in the driving dimension (row or column).  |
|                          | Nested views are distributed along the driving   |
| `int`                    | axis until this maximum number has been reached. |
|                          | A new row or column is then created to host the  |
|                          | remaining cells.                                 |
+--------------------------+--------------------------------------------------+

: BasicEvenGridViewDescriptor properties

BasicSplitViewDescriptor
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This composite view arranges its children in a container split either
horizontally or vertically. An horizontal split disposes its 2 children
*left* and *right* whereas a vertical split disposes its 2 children
*top* and *bottom*. The dividing bar can typically be moved by the user
to distribute the available space.

Default cascading order for master-detail is :

left -\> right or top -\> bottom depending on the split orientation.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **leftTopViewDescriptor* | Sets the *left* (horizontal split) of *top*      |
| *                        | (vertical split) nested view.                    |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+
| **orientation**          | Configures the split orientation of the          |
|                          | container. This is either a value of the {@code  |
| ``                       | EOrientation} enum or its equivalent string      |
|                          | representation :                                 |
|                          |                                                  |
|                          | -   {@code VERTICAL} for splitting the container |
|                          |     vertically and arranging the views top and   |
|                          |     bottom                                       |
|                          |                                                  |
|                          | -   {@code HORIZONTAL} for splitting the         |
|                          |     container horizontally and arranging the     |
|                          |     views left and right                         |
|                          |                                                  |
|                          | Default value is {@code EOrientation.VERTICAL},  |
|                          | i.e. the container is split vertically.          |
+--------------------------+--------------------------------------------------+
| **rightBottomViewDescrip | Sets the *right* (horizontal split) of *bottom*  |
| tor**                    | (vertical split) nested view.                    |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: BasicSplitViewDescriptor properties

BasicTabViewDescriptor
----------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This composite view arranges its children in tabs. Each tab potentially
displays a label (that is translated based on the name of the view in
the tab), an icon (based on the icon of the view in the tab) and a
toolTip (based on the description of the view in the tab).

Default cascading order follows the order of nested view registrations
in the container.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **lazy**                 | When set to true, this parameter configures the  |
|                          | tabs to be lazy bound (binding occurs only for   |
| `boolean`                | the selected tab). This feature is only          |
|                          | supported for tab views with {@code              |
|                          | cascadingModel} set to false. default value is   |
|                          | {@code true}.                                    |
+--------------------------+--------------------------------------------------+
| **renderingOptions**     | Indicates how the tabs should be rendered. This  |
|                          | is either a value of the {@code                  |
| ``                       | ERenderingOptions} enum or its equivalent string |
|                          | representation :                                 |
|                          |                                                  |
|                          | -   {@code LABEL\_ICON} for label and icon       |
|                          |                                                  |
|                          | -   {@code LABEL} for label only                 |
|                          |                                                  |
|                          | -   {@code ICON} for icon only.                  |
|                          |                                                  |
|                          | Default value is {@code                          |
|                          | ERenderingOptions.LABEL\_ICON}, i.e. label and   |
|                          | icon.                                            |
+--------------------------+--------------------------------------------------+
| **tabs**                 | Registers the list of views to be displayed as   |
|                          | tabs. The tabs order follows the children views  |
| `List​<​​>​`             | order of this list.                              |
+--------------------------+--------------------------------------------------+

: BasicTabViewDescriptor properties

MobileTabViewDescriptor
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

A composite view descriptor that aggregates mobile views.

+--------------------------+--------------------------------------------------+
| Property                 | Description                                      |
+==========================+==================================================+
| **carouselMode**         | Sets carousel mode.                              |
|                          |                                                  |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **cascadingModels**      | Not supported in mobile environment.             |
|                          | {@inheritDoc}                                    |
| `boolean`                |                                                  |
+--------------------------+--------------------------------------------------+
| **forClientTypes**       | Sets for client types.                           |
|                          |                                                  |
| `List​<​String​>​`       |                                                  |
+--------------------------+--------------------------------------------------+
| **position**             | Sets position.                                   |
|                          |                                                  |
| ``                       |                                                  |
+--------------------------+--------------------------------------------------+

: MobileTabViewDescriptor properties


