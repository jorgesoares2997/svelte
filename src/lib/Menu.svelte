<script>
  import Logo from "./Logo.svelte";
  import { page } from "$app/stores";

  const links = [
    { href: "/", label: "home" },
    { href: "/contato", label: "contato" },
    { href: "/portfolio", label: "portfolio" },
    { href: "/sobre", label: "sobre" },
    { href: "/faq", label: "perguntas frequentes" },
  ];
</script>

<nav class="bg-white shadow dark:bg-gray-800">
  <div
    class="container flex items-center justify-center p-6 mx-auto text-gray-600 capitalize dark:text-gray-300"
  >
    <Logo />
    {#each links as { href, label }}
      <a
        {href}
        class="mx-1.5 sm:mx-6 transition-colors duration-300 transform
            border-b-2
            {$page.url.pathname === href
          ? 'text-gray-800 dark:text-gray-200 border-blue-500'
          : 'border-transparent hover:text-gray-800 dark:hover:text-gray-200 hover:border-blue-500'}"
      >
        {label}
      </a>
    {/each}
  </div>
</nav>
