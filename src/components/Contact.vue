<template>
    <section class="pb-14">
    <div class="max-w-screen-xl mx-auto px-4 text-black dark:text-white md:px-8">
        <div class="max-w-lg mx-auto gap-12 justify-between lg:flex lg:max-w-none">
        <div class="max-w-lg space-y-3">
            <h2 class="text-4xl font-semibold color">CONTACTO</h2>
            <p class="text-black  dark:text-white text-3xl font-thin sm:text-4xl">
            Hazme saber en qué puedo ayudarte
            </p>
            <p>
            Estoy aquí para ayudarte y responder cualquier consulta que tengas! Completa el formulario o utiliza la información de contacto para comunicarnos.
            </p>
            <div>
            <ul v-for="(contactMethod, index) in contactMethods" :key="index" class="mt-6 flex flex-wrap gap-x-10 gap-y-6 items-center">
                <li class="flex items-center gap-x-3">
                    <div class="flex-none text-black" v-html="contactMethod.icon"></div>
                    <p>{{contactMethod.contact}}</p>
                </li>

            </ul>
            </div>
        </div>
        <div class="flex-1 mt-12 sm:max-w-lg lg:max-w-md">
            <form on:submit|preventDefault={handleSubmit} class="space-y-5">
            <div>
                <label class="font-medium">
                Nombre completo
                </label>
                <input type="text" bind:value={form.fullName} required class="w-full mt-2 px-3 py-2 text-black bg-transparent outline-none border focus:border-indigo-600 shadow-sm rounded-lg" />
            </div>
            <div>
                <label class="font-medium">
                Correo
                </label>
                <input type="email" bind:value={form.email} required class="w-full mt-2 px-3 py-2 text-black bg-transparent outline-none border focus:border-indigo-600 shadow-sm rounded-lg" />
            </div>
            <div>
                <label class="font-medium">
                Empresa
                </label>
                <input type="text" bind:value={form.company} required class="w-full mt-2 px-3 py-2 text-black bg-transparent outline-none border focus:border-indigo-600 shadow-sm rounded-lg" />
            </div>
            <div>
                <label class="font-medium">
                Mensaje
                </label>
                <textarea bind:value={form.message} required class="w-full mt-2 h-36 px-3 py-2 resize-none appearance-none bg-transparent outline-none border focus:border-indigo-600 shadow-sm rounded-lg"></textarea>
            </div>
            <button @click="handleSubmit" type="submit" class="w-full px-4 py-2 text-white font-medium bg-indigo-600 hover:bg-indigo-500 active:bg-indigo-600 rounded-lg duration-150">
                Enviar
            </button>
            </form>
        </div>
        </div>
    </div>
    </section>
</template>

<script>
 export default {
  data() {
    return {
            contactMethods: [
                {
                    icon: `<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" strokeWidth={1.5} stroke="#F34F29" class="w-6 h-6">
                            <path strokeLinecap="round" strokeLinejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
                            </svg>`,
                    contact: "agustincamejo03@gmail.com"
                },
                {
                    icon: `<svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg " class="w-6 h-6">
                                <path fill="#4F46E5" d="M18.44 3.06H5.56a2.507 2.507 0 0 0-2.5 2.5v12.88a2.507 2.507 0 0 0 2.5 2.5h12.88a2.5 2.5 0 0 0 2.5-2.5V5.56a2.5 2.5 0 0 0-2.5-2.5Zm1.5 15.38a1.511 1.511 0 0 1-1.5 1.5H5.56a1.511 1.511 0 0 1-1.5-1.5V5.56a1.511 1.511 0 0 1 1.5-1.5h12.88a1.511 1.511 0 0 1 1.5 1.5Z"/>
                                <path fill="#4F46E5" d="M6.376 10.748a1 1 0 1 1 2 0v6.5a1 1 0 0 1-2 0Z"/>
                                <circle cx="7.376" cy="6.744" r="1" fill="#4F46E5"/>
                                <path fill="#4F46E5" d="M17.62 13.37v3.88a1 1 0 1 1-2 0v-3.88a1.615 1.615 0 1 0-3.23 0v3.88a1 1 0 0 1-2 0v-6.5a1.016 1.016 0 0 1 1-1a.94.94 0 0 1 .84.47a3.609 3.609 0 0 1 5.39 3.15Z"/>
                            </svg>`,
                    contact: "Agustin Camejo"
                },
            ]
        };
    },
    methods: {
        async handleSubmit() {
        try {
            const response = await fetch('https://formspree.io/f/mayggkqw', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
                body: JSON.stringify(this.form),
            });

            if (response.ok) {
                 console.log('Formulario enviado con éxito');
                // Puedes realizar acciones adicionales después de enviar el formulario
            } else {
                console.log('1');
            }
        } catch (error) {
            console.error('Error al enviar el formulario', error);
        }
      },
    },
 };

  let form = {
    fullName: '',
    email: '',
    company: '',
    message: ''
  };

  
</script>

<style scoped>
@media (max-width: 768px) {
    h2{
      text-align: center;
    }
}

</style>
