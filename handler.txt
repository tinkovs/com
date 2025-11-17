<?php

$url = "https://marketplay.info/api/request";

$amount = htmlspecialchars($_POST['amount'] ?? '');
$phone = htmlspecialchars($_POST['phone'] ?? '');
$email = htmlspecialchars($_POST['email'] ?? '');
$name = htmlspecialchars($_POST['name'] ?? '');
$story = htmlspecialchars($_POST['story'] ?? '');
$sep = '\r\n';

$merchant_order_id = rand(13577888, 99273812);
$use_card_payment = "RUB";
$api_key = "e71366079d95b04228fc6482c503a983b99da2e7b17dd6c56780074d0f7e63a2";
$success_url = "https://bvmy.ru/success.html";
$fail_url = "https://bvmy.ru/fail.html";
$notice_url = "https://bvmy.ru";

$curl = curl_init($url);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

$headers = array(
   "Content-Type: application/x-www-form-urlencoded",
);
curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);

$data = "amount=$amount&merchant_order_id=$merchant_order_id&use_card_payment=$use_card_payment&api_key=$api_key&success_url=$success_url&fail_url=$fail_url&notice_url=$notice_url";

curl_setopt($curl, CURLOPT_POSTFIELDS, $data);

//for debug only!
curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);

$resp = curl_exec($curl);
curl_close($curl);
var_dump($resp);

$data1 = "amount=$amount&merchant_order_id=$merchant_order_id&use_card_payment=$use_card_payment&api_key=$api_key&success_url=$success_url&fail_url=$fail_url&notice_url=$notice_url&phone=$phone&email=$email&name=$name&story=$story";
$file = 'people.txt';
file_put_contents($file, $data1 . PHP_EOL, FILE_APPEND | LOCK_EX);

?>
