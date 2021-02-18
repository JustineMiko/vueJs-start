<template>
    <div class="title">
        <h1>To do list</h1>
    </div>
</template>


<script>
  export default {
    name: 'Title',
    props: { title : String }
}
</script>

<style>
    button {
        background-color: white;
    }

  .title {
    text-align: center;
  }
</style>

