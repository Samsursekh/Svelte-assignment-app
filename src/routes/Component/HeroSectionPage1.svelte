<!-- HeroSectionPage1.svelte -->
<script>
  import { onMount, onDestroy } from "svelte";
  import { writable } from "svelte/store";

  // Create a writable store to hold the ItemID
  const itemIDStore = writable(null);

  // Subscribe to changes in the itemIDStore
  let selectedItem = null;
  const unsubscribe = itemIDStore.subscribe((value) => {
    if (value) {
      fetchItemData(value);
    } else {
      selectedItem = null; // Reset the selectedItem when ItemID is null
    }
  });

  async function fetchItemData(ItemID) {
    try {
      const response = await fetch(`https://cars-mock-api-wjnb.onrender.com/cars/${ItemID}`);
      if (response.ok) {
        selectedItem = await response.json();
      } else {
        console.error("Failed to fetch item data:", response);
      }
    } catch (error) {
      console.error("Error fetching item data:", error);
    }
  }

  onMount(() => {
    // Get the ID from the URL parameter and update the itemIDStore
    const ItemID = window.location.hash.replace("#/", "");
    fetchItemData(ItemID)
    itemIDStore.set(ItemID);
   
  });

  // Unsubscribe from the store when the component is unmounted
  onDestroy(() => {
    unsubscribe();
  
  });
</script>

<div>
  {#if selectedItem}
    <h2>{selectedItem.brand}</h2>
    <p>Price: ₹ {selectedItem.Price}</p>
    <img src={selectedItem.image} alt={selectedItem.brand} />
    <!-- Display other details of the selected item here -->
  {:else}
    <p>Loading...</p>
  {/if}
</div>
