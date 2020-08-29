<template src="../templates/MontaMaquinaPage.html">
</template>
<script>
import picadeImage from "../assets/img/picade.png";
import picade10Image from '../assets/img/picade10.png';
import picadeStickImage from '../assets/img/picadestick.png';
import megapiImage from "../assets/img/megapi.png";
import gpiImage from "../assets/img/gpi.png";

var sistemas = [
    {'tipo': 'Arcade', 'imagen': picadeImage},
    {'tipo': 'Videoconsola', 'imagen': megapiImage},
    {'tipo': 'Portatil', 'imagen': gpiImage}
];

var carcasas = {
    Arcade: [
        {nombre:'Picade 8 pulgadas', imagen: picadeImage, precio: 175, descripcion: 'Sistema arcade Picade para 1 jugador con ampliación de mando o stick externo, pantalla de 8 pulgadas formato 4:3 clásico y entrada de alimentación USB-Tipo C, funciona con Raspberry Pi 4'},
        {nombre:'Picade 10 pulgadas', imagen: picade10Image, precio: 225, descripcion: 'Sistema arcade Picade para 1 jugador con ampliación de mando o stick externo, pantalla de 10 pulgadas formato 4:3 clásico y entrada de alimentación USB-Tipo C, funciona con Raspberry Pi 4' },
        {nombre:'Picade Stick', imagen: picadeStickImage, precio: 95, descripcion: 'Sistema arcade Picade para 1 jugador con ampliación de mando o stick externo, entrada de alimentación USB-Tipo C, funciona con Raspberry Pi 4'},
    ],
    Videoconsola: [
        {nombre:'Basic Case', imagen: '', precio: 0, descripcion: ''},
        {nombre: 'Argon One', imagen: '', precio: 0, descripcion: ''},
        {nombre:'Nespi Case', imagen: '', precio: 0, descripcion: ''},
        {nombre:'Nespi Case 4', imagen: '', precio: 0, descripcion: ''},
        {nombre:'Superpi Case', imagen: '', precio: 0, descripcion: ''},
        {nombre:'Superpi Case America', imagen: '', precio: 0, descripcion: ''},
        {nombre:'Megapi Case', imagen: megapiImage, precio: 0, descripcion: ''},
        {nombre:'Odroid Game Station Turbo', imagen: '', precio: 0, descripcion: ''},
    ],
    Portatil: [
        {nombre:'GPI Case', imagen: gpiImage, precio: 0, descripcion: ''},
        {nombre:'Odroid GO', imagen: '', precio: 0, descripcion: ''},
        {nombre:'Odroid GO Advance', imagen: '', precio: 0, descripcion: ''},
    ]
};

var presupuesto = {};

export default {
    name: "MontarMaquinaPage",
    data(){
        return{
            tipo_sistema: sistemas,
            tipo_carcasa: []
        }
    },
    methods: {
        siguientePregunta(valor, pregunta, siguiente){
            let pantalla = document.getElementById(pregunta);
            let pantalla_siguiente = document.getElementById(siguiente);

            this.tipo_carcasa = this.elegir_carcasa(valor);

            pantalla.classList.add('ocultar');
            window.setTimeout(() =>{
                pantalla.classList.remove('mostrar');
                pantalla.classList.add('borrar');
                pantalla_siguiente.classList.remove('borrar');
                pantalla_siguiente.classList.add('mostrar');
                pantalla_siguiente.classList.remove('ocultar');
            }, 500);
            presupuesto[pregunta] = valor;
            console.log(presupuesto);
        },
        elegir_carcasa(valor){
            if(valor == 'Arcade'){
                valor = carcasas['Arcade'];
            }else if(valor == 'Videoconsola'){
                valor = carcasas['Videoconsola'];
            }else if(valor == 'Portatil'){
                valor = carcasas['Portatil'];
            }else{
                valor = [];
            }

            return valor;
        }
    }
}
</script>