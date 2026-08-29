<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-50 to-[#70BFE9]/20 dark:from-gray-900 dark:to-gray-800 transition-colors">
    <div class="max-w-5xl mx-auto px-4 py-12">
      <!-- Header -->
      <div class="text-center mb-10">
        <div class="inline-flex items-center justify-center w-20 h-20 rounded-full mb-6 shadow-lg bg-gradient-to-br from-[#5AA3CC] to-[#70BFE9]">
          <IconShieldLock class="w-10 h-10 text-white" stroke-width="2" />
        </div>
        <h1 class="text-3xl md:text-5xl font-bold dark:text-[#70BFE9] text-gray-900 mb-4">
          Aviso de Privacidad y Términos de Uso
        </h1>
        <p class="text-xl text-gray-600 mb-2 dark:text-[#70BFE9]">Mi Diario Emocional</p>
        <p class="text-sm text-gray-500 dark:text-[#70BFE9]">
          Última actualización: 29 de agosto de 2026
        </p>
      </div>

      <!-- Introduction -->
      <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-8">
        <p class="text-lg text-gray-700 leading-relaxed mb-4">
          Bienvenidos a <span class="font-semibold text-[#70BFE9]">Mi Diario Emocional</span>. Este documento rige tu uso de la Aplicación y explica de manera transparente cómo recopilamos, usamos y protegemos tus datos personales, en estricto cumplimiento con la <strong>Ley Federal de Protección de Datos Personales en Posesión de los Particulares (LFPDPPP)</strong> de México.
        </p>
      </div>

      <!-- ==========================================
           SECCIÓN I: AVISO DE PRIVACIDAD
      =========================================== -->
      <div class="mb-10">
        <h2 class="text-2xl font-bold text-gray-800 dark:text-gray-200 border-b-2 border-[#70BFE9] pb-2 mb-6">
          Sección I: Aviso de Privacidad
        </h2>

        <!-- Identidad -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconBuilding class="w-6 h-6 text-[#70BFE9]" />
            </div>
            1. Identidad y Domicilio
          </h3>
          <p class="text-gray-700">
            <span class="font-semibold">Mi Diario Emocional</span>, con domicilio en Gustavo A. Madero, Ciudad de México, 07320, es el responsable del tratamiento de tus datos personales. Contacto para derechos de privacidad: <a href="mailto:midiarioemocional_help@outlook.com" class="text-[#70BFE9] hover:underline">midiarioemocional_help@outlook.com</a>.
          </p>
        </div>

        <!-- Datos Recabados -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconDatabase class="w-6 h-6 text-[#70BFE9]" />
            </div>
            2. Datos Personales que Recabamos
          </h3>
          <div class="space-y-4 text-gray-700">
            <p><strong>A. Datos Generales:</strong> Nombre completo, correo electrónico y fecha de nacimiento.</p>
            <p><strong>B. Datos de Verificación (Terapeutas):</strong> Cédula Profesional y CURP para validar identidad profesional.</p>
            <div class="bg-red-50 p-4 rounded-lg border-l-4 border-red-400">
              <p class="text-sm font-semibold text-red-700 mb-1 flex items-center">
                <IconAlertTriangle class="w-4 h-4 mr-1" /> C. Datos Personales Sensibles (Pacientes)
              </p>
              <p class="text-sm">
                Las entradas de tu diario y el análisis de emociones son datos sensibles. Requerimos tu consentimiento explícito para su tratamiento, el cual otorgas al aceptar este aviso.
              </p>
            </div>
          </div>
        </div>

        <!-- Finalidades -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconTarget class="w-6 h-6 text-[#70BFE9]" />
            </div>
            3. Finalidades del Tratamiento
          </h3>
          <p class="text-gray-700 mb-3">Tus datos se utilizan exclusivamente para finalidades necesarias para el servicio:</p>
          <ul class="list-disc pl-6 text-gray-700 space-y-1 mb-4">
            <li>Crear y gestionar tu cuenta.</li>
            <li>Almacenar de forma segura tus entradas y generar análisis algorítmico de emociones.</li>
            <li>Validar credenciales (en el caso de terapeutas).</li>
          </ul>
          <p class="text-gray-700 font-semibold text-green-600">No utilizaremos tus datos personales ni sensibles para finalidades secundarias como marketing o venta a terceros.</p>
        </div>

        <!-- Seguridad y Transferencia -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconLock class="w-6 h-6 text-[#70BFE9]" />
            </div>
            4. Seguridad y Transferencia de Datos
          </h3>
          <p class="text-gray-700 mb-3">
            Toda la comunicación de la aplicación viaja cifrada. Tus contraseñas son protegidas con algoritmos irreversibles y contamos con escudos contra accesos no autorizados en nuestros servidores.
          </p>
          <p class="text-gray-700">
            <strong>Transferencias:</strong> La única transferencia de datos sensibles que realizamos ocurre si tú (como paciente) decides vincularte con un Terapeuta mediante un código. Fuera de esto, no compartimos tu información con terceros.
          </p>
        </div>

        <!-- ARCO y Cambios -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconUserCheck class="w-6 h-6 text-[#70BFE9]" />
            </div>
            5. Derechos ARCO y Modificaciones
          </h3>
          <p class="text-gray-700 mb-3">
            Tienes derecho a <strong>Acceder, Rectificar, Cancelar u Oponerte</strong> al uso de tus datos. Puedes ejercerlos eliminando tu cuenta directamente en tu perfil, o contactándonos al correo oficial.
          </p>
          <p class="text-gray-700">
            <strong>Modificaciones:</strong> Nos reservamos el derecho de efectuar modificaciones a este aviso. Cualquier cambio será notificado a través de la aplicación o por correo electrónico.
          </p>
        </div>
      </div>

      <!-- ==========================================
           SECCIÓN II: TÉRMINOS Y CONDICIONES
      =========================================== -->
      <div class="mb-8">
        <h2 class="text-2xl font-bold text-gray-800 dark:text-gray-200 border-b-2 border-[#70BFE9] pb-2 mb-6">
          Sección II: Términos y Condiciones de Uso
        </h2>

        <!-- Aceptación y Servicio -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconClipboardText class="w-6 h-6 text-[#70BFE9]" />
            </div>
            6. Aceptación y Descripción
          </h3>
          <p class="text-gray-700 mb-2">
            Debes ser <strong>mayor de 18 años</strong> para utilizar esta Aplicación. "Mi Diario Emocional" es una herramienta digital para registrar reflexiones personales, con la opción de vincular dicha información a un profesional verificado.
          </p>
        </div>

        <!-- Descargo Médico -->
        <div class="bg-red-50 border-2 border-red-300 rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-red-700 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-red-200 flex items-center justify-center mr-3">
              <IconAlertTriangle class="w-6 h-6 text-red-700" />
            </div>
            7. ¡Importante! Descargo de Responsabilidad Médica
          </h3>
          <div class="bg-white rounded-xl p-5 mb-4 border-l-4 border-red-500">
            <p class="text-lg font-bold text-red-700 flex items-center">
              <IconAlertOctagon class="w-6 h-6 mr-2" />
              La Aplicación NO es un servicio médico ni de emergencia.
            </p>
          </div>
          <ul class="space-y-3 text-gray-800">
            <li><strong>No sustituye terapia:</strong> Es una herramienta de autoayuda, no reemplaza el consejo, diagnóstico o tratamiento de un profesional.</li>
            <li><strong>Análisis algorítmico:</strong> Las emociones detectadas son estimaciones automáticas y no constituyen diagnósticos clínicos.</li>
            <li class="font-semibold text-red-700 flex items-center">
              <IconPhoneCall class="w-5 h-5 mr-2" /> Si experimentas una crisis o emergencia, contacta al 911 o a los servicios de emergencia de tu localidad inmediatamente.
            </li>
          </ul>
        </div>

        <!-- Cuentas y Vinculación -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconLink class="w-6 h-6 text-[#70BFE9]" />
            </div>
            8. Cuentas, Seguridad y Vinculación
          </h3>
          <div class="space-y-4 text-gray-700">
            <p><strong>Cuentas:</strong> Eres responsable de mantener la confidencialidad de tu contraseña. Nos reservamos el derecho de rechazar cuentas de Terapeutas que no puedan ser validadas legalmente.</p>
            <p><strong>Para Pacientes:</strong> Al usar un "Código de Vinculación", otorgas consentimiento para que el Terapeuta acceda a tus entradas. Puedes desvincularte en cualquier momento desde tu perfil, revocando el acceso instantáneamente.</p>
            <p><strong>Para Terapeutas:</strong> Te comprometes a mantener estricta confidencialidad sobre los datos de tus pacientes. El uso indebido resultará en la terminación inmediata y permanente de tu cuenta.</p>
          </div>
        </div>

        <!-- Conducta, Terminación y Ley -->
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6">
          <h3 class="text-xl font-bold text-gray-900 mb-4 flex items-center">
            <div class="w-10 h-10 rounded-lg bg-[#70BFE9]/10 flex items-center justify-center mr-3">
              <IconScale class="w-6 h-6 text-[#70BFE9]" />
            </div>
            9. Conducta, Terminación y Ley Aplicable
          </h3>
          <div class="space-y-4 text-gray-700">
            <p><strong>Propiedad y Conducta:</strong> Tú eres el único propietario del contenido que escribes. Te comprometes a no subir contenido ilegal, difamatorio, ni a intentar comprometer la seguridad de la plataforma.</p>
            <p><strong>Terminación:</strong> Puedes eliminar tu cuenta en cualquier momento borrando permanentemente tus datos. Nos reservamos el derecho de suspender o eliminar tu cuenta si violas estos Términos.</p>
            <p><strong>Ley Aplicable:</strong> Estos Términos se rigen e interpretan de acuerdo con las leyes de los <strong>Estados Unidos Mexicanos</strong>.</p>
          </div>
        </div>
      </div>

      <!-- ==========================================
           ACEPTACIÓN
      =========================================== -->
      <template v-if="isRegistrationFlow">
        <div class="bg-white rounded-2xl shadow-lg p-6 md:p-8 mb-6" :class="{ 'ring-2 ring-red-500': showError }">
          <div class="flex items-start space-x-3">
            <input
              type="checkbox"
              id="acceptTerms"
              v-model="accepted"
              class="w-6 h-6 mt-1 text-[#70BFE9] border-gray-300 rounded focus:ring-[#70BFE9] focus:ring-2 cursor-pointer"
            >
            <label for="acceptTerms" class="cursor-pointer">
              <p class="font-semibold text-gray-900 mb-2">
                Consentimiento Explícito y Aceptación
              </p>
              <p class="text-sm text-gray-700 leading-relaxed">
                Al marcar esta casilla, declaro que soy mayor de 18 años, he leído, entendido y acepto completamente estos Términos de Uso. Asimismo, manifiesto mi consentimiento explícito para el tratamiento de mis datos personales y sensibles bajo las condiciones descritas en el Aviso de Privacidad. Comprendo especialmente el descargo de responsabilidad médica y las condiciones de vinculación.
              </p>
            </label>
          </div>
          <div v-if="showError" class="mt-4 flex items-center text-red-600 text-sm">
            <IconAlertCircle class="w-5 h-5 mr-2" />
            Debes aceptar los términos y políticas para continuar.
          </div>
        </div>

        <!-- Action Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-end mb-8">
          <button
            type="button"
            @click="handleCancel"
            class="px-8 py-3 rounded-full border-2 border-gray-300 text-gray-700 font-semibold hover:bg-gray-50 transition-all"
          >
            Volver
          </button>
          <button
            type="button"
            @click="handleAccept"
            :disabled="!accepted"
            class="px-8 py-3 rounded-full font-semibold text-white shadow-lg transition-all flex items-center justify-center"
            :class="accepted ? 'bg-gradient-to-r from-[#5AA3CC] to-[#70BFE9] hover:shadow-xl hover:scale-105' : 'bg-gray-400 cursor-not-allowed'"
          >
            <IconCheck class="w-5 h-5 mr-2" />
            Aceptar y Continuar
          </button>
        </div>
      </template>

      <!-- Footer -->
      <div class="text-center text-gray-500 text-sm">
        <p class="flex items-center justify-center">
          <IconCopyright class="w-4 h-4 mr-1" />
          {{ currentYear }} Mi Diario Emocional. Todos los derechos reservados.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, watch } from 'vue';
