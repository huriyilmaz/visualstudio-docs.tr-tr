---
title: Yük Testi Senaryosu Özellikleri
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2011438f1fcb0230cde0de527216456553e7c64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584445"
---
# <a name="load-test-scenario-properties"></a>Yük testi senaryo özellikleri

Yük testi gereksinimlerinizi karşılamak için Visual Studio'daki yük testi özellik ayarlarınızı değiştirin. Bu makalede, çeşitli yük testi senaryo özellikleri kategoriye göre listeler.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Genel

|Özellik|Tanım|
|-|----------------|
|**Adı**|Senaryonun adı.|

## <a name="mix"></a>Karışık

|Özellik|Tanım|
|-|----------------|
|**Tarayıcı Karışımı**|Yük testi için web tarayıcısı karışımını belirtir. Farklı web tarayıcısı türlerini ve bunların yük dağıtımlarını belirtebilirsiniz.<br /><br />**Tarayıcı Karıştır'ı Edit** iletişim kutusunu açmak için elips **(...)** düğmesini seçin ve yükleme testinde web tarayıcısı türlerini seçmek için **Ekle** ve **Kaldır'ı** kullanın.<br /><br />Daha fazla bilgi için [bkz.](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Ağ Karışımı**|Yük testi için ağ karışımını belirtir. Hangi ağ türlerinin dahil edilen ve yük dağılımlarını belirtebilirsiniz.<br /><br />**Ağ Karışımını Edit** iletişim kutusunu açmak için elips **(...)** düğmesini seçin ve yük testindeki ağ türlerini seçmek için **Ekle** ve **Kaldır'ı** kullanın.<br /><br />Daha fazla bilgi için [bkz.](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Test Karışımı**|Yük testi için web performansını ve birim test karışımını belirtir. Hangi testlerin dahil edilen ve yük dağılımını belirtebilirsiniz.<br /><br />**Test Mix'i Edit** iletişim kutusunu açmak için elips **(...)** düğmesini seçin ve yük testindeki testleri seçmek için **Ekle** ve **Kaldır'ı** kullanın.<br /><br />Daha fazla bilgi için, [bir yük testi senaryosu için test karışımını düzenleme.](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Test Mix Türü**|Yük testi için test karışımı modelini belirtir.<br /><br />**Test Mix'i Edit** iletişim kutusunu açmak için elips **(...)** düğmesini seçin ve yükleme testinde kullanılacak test karışımı modelini seçmek için **Test mix modelinin** altındaki açılır modeli kullanın.<br /><br />Daha fazla bilgi için [metin karışımı modellerini edit'e](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)bakın.|

## <a name="options"></a>Seçenekler

|Özellik|Tanım|
|-|----------------|
|**Kullanılacak Aracılar**|Yükleme testini uzaktan çalıştırıyorsanız, senaryonuzun kullanmasını istediğiniz aracıları belirtir. Örneğin, performans eğilimlerini analiz ederken tutarlılığı korumak için belirli bir aracı kümesi belirtmek isteyebilirsiniz. Ayrıca, aracılar coğrafi olarak dağıtılabilir, böylece çalıştırdıkları komut dosyaları yla aracının bulunduğu yer arasında bir benzerlik vardır.<br /><br />Aracılar virgülle ayrılmalıdır, örneğin "**Agent1, Agent2, Agent3**". Özelliği boş bırakmak, senaryonun kullanılabilir tüm aracıları kullanması gerektiğini belirtir.<br /><br />Daha fazla bilgi için [bkz: Kullanılacak test aracılarını belirtin.](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|
|**Pacing Gecikmesine Dağıtım Uygula**|Kullanıcı pacing test karışımı modelinde tipik dağıtım gecikmeleri uygulamak isteyip istemediğinizi belirtmek için kullanılan Boolean değeri. Bu özellik yalnızca **Test Mix Türü** özelliği **kullanıcı hızına göre**ayarlanmışsa geçerlidir.<br /><br />Daha fazla bilgi için [bkz: Dağıtım ı pacing gecikmesine uygulayın](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**IP Anahtarlama**|IP anahtarlamanın kullanIlip kullanılmadığını belirtmek için kullanılan boolean değeri.<br /><br />IP anahtarlama, bir test aracısının farklı IP adresleri kullanarak bir sunucuya istek göndermesini sağlar. Bu, farklı istemci bilgisayarlardan gelen aramaları simüle eder. IP anahtarlama, yük dengeli bir web çiftliğine karşı test yaparken önemlidir. Çoğu yük dengeleyicisi, istemcinin IP adresini kullanarak istemci ile belirli bir web sunucusu arasında yakınlık kurar. Tüm istekler tek bir istemciden geliyormuş gibi görünüyorsa, yük dengeleyici yükü dengelemez. Web çiftliğinde iyi bir yük dengesi elde etmek için, isteklerin çeşitli IP adreslerinden gelmesi önemlidir.<br /><br />IP anahtarlama yalnızca test aracısı ile kullanılabilir.|
|**Maksimum Test Yinelemeleri**|Senaryoda çalışacak maksimum test sayısını belirtmek için kullanılan sayısal değer. 0 değeri en fazla belirtin.<br /><br />Daha fazla bilgi için, [senaryolar için test yinelemelerini Yapılandır'a](../test/configure-test-iterations-in-a-load-test-scenario.md)bakın.|
|**Yeni Kullanıcıların Yüzdesi**|Senaryoda yeni kullanıcıların veya ilk kez gelen ziyaretçilerin yüzdesini belirten sayısal değer.<br /><br />Daha fazla bilgi için [bkz: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtin.](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Profili Düşün**|Senaryonun **Normal Dağılım'ı**kullanıp kullanmeyeceğini veya düşünme profilinin **Aveya** **Kapalı**olup olmadığını belirtir.<br /><br />Daha fazla bilgi için, [web sitesi insan etkileşimi gecikmeleri simüle etmek için düşünmek kez edit](../test/edit-think-times-in-load-test-scenarios.md)bakın.|

## <a name="timing"></a>Zamanlama

|Özellik|Tanım|
|-|----------------|
|**Gecikme Başlangıç Saati**|Yükleme testi başladıktan sonra senaryonun başlatılmasını geciktirmek için kaç saat, dakika ve saniye olduğunu gösteren bir zaman değeri. **Isınma sırasında devre dışı bırak** özelliği **True**olarak ayarlanmışsa, ısınma süresi tamamlandıktan sonra bekleme süresi geçerlidir.<br /><br />Daha fazla bilgi için [bkz.](../test/configure-scenario-start-delays.md)|
|**Isınma Sırasında Devre Dışı**|Yükleme testinin çalışma ayarında belirtilen **ısınma süresi** özellik zaman değeri sırasında senaryonun çalışması gerekip gerekmediğini belirtmek için kullanılan Boolean değeri.<br /><br />Yük testi çalıştırma ayar özellikleri hakkında daha fazla bilgi [için, Yük testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.<br /><br />Daha fazla bilgi için [bkz.](../test/configure-scenario-start-delays.md)|
|**Test Yinelemeleri Arasındaki Zamanları Düşünün**|Test yinelemeleri arasındaki bekleme süresini saniye cinsinden belirtmek için kullanılan sayısal değer.<br /><br />Daha fazla bilgi için, [web sitesi insan etkileşimi gecikmeleri simüle etmek için düşünmek kez edit](../test/edit-think-times-in-load-test-scenarios.md)bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
