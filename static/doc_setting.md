### 文档设置
* 可以使用设置生成的文档的设置 `$phpWord->getSettings()`。

#### 放大设置
* 默认缩放值为100％。这可以更改为另一个百分比。
```php
$phpWord->getSettings()->setZoom(75);
```
或者预定义值`fullPage`，`bestFit`，`textFit`。
```php
$phpWord->getSettings()->setZoom(Zoom::BEST_FIT);
```

#### 双页边距
* 使用双页边距为双面文档（如书籍或杂志）设置对开页面。
```php
$phpWord->getSettings()->setMirrorMargins(true);
```

#### 拼写和语法检查
* 默认情况下，只要打开word文档，就会显示拼写和语法错误。对于大文档，这可能会减慢文档的打开速度。您可以隐藏拼写和/或语法错误：
```php
$phpWord->getSettings()->setHideGrammaticalErrors(true);
$phpWord->getSettings()->setHideSpellingErrors(true);
```

* 您还可以指定拼写和语法检查的状态，标记拼写或语法，因为脏将在打开文档时强制重新检查。
```php
$proofState = new ProofState();
$proofState->setGrammar(ProofState::CLEAN);
$proofState->setSpelling(ProofState::DIRTY);
$phpWord->getSettings()->setProofState(proofState);
```

#### 跟踪修订
可以使用激活跟踪更改`setTrackRevisions`，您可以进一步指定。
* 不使用移动语法，而是移动的项目将被视为在一个地方删除并添加到另一个地方。
* 不跟踪格式修订。
```php
$phpWord->getSettings()->setTrackRevisions(true);
$phpWord->getSettings()->setDoNotTrackMoves(true);
$phpWord->getSettings()->setDoNotTrackFormatting(true);
```

#### 十进制符号
* 表示小数的默认符号是`.`(英文)。在法语中，您可能希望将其更改为`,`等符号。
```php
$phpWord->getSettings()->setDecimalSymbol(',');
```
#### 文件语言
* 可以使用以下内容更改文档的默认语言。
```php
$phpWord->getSettings()->setThemeFontLang(new Language(Language::FR_BE));
```
`Language`有3个参数，一个用于拉丁语言，一个用于东亚语言，一个用于复杂（双向）语言。`PhpOffice\PhpWord\ComplexType\Language`类中提供了几种语言代码，但可以使用任何有效的代码/ ID。

* 如果您要生成RTF文档，则需要以不同方式设置语言。
```php
$lang = new Language();
$lang->setLangId(Language::EN_GB_ID);
$phpWord->getSettings()->setThemeFontLang($lang);
```

#### 文件属性信息
* 您可以设置文档信息，例如标题，创建者和公司名称。使用以下功能：
```php
$properties = $phpWord->getDocInfo();
$properties->setCreator('My name');
$properties->setCompany('My factory');
$properties->setTitle('My title');
$properties->setDescription('My description');
$properties->setCategory('My category');
$properties->setLastModifiedBy('My name');
$properties->setCreated(mktime(0, 0, 0, 3, 12, 2014));
$properties->setModified(mktime(0, 0, 0, 3, 14, 2014));
$properties->setSubject('My subject');
$properties->setKeywords('my, key, word');
```

#### 测量单位
* Open Office XML中的基本长度单位是twip。缇意味着“英寸点的第二十”，即1缇= 1/1440英寸。
* 您可以使用PHPWord辅助函数将英寸，厘米或点转换为twip。
```
// 设置段后6twip单位的间距
$phpWord->addParagraphStyle('My Style', array(
    'spaceAfter' => \PhpOffice\PhpWord\Shared\Converter::pointToTwip(6))
);
$section = $phpWord->addSection();
$sectionStyle = $section->getStyle();
// 0.5英寸左边距
$sectionStyle->setMarginLeft(\PhpOffice\PhpWord\Shared\Converter::inchToTwip(.5));
// 2厘米右边距
$sectionStyle->setMarginRight(\PhpOffice\PhpWord\Shared\Converter::cmToTwip(2));
```

#### 文件保护
* 文档（或其中的一部分）可以受密码保护。
```php
$documentProtection = $phpWord->getSettings()->getDocumentProtection();
$documentProtection->setEditing(DocProtect::READ_ONLY);
$documentProtection->setPassword('myPassword');
```

#### 自动更新目录
* 要强制更新文档中存在的字段，请将`updateFields`设置为`true`。
```php
$phpWord->getSettings()->setUpdateFields(true);
```

#### 连字
* 连字符描述了用连字符打破单词的过程。有几种控制连字符的选项。

#### 自动连字
* 自动连接文本设置`autoHyphenation`为`true`。
```php
$phpWord->getSettings()->setAutoHyphenation(true);
```

#### 连字区
* 连字符区域（以twip为单位）是在应用连字符之前允许的空白量。连字区越小，连字越多。或者换句话说，连字区域越宽，连词越少。
```php
$phpWord->getSettings()->setHyphenationZone(\PhpOffice\PhpWord\Shared\Converter::cmToTwip(1));
```

#### 连字帽
* 要控制是否所有大写字母的单词都应使用连字符，请使用doNotHyphenateCaps选项。
```php
$phpWord->getSettings()->setDoNotHyphenateCaps(true);
```
