<template>
    <div> 
    <el-form :inline="true" :model="formInline" class="demo-form-inline" style="border-radius: 30px;">
        <el-form-item label="学校">
            <el-select v-model="school" placeholder="请选择学校" @change="ChangeSchool">
                <el-option v-for="item in schools" :key="item.value" :label="item.label" :value="item.value" ></el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="专业">
            <el-select v-model="major" placeholder="请选择专业" @change="ChangeMajor">
                <el-option v-for="item in majors" :key="item.value" :label="item.label" :value="item.value" ></el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="年级">
            <el-select v-model="grade" placeholder="请选择年级" @change="ChangeGrade">
                <el-option v-for="item in grades" :key="item.value" :label="item.label" :value="item.value" ></el-option>
            </el-select>
        </el-form-item>
        <el-form-item label="班级">
            <el-select v-model="class_" placeholder="请选择年级" @change="ChangeClass">
                <el-option v-for="item in classes" :key="item.value" :label="item.label" :value="item.value" ></el-option>
            </el-select>
        </el-form-item>
        <el-form-item><el-button type="primary" >查询</el-button></el-form-item>
        <el-form-item><el-button type="primary" >添加学生</el-button> </el-form-item>
    </el-form>
    <el-table :data="stuData" height="500" border style="width: 100%;font-size:20px;">
        <el-table-column prop="id" label="学号" style="width: 30%;"></el-table-column>
        <el-table-column prop="name" label="姓名" style="width: 30%;"></el-table-column>
    
        <el-table-column label="操作" style="width: 40%;" align="center">
            <template slot-scope="scope">
                <el-button type="text" icon="el-icon-edit" @click="editStudent">编辑</el-button>
                <el-button type="text" icon="el-icon-delete" class="red" @click="deleteStudent(scope.$index,scope.row)">删除</el-button>
            </template>
        </el-table-column>
  </el-table>
      <el-pagination class="pagination" background layout="prev, pager, next" :total="1000"></el-pagination>


    <!-- 编辑弹出框 -->
    <el-dialog title="编辑" :visible.sync="editVisible" width="30%">
        <el-form  :model="editstu" label-width="70px">
            <el-form-item label="学号">
                <el-input v-model="editstu.id"></el-input>
            </el-form-item>
            <el-form-item label="姓名">
                <el-input v-model="editstu.name"></el-input>
            </el-form-item>
        </el-form>
        <span slot="footer" class="dialog-footer">
            <el-button @click="editVisible = false">取 消</el-button>
            <el-button type="primary">确 定</el-button>
        </span>
    </el-dialog>






  </div>




   
</template>

<script>
export default {
    data() {
      return {
        editstu:{
            id:'',
            name:'',
        },
        editVisible:false,
        school:'',
        schools:[
        {
            value:1,
            label:'福州大学'
        },
        {
            value:2,
            label:'厦门大学'
        }
        ],
        major:'',
        majors:[{
            value:1,
            label:'电子信息'
        },{
            value:2,
            label:'计算机技术'
        }],
        grade:'',
        grades:[{
                value:1,
                label:'大一'
            },{
                value:2,
                label:'大二'
            },{
                value:3,
                label:'大三'
            }],
        class_:'',
        classes:[{
            value:1,
            label:'一班'
        },{
            value:2,
            label:'二班'
        }],

        stuData: []
      }
    },

    methods:{
        ChangeSchool(){
           console.log("ChangeSchool...");
           console.log(this.school);
        },
        ChangeMajor(){
           console.log("ChangeMajor...");
           console.log(this.major);
        },
        ChangeGrade(){
            console.log("ChangeGrade...");
            console.log(this.grade);
        },
        ChangeClass(){
            console.log("ChangeClass...");
            console.log(this.class_);
        },
        editStudent(){
            console.log("editStudent...");
            this.editVisible = !this.editVisible;
        },
        deleteStudent(index,row){
            console.log("deleteStudent...");
            console.log(index);
            console.log(row);
            this.$confirm('确定要删除吗？', '提示', {
                type: 'warning'
            }).then(() => {
                    this.$message.success('删除成功');
                   
                }).catch(() => {}
            )
        }


    }
  }

</script>

<style>
.pagination{
  text-align:center;
  font-size: 20px;
}
.red {
    color: #ff0000;
}
</style>