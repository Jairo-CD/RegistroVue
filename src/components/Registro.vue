<template>
    <div>
        <h1 class="display-4 text-center">Registro personal</h1>
        <hr>
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <div class="card mt-4 ">
                    <div class="card-body">
                        <div class="input-group  mb-3">
                            <input type="text" v-model="nombre"
                            class="form-control " placeholder="Nombre">
                            <input type="text" v-model="aPaterno"
                            class="form-control " placeholder="Ape. paterno">
                            <input type="text" v-model="aMaterno"
                            class="form-control " placeholder="Ape. materno">
                        </div>
                        <div class="input-group  mb-3">
                            <input type="numb" v-model="cp"
                            class="form-control " placeholder="C.P.">
                            <input type="text" v-model="pais"
                            class="form-control " placeholder="Pais">
                            <input type="text" v-model="estado"
                            class="form-control " placeholder="Estado">
                            <input type="text" v-model="municipio"
                            class="form-control " placeholder="Municipio">

                        </div>
                        <div class="input-group  mb-3">
                            <input type="text" v-model="correo"
                            class="form-control " placeholder="Correo">
                            <input type="text" v-model="numCelular"
                            class="form-control " placeholder="Num. Celular">
                            <input type="text" v-model="cargo"
                            class="form-control " placeholder="Cargo">
                        </div>
                        <div class="btn-group d-flex justify-content-center">
                            <button v-on:click="agregarEmpleado()"
                            class="btn btn-success btn-lg">Agregar</button>
                            <button v-on:click="limpceldas()"
                            class="btn btn-danger btn-lg">Limpiar</button>
                        </div>
                        <br>
                        <div class="row row-cols-1 row-cols-md-3 g-4">
                            <div v-for="(empleado, index) of listEmpleados" :key="index" class="col">
                                <div class="card">
                                    <div class="card-body">
                                        <h5 class="card-title">{{empleado.nombre}}</h5>
                                        <h6 class="card-subtitle mb-2 text-body-secondary">{{empleado.paterno}}</h6>
                                        <p class="card-text">{{ empleado.correo }}</p>
                                        <p class="card-text">{{ empleado.celular }}</p>
                                        <a href="#" class="btn btn-primary">EDITAR</a>
                                        <a href="#" v-on:click="eliminarempleado(index)" class="btn btn-danger">ELIMINAR</a>
                                    </div>
                                </div>
                            </div>

                        </div>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'RegistroPersonas',
    data(){
        return{
            nombre: '',
            aPaterno: '',
            aMaterno: '',
            cp: '',
            pais: '',
            estado: '',
            municipio: '',
            correo:'',
            numCelular: '',
            cargo:'',
            listEmpleados:[]
        }
    },
    methods:{
        agregarEmpleado(){
            const empleado ={
                nombre: this.nombre,
                paterno: this.aPaterno,
                materno: this.aMaterno,
                cp: this.cp,
                pais: this.pais,
                estado: this.estado,
                munipio: this.municipio,
                correo: this.correo,
                celular: this.numCelular,
                cargo:this.cargo
            }
            this.listEmpleados.push(empleado);
            this.nombre = '';
            this.aPaterno= '';
            this.aMaterno= '';
            this.cp= '';
            this.pais= '';
            this.estado= '';
            this.municipio= '';
            this.correo= '';
            this.numCelular= '';
            this.cargo= '';
        },
        limpceldas(){
            this.nombre = '';
            this.aPaterno= '';
            this.aMaterno= '';
            this.cp= '';
            this.pais= '';
            this.estado= '';
            this.municipio= '';
            this.correo= '';
            this.numCelular= '';
            this.cargo= '';
        },
        eliminarempleado(index){
            this.listEmpleados.splice(index,1)
        }
    }
}
</script>

<style  scoped></style>