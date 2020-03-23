---
title: Diğer diller için düzenleyici desteği ekleme
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590884"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Diğer diller için Visual Studio düzenleyici desteği ekleme

Visual Studio düzenleyicisinin farklı bilgisayar dillerinde okumayı ve gezinmeyi nasıl desteklediği ve diğer diller için Visual Studio düzenleyici desteği ni nasıl ekleyebileceğiniz hakkında bilgi edinin.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Sözdizimi renklendirme, ekstre tamamlama ve destek için gezinme

Görsel Stüdyo düzenleyicisindeki sözdizimi renklendirme, ifade tamamlama (IntelliSense olarak da bilinir) ve _Gezinme ye_ gibi özellikler kodunuzu daha kolay yazmanıza, okumanıza ve değiştirmenize yardımcı olabilir. Aşağıdaki ekran görüntüsü Visual Studio'da bir Perl komut dosyası düzenleme bir örnek gösterir. Sözdizimi otomatik olarak renklenir. Örneğin, koddaki açıklamalar yeşil renkli, kod siyah, yollar kırmızı ve deyimler mavidir. Visual Studio düzenleyicisi, desteklediği herhangi bir dile otomatik olarak sözdizimi renklendirme uygular. Ayrıca, bilinen bir dil anahtar sözcüğü veya nesnesini girmeye başladığınızda, deyim tamamlama olası deyimlerin ve nesnelerin listesini görüntüler. Ekstre tamamlama, kod yazmayı daha hızlı ve kolay bir şekilde yazmanıza yardımcı olabilir.

![Perl komut dosyasında sözdizimi renklendirme](../ide/media/vside_perledit.png)

Visual Studio şu anda [TextMate Grammars](https://manual.macromates.com/en/language_grammars)kullanarak aşağıdaki diller için sözdizimi renklendirme ve temel deyim tamamlama desteği sağlar. En sevdiğiniz dil tabloda yoksa, endişelenmeyin&mdash;ekleyebilirsiniz.

|||||||
|-|-|-|-|-|-|
|Yarasa|F#|Java|Markdown|Pas|Visual Basic|
|Clojure|Başlayın|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|Daha az|Python|SQL|VBNet|
|CSS|INI|Lua|R|Swift|XML|
|Docker|Jade|Marka|Ruby|TypeScript|YAML|

Sözdizimi renklendirme ve temel ifade tamamlama ek olarak, Visual Studio da [için git](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/)adlı bir özelliği vardır. Bu özellik, kod dosyalarını, dosya yollarını ve kod sembollerini hızla aramanızı sağlar. Visual Studio, aşağıdaki diller için Gezinme desteği sağlar.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Başlayın

- Java

- PHP

Bu dosya türlerinin tümü, belirli bir dilin desteği henüz yüklenmemiş olsa bile daha önce açıklanan özelliklere sahiptir. Bazı diller için özel destek yüklemek, IntelliSense veya ampuller gibi diğer gelişmiş dil özellikleri gibi ek dil desteği sağlayabilir.

## <a name="add-support-for-non-supported-languages"></a>Desteklenmeyen diller için destek ekleme

Visual [Studio, TextMate Grammars'ı](https://manual.macromates.com/en/language_grammars)kullanarak editörde dil desteği sağlar. En sevdiğiniz programlama dili şu anda Visual Studio düzenleyicisinde desteklenmiyorsa, öncelikle web'de&mdash;dil için bir TextMate paketinde arama yapın. Ancak bulamıyorsanız, dil gramerleri ve parçacıklar için bir TextMate paket modeli oluşturarak kendiniz destek ekleyebilirsiniz.

Visual Studio için yeni TextMate Gramerlerini aşağıdaki klasöre ekleyin:

*%userprofile%\\.vs\Uzantılar*

Bu temel yolun altında, durumunuza uygulanıyorsa aşağıdaki klasörleri ekleyin:

|Klasör Adı|Açıklama|
|-----------------|-----------------|
|\\*\<dil adı>*|Dil klasörü. * \<dil adını>* dilin adı ile değiştirin. Örneğin, *\Matlab*.|
|*\Sözdizimi*|Dilbilgisi klasörü. *Matlab.json*gibi dil için dilbilgisi *.json* dosyalarını içerir.|
|*\Parçacıklar*|Parçacıklar klasörü. Dil için parçacıklar içerir.|

Windows'da *%kullanıcı profili %yol* üzerinde çözer: *\\\<c:\Kullanıcılar kullanıcı adı>. * *Sisteminizde Uzantılar* klasörü yoksa, bunu oluşturmanız gerekir. Klasör zaten varsa, gizlenir.

> [!TIP]
> Düzenleyicide açık olan dosyalarınız varsa, TextMate Gramerleri ekledikten sonra sözdizimi vurgulamasını görmek için dosyaları kapatmanız ve yeniden açmanız gerekir.

TextMate Gramerlerinin nasıl oluşturulacaaçık bilgi için [TextMate - Introduction to Language Grammars](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) ve Notes hakkında bir [Metin Arkadaşı Paketi için Dil Dilbilgisi ve Özel Tema oluşturma](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)hakkında bilgi alın.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil Sunucusu Protokolü uzantısı ekleme](../extensibility/adding-an-lsp-extension.md)
- [İzlenecek Yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Walkthrough: Görüntü deyimi tamamlama](../extensibility/walkthrough-displaying-statement-completion.md)
