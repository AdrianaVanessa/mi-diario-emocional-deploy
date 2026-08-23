<template>
    <div class="dark:bg-gray-800 transition-colors flex h-screen bg-gray-100">
        <main class="flex-1 flex flex-col overflow-y-auto p-8 lg:p-1">
            <StreakAndTitle
              title="Audiolibro"
              :streak-count="streakCount"
            />
            <div class="bg-white rounded-2xl shadow-lg p-6 md:p-10 lg:p-16 max-w-4xl mx-auto my-6">
                <div class="text-center mb-8">
                    <h1 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight mb-2">
                        El poder de escuchar
                    </h1>
                    <p class="text-lg text-gray-600 font-semibold">Por Ismael Cala</p>
                    <p class="text-sm text-gray-500">Edición abreviada en español, 2014</p>
                </div>

                <p class="text-xl md:text-2xl font-light text-gray-700 italic text-center leading-relaxed mb-8">
                    “Una reflexión sobre la importancia de aprender a escuchar a los demás y a nosotros mismos para mejorar nuestra comunicación y nuestras relaciones.”
                </p>


                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <p class="mb-6 text-justify">
                      En <strong>El Poder de Escuchar</strong>, Ismael Cala aborda la importancia de desarrollar una escucha más consciente como parte de nuestra manera de comunicarnos y relacionarnos con otras personas. A partir de reflexiones y experiencias personales, el autor explica cómo prestar verdadera atención puede ayudarnos a comprender mejor las ideas, necesidades y emociones de quienes nos rodean.
                      </p>

                    <p class="mb-6 text-justify">
                      A lo largo del audiolibro se plantea que escuchar implica mucho más que permanecer en silencio mientras otra persona habla. Requiere atención, apertura y disposición para comprender diferentes perspectivas. Desarrollar esta capacidad puede favorecer una comunicación más clara y contribuir a fortalecer nuestras relaciones personales y profesionales.
                    </p>

                    <p class="mb-6 text-justify">
                      El autor también invita a dirigir la escucha hacia nosotros mismos. Reconocer nuestras emociones, necesidades y pensamientos puede ayudarnos a comprender mejor nuestras propias reacciones y tomar decisiones de una manera más consciente.
                    </p>

                    <p class="mb-6 text-justify">
                      Este material puede complementar el desarrollo de habilidades relacionadas con la empatía, la comunicación y el autoconocimiento, al proponer la escucha como una herramienta para mejorar tanto nuestra relación con otras personas como la forma en que comprendemos nuestras propias experiencias.
                    </p>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <div class="mb-8">
                        <div class="relative overflow-hidden w-full" style="padding-top: 5%">
                          <iframe data-testid="embed-iframe" style="border-radius:12px" src="https://open.spotify.com/embed/album/06KkA6HwQFZvfhFy0H8SvU?utm_source=generator&si=292923ce33224c14" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
                        </div>
                    </div>

                <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                </div>
            </div>

                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                        <h3 class="text-base font-bold text-gray-800 mb-2">Sobre el autor</h3>
                        <p class="mb-2">
                            <strong>Ismael Cala</strong> es periodista, escritor y conferenciante. A lo largo de su trayectoria profesional ha desarrollado contenidos relacionados con la comunicación, el liderazgo, el crecimiento personal y las relaciones interpersonales. En <strong>El Poder de Escuchar</strong>, comparte reflexiones sobre el papel que tiene la escucha en la manera en que nos comunicamos y nos relacionamos con los demás.
                        </p>
                        <p class="text-xs text-gray-500">
                            <strong>Fuente: </strong> Resumen elaborado a partir del audiolibro <strong>El Poder de Escuchar (abreviado)</strong>, de Ismael Cala, publicado por <strong>Fonolibro</strong> y disponible en Spotify. <br></br>

                        </p>
                        <p class="text-xs text-gray-500">
                          <strong>Contenido original:</strong> <a href="https://open.spotify.com/album/06KkA6HwQFZvfhFy0H8SvU" class="text-blue-600 hover:underline" target="_blank" rel="noopener noreferrer">https://open.spotify.com/embed/album/06KkA6HwQFZvfhFy0H8SvU</a>
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
