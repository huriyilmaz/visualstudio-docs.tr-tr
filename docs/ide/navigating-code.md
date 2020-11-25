---
title: Kod Gezinti komutları
description: Düzenleyicide kodunuzda gezinmek için kullanabileceğiniz farklı seçenekler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: tglee
ms.workload:
- multiple
ms.openlocfilehash: 77b0f8782f9ffaf37701f13b30be6e068ce05f8d
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871528"
---
# <a name="navigate-code"></a>Koda git

Visual Studio, düzenleyicide kod gezinmek için birçok yol sunar. Bu konu, kodunuzda gezinmek için farklı yollar özetler ve daha fazla ayrıntıya gidecek konuların bağlantılarını sağlar.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Geriye git ve Ileri git komutları

**Navigate Backward** **Ctrl** + **-** **Navigate Forward** **Ctrl** + **Shift** + **-** Ekleme noktasını önceki konumlara taşımak veya önceki bir konumdan daha yeni bir konuma geri dönmek için geri git (Ctrl) ve ileri git (Ctrl Shift) düğmelerine gidebilirsiniz. Bu düğmeler, ekleme noktasının son 20 konumunu korur. Bu komutlar Ayrıca **Görünüm** menüsünde **geri git** ' ın altında ve **İleri git**' in altında bulunur.

