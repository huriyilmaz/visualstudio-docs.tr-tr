---
title: Kod bölgelerini daraltma ve genişletme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585762"
---
# <a name="outlining"></a>Anahat Oluşturma

Bir artı işareti () altında görünmesi için bir kod bölgesini daraltarak**+** bazı kodu görünümden gizlemeyi seçebilirsiniz. Artı işaretini tıklatarak daraltılmış bir bölgeyi genişletirsiniz. Klavye kullanıcısıysanız, daraltmak ve genişletmek için **Ctrl**+**M M'yi**+**M** seçebilirsiniz. Ayrıca, anahat kenar boşluğundaki herhangi bir satırı çift tıklatarak, kodun hemen solunda görünen bir anahat bölgesini daraltabilirsiniz. Daraltılmış bölgenin üzerinde gezinirken daraltılmış bir bölgenin içeriğini araç ipucu olarak görebilirsiniz.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için [Kaynak editöre (Mac için Visual Studio)](/visualstudio/mac/source-editor)bakın.

Anahat kenar boşluğundaki bölgeler, fareyle kenar boşluğunun üzerinde gezinirken de vurgulanır. Varsayılan vurgulama rengi bazı renk yapılandırmalarında oldukça soluk görünebilir. **Araçları** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkler** > **Katlanabilir Bölge**değiştirebilirsiniz.

Özetlenen kodda çalışırken, üzerinde çalışmak istediğiniz bölümleri genişletebilir, işiniz bittiğinde daraltabilir ve sonra diğer bölümlere taşıyabilirsiniz. Anahat ların görüntülenmesini istemediğinizde, temel kodunuzu rahatsız etmeden anahat bilgilerini kaldırmak için **Anahat Oluşturmayı Durdur** komutunu kullanabilirsiniz.

**Edit** menüsündeki **Geri Al** ve **Yeniden Yap** komutları bu eylemleri etkiler. **Kopyala**, **Kes,** **Yapıştır**ve sürükle ve bırak işlemleri bilgileri anahatolarak tutar, ancak katlanabilir bölgenin durumunu korur. Örneğin, daraltılmış bir bölgeyi kopyaladiğinizde, **Yapıştır** işlemi kopyalanan metni genişletilmiş bir bölge olarak yapıştıracaktır.

> [!CAUTION]
> Ana hatlarını çizdiğinizde, anahat kaybolabilir. Örneğin, silme veya Bul ve Değiştir işlemleri bölgenin sonunu silebilir.

Aşağıdaki komutları **Düzenle** > **Anahat** alt menüsünde bulunabilir.

|||
|-|-|
|Seçimi Gizle|(**Ctrl**+**M**, **Ctrl**+**H**) - Normalde anahat için kullanılamayan seçili `if` bir kod bloğunu daraltır, örneğin bir blok. Özel bölgeyi kaldırmak **için, Akımı Gizlemeyi Durdur** (veya **Ctrl**+**M**, **Ctrl**+**U)** kullanın. Visual Basic'te kullanılamaz.|
|Anahat Genişletmesini Geçiş|- İmleç iç içe çökmüş bir bölümde yattığında, en içteki anahat bölümünün geçerli gizli veya genişletilmiş durumunu tersine çevirir.|
|Tüm Anahatları Geçiş|(**Ctrl**+**M**, **Ctrl**+**L**) - Tüm bölgeleri aynı daraltılmış veya genişletilmiş duruma ayarlar. Bazı bölgeler genişletilir ve bazıları daraltılırsa, daraltılmış bölgeler genişletilir.|
|Anahat Oluşturmayı Durdur|(**Ctrl**+**M**, **Ctrl**+**P**) - Tüm belgenin anahat bilgilerini kaldırır.|
|Akımı Gizlemeyi Durdur|(**Ctrl**+**M**, **Ctrl**+**U**) - Şu anda seçilen kullanıcı tanımlı bölgenin anahat bilgilerini kaldırır. Visual Basic'te kullanılamaz.|
|Tanımlara Daralt|(**Ctrl**+**M**, **Ctrl**+**O**) - Her tür üyeyi daraltıyor.|
|Daraltma\<Bloğu: mantıksal sınır>|(C++) Ekleme noktasını içeren işlevdeki bir bölgeyi daraltıyor. Örneğin, ekleme noktası bir döngüiçinde yatıyorsa, döngü gizlenir.|
|Tüm içinde \<Daraltma: mantıksal yapılar>|(C++) İşlev içindeki tüm yapıları daraltır.|

Genişletmek veya daraltmak istediğiniz metin bölgelerini tanımlamak için Visual Studio SDK'yı da kullanabilirsiniz. Bkz. [Walkthrough: Anahat .](../extensibility/walkthrough-outlining.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Kaynak editör (Visual Studio For Mac)](/visualstudio/mac/source-editor)