import { useRouter, useRoute } from 'vue-router';
import {
  IconShieldLock,
  IconBuilding,
  IconDatabase,
  IconLock,
  IconUserCheck,
  IconStethoscope,
  IconPhoneCall,
  IconLink,
  IconAlertTriangle,
  IconAlertOctagon,
  IconAlertCircle,
  IconCheck,
  IconCopyright,
  IconTarget,
  IconClipboardText,
  IconScale
} from '@tabler/icons-vue';

const router = useRouter();
const route = useRoute();
const accepted = ref<boolean>(false);
const showError = ref<boolean>(false);
const currentYear = computed(() => new Date().getFullYear());

const isRegistrationFlow = computed(() => route.query.flow === 'register');
const registrationType = computed(() => route.query.type);

const handleAccept = (): void => {
  if (!accepted.value) {
    showError.value = true;
    document.getElementById('acceptTerms')?.scrollIntoView({ behavior: 'smooth', block: 'center' });
    return;
  }

  showError.value = false;

  // Redirige directamente al formulario de registro correspondiente
  if (registrationType.value === 'professional') {
    router.push({ name: 'register-professional', query: { terms: 'true' } });
  } else {
    router.push({ name: 'register-patient', query: { terms: 'true' } });
  }
};

const handleCancel = (): void => {
  router.push({ name: 'register' });
};

onMounted(() => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
});

watch(() => route.query, () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
  accepted.value = false;
  showError.value = false;
});
</script>
