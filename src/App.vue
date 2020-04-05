<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives</h1>
              <p v-text="'Some text'"></p>
              <p v-html="'<strong>Some strong text</strong>'"></p>
            </div>
        </div>
        
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Custom Directives</h1>
              <p v-highlight.delayed.blink="'red'">Color This</p>
              <p v-local-highlight:background.delayed.blink="'red'">Color This too</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        directives: {
            'local-highlight': {
                bind(el, binding, vnode){
                // el.style.backgroundColor = 'green';
                //el.style.backgroundColor = binding.value;
                var delay=0;
                if(binding.modifiers['delayed']) {
                delay = 3000;
                }
                if(binding.modifiers['blink']){
                    let mainColor = binding.value;
                    let secondColor = 'green';
                    let currentColor =  mainColor;
             setTimeout(() => {
                 setInterval(() => {
                    if(currentColor == secondColor ? currentColor = mainColor : currentColor= secondColor);
                    if (binding.arg == 'background') {
                    el.style.backgroundColor = currentColor;
                }
                else{
                    el.style.color = currentColor;
                }
                 }, 500);

                }, delay);
                }
                else{
               setTimeout(() => {
                if (binding.arg == 'background') {
                    el.style.backgroundColor = binding.value;
                }
                else{
                    el.style.color = binding.value;
                }
                }, delay);
                }
 
            }
        }
        }
    }
</script>

<style>

</style>

