<template>
  <div>
    <h2>This is a test app - dad jokes</h2>
  </div>
</template>

<script>
export default{
  head(){
    return {
      title: 'Welcome Page',
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

