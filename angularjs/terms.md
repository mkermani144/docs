Angularjs terms
====


Two way data binding
----
In traditional data binding model (called one-way data binding), after building the view from template and model, changes to the model does not automatically change view and vice versa.

For example, suppose you have a page with an `input` element and a `p` element whose value is the same as `input` value. By changing the `input` value, the value of `p` element will not get updated. (Until you press a key, for example.)

In AngularJS data binding model (called two-way data binding), changes to each view or model will update the other. In our example, every change to the `input` element will update `p` element _automatically_. (And you don't need to press that key anymore!)


To-do
----
- [ ] Directives
- [ ] Scope
- [x] Data binding
