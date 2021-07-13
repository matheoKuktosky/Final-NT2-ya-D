<template>
    <div>
    <h1>Matheo Kuktosky</h1>
    <input 
        type="text"
        v-model="text" 
    >
    <h3>cantidad: {{text.length}}</h3>
    <h3>{{ text | codificado }} (codificado)</h3>
    <h3>{{ text.toUpperCase() }} (Mayúscula)</h3>
    <h3>{{ text.toLowerCase() }} (Minúscula)</h3>
    <h3>{{ text | mayusMin }} (Mayúscula/Minúscula)</h3>
    <h3>{{ text | minMayus }} (Minúscula/Mayúscula)</h3>

    <hr>

    <p>respuestas: 1:b, 2:b, 3:c, 4:b, 5:b</p>
    
  </div>
</template>


<script>
    export default{
        data() {
            return{
                text: ''
            }
        }, 
        filters: {
            codificado: function (value) {
                let newValue = value.toLowerCase()
                let chars = {'a':'u','e':'o', 'o': 'e', 'u':'a'}
                newValue = newValue.replace(/[aeou]/g, m => chars[m] ?? m)
                return newValue
            },
            mayusMin: function (value) {
                let chars = value.toLowerCase().split("");
                for (let i = 0; i < chars.length; i += 2) {
                    chars[i] = chars[i].toUpperCase();
                }
                return chars.join("");
            },
            minMayus: function (value) {
                let chars = value.toUpperCase().split("");
                for (let i = 0; i < chars.length; i += 2) {
                    chars[i] = chars[i].toLowerCase();
                }
                return chars.join("");
            }
        }   
    }   
</script>