---
layout: default
title: Standards
---

# Standards

When in doubt about standards, consider the policies which KDE has set (see [\#Links](#Links "wikilink")).

Formatting
----------

Two spaces, no tabs.

Naming
------

All classes used in avogadro or libavogadro should exist in the Avogadro namespace.

Classes should start with a capital letter.

Variables should start with a lowercase with each successive word capitalized.

  
QString \*nameString;

QTextEdit \*nameText;

QTreeView \*moleculeTree;

Acronyms are also lowercased.

  
QString \*remoteUrlString;

For setter/getter functions, prefix 'set' for the setter and include no prefix for the getter. (consistent with QT)

  
void setValue(int i) / int value()

void setHidden(bool h) / bool isHidden()

For more information see: [Designing Qt-Style C++ APIs](http://doc.qt.nokia.com/qq/qq13-apis.html)

Documentation
-------------

See [Documentation](Documentation "wikilink")

Example
-------

`<pre>
namespace Avogadro {
  /**
   * @class Test
   * @brief Class used for nothing.
   * @author Author Guy
   *
   * The Test class is not used by avogadro.  It is provided as a demonstration
   * of proper formatting and comment procedure.
   */
  class TestPrivate
  class A_EXPORT Test : public QObject
  {
    Q_OBJECT

    public:
      /**
       * Constructor
       *
       * @param parent the object parent
       */
      Test(QObject *parent=0);

    private:
      TestPrivate * const d;

    private Q_SLOTS:
      /**
       * Function that does something used internally by the class.
       * 
       * @sa testSignal
       */
      void testSlot();

    Q_SIGNALS:
      /**
       * Emitted when something happens
       *
       * @param parameter signal parameter
       */
      void testSignal(void *parameter);
  };
}
</pre>`

Links
-----

[KDE Library Code Policy (include naming conventions)](http://techbase.kde.org/Policies/Library_Code_Policy)

<Category:Developer>

