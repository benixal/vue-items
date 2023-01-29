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
import items from './components/ItemsComponent.vue';


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

