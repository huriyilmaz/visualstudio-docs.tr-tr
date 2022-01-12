---
title: Unity için Visual Studio Araçları | Microsoft Docs
description: Unity ile platformlar arası oyunlar ve uygulamalar geliştirmenize yardımcı olan ücretsiz bir Visual Studio uzantısı olan Unity için Visual Studio Araçları hakkında genel bakışı okuyun.
ms.date: 12/10/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: overview
ms.assetid: 6cabc626-5310-4622-a743-210a9abb5535
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 6512154e53c1ac1e77071e1aac01e09e90cbc120
ms.sourcegitcommit: 2a4744fb312396d36086dd59fd55ab741ae8e106
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/28/2021
ms.locfileid: "135575921"
---
# <a name="visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları
![Oyun çalmak için bir bilgisayarın, oyun denetleyicisinin ve simgelerinin ekran görüntüsü.](../media/hero.png)

## <a name="overview"></a>Genel Bakış
Unity için Visual Studio Araçları, unity C# betikleri yazmayı ve hata ayıklamayı geliştiren ve unity projeleriyle çalışan zengin bir özellik kümesi içerir.

* Unity projeleri için ayarlanmış bir hata ayıklayıcı kullanarak kodu sorun giderme, İnceleme ve araştırma.
* Unity 'ye özgü IntelliSense kod tamamlama ile Unity betiklerini hızlıca bulun ve yazın.
* Unity belgelerine hızlıca erişerek yazdığınız kod hakkında daha fazla bilgi edinin.
* Unity betikleri için en iyi yöntemleri izleyen yeniden düzenleme seçenekleriyle daha iyi bir kod yazın.
* Unity altyapısının, ileti işlevleri ve varlık kullanımları için CodeLens ipuçlarıyla kodunuzu nasıl çağırıyor olduğunu belirleme.
* Çok [daha fazla](#features).

## <a name="available-for-windows-and-macos"></a>Windows ve macos için kullanılabilir
:::zone pivot="windows"
Unity için Visual Studio Araçları ücretsiz olarak kullanılabilir ve Visual Studio 2017 Community, Professional ve Enterprise ve daha yeni bir sürümü destekler. [Visual Studio en son sürümünü indirip kullanmanızı öneririz.](https://visualstudio.microsoft.com/downloads/)
:::zone-end
:::zone pivot="macos"
Unity için Visual Studio Araçları ücretsiz olarak kullanılabilir ve her Mac için Visual Studio 2017 ve daha yeni yüklemesinde bulunabilir. [Mac için Visual Studio en son sürümünü indirip kullanmanızı öneririz.](https://visualstudio.microsoft.com/downloads/)
:::zone-end

[Unity için araçları kullanmaya](getting-started-with-visual-studio-tools-for-unity.md) başlarken Unity için Visual Studio Araçları ziyaret edin. Yükleme ve kurulum hakkında daha fazla bilgi için.

### <a name="supported-unity-versions"></a>Desteklenen Unity sürümleri
#### <a name="visual-studio-editor-unity-package"></a>Visual Studio düzenleyicisi Unity paketi
unity 2020,1 ve üzeri, Visual Studio ve Mac için Visual Studio gibi harici düzenleyici araçları için unity paketi gerektirir. [Bu değişiklikler hakkında daha fazla bilgi edinmek Için Unity blog gönderisine bakın.](https://unity.com/releases/2020-1/programmer-tools#verified-ide-packages-now-include-visual-studio)

[başlarken bölümü](getting-started-with-visual-studio-tools-for-unity.md) Visual Studio düzenleyicisi paketinin yapılandırması hakkında daha fazla bilgi içerir.

Visual Studio düzenleyicisi paketinin en son sürümü önerilir.

:::zone pivot="windows"

|Visual Studio  |Minimum Unity sürümü|En düşük paket sürümü|
|---------------|---------------------|-----------------------|
|2022           |Unity 2019,4         |Visual Studio düzenleyicisi 2.0.11|
|2019           |Unity 2017,4         |Visual Studio düzenleyicisi 2.0.0|
|2017           |Önerilmez      |Yok
:::zone-end
:::zone pivot="macos"

|Mac için Visual Studio |Minimum Unity sürümü|En düşük paket sürümü|
|---------------|---------------------|-----------------------|
|2022           |Unity 2019,4         |Visual Studio düzenleyicisi 2.0.11|
|2019           |Unity 2017,4         |Visual Studio düzenleyicisi 2.0.0|
|2017           |Önerilmez      |Yok
:::zone-end

## <a name="features"></a>Özellikler
### <a name="unity-event-functions"></a>Unity olay Işlevleri
`Start` `Update` `OnCollisionEnter` IntelliSense tarafından desteklenen otomatik Tamam önerilerini kullanarak birkaç tuş vuruşu gibi Unity olay işlevlerini hızla ve doğru şekilde ekleyin. 

:::zone pivot="windows"
![Onçarpışsionenter gösteren IntelliSense iletişim kutusunun ekran görüntüsü.](../media/vs/intellisense-example.png)
:::zone-end
:::zone pivot="macos"
⌘ + SHIFT + d kullanarak birden çok Unity olay Işlevi ve yorumları için kod oluşturun.
:::zone-end

Hızlı çözüm önerileri ile el ile eklenen olay Işlevlerinde parametre hatalarını hızlıca düzeltin.

:::zone pivot="windows"
:::zone-end
:::zone pivot="macos"
:::zone-end

### <a name="high-performance-debugger"></a>Yüksek performanslı hata ayıklayıcı
Unity için Visual Studio Araçları, Visual Studio beklemeniz gereken güçlü [hata ayıklama](using-visual-studio-tools-for-unity.md#unity-debugging) özelliklerini destekler:

* Koşullu kesme noktaları da dahil olmak üzere kesme noktaları ayarlayın.
* İzleme penceresi karmaşık ifadeleri değerlendirin.
* Değişkenlerin ve bağımsız değişkenlerin değerini inceleyin ve değiştirin.
* Karmaşık nesneler ve veri yapıları hakkında detaya gidin.

![bir kesme noktasında durdurulan Visual Studio ekran görüntüsü, değişkenleri inceliyor.](../media/vs/debugging-inspecting.png)

### <a name="quick-fixes-and-refactoring-suggestions"></a>Hızlı düzeltmeler ve yeniden düzenleme önerileri
Visual Studio Unity projelerinin derinlemesine anlaşılmasına sahip en iyi uygulamaları yakalayan daha iyi bir kod yazın.

![comparetag ile dize karşılaştırmayı yeniden düzenleme Visual Studio ekran görüntüsü.](../media/vs/unity-diagnostics.png)

:::zone pivot="windows"
### <a name="codelens-hints"></a>CodeLens ipuçları
Unity varlıklarından örtük çağrılar gösteren CodeLens ipuçlarından yararlanarak kodun nerede çağrıldığını belirler. Örtük çağrıların listesini görmek için ipucunu seçin. Belirli bir çağrının seçilmesi, doğrudan Unity düzenleyicideki nesnesine gider.

Her Unity olay Işlevine yönelik ipuçlarıyla kodunuzu Unity yöntemlerinden hızlıca ayırt edin.

 ![Unity betiği ve Unity Iletisi için CodeLens ipuçlarını gösteren yeni betiğin ekran görüntüsü.](../media/vs/codelens-support.png)
:::zone-end

:::zone pivot="windows"
### <a name="unity-project-explorer"></a>Unity Project gezgini
Proje dosyalarını Unity düzenleyicisinde hiyerarşi penceresiyle eşleşen bir şekilde görüntüleyin.

![Unity Project Explorer 'ın ekran görüntüsü.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
### <a name="unity-project-view"></a>Unity proje görünümü
Mac için Visual Studio, proje dosyalarını Unity düzenleyicideki hiyerarşi penceresiyle eşleşen bir şekilde otomatik olarak görüntüler.

:::zone-end

### <a name="unity-documentation"></a>Unity belgeleri
Kod incelenirken Unity belgelerini doğrudan araç ipuçlarında görüntüleyin.

:::zone pivot="windows"
![Araç ipuçlarında Unity belgelerinin ekran görüntüsü.](../media/vs/visual-studio-tools-unity-documentation-tooltips.png)
:::zone-end
:::zone pivot="macos"

:::zone-end

Bir sınıf veya yöntem adını vurgulayarak ve sonra yardım > Unity API başvurusu menü öğesini seçerek Unity belgelerini hızlıca arayın.

### <a name="support-for-shaders"></a>Gölgelendiriciler için destek
Gölgelendirici dosyaları için sözdizimi vurgulama ve otomatik tamamlanma. 

### <a name="support-for-assembly-definition-files"></a>Derleme tanımı dosyaları için destek
Unity birleştirici tanımı (. asmdef) dosyalarını anahtar sözcük renklendirme ve tamamlarla birlikte Visual Studio doğrudan düzenleyin.

:::zone pivot="macos"
### <a name="run-and-debug-unit-tests"></a>Birim testlerini çalıştırma ve hata ayıklama
birim testlerini doğrudan Mac için Visual Studio yazma, çalıştırma ve hata ayıklama.

:::zone-end

### <a name="automatically-refresh-unity-assets"></a>Unity varlıklarını otomatik olarak Yenile
Unity ve Visual Studio arasında daha az zaman harcaın ve geriye doğru geçiş yapın. Dosyalar kaydedildiğinde koddaki değişiklikler Unity 'de otomatik olarak güncelleştirilir.
