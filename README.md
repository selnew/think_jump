# think_jump
thinkphp6 跳转支持：可使用success、error、redirect、result方法

## 安装
~~~php
composer require selnew/think-jump
~~~

## 配置
~~~php
// 安装之后会在config目录里生成jump.php配置文件
return[
    // 默认跳转页面对应的模板文件
    'dispatch_success_tmpl' => app()->getRootPath().'/vendor/selnew/think-jump/src/tpl/dispatch_jump.tpl',
    'dispatch_error_tmpl'   => app()->getRootPath().'/vendor/selnew/think-jump/src/tpl/dispatch_jump.tpl',
];
~~~

## 用法示例

使用 use selnew\think\Jump;

在所需控制器内引用该扩展即可：
~~~php
<?php
namespace app\controller;

use selnew\think\Jump;

class Test
{
    public function index()
    {
        // return $this->error('error');
        return $this->success('success:welcome', 'index/index');
        // return $this->redirect('/admin/index/index');
        // return $this->result(['username' => 'mirze', 'email' => 'mirzeAdv@163.com']);
    }
}
~~~

### 使用参考：
~~~
return $this->success('登录成功', 'index/index');
return $this->success($msg = '登录成功', $url = 'index/index', $data = [],  $wait = 3,  $header = []);

return $this->error('登录失败');
return $this->error('登录失败','login/index');
return $this->error($msg = '登录失败',$url = 'login/index', $data = [], $wait = 3,  $header = []);

return $this->redirect('/admin/index/index');
return $this->redirect(url('index/index', ['name' => 'mirze']));
return $this->redirect('https://www.baidu.com');
return $this->redirect($url= '/admin/index/index', $code = 302, $with = ['data' => 'welcome']);

return $this->result(['username' => 'mirze', 'email' => 'mirzeAdv@163.com']);
return $this->result($data=['username' => 'mirze', 'email' => 'mirzeAdv@163.com'], $code = 0, $msg = '', $type = '',  $header = []);

~~~