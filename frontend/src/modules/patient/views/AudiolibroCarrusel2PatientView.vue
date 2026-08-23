<template>
    <div class="dark:bg-gray-800 transition-colors flex h-screen bg-gray-100">
        <main class="flex-1 flex flex-col overflow-y-auto p-8 lg:p-1">
            <StreakAndTitle
              title="Audiolibro completo"
              :streak-count="streakCount"
            />
            <div class="bg-white rounded-2xl shadow-lg p-6 md:p-10 lg:p-16 max-w-4xl mx-auto my-6">
                <div class="text-center mb-8">
                    <h1 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight mb-2">
                        Practicando el Poder del Ahora
                    </h1>
                    <p class="text-lg text-gray-600 font-semibold">Por Eckhart Tolle</p>
                    <p class="text-sm text-gray-500">Edición en español, 2014</p>
                </div>

                <p class="text-xl md:text-2xl font-light text-gray-700 italic text-center leading-relaxed mb-8">
                    “Una invitación a dirigir nuestra atención al presente y observar con mayor conciencia nuestros pensamientos y emociones.”
                </p>


                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <p class="mb-6 text-justify">
                      En <strong>Practicando el Poder del Ahora</strong>, Eckhart Tolle presenta una serie de reflexiones y ejercicios orientados a desarrollar una mayor conciencia del momento presente. El autor propone observar nuestros pensamientos y emociones sin identificarnos completamente con ellos, con el objetivo de comprender mejor la manera en que reaccionamos ante distintas situaciones.
                      </p>
                      <br>
                    <br>

                    <p class="mb-6 text-justify">
                       A lo largo del audiolibro se aborda la importancia de prestar atención a lo que ocurre en el presente, en lugar de permanecer constantemente preocupados por el pasado o anticipando situaciones futuras. Esta perspectiva busca favorecer una relación más consciente con nuestros pensamientos y con las experiencias cotidianas.
                    </p>
                    <br>
                    <br>

                    <p class="mb-6 text-justify">
                      El contenido también invita a reconocer patrones mentales que pueden generar preocupación o malestar y a practicar una actitud de observación y aceptación. De esta manera, la atención plena se presenta como una herramienta para conocernos mejor y desarrollar una mayor conciencia sobre nuestras propias emociones.
                    </p>
                    <br>
                    <br>

                    <p class="mb-6 text-justify">
                      Este material puede complementar prácticas como el mindfulness y la introspección, al proponer ejercicios y reflexiones dirigidos a fortalecer la atención y la conexión con el momento presente.
                    </p>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <div class="mb-8">
                        <div class="relative overflow-hidden w-full" style="padding-top: 5%">
                            <iframe
                              src="https://open.spotify.com/embed/album/3NszfjJLr0BcXMx3S42ReZ"
                              width="100%"
                              height="352"
                              frameborder="0"
                              allowfullscreen=""
                              allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
                              loading="lazy">
                            </iframe>
                        </div>
                    </div>

                <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                </div>
            </div>

                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                        <h3 class="text-base font-bold text-gray-800 mb-2">Sobre el autor</h3>
                        <p class="mb-2">
                            <strong>Eckhart Tolle</strong>es un escritor y conferenciante conocido por sus obras relacionadas con la atención plena, la conciencia y el desarrollo personal. Entre sus libros más conocidos se encuentran El poder del ahora y Una nueva Tierra.
                        </p>
                        <p class="text-xs text-gray-500">
                            <strong>Fuente: </strong> Resumen elaborado a partir del audiolibro <strong>Practicando el Poder del Ahora</strong>, de Eckhart Tolle, disponible en Spotify. <br></br>

                        </p>
                        <p class="text-xs text-gray-500">
                          <strong>Contenido original:</strong> <a href="https://open.spotify.com/embed/album/3NszfjJLr0BcXMx3S42ReZ" class="text-blue-600 hover:underline" target="_blank" rel="noopener noreferrer">https://open.spotify.com/embed/album/3NszfjJLr0BcXMx3S42ReZ</a>
                        </p>
                    </div>
                </div>
            </div>
        <router-view />
        </main>
        <UserProfile />
    </div>
</template>

<script setup lang="ts">
import StreakAndTitle from "../components/StreakAndTitlePatient.vue"
    import { computed } from 'vue';
  import { useAuthStore } from '@/store/auth';
import UserProfile from "../components/PatientProfile.vue";

    const authStore = useAuthStore();

    interface PatientProfile {
    name: string;
    paternal_last_name: string;
    maternal_last_name: string;
    email: string;
    alias: string;
    gender: string;
    professional_name?: string;
    is_linked: boolean;
    current_streak: number;
}

const streakCount = computed(() => {
  // Primero, verificamos si el usuario es un paciente y si su perfil ha cargado
  if (authStore.userType === 'patient' && authStore.userProfile) {
    // Si es así, le decimos a TypeScript que trate el perfil como un PatientProfile
    // y accedemos a 'current_streak' de forma segura.
    return (authStore.userProfile as PatientProfile).current_streak || 0;
  }
  // Si no es un paciente, la racha es 0.
  return 0;
});
</script>
