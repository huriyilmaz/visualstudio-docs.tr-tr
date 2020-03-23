---
title: Dosyaya git, sembole git, satıra git
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb39f1d395e48351aeacb587556224b0f86aac3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593791"
---
# <a name="find-code-using-go-to-commands"></a>Git komutlarını kullanarak kod bulma

Visual Studio'nun **Go To** komutları, belirtilen öğeleri hızla bulmanıza yardımcı olmak için kodunuzu odaklanmış bir şekilde arar. Basit, birleşik bir arabirimden belirli bir satıra, türe, simgeye, dosyaya ve üyeye gidebilirsiniz.

## <a name="how-to-use-it"></a>Nasıl kullanılır?

Girdi | İşlev
------------ | ---
**Klavye** | **Ctrl**+**T** veya **Ctrl tuşuna**+basın **,**
**Fare** | Tümünü Seç**Go To All** **Et** > **Git** > 

Kod düzenleyicinizin sağ üst kısmında küçük bir pencere görüntülenir.

![Tüm pencereye git](media/go-to-all.png)

Metin kutusuna yazarken, sonuçlar metin kutusunun altındaki açılır listede görünür. Bir öğeye gitmek için, onu listede seçin.

![Pencereye Git](../ide/media/vside_navigatetowindow.png)

Ek yardım almak için bir soru işareti**de**girebilirsiniz.

![Tüm Yardıma Git](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrelenmiş aramalar

Varsayılan olarak, belirtilen öğe tüm çözüm öğeleri aranır. Ancak, belirli karakterlerle arama terimleri önyüzerek kod aramanızı belirli öğe türleri ile sınırlandırabilirsiniz. Ayrıca, **Git** iletişim kutusu araç çubuğundaki düğmeleri seçerek arama filtresini hızla değiştirebilirsiniz. Tür filtrelerini değiştiren düğmeler sol tarafta, aramanın kapsamını değiştiren düğmeler ise sağ taraftadır.

![Üyelere git](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Belirli bir kod öğesi türüne filtre leme

Aramanızı belirli bir kod öğesi türüyle daraltmak için, arama kutusunda bir önek belirtebilir veya beş filtre simgesinden birini seçebilirsiniz:

Ön ek | Simge | Kısayol | Açıklama
:-: | - | - | -
:| ![Çizgi simgesi](media/gotoall-line-icon.png) | **Ctrl**+**G** | Belirtilen satır numarasına gitme
f| ![Dosyalar simgesi](media/gotoall-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**F** | Belirtilen dosyaya gitme
r| ![Son dosyalar simgesi](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**R** | Belirtilen, en son ziyaret edilen dosyaya gitme
t| ![Türleri simgesi](media/gotoall-types-icon.png) | **Ctrl**+**1**, **Ctrl**+**T** | Belirtilen türe gitme
m| ![Üye simgesi](media/gotoall-members-icon.png) | **Ctrl**+**1**, **Ctrl**+**M** | Belirtilen üyeye git
\#| ![Semboller simgesi](media/gotoall-symbols-icon.png) | **Ctrl**+**1**, **Ctrl**+**S** | Belirtilen simgeye gitme

### <a name="filter-to-a-specific-location"></a>Belirli bir konuma filtre leme

Aramanızı belirli bir konuma daraltmak için iki belge simgesinden birini seçin:

Simge | Açıklama
---- | ---
![Geçerli Belge](media/gotoall_currentdocument.png) | Yalnızca geçerli belgeyi arama
![Dış Belgeler](media/gotoall_external.png) | Projede/çözümde bulunanlara ek olarak harici belgeleri arama

## <a name="camel-casing"></a>Deve kılıfı

Kodunuzda [deve kılıfı](https://en.wikipedia.org/wiki/Camel_case) kullanıyorsanız, kod öğesi adının yalnızca büyük harflerini girerek kod öğelerini daha hızlı bulabilirsiniz. Örneğin, kodunuzda tür adı `CredentialViewModel`verilen bir tür varsa, **Tür** filtresini (**t)** seçip sonra da Go`CVM`To iletişim kutusuna () adının büyük harflerini girerek aramayı daraltabilirsiniz. Bu özellik, kodunuzda uzun adlar varsa yararlı olabilir.

![Pencereye Git - büyük harflerle arama](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Ayarlar

Dişli simgesini seçme ![Dişli simgesi](media/gotoall_gear.png) bu özelliğin çalışma şeklini değiştirmenize olanak tanır:

Ayar | Açıklama
------- | ---
Önizleme sekmesini kullanma | Seçili öğeyi Hemen IDE'nin önizleme sekmesinde görüntüleme
Ayrıntıları göster | Penceredeki belge yorumlarından proje, dosya, satır ve özet bilgilerini görüntüleme
Orta pencere | Bu pencereyi sağ üstteki yerine kod düzenleyicisinin en üst merkezine taşıyın

## <a name="see-also"></a>Ayrıca bkz.

- [Kodda gezinme](../ide/navigating-code.md)
- [Satıra Git iletişim kutusu](../ide/reference/go-to-line.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)
