<template>
  <div class="flex h-screen">
    <main class="flex-1 flex flex-col overflow-hidden">
      <StreakAndTitle
      title="Inicio: Recursos de Autoayuda"
      :streak-count="streakCount"
    />
      <div class="dark:bg-gray-800 transition-colors flex-1 p-6 overflow-y-auto">

        <div class="mb-8 relative bg-gradient-to-r overflow-hidden h-96 flex items-center justify-center">
          <img
            src="https://images.unsplash.com/photo-1658279366796-e0c28623cd27?q=80&w=1151&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
            alt="Artículo destacado"
            class="w-3/5 h-full object-cover rounded-2xl opacity-100"
          />

          <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 z-10 text-white text-center w-full px-4">
            <router-link to="/article-weekly-patient">
              <button
                class="bg-[#7DBFF8] bg-opacity-50 p-3 rounded-lg hover:bg-[#3457B2] transition shadow-lg transition-colors text-white"
              >
                <h1 class="font-bold">Ver: Artículo destacado</h1>
                  ¿Cómo superar el trauma de una ruptura? Una guía práctica. <b>Por: Silvia Congost</b>
              </button>
            </router-link>
          </div>

          <!-- Botones a la derecha -->
          <div class="hidden sm:flex absolute right-3.5 top-1/2 transform -translate-y-1/2 flex flex-col gap-4 z-10 ml-4">

            <!-- Botón de números de emergencia -->
            <button @click="showEmergencyNumbers = true" class="w-16 h-16 sm:w-20 sm:h-20 bg-[#B5D8B8] hover:bg-green-500 rounded-2xl flex items-center justify-center text-white shadow-lg transition-colors">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
              </svg>
            </button>

            <!-- Botón con ubicación centros de salud mental en la zona metropolitana-->
            <a href="https://www.google.com/maps/search/centros+de+salud+psicol%C3%B3gica+CDMX"
              target="_blank"
              rel="noopener noreferrer"
              class="w-16 h-16 sm:w-20 sm:h-20 bg-blue-300 hover:bg-blue-400 rounded-2xl flex items-center justify-center text-white shadow-lg transition-colors">
                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
                </svg>
            </a>

            <!-- Botón de frase motivadora -->
            <button @click="showMotivationalQuote" class="w-16 h-16 sm:w-20 sm:h-20 bg-[#EDA1A1] hover:bg-red-400 rounded-2xl flex items-center justify-center text-white shadow-lg transition-colors">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"/>
              </svg>
            </button>
          </div>
        </div>

        <div class="mb-8 snap-normal">
          <h3 class="text-xl font-semibold text-gray-800 mb-6">¿Te gustaría explorar nuevos temas? ¡Hagámoslo!</h3>
          <!-- Carrusel de temas - Component-->
          <Carrusel />
        </div>

        <!-- Botones flotantes en móvil -->
        <div class="block md:hidden fixed right-6 top-1/2 transform -translate-y-1/2 flex flex-col gap-4 z-10">

          <!-- Botón de números de emergencia -->
          <button @click="showEmergencyNumbers = true" class="w-12 h-12 bg-green-500 hover:bg-green-600 rounded-lg flex items-center justify-center text-white shadow-lg transition-colors">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
            </svg>
          </button>

          <!-- Botón con ubicación centros de salud mental en la zona metropolitana-->
          <a href="https://www.google.com/maps/search/centros+de+salud+psicol%C3%B3gica+CDMX"
              target="_blank"
              rel="noopener noreferrer"
              class="w-12 h-12 bg-blue-500 hover:bg-blue-600 rounded-lg flex items-center justify-center text-white shadow-lg transition-colors">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
          </a>

          <!-- Botón de frase motivadora -->
          <button @click="showMotivationalQuote" class="w-12 h-12 bg-red-500 hover:bg-red-600 rounded-lg flex items-center justify-center text-white shadow-lg transition-colors">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/>
            </svg>
          </button>
        </div>

        <router-view />
      </div>
    </main>

    <!-- Perfil del usuario(solo en pantallas grandes) -->
    <UserProfile />

    <!-- Emergency Numbers Modal PopUp -->
    <div v-if="showEmergencyNumbers" class="fixed inset-0 z-50 flex items-center justify-center">
      <div class="dark:bg-gray-900 rounded-lg p-8 dark:border-gray-400 shadow-xl bg-white max-w-lg w-full relative items-center justify-center">
        <button @click="showEmergencyNumbers = false" class="absolute top-2 right-2 text-gray-400 hover:text-gray-600 dark:hover:text-gray-300">
          <svg class="w-14 h-14" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>

        <IconPhoneCall class="text-green-400 center w-14 h-14 mb-4 items-center mx-auto" />
        <h3 class="text-xl text-center font-bold mb-4 text-gray-800 dark:text-white">Números de Emergencia en la Ciudad de México</h3>
        <p class="text-lg text-gray-600 dark:text-gray-300 mb-6 text-center">
          Si te sientes en una crisis, recuerda que no estás solo. Puedes llamar a estos números para recibir ayuda de inmediato.
        </p>

        <ul class="space-y-3">
          <li>
            <p class="text-blue-600 text-lg dark:text-blue-400 hover:underline font-semibold text-center w-full block">
              <span class="text-lg">🔹</span> 911 (Emergencias)
            </p>
          </li>
          <li>
            <p class="text-blue-600 text-lg dark:text-blue-400 hover:underline font-semibold text-center w-full block">
              <span class="text-lg">🔹</span> Cruz Roja (55 53 95 11 11)
            </p>
          </li>
          <li>
            <p class="text-blue-600 text-lg dark:text-blue-400 hover:underline font-semibold text-center w-full block">
              <span class="text-lg">🔹</span> Protección Civil (55 51 28 00 00)
            </p>
          </li>
          <li>
            <p class="text-blue-600 text-lg dark:text-blue-400 hover:underline font-semibold text-center w-full block">
              <span class="text-lg ">🔹</span> Apoyo Psicológico (*0311 o al 55 5658 1111)
            </p>
          </li>
        </ul>
      </div>
    </div>

