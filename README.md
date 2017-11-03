# GithubOverlayUtility
Overlay Tools (ex: delete branches etc...)

## 1. Delete branches on github:

1. add chrome extension `cjs` (add jQuery)
2. add the following code
3. goto /branches

```javascript

// branches that you don't want to delete
var white_list = ["master", "develop", "devops"]
   
$('body').prepend('<div style="position:fixed;z-index:9999;float:left;" class="back-to-top">'+
                  ' <button style="background:orange;" id="remove_branches">'+
                  '   Remove Branches'+
                  ' </button>'+
                  '</div>');

$('#remove_branches').click(remove_branches);
        
function remove_branches(){
    $('div.branch-summary').each(function(index){
        var _this = $(this);
        setTimeout(function(){
            var branch_name = _this.data('branch-name').toLowerCase();
            if(!white_list.includes(branch_name)){
                console.log(branch_name);
                _this.find('.branch-delete').eq(0).click();
            }  
        }, index*300)
    }) 
}

```
