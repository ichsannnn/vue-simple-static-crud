<template>
  <div class="container">
    <h3>{{ ichsan }}</h3>
    <div id="modalSiswa" class="modal">
      <div class="modal-content">
        <h4 v-show="!isEdit">Tambah Data Siswa</h4>
        <h4 v-show="isEdit">Ubah Data Siswa</h4>
        <div class="row">
          <div class="input-field col s12 m12 l12">
            <input type="hidden" v-model="text.id">
            <div class="input-field col s12 m12 l12">
              <input type="text" v-model="text.nis" placeholder="NIS">
            </div>
            <div class="input-field col s12 m12 l12">
              <input type="text" v-model="text.nama" placeholder="Nama">
            </div>
            <div class="input-field col s12 m12 l12">
              <input type="text" v-model="text.kelas" placeholder="Kelas">
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button @click="submit" v-show="!isEdit" class="btn waves-effect vue-color white-text">Tambah</button>
          <button @click="submit" v-show="isEdit" class="btn waves-effect vue-color white-text">Simpan</button>
          <button @click="clear" class="btn btn-flat waves-effect grey lighten-3 modal-close">Batal</button>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col s12 m12 l12">
        <div class="card z-depth-3">
          <div class="card-content">
            <div class="col s12 m6 l6">
              <div class="left">
                <span class="card-title">Data Siswa</span>
              </div>
            </div>
            <div class="col s12 m6 l6">
              <div class="right">
                <a href="#modalSiswa" @click="create" class="btn waves-effect vue-color icons modal-trigger tooltipped" data-position="top" data-delay="50" data-tooltip="Tambah Data Siswa"><i class="material-icons">add_circle</i></a>
              </div>
            </div>
            <table class="table bordered striped">
              <thead>
                <th>No</th>
                <th>NIS</th>
                <th>Nama</th>
                <th>Kelas</th>
                <th>Aksi</th>
              </thead>
              <tbody>
                <tr v-for="(data, index) in siswa">
                  <td>{{ index + 1 }}</td>
                  <td>{{ data.nis }}</td>
                  <td>{{ data.nama }}</td>
                  <td>{{ data.kelas }}</td>
                  <td>
                    <a href="#modalSiswa" @click="edit(index, data)" class="btn waves-effect blue icons modal-trigger tooltipped" data-position="top" data-delay="50" data-tooltip="Ubah Data Siswa"><i class="material-icons">edit</i></a>
                    <a href="#" @click="hapus(index, data)" class="btn waves-effect red icons tooltipped" data-position="top" data-delay="50" data-tooltip="Hapus Data Siswa"><i class="material-icons">delete</i></a>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
    <ul>
      <li><a href="https://github.com/skadevz/" target="_blank">github</a></li>
      <li><a href="https://facebook.com/skadevz/" target="_blank">facebook</a></li>
      <li><a href="https://twitter.com/skadevz/" target="_blank">twitter</a></li>
    </ul>
  </div>
</template>


<script>
export default {
  name: 'Siswa',
  data () {
    return {
      isEdit: false,
      msg: 'Welcome to Your Vue.js App',
      ichsan: 'Simple CRUD Siswa',
      text: {
        id: '',
        nis: '',
        nama: '',
        kelas: ''
      },
      siswa: [
        {nis: '10578', nama: 'Ichsan', kelas: 'RPL'}
      ]
    }
  },
  methods: {
    clear() {
      this.text.id = '';
      this.text.nis = '';
      this.text.nama = '';
      this.text.kelas = '';
      this.isEdit = false;
    },
    create() {
      this.clear();
      $('.modal').modal();
    },
    submit() {
      const id = this.text.id;
      const nis = this.text.nis;
      const nama = this.text.nama;
      const kelas = this.text.kelas;
      if (this.isEdit === false) {
        this.siswa.push({nis, nama, kelas});
        this.clear();
        alert('Data berhasil ditambahkan!');
        $('.modal').modal('close');
      } else if (this.isEdit === true) {
        this.siswa.splice(id, 1);
        this.siswa.push({nis, nama, kelas});
        this.clear();
        alert('Data berhasil diubah!');
        $('.modal').modal('close');
      }
    },
    edit(index, data) {
      this.isEdit = true;
      this.text.id = index;
      this.text.nis = data.nis;
      this.text.nama = data.nama;
      this.text.kelas = data.kelas;
      $('.modal').modal();
    },
    hapus(index, data) {
      let conf = confirm("Hapus " + data.nama + " dari kehidupanmu?");
      if (conf === true) {
        this.siswa.splice(index, 1);
        alert(data.nama + ' berhasil dihapus dari kehidupanmu!');
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.vue-color {
  background: #41B883;
}
.btn.icons{
  padding: 0 15px 0 15px;
  color: white;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
