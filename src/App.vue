
<script>
import { DropDownTreeComponent } from "@syncfusion/ej2-vue-dropdowns";
var LocalData =  [
  { id: 1, name: 'Laura Callahan', eimg: '2', job: 'General Manager', subChild: true, expanded: true },
  { id: 2, pid: 1, name: 'Nancy Davolio', eimg: '4', job: 'Product Manager', subChild: true, expanded: true },
  { id: 3, pid: 2, name: 'Andrew Fuller', eimg: '7', job: 'Team Lead', subChild: true, expanded: true},
  { id: 4, pid: 3, name: 'Anne Dodsworth', eimg: '1', job: 'Developer'},
  { id: 5, pid: 2, name: 'Michael Suyama', eimg: '9', job: 'Team Lead', subChild: true, expanded: true},
  { id: 6, pid: 5, name: 'Robert King', eimg: '8', job: 'Developer' },
  { id: 7, pid: 5, name: 'Mary', eimg: '6', job: 'Developer' },
  { id: 8, pid: 1, name: 'Janet Leverling', eimg: '3', job: 'HR' }
  ];
   export default {
    components: {
      'ejs-dropdowntree': DropDownTreeComponent
    },
    data (){
    return {
      fields: { dataSource: LocalData, parentValue: 'pid', value: 'id', text: 'name', hasChildren: 'subChild'},
      treeSettings: { autoCheck: true}
    }
    }
  }
</script>
<template>
  <div class="dropdowntree">
  <ejs-dropdowntree :fields='fields' placeholder="Select an Employee"
   popupHeight='300px' popup-width="300px"  :itemTemplate="'iTemplate'" :headerTemplate="'hTemplate'"
   :footerTemplate="'fTemplate'" :showCheckBox='true' :treeSettings='treeSettings'
    mode= 'Custom' customTemplate='${value.length} item(s) selected' >
   <template v-slot:iTemplate="{data}">
    <div>
        <img class="eimage" :src="'https://ej2.syncfusion.com/vue/demos/styles/images/Employees/' + data['eimg'] + '.png'"  />
        <div>
            <div class="ename"> {{data.name}} </div>
            <div class="ejob"> {{data.job}} </div>
        </div>
    </div>
    </template>
    <template v-slot:hTemplate >
      <div class="header"> Employee List </div>
    </template>
    <template v-slot:fTemplate="{}">
      <div class="footer">
        <span>Total list items: 8</span>
      </div>
    </template>
    <!-- <template v-slot:noRecordsTemplate="{}">
      <span class='norecord'>NO DATA AVAILABLE</span>
    </template> -->
  </ejs-dropdowntree>
  </div>
  </template>
  
  
<style>
.dropdowntree {
  width: 300px;
  margin-bottom: 200px; 
}
.ename {
  padding-top: 5px;
  opacity: .87;
  line-height: 1.5em;
  margin-top: 1px;
  font-size: 15px;
}
.eimage {
  margin: 6px 16px;
  float: left;
  width: 40px;
  height: 40px;
}
.ejob {
font-size: 14px;
color: #979A9C;
opacity: .87;
}
.e-treeview .e-fullrow {
  height: 72px;
}
.header {
  height: 40px;
  line-height: 40px;
  font-size: 14px;
  margin: 0 auto;
  width: 260px;
  font-weight: 600;
  background-color: #f5f5f5;
  padding: 0 20px;
}
.footer {
  text-indent: 1.2em;
  display: block;
  font-size: 15px;
  line-height: 40px;
  border-top: 1px solid #e0e0e0;
}
</style>