<template>
  <div>
    <h1>Catalog List</h1>
    <p>This is a catalogs list page</p>
    <b-form-group id="input-group-1" label="ID:" label-for="input-id" description="Insert ID">
      <b-form-input id="input-id" v-model="itemId" placeholder="Enter ID" required></b-form-input>
    </b-form-group>
    <b-form-group id="input-group-2" label="Description:" label-for="input-description" description="Insert description">
      <b-form-input id="input-description" v-model="itemDescription" placeholder="Enter description" required></b-form-input>
    </b-form-group>
    <b-form-group id="input-group-3" label="Remark:" label-for="input-remark" description="Insert remark">
      <b-form-input id="input-remark" v-model="itemRemark" placeholder="Enter remark" required></b-form-input>
    </b-form-group>
    <b-button @click="addItem()" variant="primary">Submit</b-button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      items: [],
      itemId: '',
      itemDescription: '',
      itemRemark: '',
      itemIssueDate: '',
      itemLastUser: '',
      itemcreateDate: '',
      itemModifyDate: ''
    }
  },
  methods: {
    async addItem() {
      console.log(this.itemName)
      const res = await axios.post('/api/catalogs', { 
        id: this.itemId,
        description: this.itemDescription,
        remark: this.itemRemark,
        issueDate: '',
        lastUser: '6666',
        createDate: '',
        modifyDate: ''
      })
      this.items = [...this.items, res.data]
      this.itemId = ''
      this.itemDescription = ''
      this.itemRemark = ''
    }
  }
}
</script>