# Queuecall (Synchronous call)

Stop execution of second function until first function finished or some tasks complete

Example: 

1. Resize image function only after image download finished        
2. Call thirdparty library functions only after library loaded in your application.


Execute second function only after first function finished


#dependencies

jQuery v1.9

#js

queuecall.js - 1kb

queuecall.min.js - (less than a kb)

#usage

    queuecall(function1, function2).startQueue(params for function1);

#Example: 

    function getScript(jspath){
        var _parent = this;
        $.getScript(jspath).done(function() {
            _parent.callnext(true);
        }).fail(function(){ 
            _parent.callnext(false); 
        });
    }

    queuecall(getScript, function(isfileloaded){
        console.log(isfileloaded);
    }).startQueue("module.js");

