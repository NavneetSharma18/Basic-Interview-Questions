### Sort Array ASC => swap element

-$a = [10,90,20,70,50,20];
-$n = count($a);

-for($i=0;$i<$n;$i++){
    -for($j=$i+1;$j<$n;$j++){
     -if($a[$i] > $a[$j]){
         -$temp = $a[$i];
         -$a[$i] = $a[$j];
         -$a[$j] = $temp;
         
     -}
    -}
-}
-print_r($a);
