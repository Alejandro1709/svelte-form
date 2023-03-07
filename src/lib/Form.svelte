<script>
  $: fullName = '';
  $: email = '';
  $: content = '';

  const handleSubmitForm = () => {
    const message = {
      name: fullName,
      email,
      content,
    };
    console.log(message);
  };
</script>

<form
  class="flex flex-col gap-4 mx-2"
  on:submit|preventDefault={handleSubmitForm}
>
  <div class="flex flex-col gap-2">
    <label for="fullname">Nombre Completo</label>
    <input
      class="border p-2"
      id="fullname"
      type="text"
      placeholder="John Doe"
      bind:value={fullName}
    />
  </div>
  <div class="flex flex-col gap-2">
    <label for="email">Correo Electrónico</label>
    <input
      class="border p-2"
      id="email"
      type="text"
      placeholder="johndoe@mail.com"
      bind:value={email}
    />
  </div>
  <div class="flex flex-col gap-2">
    <label for="content">Describe tu Idea</label>
    <textarea
      class="border p-2 resize-none"
      id="content"
      placeholder="johndoe@mail.com"
      bind:value={content}
    />
  </div>
  <div class="flex flex-col gap-2">
    <button
      class="bg-indigo-400 p-2 text-white text-lg font-semibold hover:bg-indigo-500 rounded-md"
      >Enviar</button
    >
  </div>
  <p>Cargando...</p>
</form>
