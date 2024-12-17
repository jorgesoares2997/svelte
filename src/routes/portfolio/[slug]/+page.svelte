<script lang="ts">
  export let data;
  const items = data.items.find((params) => params.slug === data.slug);
</script>

<h1>{items?.title}</h1>
<h1>hello</h1>

