# reactchanges
A summary of changes made to React.js since version 0.4 for easy reference

# React 0.5

No longer transform class to className as part of the transform! This is a breaking change - if you were using class, you must change this to className or your components will be visually broken.

# React 0.6

No breaking changes

# React 0.8

No breaking changes

# React 0.9

1. The lifecycle methods componentDidMount and componentDidUpdate no longer receive the root node as a parameter; use this.getDOMNode() instead
2. Whenever a prop is equal to undefined, the default value returned by getDefaultProps will now be used instead
3. React.unmountAndReleaseReactRootNode was previously deprecated and has now been removed
4. React.renderComponentToString is now synchronous and returns the generated HTML string
5. Full-page rendering (that is, rendering the <html> tag using React) is now supported only when starting with server-rendered markup
6. On mouse wheel events, deltaY is no longer negated
7. When prop types validation fails, a warning is logged instead of an error thrown (with the production build of React, type checks are now skipped for performance)
8. On input, select, and textarea elements, .getValue() is no longer supported; use .getDOMNode().value instead
9. this.context on components is now reserved for internal use by React
10. React no longer adds an __owner__ property to each component's props object; passed-in props are now never mutated
11. Passing an invalid or misspelled propTypes type now throws an error
12. Boolean attributes such as disabled are rendered without a value (previously disabled="true", now simply disabled)
13. Whitespace normalization has changed; now space between two tags on the same line will be preserved, while newlines between two tags will be removed

# React 0.10

No breaking changes

# React 0.11

1. getDefaultProps() is now called once per class and shared across all instances
2. MyComponent() now returns a descriptor, not an instance
3. React.isValidComponent and React.PropTypes.component validate descriptors, not component instances.
4. Custom propType validators should return an Error instead of logging directly

# React 0.11.2

1. picture is now parsed into React.DOM.picture

# React 0.12

1. key and ref moved off props object, now accessible on the element directly
2. Default prop resolution has moved to Element creation time instead of mount time, making them effectively static
3. React.__internals is removed - it was exposed for DevTools which no longer needs access
4. Composite Component functions can no longer be called directly - they must be wrapped with React.createFactory first. This is handled for you when using JSX.
5. React.renderComponent --> React.render
6. React.renderComponentToString --> React.renderToString
7. React.renderComponentToStaticMarkup --> React.renderToStaticMarkup
8. React.isValidComponent --> React.isValidElement
9. React.PropTypes.component --> React.PropTypes.element
10. React.PropTypes.renderable --> React.PropTypes.node
11. DEPRECATED React.isValidClass
12. DEPRECATED Returning false from event handlers to preventDefault
13. DEPRECATED Convenience Constructor usage as function, instead wrap with React.createFactory
14. DEPRECATED use of key={null} to assign implicit keys
15. Enforced convention: lower case tag names are always treated as HTML tags, upper case tag names are always treated as composite components
16. JSX no longer transforms to simple function calls

# React 0.13

1. Deprecated patterns that warned in 0.12 no longer work: most prominently, calling component classes without using JSX or React.createElement and using non-component functions with JSX or createElement
2. Mutating props after an element is created is deprecated and will cause warnings in development mode; future versions of React will incorporate performance optimizations assuming that props aren't mutated
3. Static methods (defined in statics) are no longer autobound to the component class
4. ref resolution order has changed slightly such that a ref to a component is available immediately after its componentDidMount method is called; this change should be observable only if your component calls a parent component's callback within your componentDidMount, which is an anti-pattern and should be avoided regardless
5. Calls to setState in life-cycle methods are now always batched and therefore asynchronous. Previously the first call on the first mount was synchronous.
6. setState and forceUpdate on an unmounted component now warns instead of throwing. That avoids a possible race condition with Promises.
7. Access to most internal properties has been completely removed, including this._pendingState and this._rootNodeID.
8. ComponentClass.type is deprecated. Just use ComponentClass (usually as element.type === ComponentClass).
9. Some methods that are available on createClass-based components are removed or deprecated from ES6 classes (getDOMNode, replaceState, isMounted, setProps, replaceProps).
10. A change was made to how some JSX was parsed, specifically around the use of > or } when inside an element. Previously it would be treated as a string but now it will be treated as a parse error. The jsx_orphaned_brackets_transformer package on npm can be used to find and fix potential issues in your JSX code.
