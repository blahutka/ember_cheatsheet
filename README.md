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
##### More on
* [action method docs](https://emberjs.com/api/classes/Ember.Templates.helpers.html#toc_passing-functions-with-the-action-helper)
* [actions how to docs](https://guides.emberjs.com/v2.13.0/components/triggering-changes-with-actions/)
* [events how to docs](https://guides.emberjs.com/v2.12.0/components/handling-events/#toc_event-names)
* [custom events docs](https://emberjs.com/api/classes/Ember.Application.html#property_customEvents)