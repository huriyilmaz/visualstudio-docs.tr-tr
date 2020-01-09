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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584445"
---
# <a name="load-test-scenario-properties"></a>Yük testi senaryosu özellikleri

Yük testi gereksinimlerinizi karşılamak için Visual Studio 'daki yük testi senaryo özelliği ayarlarınızı değiştirin. Bu makalede kategoriye göre çeşitli yük testi senaryosu özellikleri listelenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Genel

|Özellik|Tanım|
|-|----------------|
|**Ad**|Senaryonun adı.|

## <a name="mix"></a>Karışık

|Özellik|Tanım|
|-|----------------|
|**Tarayıcı karışımı**|Yük testi için Web tarayıcısı karışımını belirtir. Farklı Web tarayıcı türleri ve bunların yük dağılımını belirtebilirsiniz.<br /><br />**Tarayıcı karışımını düzenle** iletişim kutusunu açmak için üç nokta **(...)** düğmesini seçin ve yük testinde Web tarayıcı türlerini seçmek için **Ekle** ve **Kaldır** ' ı kullanın.<br /><br />Daha fazla bilgi için bkz. [Web tarayıcıları türlerini belirtme](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Ağ karışımı**|Yük testi için ağ karışımını belirtir. Hangi ağ türlerini ve bunların yük dağılımını dahil edileceğini belirtebilirsiniz.<br /><br />**Ağ karışımını düzenle** iletişim kutusunu açmak için üç nokta **(...)** düğmesini seçin ve yük testinde ağ türlerini seçmek için **Ekle** ve **Kaldır** ' ı kullanın.<br /><br />Daha fazla bilgi için [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Test karışımı**|Yük testi için Web performansını ve birim testi karışımını belirtir. Hangi testlerin ekleneceğini ve bunların yük dağılımını belirtebilirsiniz.<br /><br />**Test karışımını düzenle** iletişim kutusunu açmak için üç nokta **(...)** düğmesini seçin ve yük testinde testleri seçmek için **Ekle** ve **Kaldır** ' ı kullanın.<br /><br />Daha fazla bilgi için, [bir yük testi senaryosunun test karışımını düzenleyin](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Test karışımı türü**|Yük testi için test karışımı modelini belirtir.<br /><br />**Test karışımını düzenle** iletişim kutusunu açmak için üç nokta **(...)** düğmesini seçin ve yük testinde kullanılacak test karışımı modelini seçmek için **Test karışımı modeli** altındaki açılan düğmeyi kullanın.<br /><br />Daha fazla bilgi için bkz. [metin karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Seçenekler

|Özellik|Tanım|
|-|----------------|
|**Kullanılacak Aracılar**|Yük testini uzaktan çalıştırıyorsanız, senaryonuzun kullanmasını istediğiniz aracıları belirtir. Örneğin, performans eğilimlerini analiz ederken tutarlılık sağlamak için belirli bir aracı kümesi belirtmek isteyebilirsiniz. Ayrıca, aracıların hangi betikler çalıştırdıkları ve aracının bulunduğu bir benzeşim olması için coğrafi olarak dağıtılmış olabilir.<br /><br />Aracıları ayrılmalıdır virgüllerle, örneğin "**agent1'e, birim testi Agent2, Aracı3**". Özellik boş bırakılırsa, senaryo kullanılabilir tüm aracılar kullanması gerektiğini belirtir.<br /><br />Daha fazla bilgi için bkz. [nasıl yapılır: kullanılacak test aracılarını belirtme](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Ilerleme Gecikmesine Dağıtım Uygula**|Kullanıcı hız testi karıştırıcı modelinde tipik dağıtım gecikmeleri uygulamak istiyorsanız, belirtmek için kullanılan Boolean değeri. Bu özellik yalnızca **Test karışımı türü** özelliği **Kullanıcı adına göre**ayarlandıysa geçerlidir.<br /><br />Daha fazla bilgi için bkz [. nasıl yapılır: adım adım gecikmesine dağıtım uygulama](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**IP geçişi**|IP geçişinin kullanıldığını belirtmek için kullanılan Boolean değeri.<br /><br />IP anahtarlama, bir test aracısının istekleri bir farklı IP adresi aralığı kullanarak sunucuya göndermesini sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini yapar. Yük dengeli bir Web grubuna karşı test ettiğinizde IP geçişi önemlidir. Çoğu yük dengeleyiciler, istemcinin IP adresini kullanarak bir istemciyle belirli bir Web sunucusu arasında benzeşim kurar. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa, yük dengeleyicisi yükü dengelemez. Web grubunda iyi yük dengelemesi elde etmek için isteklerin bir IP adresi aralığından gelmesi önemlidir.<br /><br />IP değiştirme yalnızca test aracısında kullanılabilir.|
|**En yüksek test yinelemeleri**|Senaryoda çalıştırılacak en fazla test sayısını belirtmek için kullanılan sayısal değer. 0 değeri en fazla bir değer belirtir.<br /><br />Daha fazla bilgi için bkz. [senaryolar için test yinelemelerini yapılandırma](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Yeni Kullanıcı yüzdesi**|Senaryodaki yeni kullanıcıların veya ilk kez ziyaretçilerin yüzdesini belirten sayısal değer.<br /><br />Daha fazla bilgi için bkz. [nasıl yapılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Düşünme profili**|Senaryonun **normal dağıtım**kullanıp kullanyacağını veya düşünme profilinin **Açık** veya **kapalı**olduğunu belirtir.<br /><br />Daha fazla bilgi için [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme düzenleme kez](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Zamanlama

|Özellik|Tanım|
|-|----------------|
|**Gecikme başlangıç saati**|Yük testi başladıktan sonra senaryonun başlatılmasının kaç saat, dakika ve saniye gecikme süresini belirten bir zaman değeri. **Warmup özelliği sırasında devre dışı bırak** özelliği **true**olarak ayarlanırsa, beklenecek sürenin miktarı, ısınma döneminin tamamlanmasından sonra geçerli olur.<br /><br />Daha fazla bilgi için bkz. [senaryo başlangıç gecikmelerini yapılandırma](../test/configure-scenario-start-delays.md).|
|**Warmup sırasında devre dışı bırak**|Senaryonun, yük testinin çalıştırma ayarında belirtilen **Isınma süresi** özelliği zaman değeri sırasında çalıştırılması ya da olmaması durumunda olup olmadığını belirtmek için kullanılan Boolean değeri.<br /><br />Yük testi çalıştırma ayarı özellikleri hakkında daha fazla bilgi için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).<br /><br />Daha fazla bilgi için bkz. [senaryo başlangıç gecikmelerini yapılandırma](../test/configure-scenario-start-delays.md).|
|**Test yinelemeleri arasındaki düşünme süreleri**|Test yinelemeleri arasında saniye cinsinden bekleme süresini belirtmek için kullanılan sayısal değer.<br /><br />Daha fazla bilgi için [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme düzenleme kez](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
