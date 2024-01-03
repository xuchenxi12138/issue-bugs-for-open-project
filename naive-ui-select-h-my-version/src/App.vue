<script setup lang="ts">
import { h, reactive, ref } from 'vue'
import { NSelect, NDataTable } from 'naive-ui'
const optionsRef = ref([
  {
    label: '1',
    value: 1
  },
  {
    label: '2',
    value: 2
  }
])
const ComponentA = () =>
  h(
    NSelect,
    {
      options: optionsRef.value
    },
    {}
  )
const ComponentB = () =>
  h(
    NSelect,
    {
      options: optionsRef.value
    },
    null
  )
const columns = ref([
  {
    title: '序号',
    key: 'index'
  },
  {
    title: '组件A',
    key: 'comp_a',
    render: () =>
      h(
        NSelect,
        {
          options: optionsRef.value,
          style:{width:'200px'}
        },
        {}
      )
  },
  {
    title: '组件B',
    key: 'comp_b',
    render: () =>
      h(
        NSelect,
        {
          options: optionsRef.value,
          style:{width:'200px'}
        },
        null
      )
  }
])
const data = ref([
  {
    index: '1',
    comp_a: 1,
    comp_b: 2
  },
  {
    index: '3',
    comp_a: 2,
    comp_b: 1
  }
])
</script>

<template>
  <div>
    <p>这个组件可选</p>
    <ComponentA />
  </div>
  <div>
    <p>这个组件可选</p>
    <ComponentB />
  </div>
  <n-data-table :columns="columns" :data="data"> </n-data-table>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
