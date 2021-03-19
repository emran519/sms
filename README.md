# 【集成腾讯云短信，阿里云短信，邮件发送类】

# 一、调用方法

## 1.发送邮件

```php
use Sms; //引入

//实例化
$sms = new Sms();

//邮件发送
/**
     * SMTP邮件发送基本配置
     *
     * @param string $smtp_url  SMTP地址
     * @param int    $smtp_port SMTP端口 465或25
     * @param string $mail_name 发件邮箱账号
     * @param string $mail_pass 发件邮箱密码
     * @param string $alias     别名(可选)
     * @return bool  
     */
$sms->email('SMTP地址','SMTP端口'，'发件邮箱账号','发件邮箱密码','别名');
/**
     * SMTP邮件发送
     *
     * @param string $email 收件邮箱
     * @param string $title 邮件标题
     * @param string $text  邮件内容
     */
$res = $sms->emailParam('收件邮箱','邮件标题','邮件内容');
if($res === true){
    return '发送成功';
}else{
    return '发送失败';
}

```

## 2.发送腾讯云短信
```php
use Sms; //引入

//实例化
$sms = new Sms();

//邮件腾讯云短信
/**
     * 腾讯云短信基本配置
     *
     * @param string $appId  腾讯云短信AppId
     * @param string $appKey 腾讯云短信AppKey
     */
$sms->qCloudSms('腾讯云短信AppId', '腾讯云短信AppKey');
/**
     * 指定模板单发
     *
     * @param  int    $nationCode  国家码，如 86 为中国
     * @param  string $phoneNumber 不带国家码的手机号
     * @param  int    $tempId      模板 id
     * @param  string $param       模板参数列表，如模板 {1}...{2}...{3}，那么需要带三个参数
     * @param  string $sign        签名，如果填空串，系统会使用默认签名
     * @return bool                
     */
//验证码
$code = rand(111111,999999);//验证码
$res = $sms->qCloudSmsParam(86, '不带国家码的手机号', '模板ID', $code, '签名');

if($res === true){
    return '发送成功';
}else{
    return '发送失败';
}

```

## 2.发送阿里云短信
```php
use Sms; //引入

//实例化
$sms = new Sms();

//邮件阿里云短信

/**
     * 阿里云短信基本配置
     *
     * @param string $accessKeyId     AccessKeyId
     * @param string $accessKeySecret AccessKeySecret
     * @param string $signName        签名内容
     * @param string $templateCode    短信模板CODE
     */
$sms->aliSms('AccessKeyId', 'AccessKeySecret', '签名内容', '短信模板CODE');
 /**
     * 阿里云短信发送
     *
     * @param string $phone 短信接受手机号码
     * @param string $param 数字验证码
     * @return bool
     */
//验证码
$code = rand(111111,999999);//验证码
$res = $sms->aliSmsParam('短信接受手机号码', $code);

if($res === true){
    return '发送成功';
}else{
    return '发送失败';
}

```
