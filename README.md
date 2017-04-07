# api documentation for  [node-cmd (v2.0.0)](https://github.com/RIAEvangelist/node-cmd)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-cmd.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-cmd) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-cmd.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-cmd)
#### Simple commandline/terminal interface to allow you to run cli or bash style commands as if you were in the terminal.

[![NPM](https://nodei.co/npm/node-cmd.png?downloads=true)](https://www.npmjs.com/package/node-cmd)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-cmd/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-node-cmd_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-cmd/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-cmd/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-cmd/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Brandon Nozaki Miller"
    },
    "bugs": {
        "url": "https://github.com/RIAEvangelist/node-cmd/issues"
    },
    "dependencies": {},
    "description": "Simple commandline/terminal interface to allow you to run cli or bash style commands as if you were in the terminal.",
    "devDependencies": {},
    "directories": {
        "example": "example"
    },
    "dist": {
        "shasum": "6345655774a3b3f80181b3e52421ba0d23f588f4",
        "tarball": "https://registry.npmjs.org/node-cmd/-/node-cmd-2.0.0.tgz"
    },
    "gitHead": "357b375216e260f0a13f310edf20cceb1392d6ca",
    "homepage": "https://github.com/RIAEvangelist/node-cmd",
    "keywords": [
        "commandline",
        "terminal",
        "cmd",
        "cli",
        "bash",
        "script",
        "node"
    ],
    "license": "DBAD",
    "main": "cmd.js",
    "maintainers": [
        {
            "name": "mayberex",
            "email": "marioxcore1@gmail.com"
        },
        {
            "name": "riaevangelist",
            "email": "brandon@diginow.it"
        }
    ],
    "name": "node-cmd",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/RIAEvangelist/node-cmd.git"
    },
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module node-cmd](#apidoc.module.node-cmd)
1.  [function <span class="apidocSignatureSpan">node-cmd.</span>get (command, callback)](#apidoc.element.node-cmd.get)
1.  [function <span class="apidocSignatureSpan">node-cmd.</span>run (command)](#apidoc.element.node-cmd.run)
1.  object <span class="apidocSignatureSpan">node-cmd.</span>commandline

#### [module node-cmd.commandline](#apidoc.module.node-cmd.commandline)
1.  [function <span class="apidocSignatureSpan">node-cmd.commandline.</span>get (command, callback)](#apidoc.element.node-cmd.commandline.get)
1.  [function <span class="apidocSignatureSpan">node-cmd.commandline.</span>run (command)](#apidoc.element.node-cmd.commandline.run)



# <a name="apidoc.module.node-cmd"></a>[module node-cmd](#apidoc.module.node-cmd)

#### <a name="apidoc.element.node-cmd.get"></a>[function <span class="apidocSignatureSpan">node-cmd.</span>get (command, callback)](#apidoc.element.node-cmd.get)
- description and source-code
```javascript
function getString(command, callback){
    //return refrence to the child process
    return exec(
        command,
        (
            function(){
                return function(err,data,stderr){
                    if(!callback)
                        return;

                    callback(data, err, stderr);
                }
            }
        )(callback)
    );
}
```
- example usage
```shell
...
#Examples
-

'''javascript

var cmd=require('node-cmd');

cmd.get(
    'pwd',
    function(data){
        console.log('the current working dir is : ',data)
    }
);

cmd.run('touch example.created.file');
...
```

#### <a name="apidoc.element.node-cmd.run"></a>[function <span class="apidocSignatureSpan">node-cmd.</span>run (command)](#apidoc.element.node-cmd.run)
- description and source-code
```javascript
function runCommand(command){
    //return refrence to the child process
    return exec(
        command
    );
}
```
- example usage
```shell
...
cmd.get(
    'pwd',
    function(data){
        console.log('the current working dir is : ',data)
    }
);

cmd.run('touch example.created.file');

cmd.get(
    'ls',
    function(data){
        console.log('the current dir contains these files :\n\n',data)
    }
);
...
```



# <a name="apidoc.module.node-cmd.commandline"></a>[module node-cmd.commandline](#apidoc.module.node-cmd.commandline)

#### <a name="apidoc.element.node-cmd.commandline.get"></a>[function <span class="apidocSignatureSpan">node-cmd.commandline.</span>get (command, callback)](#apidoc.element.node-cmd.commandline.get)
- description and source-code
```javascript
function getString(command, callback){
    exec(
        command,
        (
            function(){
                return function(err,data,stderr){
                    callback(data,err,stderr);
                }
            }
        )(callback)
    );
}
```
- example usage
```shell
...
#Examples
-

'''javascript

var cmd=require('node-cmd');

cmd.get(
    'pwd',
    function(data){
        console.log('the current working dir is : ',data)
    }
);

cmd.run('touch example.created.file');
...
```

#### <a name="apidoc.element.node-cmd.commandline.run"></a>[function <span class="apidocSignatureSpan">node-cmd.commandline.</span>run (command)](#apidoc.element.node-cmd.commandline.run)
- description and source-code
```javascript
function runCommand(command){
    exec(
        command
    );
}
```
- example usage
```shell
...
cmd.get(
    'pwd',
    function(data){
        console.log('the current working dir is : ',data)
    }
);

cmd.run('touch example.created.file');

cmd.get(
    'ls',
    function(data){
        console.log('the current dir contains these files :\n\n',data)
    }
);
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
