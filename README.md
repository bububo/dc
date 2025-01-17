# DC

[Live Demo](https://delete-agency.github.io/dc/)

## Motivation

TODO 

## Installation

Use the package manager [npm](https://docs.npmjs.com/about-npm/) for installation.

```
$ npm install @deleteagency/dc
```

## Usage

```js
// collapsed/collapsed.js
import {DcComponent} from  '@deleteagency/dc';

export default class CollapsedComponent extends DcBaseComponent {
    constructor(...args) {
        super(...args);

        this.button = this.refs.button;
        this.content = this.refs.content;
    }

    onInit() {
        console.log('CollapsedComponent was instantiate on the element', this.element)
    }

    static getNamespace() {
        return 'collapsed'
    }
}

// collapsed/index.js
import './scss/index.scss';
import {dcFactory} from  '@deleteagency/dc';
import CollapsedComponent from './collapsed.js';
dcFactory.register(CollapsedComponent);


// later after registering all your components, when your page is ready
dcFactory.init();

```

## API

### dcFactory.register(componentClass[, selector])

#### componentClass

*Required*<br>
Type: `typeof DcBaseComponent`

Class which inherits DcBaseComponent and will be instantiated

#### selector

*Optional*<br>
Type: `string`

CSS selector which will override searching by getNamespace() and be used for searching elements of given componentClass. 

### dcFactory.init(root = document.body, withLazy = true)

Starts the factory on a given root: finds and creates all registered components within the root

#### root

*Optional*<br>
Type: `HTMLElement`

#### withLazy

*Optional*<br>
Type: `boolean`

Defines whether or not components which are marked as lazy should be created during this particular initialization.
To mark components as lazy you need to add `data-dc-lazy` attribute on its element or any of its parent elements

### dcFactory.destroy(root)

Destroy all previously registered components within the passed element

#### root

*Required*<br>
Type: `HTMLElement`

### dcFactory.getChildComponents(element, componentClass)

Returns `DcBaseComponent[]`

Returns all components of componentClass which are contained within the passed element

#### element

*Required*<br>
Type: `HTMLElement`

#### componentClass

*Required*<br>
Type: `typeof DcBaseComponent`

### dcFactory.getChildComponent(element, componentClass)

Returns `DcBaseComponent`

Returns first found component of componentClass which is contained within the passed element

#### element

*Required*<br>
Type: `HTMLElement`

#### componentClass

*Required*<br>
Type: `typeof DcBaseComponent`

### dcFactory.debug(element)

Returns `DcBaseComponent[]`

NOTE: just for debugging purpose!
Returns all components instances which were created on the given element.

#### element

*Optional*<br>
Type: `HTMLElement`


## License
[MIT](https://choosealicense.com/licenses/mit/)