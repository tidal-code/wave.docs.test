---
layout: default
title: Automation Layers
parent: Best Practices
nav_order: 2
---

# Automation Layers

For a healthy test automation project, you need to have a well-defined project structure. 
Your testing components should be logically arranged across different folders to make them easy to locate.
It is always beneficial to maintain a common folder structure across all your test automation projects. 
This enables test automation engineers to explore other code repositories and facilitates seamless transitioning between projects.

Some of the layers to consider for a UI automation projects are:

<p style="font-weight:bold;">
Steps<br>
Locators<br>
Actions<br>
Rules<br>
Processes<br>
Tasks<br>
Data<br>
Utilities<br>
</p>

### Steps

Contain the implementaton classes for the test scenarios. If you are using a BDD framework to run
your tests, the steps classes will implement the Gherkin step definitions. If you are using a unit testing framework, the
Steps class will implement the method calls which run the tests.

### Locators

When you have many choices to locate an element in the page HTML:- <br>
Id/Name is the fastest and most efficient. They are supposed to be unique in the page. <br>
CSS Selector is the next best choice.<br>
Class name is the next best choice, but there can be multiple elements with same class name. So, finding an element using class name is not a good option, unless they are unique.<br>
Link Text, Partial Link Text are the next ones but they eventually parsed into xpath locators. <br>
X path is the slowest but sometimes, they would be the only possible way to locate an element. <br>


### Actions

The action layer should contain the direct interation with the UI. They are plane, simple methods like click, clear, getText etc. 
This layer should try to reduce the logical calculations. Instead it should focus only on UI interactons. Only action methods should be
able to use the 'find("element")' methods. 

Action classes should be UI centric. Do not create action classes based on business logic. 
For example, you should not create an action class with name, CustomerCreationActions. Instead, you should create a more specific, UI centric
action class such as CustomerAddressInputActions. Action classes should not call another Action class. 


### Rules

The Rules layer should contain the logic to verify the test results. They should use a proper test assertion library to achieve this.
Rules classes can be called in Steps classes to complete the verifications. Rules classes can call Task classes and Action classes to complete the
verfication steps.

### Processes

Processes form the highest level in the test logic hierarchy. These classes represent the large business processes, which are comprised of multiple tasks and actions. 
For example, a work order creation is a business process. It contains multiple tasks and actions. A Process class should not call another process class.

### Tasks

Tasks are groups of action methods. You create a task method with seemingly ‘unrelated’ action methods. The primary purpose of creating task methods are to avoid action classes calling each other.
You should not use find() methods with task classes. You should rather call action classes in task classes.
Tasks classes can call multiple action classes. A Task class should not call another Task class. 







