 # Controllers

The purpose of controllers is to **expose variables and functionality to expressions and
directives**.

The ng-controller directive tells Angular that a Controller is responsible for the element with the directive and all of the element's children.

When a Controller is attached to the DOM via the `ng-controller` directive, Angular will instantiate a new Controller object, using the specified Controller's constructor function. **A new child scope will be created** and made available as an injectable parameter to the Controller's constructor function as `$scope`.


Any objects (or primitives) assigned to the `$scope` become **model** properties. All scope properties will be available to the template at the point in the DOM where the Controller is registered. Assign any objects (or primitives) as scope property using `$scope.x = ...`. Add **behavior** to the scope by assigning **functions**.

The syntax `Controller as` XY tells Angular to instantiate the controller and save it in the variable XY in the current scope.

Use controllers to:

- Set up the initial state of the `$scope` object.
- Add behavior to the `$scope` object.

## Scope Inheritance

It is common to attach Controllers at different levels of the DOM hierarchy. Since the ng-controller directive creates a new child scope, we get a hierarchy of scopes that inherit from each other. The `$scope` that each Controller receives will **have access to properties and methods defined by Controllers higher up the hierarchy**
