## BasicCompositeViewDescriptor

#### <a name="org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor"></a>BasicCompositeViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicCompositeViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`AbstractMobilePageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.AbstractMobilePageViewDescriptor), [`BasicBorderViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicBorderViewDescriptor), [`BasicConstrainedGridViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicConstrainedGridViewDescriptor), [`BasicEvenGridViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicEvenGridViewDescriptor), [`BasicSplitViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicSplitViewDescriptor), [`BasicTabViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicTabViewDescriptor)



This is the abstract base class for all composite views. A composite view is
 a view that arranges a collection of nested views in a predefined layout.
 Nested views can also be composite views which makes it possible to build
 complex UIs out of simple combinations. Composite views are also the
 foundation of master-detail views by allowing a nested view to take its model
 out of the selection of the previous one. This behaviour can be activated
 using the <code>cascadingModels</code> property that &quot;cascades&quot; the
 view models based on the selected elements. Whenever this behaviour is not
 activated, all nested views share the same model than their parent composite
 unless specified otherwise.



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
<td align="left"><p><strong>cascadingModels</strong></p><p><code>boolean</code></p></td>
<td><p>Enables the model &quot;cascading&quot; behaviour. This allows for instance
 to link 2 nested tables where the 2nd table model is the selected row of
 the first table (or <code>null</code> if selection is empty). Using
 <code>cascadingModel=true</code> is only necessary when tracking view
 selection on the master nested view. You don't need it if, for instance,
 the master nested view is a single model view like a component view. In the
 latter case, you can bind a table detail view just by adding it to the same
 composite without having to set <code>cascadingModel=true</code>.
 <p>
 Default value is <code>false</code>, i.e. al nested views share the same
 model than the outer composite unless explicitly specified differently.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.AbstractMobilePageViewDescriptor"></a>AbstractMobilePageViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.AbstractMobilePageViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/AbstractMobilePageViewDescriptor.html)
+ **Super-type** : [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor)
+ **Sub-types** : [`MobileCardPageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileCardPageViewDescriptor), [`MobileCompositePageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileCompositePageViewDescriptor), [`MobileNavPageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileNavPageViewDescriptor)



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
<td align="left"><p><strong>backAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets back action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>enterAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets enter action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>forClientTypes</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets for client types.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>i18nDescription</strong></p><p><code>String</code></p></td>
<td><p>Sets i 18 n description.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>i18nName</strong></p><p><code>String</code></p></td>
<td><p>Sets i 18 n name.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>mainAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets main action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>pageEndAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets page end action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>position</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EPosition.html">EPosition</a></code></p></td>
<td><p>Sets position.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>swipeLeftAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets swipe left action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>swipeRightAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets swipe right action.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileCardPageViewDescriptor"></a>MobileCardPageViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileCardPageViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileCardPageViewDescriptor.html)
+ **Super-type** : [`AbstractMobilePageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.AbstractMobilePageViewDescriptor)



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
<td align="left"><p><strong>cascadingModels</strong></p><p><code>boolean</code></p></td>
<td><p>Sets cascading models. This operation is not supported on mobile pages.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pagesCardViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ICardViewDescriptor.html">ICard&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>Sets pages.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileCompositePageViewDescriptor"></a>MobileCompositePageViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileCompositePageViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileCompositePageViewDescriptor.html)
+ **Super-type** : [`AbstractMobilePageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.AbstractMobilePageViewDescriptor)



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
<td align="left"><p><strong>cascadingModels</strong></p><p><code>boolean</code></p></td>
<td><p>Sets cascading models. This operation is not supported on mobile pages.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>editorPage</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileCompositePageViewDescriptor.html">Mobile&#x200B;Composite&#x200B;Page&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>Sets editing page.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>inlineEditing</strong></p><p><code>boolean</code></p></td>
<td><p>Sets inline editing.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageSectionDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/IMobilePageSectionViewDescriptor.html">IMobile&#x200B;Page&#x200B;Section&#x200B;View&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets page sections.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileNavPageViewDescriptor"></a>MobileNavPageViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileNavPageViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileNavPageViewDescriptor.html)
+ **Super-type** : [`AbstractMobilePageViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.AbstractMobilePageViewDescriptor)



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
<td align="left"><p><strong>cascadingModels</strong></p><p><code>boolean</code></p></td>
<td><p>Sets cascading models. This operation is not supported on mobile lists.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>headerSectionDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/IMobilePageSectionViewDescriptor.html">IMobile&#x200B;Page&#x200B;Section&#x200B;View&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets header section descriptors.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>nextPageViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/IMobilePageViewDescriptor.html">IMobile&#x200B;Page&#x200B;View&#x200B;Descriptor</a></code></p></td>
<td><p>Sets next page.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>selectionViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets selection view. Supports only tree or list.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicBorderViewDescriptor"></a>BasicBorderViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicBorderViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicBorderViewDescriptor.html)
+ **Super-type** : [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor)
+ **Sub-types** : [`MobileBorderViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileBorderViewDescriptor)



A border view is a composite view that arranges its children to the
 <i>north</i>, <i>west</i>, <i>east</i>, <i>south</i> and <i>center</i>.
 Depending its position in the container, the resizing rules apply differently
 :
 <ul>
 <li><i>north</i> and <i>south</i> are resized horizontally and kept to their
 preferred size vertically</li>
 <li><i>west</i> and <i>east</i> are resized vertically and kept to their
 preferred size horizontally</li>
 <li><i>center</i> is resized both horizontally and vertically</li>
 </ul>
 Default cascading order for master-detail is :
 <p>
 north -> west -> center -> east -> south



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
<td align="left"><p><strong>centerViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the child view to layout in the <i>center</i> zone. The child view
 will be resized both horizontally and vertically.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>eastViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the child view to layout in the <i>east</i> zone. The child view will
 be resized vertically.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>northViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the child view to layout in the <i>north</i> zone. The child view will
 be resized horizontally.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>southViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the child view to layout in the <i>south</i> zone. The child view will
 be resized horizontally.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>westViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the child view to layout in the <i>west</i> zone. The child view will
 be resized vertically.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileBorderViewDescriptor"></a>MobileBorderViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileBorderViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileBorderViewDescriptor.html)
+ **Super-type** : [`BasicBorderViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicBorderViewDescriptor)



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
<td align="left"><p><strong>backAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets back action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>eastViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Not supported in mobile environment.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>enterAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets enter action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>forClientTypes</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets for client types.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>mainAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets main action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>pageEndAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets page end action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>position</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EPosition.html">EPosition</a></code></p></td>
<td><p>Sets  position.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>swipeLeftAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets swipe left action.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>swipeRightAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Sets swipe right action.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>westViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Not supported in mobile environment.
 <p>
 {@inheritDoc}</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicConstrainedGridViewDescriptor"></a>BasicConstrainedGridViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicConstrainedGridViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicConstrainedGridViewDescriptor.html)
