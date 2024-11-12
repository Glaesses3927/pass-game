<script lang="ts">
  import Rule from "./Rule.svelte";
  import rules from "$lib/rules.json";
  import { onMount } from "svelte";
  let pass: string = "";
  let current = 1;
  const len = rules.length;

  const func = (checkFunc: string) => {
    try {
      return new Function('pass', 'today', 'sum', `return ${checkFunc}`);
    } catch (err) {
      console.error(err);
      return new Function('', `return false`);
    }
  };
  $: results = rules.map(rule => ({
      ...rule,
      result: func(rule.check)(pass, today, sum),
    }));
  $: sortedResults = [...results].sort((a, b) => {
    if (a.result === b.result && a.result == true) return b.number - a.number;
    else if (a.result === b.result) return a.number - b.number;
    return a.result ? 1 : -1;
  });
  $: {
    let a = 0;
    for(let i=0; i<len; i++){
      if(results[i].result) a = i;
      else if(i==0) {a=-1; break;}
      else {a++;break;}
    }
    if(current<a+1) current = a+1;
  }

  let day = new Date().toLocaleDateString("ja-JP",{year:"numeric",month:"2-digit",day:"2-digit"});
  let today = day.replaceAll('/', '');
  $: sum = [...pass].reduce((acc, char) => acc + (parseInt(char) || 0), 0);
</script>

<div class="hidden bg-red-50 text-red-800 border-red-300"></div>

<div class="mb-6 w-full sm:w-[500px]">
  <label for="pw" class="block mb-2 text-sm font-medium text-gray-900">Password</label>
  <textarea bind:value={pass} id="pw" class="block w-full resize-none p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-lg focus:ring-blue-500 focus:border-blue-500" style="field-sizing: content;"></textarea>
</div>

{#each sortedResults as rule}
  {#if rule.number<=current}
    <Rule num={rule.number} content={rule.content} pass={rule.result}/>
  {/if}
{/each}

<div class="text-gray-400 text-sm">Rule7以降は順次追加</div>