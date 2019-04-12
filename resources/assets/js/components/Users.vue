<template>
    <div class="container">
        <div class="row mt-5">
        <div class="col-md-12">
          <div class="card">
            <div class="card-header">
              <h3 class="card-title">Users Table</h3>

              <div class="card-tools">
                <button class="btn btn-success" data-toggle="modal" data-target="#addnewModalWindow">Add New <i class="fa fa-user-plus fa-fw"></i></button>
              </div>
            </div>
            <!-- /.box-header -->
            <div class="card-body table-responsive no-padding">
              <table class="table table-hover">
                <tbody><tr>
                  <th>ID</th>
                  <th>Name</th>
                  <th>Email</th>
                  <th>Type</th>
                  <th>Modify</th>
                </tr>
                <tr>
                  <td>183</td>
                  <td>John Doe</td>
                  <td>11-7-2014</td>
                  <td><span class="label label-success">Approved</span></td>
                  <td><a href="">Edit
                      <i class="fa fa-edit"></i>/
                      <i class="fa fa-trash"></i>
                      </a>
                  </td>
                </tr>
                
              </tbody></table>
            </div>
            <!-- /.box-body -->
          </div>
          <!-- /.box -->
        </div>
      </div>

      <!-- Modal -->
        <div class="modal fade" id="addnewModalWindow" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered" role="document">
            <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Add New</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <form @submit.prevent="createUser" class="action">
            <div class="modal-body">
                <div class="form-group">
                <label></label>
                <input v-model="form.name" type="text" name="name"
                    placeholder="Name"
                    class="form-control" :class="{ 'is-invalid': form.errors.has('name') }">
                <has-error :form="form" field="name"></has-error>
                </div>
                <div class="form-group">
                <label></label>
                <input v-model="form.email" type="text" name="email"
                    placeholder="Email"
                    class="form-control" :class="{ 'is-invalid': form.errors.has('email') }">
                <has-error :form="form" field="email"></has-error>
                </div>

                <div class="form-group">
                <label></label>
                <textarea v-model="form.bio" type="text" name="bio"
                    placeholder="Bio"
                    class="form-control" :class="{ 'is-invalid': form.errors.has('bio') }"></textarea>
                <has-error :form="form" field="bio"></has-error>
                </div>

                <div class="form-group">
                <label></label>
                <select v-model="form.type" type="text" name="type"
                    placeholder="Type"
                    class="form-control" :class="{ 'is-invalid': form.errors.has('type') }">
                    <option value="">Select User Role</option>
                    <option value="admin">Admin</option>
                    <option value="user">Standard User</option>
                    <option value="author">Author</option>
                </select>
                
                <has-error :form="form" field="type"></has-error>
                </div>

                <div class="form-group">
                <label></label>
                <input v-model="form.password" type="text" name="password"
                    placeholder="Password"
                    class="form-control" :class="{ 'is-invalid': form.errors.has('password') }">
                <has-error :form="form" field="password"></has-error>
                </div>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>
                <button type="submit" class="btn btn-primary">Create</button>
            </div>
            </form>
            </div>
        </div>
        </div>

    </div>
</template>

<script>
    export default {
        data(){
            return{
                form: new Form({
                    name : '',
                    email :'',
                    password : '',
                    type : '',
                    bio : '',
                    photo :''

                })
            }
        },
        methods:{
            createUser(){
                this.form.post('api/user')
             .then(({ data }) => { console.log(data) })
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
