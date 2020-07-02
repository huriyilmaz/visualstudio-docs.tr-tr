---
title: Diğer diller için düzenleyici desteği ekle
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
ms.openlocfilehash: 247567030d47a55b29a3fca901e12948ddd85916
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533763"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Diğer diller için Visual Studio Düzenleyicisi desteği ekleme

Visual Studio düzenleyicisinin farklı bilgisayar dillerini okumayı ve gezinmeyi nasıl desteklediğini ve diğer diller için Visual Studio Düzenleyicisi desteğini nasıl ekleyeceğinizi öğrenin.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Sözdizimi renklendirme, ekstre tamamlama ve desteğe gitme

Visual Studio düzenleyicisinin sözdizimi renklendirme, ifade tamamlama (IntelliSense olarak da bilinir) gibi özellikler ve ' a _Git_ , kodunuzu daha kolay bir şekilde yazmanıza, okumanıza ve düzenlemenize yardımcı olabilir. Aşağıdaki ekran görüntüsünde, Visual Studio 'da bir perl betiğini düzenlemeyle bir örnek gösterilmektedir. Sözdizimi otomatik olarak renklendirilmiştir. Örneğin, koddaki açıklamalar yeşil, kod siyah, yollar kırmızı ve deyimler mavi renktedir. Visual Studio Düzenleyicisi, desteklediği dile otomatik olarak sözdizimi renklendirme uygular. Ayrıca, bilinen bir dil anahtar sözcüğünü veya nesnesini girmeye başladığınızda, deyim tamamlama olası deyimler ve nesnelerin bir listesini görüntüler. Deyimin tamamlanması daha hızlı ve kolay bir şekilde kod yazmanıza yardımcı olabilir.

![Perl betikte sözdizimi renklendirme](../ide/media/vside_perledit.png)

Visual Studio şu anda [TextMate Grammars](https://manual.macromates.com/en/language_grammars)kullanarak aşağıdaki diller için sözdizimi renklendirme ve temel ifade tamamlama desteği sunmaktadır. En sevdiğiniz dil tabloda değilse, bunu ekleyebileceğiniz kaygılanmayın &mdash; .


- Dosyasýný
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Başlayın
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- BÜYÜKTÜR
- Python
- SQL
- VBNet
- CSS
- INI
- ISTEMCIYI
- R
- Swift
- XML
- Docker
- Jade
- Marka
- Ruby
- TypeScript
- YAML

Visual Studio, sözdizimi renklendirme ve temel deyimin tamamlanmasına ek olarak [şuraya git](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/)adlı bir özelliğe de sahiptir. Bu özellik, kod dosyalarında, dosya yollarında ve kod sembollerine hızlıca arama yapmanızı sağlar. Visual Studio aşağıdaki diller için desteğe git sağlar.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Başlayın

- Java

- PHP

Bu dosya türlerinin tümünde, belirli bir dil için destek henüz yüklenmemiş olsa bile daha önce açıklanan özellikler vardır. Bazı diller için özel destek yüklemek, IntelliSense veya Light bulbs gibi diğer gelişmiş dil özellikleri gibi ek dil desteği sağlayabilir.

## <a name="add-support-for-non-supported-languages"></a>Desteklenmeyen diller için destek ekleme

Visual Studio, [TextMate Grammars](https://manual.macromates.com/en/language_grammars)kullanarak düzenleyicide dil desteği sağlar. En sevdiğiniz programlama diliniz Visual Studio düzenleyicisinde henüz desteklenmiyorsa, Web 'de &mdash; dil için bir TextMate paketi zaten mevcut olabilir. Bir tane bulamıyorsanız, dil dilbilgisi ve kod parçacıkları için bir TextMate paketi oluşturarak kendiniz için destek ekleyebilirsiniz.

Aşağıdaki klasöre Visual Studio için yeni bir TextMate dilbilgisi ekleyin:

*% userprofile% \\ . Vs\extensions*

Bu temel yol altında, durumunuza uygulandıklarında aşağıdaki klasörleri ekleyin:

|Klasör adı|Açıklama|
|-----------------|-----------------|
|\\*\<language name>*|Dil klasörü. *\<language name>* Dilin adıyla değiştirin. Örneğin, *\Matlab*.|
|*\ Sözdizimleri*|Dilbilgisi klasörü. Dil için *Matlab.js*gibi Grammar *. JSON* dosyalarını içerir.|
|*\ Kod parçacıkları*|Parçacıklar klasörü. Dil için kod parçacıkları içerir.|

Windows 'da *% userprofile%* şu yolu çözer: * \\ \<user name> c:\Users*. *Uzantılar* klasörü sisteminizde yoksa, oluşturmanız gerekir. Klasör zaten varsa gizli olacaktır.

> [!TIP]
> Düzenleyicide açık dosyalarınız varsa, TextMate dilbilgisi ekledikten sonra söz dizimi vurgulamasını görmek için bunları kapatıp yeniden açmanız gerekir.

TextMate dilbilgisi oluşturma hakkında daha fazla bilgi için bkz. [TextMate-dil dilbilgisi-giriş](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) ve [bir TextMate paketi Için nasıl dil dilbilgisi ve özel tema oluşturma hakkında notlar](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Ayrıca bkz.

- [Dil Sunucusu Protokolü uzantısı ekleme](../extensibility/adding-an-lsp-extension.md)
- [İzlenecek yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [İzlenecek yol: görüntüleme ifadesinin tamamlanması](../extensibility/walkthrough-displaying-statement-completion.md)
- [Örnek kod: TextMate dilbilgisi](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Örnek kod: özel dil desteği](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)