<script lang='ts'>
  type User = {
    name?: string,
    age: number
  }
  const { age, name }: User = $props()
</script>
<h1>Hello from {name?.toUpperCase() ?? 'Larry'}. I am {age}</h1>

<style>

</style>
