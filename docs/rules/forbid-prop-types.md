# Forbid certain propTypes (forbid-prop-types)

By default this rule prevents vague prop types with more specific alternatives available (`any`, `array`, `object`), but any prop type can be disabled if desired. The defaults are chosen because they have obvious replacements. `any` should be replaced with, well, anything. `array` and `object` can be replaced with `arrayOf` and `shape`, respectively.

## Rule Details

This rule checks all JSX components and verifies that no forbidden propsTypes are used.
This rule is off by default.

The following patterns are considered warnings:

```js
var Component = React.createClass({
  propTypes: {
    a: React.PropTypes.any,
    r: React.PropTypes.array,
    o: React.PropTypes.object
  },
...
});

class Component extends React.Component {
  ...
}
Component.propTypes = {
  a: React.PropTypes.any,
  r: React.PropTypes.array,
  o: React.PropTypes.object
};

class Component extends React.Component {
  static propTypes = {
    a: React.PropTypes.any,
    r: React.PropTypes.array,
    o: React.PropTypes.object
  }
  render() {
    return <div />;
  }
}
```

## Rule Options

```js
...
"forbid-prop-types": [<enabled>, { "forbid": [<string>] }]
...
```

### `forbid`

An array of strings, with the names of `React.PropType` keys that are forbidden.

## When not to use

This rule is a formatting/documenting preference and not following it won't negatively affect the quality of your code. This rule encourages prop types that more specifically document their usage.
