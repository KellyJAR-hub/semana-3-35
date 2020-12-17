<template>
    <div>
        <br>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class = "container">
                <a class = "navbar-brand" href = "#"></a>
                
                <div
                    class = "collapse navbar-collapse justify-content-end"
                    id = "navbarNav"
                >
                    <ul class = "navbar-nav">
                        <li class = "nav-item active">
                            <a class="btn btn-primary btn-lg active" role="button" @click = "logUserOut">Logout</a>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
        <section>
            <div class = "container mt-5">
                <div class = "row">
                    <div class="container h-100">
        <div class="row justify-content-center h-100">
            <div class="col-sm-8 align-self-center text-center">
                <div class="card shadow">
                    <div class="card-body">           
                      <h1 class="m-5">
                          <ul class = "list-group">
                            <li class = "list-group-item">Name : {{ user.name }}</li>
                            <li class = "list-group-item">Email : {{ user.email }}</li>
                          </ul>
                          </h1>                
                    </div>
                </div>
            </div>
        </div>
    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
import VueJwtDecode from "vue-jwt-decode";

export default {
    data() {
        return {
            user: {}
        };
    },
    methods: {
        getUserDetails(){
            let token = localStorage.getItem("jwt");
            let decoded = VueJwtDecode.decode(token);
            this.user = decoded;
        },
        logUserOut(){
            localStorage.removeItem("jwt");
            this.$router.push("/");
        }
    },
    created(){
        this.getUserDetails();
    }
};
</script>
<style scoped></style>