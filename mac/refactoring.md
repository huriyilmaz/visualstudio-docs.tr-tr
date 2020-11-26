---
title: Kodu yeniden düzenleme
description: Mac için Visual Studio ve hızlı eylemleri kullanarak kodu iyileştirme.
author: jmatthiesen
ms.author: jomatthi
ms.date: 07/03/2020
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3892117e5c84a71f258d4e019105fca0a8cf9c5b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189244"
---
# <a name="refactoring"></a>Yeniden Düzenle

Kodu yeniden düzenleme, kodun genel davranışının değişmeyeceğinden emin olmak için mevcut kodu yeniden düzenlemek, yeniden yapılandırmak ve netleştirmek için bir yoldur.

Yeniden düzenleme, bir isteyen kod tabanı üretir, sizin için daha kolay bir şekilde çalışabilir, okunabilir ve sürdürülebilir hale gelir.

Mac için Visual Studio, Microsoft 'un açık kaynaklı .NET derleyicisi platformu ile, daha yeniden düzenleme işlemlerine izin verir.

## <a name="renaming"></a>Adlandırıl

*Yeniden düzenlemeyi yeniden adlandır* komutu herhangi bir kod tanımlayıcısı üzerinde (örneğin, bir sınıf adı, özellik adı vb.), Bu tanımlayıcının tüm oluşumlarını bulmak ve bunları değiştirmek için kullanılabilir. Bir sembolü yeniden adlandırmak için, üzerine sağ tıklayıp **yeniden adlandır...** seçeneğini belirleyin veya **cmd (⌘) + R** anahtar bağlamasını kullanın:

![Menü öğesini yeniden adlandır](media/refactoring-renaming1.png)

Bu, simgeyi ve ona yapılan tüm başvuruları vurgular. Yeni bir ad yazmaya başladığınızda kodunuzdaki tüm başvuruları otomatik olarak değiştirir ve **ENTER** tuşuna basarak yaptığınız değişiklikleri gerçekleştirebilirsiniz:

![Yeniden adlandırma ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="quick-actions-and-refactorings"></a>Hızlı Eylemler ve Yeniden Düzenlemeler

Hızlı Eylemler ve yeniden düzenlemeler kodu tek bir eylemle kolayca yeniden düzenleme, oluşturma veya başka şekilde değiştirme sağlar.

Hızlı eylemler şu Işlemler için kullanılabilir:

* Kod Çözümleyicisi kural ihlali için kod düzeltmesini uygulayın
* Kod Çözümleyicisi kural ihlalini gösterme
* Yeniden düzenleme uygulama (örneğin, satır içi geçici değişken)
* Kod oluştur (örneğin, yerel bir değişken tanıtma)

Hızlı Eylemler, ampullü ampul ![ simgesi ](media/quick-actions-light-bulb-icon.png) veya screwsürücü, ![ screwdriver simgesi ](media/quick-actions-screwdriver-icon.png) simgeleri kullanılarak veya imlecinizin bir eylemin kullanılabildiği bir kod satırında olduğunda ENTER **(⌥)** tuşuna basarak uygulanabilir + **Enter** . ![ ](media/quick-actions-error-light-bulb-icon.png) Bir hata belirten kırmızı renkli bir çizgi varsa ve Visual Studio 'nun bu hata için kullanılabilir bir düzeltilmesi varsa, bir hata ışığı hatası ampul simgesi görürsünüz.

Herhangi bir dilde üçüncü taraflar, bir SDK 'nın parçası olarak özel tanılama ve öneriler sunabilir ve bu kurallara göre Visual Studio Light bulbs hafif.

### <a name="quick-action-icons"></a>Hızlı eylem simgeleri
Hızlı bir eylem kullanılabilir olduğunda görüntülenen simge, düzeltilmesi veya kullanılabilir yeniden düzenleme türü hakkında bir gösterge sağlar. *Screwdriver* ![ screwdriver simge ](media/quick-actions-screwdriver-icon.png) simgesi, yalnızca kodu değiştirecek eylemlerin olduğunu gösterir, ancak bunları kullanmamanız gerekmez. *Sarı* ampul ![ ışığı ampul simgesi simgesi, ](media/quick-actions-light-bulb-icon.png) kodunuzu geliştirmek için yapmanız *gereken* eylemler olduğunu gösterir. *Hata ampulü* ![ hatası ampul simgesi ](media/quick-actions-error-light-bulb-icon.png) simgesi kodunuzda bir hatayı düzelten bir eylem olduğunu gösterir.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya screwsürücüyü görmek için

- Bir düzeltilmesi varsa, fareyi bir hata konumuna getirdiğinizde açık bulbs sünyler görünür.

   ![Fare üzerine gelindiğinde ampul](media/refactoring-lightbulb-hover.png)

- Giriş işaretini hızlı bir eylem veya yeniden düzenlemenin kullanılabildiği bir kod satırına taşıdığınızda, açık bulbs ve screwdrivers, düzenleyicinin sol kenar boşluğunda görüntülenir.

- **Option (⌥)** + Kullanılabilir hızlı eylemlerin ve yeniden düzenlemeler 'in bir listesini görmek için bir satırda herhangi bir yere basın seçeneğini (⌥)**girin** .

![Bağlam öğelerini görüntüle](media/refactoring-context-action.png)

Bağlam eylemlerinin herhangi birinin üzerine gelindiğinde, kodunuzla nelerin ekleneceğini veya hangilerinin kaldırılabileceği hakkında bir önizleme sunulmaktadır.

![Seçenek bağlam öğelerini gir](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek için, seçeneklerde *Açık dosyaların kaynak analizini etkinleştir* ' i seçmeniz gerekir **Mac için Visual Studio > tercihleri > metin Düzenleyicisi > kaynak analizi**:

![Kaynak analizini etkinleştirme](media/refactoring-options.png)

Mac için Visual Studio > tercihlerine göz atarak etkin veya devre dışı bırakılmış olabilecek 100 üzerinde **> kaynak analizi > C# > kod eylemleri** ve eylemin yanındaki kutuyu seçip seçimi kaldır:

![C# kaynak çözümleme eylemleri](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Ortak hızlı eylemler

Ortak [hızlı](/visualstudio/ide/common-quick-actions) eylemler makalesinde ortak hızlı eylemler hakkında daha fazla bilgi edinebilirsiniz.

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
