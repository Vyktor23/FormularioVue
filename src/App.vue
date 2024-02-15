


<!-- <template>
<div>
  <h1>{{ parseInt(num) + parseInt(num2) }}</h1>
  <h1>{{ parseInt(num) / parseInt(num2==0?1:(num2)) }}</h1>
  <input type="text" placeholder="número A..." v-model="num">
  <input type="text" placeholder="número B..." v-model="num2">
</div>
</template> -->

<!-- <script setup>
import {ref} from "vue"
let num =ref(0)
let num2 =ref(0)
let telefono =ref("123456789")
telefono.value="345"
let nombre =ref("Ramírez")
nombre.value = telefono.value
</script> -->


<!-- <template>
  <div>
    <h1>{{ opcion }}</h1>
    <select v-model="opcion">
      <option value="Hombre">Hombre</option>
      <option value="Mujer">Mujer</option>
      <option value="Otro">Otro</option>
    </select>

    <input type="radio" nombre="gen" value="Hombre" v-model="opcion">Hombre
    <input type="radio" nombre="gen" value="Mujer" v-model="opcion">Mujer
    <input type="radio" nombre="gen" value="Otro" v-model="opcion">Otro

  </div>
</template>

<script setup>
import {ref} from "vue"
let opcion=ref("Hombre")
</script> -->



<!-- <template>
  <div>
    <h1>{{ contador }}</h1>

    <button @click="contar()">Cambiar</button>
    <h2 v-if="contador<11">Hola mensaje 1 va a desaparecer.</h2>
    <h2 v-else>El mensaje 2 aparece.</h2>
    <h2>{{ contador<11?"Hola mensaje 1 va a desaparecer.":"El mensaje 2 aparece."}}</h2>

  </div>
</template>

<script setup>
import {ref} from "vue"
let contador=ref(0)

function contar(){
  contador.value+=1
}
</script> -->



<!-- <template>
  <div>
    <h1>Bienvenido</h1>
    <h1>{{ calculo }}</h1>
  <input type="text" placeholder="número A..." v-model="num1">
  <input type="text" placeholder="número B..." v-model="num2">
  <br>
  <br>
  <input type="radio" name="ope" value="+" v-model="opcion">Sumar
    <input type="radio" name="ope" value="-" v-model="opcion">Restar
    <input type="radio" name="ope" value="*" v-model="opcion">Multiplicar
    <input type="radio" name="ope" value="/" v-model="opcion">Dividir
    <br>
    <br>
    <button @click="calcular()">Calcular</button>
  </div>
</template>

<script setup>
import {ref} from "vue"

let num1 =ref(0)
let num2 =ref(0)
let calculo = ref(0)
let opcion = ref("")

function calcular(){
  if (opcion.value=="+"){
    calculo.value= parseInt(num1.value) + parseInt(num2.value)
  } else if (opcion.value=="-"){
    calculo.value= num1.value - num2.value
  } else if (opcion.value=="*"){
    calculo.value = num1.value * num2.value
  }else if (opcion.value=="/" && num2.value==0?1:(num2.value)){
    calculo.value = num1.value / num2.value
  }
}
</script> -->



<!--  Diseñar el formulario con los siguientes datos
Nombre
Apellidos
Tipo documento
Número de documento
Genero
Correo
Teléfono
Fecha de nacimiento
Validaciones para registro exitoso:
1- Validar el nombre que no esté vacio
2- Validar apellidos que no esté vacio
3- Validar que el tipo de documento no este vacio
4- Solamente números en el documento y que no este vacio
5- El género que no este vacio
6- El correo que sea formato correo y que no esté vacio
7- El teléfono debe ser mayor a 9 números positivo
8- la fecha de nacimiento que sea mayor de edad y que no esté vacio
9- Al presionar en el botón que salga el registro exitoso o el mensaje de validación
10- Si el registro es exitoso que imprima los datos en un objeto dentro de un vector-->

<template>
  <div>

    <div class="contenedor_principal">
      <h1>Bienvenido</h1>
    <h3>Formulario de Registro</h3>
    <p :style="{ color: alertColor1 }">{{ alert1 }}</p>
    <p :style="{ color: alertColor2 }">{{ alert2 }}</p>

    <input type="text" class="grupo_input" placeholder="Nombre..." v-model="nombre">
    <input type="text" class="grupo_input" placeholder="Apellido..." v-model="apellido">

    <label for="ti" class="label">Tipo de documento:</label>

    <div class="grupo_radio">
      <input type="radio" name="ti" value="CC" v-model="tipo">C.C
      <input type="radio" name="ti" value="CE" v-model="tipo">C.Ext
      <input type="radio" name="ti" value="Pasaporte" v-model="tipo">Pasaporte
      <input type="radio" name="ti" value="Otro" v-model="tipo">Otro
    </div>

    <input type="text" class="grupo_input" placeholder="Número de documento..." v-model="documento">

    <label for="op" class="grupo_label">Género:</label>
    <div class="grupo_radio">
      <input type="radio" name="op" value="Masculino" v-model="opcion">Masculino
      <input type="radio" name="op" value="Femenino" v-model="opcion">Femenino
    </div>

    <input type="email" class="grupo_input" placeholder="Correo..." v-model="correo">

    <input type="text" class="grupo_input" placeholder="Teléfono..." v-model="telefono">

    <label for="fechan" class="grupo_label">Fecha de Nacimiento:</label>
    <input type="date" name="fechan" class="grupo_input" placeholder="Fecha de nacimiento..." v-model="fecha">

    <button @click="verificar()" class="boton" v-if="bd == true">Guardar</button>
    <button @click="editarr()" class="boton" v-else>Editar</button>
    </div>

    <br>
    <br>

    <div class="tabla">
      <table>
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
          <th>Tipo de documento</th>
          <th>Nro. de documento</th>
          <th>Genero</th>
          <th>Correo</th>
          <th>Telefono</th>
          <th>Fecha de nacimiento</th>
          <th>Opciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, i) in datos" :key="i">
          <td>{{ item.nombre }}</td>
          <td>{{ item.apellido }}</td>
          <td>{{ item.tipo }}</td>
          <td>{{ item.documento }}</td>
          <td>{{ item.opcion }}</td>
          <td>{{ item.correo }}</td>
          <td>{{ item.telefono }}</td>
          <td>{{ item.fecha }}</td>
          <td>
            <button @click="eliminar(i)">❌</button>
            <button @click="editar(item, i)">📝</button>
          </td>
        </tr>

      </tbody>

    </table>
    </div>
  </div>

