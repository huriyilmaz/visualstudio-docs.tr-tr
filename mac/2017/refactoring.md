---
title: Kodu yeniden düzenleme
description: Kaynak analizinde kodu Mac için Visual Studio düzenleme, Kaynak Analizi'nin kullanımıyla basit bir şekilde yapılır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962192"
---
# <a name="refactoring"></a>Yeniden Düzenle

Kodu yeniden düzenleme, mevcut kodu yeniden düzenlemenin, yeniden yapılandırmanın ve netleştirmenin bir yolunu sağlarken kodun genel davranışının değişmesini de sağlar.

Yeniden düzenleme daha sağlıklı bir kod tabanı üretir ve bu da onu sizin veya koda başvuran diğer geliştirici veya kullanıcılar için daha kullanılabilir, okunabilir ve korunabilir hale sağlar.

Mac için Visual Studio Microsoft'un açık kaynak .NET derleyici platformu Roslyn ile tümleşerek daha fazla yeniden düzenleme işlemlerine olanak sağlar.

## <a name="renaming"></a>Yeni -den adlandırma

Yeniden *düzenlemeyi* yeniden adlandırma komutu herhangi bir kod tanımlayıcısında (örneğin, bir sınıf adı, özellik adı vb.) bu tanımlayıcının tüm oluşumlarını bulmak ve bunları değiştirmek için kullanılabilir. Bir simgeyi yeniden adlandırmak için simgesine sağ tıklayın ve Yeniden Adlandır'ı **veya** Cmd + R > yeniden **adlandır'ı** seçin:

![Menü öğesini yeniden adlandırma](media/refactoring-renaming1.png)

Bu simgeyi ve buna yapılan tüm başvuruları vurgular. Yeni bir ad yazmaya başladığınızda, kodundaki tüm başvurular otomatik olarak değişir ve Enter tuşuna basarak yeniden adlandırmayı tamamladığınızda sinyal **gönderebilirsiniz:**

![Yeniden ad ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Bağlam eylemleri

Bağlam eylemleri, tüm C# kodunu incelemeniz ve tüm olası yeniden düzenleme seçeneklerini görmeniz için size olanak sağlar.

Bağlam **öğelerini** **Çözümle ve** Yeniden Düzenleme tek bir *Hızlı Düzeltme...* öğesinde bir araya geldi. Bu öğe size tüm kullanılabilir Bağlam eylemlerini sağlar:

![Bağlam Öğelerini Görüntüleme](media/refactoring-context-action.png)

Bağlam eylemlerinden herhangi biri üzerine gelindiğinde, kodunuzdan nelerin ekli veya kaldırılacaklarının önizlemesi görüntülenir.

Alternatif olarak, kodunuzun herhangi **bir yerinde Seçenek + Enter** tuşlarına basabilirsiniz:

![Bağlam öğelerini Girme Seçeneği](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek için,  Kaynak Analizi'nde Tercihler ve Metin Düzenleyici Mac için Visual Studio > **seçeneklerinde Açık dosyaların > analizini > seçmeniz gerekir:**

![Kaynak analizini etkinleştirme](media/refactoring-options.png)

Mac için Visual Studio > Tercihleri > Kaynak Analizi **> C# > Kod** Eylemleri'ne göz atarak ve eylemin yanındaki kutuyu seçerek veya seçimi kaldırarak etkinleştirilen veya devre dışı bırakılabilir 100'den fazla eylem önerilebilir:

![C# Kaynak Analizi eylemleri](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Yaygın bağlam eylemleri

Yaygın olarak kullanılan bağlam eylemlerinin bazıları aşağıda açıklanmıştır.

#### <a name="extract-method"></a>Ayıklama metodu

Ayıklama yöntemi yeniden düzenleme işlemi, mevcut bir üyede bir kod seçimi ayıklaarak yeni bir yöntem oluşturmanıza olanak sağlar. Bu eylem iki işlem yapar:

* Seçilen kodu içeren yeni bir yöntem oluşturur
* Seçilen kodun bulunduğu yerde yeni yöntemi çağıran.

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

2. satırına `double volume = (baseArea * height) / 3;` vurgulayın, satırına sağ tıklayın ve Ayıklama Yöntemi **için yeniden > seçin.**

3. Ok tuşlarını kullanarak yeni yöntemin kodunuza yerleştirilmleri gereken yeri seçin.

#### <a name="encapsulate-field"></a>Alanı kapsülleme

Alan Kapsülle işlemi, mevcut bir alandan bir özellik oluşturmanıza olanak sağlar ve kodunuzu yeni oluşturulan özelle ilgili başvuru olarak güncelleştirmenize olanak sağlar. Alanınızı kapsüllerken bir özellik oluşturarak, genel alanınıza doğrudan erişime izin verirsiniz, yani diğer nesneler bunu değiştiremez.

Bu eylem şunları yapar:

* Erişim değiştiricisini özel olarak değiştirir.
* Alan için bir alıcı ve ayarıcı üretir (alan salt okunur değilse, bu durumda yalnızca bir getter oluşturulur).

## <a name="source-analysis"></a>Kaynak analizi

Kaynak analizi, olası hataların ve stil ihlallerinin altı çizerek ve bağlam eylemleri olarak otomatik düzeltmeler sağlayarak kodunuzu çalışma sırasında analiz eder.

Metin düzenleyicisinin sağ tarafındaki kaydırma çubuğunu görüntüerek istediğiniz zaman herhangi bir dosya için kaynak analizinin tüm sonuçlarını görüntüebilirsiniz:

![Kaynak Analizi kenar çubuğu](media/refactoring-image4a.png)

En üstte daireye tıklarsanız, her öneride en yüksek önem derecesine sahip sorunlar ilk olarak gösteriliyorsa, her öneride döngüye geçabilirsiniz. Tek bir sonucun veya satırın üzerine gelindiğinde, bağlam eylemleri aracılığıyla düzeltilecek sorun görüntülenir:

![Kaynak Analiz Öğesi](media/refactoring-image5.png)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Visual Studio üzerinde Windows)](/visualstudio/ide/refactoring-in-visual-studio)