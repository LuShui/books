//冒泡排序
function () {
    let array = [1,3,2,55,64,23,44,56]
    let len = array.length;

    for(let i = len - 1 ; i > 0 ; i --){
      for(let j = 0 ; j < i ; j ++){
        if(array[j] < array[j + 1]){
          let temp = array[j + 1];
          array[j+1] = array[j];
          array[j] = temp
        }
      }
    }
    console.log(array);
 }



 //直接插入排序
 function () {
    let array = [1,3,2,55,64,23,44,56]
    let len = array.length;

    let i , j , k ;
    for(i = 1 ; i < len ; i ++){
      for(j = i - 1 ; j >= 0 ; j --)
        if(array[j] < array[i])
          break;
      if(j != i - 1){
        let temp = array[i];
        for(k = i - 1; k > j; k --)
          array[k + 1] = array[k]
        array[k+1] = temp
      }
    }
    console.log(array);
  }