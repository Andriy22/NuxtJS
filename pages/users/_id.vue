<template>
    <section>
        <h1>User {{user.name}}</h1>

        <hr>

        <h3>{{user.email}}</h3>
    </section>
</template>


<script>
export default {
 validate({params}) {
     console.log(params.id);
     return /^\d+$/.test(params.id);
 },
 async asyncData({$axios, params}) {
     const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/' + params.id);
     console.log(user);
     return {user};
 }
}
</script>
