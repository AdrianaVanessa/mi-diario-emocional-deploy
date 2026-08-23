<template>
    <div class="dark:bg-gray-800 transition-colors flex h-screen bg-gray-100">
        <main class="flex-1 flex flex-col overflow-y-auto p-8 lg:p-1">
            <StreakAndTitle
              title="Podcast - Vamos a meditar"
              :streak-count="streakCount"
            />
            <div class="bg-white rounded-2xl shadow-lg p-6 md:p-10 lg:p-16 max-w-4xl mx-auto my-6">
                <div class="text-center mb-8">
                    <h1 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight mb-2">
                        Ejercicio de respiración para calmar la ansiedad.
                    </h1>
                    <p class="text-lg text-gray-600 font-semibold">Por Glenda Yoga</p>
                    <p class="text-sm text-gray-500">16 de noviembre 2018</p>
                </div>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <p class="mb-6 text-justify">
                        Un ejercicio guiado de respiración consciente orientado a favorecer la relajación y dirigir la atención al momento presente.
                    </p>
                    <br>

                    <p class="mb-6 text-justify">
                        En este episodio, Glenda Yoga guía un ejercicio de respiración consciente que puede realizarse durante unos minutos como una práctica de relajación. El objetivo es prestar atención al ritmo de la respiración y hacer una pausa frente a las preocupaciones o estímulos del día a día.
                    </p>
                    <br>

                    <p class="mb-6 text-justify">
                        La respiración consciente es una práctica utilizada en ejercicios de meditación y mindfulness para dirigir la atención hacia el presente. Este episodio propone utilizarla como una herramienta sencilla para favorecer una sensación de calma y reconocer las sensaciones del cuerpo.
                    </p>
                    <br>

                    <p class="mb-6 text-justify">
                        La actividad puede incorporarse como un ejercicio de bienestar y relajación, sin sustituir la atención de un profesional cuando existe malestar emocional persistente o intenso.
                    </p>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <div class="mb-8">
                        <div class="relative overflow-hidden w-full" style="padding-top: 5%">
                            <iframe
                                style="border-radius:12px"
                                src="https://open.spotify.com/embed/episode/5kVQKI7fpewVRVzEnOFxoM?utm_source=generator"
                                width="100%"
                                height="352"
                                frameBorder="0"
                                allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
                                loading="lazy">
                            </iframe>
                        </div>
                    </div>

                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                    </div>
                </div>

                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                        <h3 class="text-base font-bold text-gray-800 mb-2">Sobre la instructora</h3>
                        <p class="mb-2">
                            <strong>Glenda Yoga</strong> comparte contenido relacionado con yoga, meditación y prácticas de respiración consciente.

                        </p>
                        <p class="text-xs text-gray-500">
                            <strong>Fuente:</strong> Resumen elaborado a partir del episodio “Ejercicio de Respiración para calmar la ansiedad”, publicado por Glenda Yoga y disponible en Spotify.<br></br>
                        </p>
                        <p class="text-xs text-gray-500">
                          <strong>Contenido original:</strong> <a href="https://open.spotify.com/embed/episode/5kVQKI7fpewVRVzEnOFxoM" class="text-blue-600 hover:underline" target="_blank" rel="noopener noreferrer">https://open.spotify.com/embed/episode/5kVQKI7fpewVRVzEnOFxoM</a>
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