+ **Super-type** : [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor)



This composite view arranges its children in a grid where cell behaviour and
 dimensions are configured using cell constraints. A cell constraint is a
 simple data structure holding the following properties :
 <ul>
 <li><code>row</code>: the row to which the cell belongs</li>
 <li><code>column</code>: the column to which the cell belongs</li>
 <li><code>width</code>: the number of columns the cell spans horizontally
 (default value is 1)</li>
 <li><code>height</code>: the number of rows the cell spans vertically
 (default value is 1)</li>
 <li><code>heightResizable</code>: whether the cell should be resized to take
 all the available space vertically</li>
 <li><code>widthResizable</code>: whether the cell should be resized to take
 all the available space horizontally</li>
 </ul>
 Default cascading order follows the order of nested view registrations in the
 container.



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
<td align="left"><p><strong>cells</strong></p><p><code>Map&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a>&#x200B;,<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/CellConstraints.html">Cell&#x200B;Constraints</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the nested children views along with their cell constraints. They
 are set as a <code>Map</code> that is :
 <ul>
 <li>keyed by the children views</li>
 <li>valued by the cell constraints to apply to each nested view</li>
 </ul></p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicEvenGridViewDescriptor"></a>BasicEvenGridViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicEvenGridViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicEvenGridViewDescriptor.html)
+ **Super-type** : [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor)



This composite view arranges its children in a grid where cells are
 distributed evenly. All cells are resized horizontally and vertically to fill
 its available space.
 <p>
 The number of cells in a row / column is determined by the combination of the
 <code>drivingDimension</code> and <code>drivingDimensionCellCount</code>
 properties. the cells are spread along the driving dimension (row or column)
 until the maximum number of cells in the dimension has been reached. Then a
 new row (or column) is added. The process repeats until all the cells have
 been added.
 <p>
 This container does not allow for individual cell configuration like
 row/column spanning. Whenever cell disposition has to be customized more
 finely, a <code>BasicConstrainedGridViewDescriptor</code> should be used
 instead.
 <p>
 Default cascading order follows the order of nested view registrations in the
 container.



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
<td align="left"><p><strong>cells</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the nested views to display as grid cells.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>drivingDimension</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EAxis.html">EAxis</a></code></p></td>
<td><p>Configures the driving dimension of the grid. This is either a value of the
 <code>EAxis</code> enum or its equivalent string representation :
 <ul>
 <li><code>ROW</code> for distributing cells along rows then columns</li>
 <li><code>COLUMN</code> for distributing cells along columns then rows</li>
 </ul>
 Default value is <code>EAxis.ROW</code>, i.e. distribute cells along rows
 then columns.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>drivingDimensionCellCount</strong></p><p><code>int</code></p></td>
