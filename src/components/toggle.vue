<template>
<div class="aling">
<label class="switch">
    <input type="checkbox"  @change="toggleTheme()" />
    <span class="slider round" v-if="this.theme == 'lightMode'"> </span>
    <span class="slider round" v-else> </span>  
</label>  
</div>
</template>


<script>
export default {
    data() {
        return {
            theme: '' 
        };
    },

    mounted() {
        let localTheme = localStorage.getItem('theme'); 
        document.documentElement.setAttribute('data-theme', localTheme); // updates the data-theme 
    },
methods:{
    toggleTheme() {
                // this.theme = 'lightMode'
                this.theme = this.theme === 'lightMode' ? '' : 'lightMode'; //toggles theme value
                document.documentElement.setAttribute('data-theme', this.theme); 
                localStorage.setItem('theme', null); // stores theme value in local storage
    }
}  
}
</script>
<style>
.switch {
  position: relative;
  display: inline-block;
  width: 50px;
  height: 24px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 30px;
  width: 30px;
  left: 0px;
  bottom: 4px;
  top: 0;
  bottom: 0;
  margin: auto 0;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  box-shadow: 0 0px 15px #2020203d;
  background: white url('https://i.ibb.co/FxzBYR9/night.png');
  background-repeat: no-repeat;
  background-position: center;
}


input:checked + .slider {
  background-color: #2196F3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(24px);
  -ms-transform: translateX(24px);
  transform: translateX(24px);
  background: white url('https://i.ibb.co/7JfqXxB/sunny.png');
  background-repeat: no-repeat;
  background-position: center;
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
.aling{
    display: flex;
    justify-content: flex-end;
}
</style>
