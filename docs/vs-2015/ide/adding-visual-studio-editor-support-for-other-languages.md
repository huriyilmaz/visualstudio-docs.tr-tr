---
title: Diğer diller için düzenleyici desteği ekleme | Microsoft Docs
ms.date: 11/15/2016
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9dbd245edd81907197e23c0d193a01cc07424b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548115"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Visual Studio düzenleyicisine diğer diller için destek ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio düzenleyicisinin farklı bilgisayar dillerini okumayı ve gezinmeyi nasıl desteklediğini ve diğer diller için Visual Studio Düzenleyicisi desteğini nasıl ekleyeceğinizi öğrenin.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Sözdizimi renklendirme, ekstre tamamlama ve desteğe gitme
 Visual Studio Düzenleyicisi 'ndeki sözdizimi renklendirme, ekstre tamamlama ve gitme gibi özellikler, kodunuzun kolayca okunmasını, oluşturulmasını ve düzenlemenizi sağlamanıza yardımcı olabilir. Aşağıdaki ekran görüntüsünde, Visual Studio 'da bir perl betiğini düzenlemeyle bir örnek gösterilmektedir. Sözdizimi otomatik olarak renklendirilmiştir. Örneğin, koddaki açıklamalar yeşil, kod siyah, yollar kırmızı ve deyimler mavi renktedir. Visual Studio Düzenleyicisi, desteklediği dile otomatik olarak sözdizimi renklendirme uygular. Ayrıca, bilinen bir dil anahtar sözcüğünü veya nesnesini girmeye başladığınızda, deyim tamamlama olası deyimler ve nesnelerin bir listesini görüntüler. Deyimin tamamlanması, kodu daha hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.

 ![Perl betikte sözdizimi renklendirme](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Visual Studio şu anda [TextMate Grammars](https://manual.macromates.com/en/language_grammars)kullanarak aşağıdaki diller için sözdizimi renklendirme ve temel ifade tamamlama desteği sunmaktadır. En sevdiğiniz dil tabloda değilse, bu, endişelenmeyin, siz de ekleyebilirsiniz.

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

- Başlayın

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  Bu dosya türlerinin tümünde, belirli bir dil için destek henüz yüklenmemiş olsa bile daha önce açıklanan özellikler vardır. Bazı diller için özel destek yüklemek, IntelliSense veya hafif bulbs gibi diğer gelişmiş dil özellikleri gibi ek dil desteği sağlayabilir.

## <a name="adding-support-for-non-supported-languages"></a>Desteklenmeyen diller için destek ekleme
 Visual Studio 2015 güncelleştirme 1 ve sonraki sürümleri, [TextMate Grammars](https://manual.macromates.com/en/language_grammars)kullanarak düzenleyicide dil desteği sağlar. En sevdiğiniz programlama diliniz Visual Studio düzenleyicisinde henüz desteklenmiyorsa, önce Web 'de arama yapın, dil için bir TextMate paketi zaten mevcut olabilir. Bir tane bulamıyorsanız, dil dilbilgisi ve kod parçacıkları için bir TextMate paketi oluşturarak Visual Studio 2015 güncelleştirme 1 veya sonraki bir sürümü için kendiniz destek ekleyebilirsiniz.

 Aşağıdaki klasöre Visual Studio için yeni bir TextMate dilbilgisi ekleyin:

 % userprofile% \\ . Vs\extensions

 Bu temel yol altında, durumunuza uygulandıklarında aşağıdaki klasörleri ekleyin:

|Klasör adı|Description|
|-----------------|-----------------|
|\\*\<language name>*|Dil klasörü. *\<language name>* Dilin adıyla değiştirin. Örneğin, **\Matlab**.|
|\ Sözdizimleri|Dilbilgisi klasörü. Dil için **Matlab.js**gibi Grammar. JSON dosyalarını içerir.|
|\ Kod parçacıkları|Parçacıklar klasörü. Dil için kod parçacıkları içerir.|

 Windows 'da% userprofile% şu yolu çözer: c:\Users \\ *\<user name>* . Uzantılar klasörü sisteminizde yoksa, oluşturmanız gerekir. Klasör zaten varsa gizli olacaktır.

 TextMate dilbilgisi oluşturma hakkında ayrıntılı bilgi için bkz. [TextMate – dile giriş dilbilgisi: HTML 'de gömülü kaynak kodu sözdizimi vurgulamayı ekleme](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) ve [bir TextMate paketi için dil dilbilgisi ve özel tema oluşturma hakkında notlar](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 2013 iyileştirmeler](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md) [Izlenecek yol: deyimin tamamlanmasını görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)
