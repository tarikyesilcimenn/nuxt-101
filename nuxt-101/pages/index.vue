<template>
  <div>
    <ul>
      <li>
        <NuxtLink to="/about">About</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/posts/1">Posts 1</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/posts/2">Posts 2</NuxtLink>
      </li>
    </ul>
    <button @click="fetchData">Fetch Data</button>
    <div class="fetchContainer">
        <div>fetching data</div>
        <div>
            <ul>
                <li v-for="item in users" :key="item.id">
                    <NuxtLink :to="'/users/'+item.id">{{item.name}}</NuxtLink>
                </li>
            </ul>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    async setup(){
        const users = reactive([])
        const fetchData = async () => {
            const proxyData = await useFetch('https://jsonplaceholder.typicode.com/users')

            users.push(...proxyData.data.value)
        }
        console.log(users, 'hacıııı')
        return {fetchData, users}
    }
};
</script>

<style>
.fetchContainer {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
</style>