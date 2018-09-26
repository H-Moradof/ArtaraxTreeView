# ArtaraxTreeView
a TreeView jQuery plugin

## How to use

### 1) Put this on your html page:
``` html
 <ul class="treeview"></ul>
```

### 2) Add jquery and plugin file into your html page a:
``` javasript
<!-- jQuery -->
<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>

<!-- plugin -->
<script src="/artarax-treeview/jquery.artaraxtreeview.js"></script>
```

### 3) Declare a json array of objects with 'Id','Title','ParentId' properties 
(you can also declare an array of selected ids for checking some items on load)
``` javasript
var treeViewData = [
      { 'Id' : 1, 'Title' : 'روت', 'ParentId' : null },
      { 'Id' : 2, 'Title' : 'آیتم 1', 'ParentId' : 1 },
      { 'Id' : 3, 'Title' : 'آیتم 2', 'ParentId' : 1 },
      { 'Id' : 4, 'Title' : 'آیتم 3', 'ParentId' : 1 },
      { 'Id' : 5, 'Title' : 'آیتم 1-1', 'ParentId' : 2 },
      { 'Id' : 6, 'Title' : 'آیتم 1-2', 'ParentId' : 2 },
      { 'Id' : 7, 'Title' : 'آیتم 2-1', 'ParentId' : 3 },
      { 'Id' : 8, 'Title' : 'آیتم 3-1', 'ParentId' : 4 },
      { 'Id' : 9, 'Title' : 'آیتم 3-2', 'ParentId' : 4 }
  ];
        
var selectedItemIds = [7,8,9];
```


### 4) Set treeview settings and assign your previous variables
(you can also set multiple awesome settings like 'mode', 'isDisplayChildren' and etc)
``` javasript
// set settings
var artaraxTreeView = $.artaraxTreeView({
    jsonData: treeViewData,
    selectedIds: selectedItemIds, 
    updateCallBack: onUpdate, // callback function
    deleteCallBack: onDelete // callback function
});

// when user click the delete/update button on an item in treeview, the plugin send the item's object into your callback functions

function onUpdate(obj)
{
    // you can load updating item's data into your form to let user to edit that
    alert(obj.Id + " " + obj.Title + " " + obj.ParentId);
}

function onDelete(obj)
{
    // you can call an API to delete the item
    alert(obj.Id + " " + obj.Title + " " + obj.ParentId);
}

```

### 5) Load treeview by code below
``` javasript
// load treeview
artaraxTreeView.loadTreeViewOnInsert(1);
```

##### Here is the full settings and public functions that you can use

``` javasript
/* -------------------------------------------------------------
   options:
    {
        jsonData: 
            an object array with {Id, Title, ParentId} properties
        selectedIds: 
            an long array of selected ids
        isDisplayChildren:
            this make child <ul> tags display hidden or block. 
            *Valid values are true/false 
            (default is true)
        mode: 
            "deletable,updatable,radiobox,autoSelectChildren"
            (default is "deletable,updatable,autoSelectChildren")
        updateCallBack: 
            callback function that can get selected object as a param
        deleteCallBack: 
            callback function that can get selected object as a param
    }

    methods:
        1) getSelectedIds() : get an array of selected ids
        2) loadTreeViewOnInsert(rootId) : load treeview items
        3) loadTreeViewOnUpdate(rootId) : load treeview items and checked selected checkboxes
        4) unCheckedAll()
--------------------------------------------------------------------- */
```

For more information please see the source. there is a demo file (index.html)

If you need help, call me :
h.moradof@gmail.com
http://moradof.com

