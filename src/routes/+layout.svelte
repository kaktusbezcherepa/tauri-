<script>
    import { blur } from 'svelte/transition';
    import { page } from '$app/stores';
  </script>
  
  {#key $page.url.pathname}
    <div in:blur={{  duration: 1500 }}>
      <slot />
    </div>
  {/key}
