<template>
  <div id="app">
    <div class="container">
      <div>
          <label class="form-label">Email</label>
      <input type="email" class="form-control" :class="{'is-invalid' :$v.email.$error , 'is-valid':!$v.email.invalid && $v.email.$dirty}"  v-model="email" @blur="$v.email.$touch()">
        <div  class="invalid-feedback" v-show='!$v.email.required'>
        Iltimos maydonni to'ldairing
      </div>

      <div  class="invalid-feedback" v-show='!$v.email.email'>
        Maydonga email farmatidagi ma'lumot kiriting
      </div>
      </div>
      <hr>

      <div>
        
        <label class="form-label">Ism</label>
      <input type="text" class="form-control" :class="{'is-invalid' :$v.name.$error , 'is-valid':!$v.name.invalid && $v.name.$dirty}"  v-model="name" @blur="$v.name.$touch()">
      <div  class="invalid-feedback" v-show='!$v.name.required'>
        Iltimos maydonni to'ldairing
      </div>

      <div  class="invalid-feedback" v-show='!$v.name.minLenth'>
        Maydonga eng kamida 5 ta simvol yozilsain
      </div>
      </div>

      <button class=" mt-3 btn btn-primary" type="submit" :class="{'disabled':$v.$invalid}">Отправить</button>
      <pre>{{ $v }}</pre>
    </div>
  </div>
</template>

<script>
import { required, email, minLength } from "vuelidate/lib/validators";

export default {
  name: "App",
  data() {
    return {
      email: '', name:''}
    },
  validations: {
    email: {required, email},
    name: {
    required, 
    minLenth: minLength(5)
    }
  }
}

</script>

<style>

  
</style>
