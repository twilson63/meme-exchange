<script>
  import { take, toUpper } from "ramda";
  export let avatar;
  export let name;

  const colors = [
    "#C8792B",
    "#4BA75E",
    "#DDBC3F",
    "#449ECF",
    "#AB84B0",
    "#C8792B",
    "#CB3C34",
  ];

  function getRandomInt(max) {
    return Math.floor(Math.random() * max);
  }

  async function getBackgroundColor() {
    const i = getRandomInt(colors.length - 1);
    //bgColor = `bg-${colors[i]}`;
    return Promise.resolve(colors[i]);
  }
</script>

<div class="avatar">
  <div class="w-10 h-10">
    {#if name}
      {#await getBackgroundColor() then color}
        <div
          class="mask mask-circle h-full flex items-center justify-center text-white"
          style={`background-color: ${color};`}
        >
          {toUpper(take(2, name))}
        </div>
      {/await}
    {:else}
      <img class="mask mask-circle" src={avatar} />
    {/if}
  </div>
</div>
