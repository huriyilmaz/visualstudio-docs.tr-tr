---
title: Diğer diller için düzenleyici desteği ekleme
description: Visual Studio düzenleyicisinin farklı bilgisayar dillerinde okuma ve gezinmeyi nasıl desteklediğini ve diğer diller için nasıl destek ekleyebilirsiniz?
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4933868248da896766d95875dc8e78b2eb56b1052456e55ca086a554cd7296cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358459"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Diğer Visual Studio için düzenleyici desteği ekleme

Visual Studio düzenleyicisinin farklı bilgisayar dillerinde okuma ve gezinmeyi nasıl desteklediğini ve diğer diller için Visual Studio düzenleyici desteği ekleme hakkında bilgi edinebilirsiniz.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Söz dizimi renklendirmesi, deyim tamamlama ve Git desteği

Visual Studio düzenleyicisinde söz dizimi renklendirmesi, deyim tamamlama (IntelliSense olarak da bilinir) ve _Navigate To_ gibi özellikler kodunuzu daha kolay yazmanıza, okumanıza ve düzenlemenize yardımcı olabilir. Aşağıdaki ekran görüntüsünde, Visual Studio'de Perl betiği düzenleme örneği Visual Studio. Söz dizimi otomatik olarak renklenir. Örneğin, kodda açıklamalar yeşil, kod siyah, yollar kırmızı ve deyimleri mavi renktedir. Bu Visual Studio düzenleyicisi, desteklediği herhangi bir dile söz dizimi renklendirmesi uygular. Ayrıca, bilinen bir dil anahtar sözcüğü veya nesnesi girmeye başlandıktan sonra deyim tamamlama, olası deyimlerin ve nesnelerin listesini görüntüler. Deyim tamamlama, kodu daha hızlı ve kolay bir şekilde yazmanıza yardımcı olabilir.

![Perl betiğinde söz dizimi renklendirmesi](../ide/media/vside_perledit.png)

Visual Studio şu anda TextMate Dil Bilgisi kullanarak aşağıdaki diller için söz dizimi renklendirmesi ve temel deyim [tamamlama desteği sağlar.](https://manual.macromates.com/en/language_grammars) Ancak, sık kullanılan diliniz tabloda yoksa endişelenmeyin, &mdash; bunu ekabilirsiniz.


- Yarasa
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Go
- JavaDoc
- Objective-C
- GölgelendiriciLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- Daha az
- Python
- SQL
- VBNet
- CSS
- INI
- Lua
- R
- Swift
- XML
- Docker
- Jade
- Marka
- Ruby
- TypeScript
- YAML

Söz dizimi renklendirmesi ve temel deyim tamamlamaya ek Visual Studio git adlı bir özelliği [de vardır.](/archive/blogs/benwilli/visual-studio-tip-3-use-navigate-to) Bu özellik, kod dosyalarını, dosya yollarını ve kod simgelerini hızla aramanızı sağlar. Visual Studio aşağıdaki diller için Navigate To desteği sağlar.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Başlayın

- Java

- PHP

Bu dosya türlerinin hepsi, verilen dil desteği henüz yüklenmemiş olsa bile daha önce açıklanan özelliklere sahiptir. Bazı diller için özelleştirilmiş destek yüklemek IntelliSense veya ampuller gibi diğer gelişmiş dil özellikleri gibi ek dil desteği sağlar.

## <a name="add-support-for-non-supported-languages"></a>Destek olmayan diller için destek ekleme

Visual Studio, TextMate Dil Bilgisi kullanarak [düzenleyicide dil desteği sağlar.](https://manual.macromates.com/en/language_grammars) Sık kullanılan programlama diliniz şu anda Visual Studio düzenleyicide desteklenmiyorsa, önce web'de dil için &mdash; bir TextMate paketi aramanız gerekir. Ancak bir tane bulamazsanız, dil dil bilgisi ve kod parçacıkları için bir TextMate paket modeli oluşturarak kendiniz destek ekleyebilirsiniz.

Aşağıdaki klasöre tüm yeni TextMate Visual Studio dil bilgisi ekleyin:

*%userprofile% \\ .vs\Extensions*

Bu temel yolun altına, sizin durumunuz için geçerli olan aşağıdaki klasörleri ekleyin:

|Klasör Adı|Açıklama|
|-----------------|-----------------|
|\\*\<language name>*|Dil klasörü. yerine *\<language name>* dilin adını yazın. Örneğin, *\Matlab*.|
|*\Söz Dizimleri*|Dil bilgisi klasörü. dil bilgisi *.json* dosyalarını içerir, örneğin üzerinde *Matlab.js.*|
|*\Kod Parçacıkları*|kod parçacıkları klasörü. Dil için kod parçacıkları içerir.|

Bu *Windows, %userprofile%* *c:\Users yoluna çözümlemektedir. \\ \<user name>* Uzantılar  klasörü sisteminiz içinde yoksa oluşturmanız gerekir. Klasör zaten varsa gizlidir.

> [!TIP]
> Düzenleyicide açık dosyanız varsa, TextMate Dil Bilgisi'ni ekledikten sonra söz dizimi vurgulamayı görmek için dosyaları kapatıp yeniden açabilirsiniz.

TextMate Dil Bilgisi oluşturma hakkında ayrıntılı bilgi için textmate - Language [Grammars'a](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) giriş ve Textmate Paketi için Dil Bilgisi ve Özel Tema oluşturma hakkında [bilgi edinin.](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil Sunucusu Protokolü uzantısı ekleme](../extensibility/adding-an-lsp-extension.md)
- [İzlenecek yol: Kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)
- [Adım adım kılavuz: Deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)
- [Örnek kod: TextMate Dil Bilgisi](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Örnek kod: Özel dil desteği](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)