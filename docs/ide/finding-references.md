---
title: Kodunuzdaki başvuruları bulma
description: Kodundaki belirli kod öğelerine başvuru bulmak için Tüm Başvuruları Bul komutunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2ac1b2af6f4f664802cecc64e1cb1bddec251d23d62bc14aa79b2c31feef87ec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121373328"
---
# <a name="find-references-in-your-code"></a>Kodunuzdaki başvuruları bulma

Kod tabanınız **genelinde belirli kod öğelerine** nerede başvurul olduğunu bulmak için Tüm Başvuruları Bul komutunu kullanabilirsiniz. Tüm **Başvuruları Bul** komutu, başvuruları bulmak istediğiniz öğenin bağlam (sağ tıklama) menüsünde kullanılabilir. Veya klavye kullanıcısıysanız Shift **+ F12 tuşlarına basın.**

Sonuçlar **\<element> references** adlı bir araç penceresinde *görünür;* burada öğe, aramakta olduğunu öğenin adıdır. Başvurular penceresindeki **bir araç çubuğu** şunları sağlar:
- Açılan liste kutusunda aramanın kapsamını değiştirme. Çözümün tamamına kadar yalnızca değiştirilmiş belgelere bakabilirsiniz.
- Kopyala düğmesini seçerek, seçilen başvurulan **öğeyi** kopyalayın.
- Listede bir sonraki veya önceki konuma gitmek için düğmeleri seçin veya bunu yapmak için **F8** ve **Shift + F8** tuşlarına basın.
- Tüm Filtreleri Temizle düğmesini seçerek döndürülen sonuçlarda **yer alan filtreleri** kaldırın.
- Döndürülen öğelerin Grupla: açılan liste kutusunda bir ayar **seçerek nasıl** gruplandıklarını değiştirebilirsiniz.
- Sonuçları Tut düğmesini seçerek geçerli arama sonuçları **penceresini tutun.** Bu düğmeyi seçerseniz geçerli arama sonuçları bu pencerede kalır ve yeni arama sonuçları yeni bir araç penceresinde görünür.
- Arama Tüm Başvuruları Bul metin kutusuna metin girerek **arama sonuçlarında dizeleri** bulun.

Başvuru önizlemesini görmek için fareyi herhangi bir arama sonuçlarının üzerine de ebilirsiniz.

![Tüm Başvuruları Bul araç penceresi](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Başvurulara gidin
Başvurular penceresinde başvurulara gitmek için aşağıdaki yöntemleri **kullanabilirsiniz:**

- Sonraki başvuruya gitmek için **F8'e** veya önceki başvuruya gitmek için **Shift + F8'e** basın.
- Kodda gitmek için başvuruda **Enter** tuşuna basın veya çift tıklayın.
- Başvuruya yönelik sağ tıklama menüsünde (bağlam menüsü) Önceki Konuma Git veya Sonraki **Konuma** **Git komutlarını** seçin.
- Yukarı Ok **ve** Aşağı **Ok tuşlarını** seçin (Seçenekler iletişim kutusunda **etkinse).** Bu işlevi etkinleştirmek için, menü çubuğunda Araçlar Seçenekler Ortam Sekmeleri'ne tıklayın ve Windows Önizleme Sekmesi'ne tıklayın ve ardından Önizleme sekmesinde Yeni dosyaların açılmasına izin ver ve Sonuçları Bul kutularında seçili dosyaları önizle'yi  >    >    >    >  seçin.  

## <a name="change-reference-groupings"></a>Başvuru gruplamalarını değiştirme
Varsayılan olarak, başvurular projeye ve ardından tanıma göre gruplandırıldı. Ancak, araç çubuğundaki Gruplama: açılan liste  kutusunda ayarı değiştirerek bu gruplama sıralamalarını değiştirebilirsiniz. Örneğin, bunu varsayılan ayardan tanım Project tanım **olarak,** sonra **da proje** olarak ve diğer ayarlarla değiştirebilirsiniz.

**Tanım** **ve Project** kullanılan iki varsayılan gruplamadır, ancak seçilen öğenin  sağ tıklama veya bağlam menüsündeKi Gruplama komutunu seçerek başkalarını ekleyebilirsiniz. Çözümde çok fazla dosya ve yol varsa daha fazla gruplama eklemek yararlı olabilir.

## <a name="filter-by-reference-type-in-net"></a>.NET'te başvuru türüne göre filtreleme
C# veya Visual Basic penceresinde bulunan başvuru türünü listeleye bir Kind sütunu bulunur. Bu sütun, sütun üst bilgisi üzerine gelindiğinde görüntülenen filtre simgesine tıklayarak başvuru türüne göre filtrelemek için kullanılabilir. Başvurular Okuma, Yazma, Başvuru, Ad, Ad Alanı ve Türe göre filtrelenmiş olabilir.

![Başvuruları Bul Penceresi Türü sütunu ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodda gezinme](../ide/navigating-code.md)
