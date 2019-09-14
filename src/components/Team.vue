<template>
    <div>
        <el-row>
            <el-col>
                <div class="helptext"> To get started, click the button below and add a member to your party </div>
            </el-col>
        </el-row>
        <el-row class='give-margin'>
            <el-col :xs="12" :sm="6" :md="5" :lg="5" :xl="3" v-for="person in people" :key="person.id">
                <el-card class="box-card">
                    <div class='card-content'>
                        <div>Age: {{person.age}}</div>
                        <div>{{person.married}}</div>
                        <div>Gender: {{person.gender}}</div>
                        <div>Race: {{person.race}}</div>
                    </div>
                    <div class="bottom clearfix">
                        <el-button style="float: left; padding: 3px " type="text"
                        @click="onEdit(person.uid)">
                            Edit
                        </el-button>
                        <el-button style="float: right; padding: 3px" type="danger"
                        @click="deletePerson(person.uid)">
                            Delete
                        </el-button>
                    </div>
                </el-card>
            </el-col>
            <el-col :xs="12" :sm="6" :md="5" :lg="3" :xl="3">
                <el-card class="box-card" style="text-align: center;">
                    <el-image :src="img_url" fit="contain" style="height: 100px; cursor: pointer;"
                        @click="dialogFormVisible = true" />
                </el-card>
            </el-col>
            <el-col>
                <el-dialog :fullscreen='true' title="Add member to team" :visible.sync="dialogFormVisible">
                    <el-form :label-position="labelPosition" :model="form" v-model="form.age">
                        <el-form-item label="Age" :label-width="formLabelWidth">
                            <el-input-number v-model="default_age" :min="16" :max="150"></el-input-number>
                        </el-form-item>
                        <el-form-item label="Marirtal status" :model="form.married">
                            <el-radio-group v-model="default_radio">
                                <el-radio-button label="Not Married"></el-radio-button>
                                <el-radio-button label="Married"></el-radio-button>
                            </el-radio-group>
                        </el-form-item>
                        <el-form-item label="Gender">
                            <el-radio-group v-model="default_radio_gender" :model="form.gender">
                                <el-radio-button label="Male"></el-radio-button>
                                <el-radio-button label="Female"></el-radio-button>
                                <el-radio-button label="Other"></el-radio-button>
                            </el-radio-group>
                        </el-form-item>
                        <el-form-item label="Race">
                            <el-radio-group v-model="default_radio_race" :model="form.gender">
                                <el-radio-button label="Asian"></el-radio-button>
                                <el-radio-button label="Black"></el-radio-button>
                                <el-radio-button label="White"></el-radio-button>
                                <el-radio-button label="First Nations"></el-radio-button>
                                <el-radio-button label="Two or more races"></el-radio-button>
                                <el-radio-button label="Hawaiian or Pacific Islander"></el-radio-button>
                            </el-radio-group>
                        </el-form-item>
                    </el-form>
                    <span slot="footer" class="dialog-footer">
                        <el-button @click="dialogFormVisible = false">Cancel</el-button>
                        <el-button type="primary" @click="onSubmit">Confirm</el-button>
                    </span>
                </el-dialog>
            </el-col>
        </el-row>
        <api-call :team="people"/>
    </div>
</template>

<script>
import ApiCall from './ApiCall.vue'

    export default {
        name: 'team',
        components: {
            ApiCall,
        },
        data() {
            return {
                people: [],
                people_iowa: [],
                people_bc: [],
                dialogFormVisible: false,
                form: {
                    age: 19,
                    name: '',
                    married: false,
                    gender: 'Male',
                },
                personUid: 0,
                formLabelWidth: '120px',
                labelPosition: 'top',
                default_radio: 'Not Married',
                default_radio_gender: 'Male',
                default_radio_race: 'Male',
                default_age: 19,
                edit_id: -1,
            }
        },
        computed: {
            img_url() {
                return require('../assets/add-button.png')
            }
        },
        methods: {
            onSubmit() {
                this.dialogFormVisible = false
                let user_exists =  this.people.filter((obj) => {
                    return obj.uid === this.edit_id;
                }).length > 0
                if(user_exists){
                    let ind = this.people.findIndex(person => person.uid === this.edit_id)
                    this.people[ind].age = this.default_age,
                    this.people[ind].married = this.default_radio,
                    this.people[ind].gender = this.default_radio_gender,
                    this.people[ind].race = this.default_radio_race,
                    this.edit_id = -1
                }
                else {
                    this.people.push(
                        {
                            'uid': this.personUid,
                            'age': this.default_age,
                            'married': this.default_radio,
                            'race': this.default_radio_race,
                            'gender': this.default_radio_gender,
                        }
                    )
                    this.personUid += 1
                }
            },
            onEdit(personID) {
                this.edit_id = personID
                let ind = this.people.findIndex(person => person.uid === this.edit_id)
                this.default_age = this.people[ind].age
                this.default_radio = this.people[ind].married
                this.default_radio_gender = this.people[ind].gender
                this.default_radio_race = this.people[ind].race
                this.dialogFormVisible = true
            },
            deletePerson(personID) {
                this.people = this.people.filter( ( obj ) => {
                    return obj.uid !== personID;
                });
            }
        },
    }
</script>

<style scoped>
    .helptext {
        margin: 3em
    }

    .text {
        font-size: 14px;
    }

    .item {
        padding: 18px 0;
    }

    .box-card {
        margin: 1%;
        text-align: left;
        max-width: 350px;
    }

    .give-margin {
        margin: 2em
    }

    .text {
        font-size: 14px;
    }

    .item {
        margin-bottom: 18px;
    }

    .clearfix:before,
    .clearfix:after {
        display: table;
        content: "";
    }

    .clearfix:after {
        clear: both
    }

    .bottom {
        margin-top: 13px;
        line-height: 12px;
    }

    .add {
        background-color: #409EFF;
    }
</style>