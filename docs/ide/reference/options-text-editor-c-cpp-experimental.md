---
title: Seçenekler, Metin Düzenleyici, C/C++, Deneysel
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 7e239ad3d2091f334f18ec00a367fc47d5c21db3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278703"
---
# <a name="options-text-editor-cc-experimental"></a>Seçenekler, Metin Düzenleyici, C/C++, Deneysel

Bu seçenekleri değiştirerek, C veya C++'da programlama yaparken IntelliSense ve tarama veritabanıyla ilgili davranışı değiştirebilirsiniz. Bu özellikler gerçekten deneyseldir ve ileride yayınlanacak bir sürümde Visual Studio'dan değiştirilebilir veya kaldırılabilir.

::: moniker range="vs-2017"

Bu makalede Visual Studio 2017'deki seçenekler açıklanmaktadır. Visual Studio 2015 için, içindekiler tablosunun üstündeki seçicide **2015'i** seçin.

::: moniker-end

Bu özellik sayfasına erişmek için, arama kutusunu etkinleştirmek için **Ctrl**+**Q** tuşuna basın ve ardından **deneysel**yazın. Arama, ilk birkaç harften sonra sayfayı bulur. Ayrıca **Araçlar** > **Seçenekleri** seçerek ve **Metin Düzenleyicisi**, sonra C / C **++** genişleterek ve daha sonra **Deneysel**seçerek alabilirsiniz.

Bu özellikler Visual Studio yüklemesinde mevcuttur.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. [Bkz. Visual Studio IDE'yi Kişiselleştirin.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="enable-predictive-intellisense"></a>Predictive IntelliSense etkinleştirin

Predictive IntelliSense, IntelliSense açılır listedeki görüntülenmiş sonuç sayısını sınırlar, böylece yalnızca bağlamda alakalı sonuçlar görürsünüz. Örneğin, IntelliSense açılır düşüşünü yazıp `int x =` çağırırsanız, yalnızca tamsayı döndüren tamsayılar veya işlevler görürsünüz. Predictive IntelliSense varsayılan olarak kapatılır.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Daha hızlı proje yüklemesini etkinleştirme

Visual Studio 2017 sürüm 15.3 itibariyle bu özellik **Proje Önbelleğe Alma Özelliği** olarak adlandırılır ve [VC++ Proje Ayarları](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) özellik sayfasına taşınmıştır.

Bu seçenek, Visual Studio'nun proje verilerini önbelleğe almalarını sağlar, böylece projeyi bir dahaki sefere açtığınızda önbelleğe alınmış verileri proje dosyalarından yeniden hesaplamak yerine yükleyebilir. Önbelleğe alınan verilerin kullanılması, proje yükleme süresini önemli ölçüde hızlandırabilir.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Visual Studio Marketplace'teki ek özellikler

[Visual Studio Marketplace'teki](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads)ek metin düzenleyici özelliklerine göz atabilirsiniz. Aşağıdakileri destekleyen [C++ Hızlı Düzeltmeler'e](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)örnek olarak şunlar verilmiştir:

- **Eksik #include ekleme** - Kodunuzda bilinmeyen semboller için ilgili #include önerir

- **Ad alanı/Tam eleme simgesini kullanarak ekleme** - Önceki öğeyi beğenin, ancak ad alanları için

- **Eksik semicolon ekle**

- **Çevrimiçi yardım** - Hata iletileriniz için çevrimiçi yardım arama

- Ve daha fazlası...

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C++ içinde Yeniden Düzenleme (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
