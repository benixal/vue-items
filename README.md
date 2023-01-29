# vue CRUD items

## installation
```
npm i @benixal/vue-items
```
## Live DEMO : [https://stackblitz.com/edit/vue-9gnuib](https://stackblitz.com/edit/vue-9gnuib)
## How to use 
just bind your array to items 
```
:items="myarray"
```
and 
define 
```
v-slot="{ item }"
```
then you can access items data by
```
item.data.FIELDNAME
```
### Add new 
you can push new item to your array or define a ref for component and use addNew method
```
ref="myItems"
```
```
$refs.myItems.addNew({ title: 'im new' })
```
### Delete item
```
item.destroy
```
### Save
there is no direct save method in this library , you can pass each item to your own save method
```
<button @click="save(item)">save</button>
```

### Full Example

```
<template>
  <items :items="arrayOfItems" ref="myItems" v-slot="{ item }">
    <input type="text" v-model="item.data.title" />
    <button @click="save(item)">save</button>
    <button @click="destroy(item)">
      <strong style="color: red">X</strong>
    </button>
  </items>
  <hr />
  <button @click="$refs.myItems.addNew({ title: 'im new' })">addnew</button>
</template>

<script>
import items from '@benixal/vue-items';

export default {
  name: 'App',
  components: {
    items,
  },
  data() {
    return {
      arrayOfItems: [
        { id: 1, title: 'a' },
        { id: 2, title: 'b' },
        { id: 3, title: 'c' },
      ],
    };
  },
  methods: {
    save: function (itm) {
      console.log(itm.data);
       alert("send this to your api : \n"+JSON.stringify(itm.data));
    },
    destroy: function (itm) {
      itm.destroy();
    },
  },
};
</script>

```