![İleri ve geri gezinti düğmeleri](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Gezinti çubuğu

Kod temelindeki koda gitmek için **Gezinti çubuğunu** (kod penceresinin en üstündeki açılan kutular) kullanabilirsiniz. Doğrudan buna gitmek için bir tür veya üye seçebilirsiniz. Visual Basic, C# veya C++ kod tabanında kod düzenlediğinizde gezinti çubuğu görüntülenir. Kısmi bir sınıfta, geçerli kod dosyası dışında tanımlanan Üyeler devre dışı bırakılabilir (gri renkte görünürler).

![Kod gezinti çubuğu](../ide/media/vside_navigation_bar.png)

Açılır kutuların etrafında aşağıdaki gibi gezinebilirsiniz:

- Geçerli dosyanın ait olduğu başka bir projeye gitmek için sol taraftaki açılan kutuda seçin.

- Bir sınıfa veya türe gitmek için ortadaki açılan kutuda seçin.

- Bir yordama veya bir sınıfın diğer üyesine doğrudan gitmek için sağ açılan kutuda bunu seçin.

- Odağı kod penceresinden gezinti çubuğuna kaydırmak için **CTRL** + **F2** tuş birleşimine basın.

- Odağı gezinti çubuğundaki kutudan kutuya kaydırmak için **Tab** tuşuna basın.

- Odağa sahip olan ve kod penceresine döndürülen gezinti çubuğu öğesini seçmek için **ENTER** tuşuna basın.

- Gezinti çubuğundan bir şeyi seçmeden koda odaklanmak için **ESC** tuşuna basın.

Gezinti çubuğunu gizlemek için, **metin düzenleyici tüm diller** ayarlarında (**Araçlar** **Navigation bar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **tüm diller**) gezinti çubuğu seçeneğini değiştirin veya ayrı dillerin ayarlarını değiştirebilirsiniz.

## <a name="find-all-references"></a>Tüm başvuruları bul

Çözümdeki seçili öğenin tüm başvurularını bulur. Bunu, büyük bir yeniden düzenleme için olası yan etkileri denetlemek veya "ölü" kodu doğrulamak için kullanabilirsiniz. Sonuçlar arasında geçmek için **F8** tuşuna basın. Daha fazla bilgi için bkz. [kodunuzda başvuruları bulma](finding-references.md).

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi bir yere tür adının içine yerleştirin ve **Shift** + **F12** tuşlarına basın
**Fare** | Sağ tıklama menüsünden **tüm başvuruları bul** ' u seçin

## <a name="reference-highlighting"></a>Başvuru vurgulama

Kaynak kodunda bir simgeye tıkladığınızda, söz konusu simgenin tüm örnekleri belgede vurgulanır. Vurgulanan semboller, bildirim ve başvuru içerebilir ve **tüm başvuruları** içeren diğer birçok sembol döndürülür. Bunlar sınıfların, nesnelerin, değişkenlerin, yöntemlerin ve özelliklerin adlarını içerir. Visual Basic kodda, birçok denetim yapısı için anahtar sözcükler de vurgulanır. İleri veya önceki vurgulanan simgeye gitmek için **CTRL** + **SHIFT** + **aşağı ok** veya **CTRL** + **SHIFT** + **yukarı ok** tuşlarına basın. **Araç**  >  **seçenekleri**  >  **ortam**  >  **yazı tipi ve renkler**  >  **vurgulanan başvuru** bölümünde vurgulama rengini değiştirebilirsiniz.

## <a name="go-to-commands"></a>Komutlara git

**Git ' in altındaki** **Düzenle** menüsünde bulunan aşağıdaki komutlara gidin:

- **Satıra git** (**CTRL** + **G**): etkin belgede belirtilen satır numarasına taşı.

- **Tümüne git** (**CTRL** + **T** veya **CTRL** + **,**): belirtilen satıra, türe, dosyaya, üyeye veya simgeye gider.

- **Dosyaya git** (**CTRL** + **1**, **CTRL** + **F**): çözümdeki belirtilen dosyaya taşı.

- **Son dosyaya git** (**CTRL** + **1**, **CTRL** + **R**): çözümdeki belirtilen, son ziyaret edilen dosyaya taşı.

- **Türe git** (**CTRL** + **1**, **CTRL** + **T**): çözümdeki belirtilen türe taşı.

- **Üyeye git** (**CTRL** + **1**, **CTRL** + **e**): çözümdeki belirtilen üyeye git.

- **Simgeye git** (**CTRL** + **1**, **CTRL** + **S**): çözümdeki belirtilen simgeye gider.

Visual Studio 2017 sürüm 15,8 ve sonraki sürümlerde, aşağıdaki gezinti komutlarına **Git** de kullanılabilir:

- **Dosyadaki bir sonraki soruna git** (**alt** + **PgDn**) ve **dosyadaki bir önceki soruna git** (**alt** + **PgUp**)

- **Son düzenleme konumuna git** (**CTRL** + **SHIFT** + **geri al**)

Bu komutlar hakkında daha fazla bilgi Için bkz. [komutları kullanarak kodu bulma](../ide/go-to.md) bölümüne bakın.

## <a name="go-to-definition"></a>Tanıma Git

Tanıma git, sizi seçili öğenin tanımına götürür. Daha fazla bilgi için bkz. [Tanıma Git ve açıklama açıklaması](../ide/go-to-and-peek-definition.md).

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi bir yere tür adının içine yerleştirin ve **F12** tuşuna basın
**Fare** | Tür adına sağ tıklayın ve **Tanıma Git**  ' i seçin veya **CTRL** tuşuna basın ve tür adına tıklayın

## <a name="peek-definition"></a>Tanıma Göz At

Göz atma tanımı, seçili öğenin tanımını, kod düzenleyicisindeki geçerli konumunuzla uzaklaşmadan bir pencerede görüntüler. Daha fazla bilgi için bkz. [nasıl yapılır: Özet tanımı 'nı kullanarak kodu görüntüleme ve düzenleme](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) ve [tanıma ve bakış tanımına git](../ide/go-to-and-peek-definition.md).

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi bir yere tür adının içine yerleştirin ve **alt** + **F12** tuşlarına basın
**Fare** | Tür adına sağ tıklayın ve bakış **tanımı** ' nı seçin veya **CTRL** tuşuna basın veya tür adına tıklayın ( **göz atma görünümünde aç seçeneğinde açık tanımı** varsa)

## <a name="go-to-implementation"></a>Uygulamaya git

Uygulamaya git ' i kullanarak, temel bir sınıftan gezinebilirsiniz veya uygulamalarına bir tür ekleyebilirsiniz. Birden çok uygulama varsa, bunları **sembol sonuçları bul** penceresinde listelendiğini göreceksiniz:

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi bir yere tür adının içine yerleştirin ve **CTRL** + **F12** tuşlarına basın
**Fare** | Tür adına sağ tıklayın ve **uygulamaya git** ' i seçin.

## <a name="go-to-base"></a>Temele Git

Temele git ' i kullanarak seçili öğenin devralma zincirinde gezinebilirsiniz. Birden çok sonuç varsa, bunları **temel git** penceresinde listelendiğini göreceksiniz:

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi bir yere tür adının içine yerleştirin ve **alt** + **giriş sayfasına** basın
**Fare** | Tür adına sağ tıklayın ve **temele git** ' i seçin

## <a name="call-hierarchy"></a>Çağrı Hiyerarşisi

[Çağrı hiyerarşisi penceresindeki](../ide/reference/call-hierarchy.md)bir yönteme ve bir yöntemine yapılan çağrıları görüntüleyebilirsiniz:

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi bir yere tür adının içine yerleştirin ve **CTRL** + **K**, **CTRL** + **T** tuşlarına basın
**Fare** | Üye adına sağ tıklayın ve **Çağrı hiyerarşisini görüntüle** ' yi seçin.

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Next yöntemi ve önceki yöntem komutları (Visual Basic)

Visual Basic kod dosyalarında, ekleme noktasını farklı yöntemlere taşımak için bu komutları kullanın. **Edit**  >  **Sonraki yöntemi** Düzenle veya **Edit**  >  **önceki yöntemi** Düzenle seçeneğini belirleyin.

## <a name="structure-visualizer"></a>Yapı görselleştiricisi

Kod düzenleyicisinde yapı görselleştiricisi özelliği, *Yapı Kılavuzu satırları* -kod tabanınızda eşleşen küme ayraçları belirten dikey kesikli çizgiler gösterir. Bu, mantıksal blokların nerede başlayıp bitmekte olduğunu görmeyi kolaylaştırır.

![Yapı görselleştiricisi](../ide/media/vside_structure_visualizer.png)

Yapı Kılavuzu satırlarını devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **genel** ' e gidin ve **yapıyı göster kılavuz çizgileri** kutusunu temizleyin.

## <a name="enhanced-scroll-bar"></a>Gelişmiş kaydırma çubuğu

Kodunuzun bir kuşbakışı görünümünü almak için, bir kod penceresinde gelişmiş kaydırma çubuğunu kullanabilirsiniz. Harita modunda, imleci kaydırma çubuğunu yukarı ve aşağı taşıdığınızda kodun önizlemelerini görebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu izleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>CodeLens bilgileri

Kod düzenleyicisinde CodeLens kullandığınızda, değişiklikler ve bu değişiklikleri kimin yaptığını, başvuruları, hataları, iş öğelerini, kod incelemelerini ve birim test durumunu oluşturan belirli kod hakkındaki bilgileri bulabilirsiniz. CodeLens, Team Foundation Server Visual Studio Enterprise kullandığınızda bir başlık görünümü gibi çalışır. Bkz. [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Çağrı hiyerarşisini görüntüle](../ide/reference/call-hierarchy.md)
