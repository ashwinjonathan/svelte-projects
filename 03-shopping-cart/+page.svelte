<script>
    let products = $state([
        {name : "Screwdriver", price : 500},
        {name : "Plate", price : 60},
        {name : "Water Bottle", price : 700},
        {name : "Couch", price : 580},
        {name : "T-Shirt", price : 95}
    ])

    let total = $state([0])

    let total_amt = $derived(total.reduce((acc, curr) => acc + curr, 0))
</script>

<h1>Shopping Cart</h1>

<ul>
    {#each products as element}
        <li>{element.name}</li>
        <button onclick={() => total.push(element.price)}>Add to Cart</button>
    {/each}
</ul>

<h2>Total Amount is : ${total_amt}</h2>