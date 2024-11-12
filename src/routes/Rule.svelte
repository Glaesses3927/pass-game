<script>
  export let num;
  export let content;
  export let pass;
  let color = "red";
  $:{
    if(pass) color = "gray";
    else color = "red";
  }
</script>

<div class="w-full sm:w-[500px] p-4 mb-4 text-{color}-800 border border-{color}-300 rounded-lg bg-{color}-50" role="alert">
  <div class="flex items-center">
    <svg class="flex-shrink-0 w-4 h-4 me-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
      <path d="M10 .5a9.5 9.5 0 1 0 9.5 9.5A9.51 9.51 0 0 0 10 .5ZM9.5 4a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3ZM12 15H8a1 1 0 0 1 0-2h1v-3H8a1 1 0 0 1 0-2h2a1 1 0 0 1 1 1v4h1a1 1 0 0 1 0 2Z"/>
    </svg>
    <h3 class="text-lg font-medium">Rule {num}</h3>
  </div>
  <div class="mt-2 mb-4 text-sm">
    {content}
  </div>
</div>