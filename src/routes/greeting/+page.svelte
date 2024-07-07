<script>
    import { page } from '$app/stores';
  
    $: name = $page.url.searchParams.get('name') || 'Anonymous';
  </script>
  
  <div class="container">
    <h1>New Page</h1>
    <p>Hello, {name}! You've been greeted from the new page.</p>
    <a href="/">Go back</a>
  </div>
  
  <style>
    .container {
      margin: 0;
      padding-top: 10vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      text-align: center;
    }
  </style>