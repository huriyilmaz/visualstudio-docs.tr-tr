---
title: Dosyaya git, simgeye git, satıra git
description: Visual Studio komutlara git ve kodunuzda odaklanmış aramalar gerçekleştirmek için bunları nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 352cb8768a14d75df76e95009a5968ff8ab21d2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109246"
---
# <a name="find-code-using-go-to-commands"></a>Git komutlarını kullanarak kod bulma

Visual Studio, belirtilen öğeleri hızlı bir şekilde bulmanıza yardımcı olması için kodunuzda odaklanmış bir arama gerçekleştirmek için komutlara **gidin** . Basit ve Birleşik bir arabirimden belirli bir satıra, türe, simgeye, dosyaya ve üyeye gidebilirsiniz.

## <a name="how-to-use-it"></a>Nasıl kullanılır?

Giriş | İşlev
------------ | ---
**Klavye** | **CTRL** + **T** veya **CTRL** +  tuşlarına basın
**Fare** | **Düzenle** git ' i seçerek  >    >  **Tümünü git** ' i seçin

Kod Düzenleyicinizde sağ üst köşede küçük bir pencere görüntülenir.

![Tüm pencereye git](media/go-to-all.png)

Metin kutusuna yazarken sonuçlar, metin kutusunun altındaki bir açılan listede görüntülenir. Bir öğeye gitmek için listeden seçin.

![Pencereye git](../ide/media/vside_navigatetowindow.png)

Ek Yardım almak için bir soru işareti (**?**) de girebilirsiniz.

![Tüm yardım 'A git](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrelenmiş aramalar

Varsayılan olarak, belirtilen öğe tüm çözüm öğelerinde aranır. Ancak, arama terimlerinizi belirli karakterlerle önceden sunarak, kod Aramanızı belirli öğe türleriyle sınırlayabilirsiniz. Ayrıca, **Git** iletişim kutusu araç çubuğunda düğmeler ' i seçerek arama filtresini hızlıca değiştirebilirsiniz. Tür filtrelerini değiştiren düğmeler sol tarafta, aramanın kapsamını değiştiren düğmeler sağ tarafta bulunur.

![Üyelere git](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Belirli bir kod öğesi türüne filtrele

Aramanızı belirli bir kod öğesi türüne daraltmak için, arama kutusunda bir ön ek belirtebilir veya beş filtre simgelerinden birini seçebilirsiniz:

Ön ek | Simge | Kısayol | Açıklama
:-: | - | - | -
:| ![Çizgi simgesi](media/gotoall-line-icon.png) | **CTRL** + **G** | Belirtilen satır numarasına git
f| ![Dosyalar simgesi](media/gotoall-files-icon.png) | **CTRL** + **1**, **CTRL** + **F** | Belirtilen dosyaya git
r| ![Son dosyalar simgesi](media/gotoall-recent-files-icon.png) | **CTRL** + **1**, **CTRL** + **R** | Belirtilen, son ziyaret edilen dosyaya git
t| ![Türler simgesi](media/gotoall-types-icon.png) | **CTRL** + **1**, **CTRL** + **T** | Belirtilen türe git
m| ![Üyeler simgesi](media/gotoall-members-icon.png) | **CTRL** + **1**, **CTRL tuşuna** +  | Belirtilen üyeye git
\#| ![Semboller simgesi](media/gotoall-symbols-icon.png) | **CTRL** + **1**, **CTRL** + **S** | Belirtilen simgeye git

### <a name="filter-to-a-specific-location"></a>Belirli bir konuma filtrele

Aramanızı belirli bir konuma daraltmak için, iki belge simgesinin birini seçin:

Simge | Açıklama
---- | ---
![Geçerli belge](media/gotoall_currentdocument.png) | Yalnızca geçerli belgeyi ara
![Dış belgeler](media/gotoall_external.png) | Dış belgeleri projede/çözümde bulunanlara ek olarak ara

## <a name="camel-casing"></a>Kamel büyük harfleri

Kodunuzda [ortası](https://en.wikipedia.org/wiki/Camel_case) büyük harfleri kullanırsanız, yalnızca kod öğesi adının büyük harflerini girerek kod öğelerini daha hızlı bulabilirsiniz. Örneğin, kodunuzun adında bir tür varsa `CredentialViewModel` , **tür** filtresini (**t**) seçerek ve sonra `CVM` Git iletişim kutusunda adın yalnızca büyük harflerini () girerek aramayı daraltabilirsiniz. Kodunuzun uzun adlara sahip olması durumunda bu özellik yararlı olabilir.

![Pencereye gitme-büyük harfler ile arama](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Ayarlar

Dişli simgesini seçme ![Dişli simgesi](media/gotoall_gear.png) Bu özelliğin nasıl çalıştığını değiştirmenize izin verir:

Ayar | Açıklama
------- | ---
Önizleme sekmesini kullan | Seçili öğeyi IDE 'nin önizleme sekmesinde hemen görüntüle
Ayrıntıları göster | Penceredeki belge açıklamalarından proje, dosya, satır ve Özet bilgilerini görüntüleme
Pencereyi Ortala | Bu pencereyi, sağ üst yerine kod düzenleyicisinin üst ortasına taşıyın

## <a name="see-also"></a>Ayrıca bkz.

- [Koda git](../ide/navigating-code.md)
- [Satıra Git iletişim kutusu](../ide/reference/go-to-line.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
