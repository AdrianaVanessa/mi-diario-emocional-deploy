<template>
    <div class="dark:bg-gray-800 transition-colors flex h-screen bg-gray-100">
        <main class="flex-1 flex flex-col overflow-y-auto p-8 lg:p-1">
            <StreakAndTitle
              title="VIDEO - Mindfulness"
              :streak-count="streakCount"
            />
            <div class="bg-white rounded-2xl shadow-lg p-6 md:p-10 lg:p-16 max-w-4xl mx-auto my-6">
                <div class="text-center mb-8">
                    <h1 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight mb-2">
                        Cómo Regular y Gestionar Emociones Con Mindfulness.
                    </h1>
                    <p class="text-lg text-gray-600 font-semibold">Helena Echeverría, psicóloga</p>
                    <p class="text-sm text-gray-500">12 may 2022</p>
                </div>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <p class="mb-6 text-justify">
                        El mindfulness, también conocido como atención plena, es una práctica que busca dirigir conscientemente la atención hacia el momento presente. Consiste en observar pensamientos, emociones y sensaciones sin juzgarlos ni tratar de evitarlos, lo que puede favorecer una mayor comprensión de nuestras propias reacciones emocionales.
                    </p>
                    <br>
                    <br>
                    <p class="mb-6 text-justify">
                      En este episodio, Helena Echeverría explica algunos conceptos básicos relacionados con las emociones, como su función y los diferentes elementos que intervienen cuando experimentamos una respuesta emocional. También aborda la importancia de reconocer lo que sentimos antes de intentar regularlo.
                    </p>
                    <br>
                    <br>
                    <p class="mb-6 text-justify">
                      A lo largo del contenido se presenta el mindfulness como una herramienta que puede ayudarnos a relacionarnos de una manera más consciente con nuestras emociones. Mediante un ejercicio práctico de atención plena, se propone observar las sensaciones y pensamientos que aparecen en el momento presente sin reaccionar automáticamente ante ellos.
                    </p>
                    <br>
                    <br>
                    <p class="mb-6 text-justify">
                      El objetivo es desarrollar una mayor conciencia emocional y aprender estrategias que puedan contribuir a gestionar de una forma más consciente situaciones cotidianas de estrés o malestar.
                    </p>


                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <div class="mb-8">
                        <div class="relative overflow-hidden w-full" style="padding-top: 56.25%">
                            <iframe
                                class="absolute top-0 left-0 w-full h-full rounded-2xl"
                                src="https://www.youtube.com/embed/RdAhXhP26Uo?si=fZZzIsgyUmSO-lun"
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
                            <span class="font-bold">Helena Echeverría</span> es psicóloga y fundadora de PsicoGuías. Su trabajo de divulgación aborda temas relacionados con la psicología, las emociones, la ansiedad, el estrés y el mindfulness.
                        </p>
                        <p class="text-xs text-gray-500">
                            <span class="font-bold">Fuente:</span> Resumen elaborado a partir del contenido publicado por PsicoGuías | Podcast Psicología.<br></br>
                            <span class="font-bold">Contenido original:</span> <a href="https://www.youtube.com/watch?v=RdAhXhP26Uo" class="text-blue-600 hover:underline" target="_blank" rel="noopener noreferrer">https://www.youtube.com/watch?v=RdAhXhP26Uo</a>
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
