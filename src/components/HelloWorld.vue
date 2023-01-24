<template>
    <div class="text-left p-5 container bg-slate-300 border-slate-500 border-8 border-dashed rounded-xl">
        <form>
          <div id="req" class="flex flex-col">
              <label>Intruder</label>
              <input type="text" v-model="intruderName" name="intruderName" placeholder="Intruder`s Name">
              <label>Posada</label>
              <input type="text" v-model="posada" name="text" placeholder="Intruder`s posada">
              <label>Place</label>
              <input type="text" v-model="place" name="text" placeholder="Intruder`s place">
              <label>Message</label>
              <textarea name="message" v-model="message" cols="30" rows="5" placeholder="Message"></textarea>
              
              <label>anonim <input type="checkbox" v-model="anonim"></label>
          </div>

          <div id="notReq" v-show="!anonim" class="flex flex-col">
              <label>Name</label>
              <input type="text" v-model="fullName" name="name" placeholder="Your Name">
              <label>Phone</label>
              <input type="text" v-model="phone" name="phone" placeholder="Your phone">
          </div>

          <!-- <input type="submit" value="Send" > -->
          <button @click="sendMail" class="bg-slate-500 color text-white mt-5">Send</button>
        </form>
    </div>
</template>

<script>
import emailjs from "emailjs-com";
export default {
    data(){
        return{
            anonim:false,
            intruderName: '',
            fullName: 'anonim',
            posada:'',
            place:'',
            message:'',
            phone:'---',
            //emailTo:'koratgorovich2017@gmail.com',
            emailTo:'sladkovaoe@gmail.com',
        }
    },
    methods:{
        sendMail(){
            //emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
            console.log('Try!');
            emailjs.send('service_djz7rj7', 'template_s8ijnzb', {
                emailTo: this.emailTo,
                message: this.message,
                to_name: this.emailTo.slice(0,this.emailTo.indexOf("@")),
                intruderName: this.intruderName,
                posada: this.posada,
                place: this.place,
                fullName: this.fullName,
                phone: this.phone,
            },"HMBT3j8u7Sjcz0Q_Y")
            .then(function(response) {
                console.log('SUCCESS!', response.status, response.text);
            }, 
            function(error) {
                console.log('FAILED...', error);
            });

            // emailjs.send("service_djz7rj7","template_s8ijnzb",{
            //     to_name: "uuu",
            //     message: "yyyyyyyyy",
            //     from_name: "drgdrg",
            //     emailTo: "koratgorovich2017@gmail.com",
            // });
        }
    }
}

</script>

<style scoped>
/* * {box-sizing: border-box;} */

/* .container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
}

input, textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

label input[type="checkbox"]{
  float: left;
}

input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
} */
</style>
