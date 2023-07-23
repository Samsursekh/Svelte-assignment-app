<script>
  import SearchBarComponent from "./SearchBarComponent.svelte";
  import AddProductComp from "./AddProductComp.svelte";

  export let isSidebarOpenVeriable;
  import { debounce } from "lodash";
  import { onMount } from "svelte";

  let Allproducts = [];
  let filteredProducts = [];
  let searchQuery = "";
  let showModal = false;
  let sidebarRender = false;

  onMount(async () => {
    const data = await fetch(`https://cars-mock-api-wjnb.onrender.com/cars`);
    Allproducts = await data?.json();
    filteredProducts = Allproducts;
    console.log(filteredProducts, "products is getting...");
  });

  function applySearchFilter() {
    filteredProducts = Allproducts.filter((product) =>
      product.brand.toLowerCase().includes(searchQuery.toLowerCase())
    );
  }

  const debouncedSearch = debounce(applySearchFilter, 300);
  function handleSearch(event) {
    searchQuery = event.target.value;
    debouncedSearch();
  }
  function handleAddProductClick() {
    showModal = !showModal;
    sidebarRender = false
  }

</script>

<aside
  class={isSidebarOpenVeriable === true
    ? "bg-[#334155] w-[40%] h-[92vh] fixed top-14 left-0 transform transition-transform ease-in-out duration-300 translate-x-0 md:translate-x-0 md:static sm:static overflow-y-auto"
    : "hidden"}
>
  <!-- Search bar Goes Here -->
  <SearchBarComponent filteredProducts={filteredProducts} handleSearch={handleSearch} />
  {#if showModal}
   <AddProductComp showModal={showModal} sidebarRender={sidebarRender} filteredProducts={filteredProducts} />
   {/if}
  <button class="border rounded p-2 w-[90%] ml-[5%] mt-4 text-yellow-300" on:click={handleAddProductClick}>ADD PRODUCT</button>

  <!-- Sidebar Content Goes Here -->
  {#if filteredProducts.length > 0 }
  <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 p-4">
    {#each filteredProducts as item (item.id)}
      <div class="border rounded p-2" key={item.id}>
        <img class=" object-cover" src={item.image} alt={item.id} />
        <h3 class="text-white font-semibold text-xl mb-2">
          Name : {item.brand}
        </h3>
        <h3 class="text-white mb-2">Price : ₹ {item.Price}</h3>
      </div>
    {/each}
  </div>
  {:else}
    <p class="text-white p-4">No products found for "{searchQuery}"</p>
  {/if}
</aside>
