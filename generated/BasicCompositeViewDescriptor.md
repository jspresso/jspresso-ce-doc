Reference for BasicCompositeViewDescriptor hierarchy
====================================================

BasicCompositeViewDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``, ``, ``, ``

This is the abstract base class for all composite views. A composite view is a view that arranges a collection of nested views in a predefined layout. Nested views can also be composite views which makes it possible to build complex UIs out of simple combinations. Composite views are also the foundation of master-detail views by allowing a nested view to take its model out of the selection of the previous one. This behaviour can be activated using the {@code cascadingModels} property that "cascades" the view models based on the selected elements. Whenever this behaviour is not activated, all nested views share the same model than their parent composite unless specified otherwise.

<table>
<caption>BasicCompositeViewDescriptor properties</caption>
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
<td align="left"><p><strong>cascadingModels</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Enables the model &quot;cascading&quot; behaviour. This allows for instance to link 2 nested tables where the 2nd table model is the selected row of the first table (or {@code null} if selection is empty). Using {@code cascadingModel=true} is only necessary when tracking view selection on the master nested view. You don't need it if, for instance, the master nested view is a single model view like a component view. In the latter case, you can bind a table detail view just by adding it to the same composite without having to set {@code cascadingModel=true}.</p>
<p>Default value is {@code false}, i.e. al nested views share the same model than the outer composite unless explicitly specified differently.</p></td>
</tr>
</tbody>
</table>

AbstractMobilePageViewDescriptor
--------------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``, ``, ``

Abstract base class for mobile page view descriptors.

<table>
<caption>AbstractMobilePageViewDescriptor properties</caption>
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
<td align="left"><p><strong>backAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets back action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>enterAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets enter action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>forClientTypes</strong></p>
<p><code>List​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Sets for client types.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>i18nDescription</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets i 18 n description.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>i18nName</strong></p>
<p><code>String</code></p></td>
<td align="left"><p>Sets i 18 n name.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>mainAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets main action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>pageEndAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets page end action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>position</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets position.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>swipeLeftAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets swipe left action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>swipeRightAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets swipe right action.</p></td>
</tr>
</tbody>
</table>

MobileCardPageViewDescriptor
----------------------------

-   **Full name** : ``

-   **Super-type** : ``

A card view descriptor that aggregates other pages as card.

<table>
<caption>MobileCardPageViewDescriptor properties</caption>
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
<td align="left"><p><strong>cascadingModels</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets cascading models. This operation is not supported on mobile pages.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pagesCardViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets pages.</p></td>
</tr>
</tbody>
</table>

MobileCompositePageViewDescriptor
---------------------------------

-   **Full name** : ``

-   **Super-type** : ``

A composite view descriptor that aggregates view sections on a single page.

<table>
<caption>MobileCompositePageViewDescriptor properties</caption>
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
<td align="left"><p><strong>cascadingModels</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets cascading models. This operation is not supported on mobile pages.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>editorPage</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets editing page.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>inlineEditing</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets inline editing.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageSectionDescriptors</strong></p>
<p><code>List​&lt;​​&gt;​</code></p></td>
<td align="left"><p>Sets page sections.</p></td>
</tr>
</tbody>
</table>

MobileNavPageViewDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

Navigation page view descriptors that are able to navigate to another page based on a selection component.

<table>
<caption>MobileNavPageViewDescriptor properties</caption>
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
<td align="left"><p><strong>cascadingModels</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets cascading models. This operation is not supported on mobile lists.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>headerSectionDescriptors</strong></p>
<p><code>List​&lt;​​&gt;​</code></p></td>
<td align="left"><p>Sets header section descriptors.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>nextPageViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets next page.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>selectionViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets selection view. Supports only tree or list.</p></td>
</tr>
</tbody>
</table>

BasicBorderViewDescriptor
-------------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

A border view is a composite view that arranges its children to the *north*, *west*, *east*, *south* and *center*. Depending its position in the container, the resizing rules apply differently :