</template>


<script setup>

import { ref } from "vue";

let datos = ref([]);

let bd = ref(true);
let index = ref(null);

let nombre = ref("");
let apellido = ref("");
let tipo = ref("");
let documento = ref("");
let opcion = ref("");
let correo = ref("");
let telefono = ref("");
let fecha = ref("");
let alert1 = ref("");
let alert2 = ref("");
let alertColor1 = ref("red");
let alertColor2 = ref("green");


function editarr() {
  datos.value[index.value].nombre = nombre.value;
  datos.value[index.value].apellido = apellido.value
  datos.value [index.value].tipo = tipo.value
  datos.value [index.value].documento =documento.value
  datos.value [index.value].opcion =opcion.value
  datos.value [index.value].correo =correo.value
  datos.value [index.value].telefono =telefono.value
  datos.value [index.value].fecha =fecha.value

    bd=true

  nombre.value = "";
  apellido.value = "";
  tipo.value = "";
  documento.value = "";
  opcion.value = "";
  correo.value = "";
  telefono.value = "";
  fecha.value = "";
}

function eliminar(i) {
  datos.value.splice(i, 1)
}

function editar(item, i) {
  nombre.value = item.nombre
  apellido.value = item.apellido
  tipo.value = item.tipo
  documento.value = item.documento
  opcion.value = item.opcion
  correo.value = item.correo
  telefono.value = item.telefono
  fecha.value = item.fecha

  index.value = i;
  bd.value = false;
}

function verificar() {
  alert1.value = "";
  alert2.value = "";
  alertColor1.value = "red";
  alertColor2.value = "green";

  let fechaNacimiento = new Date(fecha.value);
  let fechaActual = new Date();
  let edad = fechaActual.getFullYear() - fechaNacimiento.getFullYear();

  if (nombre.value === "") {
    alert1.value = "El nombre no puede estar vacío.";
    return;
  }

  if (apellido.value === "") {
    alert1.value = "El apellido no puede estar vacío.";
    return;
  }

  if (tipo.value === "") {
    alert1.value = "Selecciona un tipo de documento.";
    return;
  }

  if (documento.value === "" || isNaN(documento.value)) {
    alert1.value = "Solo números en el documento y no puede estar vacío.";
    return;
  }

  if (opcion.value === "") {
    alert1.value = "Selecciona un género.";
    return;
  }

  if (correo.value === "" || !/^\S+@\S+\.\S+$/.test(correo.value)) {
    alert1.value = "Ingresa un correo válido y no puede estar vacío.";
    return;
  }

  if (telefono.value === "" || isNaN(telefono.value) || telefono.value.length < 10) {
    alert1.value = "El teléfono deben ser solo números y tener al menos 10 dígitos.";
    return;
  }

  if (fecha.value === "") {
    alert1.value = "La fecha de nacimiento no puede estar vacía.";
    return;
  }

  if (edad < 18) {
    alert1.value = "Debes ser mayor de 18 años para registrarte.";
    return;
  }


  const nuevoRegistro = {
    nombre: nombre.value,
    apellido: apellido.value,
    tipo: tipo.value,
    documento: documento.value,
    genero: opcion.value,
    correo: correo.value,
    telefono: telefono.value,
    fecha: fecha.value,
  };


  datos.value.push(nuevoRegistro);
  alert2.value = "Registro exitoso.";
  ocultarAlerta();
  alertColor2.value = "green";

  nombre.value = "";
  apellido.value = "";
  tipo.value = "";
  documento.value = "";
  opcion.value = "";
  correo.value = "";
  telefono.value = "";
  fecha.value = "";


}

function ocultarAlerta() {
  setTimeout(() => {
    alert2.value = "";
  }, 3500)
}
</script>


<style scoped>

.contenedor_principal {
  font-size: 18px;
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 50px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: rgba(18, 37, 99, 0.733)
}

.grupo_input {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  box-sizing: border-box;
  border-radius: 10px;
}

.grupo_radio {
  margin-bottom: 10px;
}

.grupo_label {
  display: block;
  margin-bottom: 5px;
}

.boton {
  background-color: #4CAF50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 100px;
  cursor: pointer;
}

.boton:hover {
  background-color: #3d8b41;
}

th,
tr,
td {
  border: 1px solid #ccc;
}
</style>


