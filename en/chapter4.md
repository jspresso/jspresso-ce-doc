# Actions

<!-- toc -->

# Overview

![Actions class diagram](../uml/actions.PNG)

# Common part

## Reference

!INCLUDE "../generated/AbstractActionContextAware.md"

!INCLUDE "../generated/ActionMap.md"

!INCLUDE "../generated/ActionList.md"

# Backend actions

## Reference

!INCLUDE "../generated/BackendAction.md"

# Frontend actions

## Reference

!INCLUDE "../generated/FrontendAction.md"

# Built-in actions

You will find here the complete list of Jspresso built-in actions along
with their Spring id and a short description.

<table>
<caption>Built-in actions</caption>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Spring Id</th>
<th align="left">SJS Id</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">pasteCollectionBackAction</td>
<td align="left">back.component.paste</td>
<td align="left">Pastes entities/components from the application clipboard.</td>
</tr>
<tr class="even">
<td align="left">removeCollectionFromMasterBackAction</td>
<td align="left">back.component.remove</td>
<td align="left">Marks the selected objects for deletion (next save operation) and removes them from the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">saveBackAction</td>
<td align="left">back.component.save</td>
<td align="left">Gets a collection of entities to save out of the context and saves them transactionally.</td>
</tr>
<tr class="even">
<td align="left">createQueryComponentAction</td>
<td align="left">back.filter.create</td>
<td align="left">Creates a filter model for QBE queries and set it as value of the filter model connector retrieved from the context.</td>
</tr>
<tr class="odd">
<td align="left">initModuleFilterAction</td>
<td align="left">back.filter.init</td>
<td align="left">Retrieves the current module filter connector and adds it in the context.</td>
</tr>
<tr class="even">
<td align="left">queryEntitiesBackAction</td>
<td align="left">back.filter.query</td>
<td align="left">Executes an QBE query based on a filter retrieved from the context. The resulting entity collection is added to the context.</td>
</tr>
<tr class="odd">
<td align="left">reloadBackAction</td>
<td align="left">back.module.reload</td>
<td align="left">Reloads current module selected objects from the persistent store.</td>
</tr>
<tr class="even">
<td align="left">removeFromModuleObjectsAction</td>
<td align="left">back.module.remove</td>
<td align="left">Marks current module selected objects for deletion (next save operation) and removes them from the module managed collection.</td>
</tr>
<tr class="odd">
<td align="left">saveModuleObjectBackAction</td>
<td align="left">back.module.save</td>
<td align="left">Saves the current module selected objects to the persistent store.</td>
</tr>
<tr class="even">
<td align="left">doPrintBackendAction</td>
<td align="left">back.report.generate</td>
<td align="left">Generates a Jasper report and adds it to the context.</td>
</tr>
<tr class="odd">
<td align="left">scriptedBackAction</td>
<td align="left">back.script.dynamic</td>
<td align="left">Executes a script taken out of the context. Supports any BSF supported language (Groovy, Jython, Beanshell, ...).</td>
</tr>
<tr class="even">
<td align="left">staticScriptedBackAction</td>
<td align="left">back.script.static</td>
<td align="left">Executes a script statically defined as an action parameter. Supports any BSF supported language (Groovy, Jython, Beanshell, ...).</td>
</tr>
<tr class="odd">
<td align="left">lovFindBackAction</td>
<td align="left">back.lov.find</td>
<td align="left">Standard QBE find action for &quot;list of values&quot;.</td>
</tr>
<tr class="even">
<td align="left">abstractChooseActionAction</td>
<td align="left">front.action.choose</td>
<td align="left">Opens a modal dialog box offering a choice of actions.</td>
</tr>
<tr class="odd">
<td align="left">executeActionAction</td>
<td align="left">front.action.execute</td>
<td align="left">Takes an action out of the context and executes it.</td>
</tr>
<tr class="even">
<td align="left">chooseActionOkFrontAction</td>
<td align="left">front.action.ok</td>
<td align="left">Gets the selected action and places it in the context for execution.</td>
</tr>
<tr class="odd">
<td align="left">addAnyToMasterFrontAction</td>
<td align="left">front.any.add</td>
<td align="left">Retrieves an object collection from the context and appends it to the master managed collection (no creation).</td>
</tr>
<tr class="even">
<td align="left">moveDownFrontAction</td>
<td align="left">front.any.down</td>
<td align="left">Moves downward the selected objects contained in an ordered collection.</td>
</tr>
<tr class="odd">
<td align="left">moveBottomFrontAction</td>
<td align="left">front.any.bottom</td>
<td align="left">Moves bottom the selected objects contained in an ordered collection.</td>
</tr>
<tr class="even">
<td align="left">removeAnyCollectionFromMasterFrontAction</td>
<td align="left">front.any.remove</td>
<td align="left">After user confirmation, retrieves an object collection from the context and removes it from the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">moveUpFrontAction</td>
<td align="left">front.any.up</td>
<td align="left">Moves upward the selected objects contained in an ordered collection.</td>
</tr>
<tr class="even">
<td align="left">moveTopFrontAction</td>
<td align="left">front.any.top</td>
<td align="left">Moves top the selected objects contained in an ordered collection.</td>
</tr>
<tr class="odd">
<td align="left">binaryPropertyInfoAction</td>
<td align="left">front.binary.info</td>
<td align="left">Retrieves a binary property value out of the connector and opens a message box displaying the size of the binary content.</td>
</tr>
<tr class="even">
<td align="left">openFileAsBinaryPropertyAction</td>
<td align="left">front.binary.load</td>
<td align="left">Let the user browse the local file system to choose a file. The file content is used as the content of a binary property.</td>
</tr>
<tr class="odd">
<td align="left">saveBinaryPropertyAsFileAction</td>
<td align="left">front.binary.save</td>
<td align="left">Let the user browse the local file system to choose a file. The file is used to save the content of a binary property.</td>
</tr>
<tr class="even">
<td align="left">chartAction</td>
<td align="left">front.chart</td>
<td align="left">Computes and displays a fusioncharts chart.</td>
</tr>
<tr class="odd">
<td align="left">abstractAddToMasterFrontAction</td>
<td align="left">front.component.add.abstract</td>
<td align="left">Creates a new entity/component and adds it to the master managed collection. No icon nor accelerator set.</td>
</tr>
<tr class="even">
<td align="left">addToMasterFrontAction</td>
<td align="left">front.component.add</td>
<td align="left">Creates a new entity/component and adds it to the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">chooseComponentAction</td>
<td align="left">front.component.choose</td>
<td align="left">Opens a modal dialog to let the user choose an component/entity out of a collection retrieved from the context.</td>
</tr>
<tr class="even">
<td align="left">cloneEntityCollectionFrontAction</td>
<td align="left">front.component.clone</td>
<td align="left">Duplicates selected entities/components and adds the clones to the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">copyCollectionFrontAction</td>
<td align="left">front.component.copy</td>
<td align="left">Copies the selected entities/components to the application clipboard.</td>
</tr>
<tr class="even">
<td align="left">cutCollectionFrontAction</td>
<td align="left">front.component.cut</td>
<td align="left">Cuts the selected entities/components to the application clipboard.</td>
</tr>
<tr class="odd">
<td align="left">editSelectedComponentAction</td>
<td align="left">front.selected.edit</td>
<td align="left">Opens a dialog box to edit the selected entity/component in an arbitrary view.</td>
</tr>
<tr class="even">
<td align="left">editComponentAction</td>
<td align="left">front.component.edit</td>
<td align="left">Opens a dialog box to edit an entity/component in an arbitrary view.</td>
</tr>
<tr class="odd">
<td align="left">pasteCollectionFrontAction</td>
<td align="left">front.component.paste</td>
<td align="left">Pastes entities/components from the application clipboard.</td>
</tr>
<tr class="even">
<td align="left">removeEntityCollectionFromMasterFrontAction</td>
<td align="left">front.component.remove</td>
<td align="left">After user confirmation, marks the selected objects for deletion (next save operation) and removes them from the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">viewConnectorSetAction</td>
<td align="left">front.connector.set</td>
<td align="left">Retrieves an arbitrary value from the context and assigns it to the view connector value.</td>
</tr>
<tr class="even">
<td align="left">okDialogFrontAction</td>
<td align="left">front.dialog.ok</td>
<td align="left">Closes the top most dialog. Icon and name set.</td>
</tr>
<tr class="odd">
<td align="left">cancelDialogFrontAction</td>
<td align="left">front.dialog.cancel</td>
<td align="left">Closes the top most dialog. Icon and name set.</td>
</tr>
<tr class="even">
<td align="left">closeDialogAction</td>
<td align="left">front.dialog.close</td>
<td align="left">Closes the top most dialog.</td>
</tr>
<tr class="odd">
<td align="left">modalDialogAction</td>
<td align="left">front.dialog.open</td>
<td align="left">Opens a modal dialog box that is parametrized out of context values (title, view bound to its model, size, secondary action list).</td>
</tr>
<tr class="even">
<td align="left">openFileAction</td>
<td align="left">front.file.open</td>
<td align="left">Let the user browse the local file system to choose a file. The selected file content is placed in the context.</td>
</tr>
<tr class="odd">
<td align="left">saveFileAction</td>
<td align="left">front.file.save</td>
<td align="left">Let the user browse the local file system to choose a file. The selected file is used to save an arbitrary content taken from the context.</td>
</tr>
<tr class="even">
<td align="left">nextModuleFilterPageAction</td>
<td align="left">front.filter.next</td>
<td align="left">Moves to the next result page of a filtered module.</td>
</tr>
<tr class="odd">
<td align="left">previousModuleFilterPageAction</td>
<td align="left">front.filter.previous</td>
<td align="left">Moves to the previous result page of a filtered module.</td>
</tr>
<tr class="even">
<td align="left">queryModuleFilterAction</td>
<td align="left">front.filter.query</td>
<td align="left">Performs the QBE query of a filtered module.</td>
</tr>
<tr class="odd">
<td align="left">infoFrontAction</td>
<td align="left">front.info.dynamic</td>
<td align="left">Retrieves an information message from the context and displays it to the user.</td>
</tr>
<tr class="even">
<td align="left">staticInfoFrontAction</td>
<td align="left">front.info.static</td>
<td align="left">Translates an information message statically parametrized in the action and displays it to the user.</td>
</tr>
<tr class="odd">
<td align="left">lovAction</td>
<td align="left">front.lov</td>
<td align="left">Pops-up a &quot;list of values&quot; dialog.</td>
</tr>
<tr class="even">
<td align="left">lovFindFrontAction</td>
<td align="left">front.lov.find</td>
<td align="left">Performs the QBE query of a &quot;list of values&quot;.</td>
</tr>
<tr class="odd">
<td align="left">nextLovPageFrontAction</td>
<td align="left">front.lov.next</td>
<td align="left">Moves to the next result page of a &quot;list of values&quot;.</td>
</tr>
<tr class="even">
<td align="left">lovOkFrontAction</td>
<td align="left">front.lov.ok</td>
<td align="left">Gets the selected result from a &quot;list of values&quot; and places it in the context.</td>
</tr>
<tr class="odd">
<td align="left">previousLovPageFrontAction</td>
<td align="left">front.lov.previous</td>
<td align="left">Moves to the previous result page of a &quot;list of values&quot;.</td>
</tr>
<tr class="even">
<td align="left">addMapToMasterFrontAction</td>
<td align="left">front.map.add</td>
<td align="left">Creates a new map and adds it to the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">cloneMapCollectionFrontAction</td>
<td align="left">front.map.clone</td>
<td align="left">Duplicates selected maps and adds the clones to the master managed collection.</td>
</tr>
<tr class="even">
<td align="left">cloneMapCollectionFrontAction</td>
<td align="left">front.map.clone</td>
<td align="left">Duplicates selected maps and adds the clones to the master managed collection.</td>
</tr>
<tr class="odd">
<td align="left">cloneModuleObjectFrontAction</td>
<td align="left">front.module.clone</td>
<td align="left">Duplicates selected entities/components and adds the clones to the module managed collection.</td>
</tr>
<tr class="even">
<td align="left">reloadModuleObjectFrontAction</td>
<td align="left">front.module.reload</td>
<td align="left">Reloads the module selected entity/component from the persistent store. entities/components previously marked for deletion are also restored.</td>
</tr>
<tr class="odd">
<td align="left">removeFromModuleObjectFrontAction</td>
<td align="left">front.module.remove</td>
<td align="left">After user confirmation, marks the selected module entities/components for deletion (next save operation) and removes them from the module managed collection.</td>
</tr>
<tr class="even">
<td align="left">restartModuleFrontAction</td>
<td align="left">front.module.reset</td>
<td align="left">Restarts the current module.</td>
</tr>
<tr class="odd">
<td align="left">saveModuleObjectFrontAction</td>
<td align="left">front.module.save</td>
<td align="left">Saves the module selected entities/components to the persistent store and performs deletion of previously &quot;marked for deletion&quot; entities/components.</td>
</tr>
<tr class="even">
<td align="left">saveModuleObjectAndGoBackFrontAction</td>
<td align="left">front.module.save.back</td>
<td align="left">Saves the module selected entities/components to the persistent store and performs deletion of previously &quot;marked for deletion&quot; entities/components. If successful, returns back to the parent module.</td>
</tr>
<tr class="odd">
<td align="left">parentModuleConnectorSelectionFrontAction</td>
<td align="left">front.module.back</td>
<td align="left">Returns back to the parent module.</td>
</tr>
<tr class="even">
<td align="left">moduleConnectorSelectionFrontAction</td>
<td align="left">front.module.select</td>
<td align="left">Gets a module out or the context and selects it in the current workspace.</td>
</tr>
<tr class="odd">
<td align="left">addAsChildModuleFrontAction</td>
<td align="left">front.module.sub</td>
<td align="left">Gets selected module objects, adds them as current module children then selects them.</td>
</tr>
<tr class="even">
<td align="left">nextPinnedModuleAction</td>
<td align="left">front.module.next</td>
<td align="left">Navigates to the next pinned module in history.</td>
</tr>
<tr class="odd">
<td align="left">previousPinnedModuleAction</td>
<td align="left">front.module.previous</td>
<td align="left">Navigates to the previous pinned module in history.</td>
</tr>
<tr class="even">
<td align="left">okCancelFrontAction</td>
<td align="left">front.okcancel.dynamic</td>
<td align="left">Retrieves an ok/cancel message out of the context and displays it to the user.</td>
</tr>
<tr class="odd">
<td align="left">staticOkCancelFrontAction</td>
<td align="left">front.okcancel.static</td>
<td align="left">Retrieves an ok/cancel message statically parametrized in the action and displays it to the user.</td>
</tr>
<tr class="even">
<td align="left">changePasswordAction</td>
<td align="left">front.password.change</td>
<td align="left">Opens a dialog box allowing the user to initiate a password change operation (old, new, check).</td>
</tr>
<tr class="odd">
<td align="left">printOkFrontAction</td>
<td align="left">front.print.ok</td>
<td align="left">Retrieves the selected Jasper report and puts it in the context for display/print.</td>
</tr>
<tr class="even">
<td align="left">resetPropertyFrontAction</td>
<td align="left">front.property.reset</td>
<td align="left">Resets a property to its default value.</td>
</tr>
<tr class="odd">
<td align="left">displayReportAction</td>
<td align="left">front.report.display</td>
<td align="left">Displays/prints a Jasper report taken out of the context to the user.</td>
</tr>
<tr class="even">
<td align="left">reportAction</td>
<td align="left">front.report.dynamic</td>
<td align="left">Retrieves a Jasper report definition out of the context, opens the report parameters entry dialog, then triggers generation and display/print.</td>
</tr>
<tr class="odd">
<td align="left">editReportParametersAction</td>
<td align="left">front.report.edit</td>
<td align="left">Opens a dialog box for the user to input a Jasper report parameters.</td>
</tr>
<tr class="even">
<td align="left">doPrintAction</td>
<td align="left">front.report.print</td>
<td align="left">Triggers generation and display/print of a Jasper report after parameters input.</td>
</tr>
<tr class="odd">
<td align="left">staticReportAction</td>
<td align="left">front.report.static</td>
<td align="left">Gets a Jasper report definition statically defined as an action parameter, opens the report parameters entry dialog, then triggers generation and display/print.</td>
</tr>
<tr class="even">
<td align="left">displayUrlFrontAction</td>
<td align="left">front.url.dynamic</td>
<td align="left">Targets the browser (actually a new browser window/tab) to a URL retrieved from the context.</td>
</tr>
<tr class="odd">
<td align="left">staticDisplayUrlFrontAction</td>
<td align="left">front.url.static</td>
<td align="left">Targets the browser (actually a new browser window/tab) to a URL statically defined as an action parameter. The URL is previously translated so thant it can be variabilized based on the user language (used for online help for instance).</td>
</tr>
<tr class="even">
<td align="left">connectorSelectionFrontAction</td>
<td align="left">front.view.select</td>
<td align="left">Retrieves an object collection out of the context and selects it on the collection view (table, list, tree).</td>
</tr>
<tr class="odd">
<td align="left">wizardAction</td>
<td align="left">front.wizard</td>
<td align="left">Triggers a wizard dialog.</td>
</tr>
<tr class="even">
<td align="left">yesNoFrontAction</td>
<td align="left">front.yesno.dynamic</td>
<td align="left">Retrieves a yes/no binary question out of the context and displays it to the user.</td>
</tr>
<tr class="odd">
<td align="left">staticYesNoFrontAction</td>
<td align="left">front.yesno.static</td>
<td align="left">Retrieves a yes/no binary question statically parametrized in the action and displays it to the user.</td>
</tr>
<tr class="even">
<td align="left">yesNoCancelFrontAction</td>
<td align="left">front.yesnocancel.dynamic</td>
<td align="left">Retrieves a yes/no/cancel binary question out of the context and displays it to the user.</td>
</tr>
<tr class="odd">
<td align="left">staticYesNoCancelFrontAction</td>
<td align="left">front.yesnocancel.static</td>
<td align="left">Retrieves a yes/no/cancel binary question statically parametrized in the action and displays it to the user.</td>
</tr>
</tbody>
</table>

---