<!-- Motivational Quote Modal PopUp -->
    <div v-if="showQuoteModal" class="fixed inset-0 z-50 flex items-center justify-center">
      <div class="dark:bg-gray-900 rounded-lg p-8 dark:border-gray-400 shadow-xl bg-white max-w-lg w-full relative items-center justify-center mx-4">
        <button @click="showQuoteModal = false" class="absolute top-2 right-2 text-gray-400 hover:text-gray-600 dark:hover:text-gray-300">
          <svg class="w-14 h-14" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>

        <!-- Icono de estrella para frases motivadoras -->
        <div class="flex items-center justify-center w-14 h-14 mx-auto">
          <IconMoodHeart class="center w-14 h-14 mb-4 items-center mx-auto text-[#F38386]" />
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"/>

        </div>

        <h3 class="text-xl text-center font-bold mb-4 text-gray-800 dark:text-white">✨ Tu Frase del Día</h3>
        <p class="text-xl text-gray-600 dark:text-gray-300 mb-6 text-center">
          Una pequeña dosis de inspiración para alegrar tu día
        </p>

        <!-- Contenido de la frase -->
        <div class="bg-gray-100 dark:bg-gray-800 rounded-xl p-6 mb-6">
          <p class="text-lg font-medium text-gray-800 dark:text-gray-200 leading-relaxed mb-3 text-center">
            "{{ currentQuote.text }}"
          </p>
          <p class="text-sm text-gray-500 dark:text-gray-400 italic text-center">
            — {{ currentQuote.author }}
          </p>
        </div>

        <!-- Botones -->
        <div class="flex gap-3">
          <button
            @click="showMotivationalQuote"
            class="flex-1 bg-[#7DBFF8] hover:bg-[#3457B2] text-white font-semibold py-3 px-6 rounded-lg transition-colors"
          >
            Otra Frase
          </button>
          <button
            @click="showQuoteModal = false"
            class="flex-1 bg-gray-200 hover:bg-gray-300 dark:bg-gray-700 dark:hover:bg-gray-600 text-gray-700 dark:text-gray-300 font-semibold py-3 px-6 rounded-lg transition-colors"
          >
            Cerrar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { IconPhoneCall, IconMoodHeart } from "@tabler/icons-vue"
