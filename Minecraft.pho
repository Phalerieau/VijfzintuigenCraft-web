<?php
//variables
/*********************************** Variables ***********************************/
/**/  $checkpass = "PutYourPasswordHere";
/**/  $hashAlgorithm = "sha512";
/*********************************************************************************/
$receivedHash = $_POST['authKey'];
$args = $_POST["args"]; //each argument is stored in an array called "args"
if($_POST['isCompressed'] == "true" && isset($_FILES['jsonData']['tmp_name'])){
    $json = json_decode(gzdecode(file_get_contents($_FILES['jsonData']['tmp_name'])));
}else{
    $json = json_decode($_POST["jsonData"]);
}
if($json == ''){
    print('/Output/PrintToConsole:Error:Failed to retrieve JSON data!;');
    //If compressed is enabled PHP probably refused the binary data: check upload_max_filesize, post_max_size and file_uploads
}
/*********************************************************************************/

$invoker = $json->{'Invoker'}->{'Name'};

if($receivedHash != "" && $args[0] != "")
{
    if($receivedHash == hash($hashAlgorithm, $checkpass))
    {
        //Begin your code here.
        if($args[0] == "attractie"){
            if($invoker == '@Console'){
                   
            }
            else {
                if($args[2] == "open"){
                        $open = 1;
                        attractie();
                } 
                elseif ($args[2] == "dicht") {
                        $open = 0;
                        attractie();
                }
                else {
                    print("/Output/PrintToPlayer:&7Incorrect command, try again."); 
                }
                function attractie(){
                    ?>
                        <script src='https://cdn.firebase.com/js/client/2.2.1/firebase.js'></script>
                        <script>
                            var myDataRef = new Firebase('https://brilliant-fire-2372.firebaseio.com/');
                            myDataRef.push({attractie: "<?php echo $args[1] ?>", open: "<?php echo $open ?>"});
                        </script>
                    <?php
                    print("/Output/PrintToPlayer:&7De &a".$args[1]." &7is ".$args[2]."."); 
                }
                
            }
        }
        else
        {
            print('/Output/PrintToPlayer:Websend: Unknown command.;');
        }
        //Stop editing here.
    }
    else
    {
        print('/Output/PrintToConsole:Authorization Failed;');
    }
}
else
{
    print("/Output/PrintToConsole:No (enough) data provided.;");
}
?>
