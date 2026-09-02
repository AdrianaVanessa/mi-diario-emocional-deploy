<template>
  <div
    class="min-h-screen bg-gradient-to-br from-slate-50 to-[#70BFE9]/20 dark:from-gray-900 dark:to-gray-800 transition-colors"
  >
    <div class="grid grid-cols-1 lg:grid-cols-2 min-h-screen">
      <div class="flex items-center justify-center">
        <WomanHeart />
      </div>

      <div class="flex items-center justify-center p-6">
        <div
          class="w-full max-w-md rounded-2xl bg-white dark:bg-gray-800 p-8 shadow-lg border border-gray-200 dark:border-gray-700"
        >
          <h1 class="mb-8 text-3xl font-bold text-center text-[#70BFE9]">Iniciar sesión</h1>

          <p v-if="errorMessage" class="text-base text-red-500 text-center mb-4 font-semibold">
              {{ errorMessage }}
          </p>

          <div v-if="showRedirectButton" class="text-center">
            <p class="text-gray-600 dark:text-gray-400 mb-6">
                Haz clic en el botón de abajo para ir a la página de activación y solicitar un nuevo código.
            </p>
            <button
                @click="redirectToVerification"
                class="w-full bg-green-500 hover:bg-green-600 text-white font-semibold py-3 px-6 rounded-lg transition-colors"
            >
                Activar mi Cuenta
            </button>
          </div>

          <!-- Formulario corregido: el v-else ahora está directamente en el form real -->
          <form v-else @submit.prevent="login">
            <div class="mb-6">
              <label
                for="email"
                class="block text-gray-700 dark:text-gray-300 text-base font-semibold mb-2"
              >
                Correo electrónico
              </label>
              <div class="relative">
                <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                  <IconMail class="h-6 w-6 mx-auto text-[#70BFE9] dark:text-gray-300" />
                </div>
                <input
                  type="email"
                  id="email"
                  v-model="email"
                  placeholder="Ingresa tu correo electrónico"
                  class="pl-10 p-3 w-full border rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-50 dark:bg-gray-700 border-gray-300 dark:border-gray-600 text-gray-900 dark:text-white placeholder-gray-400 dark:placeholder-gray-400"
                  required
                />
              </div>
            </div>

            <div class="mb-6">
              <label
                for="password"
                class="block text-gray-700 dark:text-gray-300 text-base font-semibold mb-2"
              >
                Contraseña
              </label>
              <div class="relative">
                <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
                  <IconLockSquareRounded class="h-6 w-6 mx-auto text-[#70BFE9] dark:text-gray-300" />
                </div>

                <input
                  :type="showPassword ? 'text' : 'password'"
                  id="password"
                  v-model="password"
                  placeholder="Ingresa tu contraseña"
                  class="pl-10 pr-10 p-3 w-full border rounded-lg focus:ring-blue-500 focus:border-blue-500 bg-gray-50 dark:bg-gray-700 border-gray-300 dark:border-gray-600 text-gray-900 dark:text-white placeholder-gray-400 dark:placeholder-gray-400"
                  required
                />

                <div
                  class="absolute inset-y-0 right-0 flex items-center pr-3 cursor-pointer"
                  @click="showPassword = !showPassword"
                >
                  <IconEye v-if="!showPassword" class="h-5 w-5 text-gray-500 hover:text-[#70BFE9]" />
                  <IconEyeOff v-else class="h-5 w-5 text-gray-500 hover:text-[#70BFE9]" />
                </div>
              </div>
            </div>

            <button
              type="submit"
              class="w-full bg-[#70BFE9] hover:bg-[#3457B2] text-white font-semibold py-3 px-6 rounded-lg transition-colors mb-4"
              :disabled="authStore.loading"
            >
              {{authStore.loading ? 'Iniciando sesión...' : 'Iniciar sesión'}}
            </button>
            <router-link
              to="/"
              class="w-full inline-block text-center bg-gray-100 hover:bg-gray-200 dark:bg-gray-700 dark:hover:bg-gray-600 text-gray-800 dark:text-gray-200 font-semibold py-3 px-6 rounded-lg transition-colors"
            >
              Regresar al Inicio
            </router-link>
          </form>

          <div class="mt-8 text-center text-gray-600 dark:text-gray-400">
            ¿No tienes una cuenta?
            <router-link to="/register" class="text-[#70BFE9] hover:underline font-semibold ml-1">
              Regístrate aquí
            </router-link>
            <br />
            <router-link
              to="/forgot-password"
              class="text-[#70BFE9] hover:underline mt-2 inline-block"
            >
              Olvidé mi contraseña
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { IconLockSquareRounded, IconMail, IconEye, IconEyeOff } from '@tabler/icons-vue';
import WomanHeart from '../components/WomanHeart.vue';
import { useAuthStore } from '@/store/auth';
import { isAxiosError } from 'axios';

const email = ref('');
const password = ref('');
const router = useRouter();
const authStore = useAuthStore();
const errorMessage = ref('');
const showRedirectButton = ref(false);
const inactiveUserRole = ref<string | null>(null);
const showPassword = ref(false);

const redirectToVerification = () => {
  if (!inactiveUserRole.value) {
    console.error("No se pudo determinar el rol del usuario para la redirección.");
    return;
  }

  const routePayload = {
    name: 'first-login',
    params: { type: inactiveUserRole.value },
    query: { email: email.value }
  };

  console.log("Redirigiendo a 'first-login' con los siguientes parámetros:", routePayload);
  router.push(routePayload);
};

const login = async () => {
  errorMessage.value = '';
  showRedirectButton.value = false;
  inactiveUserRole.value = null;

  try {
    const redirectPath = await authStore.login({ email: email.value, password: password.value });
    router.push(redirectPath);

  } catch (error: unknown) {
    let finalMessage = 'Credenciales inválidas. Verifique su correo y contraseña.';

    if (isAxiosError(error) && error.response) {
      const errorData = error.response.data;
      console.log("Error recibido del backend:", errorData);

      // Aquí capturamos tanto el nuevo error de PreRegistration como el de cuenta inactiva
      if (errorData.error === 'pending_verification' || errorData.code === 'account_not_active') {
        finalMessage = '¡Cuenta pendiente de verificación! Haz clic abajo para validarla.';
        showRedirectButton.value = true;
        inactiveUserRole.value = errorData.role;

        console.log("Rol de usuario inactivo guardado:", inactiveUserRole.value);
      } else if (errorData.detail) {
        finalMessage = errorData.detail;
      }
    }

    errorMessage.value = finalMessage;
  }
};
</script>
