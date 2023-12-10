<script lang="ts">
  import "duoyun-ui/svelte/button";
  import "duoyun-ui/svelte/card";
  import "duoyun-ui/svelte/paragraph";
  import "duoyun-ui/svelte/space";
  import "duoyun-ui/svelte/color-picker";
  import type { DuoyunColorPickerElement } from "duoyun-ui/svelte/color-picker";

  let colorElement: DuoyunColorPickerElement | undefined;
  let cardActions = [
    { text: "Action1", handle: console.log },
    { text: "Action2", handle: console.log },
    { text: "Action3", handle: console.log },
    { text: "Action4", handle: console.log },
  ];
  let cardHeader = "This header";
  let color: `#${string}` = "#f0f";

  const clickHandle = () => {
    cardActions = cardActions.reverse();
    cardHeader = [...cardHeader].reverse().join("");
  };

  const onChange = (e: CustomEvent) => {
    color = e.detail;
  };
</script>

<div>
  <dy-paragraph>
    <dy-space>
      <dy-button on:click={() => colorElement?.showPicker()}>
        Open Color Picker
      </dy-button>
      <dy-color-picker
        bind:this={colorElement}
        on:change={onChange}
        value={color}
        alpha
      ></dy-color-picker>
    </dy-space>
  </dy-paragraph>

  <dy-card
    on:click={clickHandle}
    class="card"
    avatar="https://api.dicebear.com/5.x/bottts-neutral/svg"
    preview="https://picsum.photos/400/300"
    header={cardHeader}
    detail={`CE`}
    actions={cardActions}
  >
    Fugiat do laboris ad officia in anim qui mollit nulla reprehenderit pariatur
    anim sunt.
  </dy-card>
</div>

<style>
  .card {
    width: 240px;
  }
</style>