import StreakAndTitle from "../components/StreakAndTitlePatient.vue";
import UserProfile from "../components/PatientProfile.vue"
import Carrusel from "../components/CarruselPatient.vue"
import { ref, onMounted, computed } from 'vue';
import { useRouter } from 'vue-router';
import { useAuthStore } from '@/store/auth';
import { isAxiosError } from 'axios';
import * as AuthServices from '@/modules/auth/services/authServices';

// ----------------------------------------------------
// DEFINICIONES DE TIPO (PatientProfile)
// ----------------------------------------------------
interface PatientProfile {
    name: string;
    paternal_last_name: string;
    maternal_last_name: string;
    email: string;
    alias: string;
    gender: string;
    professional_name?: string; // Es opcional y puede ser nulo
    is_linked: boolean;
    current_streak: number;
}

// ----------------------------------------------------
// VARIABLES REACTIVAS
// ----------------------------------------------------
const patientData = ref<PatientProfile | null>(null);
const loadingProfile = ref(true);
const authStore = useAuthStore();
const router = useRouter();

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

// Variables de UI y modales
const showEmergencyNumbers = ref(false);
const showQuoteModal = ref(false);
const currentQuote = ref({ text: '', author: '' });
let lastQuoteIndex = -1;

// Base de datos de frases (Tu lógica de frases permanece igual)
        const quotes = {
            motivacional: [
                { text: "La felicidad es una dirección, no un lugar.", author: "Sydney J. Harris" },
                { text: "Si supiera que el mundo se acaba mañana, yo, hoy todavía, plantaría un árbol.", author: "Martin Luther King Jr." },
                { text: "Si escuchas una voz dentro de ti que dice 'no puedes pintar', entonces pinta y esa voz será silenciada.", author: "Vincent Van Gogh" },
                { text: "Sigues poniendo un pie delante del otro y un día miras hacia atrás y has escalado una montaña.", author: "Tom Hiddleston" },
                { text: "El éxito es caminar de fracaso en fracaso sin perder el entusiasmo.", author: "Winston Churchill" },
                { text: "La diferencia entre ganar y perder suele ser no darse por vencido.", author: "Walt Disney" },
                { text: "El camino hacia el éxito y el camino hacia el fracaso son prácticamente el mismo.", author: "Colin R. Davis" },
                { text: "No nos quedamos sentados esperando a otras personas. Simplemente, nos ponemos en marcha y lo hacemos.", author: "Arlan Hamilton" },
                { text: "La educación es el arma más poderosa para cambiar el mundo.", author: "Nelson Mandela" },
                { text: "Mantén tus ojos en las estrellas y tus pies en el suelo.", author: "Theodore Roosevelt" },
                { text: "Sólo un pequeño pensamiento positivo por la mañana puede cambiar todo tu día.", author: "Dalai Lama" },
                { text: "Si puedes imaginarlo, puedes hacerlo.", author: "Tom Fitzgerald" },
                { text: "El gran descubrimiento de mi generación es que los seres humanos pueden cambiar sus vidas cambiando su actitud.", author: "William James" },
                { text: "Los lunes ofrecen un nuevo comienzo 52 veces al año.", author: "David Dweck" },
                { text: "Cuando todo parezca ir en tu contra, recuerda que un avión despega contra el viento, no a favor de él.", author: "Henry Ford" }
            ],

            amor: [
                { text: "El amor propio tiene muy poco que ver con cómo te sientes con tu apariencia. Se trata de aceptar todo de ti mismo.", author: "Tyra Banks" },
                { text: "Amarse a uno mismo es el comienzo de un romance de por vida.", author: "Oscar Wilde" },
                { text: "Prefiero ser sincero conmigo mismo, incluso ante el riesgo de hacer el ridículo ante los demás, en lugar de ser falso, e incurrir en mi propio aborrecimiento.", author: "Frederick Douglass" },
                { text: "Nunca es demasiado tarde para ser lo que podrías haber sido.", author: "George Eliot" },
                { text: "Tú mismo, tanto como cualquier otro ser en el universo entero, mereces tu propio amor y afecto.", author: "Buda" },
                { text: "El amor propio es la fuente de todos los amores.", author: "Pierre Corneille" },
                { text: "Si tienes la capacidad de amar, ámate a ti mismo primero.", author: "Charles Bukowski" },
                { text: "No podemos estar tan desesperados por recibir amor como para olvidamos de dónde lo encontramos siempre; adentro.", author: "Alexandra Elle" },
                { text: "A medida que empecé a quererme, dejé de ansiar tener una vida diferente, y pude ver que todo lo que me rodeaba me estaba invitando a crecer. Hoy en día lo llamo 'madurez'.", author: "Charlie Chaplin" },
                { text: "La única persona que puede deprimirme soy yo mismo, y no voy a dejar que me deprima más.", author: "C. JoyBell C" },
                { text: "¿Por qué, en general, se rehuye la soledad? Porque son muy pocos los que encuentran compañía consigo mismos.", author: "Carlo Dossi" },
                { text: "Nadie te puede hacer sentir inferior sin tu consentimiento.", author: "Eleanor Roosevelt" },
                { text: "Conservar algo que me ayude a recordarte sería admitir que te puedo olvidar.", author: "William Shakespeare" },
                { text: "Ser dueño de nuestras historias y amarnos a nosotros mismos a través de ese proceso, es lo más valiente que jamás haremos.", author: "Brené Brown" },
                { text: "La mejor manera de ganar confianza en ti mismo es hacer lo que tienes miedo de hacer.", author: "Swati Sharma" }
            ],

            bienestar: [
                { text: "Cuando quieres cambiar tus circunstancias, primero debes cambiar tus pensamientos.", author: "Rhonda Byrne" },
                { text: "El tiempo que disfrutas perdiéndolo no es tiempo perdido.", author: "Marthe Troly-Curtin" },
                { text: "El éxito no se logra solo con cualidades especiales. Es, sobre todo, un trabajo de constancia, de método y de organización.", author: "Victor Hugo" },
                { text: "Si no puedes volar, corre; si no puedes correr, camina; si no puedes caminar, gatea, pero sigue avanzando hacia tu meta.", author: "Martin Luther King Jr." },
                { text: "Busca la libertad y conviértete en cautivo de tus deseos. Busca la disciplina y encuentra la libertad.", author: "Frank Herbert" },
                { text: "Odié cada minuto de entrenamiento, pero dije, no te rindas. Sufre ahora y vive el resto de tu vida como un campeón.", author: "Muhammad Ali" },
                { text: "Sé brutalmente honesto con lo de corto plazo, y optimista y confiado con lo planteado a largo plazo.", author: "Reed Hastings" },
                { text: "Acepta la responsabilidad en tu vida. Sé consciente de que serás tú quien te llevará a donde quieres ir, nadie más.", author: "Les Brown" },
                { text: "Únicamente aquellos que se atreven a tener grandes fracasos, terminan consiguiendo grandes éxitos.", author: "Robert F. Kennedy" },
                { text: "No podemos estar en modo de supervivencia. Tenemos que estar en modo de crecimiento.", author: "Jeff Bezos" },
                { text: "El que pasa el tiempo arrepintiéndose del pasado, pierde el presente y arriesga el futuro.", author: "Francisco de Quevedo" },
                { text: "El que tiene fe en sí mismo no necesita que los demás crean en él.", author: "Miguel de Unamuno" },
                { text: "Aléjate de la gente que trata de empequeñecer tus ambiciones. La gente pequeña siempre hace eso, pero la gente realmente grande, te hace sentir que tú también puedes ser grande.", author: "Mark Twain" },
                { text: "Un día sin una sonrisa es un día perdido.", author: "Charles Chaplin" },
                { text: "Si escuchas una voz dentro de ti que dice 'no puedes pintar', entonces pinta, y la voz será silenciada.", author: "Vincent Van Gogh" },


            ],

            sabiduria: [
                { text: "El misterio de la vida no es un problema a resolver, sino una realidad a experimentar.", author: "Frank Herbert" },
                { text: "La vida es 10% lo que me ocurre y 90% cómo reacciono a ello.", author: "Charles R. Swindoll" },
                { text: "No podemos cambiar las cartas que nos han repartido, pero sí cómo jugamos la mano.", author: "Randy Pausch" },
                { text: "El que tiene un porqué para vivir puede soportar casi cualquier cómo.", author: "Friedrich Nietzsche" },
                { text: "No juzgues cada día por la cosecha que recoges, sino por las semillas que plantas.", author: "Robert Louis Stevenson" },
                { text: "Nuestro destino vive en los momentos más pequeños. Y esos momentos a veces son tan fugaces como un susurro.", author: "Glenn Cooper"},
                { text: "Es el tiempo que has perdido en tu rosa lo que hace que tu rosa sea importante.", author: "Antoine de Saint-Exupéry" },
                { text: "Todo lo que una persona puede imaginar, otra puede hacerlo realidad.", author: "Julio Verne" },
                { text: "El mundo está lleno de magia para quien sabe mirar.", author: "Cassandra Clare" },
                { text: "No es bueno detenerse en los sueños y olvidarse de vivir.", author: "J.K. Rowling" },
                { text: "El hombre llega mucho más lejos para evitar lo que teme que para alcanzar lo que desea.", author: "Dan Brown" },
                { text: "Si esperamos hasta que estemos listos, estaremos esperando por el resto de nuestras vidas.", author: "Lemony Snicket" },
                { text: "Vivir es experimentar. Y no quedarse pensando en el sentido de la vida.", author: "Paulo Coelho" },
                { text: "La vida es eso que pasa mientras esperamos un futuro mejor.", author: "Javier Iriondo" },
                { text: "No llores porque ya se terminó, sonríe porque sucedió.", author: "Gabriel García Márquez" },




              ]
        };
