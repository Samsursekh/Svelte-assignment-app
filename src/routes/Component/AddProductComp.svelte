<script>
    export let showModal;
    export let sidebarRender;
    export let filteredProducts;
    console.log(filteredProducts , "filteredProducts are there  ???");
    let count = 0;

    let brand = '';
    let type = '';
    let year = 2023; // Default value for the year select dropdown
    let kms = 0;
    let Description = '';
    let Price = 0;
    let image = '';
    function closeModal() {
      showModal = !showModal;
      sidebarRender = false;
      count++;
    }
  
    async function handleSubmit(event) {
    event.preventDefault();
    const newProduct = {
      brand,
      type,
      year,
      kms,
      Description,
      Price,
      image,
    };

    try {
      const response = await fetch('https://cars-mock-api-wjnb.onrender.com/cars', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(newProduct),
      });

      if (!response.ok) {
        throw new Error('Failed to add product.');
      }
      console.log('Product added successfully!');
      closeModal();
      location.reload();
    } catch (error) {
      console.error(error.message);
    }
  } 
  
  </script>
  
  {#if showModal}
  <div class="fixed top-0 left-0 w-full h-full flex items-center justify-center z-50">  
    <div class="bg-white rounded p-4 w-96">
      <h2 class="text-xl font-semibold mb-4">Add Product</h2>
      <form>
        <input class="border rounded p-2 w-full mb-2" type="text"  bind:value={brand} placeholder="Enter Brand Here">
        <div class="flex mb-2">
            <div class="w-1/2 pr-2">
              <select id="type" class="border rounded p-2 w-full"  bind:value={type}>
                <option value="">Select Type</option>
                <option value="Manual">Manual</option>
                <option value="Automatic">Automatic</option>
              </select>
            </div>
            <div class="w-1/2 pl-2">
              <select id="year" class="border rounded p-2 w-full"  bind:value={year}>
                <option value="">Select Year</option>
                <option value="2023">2023</option>
                <option value="2022">2022</option>
                <option value="2021">2021</option>
              </select>
            </div>
          </div>
        <input class="border rounded p-2 w-full mb-2" type="number" bind:value={kms} placeholder="Enter Kms Here">
        <textarea class="border rounded p-2 w-full mb-2" bind:value={Description} placeholder="Enter Description Here"></textarea>
        <input class="border rounded p-2 w-full mb-2" type="number" bind:value={Price} placeholder="Enter Price Here">
        <input class="border rounded p-2 w-full mb-2" type="text" bind:value={image} placeholder="Enter Image URL Here">
      </form>  
      <div class="flex justify-end mt-4">
        <button class="border rounded p-2 mr-2" on:click={closeModal}>Cancel</button>
        <button class="border rounded p-2 bg-blue-500 text-white" on:click={handleSubmit}>Add Product</button>
      </div>
    </div>
  </div>
  {/if}

  <!-- {#if isSubmitted}
  <p class="fixed bottom-0 left-0 w-full bg-green-500 text-white p-4 text-center">
    Product added successfully! The form will reset for the next entry.
  </p>
  {/if} -->
  