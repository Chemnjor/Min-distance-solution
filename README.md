/* Min-distance-solution */
'use strict';

const fs = require('fs');

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'minimumDistances' function below.
 *
 * The function is expected to return an INTEGER.
 * The function accepts INTEGER_ARRAY a as parameter.
 */

function minimumDistances(a) {
    // Write your code here
    let distance = [];
    for(let n = 0; n<a.length; n++){
        if(a.indexOf(a[n]) !== a.lastIndexOf(a[n])){
        let minDistance = a.lastIndexOf(a[n]) - a.indexOf(a[n]);
            distance.push(minDistance);
        }
    }
  
    if(distance.length === 0){
        return -1;
    }else{
        distance.sort(function(a, b) {
          return a - b;
        });
    
        return distance[0];
    }


}

function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH);

    const n = parseInt(readLine().trim(), 10);

    const a = readLine().replace(/\s+$/g, '').split(' ').map(aTemp => parseInt(aTemp, 10));

    const result = minimumDistances(a);

    ws.write(result + '\n');

    ws.end();
}
