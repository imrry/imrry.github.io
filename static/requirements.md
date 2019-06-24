### 安装/配置
#### 1.要求

* 必须的
    * PHP 5.3.3+
    * XML Parser 扩展
    * Zend\Escaper 组件
    * Zend\Stdlib 组件
    * Zend\Validator 组件

* 可选的
    * Zib扩展
    * GD扩展
    * XML Writer扩展
    * XLS扩展
    * DomPDF库扩展
    
#### 2.安装
   * 安装方式一：通过Composer进行安装，安装前需要依据上方的要求在你的环境中安装并启用必须的组件和扩展。
   
    在你的composer.json文件中加入以下内容：
        ```
        {
            "require": {
                "phpoffice/phpword": "v0.14.*"
			}
         }
        ```
        如果您是开发人员，或者如果您想帮助我们进行测试，那么请为开发人员获取最新的分支。注意：所有贡献必须针对开发者分支。
        ```
        {
            "require": {
               "phpoffice/phpword": "dev-develop"
            }
        }
        ```

* 安装方式二：前往[PHPWord](https://github.com/imrry/PHPOffice)下载源码或者通过以下方式下拉项目到本地进行安装。
```php
git clone https://github.com/imrry/PHPOffice.git
```

#### 3.使用
* 启动调试环境

    进入你要启动环境的根目录，在命令行中输入以下指令，可在本地启动一个测试环境。
    ```
    //进入项目根目录
    cd PHPOffice/Web
    //使用PHP启动本地服务，以供web进行访问，0.0.0.0代表监听所有来源地址，:8080代表监听端口
    php -S 0.0.0.0:8080
    ``` 

* 访问调试环境

    浏览器输入 http://localhost:8080
