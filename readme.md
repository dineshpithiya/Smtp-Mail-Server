```
<?php 
require 'PHPMailer-master/PHPMailerAutoload.php';
require 'PHPMailer-master/class.phpmailer.php';

function send_mail_admin($to,$emailSubject, $Message,$cc) 
{
		$mail = new PHPMailer(true);
        $mail->IsSMTP();
        //$mail->SMTPDebug = 2;
        $mail->SMTPAuth = true;
        $mail->Host = "host-name";
        $mail->Port = 587;
        $mail->CharSet = 'UTF-8';
        $mail->ContentType = 'text/html';
        $mail->Username = "username";
        $mail->Password = "password";
        //$mail->SingleTo = true;
        $mail->SMTPSecure = 'tls';
        $mail->From = 'dinesh@domain.com';
        $mail->FromName = 'Dinesh pithiya';
        $mail->addReplyTo('dinesh@domain.com', 'Dinesh pithiya');
        $mail->Subject = $emailSubject;
        $mail->Body = $Message;
        $mail->IsHTML(true);
        
        //$bccarray = array('chandani@moontechnolabs.com','moon1@moontechnolabs.com','jayanti.katariya@moontechnolabs.com');
        //$bccarray = array('chandani@moontechnolabs.com');
        
        /*for($i=0; $i<count($bccarray); $i++)
        {
            $mail->addBCC($bccarray[$i]);
        }*/
        if(!empty($cc)){
            $mail->AddCC($cc);
        }
        for($i=0; $i<count($to); $i++)
        {
            $mail->AddAddress($to[$i]);
        }
        //$mail->AddAddress($to);
       
        if ($mail->Send()) {
            $mail->ClearAllRecipients(); // remove previous address
            return true;
        } else {
            $mail->ClearAllRecipients(); // remove previous address
            return true;
        }
    }
?>
```