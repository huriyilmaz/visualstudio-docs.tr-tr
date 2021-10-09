---
title: Seçenekler, Metin Düzenleyici, C/C++, Deneysel
description: IntelliSense ve gözatma veritabanıyla ilgili deneysel davranışları değiştirmek için C/C++ bölümünde deneysel sayfayı nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2021
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
ms.openlocfilehash: 6bdb43b30b2d8999de07134f113e8cca2994477a
ms.sourcegitcommit: 5f1e0171626e13bb2c5a6825e28dde48061208a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2021
ms.locfileid: "129704656"
---
# <a name="options-text-editor-cc-experimental"></a>Seçenekler, Metin Düzenleyici, C/C++, Deneysel

Bu seçenekleri değiştirerek, C veya C++ ' da programlama yaparken IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirebilirsiniz. bu özellikler gerçekten deneysel bir sürümündedir ve gelecekte Visual Studio değiştirilebilir veya kaldırılabilir.

::: moniker range="vs-2017"

bu makalede Visual Studio 2017 ' deki seçenekler açıklanmaktadır. Visual Studio 2015 için, içindekiler tablosunun üzerindeki seçicide **2015** ' i seçin.

::: moniker-end

Bu özellik sayfasına erişmek için **CTRL** + **Q** tuşlarına basarak arama kutusunu etkinleştirin ve **deneysel** yazın. Arama, ilk birkaç harften sonra sayfayı bulur. Ayrıca, **Araçlar**  >  **Seçenekler** ' i ve **metin düzenleyicisini** genişleterek, **C/C++** ve sonra **deneysel**' u seçerek de bu işe ulaşabilirsiniz.

bu özellikler Visual Studio yüklemesinde mevcuttur.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. bkz. [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Tahmine dayalı IntelliSense 'i etkinleştir

Tahmine dayalı IntelliSense, yalnızca bağlamla ilgili sonuçları görmeniz için IntelliSense açılan listesinde görüntülenen sonuçların sayısını sınırlar. Örneğin, `int x =` IntelliSense açılan listesini yazıp çağırdığınızda yalnızca tamsayılar döndüren tamsayılar veya işlevler görürsünüz. Tahmine dayalı IntelliSense varsayılan olarak kapalıdır.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Daha hızlı proje yüklemeyi etkinleştir

Visual Studio 2017 sürüm 15,3 itibariyle, bu özellik **Project Önbelleğe Alma etkinleştir** olarak adlandırılır ve [VC + + Project Ayarlar](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) özellik sayfasına taşınmıştır.

bu Visual Studio seçenek, proje verilerinin önbelleğe alınmasını sağlayarak projeyi bir dahaki sefer açtığınızda proje dosyalarından yeniden bilgi işlem yerine önbelleğe alınmış verileri yükleyebilir. Önbelleğe alınmış verilerin kullanılması, proje yükleme süresini önemli ölçüde hızlandırabilir.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Visual Studio market 'teki ek özellikler

[Visual Studio marketi](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads)'nde ek metin düzenleyicisi özelliklerine gidebilirsiniz. Aşağıda, [C++ hızlı düzeltmeleri](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)ve aşağıdakiler desteklenir:

- **Eksik #include Ekle** -kodunuzda bilinmeyen semboller için ilgili #include önerilir

- Önceki öğe gibi **ad alanı/tam niteleme simgesini kullanarak ekleme** , ancak ad alanları için

- **Eksik noktalı virgül Ekle**

- **Çevrimiçi yardım** -hata iletileriniz için çevrimiçi Yardım ara

- Ve daha fazlası...

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
- [C++ ' da yeniden düzenleme (VC blogu)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
