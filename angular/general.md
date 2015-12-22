#Concept

AngularJS is a structural framework for dynamic web apps. It lets you use HTML as your
template language and lets you **extend HTML**'s syntax to express your application's
components clearly and succinctly. Angular is what HTML would have been, had it been
designed for applications. **Angular teaches the browser new syntax** through a
construct we call **directives**.

**Angular was built with the CRUD application in mind**. In other words, not every app
is a good fit for Angular. Games and GUI editors are examples of applications with
intensive and tricky DOM manipulation. These kinds of apps are different from CRUD
apps, and as a result are probably not a good fit for Angular. In these cases it may be
better to use a library with a lower level of abstraction, such as jQuery.

Angular frees you from the following pains:

- 	**Registering callbacks**

- 	**Manipulating HTML DOM programmatically**
	By declaratively describing how the UI should change as your application state changes, you are freed from low-level DOM manipulation tasks

- 	**Marshaling data to and from the UI**

##Dependency Injection

Within Angular, the DI container is called the **injector**.
To use DI, there needs to be a place where all the things that should work together are
registered. In Angular, this is the purpose of the modules