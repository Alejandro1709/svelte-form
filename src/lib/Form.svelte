<script>
  import { supabase } from './supabaseClient';

  $: fullName = '';
  $: email = '';
  $: content = '';
  $: state = 'idle';

  const handleSubmitForm = async () => {
    state = 'loading';

    if (!fullName || !email || !content) {
      state = 'error';
      return;
    }

    const message = {
      fullname: fullName,
      email,
      content,
    };

    const { data, error } = await supabase
      .from('entry')
      .insert(message)
      .select();

    if (error) {
      state = 'error';
      return;
    }
    state = 'success';

    console.log(data, error);
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
      disabled={state === 'success'}
      class="bg-indigo-400 p-2 text-white text-lg font-semibold hover:bg-indigo-500 rounded-md cursor-pointer"
      >Enviar</button
    >
  </div>
  {#if state === 'loading'}
    <p>Cargando...</p>
  {:else if state === 'success'}
    <p>Mensaje enviado!</p>
  {:else if state === 'error'}
    <p>Hubo un error...</p>
  {:else}
    <p>Cuando este listo, mande el mensaje.</p>
  {/if}
</form>
