### 一般用法

```php
<?php
    require_once 'bootstrap.php';
    
    //创建文档
    $phpWord = new \PhpOffice\PhpWord\PhpWord();
    
    //添加节
    $section = $phpWord->addSection();
    
    //向节内添加文本
    $section->addText('从昨天开始，为今天而活。希望不要停止思考。');
    
    $section->addText('"Great achievement is usually born of great sacrifice, ',
       [
        'name' => 'Tahoma',
        'size' => 10
       ]);
    
    //设置字体样式
    $fontStyleName = 'oneUserDefinedStyle'
    $phpWord->addFontStyle(
        $fontStyleName,
        ['name' => 'Tahoma', 'size' => 10, 'color' => '1B2232', 'bold' => true)]
    );
    
    $section->addText(
        '"The greatest accomplishment is not in never falling, '
            . 'but in rising again after you fall." '
            . '(Vince Lombardi)',
        $fontStyleName
    );
    
    //为单独的内容块设置样式
    $fontStyle = new \PhpOffice\PhpWord\Style\Font();
    $fontStyle->setBold(true);
    $fontStyle->setName('Tahoma');
    $fontStyle->setSize(13);
    $myTextElement = $section->addText('"Believe you can and you\'re halfway there." (Theodor Roosevelt)');
    $myTextElement->setFontStyle($fontStyle);
    
    //保存为OOXML格式文档
    $objWriter = \PhpOffice\PhpWord\IOFactory::createWriter($phpWord, 'Word2007');
    $objWriter->save('helloWorld.docx');
    
    //保存为ODF格式文档
    $objWriter = \PhpOffice\PhpWord\IOFactory::createWriter($phpWord, 'ODText');
    $objWriter->save('helloWorld.odt');
    
    //保存为HTML格式文档
    $objWriter = \PhpOffice\PhpWord\IOFactory::createWriter($phpWord, 'HTML');
    $objWriter->save('helloWorld.html');
    
    //这里跳过RTF和PDF的案例，因为他们不是基于XML进行渲染的。
```
