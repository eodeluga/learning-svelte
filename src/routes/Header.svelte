<script lang='ts'>
  export type User = {
    name?: string
  }
  
  const { name }: User = $props()
  
</script>

<div>
  <h1>{name ? `${name}'s Form` : 'Form'}</h1>
</div>
