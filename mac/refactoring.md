---
title: Kodu yeniden düzenleme
description: Mac için Visual Studio'u kullanarak kodu ve hızlı işlemleri rafine etme.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 5a87b87f3a14462daec1e069fe222164818d2a19
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691291"
---
# <a name="refactoring"></a>Yeniden Düzenle

Yeniden düzenleme kodu, kodun genel davranışının değişmemesini sağlarken varolan kodu yeniden düzenlemenin, yeniden yapılandırmanın ve netleştirmenin bir yoludur.

Yeniden düzenleme, sizin veya koda atıfta bulunabilecek başka bir geliştirici veya kullanıcı için daha kullanılabilir, okunabilir ve bakımlı hale getirerek daha sağlıklı bir kod tabanı üretir.

Mac'in Microsoft'un açık kaynak kodlayıcı platformu Roslyn ile tümleşmesi için Visual Studio, daha fazla yeniden düzenleme işlemi sağlar.

## <a name="renaming"></a>Yeni -den adlandırma

*Yeniden Adlandırma* yeniden düzenleme komutu, bu tanımlayıcının tüm oluşumlarını bulmak ve değiştirmek için herhangi bir kod tanımlayıcısında (örneğin, bir sınıf adı, özellik adı vb.) kullanılabilir. Bir sembolü yeniden adlandırmak için üzerine sağ tıklayın ve **Yeniden Adlandır'ı seçin...** veya **Cmd (3) + R** tuş bağlamayı kullanın:

![Menü öğeyi yeniden adlandır](media/refactoring-renaming1.png)

Bu, sembolü ve ona yapılan tüm başvuruları vurgular. Yeni bir ad yazmaya başladığınızda, kodunuzdaki tüm başvuruları otomatik olarak değiştirir ve **Enter**tuşuna basarak değişikliklerinizi gerçekleştirebilirsiniz:

![Yeniden adlandırma ve tanımlayıcı](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Hızlı eylemler

Hızlı Eylemler, kodu tek bir eylemle kolayca yeniden düzenlemenize, oluşturmanıza veya başka bir şekilde değiştirmenize izin sağlar.

Hızlı Eylemler için kullanılabilir:

* Kod çözümleyici kural ihlali için kod düzeltmesi uygulama
* Kod çözümleyicikural ihlalini bastırma
* Yeniden düzenleme uygulayın (örneğin, geçici bir değişken inline)
* Kod oluşturma (örneğin, yerel bir değişken tanıtın)

Hızlı ![İşlemler ampul ampul simgesi](media/quick-actions-light-bulb-icon.png) veya tornavida ![simgeleri](media/quick-actions-screwdriver-icon.png) kullanılarak veya imleç bir eylem kullanılabilir kod satırında olduğunda Seçenek **(3)**+**Girin** tuşuna basarak uygulanabilir. Bir hata gösteren kırmızı ![bir dalgalı](media/quick-actions-error-light-bulb-icon.png) varsa bir hata ampul ampul simge görürsünüz ve Visual Studio bu hata için kullanılabilir bir düzeltme vardır.

Herhangi bir dil için, üçüncü taraflar özel tanılama ve öneriler sağlayabilir, örneğin bir SDK'nın bir parçası olarak, ve Visual Studio ampuller bu kurallara göre yanar.

### <a name="quick-action-icons"></a>Hızlı Eylem Simgeleri
Hızlı Eylem kullanılabilir olduğunda görünen simge, kullanılabilen düzeltme veya yeniden düzenleme türünü gösterir. *Tornavida* ![simgesi](media/quick-actions-screwdriver-icon.png) simgesi, kodu değiştirmek için kullanılabilir eylemler olduğunu gösterir, ancak bunları mutlaka kullanmamalısınız. *Sarı ampul* ![ampul simgesi,](media/quick-actions-light-bulb-icon.png) kodunuzu geliştirmek için yapmanız *gereken* eylemler olduğunu gösterir. Hata ![ *ampulü* hata ampul](media/quick-actions-error-light-bulb-icon.png) simge simgesi, kodunuzda bir hatayı düzelten bir eylem olduğunu gösterir.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Ampul veya tornavida görmek için

- Düzeltme varsa, fareyi bir hatanın bulunduğu yerde gezdiğinizde ampuller kendiliğinden görünür.

   ![Fare havada gezinen ampul](media/refactoring-lightbulb-hover.png)

- Ampuller ve tornavidalar, bakıcıyı Hızlı İşlemin kullanılabildiği bir kod satırına taşıdığınızda editörün sol kenar boşluğunda görünür.

- **Seçenek (3)**+Tuşuna basın, kullanılabilir Hızlı Eylemlerin ve yeniden düzenlemelistesinin listesini görmek için bir satırın herhangi bir yerine**girin.**

![Bağlam Öğelerini Görüntüle](media/refactoring-context-action.png)

İçerik eylemlerinden herhangi birinin üzerinde gezinmek, kodunuzdan eklenecek veya kaldırılacak ların önizlemesini sağlar.

![Bağlam öğelerini girin seçeneği](media/refactoring-image2a.png)

Bu seçenekleri etkinleştirmek **için, Mac > Tercihleri için Visual Studio seçeneklerinde** *açık dosyaların kaynak çözümlemesini etkinleştir'i* > Metin Düzenleyici> Kaynak Analizi'ni seçmeniz gerekir:

![Kaynak çözümlemesini etkinleştirme](media/refactoring-options.png)

Mac > Tercihleri için Visual Studio'ya göz atarak etkinleştirilen veya devre dışı bırakılan 100'den fazla olası eylem vardır **> Kaynak Analizi > C# > Kod Eylemleri'nin** yanındaki kutuyu seçip seçerek veya seçerek:

![C# Kaynak Analizi eylemleri](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Sık karşılaşılan hızlı eylemler

[Ortak Hızlı Eylemler](/visualstudio/ide/common-quick-actions) makalesinde sık kullanılan hızlı eylemler hakkında daha fazla bilgi edinebilirsiniz.

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