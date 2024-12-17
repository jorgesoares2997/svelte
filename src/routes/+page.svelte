<script>
  const lista = [
    { nome: "Adilso", idade: "44" },
    { nome: "Jorgin", idade: "25" },
    { nome: "Manuquinha", idade: "32" },
  ];

  for (let nome of lista) {
    console.log(nome);
  }
</script>

<h1 class="text-green-500">Meu site</h1>

{#each lista as pessoa}
  <p>{pessoa.nome}</p>
{/each}
