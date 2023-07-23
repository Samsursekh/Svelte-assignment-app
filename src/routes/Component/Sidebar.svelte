<script>
  export let isSidebarOpenVeriable;
 
  import { onMount } from "svelte";
  let products = [];

  onMount(async() => {
    const data = await fetch(`https://cars-mock-api-wjnb.onrender.com/cars`);
    products = await data.json();
    console.log(products, "products is getting...");

  })
  
</script>

<aside
  class={isSidebarOpenVeriable === true
    ? "bg-[#334155] w-[40%] h-[92vh] fixed top-14 left-0 transform transition-transform ease-in-out duration-300 translate-x-0 md:translate-x-0 md:static sm:static overflow-y-auto"
    : "hidden"}
>

 <div><input type="text" class="border rounded p-2 w-[90%] ml-[5%] mt-4 outline-none" placeholder="Search product here..."></div>
  <!-- Sidebar Content Goes Here -->
  <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 p-4">
    {#each products as item (item.id)}
      <div class="border rounded p-2">
        <img class=" object-cover" src={item.image} alt={item.id}>
        <h3 class="text-white font-semibold text-xl mb-2">Name : {item.brand}</h3>
        <h3 class="text-white mb-2">Price : ₹ {item.Price}</h3>
      </div>
    {/each}
  </div>
</aside>
