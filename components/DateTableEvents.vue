<template>
    <div>
        <el-table :data="tableData" style="width: 100%">
            <el-table-column prop="eventDate" label="Дата" width="180"></el-table-column>
            <el-table-column prop="event" label="Событие" width="180"></el-table-column>
        </el-table>
    </div>
</template>

<script>
    import moment from 'moment';

    export default {
        created() {
        },
        data() {
            return {
                tableData: [],
                message: "",
                logs: [],
                status: "disconnected",
                eventsTable: []
            }
        },
        computed: {
        },
        methods : {
            setPage (val) {
                this.page = val
            },
            connect() {
                this.socket = new WebSocket(" wss://test.relabs.ru/event");
                this.socket.onopen = () => {
                    this.status = "connected";
                    this.logs.push({ event: "Connected to", data: ' wss://test.relabs.ru/event'})
                    

                    this.socket.onmessage = ({data}) => {
                        this.logs.push({ event: "Recieved message", data });
                        data = JSON.parse(data);
                        this.tableData.push({
                            eventDate: moment(data.ctime).format('DD.MM.YYYY HH:mm'),
                            event: data.event
                        });
                    };
                };
            },
            disconnect() {
                this.socket.close();
                this.status = "disconnected";
                this.logs = [];
            },
            sendMessage(e) {
                this.socket.send(this.message);
                this.logs.push({ event: "Sent message", data: this.message });
                this.message = "";
            }
        },
        mounted() {
            this.connect();
        },  
    }
</script>