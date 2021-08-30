<!-- HTLM code -->
    <template>
    <div class="classe">
        <h1 id="titleMain"> Calcular horario </h1>
        <h1 class="mainText" id="text1"> Digite a hora e os minutos, dividindo-os com : (dois pontos) </h1>
        <input id="box1" v-model="horario1">
        <h1 class="mainText" id="text2"> Agora, digite a hora a ser calculada com primeira </h1>
        <input id="box2" v-model="horario2">
        <button id="botao1" v-on:click="somarHora"> Somar horario </button>
        <button id="botao2" v-on:click="subtrairHora"> Subtrair horario </button>
        <button id="botao3" v-on:click="diferencaHora"> Diferença de horas </button>
        <h1 class="mainText" id="text3"> {{horario3}} </h1>
    </div> 
    </template>

 

<!-- JavaScript code -->
    <script>
    export default{
        
        data() {
        return {
            horario1: " ",
            horario2: " ",
            horario3: " ",  
            hora: null,
            minuto: null,
        }
        },
        methods:{
            // Pega o numero e transforma em hora e minuto
            // Soma 
            somarNumero(){
                this.hora = parseInt(this.horario1.split(":")[0]) + parseInt(this.horario2.split(":")[0]);
                this.minuto = parseInt(this.horario1.split(":")[1]) + parseInt(this.horario2.split(":")[1]);
                
            },

            // Subtrai
            subtrairNumero(){
                this.hora = parseInt(this.horario1.split(":")[0]) - parseInt(this.horario2.split(":")[0]);
                this.minuto = parseInt(this.horario1.split(":")[1]) - parseInt(this.horario2.split(":")[1]);
               
                
            },

            // Função do botão pra somar
            somarHora(){
                this.somarNumero();
                var hora = this.hora;
                var minuto = this.minuto
                while(minuto > 59){
                    hora++;
                    minuto -= 60;
                }
                if(hora > 23){
                    hora -= 24;
                }
                if(minuto < 10){
                    minuto = "0" + minuto    
                }
                this.horario3 = hora + ":" + minuto;
                this.checkNumber()
            },

            // Função do botão pra subtrair
            subtrairHora(){
                this.subtrairNumero();
                var hora = this.hora;
                var minuto = this.minuto
                while(minuto < 0){
                    minuto = minuto + 60;
                    hora--;
                }
                if(hora < 0){
                    hora += 24;
                }   
                if(minuto < 10 && minuto >= 0){
                    minuto = "0" + minuto;    
                }
                this.horario3 = hora + ":" + minuto;
                this.checkNumber()
            },

            diferencaHora(){
                this.subtrairNumero();
                var hora = this.hora;
                var minuto = this.minuto
                if(minuto < 0){
                    minuto += 60;
                    minuto = minuto * (-1);
                    hora++
            
                }
            
                if(minuto < 10 && minuto >= 0){
                    minuto = "0" + minuto    
                }
                this.horario3 = hora + ":" + minuto;
                this.checkNumber()
            },

            checkNumber(){
                if(this.horario3 == "NaN:NaN" || this.horario3 == this.hora + ":NaN" || this.horario3 == "NaN:" + this.minuto){
                    this.horario3 = "Valor invalido detectado"
                }
            }

        },   
    }
    </script>

<!-- CSS code -->
    <style>

   

    </style>
