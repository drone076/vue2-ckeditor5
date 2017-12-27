# vue2-ckeditor5
Integrate Ckeditor 5 into VUE 2 component, two way binding

```javascript
yarn add @ckeditor/ckeditor5-build-classic
```

Usage:

```javascript
import Ckeditor from '@/components/Ckeditor'

export default {
  name: 'EditPage',
  ...
  components: {
    ...
    Ckeditor,
    ...
...    

<template>
  ...
  <ckeditor v-model="model"></ckeditor>
  ...
</template>
```

Peace!
