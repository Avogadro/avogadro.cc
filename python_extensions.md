---
layout: default
title: Python Extensions
---

# Python Extensions

Introduction
============

Extensions are python scripts (or C++ plugins) which expose various actions that can be performed on user request. Unlike tools, extensions don't require any clicking on the GLWidget (the 3D view). Some examples that can be implemented as extension are "Add Hydrogens", "Clear Molecule", "Optimize Geometry", ...

This page assumes you already know how to work with the [Molecule](Python_Molecule "wikilink") and [GLWidget](Python_GLWidget "wikilink") classes.

The following class and method names should be used when writing extensions.

**`class` `Extension(QObject):`**
`  def __init__(self):`
`    QObject.__init__(self)`
`    ... code...`
`  `**`def` `name(self):` `#` `Recommended`**
`    return "My Extension"`
`  `**`def` `description(self):` `#` `Recommended`**
`    return "My Extension does ..."`
`  `**`def` `actions(self):` `#` `Required`**
`    ...code...`
`  `**`def` `performAction(self,` `action,` `glwidget):` `#` `Required`**
`    ...code...`
`  `**`def` `menuPath(self,` `action):` `#` `Optional`**
`    ...code...   `
`  `**`def` `readSettings(self,` `settings):` `#` `Optional`**
`    ...code...`
`  `**`def` `writeSettings(self,` `settings):` `#` `Optional`**
`    ...code...`

How to implement actions and performAction methods is best illustrated with a simple example. The example below returns one action named "Clear Molecule" and can perform this action in the performAction method.

![Figure 1: By default, the action(s) can be found in the menu: Scripts \> ...](Python_extension1.png "Figure 1: By default, the action(s) can be found in the menu: Scripts > ...")

*`#` `PyQt4` `needed` `for` `QObject` `&` `QAction`*
`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
*`#` `import` `the` `Avogadro` `python` `module`*
`import Avogadro `
*`#` `always` `use` `'Extension'` `for` `class` `name`*
**`class` `Extension(QObject):`**
`  `**`def` `__init__(self):`**
`    QObject.__init__(self)`
`  `**`def` `actions(self):`**
`    actions = []`
`    `*`#` `Actions` `are` `just` `instances` `of` `the` `QAction` `class` `from` `PyQt4`*
`    action = QAction(self)`
`    action.setText("Clear molecule")`
`    actions.append(action)`
`    return actions`
`  `**`def` `performAction(self,` `action,` `glwidget):`**
`    `*`#` `Check` `is` `not` `really` `needed` `here` `since` `we` `only` `have` `one` `action.`*
`    `*`#` `Your` `script` `will` `never` `be` `asked` `to` `perform` `an` `action` `it` `didn't` `provide.`*
`    if action.text() == "Clear molecule":`
`      # clear the molecule`
`      glwidget.molecule.clear()`
`    `*`#` `we` `don't` `provide` `a` `QUndoCommand`*`'`
`    return None`

When Avogadro starts (or when python extensions are reloaded), each script's actions() method is called and the actions are by default added to the 'Scripts' menu. In the example above, there is only one action and so the if statement in performAction() could be left out. However, if the extension provides multiple actions, checking the action.text() field is an easy way to determine which action should be performed.

parameters
----------

**def performAction(self, action, glwidget):**

