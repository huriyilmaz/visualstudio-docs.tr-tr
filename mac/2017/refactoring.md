---
title: Kodu yeniden düzenleme
description: Visual Studio for Mac'te koduyeniden düzenleme, Kaynak Analizi kullanımı yla basitleştirilmiştir.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985240"
---
# <a name="refactoring"></a>Yeniden Düzenle

Yeniden düzenleme kodu, kodun genel davranışının değişmemesini sağlarken varolan kodu yeniden düzenlemenin, yeniden yapılandırmanın ve netleştirmenin bir yoludur.

Yeniden düzenleme, sizin veya koda atıfta bulunabilecek başka bir geliştirici veya kullanıcı için daha kullanılabilir, okunabilir ve bakımlı hale getirerek daha sağlıklı bir kod tabanı üretir.

Mac'in Microsoft'un açık kaynak kodlayıcı platformu Roslyn ile tümleşmesi için Visual Studio, daha fazla yeniden düzenleme işlemi sağlar.

## <a name="renaming"></a>Yeni -den adlandırma

*Yeniden Adlandırma* yeniden düzenleme komutu, bu tanımlayıcının tüm oluşumlarını bulmak ve değiştirmek için herhangi bir kod tanımlayıcısında (örneğin, bir sınıf adı, özellik adı vb.) kullanılabilir. Bir sembolü yeniden adlandırmak için üzerine sağ tıklayın ve **Refactor > Rename**veya **Cmd + R** tuşu bağlamayı seçin:

![Menü öğeyi yeniden adlandır](media/refactoring-renaming1.png)

Bu, sembolü ve ona yapılan tüm başvuruları vurgular. Yeni bir ad yazmaya başladığınızda, kodunuzdaki tüm başvuruları otomatik olarak değiştirir ve **Enter**tuşuna basarak yeniden adınızı tamamlayabileceğinizi işaret edebilirsiniz:

![Yeniden adlandırma ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Bağlam eylemleri

Bağlam eylemleri, herhangi bir C# kodunu incelemenize ve olası tüm yeniden düzenleme seçeneklerini görmenize olanak sağlar.

**Çözümle** ve **Yeniden Et** bağlam öğeleri, size tüm kullanılabilir Bağlam eylemlerini sağlayacak tek bir Hızlı *Düzeltme öğesinde* birleştirilir:

![Bağlam Öğelerini Görüntüle](media/refactoring-context-action.png)

İçerik eylemlerinden herhangi birinin üzerinde gezinmek, kodunuzdan eklenecek veya kaldırılacak ların önizlemesini sağlar.

Alternatif olarak, **Seçeneğiniz +** Kodunuzun herhangi bir yerine girin tuşuna basabilirsiniz:

![Bağlam öğelerini girin seçeneği](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek **için, Mac > Tercihleri için Visual Studio seçeneklerinde** *açık dosyaların kaynak çözümlemesini etkinleştir'i* > Metin Düzenleyici> Kaynak Analizi'ni seçmeniz gerekir:

![Kaynak çözümlemesini etkinleştirme](media/refactoring-options.png)

Mac > Tercihleri için Visual Studio'ya göz atarak etkinleştirilen veya devre dışı bırakılan 100'den fazla olası eylem vardır **> Kaynak Analizi > C# > Kod Eylemleri'nin** yanındaki kutuyu seçip seçerek veya seçerek:

![C# Kaynak Analizi eylemleri](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Ortak bağlam eylemleri

Çoğunlukla yaygın olarak kullanılan bağlam eylemlerinden bazıları aşağıda açıklanmıştır.

#### <a name="extract-method"></a>Ayıklama metodu

Ayıklama yöntemi yeniden düzenleme işlemi, varolan bir üyede kod seçimini ayıklayarak yeni bir yöntem oluşturmanıza olanak tanır. Bu eylem iki şey yapacaktır:

* Seçili kodu içeren yeni bir yöntem oluşturur
* Seçili kodun olduğu yerde yeni yöntemi çağırır.

##### <a name="example"></a>Örnek

1. Aşağıdaki kodu ekleyin:

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Satırı `double volume = (baseArea * height) / 3;`vurgulayın, üzerine sağ tıklayın ve **Refactor > Extract Method'u**seçin.

3. Kodunuzda yeni yöntemin nereye yerleştirileceğini seçmek için ok tuşlarını kullanın.

#### <a name="encapsulate-field"></a>Alanı kapsülleme

Encapsulate Field işlemi, varolan bir alandan bir özellik oluşturmanıza olanak tanır ve kodunuzu yeni oluşturulan özelliğe başvurmak üzere güncelleştirir. Alanınızı kapsülleyen bir özellik oluşturarak, ortak alanınıza doğrudan erişime izin vermiyorsunuz, bu da diğer nesnelerin alanı değiştiremeyebileceği anlamına geliyor.

Bu eylem aşağıdakileri yapar:

* Erişim değiştiriciyi özel olarak değiştirir.
* Alan için bir getter ve ayarlayıcı oluşturur (alan salt okunur olmadığı sürece, bu durumda yalnızca bir getter oluşturur).

## <a name="source-analysis"></a>Kaynak analizi

Kaynak çözümlemesi, olası hataların ve stil ihlallerinin altını çizerek ve bağlam eylemleri olarak otomatik düzeltmeler sağlayarak kodunuzu anında analiz eder.

Metin düzenleyicisinin sağ tarafındaki kaydırma çubuğunu görüntüleyerek istediğiniz zaman herhangi bir dosya için kaynak çözümlemenin tüm sonuçlarını görüntüleyebilirsiniz:

![Kaynak Analizi kenar çubuğu](media/refactoring-image4a.png)

Üstteki daireyi tıklatırsanız, her öneride, en yüksek önem sorunları ilk olarak göstererek yineleyebilirsiniz. Tek bir sonuç veya satır üzerinde gezinme, bağlam eylemleri ile düzeltilebilir sorunu görüntüler:

![Kaynak Analiz Öğesi](media/refactoring-image5.png)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Windows'ta Visual Studio)](/visualstudio/ide/quick-actions)
- [Refactor kodu (Windows'ta Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)