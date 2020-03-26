#A Simple Image Preview Vue Component

Used as a simple preview component for picture upload forms.

##Install

``$ npm install apl-vue-image-preview``

or

``$ yarn add apl-vue-image-previews``

##Usage

**In a Vue file:**

```javascript
import ImagePreview from 'apl-vue-image-preview';

export default {
	components: {
        'image-preview': ImagePreview,
	},

    //...
}
```

**In a js file (like Laravel's app.js):**

```javascript
window.Vue = require('vue');

Vue.component('image-preview', require('apl-vue-image-preview').default);

const app = new Vue({
    el: '#app',
});
```

###Parameters

* **file-selector** - (mandatory) The id of the file input
* **src** - (optional - default: null) The url to the current file (if any)
* **alt** - (optional - default: "Image Preview") The text to be displayed if no picture is selected
* **transparent** - (optional - default: false) Whether to display the squared background for transparent images

###Styling

**To be defined**