<td><p>This property configures the maximum number of cells in the driving
 dimension (row or column). Nested views are distributed along the driving
 axis until this maximum number has been reached. A new row or column is
 then created to host the remaining cells.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicSplitViewDescriptor"></a>BasicSplitViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicSplitViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicSplitViewDescriptor.html)
+ **Super-type** : [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor)



This composite view arranges its children in a container split either
 horizontally or vertically. An horizontal split disposes its 2 children
 <i>left</i> and <i>right</i> whereas a vertical split disposes its 2 children
 <i>top</i> and <i>bottom</i>. The dividing bar can typically be moved by the
 user to distribute the available space.
 <p>
 Default cascading order for master-detail is :
 <p>
 left -> right or top -> bottom depending on the split orientation.



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
<td align="left"><p><strong>leftTopViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the <i>left</i> (horizontal split) of <i>top</i> (vertical split)
 nested view.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orientation</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EOrientation.html">EOrientation</a></code></p></td>
<td><p>Configures the split orientation of the container. This is either a value
 of the <code>EOrientation</code> enum or its equivalent string
 representation :
 <ul>
 <li><code>VERTICAL</code> for splitting the container vertically and
 arranging the views top and bottom</li>
 <li><code>HORIZONTAL</code> for splitting the container horizontally and
 arranging the views left and right</li>
 </ul>
 Default value is <code>EOrientation.VERTICAL</code>, i.e. the container is
 split vertically.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rightBottomViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the <i>right</i> (horizontal split) of <i>bottom</i> (vertical split)
 nested view.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicTabViewDescriptor"></a>BasicTabViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicTabViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicTabViewDescriptor.html)
+ **Super-type** : [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor)
+ **Sub-types** : [`MobileTabViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileTabViewDescriptor)



This composite view arranges its children in tabs. Each tab potentially
 displays a label (that is translated based on the name of the view in the
 tab), an icon (based on the icon of the view in the tab) and a toolTip (based
 on the description of the view in the tab).
 <p/>
 Default cascading order follows the order of nested view registrations in the
 container.



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
<td align="left"><p><strong>lazy</strong></p><p><code>boolean</code></p></td>
<td><p>When set to true, this parameter configures the tabs to be lazy bound
 (binding occurs only for the selected tab). This feature is only supported
 for tab views with <code>cascadingModel</code> set to false. default value
 is <code>true</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderingOptions</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/ERenderingOptions.html">ERendering&#x200B;Options</a></code></p></td>
<td><p>Indicates how the tabs should be rendered. This is either a value of the
 <code>ERenderingOptions</code> enum or its equivalent string representation
 :
 <ul>
 <li><code>LABEL_ICON</code> for label and icon</li>
 <li><code>LABEL</code> for label only</li>
 <li><code>ICON</code> for icon only.</li>
 </ul>
 <p/>
 Default value is <code>ERenderingOptions.LABEL_ICON</code>, i.e. label and
 icon.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>tabSelectionAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Registers an action that is implicitly triggered every time the tab selection
 changes on the tab view UI peer. The context of the action execution
 is the same as if the action was registered in the view action map.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>tabs</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the list of views to be displayed as tabs. The tabs order follows
 the children views order of this list.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileTabViewDescriptor"></a>MobileTabViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileTabViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileTabViewDescriptor.html)
+ **Super-type** : [`BasicTabViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicTabViewDescriptor)



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
<td align="left"><p><strong>carouselMode</strong></p><p><code>boolean</code></p></td>
<td><p>Sets carousel mode.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>cascadingModels</strong></p><p><code>boolean</code></p></td>
<td><p>Not supported in mobile environment.
 <p/>
 {@inheritDoc}</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>forClientTypes</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets for client types.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>position</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EPosition.html">EPosition</a></code></p></td>
<td><p>Sets position.</p></td>
</tr>
</tbody>
</table>

---


