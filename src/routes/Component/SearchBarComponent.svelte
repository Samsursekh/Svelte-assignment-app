<script>
    export let handleSearch;
</script>

<div>
    <input
      type="text"
      on:input={handleSearch}
      class="border rounded p-2 w-[90%] ml-[5%] mt-4 outline-none"
      placeholder="Search product here..."
    />
 </div>