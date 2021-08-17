---
title: Kodunuzdaki başvuruları bulma
description: Kodunuzda belirli kod öğelerine yönelik başvuruları bulmak için tüm başvuruları bul komutunu öğrenin.
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
ms.openlocfilehash: 2a942755238a356032f41e7cff9e5a462196275c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109220"
---
# <a name="find-references-in-your-code"></a>Kodunuzdaki başvuruları bulma

Kodlarınızın tamamında belirli kod öğelerine nerede başvurulduğunu bulmak için **tüm başvuruları bul** komutunu kullanabilirsiniz. **Tüm başvuruları bul** komutu, başvuruları bulmak istediğiniz öğenin bağlam (sağ tıklama) menüsünde mevcuttur. Ya da bir klavye kullanıcısı kullanıyorsanız **SHIFT + F12** tuşlarına basın.

Sonuçlar, **\<element> başvuru** adlı bir araç penceresinde görüntülenir; burada *öğe* , aradığınız öğenin adıdır. **Başvurular** penceresindeki bir araç çubuğu şunları yapmanızı sağlar:
- Açılan liste kutusunda aramanın kapsamını değiştirin. Yalnızca değiştirilen belgelerde, tüm çözüme kadar olan görünümü seçebilirsiniz.
- Seçilen başvurulan öğeyi **Kopyala** düğmesini seçerek kopyalayın.
- Listedeki bir sonraki veya önceki konuma gitmek için düğmeleri seçin veya **F8** **+ SHIFT + F8** tuşlarına basarak bunu yapın.
- **Tüm filtreleri temizle** düğmesini seçerek döndürülen sonuçlarda bulunan filtreleri kaldırın.
- **Gruplama ölçütü:** açılan liste kutusunda bir ayar seçerek döndürülen öğelerin nasıl gruplanacağını değiştirin.
- **Sonuçları tut** düğmesini seçerek geçerli arama sonuçları penceresini tutun. Bu düğmeyi seçtiğinizde, geçerli arama sonuçları bu pencerede kalır ve yeni arama sonuçları yeni bir araç penceresinde görüntülenir.
- **Tüm başvuruları bul** metin kutusuna metin girerek arama sonuçlarının içindeki dizeleri arayın.

Ayrıca, başvurunun bir önizlemesini görmek için fareyi herhangi bir arama sonucunun üzerine de taşıyabilirsiniz.

![Tüm başvuruları bul araç penceresi](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Başvurulara git
**Başvurular** penceresinde başvurulara gitmek için aşağıdaki yöntemleri kullanabilirsiniz:

- Sonraki başvuruya gitmek için **F8** tuşuna basın veya önceki başvuruya gitmek için **SHIFT + F8** tuşlarına basın.
- Bir başvuru üzerinde **ENTER** tuşuna basın veya kodda bu koda gitmek için çift tıklayın.
- Başvurunun sağ tıklama menüsünde (bağlam menüsü) **önceki konuma git** ' i veya **sonraki konum komutlarına git** ' i seçin.
- **Yukarı ok** ve **aşağı ok** tuşlarını ( **Seçenekler** iletişim kutusunda etkinse) seçin. bu işlevi etkinleştirmek için, menü çubuğunda **araçlar**  >  **seçenekler**  >  **ortam**  >  **sekmeleri ve Windows**  >  **önizleme sekmesini** seçin ve ardından **yeni dosyaların önizleme sekmesinde açılmasına izin ver** ' i seçin ve **sonuçları bul kutularında seçili dosyaları önizleyin** .

## <a name="change-reference-groupings"></a>Başvuru gruplamalarını değiştirme
Varsayılan olarak, başvurular projeye göre ve ardından tanıma göre gruplandırılır. Ancak, bu Gruplandırma sırasını, araç çubuğundaki gruplandırma **ölçütü:** açılan liste kutusunda bulunan ayarı değiştirerek değiştirebilirsiniz. örneğin, Project varsayılan ayarından, sonra tanım ' ın **ardından proje**' ye ve diğer ayarlar ' **a** dönüştürebilirsiniz.

**tanım** ve **Project** varsayılan olarak kullanılan iki **gruplandırmadır** , ancak seçili öğenin sağ tıklama veya bağlam menüsünde gruplandırma komutunu seçerek diğerlerini de ekleyebilirsiniz. Çözümünüz çok sayıda dosya ve yol içeriyorsa daha fazla gruplandırma eklemek yararlı olabilir.

## <a name="filter-by-reference-type-in-net"></a>.NET 'te başvuru türüne göre filtrele
C# veya Visual Basic içinde, başvuruları bul penceresi, bulduğu tür başvuruyu listeleyen bir tür sütununa sahiptir. Bu sütun, sütun üst bilgisinin üzerine gelindiğinde görüntülenen filtre simgesine tıklayarak başvuru türüne göre filtrelemek için kullanılabilir. Başvurular okuma, yazma, başvuru, ad, ad alanı ve tür tarafından filtrelenebilir.

![Başvuruları bul pencere türü sütunu ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod gezinme](../ide/navigating-code.md)
