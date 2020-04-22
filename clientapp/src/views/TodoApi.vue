<template>
  <div class="todo-api">
    <h3>Lista Todo´s</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Complete</th>
          <th scope="col-2"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="value in values" :key="value.id">
          <td scope="row">{{ value.id }}</td>
          <td>{{ value.name }}</td>
          <td>{{ value.isComplete }}</td>
          <td>
            <ul class="list-inline m-0">
              <li class="list-inline-item">
                <button
                  class="btn btn-success btn-sm rounded-2"
                  type="button"
                  data-toggle="tooltip"
                  data-placement="top"
                  title="Edit"
                >
                  <i class="fa fa-edit"></i>
                </button>
              </li>
              <li class="list-inline-item">
                <button
                  class="btn btn-danger btn-sm rounded-2"
                  type="button"
                  data-toggle="tooltip"
                  data-placement="top"
                  title="Delete"
                >
                  <i class="fa fa-trash"></i>
                </button>
              </li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "todo-api",
  data() {
    return {
      values: []
    };
  },
  created() {
    // Send request to the ASP.NET Core application.
    // No need to specify the host:port since it all runs from the same location
    return fetch("api/todoitem")
      .then(res => res.json())
      .then(data => {
        console.log(data);
        this.values = data;
      });
  },
  methods: {}
};
</script>

<style lang="scss" scoped>
$primary: #42b983;
$fontColor: #fff;

.btn-loading {
  border: 1px solid $primary;
  color: $primary;
}

.btn-loading:hover {
  border: 1px solid $primary;
  background: $primary;
  color: $fontColor;
}

.btn-loading:focus {
  box-shadow: 0 0 0 0.2rem $primary;
}
</style>
