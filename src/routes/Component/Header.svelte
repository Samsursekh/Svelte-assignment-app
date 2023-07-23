<!-- Sidebar.svelte -->
<script>
  import { page } from "$app/stores";
  import HeroSectionPage1 from "./HeroSectionPage1.svelte";
  import HeroSectionPage2 from "./HeroSectionPage2.svelte";
  let isSidebarOpen = false;
  import Sidebar from "./Sidebar.svelte";

  function toggleSidebar() {
    isSidebarOpen = !isSidebarOpen;
  }
</script>

<nav class="bg-blue-500 p-4">
  <ul class="flex items-center justify-evenly space-x-4">
    <button
      on:click={toggleSidebar}
      class="inline-block rounded bg-primary text-xs font-medium uppercase leading-tight text-white shadow-md transition duration-150 ease-in-out hover:bg-primary-700 hover:shadow-lg focus:bg-primary-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-primary-800 active:shadow-lg"
      data-te-sidenav-toggle-ref
      data-te-target="#sidenav-1"
      aria-controls="#sidenav-1"
      aria-haspopup="true"
    >
      <span class="block [&>svg]:h-5 [&>svg]:w-5 [&>svg]:text-white">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          fill="currentColor"
          class="h-5 w-5"
        >
          <path
            fill-rule="evenodd"
            d="M3 6.75A.75.75 0 013.75 6h16.5a.75.75 0 010 1.5H3.75A.75.75 0 013 6.75zM3 12a.75.75 0 01.75-.75h16.5a.75.75 0 010 1.5H3.75A.75.75 0 013 12zm0 5.25a.75.75 0 01.75-.75h16.5a.75.75 0 010 1.5H3.75a.75.75 0 01-.75-.75z"
            clip-rule="evenodd"
          />
        </svg>
      </span>
    </button>
    <!-- <button on:click={toggleSidebar} class="text-white font-bold">Sidebar</button> -->
    <li
      class:aria-current={$page.url.pathname === "/" ? "page" : undefined}
      class={$page.url.pathname === "/"
        ? "text-white font-bold"
        : "text-gray-200"}
    >
      <a href="/">Home</a>
    </li>
    <li
      class:aria-current={$page.url.pathname === "/page2" ? "page" : undefined}
      class={$page.url.pathname === "/page2"
        ? "text-white font-bold"
        : "text-gray-200"}
    >
      <a href="/page2">Second Page</a>
    </li>
  </ul>
</nav>

<div class=" flex justify-between">
  <Sidebar isSidebarOpenVeriable={isSidebarOpen} />
  <div class="flex justify-evenly w-[100%]">
    {#if $page.url.pathname === "/page2"}
      <HeroSectionPage2 />
    {:else if $page.url.pathname === "/"}
      <HeroSectionPage1 />
    {/if}
  </div>
</div>
