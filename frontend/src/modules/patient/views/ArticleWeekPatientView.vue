<template>
    <div class="dark:bg-gray-800 transition-colors flex h-screen bg-gray-100">

        <main class="flex-1 flex flex-col overflow-y-auto p-8 lg:p-1">
            <StreakAndTitle
              title="Artículo destacado"
              :streak-count="streakCount"
            />

            <div class="bg-white rounded-2xl shadow-lg p-6 md:p-10 lg:p-16 max-w-4xl mx-auto my-6">
                <div class="text-center mb-8">
                    <h1 class="text-3xl md:text-4xl font-bold text-gray-800 leading-tight mb-2">
                        ¿Cómo superar el trauma de una ruptura? Una guía práctica
                    </h1>
                    <p class="text-lg text-gray-600 font-semibold">Autora original: Silvia Congost</p>
                    <p class="text-sm text-gray-500">26 MAR 2025</p>
                </div>

                <div class="text-gray-700 leading-relaxed text-base md:text-lg">
                    <p class="mb-6 text-justify">
                        Una ruptura amorosa puede ser una experiencia especialmente dolorosa porque no implica únicamente separarse de una persona. También supone dejar atrás rutinas, proyectos compartidos y expectativas sobre el futuro. Este cambio puede generar miedo, resistencia y una sensación de pérdida difícil de aceptar.
                    </p>
                    <p class="mb-6 text-justify">
                        Además, el final de una relación puede afectar la autoestima. Cuando alguien deja de formar parte de nuestra vida, es común cuestionar nuestro propio valor o sentir que no fuimos suficientes. Por ello, parte del proceso de recuperación consiste en reconstruir la relación con nosotros mismos, aprender a tratarnos con mayor comprensión y reconocer que nuestro valor no depende de que otra persona permanezca a nuestro lado.
                    </p>
                    <p class="mb-6 text-justify">
                    Superar una ruptura requiere tiempo y cada persona vive este proceso de manera diferente. Durante el duelo pueden aparecer emociones como tristeza, enojo, frustración o incluso dificultad para aceptar lo ocurrido. Comprender que estas reacciones forman parte del proceso puede ayudar a transitarlas sin compararnos con la forma en que otras personas enfrentan experiencias similares.
                      </p>
                    <p class="mb-6 text-justify">
                      Aprender a soltar también significa aceptar aquello que ya no podemos controlar y dirigir nuestra atención hacia lo que continúa formando parte de nuestra vida. Valorar nuestros vínculos, aprendizajes y recursos personales puede ayudarnos a recuperar poco a poco la estabilidad y continuar construyendo nuevas etapas.
                    </p>


                    <div class="mt-8 pt-4 border-t border-gray-200 text-gray-600 text-sm">
                        <h3 class="text-base font-bold text-gray-800 mb-2">Sobre la autora</h3>
                        <p class="mb-2">
                            <span class="font-bold">Silvia Congost</span> es psicóloga, conferenciante y escritora especializada en autoestima, dependencia emocional y relaciones de pareja. Su trabajo aborda especialmente los procesos de ruptura y la construcción de relaciones emocionalmente saludables.
                        </p>
                        <p class="text-xs text-gray-500">
                            <span class="font-bold">Fuente:</span> Resumen elaborado a partir del artículo de Silvia Congost, <span class="font-bold">¿Cómo superar el trauma de una ruptura? Una guía práctica</span>, publicado en <span class="font-bold">El País</span> en marzo de 2025. <br></br>
                            <span class="font-bold">Consultar artículo original: </span><br></br>
                            <a href="https://elpais.com/eps/psicologia-y-bienestar/2025-03-27/como-superar-el-trauma-de-una-ruptura-una-guia-practica.html" class="text-blue-600 hover:underline" target="_blank" rel="noopener noreferrer">https://elpais.com/eps/psicologia-y-bienestar/2025-03-27/como-superar-el-trauma-de-una-ruptura-una-guia-practica.html</a>
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
