---
title: Seçenekler, Metin Düzenleyici, C/C++, Biçimlendirme
description: C ve C++ ile programlama yapmak için kod düzenleyicisinde kod biçimlendirme seçeneklerini ayarlamak için Biçimlendirme seçenekleri sayfasını ve alt sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: b89e3949a5002d7194939f4edc1bd5c185e145d1
ms.sourcegitcommit: 5f1e0171626e13bb2c5a6825e28dde48061208a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2021
ms.locfileid: "129704693"
---
# <a name="options-text-editor-cc-formatting"></a>Seçenekler, Metin Düzenleyici, C/C++, Biçimlendirme

C veya C++ dilinde programlama yapmak için kod düzenleyicisinin varsayılan davranışını değiştirmek için bu özellik sayfalarını kullanın.

![C++ Biçimlendirme özellik sayfaları](media/cpp-formatting.png)

Bu sayfaya erişmek için, Seçenekler iletişim kutusundaki sol bölmede Metin Düzenleyici'yi **genişletin,** **C/C++ öğesini genişletin** ve biçimlendirme'ye **tıklayın.** 

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="general-page"></a>Genel Sayfa

Bu sayfada, siz bunları yazarak deyimleri ve blokları biçimlendirme seçenekleri vardır.

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.7 ve sonraki sürümler:**

::: moniker-end

Sayfada [Ayrıca ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) sürüm 5.0 için destek yapılandırma seçenekleri de vardır. ClangFormat, kodunuzu .clang biçiminde veya bir .clang biçiminde ya da farklı biçimli bir dosyada yapılandırılan bir kural kümesine göre stil ve biçim _clang kolaylaştıran bir yardımcı programdır.

### <a name="configuring-clangformat-options"></a>ClangFormat seçeneklerini yapılandırma

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.7 ve sonraki sürümler:**

::: moniker-end

ClangFormat desteği varsayılan olarak etkindir. Tüm projelerinize uygulanacak yaygın biçimlendirme kuralları arasında hangilerini seçebilirsiniz: LLVM, Google, Chromium, Mozilla veya WebKit. Ayrıca özel bir biçim tanımı .clang-format veya _clang biçimi dosyası oluşturabilirsiniz. Böyle bir dosya bir proje klasöründe varsa, Visual Studio klasördeki ve alt klasördeki tüm kaynak kod dosyalarını biçimlendirmek için bu dosyayı kullanır.

Varsayılan olarak, Visual Studio arka clangformat.exe siz yazarak biçimlendirmeyi uygular. Ayrıca, yalnızca el ile çağrılan biçimlendirme komutları için çalıştırmayı belirtebilirsiniz Belgeyi **Biçimlendir (Ctrl+K, Ctrl+D)** veya Biçim Seçimi **(Ctrl + K, Ctrl + F)**.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Girintileme, Yeni Satırlar, Aralıklar, Kaydırma sayfaları

Bu sayfalar çeşitli biçimlendirme özelleştirmelerini etkinleştirir, ancak ClangFormat etkinse yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense'i kullanma](../../ide/using-intellisense.md)
