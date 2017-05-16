# ember_cheatsheet

## Passing Action 

```handlebars
  {{! index.hbs}}
    {{pressCount}} Button presses
    {{button-wrapper click=(action "buttonClick")}}
  
  {{! components/button-wrapper.hbs}}
    <h2>Button Wrapper</h2>
    {{press-button click=(action click)}}
  
  {{! components/press-button.hbs}}
    <button>My Button</button>
```

```handlebars
  {{drop-target action=(action "didDrop")}}
```  

```handlebars
  <button onclick={{action 'signUp'}}>Sign Up</button>
```

*Invoking an action* [...docs](https://emberjs.com/api/classes/Ember.Templates.helpers.html#toc_invoking-an-action)
```typescript
export default Ember.Component.extend({
  actions: {
    // Usage {{input on-input=(action (action 'setName' model) value="target.value")}}
    setName(model, name) {
      model.set('name', name);
    }
  }
});
```
**Actions from component to route**
```typescript
// application route
  actions: {
    addBook() {};
  }
```

```handlebars
// Template application.hbs
{{reading-list books=model addBook=(route-action 'addBook') }}
```

```javascript
// Component reading-list
...
  actions: {
    onEnter() {}
  }
```
```handlebars
// Template reading-list.hbs
{{input value onEnter=(action 'onEnter') }}
```


*Bubble action* [..docs](https://emberjs.com/api/classes/Ember.Templates.helpers.html#toc_attaching-actions-to-dom-elements)
```handlebars
{{! An example of element space }}
<div {{action "save"}}></div>
```
Used this way, the {{action}} helper provides a useful shortcut for registering an HTML element in a template for a single DOM event and forwarding that interaction to the template's context (controller or component). **If the context of a template is a controller**, actions used this way **will bubble to routes** when the controller does not implement the specified action. Once an action hits a route, it will bubble through the route hierarchy.


##### More on
* [action method docs](https://emberjs.com/api/classes/Ember.Templates.helpers.html#toc_passing-functions-with-the-action-helper)
* [actions how to docs](https://guides.emberjs.com/v2.13.0/components/triggering-changes-with-actions/)
* [events how to docs](https://guides.emberjs.com/v2.12.0/components/handling-events/#toc_event-names)
* [custom events docs](https://emberjs.com/api/classes/Ember.Application.html#property_customEvents)
* [actions blog](https://emberigniter.com/send-closure-actions-up-data-owner/)
* [actions blog](https://medium.com/@jordanvincent/ember-actions-best-practices-442be5eed88d)
* [actions blog](https://embermap.com/notes/26-a-note-on-actions)

# TypeScript with Ember

**Assign multiple variables**
```typescript
const { login, password } = this.getProperties('login', 'password');
```

# Ember-redux
* [Video](https://vimeo.com/212534548) + [source](https://github.com/toranb/ember-redux-yelp/tree/themeSwitchRedux)
