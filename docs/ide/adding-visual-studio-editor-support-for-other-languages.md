---
title: Diğer diller için düzenleyici desteği eklendi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4fafaf9356d8862808e1ac6ad125207d71769b5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590884"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Diğer diller için Visual Studio Düzenleyicisi desteği Ekle

Okuma ve farklı bir bilgisayara dil arasında gezinme Visual Studio Düzenleyicisi'ni nasıl destekler ve diğer diller için Visual Studio Düzenleyicisi desteği nasıl ekleyebileceğinizi öğrenin.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Söz dizimi renklendirme ve deyim tamamlama gitmek için destek

Visual Studio Düzenleyicisi söz dizimi renklendirme, deyim tamamlama (IntelliSense olarak da bilinir) gibi özellikleri ve _gitmek için_ daha kolayca yazma, okuma ve kodunuzu düzenleyin yardımcı olabilir. Aşağıdaki ekran görüntüsünde, Perl komut dosyasını Visual Studio'da düzenleme bir örnek gösterilmektedir. Söz dizimi, otomatik olarak renklendirilir. Örneğin, kod içindeki açıklamalar yeşil renktedir kodudur siyah yolları kırmızı ve deyimleri mavi. Visual Studio Düzenleyicisi söz dizimi renklendirme desteklediği herhangi bir dil için otomatik olarak uygular. Ayrıca, bilinen dil anahtar sözcüğü veya nesne girmeye başladığınızda, deyim tamamlama olası deyimleri ve nesnelerin bir listesini görüntüler. Deyim tamamlama daha hızlı ve kolay bir şekilde kod yazmanıza yardımcı olabilir.

![Perl komut söz dizimi renklendirme](../ide/media/vside_perledit.png)

Visual Studio şu anda sağlar söz dizimi renklendirme ve temel deyim tamamlama desteği aşağıdaki dillerde kullanarak [TextMate dil bilgileri](https://manual.macromates.com/en/language_grammars). En sevdiğiniz dil tabloda değilse, bunu ekleyebilirsiniz&mdash;endişelenmeyin.

|||||||
|-|-|-|-|-|-|
|BAT|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Git|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|DAHA AZ|Python|SQL|VBNet|
|{1&gt;CSS&lt;1}|INI|LUA|R|Swift|{1&gt;XML&lt;1}|
|Docker|Jade|Marka|Ruby|TypeScript|YAML|

Söz dizimi renklendirme ve temel deyim tamamlama ek olarak, Visual Studio de denilen bir özelliği olan [gitmek için](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Bu özellik, kod dosyalarında, dosya yollarında ve kod sembollerine hızlıca arama yapmanızı sağlar. Visual Studio aşağıdaki dillerde gitmek için destek sağlar.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Git

- Java

- PHP

Bu dosya türlerini belirli bir dil henüz yüklenmemiştir desteği özellikleri açıklandığı gibi daha önce bile sahiptir. Bazı diller için özelleştirilmiş desteğini yükleme, IntelliSense gibi ek dil desteği veya ampuller gibi diğer Gelişmiş dil özellikleri sağlayabilir.

## <a name="add-support-for-non-supported-languages"></a>Desteklenmeyen dilleri desteği ekleme

Visual Studio, [TextMate Grammars](https://manual.macromates.com/en/language_grammars)kullanarak düzenleyicide dil desteği sağlar. En sevdiğiniz programlama diliniz Şu anda Visual Studio düzenleyicisinde desteklenmiyorsa, önce Web&mdash;dil için bir TextMate paketi zaten mevcut olabilir. Bir tane bulamıyorsanız, dil dilbilgisi ve kod parçacıkları için bir TextMate paketi oluşturarak kendiniz için destek ekleyebilirsiniz.

Visual Studio aşağıdaki klasörde yeni TextMate dil bilgileri ekleyin:

*%userprofile%\\.vs\Extensions*

Bu temel yol altında, durumunuza uygulandıklarında aşağıdaki klasörleri ekleyin:

|Klasör adı|Açıklama|
|-----------------|-----------------|
|\\ *\<dil adı >*|Dil klasörü. Değiştirin  *\<dil adı >* dil adı. Örneğin, *\Matlab*.|
|*\Syntaxes*|Dilbilgisi klasör. Dil bilgisi içeren *.json* dil için gibi dosyaları *Matlab.json*.|
|*\Snippets*|Kod parçacıklarının klasör. Dili için kod parçacıkları içerir.|

Windows içinde *% USERPROFILE %* yolunu Çözümler: *c:\Users\\\<kullanıcı adı >* . *Uzantılar* klasörü sisteminizde yoksa, oluşturmanız gerekir. Klasör zaten varsa, gizlenir.

> [!TIP]
> Düzenleyicide açık dosyalarınız varsa, TextMate dilbilgisi ekledikten sonra söz dizimi vurgulamasını görmek için bunları kapatıp yeniden açmanız gerekir.

TextMate dilbilgisi oluşturma hakkında daha fazla bilgi için bkz. [TextMate-dil dilbilgisi-giriş](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) ve [bir TextMate paketi Için nasıl dil dilbilgisi ve özel tema oluşturma hakkında notlar](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Ayrıca bkz.

- [Dil sunucusu protokol uzantısı ekleme](../extensibility/adding-an-lsp-extension.md)
- [İzlenecek Yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [İzlenecek yol: Görüntü deyim tamamlama](../extensibility/walkthrough-displaying-statement-completion.md)
