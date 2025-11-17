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

?>
