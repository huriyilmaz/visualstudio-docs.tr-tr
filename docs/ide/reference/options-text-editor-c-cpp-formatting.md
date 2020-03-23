---
title: Seçenekler, Metin Düzenleyici, C/C++, Biçimlendirme
ms.date: 04/30/2018
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
ms.openlocfilehash: d7a6029058ab0bc02a623df0e1733eb8548102d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596261"
---
# <a name="options-text-editor-cc-formatting"></a>Seçenekler, Metin Düzenleyici, C/C++, Biçimlendirme

C veya C++'da programlama yaparken kod düzenleyicisinin varsayılan davranışını değiştirmek için bu özellik sayfalarını kullanın.

![C++ Özellik sayfalarını biçimlendirme](media/cpp-formatting.png)

Bu sayfaya erişmek için, **Sol** bölmedeki Seçenekler iletişim kutusunda, Metin Düzenleyicisi'ni genişletin, **C/C++'ı**genişletin ve ardından **Biçimlendirme'yi**tıklatın. **Text Editor**

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi Kişiselleştir'e](../../ide/personalizing-the-visual-studio-ide.md)bakın.

## <a name="general-page"></a>Genel Sayfa

Bu sayfada, siz yazarken ifadeleri ve blokları biçimlendirme seçenekleri vardır.

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.7 ve sonrası**:

::: moniker-end

Sayfada ayrıca [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) sürüm 5.0 için destek yapılandırma seçenekleri de vardır. ClangFormat, .clang formatında veya _clang biçimli bir dosyada yapılandırılabilen bir dizi kurala göre kodunuzu stillendirmeyi ve biçimlendirmeyi kolaylaştıran bir yardımcı programdır.

### <a name="configuring-clangformat-options"></a>ClangFormat seçeneklerini yapılandırma

::: moniker range="vs-2017"

**Visual Studio 2017 sürüm 15.7 ve sonrası**:

::: moniker-end

ClangFormat desteği varsayılan olarak etkinleştirilir. Bu ortak biçimlendirme kurallarından hangisini tüm projelerinize uygulayacağını seçebilirsiniz: LLVM, Google, Chromium, Mozilla veya WebKit. Ayrıca özel biçim tanımı .clang biçimi veya _clang biçimli dosya oluşturabilirsiniz. Böyle bir dosya bir proje klasöründe varsa, Visual Studio bu klasördeki tüm kaynak kod dosyalarını ve alt klasörlerini biçimlendirmek için kullanır.

Varsayılan olarak, Visual Studio clangformat.exe arka planda çalışır yazarken biçimlendirme uygular. Ayrıca yalnızca el ile çağrılan biçimlendirme komutları **biçimlendirme belgesi (Ctrl+K, Ctrl+D)** veya **Biçim Seçimi (Ctrl + K, Ctrl + F)** için de çalıştırabilirsiniz.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Girintisi, Yeni Satırlar, Boşluk Tamamlama sayfaları

Bu sayfalar çeşitli biçimlendirme özelleştirmeleri etkinleştirir, ancak ClangFormat etkinse yoksayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [IntelliSense Kullanma](../../ide/using-intellisense.md)
