---
title: Kodu yeniden düzenleme
description: Mac için Visual Studio kodu yeniden düzenleme, kaynak analizinin kullanımı aracılığıyla basit hale getirilir.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985240"
---
# <a name="refactoring"></a>Yeniden Düzenle

Kodu yeniden düzenleme, kodun genel davranışının değişmeyeceğinden emin olmak için mevcut kodu yeniden düzenlemek, yeniden yapılandırmak ve netleştirmek için bir yoldur.

Yeniden düzenleme, bir isteyen kod tabanı üretir, sizin için daha kolay bir şekilde çalışabilir, okunabilir ve sürdürülebilir hale gelir.

Mac için Visual Studio, Microsoft 'un açık kaynaklı .NET derleyicisi platformu ile, daha yeniden düzenleme işlemlerine izin verir.

## <a name="renaming"></a>Adlandırıl

*Yeniden düzenlemeyi yeniden adlandır* komutu herhangi bir kod tanımlayıcısı üzerinde (örneğin, bir sınıf adı, özellik adı vb.), Bu tanımlayıcının tüm oluşumlarını bulmak ve bunları değiştirmek için kullanılabilir. Bir sembolü yeniden adlandırmak için, üzerine sağ tıklayın ve **yeniden düzenle > yeniden adlandır**' ı veya **cmd + R** tuşu bağlamasını seçin:

![Menü öğesini yeniden adlandır](media/refactoring-renaming1.png)

Bu, simgeyi ve ona yapılan tüm başvuruları vurgular. Yeni bir ad yazmaya başladığınızda kodunuzdaki tüm başvuruları otomatik olarak değiştirir ve **ENTER**tuşuna basarak yeniden adlandırma tamamlanmanıza işaret edebilirsiniz:

![Yeniden adlandırma ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Bağlam eylemleri

Bağlam eylemleri herhangi bir C# kodunu incelemenizi sağlar ve tüm olası yeniden düzenleme seçeneklerini görürsünüz.

**Çözümle** ve yeniden **düzenleme** bağlam öğeleri, size tüm kullanılabilir bağlam eylemlerini sağlayacak tek bir *hızlı düzelme...* öğesi içinde birleştirilir:

![Bağlam öğelerini görüntüle](media/refactoring-context-action.png)

Bağlam eylemlerinin herhangi birinin üzerine gelindiğinde, kodunuzla nelerin ekleneceğini veya hangilerinin kaldırılabileceği hakkında bir önizleme sunulmaktadır.

Alternatif olarak, kodunuzda herhangi bir yere **ENTER + ENTER** tuşuna basabilirsiniz:

![Seçenek bağlam öğelerini gir](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek için, seçeneklerde *Açık dosyaların kaynak analizini etkinleştir* ' i seçmeniz gerekir **Mac için Visual Studio > tercihleri > metin Düzenleyicisi > kaynak analizi**:

![Kaynak analizini etkinleştirme](media/refactoring-options.png)

Mac için Visual Studio > tercihlerine göz atarak etkin veya devre dışı bırakılmış olabilecek 100 üzerinde **> kaynak analizi > C# > kod eylemleri** ve eylemin yanındaki kutuyu seçip seçimi kaldır:

![C# kaynak çözümleme eylemleri](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Ortak bağlam eylemleri

Yaygın olarak kullanılan bazı bağlam eylemleri aşağıda açıklanmaktadır.

#### <a name="extract-method"></a>Ayıklama metodu

Metodu Ayıkla yeniden düzenleme işlemi, varolan bir üyede bir kod seçimini ayıklayarak yeni bir yöntem oluşturmanıza olanak sağlar. Bu eylem iki şeyi yapar:

* Seçilen kodu içeren yeni bir yöntem oluşturur
* Seçili kodun olduğu yerde yeni yöntemi çağırır.

##### <a name="example"></a>Örnek

1. Şu kodu ekleyin:

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

2. Çizgiyi vurgulayın `double volume = (baseArea * height) / 3;` , üzerine sağ tıklayın ve **yöntemi Ayıkla > yeniden Düzenle**' yi seçin.

3. Yeni yöntemin kodunuza yerleştirilmesi gereken yeri seçmek için ok tuşlarını kullanın.

#### <a name="encapsulate-field"></a>Alanı kapsülleme

Alanı Yalıtma işlemi, mevcut bir alandan bir özellik oluşturmanıza ve kodunuzu yeni oluşturulan özelliğe başvuracak şekilde günceletmenize olanak tanır. Alanınızı kapsülleyen bir özellik oluşturarak, ortak alana doğrudan erişim izni verilmez, yani diğer nesneler bunu değiştiremeyeceği anlamına gelir.

Bu eylem şunları yapılır:

* Erişim değiştiricisini özel olarak değiştirir.
* Alan için bir alıcı ve ayarlayıcı üretir (alan salt okunurdur, bu durumda yalnızca bir alıcı oluşturur).

## <a name="source-analysis"></a>Kaynak analizi

Kaynak analizi, olası hataların ve stil ihlallerinin altını ve bağlam eylemleri olarak otomatik düzeltmeler sağlayarak kodunuzu anında analiz eder.

Herhangi bir dosya için kaynak analizinin tüm sonuçlarını, istediğiniz zaman, metin düzenleyicisinin sağ tarafındaki kaydırma çubuğunu görüntüleyerek görüntüleyebilirsiniz:

![Kaynak çözümleme kenar çubuğu](media/refactoring-image4a.png)

Üstteki daireye tıkladığınızda, en yüksek önem derecesine sahip olan ilk öneri arasında yineleme yapabilirsiniz. Tek bir sonucun veya satırın üzerine gelindiğinde sorun görüntülenir ve bu, bağlam eylemleri aracılığıyla düzeltilenebilir:

![Kaynak analiz öğesi](media/refactoring-image5.png)

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı eylemler (Windows üzerinde Visual Studio)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Windows üzerinde Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)