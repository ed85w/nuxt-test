<template>
  <div>
    <h1>About</h1>
    <p>About page for this app</p>
  </div>
</template>

<script>
export default{
  head(){
    return {
      title: 'About Page',
      meta: [
        {
          hid: 'description', //id
          description: 'description', //meta type
          content: 'this is the description' //meta content

        }
      ]
    };
  }
}
</script>

<style>

</style>