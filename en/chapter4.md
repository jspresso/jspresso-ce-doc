Actions
=======

<!-- toc -->

Overview
========

![Actions class diagram](../uml/actions.PNG)

Common part
===========

Reference
---------

Backend actions
===============

Reference
---------

Frontend actions
================

Reference
---------

Built-in actions
================

You will find here the complete list of Jspresso built-in actions along
with their Spring id and a short description.

  --------------------------------------------------------------------------
  Spring Id          SJS Id             Description
  ------------------ ------------------ ------------------------------------
  pasteCollectionBac back.component.pas Pastes entities/components from the
  kAction            te                 application clipboard.

  removeCollectionFr back.component.rem Marks the selected objects for
  omMasterBackAction ove                deletion (next save operation) and
                                        removes them from the master managed
                                        collection.

  saveBackAction     back.component.sav Gets a collection of entities to
                     e                  save out of the context and saves
                                        them transactionally.

  createQueryCompone back.filter.create Creates a filter model for QBE
  ntAction                              queries and set it as value of the
                                        filter model connector retrieved
                                        from the context.

  initModuleFilterAc back.filter.init   Retrieves the current module filter
  tion                                  connector and adds it in the
                                        context.

  queryEntitiesBackA back.filter.query  Executes an QBE query based on a
  ction                                 filter retrieved from the context.
                                        The resulting entity collection is
                                        added to the context.

  reloadBackAction   back.module.reload Reloads current module selected
                                        objects from the persistent store.

  removeFromModuleOb back.module.remove Marks current module selected
  jectsAction                           objects for deletion (next save
                                        operation) and removes them from the
                                        module managed collection.

  saveModuleObjectBa back.module.save   Saves the current module selected
  ckAction                              objects to the persistent store.

  doPrintBackendActi back.report.genera Generates a Jasper report and adds
  on                 te                 it to the context.

  scriptedBackAction back.script.dynami Executes a script taken out of the
                     c                  context. Supports any BSF supported
                                        language (Groovy, Jython, Beanshell,
                                        ...).

  staticScriptedBack back.script.static Executes a script statically defined
  Action                                as an action parameter. Supports any
                                        BSF supported language (Groovy,
                                        Jython, Beanshell, ...).

  lovFindBackAction  back.lov.find      Standard QBE find action for "list
                                        of values".

  abstractChooseActi front.action.choos Opens a modal dialog box offering a
  onAction           e                  choice of actions.

  executeActionActio front.action.execu Takes an action out of the context
  n                  te                 and executes it.

  chooseActionOkFron front.action.ok    Gets the selected action and places
  tAction                               it in the context for execution.

  addAnyToMasterFron front.any.add      Retrieves an object collection from
  tAction                               the context and appends it to the
                                        master managed collection (no
                                        creation).

  moveDownFrontActio front.any.down     Moves downward the selected objects
  n                                     contained in an ordered collection.

  moveBottomFrontAct front.any.bottom   Moves bottom the selected objects
  ion                                   contained in an ordered collection.

  removeAnyCollectio front.any.remove   After user confirmation, retrieves
  nFromMasterFrontAc                    an object collection from the
  tion                                  context and removes it from the
                                        master managed collection.

  moveUpFrontAction  front.any.up       Moves upward the selected objects
                                        contained in an ordered collection.

  moveTopFrontAction front.any.top      Moves top the selected objects
                                        contained in an ordered collection.

  binaryPropertyInfo front.binary.info  Retrieves a binary property value
  Action                                out of the connector and opens a
                                        message box displaying the size of
                                        the binary content.

  openFileAsBinaryPr front.binary.load  Let the user browse the local file
  opertyAction                          system to choose a file. The file
                                        content is used as the content of a
                                        binary property.

  saveBinaryProperty front.binary.save  Let the user browse the local file
  AsFileAction                          system to choose a file. The file is
                                        used to save the content of a binary
                                        property.

  chartAction        front.chart        Computes and displays a fusioncharts
                                        chart.

  abstractAddToMaste front.component.ad Creates a new entity/component and
  rFrontAction       d.abstract         adds it to the master managed
                                        collection. No icon nor accelerator
                                        set.

  addToMasterFrontAc front.component.ad Creates a new entity/component and
  tion               d                  adds it to the master managed
                                        collection.

  chooseComponentAct front.component.ch Opens a modal dialog to let the user
  ion                oose               choose an component/entity out of a
                                        collection retrieved from the
                                        context.

  cloneEntityCollect front.component.cl Duplicates selected
  ionFrontAction     one                entities/components and adds the
                                        clones to the master managed
                                        collection.

  copyCollectionFron front.component.co Copies the selected
  tAction            py                 entities/components to the
                                        application clipboard.

  cutCollectionFront front.component.cu Cuts the selected
  Action             t                  entities/components to the
                                        application clipboard.

  editSelectedCompon front.selected.edi Opens a dialog box to edit the
  entAction          t                  selected entity/component in an
                                        arbitrary view.

  editComponentActio front.component.ed Opens a dialog box to edit an
  n                  it                 entity/component in an arbitrary
                                        view.

  pasteCollectionFro front.component.pa Pastes entities/components from the
  ntAction           ste                application clipboard.

  removeEntityCollec front.component.re After user confirmation, marks the
  tionFromMasterFron move               selected objects for deletion (next
  tAction                               save operation) and removes them
                                        from the master managed collection.

  viewConnectorSetAc front.connector.se Retrieves an arbitrary value from
  tion               t                  the context and assigns it to the
                                        view connector value.

  okDialogFrontActio front.dialog.ok    Closes the top most dialog. Icon and
  n                                     name set.

  cancelDialogFrontA front.dialog.cance Closes the top most dialog. Icon and
  ction              l                  name set.

  closeDialogAction  front.dialog.close Closes the top most dialog.

  modalDialogAction  front.dialog.open  Opens a modal dialog box that is
                                        parametrized out of context values
                                        (title, view bound to its model,
                                        size, secondary action list).

  openFileAction     front.file.open    Let the user browse the local file
                                        system to choose a file. The
                                        selected file content is placed in
                                        the context.

  saveFileAction     front.file.save    Let the user browse the local file
                                        system to choose a file. The
                                        selected file is used to save an
                                        arbitrary content taken from the
                                        context.

  nextModuleFilterPa front.filter.next  Moves to the next result page of a
  geAction                              filtered module.

  previousModuleFilt front.filter.previ Moves to the previous result page of
  erPageAction       ous                a filtered module.

  queryModuleFilterA front.filter.query Performs the QBE query of a filtered
  ction                                 module.

  infoFrontAction    front.info.dynamic Retrieves an information message
                                        from the context and displays it to
                                        the user.

  staticInfoFrontAct front.info.static  Translates an information message
  ion                                   statically parametrized in the
                                        action and displays it to the user.

  lovAction          front.lov          Pops-up a "list of values" dialog.

  lovFindFrontAction front.lov.find     Performs the QBE query of a "list of
                                        values".

  nextLovPageFrontAc front.lov.next     Moves to the next result page of a
  tion                                  "list of values".

  lovOkFrontAction   front.lov.ok       Gets the selected result from a
                                        "list of values" and places it in
                                        the context.

  previousLovPageFro front.lov.previous Moves to the previous result page of
  ntAction                              a "list of values".

  addMapToMasterFron front.map.add      Creates a new map and adds it to the
  tAction                               master managed collection.

  cloneMapCollection front.map.clone    Duplicates selected maps and adds
  FrontAction                           the clones to the master managed
                                        collection.

  cloneMapCollection front.map.clone    Duplicates selected maps and adds
  FrontAction                           the clones to the master managed
                                        collection.

  cloneModuleObjectF front.module.clone Duplicates selected
  rontAction                            entities/components and adds the
                                        clones to the module managed
                                        collection.

  reloadModuleObject front.module.reloa Reloads the module selected
  FrontAction        d                  entity/component from the persistent
                                        store. entities/components
                                        previously marked for deletion are
                                        also restored.

  removeFromModuleOb front.module.remov After user confirmation, marks the
  jectFrontAction    e                  selected module entities/components
                                        for deletion (next save operation)
                                        and removes them from the module
                                        managed collection.

  restartModuleFront front.module.reset Restarts the current module.
  Action                                

  saveModuleObjectFr front.module.save  Saves the module selected
  ontAction                             entities/components to the
                                        persistent store and performs
                                        deletion of previously "marked for
                                        deletion" entities/components.

  saveModuleObjectAn front.module.save. Saves the module selected
  dGoBackFrontAction back               entities/components to the
                                        persistent store and performs
                                        deletion of previously "marked for
                                        deletion" entities/components. If
                                        successful, returns back to the
                                        parent module.

  parentModuleConnec front.module.back  Returns back to the parent module.
  torSelectionFrontA                    
  ction                                 

  moduleConnectorSel front.module.selec Gets a module out or the context and
  ectionFrontAction  t                  selects it in the current workspace.

  addAsChildModuleFr front.module.sub   Gets selected module objects, adds
  ontAction                             them as current module children then
                                        selects them.

  nextPinnedModuleAc front.module.next  Navigates to the next pinned module
  tion                                  in history.

  previousPinnedModu front.module.previ Navigates to the previous pinned
  leAction           ous                module in history.

  okCancelFrontActio front.okcancel.dyn Retrieves an ok/cancel message out
  n                  amic               of the context and displays it to
                                        the user.

  staticOkCancelFron front.okcancel.sta Retrieves an ok/cancel message
  tAction            tic                statically parametrized in the
                                        action and displays it to the user.

  changePasswordActi front.password.cha Opens a dialog box allowing the user
  on                 nge                to initiate a password change
                                        operation (old, new, check).

  printOkFrontAction front.print.ok     Retrieves the selected Jasper report
                                        and puts it in the context for
                                        display/print.

  resetPropertyFront front.property.res Resets a property to its default
  Action             et                 value.

  displayReportActio front.report.displ Displays/prints a Jasper report
  n                  ay                 taken out of the context to the
                                        user.

  reportAction       front.report.dynam Retrieves a Jasper report definition
                     ic                 out of the context, opens the report
                                        parameters entry dialog, then
                                        triggers generation and
                                        display/print.

  editReportParamete front.report.edit  Opens a dialog box for the user to
  rsAction                              input a Jasper report parameters.

  doPrintAction      front.report.print Triggers generation and
                                        display/print of a Jasper report
                                        after parameters input.

  staticReportAction front.report.stati Gets a Jasper report definition
                     c                  statically defined as an action
                                        parameter, opens the report
                                        parameters entry dialog, then
                                        triggers generation and
                                        display/print.

  displayUrlFrontAct front.url.dynamic  Targets the browser (actually a new
  ion                                   browser window/tab) to a URL
                                        retrieved from the context.

  staticDisplayUrlFr front.url.static   Targets the browser (actually a new
  ontAction                             browser window/tab) to a URL
                                        statically defined as an action
                                        parameter. The URL is previously
                                        translated so thant it can be
                                        variabilized based on the user
                                        language (used for online help for
                                        instance).

  connectorSelection front.view.select  Retrieves an object collection out
  FrontAction                           of the context and selects it on the
                                        collection view (table, list, tree).

  wizardAction       front.wizard       Triggers a wizard dialog.

  yesNoFrontAction   front.yesno.dynami Retrieves a yes/no binary question
                     c                  out of the context and displays it
                                        to the user.

  staticYesNoFrontAc front.yesno.static Retrieves a yes/no binary question
  tion                                  statically parametrized in the
                                        action and displays it to the user.

  yesNoCancelFrontAc front.yesnocancel. Retrieves a yes/no/cancel binary
  tion               dynamic            question out of the context and
                                        displays it to the user.

  staticYesNoCancelF front.yesnocancel. Retrieves a yes/no/cancel binary
  rontAction         static             question statically parametrized in
                                        the action and displays it to the
                                        user.
  --------------------------------------------------------------------------

  : Built-in actions


