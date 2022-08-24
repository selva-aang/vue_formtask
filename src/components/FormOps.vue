 
            <template>
                
                <div class="form-control">
                    <!-- <input type="text" class="form-control" name="field_1" id="field_1" placeholder="Name" data-msg-required="This field is required" style="background: rgb(255, 255, 255) none repeat scroll 0% 0%;">
                
                <input type="email" class="form-control" name="field_2" id="field_2" placeholder="Email" data-msg-required="This field is required" style="background: rgb(255, 255, 255) none repeat scroll 0% 0%;"> -->
                <!-- <input type="password" class="form-control" name="pass" id="pass"  placeholder="Password" value=""  data-msg-required="This field is required" aria-label="Password"> -->
                    <!-- <span>Gender: {{ gender }}</span> -->
                    <!-- <input type="radio" id="one" value="Male" v-model="Gender">
                    <label for="one">Male</label>
                    <br>
                    <input type="radio" id="two" value="Two" v-model="Gender">
                    <label for="two">Female</label>
                    <br> -->
                        
                <v-text-field
                v-model="name"
                :counter="15"
                :rules="nameRules"
                label="Name"
                required
            ></v-text-field>
        
            <v-text-field
                v-model="email"
                :rules="emailRules"
                label="E-mail"
                required
            ></v-text-field>
            <v-text-field
            v-model="lengthPassword"
            label="Length password"
            >
            </v-text-field>
            
            
        <v-container fluid>
        <v-row>
           

            <v-col
            cols="12"
            sm="6"
            >
            <v-text-field
                v-model="password"
                label="password"
               
            ></v-text-field>
            </v-col>
            <v-col>
                <v-btn 
                @click="generatePassword">
                    Generate
                </v-btn>
            </v-col>

            

         
        </v-row>
        </v-container>
    
            
            
    <v-row align="center">
        <v-col cols="12">
            <v-combobox
          v-model="select_the_state"
          :items="items"
          label="Select the state"
          outlined
          dense
        ></v-combobox>
        <!-- <v-select
            :items="items"
            select_the_state
            label="Select_the_state"
        ></v-select> -->
        </v-col>
    </v-row>

    
            
            
                

            
            
            
        
        
                <v-radio-group v-model="radioGroup">
                <v-radio
                    
                
                    label="Male"
                    value="radio-Male"
                ></v-radio>
                <v-radio
                    label="Female"
                    value="radio-Female"
                ></v-radio>
                
                
                </v-radio-group>
            

                    <!-- <span>Checked boxes: {{ checkBoxes }}</span>
                    <br>
                    <input type="checkbox" id="1" value="yes i'm interested in" v-modal="checkBoxes">
                    <label for="1">yes i'm interested in</label>
                    <input type="checkbox" id="2" value="yes i'm not interested" v-modal="checkBoxes">
                    <label for="2">yes i'm not interested </label>

                    <br> -->
              
              <v-checkbox
              v-model="checkBoxes"
              label="yes i'm interested in"
              color="blue"
              value="yes i'm interested in"
              hide-details
            ></v-checkbox>
                 <v-checkbox
              v-model="checkBoxes"
              label="yes i'm not interested"
              color="red"
              value="yes i'm not interested"
              hide-details
            ></v-checkbox>
            
                <v-btn
                 
                    rounded
                    color="primary"
                    @click ="handleSave"
                >
                 Save
                </v-btn>
                 <td>
                    <v-btn 
                    rounded
                    color="primary"
                    @click="editUpdate"
                    >
                     edit

                    </v-btn>

                </td>

            <v-simple-table fields="fields">
            <template v-slot:default>
            <thead>
                <tr>
                <th class="text-left">
                    Name
                </th>
                <th class="text-left">
                    Email
                </th>
                <th class="text-left">
                    Choose the state
                </th>
                <th class="text-left">
                    Gender
                </th>
                <th class="text-left">
                    Feedback
                </th>
                  <th class="text-left">
                    Actions
                </th>
                </tr>
            </thead>
            <tbody>
                <tr
                v-for="(item, index) in save"
                :key="item.name"
                >
                <td>{{ item.name }}</td>
                <td>{{ item.email }}</td>
                
                <td>{{item.select_the_state}}</td>
                <td>{{item.radioGroup}}</td> 
                <td>{{item.checkBoxes}}</td>
                <td>
                    <v-btn 
                    depressed
                    @click="deleteUser(index)">
                      <i class="fa fa-trash"></i>
                    </v-btn>
                </td>
                <td>
                    <v-btn 
                    depressed
                    @click="editUser(index)">
                     <i class="fa fa-edit" style="font-size:38px;color:blue"></i>

                    </v-btn>
                </td>
               


                <!-- <td>{{item.edit}}</td>
                <td>{{item.delete}}</td>
                <v-row
                        align="center to right"
                        justify="center"
                       
                >
   
                    <v-btn
                    color="primary"
                    depressed
                    >
                    <v-icon left>
                    <font-awesome-icon icon="fa-solid fa-circle-trash" />

                        
                    </v-icon>
                    Delete
                    </v-btn>
                </v-row> -->
                <!-- <font-awesome-icon icon="fa-solid fa-circle-trash" />
                {{ icons.mdiDelete }} -->
                </tr>
            </tbody>
            </template>
           </v-simple-table>
                </div>
            </template>
            <script>


        export default {
         data ()  {
            return {  
            lengthPassword: '',
            valid: true,
            name: '',
            email: '',
            password:'',
            select_the_state: '',
            radioGroup: [],
            checkBoxes: [],
            save: [],
            edit:[],
            rowId:0,
            
        
              
            nameRules: [
                v => !!v || 'Name is required',
                v => (v && v.length <= 15) || 'Name must be less than 15 characters',
            ],
            
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
            ],
            items: ['Andhra', 'karantaka', 'tamilnadu','Delhi', 'kolkata'],
            
            
            rules: {
                required: value => !!value || 'Required.',
                min: v => v.length >= 8 || 'Min 8 characters',
                emailMatch: () => (`The email and password you entered don't match`),
            },
            
        
              
            
             } },
    
    methods:{
        generatePassword(){
    
            const Allowed = {
                Uppers: "QWERTYUIOPASDFGHJKLZXCVBNM",
                Lowers: "qwertyuiopasdfghjklzxcvbnm",
                Numbers: "1234567890",
                Symbols: "!@#$%^&*"
            }
            const getRandomCharFromString = (str) => str.charAt(Math.floor(Math.random() * str.length))
            const generate = (length = this.lengthPassword) => { // password will be @Param-length, default to 8, and have at least one upper, one lower, one number and one symbol
                let pwd = "";
                pwd += getRandomCharFromString(Allowed.Uppers); //pwd will have at least one upper
                pwd += getRandomCharFromString(Allowed.Lowers); //pwd will have at least one lower
                pwd += getRandomCharFromString(Allowed.Numbers); //pwd will have at least one number
                pwd += getRandomCharFromString(Allowed.Symbols);//pwd will have at least one symbol
                for (let i = pwd.length; i < length; i++)
                    pwd += getRandomCharFromString(Object.values(Allowed).join('')); //fill the rest of the pwd with random characters
                return pwd
            }
            this.password = generate(this.lengthPassword)
        },
         handleSave(){
            this.save.push({
                name: this.name,
                email: this.email,
                lengthPassword: this.lengthPassword,
                password:this.password,
                select_the_state: this.select_the_state,
                radioGroup: this.radioGroup,
                checkBoxes: this.checkBoxes,
            })
            console.log(this.save)
            },

        deleteUser(id){
            this.save.splice(id,1)
        },
        editUser(id){
      // console.log(this.save[id].name);
      this.rowId = id
      this.name = this.save[id].name
      this.email = this.save[id].email
      this.select_the_state = this.save[id].select_the_state
      this.radioGroup = this.save[id].radioGroup
      this.checkBoxes = this.save[id].checkBoxes
      
      
      
      
    },
    editUpdate(){
      
      this.save[this.rowId].id=this.id
      this.save[this.rowId].name=this.name
      this.save[this.rowId].email=this.email
      this.save [this.rowId].select_the_state=this.select_the_state
      this.save [this.rowId].radioGroup=this.radioGroup
      this.save[this.rowId].checkBoxes=this.checkBoxes
      
      
      
      
    },

             
    
    // computed:{
        // isButtonClick() {
        // return (
        //     this.name.length == 0 ||
        //     this.email.length == 0 ||
        //     this.lengthPassword.length == 0 ||
        //     this.select_the_state.length == 0 ||
        //     this.radioGroup.length == 0 ||
        //     this.checkBoxes.length == 0
          
            
        //     )
        //   }
        // },

          
           
        
       

    }}
            </script>