<template>
    <div v-for="item in items" :key="item.id">
      <slot
        v-bind="{
          item: {
            data: item,
  
            destroy: () => {
              const index = items.indexOf(item);
  
              if (index > -1) {
                // eslint-disable-next-line vue/no-mutating-props
                items.splice(index, 1);
              }
            },
          },
        }"
      ></slot>
    </div>
  </template>
  
  <script>
  export default {
    name: 'App',
  
    props: { items: Array },
  
    methods: {
      addNew: function (n) {
        // eslint-disable-next-line vue/no-mutating-props
        this.items.push(n);
      },
    },
  };
  </script>
  