<template>
  <div id='Formulariodecontacto' class="container" >
    <div v-if="!ingreso" id='formulariodecontacto' class="row">
      <div id='titulo' class="row my-2">
        <h1>{{titulo}}</h1>
      </div>
      <div class='col-8 border rounded'>					
      <div class="formulariodecontacto-group">
        <label for="name" class="cols-sm-2 control-label">{{campo_nombre}}</label>
        <div class="cols-sm-10">
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-user fa" aria-hidden="true"></i></span>
            <input v-model="pdNombre" type="text" class="form-control" name="name" id="name"  :placeholder='campo_nombre'/>
          </div>
      </div>
      </div>
      
      <div class="formulariodecontacto-group">
        <label for="email" class="cols-sm-2 control-label">{{campo_email}}</label>
        <div class="cols-sm-10">
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-envelope fa" aria-hidden="true"></i></span>
            <input type="text" class="form-control" 
                    name="pdEmail" id="pdEmail" 
                    :placeholder="campo_email"
                    v-model='pdEmail'/>
          </div>
        </div>
      </div>

      <div class="formulariodecontacto-group">
        <label for="username" class="cols-sm-2 control-label">{{campo_usuario}}</label>
        <div class="cols-sm-10">
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-users fa" aria-hidden="true"></i></span>
            <input type="text" class="form-control" name="username" id="username"  :placeholder="campo_usuario"/>
          </div>
        </div>
      </div>

      <div class="formulariodecontacto-group">
        <label for="password" class="cols-sm-2 control-label">{{campo_pass}}</label>
        <div class="cols-sm-10">
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-lock fa-lg" aria-hidden="true"></i></span>
            <input type="password" class="form-control" 
                    name="password" id="password"  
                    :placeholder="campo_pass"
                    v-model="pdPass" />
          </div>
        </div>
      </div>

      <div class="formulariodecontacto-group">
        <label for="confirm" class="cols-sm-2 control-label">{{campo_pass_confirm}}</label>
        <div class="cols-sm-10">
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-lock fa-lg" aria-hidden="true"></i></span>
            <input type="password" class="form-control" name="confirm" id="confirm"  :placeholder="campo_pass_confirm"/>
          </div>
        </div>
      </div>

      <div class="formulariodecontacto-group col-3">
        <button type="button" 
                class="btn btn-primary btn-lg btn-block login-button"
                @click='validateLogin($event)'>Registro</button>
      </div>
      </div>
    </div>
    <div v-else>
      <h1>Registro satisfactorio en el sistema</h1>
      <h5>Muchas gracias por crear su registro {{pdNombre}} </h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      titulo : 'Registro del Sistema',
      campo_nombre: 'Nombre Completo',
      campo_email: 'Correo Electrónico',
      campo_usuario: 'Nombre de usuario',
      campo_pass: 'Contraseña',
      campo_pass_confirm: 'Confirme la contraseña',
      pdEmail:'',
      pdPass:'',
      pdNombre:'',
      ingreso:false
    }
  },
  methods: {
    validateLogin: function(){
      if (this.emailValido(this.pdEmail) &&
          this.passValido(this.pdPass) && !this.vacio(this.pdNombre))
        this.ingreso=true;
      else
        alert('Campo inválidos');
    },
    emailValido:function(email){
      const reEmail=/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$/;
      return reEmail.test(email);
    },
    passValido:function(pass){
      const rePass=/.{3,14}/;
      return rePass.test(pass);
    },
    vacio(campo){
      return (campo === '');
    }
  }
}
</script>