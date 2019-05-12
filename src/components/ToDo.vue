<template>
    <div　id=list>
        <strong>重要:タスク名:完了ボタン</strong>
        <div v-for="Task in Tasks":key="Task.name">
            <label class="Task" v-bind:style="[Task.vital ? vital:'',Task.done ? done:'',!Task.done ? yet:'']">
                <input type="checkbox" v-model="Task.vital"></input>
                <label class="name">名前:{{Task.name}}</label>
                <button @click="Task.done=!Task.done">完了</button>
            </label>
        </div>
        <div>
            <label for>
                <strong>やること:</strong>
                <input type="checkbox" id="ifvital" v-model="newTaskVital">
                <label for="ifvital"><small>(重要ならチェック)</small></label>
                <input type="text" v-model="newTaskName">
            </label>
            <button @click="addTask">add</button>
        </div>
        <div>
            表示するタスク:
            <input type="checkbox" id="showyet" v-model="Showyet"><label for="showyet">未完</label>
            <input type="checkbox" id="showdone" v-model="Showdone"><label for="showdone">完了</label>
            <button @click="refresh">表示更新</button>
        </div>
    </div>
</template>
<script>

export default{
    name:"Tasklist",
    
    data(){
        return{
            Tasks:[
            ],
            newTaskName:"",
            newTaskVital:false,
            Showyet:true,
            Showdone:true,
            vital:{
            "background":"red",
            },
            done:{
                "display":"block",
                "color":"#DDDDDD",
                "background":"white",
            },
            yet:{
                "display":"block"
            },
        };
        
    },
    methods:{
        addTask(){
            if(this.newTaskName!=""){
                this.Tasks.push({name:this.newTaskName, done:false,vital:this.newTaskVital})
                this.newTaskName=""
                this.newTaskVital=false;
            }else{
                alert("件名を入力しましょう");
            }
        },
        refresh(){
                if(this.Showdone){this.done.display="block";}else{this.done.display="none";};
                if(this.Showyet){this.yet.display="block";}else{this.yet.display="none";};
        },

    }
}
</script>
<style>
#list{
    
    margin-bottom:20px;
}
.Task{
    font-size:25px
}
</style>
