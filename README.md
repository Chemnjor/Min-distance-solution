/* Min-distance-solution */


function minimumDistances(a) {
  
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

