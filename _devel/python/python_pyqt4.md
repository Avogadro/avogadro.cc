---
layout: single
title: Python PyQt4
---

# Python PyQt4

The Avogadro python module only wraps Avogadro specific classes, Qt classes are already available in [PyQt4](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html). When you call a method which returns a Qt object, you get a real PyQt4 object with all it's associated methods etc.

`>>> print engine`
<Avogadro.Engine object at 0x9b0372c>
`>>> print engine.settingsWidget`
<PyQt4.QtGui.QWidget object at 0x9ae03ac>

It is also possible to use PyQt4 objects as parameters in method calls.

`>>> from PyQt4.Qt import *`
`>>> import Avogadro`
`>>> import sys`
`>>> app = QApplication(sys.argv) # need to create app before GLWidget`
`>>> glwidget = Avogadro.GLWidget() # Avogadro object`
`>>> print glwidget`
<Avogadro.GLWidget object at 0xb7da57d4>
`>>> undostack = QUndoStack() # PyQt4 object`
`>>> print undostack`
<PyQt4.QtGui.QUndoStack object at 0xb7d969ac>
`>>> print glwidget.undoStack`
`None`
`>>> glwidget.undoStack = undostack # calls GLWidget::setUndoStack(QUndoStack*)`
`>>> print glwidget.undoStack`
<PyQt4.QtGui.QUndoStack object at 0xb7d969ac>

Avogadro.toPyQt(...)
--------------------

Although most Avogadro classes are derived from a Qt class, they are not directly available as PyQt4 objects. To get the underlying PyQt4 object, the Avogadro python module provides the toPyQt(...) function.

`>>> print glwidget`
<Avogadro.GLWidget object at 0x8a207ac>
`>>> print Avogadro.toPyQt(glwidget)`
<PyQt4.QtOpenGL.QGLWidget object at 0x8ec0b6c>

| Class         | toPyQt(Class) |
|---------------|---------------|
| Atom          | QObject       |
| Bond          | QObject       |
| Cube          | QObject       |
| Engine        | QObject       |
| Extension     | QObject       |
| Fragment      | QObject       |
| GLWidget      | QGLWidget     |
| Mesh          | QObject       |
| Molecule      | QObject       |
| Painter       | QObject       |
| PluginManager | QObject       |
| Primitive     | QObject       |
| Residue       | QObject       |
| Tool          | QObject       |
| ToolGroup     | QObject       |

The use of the toPyQt function is best explained with some examples:

-   Use toPyQt(...) to call Qt methods like show(), resize(...), ...

`>>> glwidget.show()`
`Traceback (most recent call last):`
`  File "`<stdin>`", line 1, in `<module>
`AttributeError: 'GLWidget' object has no attribute 'show'`
`>>> Avogadro.toPyQt(glwidget).show()`
`GLWidget initialisation... `
`GLSL support enabled, no OpenGL 2.0 support. `
`GLWidget initialised... `

-   Use toPyQt to pass an Avogadro class as argument to a PyQt4 method

`>>> mainwindow = QMainWindow()`
`>>> glwidget = Avogadro.GLWidget()`
`mainwindow.setCentralWidget(glwidget)`
`Traceback (most recent call last):`
`  File "`<stdin>`", line 1, in `<module>
`TypeError: argument 1 of QMainWindow.setCentralWidget() has an invalid type`
`>>> mainwindow.setCentralWidget(Avogadro.toPyQt(glwidget))`

Qt signals and slots
--------------------

Qt's [signals and slots](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#signal-and-slot-support) are also handled by PyQt4. Connecting a signal to a slot from two PyQt4 classes:

` [QtCore.]QObject.connect(a, [QtCore.]SIGNAL("QtSig()"), b, [QtCore.]SLOT("QtSlot()"))`

When a class is an Avogadro class, we need to use toPyQt(...) to get the PyQt4 object:

` [QtCore.]QObject.connect(Avogadro.toPyQt(atom), [QtCore.]SIGNAL("updated()"), b, [QtCore.]SLOT("QtSlot()"))`

Note: Even when the signal/slot is defined in Avogadro, you should always use toPyQt(...) to connect signals/slots.

**Important!!!** The syntax for signal and slots described before is the only one that works in Avogadro:

`  class Generic(QObject)`
`   def __init__(self):`
`       super(Generic,self).__init__()`
`       self.button = QPushButton()`
`       #a.clicked.connect( self.on_clicked ) # Don't work`
`       #QObject.connect(self,SIGNAL("iterated(int,float)"), self.on_clicked ) # Don't work`
`       QObject.connect(self,SIGNAL("clicked()"),self,SLOT("on_clicked()")) # This works`
`       QObject.connect(self,SIGNAL("toggled(bool)",self,SLOT("on_clicked(bool)"))# This works, with additional argument`
`   @pyqtSignature("")`
`   def on_clicked(self):`
`       ... do stuff ...`
`   @pyqtSignature("bool")`
`   def on_toggled(self):`
`       ... do stuff ...`

A detailed description on how to use signal/slots can be found in this [blog post](http://timvdm.blogspot.com/2008/12/avogadro-gets-new-python-wrappers.html).

The PyQt4 documentation provides more information on how to use signal/slots:

-   <http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html>
-   <http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#new-style-signal-and-slot-support>
-   <http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#old-style-signal-and-slot-support>

### Threads: QThreads and threading.Threads

Threads are generally used to perform blocking tasks without blocking the GUI. Examples are intensive calculations or long I/O operations.

Unfortunately, threads don't work, a solution is to use [multiprocessing.Process](http://docs.python.org/library/multiprocessing.html#multiprocessing.Process) to run the task in another process writing results in a [Queue](http://docs.python.org/library/multiprocessing.html#multiprocessing.Queue), in combination with [QtCore.QTimer](http://doc.trolltech.com/4.3/qtimer.html) that periodically fetches results from the Queue until the process finish.

`import multiprocessing.Process`
`from PyQt4.QtCore import *`
`class Task(multiprocessing.Process):`
`    def __init__(self,data):`
`        super(Task,self).__init__()`
`        self.data = data # Pass the data throught the constructor`
`        self.queue = multiprocess.Queue()`
`    def run(self):`
`        self.queue.put("Starting process")`
`        ... do stuff putting data in the queue ...`
`class Controller(QObject):`
`    def __init__(self):`
`       super(Controller,self).__init__()`
`       data = GenericObject()`
`       self.timer = QTimer()`
`       self.task = Task(data)`
`       QObject.connect(self.timer, SIGNAL("timeout()"),self, SLOT("process_data"))`
`       self.task.start()`
`       self.timer.start(10) # Call process_data every 10 milliseconds`
`    pySignature("")`
`    def process_data(self):`
`       if self.task.queue.empty(): # If the queue is empty`
`          if not self.task.is_alive():  # And if the process is exited`
`              self.timer.stop() # Stop the timer`
`              return `
`          else: return # nothing to read`
`       else: # The queue has something to read`
`          stuff = self.task.queue.get()`
`          ... do things with stuff, like update GUI etc ...`
`Controller()`

In addition, the multiprocessing approach works very well on multicore machines, the operating system can take the various processes over multiple processors.

<Category:Scripting>

