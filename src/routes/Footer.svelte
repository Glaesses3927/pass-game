<script>
  import flowbitelogo from '$lib/logo_flowbite.svg';
  import tailwindcsslogo from '$lib/logo_tailwindcss.svg';
  import sveltelogo from '$lib/logo_svelte.svg';
  const today = new Date();
  const this_year = today.getFullYear();
</script>

<section class='flex flex-col items-center py-12'>
  <div class='flex items-center mx-auto mb-4'>
    <div class='h-px w-12 bg-gray-400'></div>
    <h3 class='text-sm font-bold text-gray-500 mx-3'>CREATED WITH</h3>
    <div class='h-px w-12 bg-gray-400'></div>
  </div>
  <div class='flex gap-4 justify-center'>
    <img src={sveltelogo} class='h-7 w-7' alt='sveltelogo'/>
    <img src={tailwindcsslogo} class='h-7 w-7' alt='tailwindcsslogo'/>
    <img src={flowbitelogo} class='h-7 w-7' alt='flowbitelogo'/>
  </div>
</section>
<footer class='text-center w-full bg-white'>
  <small>© { this_year } Glaesses All rights Reserved.</small>
</footer>