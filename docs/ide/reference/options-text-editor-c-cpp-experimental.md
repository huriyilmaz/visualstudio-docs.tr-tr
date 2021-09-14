---
title: Seçenekler, Metin Düzenleyici, C/C++, Deneysel
description: IntelliSense ve göz atma veritabanıyla ilgili deneysel davranışları değiştirmek için C/C++ bölümündeki Deneysel sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e35bdb8c6a56ef3174277836769201cd00e47dad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724921"
---
# <a name="options-text-editor-cc-experimental"></a>Seçenekler, Metin Düzenleyici, C/C++, Deneysel

Bu seçenekleri değiştirerek, C veya C++ dilinde programlama yapmak için IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirebilirsiniz. Bu özellikler gerçekten deneyseldir ve gelecek bir sürümde Visual Studio veya kaldırılabilir.

::: moniker range="vs-2017"

Bu makalede, 2017'Visual Studio seçenekleri açıklanmıştır. 2015'Visual Studio için içindekiler öğesinin üzerindeki seçicide **2015'i** seçin.

::: moniker-end

Bu özellik sayfasına erişmek için **Ctrl** + **Q tuşlarına** basarak arama kutusunu etkinleştirin ve deneysel **yazın.** Arama, ilk birkaç harfin ardından sayfayı bulur. Ayrıca, Araçlar Seçenekleri'ni seçerek ve **Metin** Düzenleyici'yi genişleterek,  >   ardından **C/C++** ve deneysel'i seçerek de bu seçenenebilirsiniz. 

Bu özellikler, bir Visual Studio kullanılabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz. [IDE'Visual Studio kişiselleştirme.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="enable-predictive-intellisense"></a>Tahmine Dayalı IntelliSense'i etkinleştirme

Tahmine dayalı IntelliSense, IntelliSense açılan listesinde görüntülenen sonuç sayısını sınırlar, böylece yalnızca bağlamda ilgili sonuçları görürsünüz. Örneğin, IntelliSense açılan listelerini yazarak çağırırsanız yalnızca tamsayıları veya `int x =` tamsayıları dönüşen işlevleri görürsünüz. Tahmine dayalı IntelliSense varsayılan olarak kapalıdır.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Daha hızlı proje yüklemesini etkinleştirme

2017 Visual Studio 15.3 sürümünden bu özellik Enable **Project Önbelleğe Alma** olarak adlandırılan ve [VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) Project Ayarlar özellik sayfasına taşınmıştır.

Bu seçenek Visual Studio proje verilerini önbelleğe almalarını sağlar. Böylece, projeyi bir sonraki aç aç seçeneğinde, önbelleğe alınan verileri proje dosyalarından yeniden hesaplamak yerine yük devredebilirsiniz. Önbelleğe alınan verilerin kullanımı proje yükleme sürelerini önemli ölçüde hızlandırabilir.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Visual Studio Market'te ek özellikler

Market'te ek metin düzenleyicisi özelliklerine [Visual Studio göz atabilirsiniz.](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads) Aşağıdakiler destekleyen [C++ Hızlı](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)Düzeltmeleri örneğidir:

- **Eksik #include** ekleme - Kodu #include bilinmeyen semboller için ilgili kodlar önerir

- **Ad alanı kullanarak ekleme/Tam nitelendirma simgesi** - Önceki öğe gibi, ancak ad alanları için

- **Eksik noktalı virgül ekleme**

- **Çevrimiçi yardım** - Hata iletileriniz için çevrimiçi yardım arama

- Ve daha fazlası...

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C++ içinde yeniden düzenleme (VC Blogu)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