-   *north* and *south* are resized horizontally and kept to their preferred size vertically

-   *west* and *east* are resized vertically and kept to their preferred size horizontally

-   *center* is resized both horizontally and vertically

Default cascading order for master-detail is :

north -\> west -\> center -\> east -\> south

<table>
<caption>BasicBorderViewDescriptor properties</caption>
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
<td align="left"><p><strong>centerViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the child view to layout in the <em>center</em> zone. The child view will be resized both horizontally and vertically.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>eastViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the child view to layout in the <em>east</em> zone. The child view will be resized vertically.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>northViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the child view to layout in the <em>north</em> zone. The child view will be resized horizontally.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>southViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the child view to layout in the <em>south</em> zone. The child view will be resized horizontally.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>westViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the child view to layout in the <em>west</em> zone. The child view will be resized vertically.</p></td>
</tr>
</tbody>
</table>

MobileBorderViewDescriptor
--------------------------

-   **Full name** : ``

-   **Super-type** : ``

A composite view descriptor that aggregates mobile views.

<table>
<caption>MobileBorderViewDescriptor properties</caption>
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
<td align="left"><p><strong>backAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets back action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>eastViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Not supported in mobile environment.</p>
<p>{@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>enterAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets enter action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>forClientTypes</strong></p>
<p><code>List​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Sets for client types.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>mainAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets main action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageEndAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets page end action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>position</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets position.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>swipeLeftAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets swipe left action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>swipeRightAction</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets swipe right action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>westViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Not supported in mobile environment.</p>
<p>{@inheritDoc}</p></td>
</tr>
</tbody>
</table>

BasicConstrainedGridViewDescriptor
----------------------------------

-   **Full name** : ``

-   **Super-type** : ``

This composite view arranges its children in a grid where cell behaviour and dimensions are configured using cell constraints. A cell constraint is a simple data structure holding the following properties :

-   {@code row}: the row to which the cell belongs

-   {@code column}: the column to which the cell belongs

-   {@code width}: the number of columns the cell spans horizontally (default value is 1)

-   {@code height}: the number of rows the cell spans vertically (default value is 1)

-   {@code heightResizable}: whether the cell should be resized to take all the available space vertically

-   {@code widthResizable}: whether the cell should be resized to take all the available space horizontally

Default cascading order follows the order of nested view registrations in the container.

<table>
<caption>BasicConstrainedGridViewDescriptor properties</caption>
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
<td align="left"><p><strong>cells</strong></p>
<p><code>Map​&lt;​​,​&gt;​</code></p></td>
<td align="left"><p>Registers the nested children views along with their cell constraints. They are set as a {@code Map} that is :</p>
<ul>
<li><p>keyed by the children views</p></li>
<li><p>valued by the cell constraints to apply to each nested view</p></li>
</ul></td>
</tr>
</tbody>
</table>

BasicEvenGridViewDescriptor
---------------------------

-   **Full name** : ``

-   **Super-type** : ``

This composite view arranges its children in a grid where cells are distributed evenly. All cells are resized horizontally and vertically to fill its available space.

The number of cells in a row / column is determined by the combination of the {@code drivingDimension} and {@code drivingDimensionCellCount} properties. the cells are spread along the driving dimension (row or column) until the maximum number of cells in the dimension has been reached. Then a new row (or column) is added. The process repeats until all the cells have been added.

This container does not allow for individual cell configuration like row/column spanning. Whenever cell disposition has to be customized more finely, a {@code BasicConstrainedGridViewDescriptor} should be used instead.

Default cascading order follows the order of nested view registrations in the container.

<table>
<caption>BasicEvenGridViewDescriptor properties</caption>
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
<td align="left"><p><strong>cells</strong></p>
<p><code>List​&lt;​​&gt;​</code></p></td>
<td align="left"><p>Registers the nested views to display as grid cells.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>drivingDimension</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the driving dimension of the grid. This is either a value of the {@code EAxis} enum or its equivalent string representation :</p>
<ul>
<li><p>{@code ROW} for distributing cells along rows then columns</p></li>
<li><p>{@code COLUMN} for distributing cells along columns then rows</p></li>
</ul>
<p>Default value is {@code EAxis.ROW}, i.e. distribute cells along rows then columns.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>drivingDimensionCellCount</strong></p>
<p><code>int</code></p></td>
<td align="left"><p>This property configures the maximum number of cells in the driving dimension (row or column). Nested views are distributed along the driving axis until this maximum number has been reached. A new row or column is then created to host the remaining cells.</p></td>
</tr>
</tbody>
</table>

BasicSplitViewDescriptor
------------------------

-   **Full name** : ``

-   **Super-type** : ``

This composite view arranges its children in a container split either horizontally or vertically. An horizontal split disposes its 2 children *left* and *right* whereas a vertical split disposes its 2 children *top* and *bottom*. The dividing bar can typically be moved by the user to distribute the available space.

Default cascading order for master-detail is :

left -\> right or top -\> bottom depending on the split orientation.

<table>
<caption>BasicSplitViewDescriptor properties</caption>
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
<td align="left"><p><strong>leftTopViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the <em>left</em> (horizontal split) of <em>top</em> (vertical split) nested view.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orientation</strong></p>
<p><code></code></p></td>
<td align="left"><p>Configures the split orientation of the container. This is either a value of the {@code EOrientation} enum or its equivalent string representation :</p>
<ul>
<li><p>{@code VERTICAL} for splitting the container vertically and arranging the views top and bottom</p></li>
<li><p>{@code HORIZONTAL} for splitting the container horizontally and arranging the views left and right</p></li>
</ul>
<p>Default value is {@code EOrientation.VERTICAL}, i.e. the container is split vertically.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rightBottomViewDescriptor</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets the <em>right</em> (horizontal split) of <em>bottom</em> (vertical split) nested view.</p></td>
</tr>
</tbody>
</table>

BasicTabViewDescriptor
----------------------

-   **Full name** : ``

-   **Super-type** : ``

-   **Sub-types** : ``

This composite view arranges its children in tabs. Each tab potentially displays a label (that is translated based on the name of the view in the tab), an icon (based on the icon of the view in the tab) and a toolTip (based on the description of the view in the tab).

Default cascading order follows the order of nested view registrations in the container.

<table>
<caption>BasicTabViewDescriptor properties</caption>
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
<td align="left"><p><strong>lazy</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>When set to true, this parameter configures the tabs to be lazy bound (binding occurs only for the selected tab). This feature is only supported for tab views with {@code cascadingModel} set to false. default value is {@code true}.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderingOptions</strong></p>
<p><code></code></p></td>
<td align="left"><p>Indicates how the tabs should be rendered. This is either a value of the {@code ERenderingOptions} enum or its equivalent string representation :</p>
<ul>
<li><p>{@code LABEL_ICON} for label and icon</p></li>
<li><p>{@code LABEL} for label only</p></li>
<li><p>{@code ICON} for icon only.</p></li>
</ul>
<p>Default value is {@code ERenderingOptions.LABEL_ICON}, i.e. label and icon.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>tabs</strong></p>
<p><code>List​&lt;​​&gt;​</code></p></td>
<td align="left"><p>Registers the list of views to be displayed as tabs. The tabs order follows the children views order of this list.</p></td>
</tr>
</tbody>
</table>

MobileTabViewDescriptor
-----------------------

-   **Full name** : ``

-   **Super-type** : ``

A composite view descriptor that aggregates mobile views.

<table>
<caption>MobileTabViewDescriptor properties</caption>
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
<td align="left"><p><strong>carouselMode</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Sets carousel mode.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>cascadingModels</strong></p>
<p><code>boolean</code></p></td>
<td align="left"><p>Not supported in mobile environment. {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>forClientTypes</strong></p>
<p><code>List​&lt;​String​&gt;​</code></p></td>
<td align="left"><p>Sets for client types.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>position</strong></p>
<p><code></code></p></td>
<td align="left"><p>Sets position.</p></td>
</tr>
</tbody>
</table>


