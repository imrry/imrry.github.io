### PHPWord设置
* 本`PhpOffice\PhpWord\Settings`类提供了一些选项，这将影响PHPWord的一些属性设置，请参考以下内容：

#### XML Writer兼容性
   
   * 此选项设置`XMLWriter::setIndent`和`XMLWriter::setIndentString`。
   
   * 此选项的默认值为`true`（兼容），这是OpenOffice正确呈现OOXML文档所必需的。
   
   * 在开发期间你可以将此选项设置为`false`使得生成的XML文件更易于阅读。
```php
\PhpOffice\PhpWord\Settings::setCompatibility(false);
```

#### Zip类
* 默认情况下，PHPWord使用[Zip扩展](http://php.net/manual/en/book.zip.php)来处理ZIP压缩存档和其中的文件。如果您的服务器上没有安装Zip扩展，则可以使用[PHPWord](http://www.phpconcept.net/pclzip/)中包含的纯PHP库替代PclZip。
```php
\PhpOffice\PhpWord\Settings::setZipClass(\PhpOffice\PhpWord\Settings::PCLZIP);
```

#### 输出转义
* 编写某些格式的文档，尤其是基于XML的文档，需要正确的输出转义。如果没有它，当您在其中添加“＆”符号，引号和其他字符时，您的文档可能会被破坏。
  
* 转义可以通过两种方式执行：软件开发人员在库外部，内置机制在库内部。默认情况下，禁用内置机制以向后兼容v0.13.0之前的版本。要在PHPWord配置文件中打开set `outputEscapingEnabled`选项，`true`或在运行时使用以下指令：
```php
\PhpOffice\PhpWord\Settings::setOutputEscapingEnabled(true);
```

#### 默认字体
* 默认情况下，每个文本都显示在Arial 10磅中。您可以使用以下两个函数更改默认字体：
```php
$phpWord->setDefaultFontName('Times New Roman');
$phpWord->setDefaultFontSize(12);
```
