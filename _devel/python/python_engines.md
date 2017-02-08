---
layout: single
title: Python Engines
---

# Python Engines

Creating python engines (display types)
---------------------------------------

### Hello World Engine

`import Avogadro`
`class Engine():`
`  def renderOpaque(self, pd):`
`    pd.painter.drawText(50, 50, "Hello World")`

### A real example: wireframe engine

#### Step 1: Render all bonds as green lines

wireframe1.py:

`from PyQt4.Qt import *`
`import Avogadro`
`class Engine(QObject):`
`  # constructor`
`  def __init__(self):`
`    QObject.__init__(self)`
`  # pd = PainterDevice`
`  def renderOpaque(self, pd):`
`    # Painter `
`    painter = pd.painter`
`    # Molecule`
`    molecule = pd.molecule`
`    # Set the color to green (red, green, blue, alpha)`
`    color = Avogadro.Color(0.0, 1.0, 0.0, 1.0)`
`    painter.setColor(color)`
`    for bond in molecule.bonds:`
`      # get the begin atom for this bond`
`      beginAtom = molecule.atomById(bond.beginAtomId)`
`      # get the end atom for this bond`
`      endAtom = molecule.atomById(bond.endAtomId)`
`      # draw the line between the atoms`
`      painter.drawLine(beginAtom.pos, endAtom.pos, 2.0)`

<Category:Scripting>

