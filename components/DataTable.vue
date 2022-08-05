<template>
    <div>
        <el-table :data="pagedTableData" style="width: 100%" v-loading="usersLoading">
            <el-table-column prop="id" label="Id" width="180"></el-table-column>
            <el-table-column prop="name" label="Имя" width="180"></el-table-column>
            <el-table-column prop="role" label="Роль"></el-table-column>
            <el-table-column prop="ctime" label="Дата создания"></el-table-column>
            <el-table-column prop="ctime" label="Действие"></el-table-column>
        </el-table>
        <el-pagination layout="prev, pager, next" :total="this.tableData.length" @current-change="setPage">
        </el-pagination>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        created() {
            this.fetchUsers();
        },
        data() {
            return {
                tableData: [],
                page: 1,
                limit: 100,
                pageSize: 5,
                usersLoading: false,
                users: []
            }
        },
        computed: {
            pagedTableData() {
                return this.tableData.slice(this.pageSize * this.page - this.pageSize, this.pageSize * this.page)
            }
        },
        methods : {
            setPage (val) {
                this.page = val
            },       
            async fetchUsers(){
                try {
                    this.usersLoading = true;
                    setTimeout(async () => {
                        const response = await axios.get('https://test.relabs.ru/api/users/list', {
                        params: {
                                page: 1,
                                limit: this.limit
                            }
                        });
                        this.users = response.data;

                        this.usersLoading = false;
                        for(let i=0; i<this.users.items.length; i++) {
                            let item = this.users.items[i];
                            this.tableData.push({
                                id: item.id,
                                role: item.role,
                                name: item.name,
                                ctime: item.ctime,
                            });
                        };
                        this.usersLoading = false;
                    }, 1000);

                } catch(e) {
                    alert('Ошибка');
                } finally {
                    //this.usersLoading = false;
                }
            },
        },
        mounted() {
            
        },  
    }
</script>