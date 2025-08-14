<script lang='ts'>
  type Item = {
    name: string
    description: string
    price: number
  }
  
  type Cart = {
    items: Item[]
    totalPrice: number
    totalItems: number
  }
  
  let items: Item[] = $state([])
  
  let cartTotals: Cart = $derived({
    items,
    totalItems: items.length,
    totalPrice: items.reduce((acc, curr) => {
      return acc += curr.price
    }, 0)
  })

</script>

<table>
  <tbody>
    {#each Object.entries(items[0]) as [key, _]}
      <tr>
        <th>{key}</th>
      </tr>
    {/each}
    {#each items as {description, name, price}}
      <tr>
        <td>{description}</td>
        <td>{name}</td>
        <td>{price}</td>
      </tr>
    {/each}
  </tbody>
</table>

<h1>Totals</h1>
<div>Total items: {cartTotals.totalItems}</div>
<div>Total price: {cartTotals.totalPrice}</div>
