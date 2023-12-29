<template>
  <ul>
    <li v-for="item in user" :key="item.id">
        <p>Name: {{item.name}}</p>
        <p>UserName: {{item.username}}</p>
        <p>Email: {{item.email}}</p>
        <p>Phone: {{item.phone}}</p>


    </li>
  </ul>
</template>

<script>
export default {
  async setup() {
    const route = useRoute();
    const user = reactive([]);
    const proxyData = await useFetch(
      "https://jsonplaceholder.typicode.com/users/" + route.params.id
    );
    user.push(proxyData.data.value);
    console.log(user, "hacıııı");
    return { user, route };
  },
};
</script>

<style>
</style>