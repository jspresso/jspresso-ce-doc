## BasicViewDescriptor

#### <a name="org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor"></a>BasicViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicViewDescriptor.html)
+ **Super-type** : [`DefaultIconDescriptor`](#org.jspresso.framework.util.descriptor.DefaultIconDescriptor)
+ **Sub-types** : [`AbstractCardViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractCardViewDescriptor), [`AbstractComponentViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractComponentViewDescriptor), [`AbstractTreeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractTreeViewDescriptor), [`BasicActionViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicActionViewDescriptor), [`BasicCollectionViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCollectionViewDescriptor), [`BasicCompositeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCompositeViewDescriptor), [`BasicMapViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicMapViewDescriptor), [`BasicPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor)



This is the abstract base descriptor for all views. Its main purpose, since
 it cannot be used directly, is to factorize common properties.



<table>
<caption>BasicViewDescriptor properties</caption>
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
<td><p>Assigns the view action map. An action map is generally represented as a
 toolbar attached to the view. The toolbar follows the structure of the
 action map :
 <ul>
 <li>each action list is contained in its own toolbar section which is
 visually separated from the other sections. This allows for visually
 grouping related actions as they are grouped in the action lists.</li>
 <li>each action contained in an action list is represented by a toolbar
 button using the action image as icon and translated action description as
 toolTip.</li>
 </ul>
 Depending on the UI channel, the view action map may also be replicated in
 a component contextual menu. In that case, the translated action name is
 used to label each menu item. The same grouping rules apply for the
 contextual menu than for the toolbar.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>background</strong></p><p><code>String</code></p></td>
<td><p>Sets the background color of the UI component. The color must be defined
 using its string hexadecimal representation (<i>0xargb</i> encoded).
 <p/>
 Default value is <code>null</code>, meaning use UI default.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>borderType</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EBorderType.html">EBorder&#x200B;Type</a></code></p></td>
<td><p>Sets the border type of the view. This is either a value of the
 <code>EBorderType</code> enum or its equivalent string representation :
 <ul>
 <li><code>NONE</code> for no border</li>
 <li><code>SIMPLE</code> for a line border</li>
 <li><code>TITLED</code> for a titled border. The view is then labeled with
 its translated name and and icon. Whenever the view name has not been
 explicitly set, the model name is used is used.</li>
 </ul>
 <p/>
 Default value is <code>EBorderType.NONE</code>, i.e. no border.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>font</strong></p><p><code>String</code></p></td>
<td><p>Allows to customize the font used by the UI component. The font must be
 string encoded using the pattern <b>&quot;[name];[style];[size]&quot;</b> :
 <ul>
 <li><b>[name]</b> is the name of the font, e.g. <i>arial</i>.</li>
 <li><b>[style]</b> is PLAIN, BOLD, ITALIC or a union of BOLD and ITALIC
 combined with the '|' character, e.g. <i>BOLD|ITALIC</i>.</li>
 <li><b>[size]</b> is the size of the font, e.g. <i>10</i>.</li>
 </ul>
 Any of the above pattern section can be left empty, thus falling back to
 the component default.
 <p/>
 Default value is <code>null</code>, meaning use default component font.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>foreground</strong></p><p><code>String</code></p></td>
<td><p>Sets the foreground color of the UI component. The color must be defined
 using its string hexadecimal representation (<i>0xargb</i> encoded).
 <p/>
 Default value is <code>null</code>, meaning use UI default.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>grantedRoles</strong></p><p><code>Collection&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns the roles that are authorized to use this view. It supports
 &quot;<b>!</b>&quot; prefix to negate the role(s). Whenever the user is not
 granted sufficient privileges, the view is replaced by an empty section at
 runtime. Setting the collection of granted roles to <code>null</code>
 (default value) disables role based authorization on the view level. The
 framework then checks for the model roles authorizations and will apply the
 same restrictions. If both view and model granted roles collections are
 <code>null</code>, then access is granted to anyone.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>modelDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IModelDescriptor.html">IModel&#x200B;Descriptor</a></code></p></td>
<td><p>Assigns the model descriptor backing the view. The model descriptor serves
 several purposes :
 <ul>
 <li>configuration of the view content. For instance whenever a form is
 assigned a component model descriptor, it will install 1 field per
 component rendering properties, unless otherwise specified in the view
 descriptor itself.</li>
 <li>configuration of the binding layer. There is no need for the developer
 to configure anything for the binding to occur between the view and the
 model. Based on their model descriptor, Jspresso will setup all the
 necessary plumbing to efficiently synchronize model properties with their
 view counterpart bi-directionally. This synchronization occurs implicitly
 using the <i>observer</i> pattern and one of the Jspresso key contract is
 to guarantee this synchronization seamlessly.</li>
 </ul>
 Although it is the developer responsibility to make sure the correct model
 descriptor is assigned to the view, there are cases where the framework
 will infer it. For instance, a composite view will by default transmit its
 model descriptor to its children that do not have their model descriptor
 explicitly set. This allows for setting the model descriptor only on the
 composite view and keep default <code>null</code> value on the children as
 an implicit model inheritance enablement.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>permId</strong></p><p><code>String</code></p></td>
<td><p>Sets the permanent identifier to this application element. Permanent
 identifiers are used by different framework parts, like dynamic security or
 record/replay controllers to uniquely identify an application element.
 Permanent identifiers are generated by the SJS build based on the element
 id but must be explicitly set if Spring XML is used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>preferredHeight</strong></p><p><code>Integer</code></p></td>
<td><p>Allows to set a preferred height (in pixels) for the created peer UI
 component. This will override default and give hints to the UI layouting
 system.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>preferredSize</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/Dimension.html">Dimension</a></code></p></td>
<td><p>Sets the preferred size.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>preferredWidth</strong></p><p><code>Integer</code></p></td>
<td><p>Allows to set a preferred width (in pixels) for the created peer UI
 component. This will override default and give hints to the UI layouting
 system.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>readOnly</strong></p><p><code>boolean</code></p></td>
<td><p>Allows to set a view read-only, i.e. none of the view part will allow for
 updating the underlying model. This is mainly a shortcut to assigning an
 &quot;always closed&quot; writability gate. One difference though is that,
 since the framework knows that the view will never be updatable, it may
 take specific decisions to render properties in a slightly different way,
 e.g. instead of using a disabled text field, use a label.
 <p/>
 Default value is <code>false</code>, i.e. view is updatable.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>secondaryActionMap</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/ActionMap.html">Action&#x200B;Map</a></code></p></td>
<td><p>Assigns the view secondary action map. Same rules as the primary action map
 apply except that actions in this map should be visually distinguished from
 the main action map, e.g. placed in another toolbar.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>styleName</strong></p><p><code>String</code></p></td>
<td><p>Assigns the style name to use for this view. The way it is actually
 leveraged depends on the UI channel. It will generally be mapped to some
 sort of CSS style name.
 <p/>
 Default value is <code>null</code>, meaning that a default style is used.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>writabilityGates</strong></p><p><code>Collection&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gate/IGate.html">IGate</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Assigns a collection of gates to determine view <i>writability</i>. A view
 will be considered writable (updatable) if and only if all gates are open.
 This mechanism is mainly used for dynamic UI authorization based on model
 state, e.g. a validated invoice should not be editable anymore.
 <p/>
 View assigned gates will be cloned for each view instance created and
 backed by this descriptor. So basically, each view instance will have its
 own, unshared collection of writability gates.
 <p/>
 Jspresso provides a useful set of gate types, like the binary property gate
 that open/close based on the value of a boolean property of the view model.
 <p/>
 By default, view descriptors are not assigned any gates collection, i.e.
 there is no writability restriction. Note however that view actual
 writability is the combination of view <i>and</i> model writability.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.AbstractCardViewDescriptor"></a>AbstractCardViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.AbstractCardViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/AbstractCardViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`BasicCardViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCardViewDescriptor), [`EntityCardViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.EntityCardViewDescriptor)



This descriptor serves as abstract base implementation for card view
 descriptor. A card view is a view stack made of children views (the cards)
 where only the view (card) at the top of the stack is visible. The actual
 child view to place on the top of the stack is dynamically determined based
 on the bound model. This card determination strategy depends on the concrete
 descriptor sub-types.
 <p>
 One might wonder why a card view is not considered as (and actually does not
 inherit from) a composite view. The difference is that composite views are
 used aggregate views that displays - hopefully - different parts (the children
 views) of the <b>same</b> model. A card view descriptor is rather used to
 make the same UI region display different views depending on different models
 (or different model states). Once the model is fixed, the card view behaves
 exactly as its top card.
 <p>
 One of the most important usage of card views is when it is combine as the
 detail in a master-detail view. The detail view may then change dynamically
 based on the selected master.



<table>
<caption>AbstractCardViewDescriptor properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicCardViewDescriptor"></a>BasicCardViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicCardViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicCardViewDescriptor.html)
+ **Super-type** : [`AbstractCardViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractCardViewDescriptor)



Describes a multi-purpose card view that is configurable with a custom card
 determination strategy. Cards are registered with a name key that is used to
 retrieve the card to display based on the card selector selected name key.



<table>
<caption>BasicCardViewDescriptor properties</caption>
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
<td align="left"><p><strong>cardNameSelector</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ICardNameSelector.html">ICard&#x200B;Name&#x200B;Selector</a></code></p></td>
<td><p>Configures the card determination strategy. This delegate is responsible
 for selecting the card name key based on the model bound to the view.
 Every time the bound model changes, the card name selector is triggered to
 select a new card. The names returned by the card name selector must match
 the names under which the cards are registered. Whenever the card name
 selector returns an unknown name, the card view displays an empty view. The
 card name selector can optionally implement <code>ICardProvider</code> in
 which case, it will be given a chance to create cards dynamically based on
 their names.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>cardViewDescriptors</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the card views keyed by their name keys. The names used as key of
 the <code>Map</code> must match the names that are returned by the
 registered card name selector.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.EntityCardViewDescriptor"></a>EntityCardViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.EntityCardViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/EntityCardViewDescriptor.html)
+ **Super-type** : [`AbstractCardViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractCardViewDescriptor)



This card view provides a simple card determination strategy that is based on
 the bound model type. This strategy pulls up the card whose model descriptor
 matches the type of the bound model.



<table>
<caption>EntityCardViewDescriptor properties</caption>
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
<td align="left"><p><strong>viewDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Registers the list of card view descriptors. Every time the bound model
 changes, this list is iterated until a card with a matching model is found.
 The first matching card is displayed. Whenever no registered card matches,
 an empty view is displayed.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.AbstractComponentViewDescriptor"></a>AbstractComponentViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.AbstractComponentViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/AbstractComponentViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`BasicComponentViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicComponentViewDescriptor), [`MobileComponentViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileComponentViewDescriptor)



Abstract class for component view descriptors.



<table>
<caption>AbstractComponentViewDescriptor properties</caption>
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
<td align="left"><p><strong>labelFont</strong></p><p><code>String</code></p></td>
<td><p>This property defines the font of the property labels. It might differ from
 the field component one. The font must be string encoded using the pattern
 <b>&quot;[name];[style];[size]&quot;</b> :
 <ul>
 <li><b>[name]</b> is the name of the font, e.g. <i>arial</i>.</li>
 <li><b>[style]</b> is PLAIN, BOLD, ITALIC or a union of BOLD and ITALIC
 combined with the '|' character, e.g. <i>BOLD|ITALIC</i>.</li>
 <li><b>[size]</b> is the size of the font, e.g. <i>10</i>.</li>
 </ul>
 Any of the above pattern section can be left empty, thus falling back to
 the component default.
 <p/>
 This property can be overridden on a field basis using an explicit property view definition.
 <p/>
 Default value is <code>null</code>, meaning use default component font.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>labelsPosition</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ELabelPosition.html">ELabel&#x200B;Position</a></code></p></td>
<td><p>Instructs Jspresso where to place the fields label. This is either a value
 of the <code>ELabelPosition</code> enum or its equivalent string
 representation :
 <ul>
 <li><code>ABOVE</code> for placing each field label above the property UI
 component</li>
 <li><code>ASIDE</code> for placing each field label aside the property UI
 component</li>
 <li><code>NONE</code> for completely disabling fields labelling on the view
 </li>
 </ul>
 Default value is <code>ELabelPosition.ASIDE</code>, i.e. fields label next
 to the property UI component.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>propertyViewDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IPropertyViewDescriptor.html">IProperty&#x200B;View&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows for configuring the fields of the component view in a
 very customizable manner, thus overriding the model descriptor defaults.
 Each property view descriptor contained in the list describes a form field
 that will be rendered in the UI accordingly.
 <p/>
 For instance, a writable property can be made specifically read-only on
 this component view by specifying its property view descriptor read-only.
 In that case, the model remains untouched and only the view is impacted.
 <p/>
 Following the same scheme, you can assign a list of writability gates on a
 field to introduce dynamic field editability on the view without modifying
 the model.
 <p/>
 A last, yet important, example of column view descriptor usage is the
 role-based field set configuration. Whenever you want a field to be
 available only for certain user roles (profiles), you can configure a field
 property view descriptor with a list of granted roles. If the user doesn't
 have the field(s)required role, the forbidden field(s) simply won't be
 displayed. This allows for high authorization-based versatility.
 <p/>
 There are many other usages of defining field property view descriptors
 (like individual labels color and font), all of them being linked to
 customizing the form fields without impacting the model.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderedProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This is somehow a shortcut to using the
 <code>propertyViewDescriptors</code> property. Instead of providing a
 full-blown list of property view descriptors to configure the component
 view fields, you just pass-in a list of property names. view fields are
 then created from this list, keeping model defaults for all fields
 characteristics.
 <p/>
 Whenever the property value is <code>null</code> (default), the fields list
 is determined from the component descriptor <code>renderedProperties</code>
 property.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>valueFont</strong></p><p><code>String</code></p></td>
<td><p>This property defines the font of the property values. The font must be string encoded using the pattern
 <b>&quot;[name];[style];[size]&quot;</b> :
 <ul>
 <li><b>[name]</b> is the name of the font, e.g. <i>arial</i>.</li>
 <li><b>[style]</b> is PLAIN, BOLD, ITALIC or a union of BOLD and ITALIC
 combined with the '|' character, e.g. <i>BOLD|ITALIC</i>.</li>
 <li><b>[size]</b> is the size of the font, e.g. <i>10</i>.</li>
 </ul>
 Any of the above pattern section can be left empty, thus falling back to
 the component default.
 <p/>
 This property can be overridden on a field basis using an explicit property view definition.
 <p/>
 Default value is <code>null</code>, meaning use default component font.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicComponentViewDescriptor"></a>BasicComponentViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicComponentViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicComponentViewDescriptor.html)
+ **Super-type** : [`AbstractComponentViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractComponentViewDescriptor)



Component view descriptors are surely one of the most commonly used view
 descriptors in Jspresso. It allows to implement advanced form-like views to
 interact with a single component model. Component properties that are
 displayed in the view are organized in an invisible grid. Each field
 component is labelled with the property name it displays and labels can be
 configured to be displayed aside or above their peer field. Property fields
 can be configured to span multiple form columns. Component view offer various
 straightforward customizations, but the most advanced and powerful one is
 definitely the <code>propertyViewDescriptors</code> property tat allows to
 fine-tune each component UI field individually.
 <p>
 The description property is used to compute view tooltips and support the
 following rules :
 <ol>
 <li>if the description is a property name of the underlying model, this
 property will be used to compute the (dynamic) tooltip (depending on the
 actual model).</li>
 <li>if the description is not a property name of the underlying model, the
 the tooltip is considered static and the translation will searched in the
 application resource bundles.</li>
 <li>if the description is the empty string (''), the tooltip is de-activated.
 </li>
 <li>if the description is not set, then the toHtml property (see toHtml
 property on entities / components definition) is used as dynamic property.
 And the toHtml falls back to the toString if not set, which falls back to the
 1st string rendered property if not set.</li>
 </ol>
 Note that on every case above, HTML is supported. This way, you can have
 really useful tooltips (event multi-line), in order to detail some synthetic
 data. Moreover, this rule is available for the form tooltip, but also for
 each individual field (property view) in the form.



<table>
<caption>BasicComponentViewDescriptor properties</caption>
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
<td align="left"><p><strong>columnCount</strong></p><p><code>int</code></p></td>
<td><p>Configures the number of columns on this component view. Property fields
 that are to be displayed in the view are spread across columns and rows
 following their defined order. Whenever a row does not contain enough empty
 cells to receive the next field (either because the last column has been
 reached or the next field has been configured to span multiple columns and
 there is not enough cells left in the current row to satisfy the span), a
 new row is created and the next field is added to the first column on the
 new row.
 <p>
 Note that column count and span are defined in fields coordinates (the
 <i>field</i> including the property UI component + its label). The
 underlying grid is actually finer since it has to cope with the labels; but
 this is internal implementation details and Jspresso takes care of it,
 without the developer having to cope with labels placements.
 <p>
 Default value is 1, meaning that all rendered fields will be stacked in a
 single column.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>labelsHorizontalPosition</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EHorizontalPosition.html">EHorizontal&#x200B;Position</a></code></p></td>
<td><p>Configures the label horizontal position. There are special cases when the default label position has to be
 overridden. This is either a value of the <code>EHorizontalPosition</code>
 enum or its equivalent string representation :
 <ul>
 <li><code>LEFT</code> for left position</li>
 <li><code>RIGHT</code> for right position</li>
 </ul>
 <p>
 Default value is <code>LEFT</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>propertyWidths</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,Object&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows to simply define property spans in the underlying grid
 without having to extensively define the
 <code>propertyViewDescriptors</code> property. It must be configured with a
 <code>Map</code> containing only the properties that need to span more than
 1 column. The other properties will follow the default span of 1.
 <p>
 The <code>Map</code> is :
 <ul>
 <li>keyed by the name of the property</li>
 <li>valued by the number of columns of the property span</li>
 </ul>
 Default value is <code>null</code>, meaning all property fields have a span
 of 1.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderedChildProperties</strong></p><p><code>Map&#x200B;&lt;&#x200B;String&#x200B;,List&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Whenever a rendered property is not scalar, this property allows to
 override which of the referenced component fields should be displayed :
 <ul>
 <li>as columns when the rendered property is a collection property</li>
 <li>as fields when the rendered property is a reference property</li>
 </ul>
 The property must be configured with a <code>Map</code> which is :
 <ul>
 <li>keyed by the non-scalar property name</li>
 <li>valued by the list of the property names to render for the child
 element(s)</li>
 </ul>
 <p>
 A <code>null</code> value (default), means that all non-scalar properties
 will be rendered using default rendered properties as specified in their
 referenced model descriptor.
 <p>
 Please note that this is quite unusual to embed non-scalar properties
 directly in a component view. Although permitted, you won't have as much
 flexibility in the content layouting as you would have when using composite
 views; so the latter is by far recommended.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>verticallyScrollable</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to define the form vertical scrolling behaviour.
 Whenever it is set to true, the corresponding UI component will install a
 vertical scroll bar when the available vertical space is not enough.
 <p>
 Default value is <code>false</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>widthResizeable</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to define the form horizontal fill behaviour.
 Whenever it is set to true, the corresponding UI component will fill all its available horizontal space.
 <p/>
 Default value is <code>true</code>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileComponentViewDescriptor"></a>MobileComponentViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileComponentViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileComponentViewDescriptor.html)
+ **Super-type** : [`AbstractComponentViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractComponentViewDescriptor)



A mobile form view descriptor.



<table>
<caption>MobileComponentViewDescriptor properties</caption>
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
<td align="left"><p><strong>excludedReadingProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets filtered reading properties. Allows to configure the properties that will be excluded from the read-only page.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>excludedWritingProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets filtered writing properties. Allows to configure the properties that will be excluded from the editor page.</p></td>
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


#### <a name="org.jspresso.framework.view.descriptor.basic.AbstractTreeViewDescriptor"></a>AbstractTreeViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.AbstractTreeViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/AbstractTreeViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`BasicTreeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicTreeViewDescriptor), [`MobileTreeViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileTreeViewDescriptor)



This descriptor is use to design a tree view. The way to define a tree view
 in Jspresso is a matter of assembling <i>tree level descriptors</i>
 hierarchically. A <i>tree level descriptor</i> is a group of sibling nodes
 that usually represent a component collection property. Each individual tree
 node collection can be secured by using role-based authorization (i.e.
 <code>grantedRoles</code>) on its descriptor.



<table>
<caption>AbstractTreeViewDescriptor properties</caption>
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
<td align="left"><p><strong>childDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ITreeLevelDescriptor.html">ITree&#x200B;Level&#x200B;Descriptor</a></code></p></td>
<td><p>Configures the first tree level as being a single collection of sibling
 nodes. For instance, if the child tree level is mapped to a collection
 (collA) containing 5 elements (collA_Elt-1 to 5), the tree would look like
 :
 <p/>
 <pre>
 rootItem
   coll<b>A</b>_Elt-<b>1</b>
   coll<b>A</b>_Elt-<b>2</b>
   coll<b>A</b>_Elt-<b>3</b>
   coll<b>A</b>_Elt-<b>4</b>
   coll<b>A</b>_Elt-<b>5</b>
 </pre>
 <p/>
 In the example above, you should notice that there is no need for the tree
 to install an intermediary node to visually group the collection elements
 since the collection is alone on its level.
 <p/>
 This property is only used if the <code>rootSubtreeDescriptor</code> is not
 explicitly set. In the latter case, nested subtrees are determined from
 the <code>rootSubtreeDescriptor</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>childrenDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ITreeLevelDescriptor.html">ITree&#x200B;Level&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Configures the first tree level as being a list of collections of sibling
 nodes (subtrees). For instance, if the children tree levels are mapped to 2
 collection properties (collA, collB) each containing 3 elements
 (collA_Elt-1 to 3 and collB_Elt-1 to 3), the tree would look like :
 <p/>
 <pre>
 rootItem
   <i>collA</i>
     coll<b>A</b>_Elt-<b>1</b>
     coll<b>A</b>_Elt-<b>2</b>
     coll<b>A</b>_Elt-<b>3</b>
   <i>collB</i>
     coll<b>B</b>_Elt-<b>1</b>
     coll<b>B</b>_Elt-<b>2</b>
     coll<b>B</b>_Elt-<b>3</b>
 </pre>
 <p/>
 In the example above, you should notice intermediate collection property
 grouping nodes (collA and collB in italic). They automatically appeared to
 clearly group the tree nodes belonging to the different collections.
 <p/>
 This property is only used if the <code>rootSubtreeDescriptor</code> is not
 explicitly set. In the latter case, nested subtrees are determined from
 the <code>rootSubtreeDescriptor</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>displayIcon</strong></p><p><code>boolean</code></p></td>
<td><p>Configures if the tree view should show icon based on the icon image url provider. Defaults to <code>true</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconImageURLProvider</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/IconProvider.html">Icon&#x200B;Provider</a></code></p></td>
<td><p>The icon image URL provider is the delegate responsible for inferring a
 tree node icon based on its underlying model. By default (i.e. when
 <code>iconImageURLProvider</code> is <code>null</code>), Jspresso will use
 the underlying component descriptor icon, if any. Using a custom icon image
 URL provider allows to implement finer rules like using different icons
 based on the underlying object state. There is a single method to implement
 to achieve this :
 <p/>
 <code>String getIconImageURLForObject(Object userObject);</code></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>itemSelectionAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>This property allows to bind an action that gets triggered every time the
 selection changes on the tree view. The action context passed to the action
 when it is executed is the same as if it had been registered on the tree
 view.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>maxDepth</strong></p><p><code>int</code></p></td>
<td><p>This property is used only when the tree (or sub-tree) is declared
 recursively, i.e. a tree level belongs to its own children hierarchy.
 Default value is <i>10</i>, meaning that a maximum number of 10 levels can
 be nested.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>renderedProperty</strong></p><p><code>String</code></p></td>
<td><p>This property allows to define the model property used to label the root
 node.
 <p/>
 This property is only used if the <code>rootSubtreeDescriptor</code> is not
 explicitly set. In the latter case, <code>renderedProperty</code> is
 determined from the <code>rootSubtreeDescriptor</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>rootSubtreeDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ITreeLevelDescriptor.html">ITree&#x200B;Level&#x200B;Descriptor</a></code></p></td>
<td><p>This property allows to explicitly define the tree root level as any other
 level. Most of the time, you will prefer using the following shortcut
 properties :
 <ul>
 <li><code>childDescriptor</code></li>
 <li><code>childrenDescriptors</code></li>
 <li><code>renderedProperty</code></li>
 </ul>
 Whenever <code>rootSubtreeDescriptor</code> is explicitly set, the
 properties above are simply ignored since all values are determined from
 <code>rootSubtreeDescriptor</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rowAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Registers an action that is implicitly triggered every time a row is
 activated (e.g. double-clicked for current UI channels) on the collection
 view UI peer. The context of the action execution is the same as if the
 action was registered in the view action map.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicTreeViewDescriptor"></a>BasicTreeViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicTreeViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicTreeViewDescriptor.html)
+ **Super-type** : [`AbstractTreeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractTreeViewDescriptor)
+ **Sub-types** : 



This descriptor is use to design a tree view. The way to define a tree view
 in Jspresso is a matter of assembling <i>tree level descriptors</i>
 hierarchically. A <i>tree level descriptor</i> is a group of sibling nodes
 that usually represent a component collection property. Each individual tree
 node collection can be secured by using role-based authorization (i.e.
 <code>grantedRoles</code>) on its descriptor.



<table>
<caption>BasicTreeViewDescriptor properties</caption>
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
<td align="left"><p><strong>expanded</strong></p><p><code>boolean</code></p></td>
<td><p>Setting this property to <code>true</code> configures the created tree to
 appear with its node expanded. A value of <code>false</code> (default)
 means that the tree nodes are initially collapsed.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileTreeViewDescriptor"></a>MobileTreeViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileTreeViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileTreeViewDescriptor.html)
+ **Super-type** : [`AbstractTreeViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractTreeViewDescriptor)
+ **Sub-types** : 



This descriptor is use to design a tree view. The way to define a tree view
 in Jspresso is a matter of assembling <i>tree level descriptors</i>
 hierarchically. A <i>tree level descriptor</i> is a group of sibling nodes
 that usually represent a component collection property. Each individual tree
 node collection can be secured by using role-based authorization (i.e.
 <code>grantedRoles</code>) on its descriptor.



<table>
<caption>MobileTreeViewDescriptor properties</caption>
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
<td align="left"><p><strong>showArrow</strong></p><p><code>boolean</code></p></td>
<td><p>Sets show arrow.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicActionViewDescriptor"></a>BasicActionViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicActionViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicActionViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)



This type of view allows to make an action available as a view and thus
 participate in the UI composition as a visual component. An action view can
 then be embedded in surrounding a composite view. It literally takes the
 action away from the toolbar/context menu it is located when registered in an
 action map and makes it a primary citizen of the UI.



<table>
<caption>BasicActionViewDescriptor properties</caption>
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
<td align="left"><p><strong>action</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Assigns the action to display as a view. The action will typically be
 rendered as a button in the UI. whenever you want to size the icon used to
 display the action (and thus the button peer), you might use the
 <code>preferredWidth</code> / <code>preferredHeight</code> properties.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderingOptions</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/ERenderingOptions.html">ERendering&#x200B;Options</a></code></p></td>
<td><p>Indicates how the action should be rendered. This is either a value of the
 <code>ERenderingOptions</code> enum or its equivalent string representation
 :
 <ul>
 <li><code>LABEL_ICON</code> for label and icon</li>
 <li><code>LABEL</code> for label only</li>
 <li><code>ICON</code> for icon only.</li>
 </ul>
 <p>
 Default value is <code>ERenderingOptions.ICON</code>, i.e. icon only.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicCollectionViewDescriptor"></a>BasicCollectionViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicCollectionViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicCollectionViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`AbstractListViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractListViewDescriptor), [`BasicTableViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicTableViewDescriptor)



This is the abstract base descriptor of all views used to display a
 collection of elements. A collection view must be backed by a collection
 descriptor model. Most of the time, the model will be a collection property
 descriptor so that the collection to display is directly inferred from the
 collection property value through the binding layer.



<table>
<caption>BasicCollectionViewDescriptor properties</caption>
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
<td align="left"><p><strong>autoSelectFirstRow</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the default selection that gets applied when the content of the
 collection view changes. Whenever set to <code>true</code>, the 1st row
 will be automatically selected, whereas nothing happens when set to false.
 <p>
 The default value depends on the selection mode of the collection view.
 When a cumulative selection mode is used, <code>autoSelectFirstRow</code>
 defaults to <code>false</code>. It defaults to <code>true</code> otherwise.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>itemSelectionAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Registers an action that is implicitly triggered every time the selection
 changes on the collection view UI peer. The context of the action execution
 is the same as if the action was registered in the view action map.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>modelDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IModelDescriptor.html">IModel&#x200B;Descriptor</a></code></p></td>
<td><p>{@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>paginationViewDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IViewDescriptor.html">IView&#x200B;Descriptor</a></code></p></td>
<td><p>Configures a view that will control the pagination (if any) on this
 collection view. When constructed, the collection view will be decorated
 with the pagination view. The pagination view will be bound to the same
 model as the one providing the collection of the collection view.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>rowAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Registers an action that is implicitly triggered every time a row is
 activated (e.g. double-clicked for current UI channels) on the collection
 view UI peer. The context of the action execution is the same as if the
 action was registered in the view action map.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>selectionMode</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/ESelectionMode.html">ESelection&#x200B;Mode</a></code></p></td>
<td><p>Sets the selection mode of the collection view. This is either a value of
 the <code>ESelectionMode</code> enum or its equivalent string
 representation :
 <ul>
 <li><code>MULTIPLE_INTERVAL_SELECTION</code> for allowing any type of
 selection</li>
 <li><code>MULTIPLE_INTERVAL_CUMULATIVE_SELECTION</code> for allowing any
 type of selection with toggle behaviour</li>
 <li><code>SINGLE_INTERVAL_SELECTION</code> for allowing only contiguous
 interval selection</li>
 <li><code>SINGLE_INTERVAL_CUMULATIVE_SELECTION</code> for allowing only
 contiguous interval selection with toggle behaviour</li>
 <li><code>SINGLE_SELECTION</code> for allowing only a single item selection
 </li>
 <li><code>SINGLE_CUMULATIVE_SELECTION</code> for allowing only a single
 item selection with toggle behaviour</li>
 </ul>
 <p>
 Default value is <code>ESelectionMode.MULTIPLE_INTERVAL_SELECTION</code>,
 i.e. any type of selection allowed.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>selectionModelDescriptor</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/model/descriptor/IModelDescriptor.html">IModel&#x200B;Descriptor</a></code></p></td>
<td><p>Sets the selectionModelDescriptor.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.AbstractListViewDescriptor"></a>AbstractListViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.AbstractListViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/AbstractListViewDescriptor.html)
+ **Super-type** : [`BasicCollectionViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCollectionViewDescriptor)
+ **Sub-types** : [`BasicListViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicListViewDescriptor), [`MobileListViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileListViewDescriptor)



This type of descriptor is used to implement a list view. A list view is a
 single column, un-editable collection view used to display a collection of
 components. Each item is displayed using a string representation that can be
 customized using the <code>renderedProperty</code> property. List views are
 rarely used since one might prefer its much more advanced cousin, i.e. the
 table view.
 <p>
 Despite its low usage as an individual UI component, the list view is also
 used by Jspresso to describe tree parts. A collection of sibling tree nodes
 can actually be considered as being a list view and can be described as such.
 In the latter case, the <code>renderedProperty</code> property will be used
 to label the tree nodes.



<table>
<caption>AbstractListViewDescriptor properties</caption>
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
<td align="left"><p><strong>displayIcon</strong></p><p><code>boolean</code></p></td>
<td><p>Configures if the list view should show icon based on the icon image url provider. Defaults to <code>true</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>iconImageURLProvider</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/IconProvider.html">Icon&#x200B;Provider</a></code></p></td>
<td><p>The icon image URL provider is the delegate responsible for inferring a
 tree node icon based on its underlying model. By default (i.e. when
 <code>iconImageURLProvider</code> is <code>null</code>), Jspresso will use
 the underlying component descriptor icon, if any. Using a custom icon image
 URL provider allows to implement finer rules like using different icons
 based on the underlying object state. There is a single method to implement
 to achieve this :
 <p>
 <code>String getIconImageURLForObject(Object userObject);</code></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>renderedProperty</strong></p><p><code>String</code></p></td>
<td><p>Configures the model property to be rendered in the list. Whenever this
 property is left to <code>null</code> (default value), the
 <code>toStringProperty</code> of the element component descriptor is used.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicListViewDescriptor"></a>BasicListViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicListViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicListViewDescriptor.html)
+ **Super-type** : [`AbstractListViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractListViewDescriptor)



This type of descriptor is used to implement a list view. A list view is a
 single column, un-editable collection view used to display a collection of
 components. Each item is displayed using a string representation that can be
 customized using the <code>renderedProperty</code> property. List views are
 rarely used since one might prefer its much more advanced cousin, i.e. the
 table view.
 <p>
 Despite its low usage as an individual UI component, the list view is also
 used by Jspresso to describe tree parts. A collection of sibling tree nodes
 can actually be considered as being a list view and can be described as such.
 In the latter case, the <code>renderedProperty</code> property will be used
 to label the tree nodes.



<table>
<caption>BasicListViewDescriptor properties</caption>
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
<tr>
<td align="left">This class does not have any specific property.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileListViewDescriptor"></a>MobileListViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileListViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileListViewDescriptor.html)
+ **Super-type** : [`AbstractListViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.AbstractListViewDescriptor)



This type of descriptor is used to implement a list view. A list view is a
 single column, un-editable collection view used to display a collection of
 components. Each item is displayed using a string representation that can be
 customized using the <code>renderedProperty</code> property. List views are
 rarely used since one might prefer its much more advanced cousin, i.e. the
 table view.
 <p>
 Despite its low usage as an individual UI component, the list view is also
 used by Jspresso to describe tree parts. A collection of sibling tree nodes
 can actually be considered as being a list view and can be described as such.
 In the latter case, the <code>renderedProperty</code> property will be used
 to label the tree nodes.



<table>
<caption>MobileListViewDescriptor properties</caption>
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
<td align="left"><p><strong>autoSelectFirstRow</strong></p><p><code>boolean</code></p></td>
<td><p>Not supported in mobile environment.
 <p>
 {@inheritDoc}</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>showArrow</strong></p><p><code>boolean</code></p></td>
<td><p>Sets show arrow.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicTableViewDescriptor"></a>BasicTableViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicTableViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicTableViewDescriptor.html)
+ **Super-type** : [`BasicCollectionViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicCollectionViewDescriptor)



This descriptor is used to implement a table view. This is certainly the most
 commonly used collection descriptor in Jspresso. A table view displays a
 collection of components (one row per component in the collection) detailed
 by a set of properties (one column per displayed component property).
 <p>
 The table view will automatically adapt its columns depending on the
 underlying property descriptors, e.g. :
 <ul>
 <li>columns for read-only properties won't be editable</li>
 <li>columns that are assigned writability gates will compute the editability
 of their cells based on each cell's gates</li>
 <li>columns will adapt their renderer/editor based on the underlying property
 type, e.g. a calendar component will be used for dates</li>
 <li>column titles will be filled with property names translations based on
 the user locale</li>
 <li>mandatory properties will be visually indicated</li>
 <li>...</li>
 </ul>
 A table view provides sensible defaults regarding its configuration, but it
 can be refined using either the simple <code>renderedProperties</code> or the
 more advanced yet lot more powerful <code>columnViewDescriptors</code>
 properties.
 <p>
 The description property is used to compute view tooltips and support the
 following rules :
 <ol>
 <li>if the description is a property name of the underlying model, this
 property will be used to compute the (dynamic) tooltip (depending on the
 actual model).</li>
 <li>if the description is not a property name of the underlying model, the
 the tooltip is considered static and the translation will searched in the
 application resource bundles.</li>
 <li>if the description is the empty string (''), the tooltip is de-activated.
 </li>
 <li>if the description is not set, then the toHtml property (see toHtml
 property on entities / components definition) is used as dynamic property.
 And the toHtml falls back to the toString if not set, which falls back to the
 1st string rendered property if not set.</li>
 </ol>
 Note that on every case above, HTML is supported. This way, you can have
 really useful tooltips (event multi-line), in order to detail some synthetic
 data. Moreover, this rule is available for the table rows tooltip, but also
 for each individual column (property view) in the table.



<table>
<caption>BasicTableViewDescriptor properties</caption>
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
<td align="left"><p><strong>columnReorderingAllowed</strong></p><p><code>boolean</code></p></td>
<td><p>Configures if the table view should allow for column reordering.
 The default value is <code>true</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>columnViewDescriptors</strong></p><p><code>List&#x200B;&lt;&#x200B;<a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/IPropertyViewDescriptor.html">IProperty&#x200B;View&#x200B;Descriptor</a>&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This property allows for configuring the columns of the table view in a
 very customizable manner, thus overriding the model descriptor defaults.
 Each property view descriptor contained in the list describes a table
 column that will be rendered in the UI accordingly.
 <p>
 For instance, a writable property can be made specifically read-only on
 this table view by specifying its column property view descriptor
 read-only. In that case, the model remains untouched and only the view is
 impacted.
 <p>
 Following the same scheme, you can assign a list of writability gates on a
 column to introduce dynamic cell editability on the view without modifying
 the model.
 <p>
 A last, yet important, example of column view descriptor usage is the
 role-based column set configuration. Whenever you want a column to be
 available only for certain user roles (profiles), you can configure a
 column property view descriptor with a list of granted roles. If the user
 doesn't have the column(s)required role, the forbidden columns simply won't
 be displayed. This allows for high authorization-based versatility.
 <p>
 There are many other usages of defining column property view descriptors
 all of them being linked to customizing the table columns without impacting
 the model.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>horizontallyScrollable</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to define the table horizontal scrolling behaviour.
 Whenever it is set to false, the corresponding table UI component will
 adapt its columns to fit the available horizontal space.
 <p>
 Default value is <code>true</code>, i.e. table columns will have their
 default size and tha table will scroll horizontally as needed.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderedProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>This is somehow a shortcut to using the <code>columnViewDescriptors</code>
 property. Instead of providing a full-blown list of property view
 descriptors to configure the table columns, you just pass-in a list of
 property names. Table columns are then created from this list, keeping
 model defaults for all column characteristics.
 <p>
 Whenever the property value is <code>null</code> (default), the column list
 is determined from the collection element component descriptor
 <code>renderedProperties</code> property.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>sortable</strong></p><p><code>boolean</code></p></td>
<td><p>This property allows to define the table horizontal sorting behaviour.
 Whenever it is set to false, the corresponding table UI component will not
 allow manual sorting of its rows.
 <p>
 Default value is <code>true</code>, i.e. table allows for its rows to be
 sorted.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>sortingAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures the action to be activated when a sort is triggered by the user.
 It should be used with caution and rarely be overridden from the default.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicMapViewDescriptor"></a>BasicMapViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicMapViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicMapViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`MobileMapViewDescriptor`](#org.jspresso.framework.view.descriptor.mobile.MobileMapViewDescriptor)



This descriptor is used to implement a map view.



<table>
<caption>BasicMapViewDescriptor properties</caption>
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
<td align="left"><p><strong>latitudeProperty</strong></p><p><code>String</code></p></td>
<td><p>Sets latitude property.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>longitudeProperty</strong></p><p><code>String</code></p></td>
<td><p>Sets longitude property.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.mobile.MobileMapViewDescriptor"></a>MobileMapViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.mobile.MobileMapViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/mobile/MobileMapViewDescriptor.html)
+ **Super-type** : [`BasicMapViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicMapViewDescriptor)



A mobile map view descriptor.



<table>
<caption>MobileMapViewDescriptor properties</caption>
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


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor"></a>BasicPropertyViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicPropertyViewDescriptor.html)
+ **Super-type** : [`BasicViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicViewDescriptor)
+ **Sub-types** : [`BasicEnumerationPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicEnumerationPropertyViewDescriptor), [`BasicHtmlViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicHtmlViewDescriptor), [`BasicImageViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicImageViewDescriptor), [`BasicStringPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicStringPropertyViewDescriptor)



This view descriptor serves 2 purposes :
 <ul>
 <li>configure complex, component based views : refine <i>columns</i> of table
 views and <i>fields</i> of component (form) views.</li>
 <li>display a single property as an autonomous view, i.e. not as a table
 column or a form field.</li>
 </ul>
 The second usage might be a little bit unusual, but here is a use-case
 scenario : display a text area which maps a text property that contains XML
 content. This text area must be displayed in a split pane and provide actions
 to interact directly with the FS (save content to a file, load content from a
 file, ...). In that case, defining a property view alone on the text property
 of the owning component might be a good solution.



<table>
<caption>BasicPropertyViewDescriptor properties</caption>
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
<td align="left"><p><strong>action</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/action/IAction.html">IAction</a></code></p></td>
<td><p>Configures the action to be triggered when <i>acting</i> on this property.
 There are 2 cases :
 <p>
 <ol>
 <li>If the property is read-only, then assigning an action turns the
 property into a clickable hyperlink</li>
 <li>If the property is read-write, the registered action will be triggered
 when the user changes the value of the field. Note that in that case, the
 action is executed <i>after</i> the model has been updated. However the old
 property value can be retrieved from the context action param.</li>
 </ol></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>forClientTypes</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Sets for client types.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>horizontalAlignment</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EHorizontalAlignment.html">EHorizontal&#x200B;Alignment</a></code></p></td>
<td><p>This property allows to control the property alignment in views that
 support it. This is either a value of the <code>EHorizontalAlignment</code>
 enum or its equivalent string representation :
 <ul>
 <li><code>LEFT</code> for left alignment</li>
 <li><code>CENTER</code> for center alignment</li>
 <li><code>RIGHT</code> for right alignment</li>
 </ul>
 <p>
 Default value is <code>null</code>, meaning use property type default.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>labelBackground</strong></p><p><code>String</code></p></td>
<td><p>When the property has to be labelled (e.g. in a component view), this
 property defines the background color of the corresponding label. It might
 differ from the field component one. The color must be defined using its
 string hexadecimal representation (<i>0xargb</i> encoded).
 <p>
 Default value is <code>null</code>, meaning use UI default.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>labelFont</strong></p><p><code>String</code></p></td>
<td><p>When the property has to be labelled (e.g. in a component view), this
 property defines the font of the corresponding label. It might differ from
 the field component one. The font must be string encoded using the pattern
 <b>&quot;[name];[style];[size]&quot;</b> :
 <ul>
 <li><b>[name]</b> is the name of the font, e.g. <i>arial</i>.</li>
 <li><b>[style]</b> is PLAIN, BOLD, ITALIC or a union of BOLD and ITALIC
 combined with the '|' character, e.g. <i>BOLD|ITALIC</i>.</li>
 <li><b>[size]</b> is the size of the font, e.g. <i>10</i>.</li>
 </ul>
 Any of the above pattern section can be left empty, thus falling back to
 the component default.
 <p>
 Default value is <code>null</code>, meaning use default component font.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>labelForeground</strong></p><p><code>String</code></p></td>
<td><p>When the property has to be labelled (e.g. in a component view), this
 property defines the foreground color of the corresponding label. It might
 differ from the field component one. The color must be defined using its
 string hexadecimal representation (<i>0xargb</i> encoded).
 <p>
 Default value is <code>null</code>, meaning use UI default.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>labelHorizontalPosition</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EHorizontalPosition.html">EHorizontal&#x200B;Position</a></code></p></td>
<td><p>Configures the label horizontal position. There are special cases when the default label position has to be
 overridden. This is either a value of the <code>EHorizontalPosition</code>
 enum or its equivalent string representation :
 <ul>
 <li><code>LEFT</code> for left position</li>
 <li><code>RIGHT</code> for right position</li>
 </ul>
 <p>
 Default value is <code>LEFT</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>renderedChildProperties</strong></p><p><code>List&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Whenever the property descriptor backing the view is not scalar, this
 property allows to override which of the referenced component fields should
 be displayed :
 <ul>
 <li>as columns when the rendered property is a collection property</li>
 <li>as fields when the rendered property is a reference property</li>
 </ul>
 The property must be configured with a <code>List</code> containing the
 property names to render for the child element(s).
 <p>
 A <code>null</code> value (default), means that the non-scalar property
 will be rendered using default rendered properties as specified in its
 referenced model descriptor.
 <p>
 Please note that this is quite unusual to embed non-scalar properties
 directly in a property view. Although permitted, you won't have as much
 flexibility in the content layouting as you would have when using composite
 views; so the latter is by far recommended.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>sortable</strong></p><p><code>boolean</code></p></td>
<td><p>Configure the sortability of a property view when used to defines a table
 column for instance. Whenever it is not explicitly set, it falls back to
 the model property sortability. If no model descriptor is set, defaults to
 <code>true</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>width</strong></p><p><code>Integer</code></p></td>
<td><p>When the property has to be displayed in a grid-like layout (e.g. in a
 component view), this property defines the umber of grid columns the
 corresponding UI component will span.
 <p>
 Default value is <code>null</code>, meaning use default span of 1.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicEnumerationPropertyViewDescriptor"></a>BasicEnumerationPropertyViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicEnumerationPropertyViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicEnumerationPropertyViewDescriptor.html)
+ **Super-type** : [`BasicPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor)



This specialized property view descriptor is used in order to be able to
 refine the &quot;values&quot; that are taken from the model enumeration. You
 can configure a set of allowed values from which the user can choose.



<table>
<caption>BasicEnumerationPropertyViewDescriptor properties</caption>
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
<td align="left"><p><strong>allowedValues</strong></p><p><code>Set&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Returns an optional forbidden set of values to restrict the model ones.
 Only values belonging to the allowed ones should actually be made available
 as a choice.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>enumIconDimension</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/util/gui/Dimension.html">Dimension</a></code></p></td>
<td><p>Sets the icon dimension.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>enumIconHeight</strong></p><p><code>int</code></p></td>
<td><p>Sets the enumeration icon height.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>enumIconWidth</strong></p><p><code>int</code></p></td>
<td><p>Sets the enumeration icon width.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>forbiddenValues</strong></p><p><code>Set&#x200B;&lt;&#x200B;String&#x200B;&gt;&#x200B;</code></p></td>
<td><p>Returns an optional forbidden set of values to restrict the model ones.
 Only values not belonging to the forbidden ones should actually be made
 available as a choice.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>orientation</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/EOrientation.html">EOrientation</a></code></p></td>
<td><p>Configures whether radio values be rendered horizontally or vertically.
 <code>HORIZONTAL</code> if radio values should be rendered horizontally and
 <code>VERTICAL</code> otherwise. Default value is <code>VERTICAL</code>.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>radio</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the rendering of the enumeration property as radio buttons if
 supported instead of combo box. Default value is <code>false</code>.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicHtmlViewDescriptor"></a>BasicHtmlViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicHtmlViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicHtmlViewDescriptor.html)
+ **Super-type** : [`BasicPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor)



This type of view descriptor is used to display a a string property
 containing HTML text. The objective is to be able to configure scrollability
 of the HTML component.



<table>
<caption>BasicHtmlViewDescriptor properties</caption>
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
<td align="left"><p><strong>horizontallyScrollable</strong></p><p><code>boolean</code></p></td>
<td><p>Sets the horizontallyScrollable.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>verticallyScrollable</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the view to be either vertically cropped or scrollable when the
 display area is too small to display it.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicImageViewDescriptor"></a>BasicImageViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicImageViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicImageViewDescriptor.html)
+ **Super-type** : [`BasicPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor)



This type of view descriptor is used to display a binary property or a string
 property containing an URL as an image. By default, binary properties are
 rendered as button fields that allow to upload, download and query size of
 the binary content. This button field visually indicate whether the binary
 property is empty or not. Whenever you know that the underlying property is
 used to store image content, you can explicitly define an image view backed
 by the binary property descriptor and use it in your UI. Jspresso will then
 display the image whose content is stored in the binary property directly in
 the UI.



<table>
<caption>BasicImageViewDescriptor properties</caption>
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
<td align="left"><p><strong>drawable</strong></p><p><code>boolean</code></p></td>
<td><p>Configures whether this image view can be modified by the user drawing in the screen,
 e.g. a POD signature. Defaults to <code>false</code>.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scaledHeight</strong></p><p><code>Integer</code></p></td>
<td><p>Sets scaled height. This property, when set to a positive integer will force the image height to be resized to the
 target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect
 ratio.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>scaledWidth</strong></p><p><code>Integer</code></p></td>
<td><p>Sets scaled width. This property, when set to a positive integer will force the image width to be resized to the
 target value. If only one of the 2 scaled dimensions is set, then the image is scaled by preserving its aspect
 ratio.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>scrollable</strong></p><p><code>boolean</code></p></td>
<td><p>Configures the image view to be either cropped or scrollable when the
 display area is too small to display it. A value of <code>true</code>
 (default) means that the image view will be made scrollable.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicStringPropertyViewDescriptor"></a>BasicStringPropertyViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicStringPropertyViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicStringPropertyViewDescriptor.html)
+ **Super-type** : [`BasicPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicPropertyViewDescriptor)
+ **Sub-types** : [`BasicReferencePropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicReferencePropertyViewDescriptor)



This type of view descriptor is used to display a a string property.
 The objective is to be able to configure an action bound to character typing.



<table>
<caption>BasicStringPropertyViewDescriptor properties</caption>
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
<td align="left"><p><strong>characterAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Configures an action that gets triggered every time the text is changed in the field.</p></td>
</tr>
</tbody>
</table>

---


#### <a name="org.jspresso.framework.view.descriptor.basic.BasicReferencePropertyViewDescriptor"></a>BasicReferencePropertyViewDescriptor

+ **Full name** : [`org.jspresso.framework.view.descriptor.basic.BasicReferencePropertyViewDescriptor`](http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/descriptor/basic/BasicReferencePropertyViewDescriptor.html)
+ **Super-type** : [`BasicStringPropertyViewDescriptor`](#org.jspresso.framework.view.descriptor.basic.BasicStringPropertyViewDescriptor)



This specialized property view descriptor is used in order to be able to
 refine the &quot;List of values&quot; action that gets automatically
 installed by Jspresso when a reference property is displayed. You can then
 customize this action when defining the corresponding column in a table view
 or field in a component view.



<table>
<caption>BasicReferencePropertyViewDescriptor properties</caption>
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
<td align="left"><p><strong>autoCompleteEnabled</strong></p><p><code>boolean</code></p></td>
<td><p>Sets auto complete enabled. I set to <code>false</code>, then the field will always be read-only whereas the LOV
 action button will follow enabled / disabled rules.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>lovAction</strong></p><p><code><a href="http://www.jspresso.org/external/maven-site/apidocs/org/jspresso/framework/view/action/IDisplayableAction.html">IDisplayable&#x200B;Action</a></code></p></td>
<td><p>Allows to override the default &quot;List of values&quot; action attached
 to this reference property view.
 <p/>
 A <code>null</code> value (default) keeps the standard action.</p></td>
</tr>
</tbody>
</table>

---


