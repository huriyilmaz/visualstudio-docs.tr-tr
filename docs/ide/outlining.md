---
title: Kod bölgelerini daraltma ve genişletme
description: Ana hat modunda çalışmak için genişletme ve daraltma komutlarını nasıl kullanabileceğinizi Visual Studio
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: fc44968f42f95dcc3a7fa1ce5e80e07a0988496a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636046"
---
# <a name="outlining"></a>Anahat Oluşturma

Kodun bir bölgeyi daraltarak kodun bir artı işareti () altında görüntülendiğinden, bazı kodu görünümden gizlemeyi **+** seçebilirsiniz. Artı işaretine tıklayarak daraltılmış bir bölgeyi genişletersiniz. Klavye kullanıcısıysanız, daraltmak ve genişletmek için **Ctrl** + **M** + **M'yi** seçebilirsiniz. Ayrıca, kodun hemen sol yanında görünen, satır çizgisi kenar boşluğundaki herhangi bir satıra çift tıklayarak bir satır çizgilerini daraltabilirsiniz. Daraltılmış bölgenin üzerine gelindiğinde, daraltılmış bölgenin içeriğini bir araç ipucu olarak görebilir.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Fareyle kenar boşluğun üzerine gelindiğinde, altı çizili kenar boşluğunda bölgeler de vurgulanır. Varsayılan vurgulama rengi bazı renk yapılandırmalarında oldukça belirsiz görünebilir. Bunu Araçlar Seçenekleri Ortam Yazı **Tipleri**  >  **ve**  >  **Renkler**  >  **Daraltılabilir**  >  **Bölgesi'nde değiştirebilirsiniz.**

Ana hatları belirtilen kodda çalışıyorsanız, üzerinde çalışmak istediğiniz bölümleri genişletebilirsiniz, bitirenleri daraltabilir ve ardından diğer bölümlere geçebilirsiniz. Ana hat görüntülenebilir olmasını istediğiniz zaman, temel  kodunuzu bozmadan ana hat bilgilerini kaldırmak için Ana Hat Etmeyi Durdur komutunu kullanabilirsiniz.

Düzenle **menüsündeki** **Geri Al** ve **Tekrarla komutları** bu eylemleri etkiler. **Kopyala,** **Kes**, **Yapıştır** ve sürükle ve bırak işlemleri daraltılabilir bölgenin durumunu değil, anahat bilgilerini korur. Örneğin daraltılmış bir bölgeyi kopyalayıp Yapıştır  işlemi kopyalanan metni genişletilmiş bölge olarak yapıştıracak.

> [!CAUTION]
> Ana hatlı bir bölgeyi değiştirerek ana hatlama kaybolabilir. Örneğin silme veya Bul **ve Değiştir** işlemleri bölgenin sonunu silmeye devam ediyor olabilir.

Aşağıdaki komutlar, AçıklamaYı **Düzenle**  >  **alt menüsünde** bulunabilir.

|Ad|Açıklama|
|-|-|
|Seçimi Gizle|(**Ctrl** + **M**, **Ctrl** H ) - Normalde bir blok gibi, genel olarak kullanılabilir olmayacak seçili bir kod + bloğu `if` daraltıyor. Özel bölgeyi kaldırmak için Geçerli **Gizlemeyi** Durdur (veya **Ctrl** + **M**, **Ctrl** + **U) kullanın.** Şu anda Visual Basic.|
|Altı Çizili Genişletmeyi Değiştir| (**Ctrl** + **M**, **Ctrl** M ) - İmleç iç içe daraltılmış bir bölümde olduğunda en iç içe geçmiş altı çizili bölümün geçerli gizli veya genişletilmiş + durumunu tersine çevirer.|
|Tüm Outlining'i Değiştir|(**Ctrl** + **M**, **Ctrl** + **L**) - Tüm bölgeleri aynı daraltılmış veya genişletilmiş durum olarak ayarlar. Bazı bölgeler genişletilir ve bazıları daraltılmışsa daraltılmış bölgeler genişletilir.|
|Outlining'i Durdurma|(**Ctrl** + **M**, **Ctrl** + **P**) - Belgenin tamamı için tüm genel açıklama bilgilerini kaldırır.|
|Geçerli Gizlemeyi Durdurma|(**Ctrl** + **M**, **Ctrl** + **U**) - Seçili olan kullanıcı tanımlı bölgeye ilişkin temel bilgileri kaldırır. Şu anda Visual Basic.|
|Tanımları Daralt|(**Ctrl** + **M**, **Ctrl** + **O**) - Tüm türlerin üyelerini daraltıyor.|
|Bloğu Daralt:\<logical boundary>|(C++) İşlevde ekleme noktasını içeren bir bölgeyi daraltıyor. Örneğin, ekleme noktası bir döngü içinde yer alan döngü gizlenir.|
|Hepsini Daralt: \<logical structures>|(C++) İşlevin içindeki tüm yapıları daraltıyor.|

Ayrıca, genişletmek veya daraltmak Visual Studio bölgelerini tanımlamak için Visual Studio SDK'sı kullanabilirsiniz. Bkz. [Adım adım kılavuz: Açıklama.](../extensibility/walkthrough-outlining.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Kaynak düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)
