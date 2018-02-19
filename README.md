Browser-storage adapter
=

just simple browser storage with namespace support. Adapter for localStorage, sessionStorage in browser


##how to use:
 
```
 //bind to local-storage
 var myLocalStorage = JrMakeStorage('prefix', 'local-storage', window.localStorage);
 
 //bind to session-storage
 var mySessionStorage = JrMakeStorage('prefix', 'session-storage', window.sessionStorage);
 
 myLocalStorage('myKey', 'myWord'); - set single key
 myLocalStorage.remove('myKey); - remove single key
 myLocalStorage.clear(); - remove all keys
 myLocalStorage.setPrefix(); - set prefix to this plugin localStorage keys
 myLocalStorage.map(cb, opt) - walk in stored keys
 
 myLocalStorage.on(cb) - bind callback data changes on other tab with current domain
 myLocalStorage.off(cb) - unbind callback

``` 
    event structures and data:

```          
 evData = {
              key: key,
              newValue: newValue,
              type: type
          }
 //type have two values:
 
     myLocalStorage.EVENT_TAB // fires when in current tab value is changed
     myLocalStorage.EVENT_STORAGE // fires when other tab is changed value
          

```
 ... somewhere in far far code ...

```
    var MY_KEY = 'myKey';
    var myFirstVal = myLocalStorage('myKey') // return 'myWord'
    
    myLocalStorage.on(function(evData){
        // fired when data changed
        if (evData.key == MY_KEY) {
            var firedVal = evData.newValue; // return 'myWord'
        }
    }) 

```

 licence: MIT, dudiq 2017
