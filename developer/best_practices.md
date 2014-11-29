---
layout: default
title: Best Practices
categories: Developer
---



This page is a guide for newcomers to the project. It should gain some insight on how the project has been designed code-wise and save you time in the long run. These are just my (dcurtis) tips on adding new functionality to areas of Avogadro and keeping the API clean and simple.

Parameters
----------

Keeping public function parameters minimal is a plus. While there are some public functions that can require lots of parameters, in most cases any data a class member function needs is already associated with the class in some way, shape or form. This, in itself, keeps data consistent and makes it easier to trace data flow when debugging. In adding a parameter you're asking the developer for information that you might already know. If the function user gives you the wrong information, your code can easily look like it's the problem when it's been supplied bad information. Before adding a parameter consider the following;

-   Does the function already have access to this data either through it's class data or parent?
-   Is the data you're passing persistent (ie. does it exist as a member of another class)?
-   Should this function have access to this data through it's class or parent?

If you can answer yes to these questions then you probably shouldn't be adding a parameter. Most likely you should use that class/parent data. If it doesn't have access to this data, and intuitively it should, then this the root of the problem and most likely the reason you're thinking you need the parameter. For example, consider a function in the Atom class that requires information about the Molecule it belongs to. The correct way to implement this would be to implement Atom::parent(), Atom::setParent() and add a parent parameter to the constructor. The incorrect way would be to pass this information to the function. The reasoning behind this is that it is reasonable to expect a class to know about the parent it belongs to. Also in the future it may be required that other functions also need this information. We use the word reasonable synonymously with intuitive. Remember that we're implementing code based on knowledge of a real world domain, chemistry. We know Atoms belong to Molecules and sometimes their properties are based on the Molecule they belong to. It is reasonable and intuitive if the code reflects that. Of course this is not a rule and there are times when data given to a function of the Atom class would not "intuitively" be part of the Atom class properties. Some examples where a parameter is needed is when the data being passed is non-persistent in any other class (static string or value) or when the parameter is a pointer to an object which the receiving function is taking control of that object.

If you're unsure, you can always ask another developer. Many times in explaining the question to another you will give yourself the answer you need.

*Note: These suggestions apply mainly to public member functions. Private member functions are used to reduce code size by replacing frequently used segments of code with a single function call which rely heavily on their parameters. Private member functions are also not visible to the library user and can be fixed without user knowledge.*

Classes
-------

In general classes should be used to simplify major elements of the project. Most data you need is in some way associated or can be grouped with other data. While it may not be the only great thing about classes, it is important that classes be intuitive. It makes it much easier on the developer building the class and using the class. Unless you are designing a new plugin (tool / engine / extension), most of the time adding a new class only creates unneeded bulk in the API.

A suggestion i would have is that if the data you're putting in a class is one-to-one with another class, then most likely it could be contained in that other class.



