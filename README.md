#### Page 1:
 ***The page structure should include the following components:***

****1. Collapsible Sidebar/Drawer: ****
• The sidebar should contain a list of dummy data (referred to as data1) presented in the form of cards. ✅
• The sidebar should also feature a search functionality, allowing users to easily locate specific cards. ✅
• Additionally, an option to add new cards should be provided, facilitated by a modal window. ✅
2. Content Area:
• By default, the content area should remain empty.
• Once a card within the sidebar is clicked, the content area should dynamically populate with a list of nested dummy data (referred to as data2) specific to the selected card.
• Similar to the sidebar, the content area should include search and filter functionalities, enabling users to efficiently explore and navigate the nested data.
• Furthermore, users should be able to add new cards to the content area via a modal window.
• At the top of the content area, an expand button should be available to reveal the contents of the currently selected card (data2) on the second page.

For example, the sidebar could contain names and descriptions of various car companies, while the content area would display all the car models sold by the selected company.

Page 2:
The structure of this page should consist of the following component:
1. Content Area:
• This area should display dummy data in the form of cards, similar to the content area on page 1.
• Users should have the ability to search and filter the displayed data, ensuring an efficient browsing experience.
• Additionally, a modal window should allow users to add new cards to the content area.

It is important to note that data persistence is a requirement both across pages and within sessions.

NOTE
### It is not expected from you to implement all the functionalities mentione d#### above, your willingness and ability to learn is a more significant factor in evaluating your performance. However, a complete and comprehensive project will be highly regarded during the assessment process.

Quick video introduction to svelte and tailwind:
Svelte in 100 Seconds - YouTube
https://www.youtube.com/watch?v=rv3Yq-B8qp4
The easiest realtime app I’ve ever built - YouTube
https://www.youtube.com/watch?v=UbOaAtHWidc
Tailwind in 100 Seconds - YouTube
https://www.youtube.com/watch?v=mr15Xzb1Ook
Ultimate Tailwind CSS Tutorial // Build a Discord-inspired Animated Navbar - YouTube
https://www.youtube.com/watch?v=pfaSUYaSgRo

Reference Documentation:
https://svelte.dev/
https://kit.svelte.dev/
https://tailwindcss.com/
https://tailwindcss.com/docs/guides/sveltekit
https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage





















# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm create svelte@latest

# create a new project in my-app
npm create svelte@latest my-app
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.
