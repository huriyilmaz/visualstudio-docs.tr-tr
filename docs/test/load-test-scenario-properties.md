---
title: Yük Testi Senaryosu Özellikleri
description: Yük testi senaryosu özellik ayarlarınızı bu makaledeki Visual Studio test senaryosu özelliklerinden biri olarak değiştirme hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f5f85269ab91390034d7ffe897e98ed47946c9721e1e11c6f60e0c8240e11182
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408948"
---
# <a name="load-test-scenario-properties"></a>Yük testi senaryosu özellikleri

Yük testi gereksinimlerinizi karşılamak için Visual Studio senaryo özellik ayarlarınızı değiştirin. Bu makalede kategoriye göre çeşitli yük testi senaryosu özellikleri listelemektedir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Genel

|Özellik|Tanım|
|-|----------------|
|**Ad**|Senaryonun adı.|

## <a name="mix"></a>Karışık

|Özellik|Tanım|
|-|----------------|
|**Tarayıcı Karışımı**|Yük testi için web tarayıcısı karışımını belirtir. Farklı web tarayıcısı türlerini ve bunların yük dağıtımını belirtebilirsiniz.<br /><br />Tarayıcı Karışımını Düzenle iletişim kutusunu  açmak için üç  nokta  **(...)** düğmesini seçin ve Ekle ve Kaldır'ı kullanarak yük testinde web tarayıcısı türlerini seçin.<br /><br />Daha fazla bilgi için [bkz. Web tarayıcısı türlerini belirtme.](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Ağ Karışımı**|Yük testi için ağ karışımını belirtir. Dahil etmek istediğiniz ağ türlerini ve bunların yük dağıtımını belirtebilirsiniz.<br /><br />Üç nokta **(...) düğmesini seçerek** Ağ Karışımını Düzenle  iletişim  kutusunu açın ve Ekle ve Kaldır'ı kullanarak yük testinde ağ türlerini seçin. <br /><br />Daha fazla bilgi için [bkz. Sanal ağ türlerini belirtme.](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Test Karışımı**|Yük testi için web performansını ve birim testi karışımını belirtir. Hangi testleri dahil etmek ve bunların yük dağılımını belirtesiniz.<br /><br />Üç nokta **(...) düğmesini seçerek** **Test** Karışımını Düzenle  iletişim  kutusunu açın ve Ekle ve Kaldır'ı kullanarak yük testinde testleri seçin.<br /><br />Daha fazla bilgi için [yük testi senaryosu için test karışımını düzenleyin.](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Test Karışımı Türü**|Yük testi için test karışımı modelini belirtir.<br /><br />Üç nokta **(...) düğmesini** seçerek **Test** Karışımını Düzenle iletişim kutusunu açın ve **Test** karışımı modeli altındaki açılır listeyle yük testinde kullanmak üzere test karışımı modelini seçin.<br /><br />Daha fazla bilgi için [bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|

## <a name="options"></a>Seçenekler

|Özellik|Tanım|
|-|----------------|
|**Kullanım Aracıları**|Yük testini uzaktan çalıştırıyorsanız senaryonun kullanmasına istediğiniz aracıları belirtir. Örneğin, performans eğilimlerini analiz ederken tutarlılığı korumak için belirli bir aracı kümesi belirtmek istiyor olabilir. Ayrıca aracılar, çalıştırıldıları betikler ile aracının bulunduğu konum arasında benzeşim olması için coğrafi olarak dağıtılmalarını sağlar.<br /><br />Aracılar virgülle ayrılabilir; örneğin, "**Aracı1, Aracı2, Aracı3**". Özelliğini boş bırakmak, senaryonun tüm kullanılabilir aracıları kullanması gerektiğini belirtir.<br /><br />Daha fazla bilgi için, [bkz. How to: Specify test agents to use](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Gecikme Süresine Dağıtım Uygulama**|Kullanıcı hızı test karışımı modelinde tipik dağıtım gecikmeleri uygulamak mı istediğiniz belirtmek için kullanılan Boole değeri. Bu özellik yalnızca **Test** Karışımı Türü özelliği Kullanıcı hızına göre **olarak ayarlanırsa geçerlidir.**<br /><br />Daha fazla bilgi için [bkz. Nasıl yapılır: Dağıtımı ilerleme gecikmesine uygulama](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**IP Değiştirme**|IP değiştirmenin kullanılıp kullanılmay olduğunu belirtmek için kullanılan Boole değeri.<br /><br />IP değiştirme, bir test aracısına farklı IP adresleri aralığı kullanarak sunucuya istek göndermesini sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini sağlar. Yük dengeli bir web grubuyla test etmek için IP değiştirme önemlidir. Çoğu yük dengeci, istemcinin IP adresini kullanarak bir istemci ile belirli bir web sunucusu arasında benzeştir. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa yük dengeleyici yükü dengelemez. Web grubu içinde iyi bir yük dengelemesi elde etmek için, isteklerin bir dizi IP adresi aralığından olması önemlidir.<br /><br />IP değiştirme yalnızca test aracısı ile kullanılabilir.|
|**En Fazla Test Yinelemesi**|Senaryoda çalıştıracak en fazla test sayısını belirtmek için kullanılan sayısal değer. 0 değeri en yüksek değeri belirtir.<br /><br />Daha fazla bilgi için [bkz. Senaryolar için test yinelemelerini yapılandırma.](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Yeni Kullanıcıların Yüzdesi**|Senaryoda yeni kullanıcıların veya ilk kez ziyaretçilerin yüzdesini belirten sayısal değer.<br /><br />Daha fazla bilgi için [bkz. Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme.](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Think Profile**|Senaryonun Normal Dağıtımı kullanmayacak **veya** düşünme profilinin Açık veya Kapalı **olduğunu** **belirtir.**<br /><br />Daha fazla bilgi için [bkz. Web sitesi insan etkileşimi gecikmelerinin benzetimini yapmak için düşünme sürelerini düzenleme.](../test/edit-think-times-in-load-test-scenarios.md)|

## <a name="timing"></a>Zamanlama

|Özellik|Tanım|
|-|----------------|
|**Gecikme Başlangıç Zamanı**|Yük testi başladıktan sonra senaryoyu başlatmanın kaç saat, dakika ve saniye gecikmeli olduğunu gösteren bir zaman değeri. **Isınma Sırasında** Devre Dışı Bırak özelliği **True** olarak ayarlanırsa, bekleme süresi, isınma süresi tamamlandıktan sonra geçerli olur.<br /><br />Daha fazla bilgi için [bkz. Senaryo başlatma gecikmelerini yapılandırma.](../test/configure-scenario-start-delays.md)|
|**Isınma Sırasında Devre Dışı Bırak**|Senaryonun, yük testinin çalıştırma ayarında belirtilen Isınma Süresi özellik zaman değeri sırasında çalıştırılamayacak olup olmadığını belirtmek için kullanılan Boole değeri. <br /><br />Yük testi çalıştırma ayarı özellikleri hakkında daha fazla bilgi için [bkz. Yük testi çalıştırma ayarları özellikleri.](../test/load-test-run-settings-properties.md)<br /><br />Daha fazla bilgi için [bkz. Senaryo başlatma gecikmelerini yapılandırma.](../test/configure-scenario-start-delays.md)|
|**Test Yinelemeleri Arasında Düşünme Süreleri**|Test yinelemeleri arasında saniyeler içinde bekleme süresi belirtmek için kullanılan sayısal değer.<br /><br />Daha fazla bilgi için [bkz. Web sitesi insan etkileşimi gecikmelerinin benzetimini yapmak için düşünme sürelerini düzenleme.](../test/edit-think-times-in-load-test-scenarios.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
