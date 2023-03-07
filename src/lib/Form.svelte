<form class="flex flex-col gap-4 mx-2">
  <div class="flex flex-col gap-2">
    <label for="fullname">Nombre Completo</label>
    <input
      class="border p-2"
      id="fullname"
      type="text"
      placeholder="John Doe"
    />
  </div>
  <div class="flex flex-col gap-2">
    <label for="email">Correo Electrónico</label>
    <input
      class="border p-2"
      id="email"
      type="text"
      placeholder="johndoe@mail.com"
    />
  </div>
  <div class="flex flex-col gap-2">
    <label for="content">Describe tu Idea</label>
    <textarea
      class="border p-2 resize-none"
      id="content"
      placeholder="johndoe@mail.com"
    />
  </div>
  <div class="flex flex-col gap-2">
    <button
      class="bg-indigo-400 p-2 text-white text-lg font-semibold hover:bg-indigo-500 rounded-md"
      >Enviar</button
    >
  </div>
</form>
