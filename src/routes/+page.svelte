<script>
  import HomeController from "../components/home.svelte";
  import AboutController from "../components/about.svelte";
  import { Fullpage, FullpageSection } from "svelte-fullpage";
  let fullpageController;
  let hasBeenAboutActive = false;
  $: if ($fullpageController === 1) {
    hasBeenAboutActive = true;
  }
  $: isAboutActive = hasBeenAboutActive;
  $: console.log(`Active section: ${$fullpageController}`);
</script>

<Fullpage bind:controller={fullpageController}>
  <FullpageSection title="Home" class="homepage">
    <HomeController />
  </FullpageSection>
  <FullpageSection title="About me">
    <AboutController {isAboutActive} />
  </FullpageSection>
</Fullpage>

<style global lang="scss">
  :global(body) {
    height: 100vh;
  }
</style>
