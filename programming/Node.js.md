Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-05-04T10:55:06+08:00

====== Node.js ======

async.waterfall([
    function(callback){
        callback(null, 'one', 'two');
    },
    function(arg1, arg2, callback){
        callback(null, 'three');
    },
    function(arg1, callback){
        // arg1 now equals 'three'
        callback(null, 'done');
    }
], function (err, result) {
   // result now equals 'done'    
});

async.auto({
    get_data: function(callback){
        // async code to get some data
    },
    make_folder: function(callback){
        // async code to create a directory to store a file in
        // this is run at the same time as getting the data
    },
    write_file: ['get_data', 'make_folder', function(callback){
        // once there is some data and the directory exists,
        // write the data to a file in the directory
        callback(null, filename);
    }],
    email_link: ['write_file', function(callback, results){
        // once the file is written let's email a link to it...
        // results.write_file contains the filename returned by write_file.
    }]
});


var async = require('async');

var arr = ['1','2'];
async.map(arr, getInfo, function (e, r) {
  console.log(r);
});

function getInfo(name, callback) {
  setTimeout(function() {
    callback(null, name + 'new');
  }, 1000);
}
