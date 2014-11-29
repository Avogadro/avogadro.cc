---
layout: default
title: Saveconformers.py
---

# Saveconformers.py

`#`
`# Save all conformers by specifying filename.ext. The filenames`
`# will be filename_n.ext where n is the conformer index (0...numConformers)`
`#`
`# NOTE: requires Avogadro 1.0.1 or above`
`#`
`import Avogadro`
`from PyQt4.QtCore import *`
`from PyQt4.QtGui import *`
`class Extension(QObject):`
`  def __init__(self):`
`    QObject.__init__(self)`
`  def actions(self):`
`    actions = []`
`    action = QAction(self)`
`    action.setText("Save All Conformers")`
`    actions.append(action)`
`    return actions`
`  def performAction(self, action, glwidget):`
`    molecule = glwidget.molecule`
`    fileName = QFileDialog.getSaveFileName()`
`    info = QFileInfo(fileName)`
`    for i in range(molecule.numConformers):`
`      molecule.setConformer(i)`
`      fileName = info.baseName() + "_" + QString.number(i) + "." + info.completeSuffix()`
`      Avogadro.MoleculeFile.writeMolecule(molecule, fileName.toAscii().data())`

