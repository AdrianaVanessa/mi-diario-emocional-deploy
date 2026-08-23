<template>
    <div class="dark:bg-gray-800 transition-colors flex h-screen bg-gray-100">
        <main class="flex-1 flex flex-col overflow-y-auto p-8 lg:p-1">
            <StreakAndTitle
              title="VIDEO - Aprendemos Juntos BBVA"
              :streak-count="streakCount"
            />
            <div class="bg-white rounded-2xl shadow-lg p-6 md:p-10 lg:p-16 max-w-4xl mx-auto my-6">
                <div class="text-center mb-8">
                    <h1 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight mb-2">
                        V. Completa. Recupera tu mente, reconquista tu vida.
                    </h1>
                    <p class="text-lg text-gray-600 font-semibold">Marian Rojas-Estapé, psiquiatra y escritora</p>
                    <p class="text-sm text-gray-500">22 jul 2024</p>
                </div>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <p class="mb-6 text-justify">
                      En este video, Marian Rojas-Estapé aborda la importancia de comprender cómo nuestros pensamientos, emociones y hábitos influyen en nuestro bienestar. Explica que es posible desarrollar una visión más optimista de la vida prestando atención a nuestra voz interior y aprendiendo a relacionarnos de forma más consciente con lo que ocurre a nuestro alrededor.
                    </p>
                    <br>
                    <br>
                    <p class="mb-6 text-justify">
                      La especialista también reflexiona sobre la necesidad de conectar con el presente en un contexto marcado por las pantallas, la sobreestimulación y las distracciones constantes. Prácticas como la introspección y la contemplación pueden ayudarnos a identificar lo que sentimos, comprender mejor nuestros patrones y valorar las pequeñas experiencias positivas de la vida cotidiana.
                    </p>
                    <br>
                    <br>
                    <p class="mb-6 text-justify">
                      Otro de los temas centrales es la relación entre la mente y el cuerpo. Comprender nuestras emociones y las reacciones de nuestro organismo puede ayudarnos a gestionar mejor determinadas situaciones, sin asumir que todas las dificultades emocionales representan necesariamente una enfermedad.
                    </p>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <div class="mb-8">
                        <div class="relative overflow-hidden w-full" style="padding-top: 56.25%">
                            <iframe
                                class="absolute top-0 left-0 w-full h-full rounded-2xl"
                                src="https://www.youtube.com/embed/S_0l-EqwknU?si=R_LydyDwWWnhnEfo"
                                title="YouTube video player"
                                frameborder="0"
                                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                                allowfullscreen>
                            </iframe>
                        </div>
                    </div>

                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                    </div>
                </div>

                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                        <h3 class="text-base font-bold text-gray-800 mb-2">Sobre la especialista</h3>
                        <p class="mb-2">
                            <span class="font-bold">Marian Rojas-Estapé</span> es médica especialista en psiquiatría y escritora española. Su trabajo de divulgación se centra en explicar de manera accesible la relación entre las emociones, el comportamiento y el bienestar psicológico. Es autora de libros como <span class="font-bold">Cómo hacer que te pasen cosas buenas</span>, <span class="font-bold">Encuentra tu persona vitamina</span> y <span class="font-bold">Recupera tu mente, reconquista tu vida</span>.
                        </p>
                        <p class="text-xs text-gray-500">
                            <span class="font-bold">Fuente:</span> Resumen elaborado a partir del contenido publicado por <span class="font-bold">Aprendemos Juntos 2030 - BBVA</span> <br></br>
                            <span class="font-bold">Contenido original:</span> <a href="https://www.youtube.com/watch?v=S_0l-EqwknU" class="text-blue-600 hover:underline" target="_blank" rel="noopener noreferrer">https://www.youtube.com/watch?v=S_0l-EqwknU</a>
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
import StreakAndTitle from "../components/StreakAndTitlePatient.vue";
import UserProfile from "../components/PatientProfile.vue";
import { computed } from 'vue';
  import { useAuthStore } from '@/store/auth';
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