const getAllQuotes = () => {  let allQuotes: { text: string; author: string }[] = [];
  Object.values(quotes).forEach(categoryQuotes => {
    allQuotes = allQuotes.concat(categoryQuotes);
  });
  return allQuotes; };

const showMotivationalQuote = () => {
    const availableQuotes = getAllQuotes();

  // Evitar mostrar la misma frase consecutiva
  let randomIndex;
  do {
    randomIndex = Math.floor(Math.random() * availableQuotes.length);
  } while (randomIndex === lastQuoteIndex && availableQuotes.length > 1);

  lastQuoteIndex = randomIndex;
  currentQuote.value = availableQuotes[randomIndex];
  showQuoteModal.value = true;
 };


// ----------------------------------------------------
// LÓGICA COMPUTADA (Uso de datos)
// ----------------------------------------------------

const patientFullName = computed(() => {
    if (loadingProfile.value || !patientData.value) return 'Cargando...';
    // Muestra el nombre y el primer apellido del paciente
    return `${patientData.value.name} ${patientData.value.paternal_last_name}`;
});

const welcomeSalutation = computed(() => {
    if (!patientData.value) return 'Hola,';
    const gender = patientData.value.gender.toLowerCase();
    return (gender === 'female') ? '¡Bienvenida,' : '¡Bienvenido,';
});


// ----------------------------------------------------
// FUNCIÓN DE CARGA DE DATOS REALES (loadPatientData)
// ----------------------------------------------------

async function loadPatientData() {
    loadingProfile.value = true;

    if (!authStore.authToken) {
        router.push({ name: 'login' });
        return;
    }

    try {
        // Llama al endpoint unificado /profile/me/
        const response = await AuthServices.fetchUserProfile();

        // Asignar los datos recibidos
        patientData.value = response.data as PatientProfile;

        // Integrar el nombre del paciente en el título principal
        const titleElement = document.querySelector('.streak-title h1');
        if (titleElement) {
            titleElement.textContent = `${welcomeSalutation.value} ${patientFullName.value}!`;
        }

    } catch (error: unknown) {
        if (isAxiosError(error) && error.response && error.response.status === 401) {
            console.error('Sesión expirada. Forzando logout.');
            authStore.logout();
            router.push({ name: 'login' });
        }
        console.error('Error al cargar datos del perfil del paciente:', error);
    } finally {
        loadingProfile.value = false;
    }
}

// Ciclo de vida para cargar los datos al inicio
onMounted(() => {
    loadPatientData();
});
</script>
