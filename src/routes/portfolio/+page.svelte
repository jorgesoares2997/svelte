<script>
  export let data;

  let categories = [
    { name: "All", isActive: true },
    { name: "Animation", isActive: false },
    { name: "Web design", isActive: false },
    { name: "App design", isActive: false },
    { name: "Branding", isActive: false },
  ];

  let currentCategory = "All";
  let portfolioItems = data.items;

  function filterPortfolio() {
    portfolioItems = data.items.filter((item) => {
      return item.category === currentCategory || currentCategory === "All";
    });
  }

  /**
   * @param {number} index
   */
  function activateCategory(index) {
    categories = categories.map((category, i) => ({
      ...category,
      isActive: i === index,
    }));

    currentCategory = categories[index].name; // Atualiza a categoria ativa
    filterPortfolio(); // Filtra os itens do portfólio com base na categoria ativa
  }
</script>

<section class="bg-white dark:bg-gray-900">
  <div class="container px-6 mx-auto">
    <!-- Botões de categorias -->
    <div
      class="flex py-4 overflow-x-auto md:justify-center sticky top-0 bg-white dark:bg-gray-900 z-10"
      style="scrollbar-width: thin; scrollbar-color: #d1d5db transparent;"
    >
      {#each categories as category, index}
        <button
          class={`h-12 px-8 py-2 -mb-px text-sm sm:text-base whitespace-nowrap focus:outline-none ${
            category.isActive
              ? "text-blue-600 border-b-2 border-blue-500 dark:border-blue-400 dark:text-blue-300"
              : "text-gray-700 border-b-2 border-gray-200 dark:text-white dark:border-gray-700 hover:border-gray-400"
          }`}
          on:click={() => activateCategory(index)}
          aria-pressed={category.isActive}
        >
          {category.name}
        </button>
      {/each}
    </div>

    <!-- Conteúdo -->
    <section class="mt-8 space-y-8 lg:mt-12">
      {#each portfolioItems as item}
        <section class="lg:flex lg:items-center">
          <a href={`/portfolio/${item.slug}`}>
            <div class="lg:w-1/2">
              <p
                class="text-lg tracking-wider text-blue-500 uppercase dark:text-blue-400"
              >
                {item.title}
              </p>
              <h2
                class="mt-2 text-2xl font-semibold text-gray-800 capitalize dark:text-white"
              >
                {item.subtitle}
              </h2>
            </div>
            <div class="mt-4 lg:w-1/2 lg:mt-0">
              <img
                class="object-cover w-full h-64 rounded-lg md:h-96"
                src={item.image}
                alt={item.title}
              />
            </div></a
          >
        </section>
      {/each}
    </section>
  </div>
</section>
