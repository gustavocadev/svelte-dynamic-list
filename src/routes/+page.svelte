<script lang="ts">
  interface Label {
    name: '';
  }

  let productTags: Label[] = [{ name: '' }];

  const addProductTag = () => {
    if (productTags.length === 5) return;
    productTags = [...productTags, { name: '' }];
  };

  const onSubmit = () => {
    console.log(productTags);
  };

  const deleteProductTag = (idx: number) => {
    if (idx === 0) {
      productTags = [{ name: '' }];
      return;
    }
    productTags = productTags.filter((_, i) => i !== idx);
  };
</script>

<main class="mx-auto container">
  <h1>Agregar hasta 5 etiquetas</h1>

  {#each productTags as tag, idx}
    <div class="gap-3 flex px-30 md:px-60 lg:px-96 my-2">
      <button
        class="btn btn-filled-tertiary"
        on:click={() => deleteProductTag(idx)}>-</button
      >
      <input
        type="text"
        placeholder={idx.toString()}
        class="px-3 "
        bind:value={tag.name}
      />

      {#if idx === productTags.length - 1 && productTags.length < 5}
        <button on:click={addProductTag} class="btn btn btn-filled-tertiary"
          >+</button
        >
      {/if}
    </div>
  {/each}

  <button
    type="submit"
    class="btn btn-filled-primary mx-auto flex"
    on:click={onSubmit}>Guardar</button
  >
</main>

<style>
</style>