-   action: Instance of [QAction](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qaction.html) class from PyQt4. Script will never be asked to perform an action it didn't provide.
-   glwidget: The current [GLWidget](http://avogadro.openmolecules.net/api/dev/classAvogadro_1_1GLWidget.html).

Debugging Python Extensions
===========================

![Figure 2: All python errors are reported to the "Messages" log](Python extension4.png "Figure 2: All python errors are reported to the "Messages" log")

`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
`import Avogadro `
*`#` `always` `use` `'Extension'` `for` `class` `name`*
**`class` `Extension(QObject):`**
`  `**`def` `__init__(self):`**
`    QObject.__init__(self)`
`  `**`def` `actions(self):`**
`    actions = []`
`    action = QAction(self)`
`    action.setTeeeeeeeeeeeext("Clear molecule")`
`    actions.append(action)`
`    return actions`
`  `*`#` `performAction(...)` `is` `missing...`*

Name and description
====================

Like any python plugin in Avogadro, python extensions can be enabled or disabled using *Settings \> Configure Avogadro...* (Figure 2). To make it easier to identify an extension in the configuration dialog, a name method can be added to the extension. Extensions without a name method will all appear as 'Unknown Python Extension'. Providing a description method is also recommended, the description for the selected extension is displayed in the Details field in Figure 2.

![Figure 3: Define a name() & description() method to help keep track of your scripts.](Python_extension3.png "Figure 3: Define a name() & description() method to help keep track of your scripts.")

`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
`import Avogadro`
*`#` `always` `use` `'Extension'` `for` `class` `name`*
**`class` `Extension(QObject):`**
`  `**`def` `__init__(self):`**
`    QObject.__init__(self)`
`  `**`def` `name(self):`**
`    return "My First Extension"`
`  `**`def` `description(self):`**
`    return "This is my first Avogadro python extension"`
`  `*`#` `implementation` `not` `relevant` `here`*
`  `**`def` `actions(self):`**
`    actions = []`
`    return actions`
`  `*`#` `implementation` `not` `relevent` `here`*
`  `**`def` `performAction(self,` `action,` `glwidget):`**
`    return None`

Changing the menu path
======================

By adding a menuPath() method, the menu path for each action in the extension can be specified. This can be useful to group actions in a more meaningful way.

![Figure 4: Define a menuPath() method to customize your action's menu path.](Python_Extension2.png "Figure 4: Define a menuPath() method to customize your action's menu path.")

`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
`import Avogadro `
*`#` `always` `use` `'Extension'` `for` `class` `name`*
**`class` `Extension(QObject):`**
`  `**`def` `__init__(self):`**
`    QObject.__init__(self)`
`  `**`def` `actions(self):`**
`    actions = []`
`    action = QAction(self)`
`    action.setText("Action 1")`
`    actions.append(action)`
`    action = QAction(self)`
`    action.setText("Action 2")`
`    actions.append(action)`
`    action = QAction(self)`
`    action.setText("Action 3")`
`    actions.append(action)`
`    return actions`
`  `*`#` `dummy` `method` `here`*
`  `**`def` `performAction(self,` `action,` `glwidget):`**
`    return None`
`  `**`def` `menuPath(self,` `action):`**
`    if action.text() == "Action 3":`
`      return "Extra Menu"`
`    else:`
`      return "Extra Menu>Submenu"`

Sometimes it makes more sense to add a specific action to an already existing menu path. When doing this, include an ampersand ('&') character before the letter which is underlined in menu path. For example, if an action should go in the *View* menu path, '&View' should be used. This marking is used for shortcuts, pressing **ALT + V** will open the View menu.

Using QUndoCommand for undo/redo functionality
==============================================

It is not strictly needed to provide undo functionality to your extension. However, it is always nice to be able to undo mistakes. To implement undo-able actions a QUndoCommand derived class is used. In perfromAction, an instance of this class is returned and Avogadro calls the redo() method. When the user presses **Crtl + Z** (or *Edit \> Undo*), the undo method() is called and so on.

It is important to realize commands need to be able to undo/redo actions many times (see comment in undo method).

`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
`import Avogadro`
**`class` `ClearCommand(QUndoCommand):`**
`  `**`def` `__init__(self,` `glwidget):`**
`    QUndoCommand.__init__(self)`
`    `*`#` `store` `the` `glwidget` `for` `use` `in` `undo/redo`*
`    self.glwidget = glwidget`
`    `*`#` `create` `a` `new` `molecule`*
`    self.molCopy = Avogadro.molecules.addMolecule()`
`    `*`#` `make` `a` `copy` `of` `the` `molecule` `for` `undo`*
`    self.molCopy.copy(glwidget.molecule)`
`    `*`#` `set` `the` `command's` `text`*
`    self.setText("Clear Molecule")`
`  `**`def` `redo(self):`**
`    `*`#` `clear` `the` `current` `molecule`*
`    self.glwidget.molecule.clear()`
`  `**`def` `undo(self):`**
`    `*`#` `Restore` `the` `molecule,` `we` `use` `the` `copy` `function` `again`*
`    `*`#` `because` `we` `might` `need` `to` `undo/redo` `multiple` `times.`*
`    `*`#` `If` `we` `just` `set` `the` `current` `molecule` `to` `molCopy,` `the` `next`*
`    `*`#` `redo` `would` `clear` `it` `and` `we` `wouldn't` `have` `a` `valid` `copy`*
`    `*`#` `anymore.`*
`    self.glwidget.molecule.copy(self.molCopy)`
*`#` `always` `use` `'Extension'` `for` `class` `name`*
**`class` `Extension(QObject):`**
`  `**`def` `__init__(self):`**
`    QObject.__init__(self)`
`  `**`def` `actions(self):`**
`    actions = []`
`    action = QAction(self)`
`    action.setText("Clear molecule (Undoable)")`
`    actions.append(action)`
`    return actions`
`  `**`def` `performAction(self,` `action,` `glwidget):`**
`    `*`#` `return` `the` `undo` `command` `(ownership` `will` `be` `handled` `automatically)`*
`    return ClearCommand(glwidget)`

readSettings & writeSettings
============================

Implementing a readSettings and writeSettings method allow extensions to save their settings between sessions.

`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
`import Avogadro`
**`class` `Extension(QObject):`**
`  `**`def` `__init__(self):`**
`    QObject.__init__(self)`
`  `**`def` `actions(self):`**
`    ...`
`  `**`def` `performAction(self,` `action,` `glwidget):`**
`    ...`
`  `**`def` `readSettings(self,` `settings):` `#` `Optional`**
`    `*`#` `load` `the` `variable(s)`*
`    self.someSetting = settings.value("someSetting", QVariant(4))`
`  `**`def` `writeSettings(self,` `settings):` `#` `Optional`**
`    `*`#` `save` `the` `variable(s)`*
`    settings.setValue("someSetting", self.someSetting)`

Examples
========

-   [protein.py](protein.py "wikilink")
-   [saveconformers.py](saveconformers.py "wikilink")
-   [cubeeditor.py](cubeeditor.py "wikilink")

<Category:Scripting>

