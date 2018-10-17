## Runtime complexity

Describes the performance of an algorithm

How much more processing power/time is required to run your algorithm if we double the inputs?

  * String Reverse
  
    function reverse(str) {
       let reversed = '';
       for (let character of str){
         reversed = character + reversed;
         debugger;
       }
       return reversed;
    }
  
  ex) abc -> cba
  
  Each additional character = 1 step through 1 loop
  
  This would be 'N' or 'linear' runtime.
  
  
  * Steps Algorithm
  
    function steps(n) {
      for (let row =0; row <n; row++){
        let stair='';

        for(let column =0; column < n; column++){
          if (column <= row){
            stair += '#';
          }else {
            stair += ' ';
          }
        }
        console.log(stair);
      }
    }
  
  ex) n= 2 -> had to do 4 things, n=3 -> had to do 9 things, n=4 -> had to do 16 things
    #
    ##
    ###
    ####
    
  As 'n' increase by one, we had to do way, way more stuff, or(n*n) things total
  
  This would be N^2, or quadratic runtime
  
  
    Constant Time : 1 -> No matter how many elements we're working with, the algorithm/operation/whatever will always take the same amount of time

    Logarithmic Time: log(n) -> You have this if doubling the number of elements you are iterating over doesn't double the amount of work. Always assume that searching operations ar log(n)
    
    Linear Time : n -> iterating through all elements in a collection of data. if you see a for loop spanning from '0' to 'array.length', you probably have 'n', or linear runtime
    
    Quasilinear Time: n * log(n) -> You have this if doubling the number of elements you are iterating over doesn't double the amount of work. Always assume that any sorting operation is n*log(n)
    
    Quadratic Time: n^2 -> Every element in a collection has to be compared to every other element. "The handshake problem"
    
    Exponential Time: 2^n -> If you add a *single* element to a collection, the processing power required doubles
    

Big 'O' Notation

    O(n) -> Linear
    O(1) -> Constant
    O(n^2) -> Quadratic

  * Identifying  Runtime Complexity
  
  
        Iterating with a simple for loop through a single collection -> Probably O(n)

        Iterating through half a collection? -> Still O(n). There are no constants in runtime

        Iterating through two *different* collections with separate for loops? -> O(n+m)

        Two nested for loops iterating over the same collection? -> O(n^2)

        Two nested for loops iterating over different collection? -> O(n*m)

        Sorting? -> O(n*log(n))

        Searching a sorted array? -> O(log(n))


Space Complexity is a thing too

  How much more memory is required by doubling the problem set?
    


Memoization
 
 Store the arguments of each function call along with the result. If the function is called again with the same arguments, return the precomputed result, rather than running the function again.
 
    function fib(n) {
      if (n < 2){
        return n;
      }

      return fib(n-1) + fib(n-2);
    }

    module.exports = fib;
 
  O(2^n)
  
Slow Fib Function -> Memoizer -> Fast, Memoized Fib Function


    function memoize(fn) {
       const cache ={};

       return function(...args){
         if (cache[args]) {
           return cache[args];
         }
         const result = fn.apply(this,args);
         cache[args] = result;

         return result;
       }

     }

     function slowFib(n) {
       if (n < 2){
         return n;
       }

       return fib(n-1) + fib(n-2);
     }

     const fib = memoize(slowFib);

     module.exports = fib;

 
