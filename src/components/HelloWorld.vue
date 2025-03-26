<script setup lang="ts">
import { ref, computed } from 'vue'

defineProps<{ msg: string }>()

const usuario = ref("")
const email = ref("")
const pass = ref("")
const fecha = ref("")

const edad = computed(() => {
  if (!fecha.value) return null

  const nacimiento = new Date(fecha.value)
  const hoy = new Date()

  let edadCalculada = hoy.getFullYear() - nacimiento.getFullYear()
  const mesDiferencia = hoy.getMonth() - nacimiento.getMonth()

  if (mesDiferencia < 0 || (mesDiferencia === 0 && hoy.getDate() < nacimiento.getDate())) {
    edadCalculada--
  }
  return edadCalculada
});


function guardar (){
  if (!fecha.value) {
    alert("La fecha de nacimiento es obligatoria.")
    return;
  }

  let persona = {
    usuario: usuario.value,
    email: email.value,
    pass: pass.value,
    fecha: fecha.value,
    edad: edad.value
  }
  function mostrarAlerta() {
  alert(`
  ¡Se creó correctamente el nuevo usuario!
    Usuario: ${usuario.value}
    Email: ${email.value}
    Edad: ${edad.value} años
  `);
}

mostrarAlerta()
usuario.value = ""
email.value = ""
pass.value = ""
fecha.value= ""
}

</script>

<template>

<h1>{{ msg }}</h1>


  <input type="text" placeholder="Nombre de usuario" v-model="usuario">
  <input type="email" placeholder="E-mail" v-model="email">
  <input type="password" placeholder="Contraseña" v-model="pass">
  <input type="date" v-model="fecha">
  <button @click="guardar">Crear nuevo usuario</button>


  <div class="card">
    <h2>
      {{ usuario }}<br>{{ email }}<br>{{ fecha }}
      
    </h2>
  </div>
</template>

