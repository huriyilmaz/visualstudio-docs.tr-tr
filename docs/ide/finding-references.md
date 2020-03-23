---
title: Kodunuzdaki başvuruları bulma
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4ef16ef88e871778fd4e0c755ffb156c374109
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592041"
---
# <a name="find-references-in-your-code"></a>Kodunuzdaki başvuruları bulma

Kod tabanınız boyunca belirli kod öğelerinin başvurulduğu yeri bulmak için **Tüm Başvuruları Bul** komutunu kullanabilirsiniz. **Tüm Başvuruları Bul** komutu, başvuruları bulmak istediğiniz öğenin bağlam (sağ tık) menüsünde kullanılabilir. Veya klavye kullanıcısıysanız **Shift + F12 tuşuna**basın.

Sonuçlar, öğeyi aradığınız öğenin adı *olan* ** \<başvuru> adlı**bir araç penceresinde görünür. **Başvurular** penceresindeki bir araç çubuğu şunları yapmanızı sağlar:
- Açılan liste kutusundaki aramanın kapsamını değiştirin. Yalnızca değiştirilen belgelere tüm çözüme kadar bakmayı seçebilirsiniz.
- **Kopyala** düğmesini seçerek seçili başvurulan öğeyi kopyalayın.
- Listedeki bir sonraki veya önceki konuma gitmek için düğmeleri seçin veya bunu yapmak için **F8** ve Shift + **F8** tuşlarına basın.
- **Tüm Filtreleri Temizle** düğmesini seçerek döndürülen sonuçlardaki filtreleri kaldırın.
- **Grup'ta** açılan liste kutusuna göre bir ayar seçerek döndürülen öğelerin nasıl gruplandırılacağını değiştirin.
- **Sonuçları Tut** düğmesini seçerek geçerli arama sonuçları penceresini tutun. Bu düğmeyi seçtiğinizde, geçerli arama sonuçları bu pencerede kalır ve yeni arama sonuçları yeni bir araç penceresinde görünür.
- **Tüm Başvuruları Bul** metin kutusuna metin girerek arama sonuçlarındaki dizeleri arayın.

Ayrıca, başvurunun önizlemesini görmek için fareyi herhangi bir arama sonucunun üzerine gezdirebilirsiniz.

![Tüm Başvuruları Bul araç penceresi](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Başvurulara gidin
**Başvurular** penceresindeki başvurulara gitmek için aşağıdaki yöntemleri kullanabilirsiniz:

- Bir sonraki başvuruya gitmek için **F8'e** veya önceki başvuruya gitmek için **Shift + F8** tuşuna basın.
- Bir başvuruda **Enter** tuşuna basın veya kod olarak gitmek için çift tıklatın.
- Bir başvurunun sağ tıklama menüsünde (bağlam menüsü) **Önceki Konuma Git** veya Sonraki Konuma **Git** komutlarını seçin.
- Yukarı **Ok** ve **Aşağı Ok** tuşlarını seçin **(Seçenekler** iletişim kutusunda etkinleştiriliyorsa). Bu işlevselliği etkinleştirmek için menü çubuğunda **Araçlar** > **Seçenekleri** > **Çevre** > **Sekmeleri ve Windows** > **Önizleme Sekmesi'ni**seçin ve ardından önizleme **sekmesinde açılacak yeni dosyalara izin ver'i** seçin ve Sonuçları Bul **kutularında seçili dosyaları önizleyin.**

## <a name="change-reference-groupings"></a>Referans gruplandırmalarını değiştirme
Varsayılan olarak, başvurular projeye göre, sonra da tanım olarak gruplandırılır. Ancak, **Grup'taki** ayarı araç çubuğundaki açılır liste kutusuna göre değiştirerek bu gruplandırma sırasını değiştirebilirsiniz. Örneğin, proje sonra **tanım** tanım varsayılan ayarı itibaren **tanım,** proje , hem de diğer ayarları değiştirebilirsiniz.

**Tanım** ve **Proje** kullanılan iki varsayılan gruplandırmadır, ancak seçili öğenin sağ tıklama veya bağlam menüsünde **Gruplandırma** komutunu seçerek başkalarını ekleyebilirsiniz. Çözümünüzde çok sayıda dosya ve yol varsa, daha fazla gruplandırma eklemek yararlı olabilir.

## <a name="filter-by-reference-type-in-net"></a>.NET'te referans türüne göre filtreleme
C# veya Visual Basic'te, Başvuruları Bul penceresinde ne tür bir başvuru bulduğunu listeleyen bir Tür sütunu bulunur. Bu sütun, sütun üstbilgisinin üzerinde gezinirken görünen filtre simgesine tıklayarak başvuru türüne göre filtre lemek için kullanılabilir. Başvurular Okuma, Yazma, Başvuru, Ad, Ad alanı ve Tür'e göre filtrelenebilir.

![Başvuruları Bul Pencere Türü sütunu ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu gezinme](../ide/navigating-code.md)
