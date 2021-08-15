---
title: Kodu yeniden düzenleme
description: Kod ve hızlı Mac için Visual Studio kullanarak kodu yenidenfining.
author: jmatthiesen
ms.author: jomatthi
ms.date: 07/03/2020
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 77f3c2195e78e3658bd436064f10bc864788421b91488456285a13994f79efe6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121242606"
---
# <a name="refactoring"></a>Yeniden Düzenle

Kodu yeniden düzenleme, mevcut kodu yeniden düzenlemenin, yeniden yapılandırmanın ve netleştirmenin bir yolunu sağlarken kodun genel davranışının değişmesini de sağlar.

Yeniden düzenleme daha sağlıklı bir kod tabanı üretir ve bu da onu sizin veya koda başvuran diğer geliştirici veya kullanıcılar için daha kullanılabilir, okunabilir ve korunabilir hale sağlar.

Mac için Visual Studio Microsoft'un açık kaynak .NET derleyici platformu Roslyn ile tümleşerek daha fazla yeniden düzenleme işlemlerine olanak sağlar.

## <a name="renaming"></a>Yeni -den adlandırma

Yeniden *düzenlemeyi* yeniden adlandırma komutu herhangi bir kod tanımlayıcısında (örneğin, bir sınıf adı, özellik adı vb.) bu tanımlayıcının tüm oluşumlarını bulmak ve bunları değiştirmek için kullanılabilir. Bir simgeyi yeniden adlandırmak için simgeye sağ tıklayın ve Yeniden **Adlandır...** öğesini seçin veya **Cmd (⌘) + R tuş bağlaması** kullanın:

![Menü öğesini yeniden adlandırma](media/refactoring-renaming1.png)

Bu simgeyi ve buna yapılan tüm başvuruları vurgular. Yeni bir ad yazmaya başladığınızda, kodundaki tüm başvuruları otomatik olarak değiştirir ve Enter tuşuna basarak değişikliklerinizi **işebilirsiniz:**

![Yeniden ad ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="quick-actions-and-refactorings"></a>Hızlı Eylemler ve Yeniden Düzenlemeler

Hızlı Eylemler ve Yeniden Düzenleme işlemleri, tek bir eylemle kodu kolayca yeniden düzenlemenizi, oluşturmanizi veya başka bir şekilde değiştirmenizi sağlar.

Hızlı Eylemler şunları yapmak için kullanılabilir:

* Kod çözümleyicisi kural ihlali için kod düzeltmesi uygulama
* Kod çözümleyicisi kural ihlallerini gizleme
* Yeniden düzenleme uygulama (örneğin, satır içi geçici değişken)
* Kod oluşturma (örneğin, bir yerel değişken tanıtma)

Hızlı Eylemler, ampul ampul simgesi veya tornavida tornavida simgesi simgeleri kullanılarak veya imleciniz bir eylemin kullanılabilir olduğu bir kod satırı üzerindeyken ![ ](media/quick-actions-light-bulb-icon.png) Seçenek ![ ](media/quick-actions-screwdriver-icon.png) **(⌥)** + **Enter** tuşuna basarak uygulanabilir. Hataya işaret eden kırmızı bir geçiş varsa ve bu hata için bir düzeltme varsa hata ampulü Visual Studio ampul ![ ](media/quick-actions-error-light-bulb-icon.png) simgesi görüntülenir.

Herhangi bir dil için, üçüncü taraflar sdk'nın bir parçası gibi özel tanılamalar ve öneriler s sağlamanın yanı sıra bu Visual Studio ampulleri kullanabilir.

### <a name="quick-action-icons"></a>Hızlı Eylem Simgeleri
Hızlı Eylem kullanılabilir olduğunda görüntülenen simge, kullanılabilir düzeltmenin veya yeniden düzenlemenin türünü gösterir. *Tornavida* tornavida simgesi simgesi, kodu değiştirmek için kullanabileceğiniz eylemler olduğunu gösterir, ancak bunları ![ ](media/quick-actions-screwdriver-icon.png) mutlaka kullanmamak gerekir. Sarı *ampul ampul* simgesi ![ ](media/quick-actions-light-bulb-icon.png) simgesi, kodunuzu geliştirmek için gereken *eylemler* olduğunu gösterir. Hata *ampulü* ![ hata ampul simgesi ](media/quick-actions-error-light-bulb-icon.png) simgesi, kodundaki bir hatayı düzelten bir eylem olduğunu gösterir.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Bir ampulü veya tornavidayı görmek için

- Bir düzeltme varsa, farenin üzerine bir hatanın üzerine gelindiğinde ampuller aniden görünür.

   ![Fareyle üzerine gelinen ampul](media/refactoring-lightbulb-hover.png)

- Ampuller ve tornavidalar, düzenleyicinin sol kenar boşluğunda, caret'i Hızlı Eylem veya Yeniden Düzenleme'nin kullanılabilir olduğu bir kod satırına taşıyabilirsiniz.

- Kullanılabilir Hızlı Eylemler ⌥ yeniden düzenleme listesini görmek için Seçenek **(⌥)** tuşuna +  basın.

![Bağlam Öğelerini Görüntüleme](media/refactoring-context-action.png)

Bağlam eylemlerinden herhangi biri üzerine gelindiğinde, kodunuzdan nelerin ekli veya kaldırılacaklarının önizlemesi görüntülenir.

![Bağlam öğelerini Girme Seçeneği](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek için,  Kaynak Analizi için Tercihler ve Metin Düzenleyici seçeneklerinde **açık Mac için Visual Studio > kaynak analizini >'> seçmeniz gerekir:**

![Kaynak analizini etkinleştirme](media/refactoring-options.png)

Mac için Visual Studio > Tercihleri > Kaynak Analizi **> C# > Kod** Eylemleri'ne göz atarak ve eylemin yanındaki kutuyu seçerek veya seçimi kaldırarak etkinleştirilen veya devre dışı bırakılabilir 100'den fazla olası eylem vardır:

![C# Kaynak Analizi eylemleri](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Yaygın hızlı eylemler

Yaygın hızlı eylemler hakkında daha fazla bilgi edinmek için Common [Quick Actions makalesine bakın.](/visualstudio/ide/common-quick-actions)

## <a name="source-analysis"></a>Kaynak analizi

Kaynak analizi, olası hataların ve stil ihlallerinin altı çizili olarak ve bağlam eylemleri olarak otomatik düzeltmeler sağlayarak kodunuzu çalışma sırasında analiz eder.

Metin düzenleyicisinin sağ tarafındaki kaydırma çubuğunu görüntüerek istediğiniz zaman herhangi bir dosya için kaynak analizinin tüm sonuçlarını görüntüebilirsiniz:

![Kaynak Analizi kenar çubuğu](media/refactoring-image4a.png)

En üstte daireye tıklarsanız, her öneride en yüksek önem derecesine sahip sorunlar ilk olarak gösteriliyorsa, her öneride döngüye geçabilirsiniz. Tek bir sonucun veya satırın üzerine gelindiğinde, bağlam eylemleriyle düzeltilecek olan sorun görüntülenir:

![Kaynak Analiz Öğesi](media/refactoring-image5.png)

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Visual Studio üzerinde Windows)](/visualstudio/ide/refactoring-in-visual-studio)
