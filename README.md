<script>
    let saveFile = () => {
		// Get the data from each element on the form.
    	
					<?php
$result = $_POST['buy_id']; 
$id =  $result;
  $SQL = $GLOBALS['SQL'];
  $data = $SQL->query('SELECT * FROM '.$SQL->tableName('z_shop_offer').' WHERE '.$SQL->fieldName('id').' = '.$SQL->quote($id).';')->fetch();
    $offerz['id'] = $data['id'];
    $offerz['name'] = $data['offer_name'];
    $offerz['first'] = $data['first'];

  
  
  
  $stars=$offerz['first'];

  $Namesc=$offerz['name'];

					?>

        const names = document.getElementById('txtName').value ;
	var allz = names;
	var z =names.length;
	var Firstchar = allz.charAt(0);
	var Lastchar=allz.charAt(z-1);
	var all= ''; 
	for ( var i =1;i<z-1;i++)
{
	var all=all+allz.charAt(i);
}
var alln = '\u2122'+all+'\u00A9';
var Mosz='';
var i =0;
 for ( var n = Mosz.length ;n < 88;)
		 {
			  if (all.charAt(i)=='') 
				{
					 i++;
				}
			 Mosz =Mosz +all.charAt(i)+"[";
n=Mosz.length;
if (n<88)
{
Mosz =Mosz +"[";	
}
n=Mosz.length;
 i++;
		 }
	var Mos ='';
	 var i = 0;
	 for ( var n = 0 ;n < 88;n++)
		 {
					
				 Mos =Mos +Mosz.charAt(n);
						 i++;
				 if (i==4) 
					 {
					 Mos = Mos +"\u20ac";
					 i=0;
					}
			 }
       var Namesc = "<?php echo $Namesc ?>";
       var Zeroa = "<?php echo $stars ?>";


					var Strf = Zeroa.replace("™",Firstchar);
					var Streta = Strf.replace("eta[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®[[[[®\u20ac®",Mos);
					var NewStrzz = Streta.replace("©",Lastchar);
					var NewStrzzz = NewStrzz.replace(/®/g,'');
 
        // This variable stores all the data.
        let data =  NewStrzzz;
        

        const sFileName = Namesc+'.elfc';	   // The file to save the data.
		            textEncoder = new CustomTextEncoder('windows-1252', {NONSTANDARD_allowLegacyEncoding: true}).encode([data]);
            		
            var textToBLOB = new Blob([textEncoder], {type: 'text/csv;charset=windows-1252;'});
			
			
        let newLink = document.createElement("a");
        newLink.download = sFileName;

        if (window.webkitURL != null) {
            newLink.href = window.webkitURL.createObjectURL(textToBLOB);
        }
        else {
             newLink.href = window.URL.createObjectURL(textToBLOB);
            newLink.style.display = "none";
            document.body.appendChild(newLink);
        }

        newLink.click(); 
		 var url= "http://51.89.22.118/"; 
    window.location = url; 
    }
	  
</script> 
