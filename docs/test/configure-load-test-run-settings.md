---
title: Yük Testi Çalıştırma Ayarlarını Yapılandırma
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e8002373b7ad34796df557686c1aff6a417d49ea
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288838"
---
# <a name="configure-load-test-run-settings"></a>Yük testi çalıştırma ayarlarını yapılandır

*Çalışma ayarları* , yük testinin çalışma biçimini etkileyen bir özellikler kümesidir. Çalışma ayarları, **Özellikler** penceresindeki kategorilere göre düzenlenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testinde birden fazla çalışma ayarınız olabilir, ancak çalıştırma ayarlarından yalnızca biri etkin olabilir. Diğer çalışma ayarları, sonraki test çalıştırmaları için kullanılacak alternatif bir ayar seçmek için hızlı bir yol sağlar.

**Yeni Yük Testi Sihirbazı**kullanarak bir yük testi oluşturduğunuzda ilk çalıştırma ayarı oluşturulur.

![Yük testi çalıştırma ayarları](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-|
|**Yük testinize daha fazla çalışma ayarı ekleyin:** **Yeni Yük Testi Sihirbazı**çalıştırdığınızda oluşturulan çalıştırma ayarına ek olarak, testi farklı koşullarda çalıştırabilmeniz için yük testinize daha fazla çalışma ayarları ekleyebilirsiniz.|-   [Nasıl yapılır: yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Yük testiyle birlikte kullanılacak etkin çalıştırma ayarını belirtin:** Yük Testi Düzenleyicisi kullanarak, yük testinizdeki kullanmak istediğiniz çalıştırma ayarını seçebilirsiniz. Etkin çalıştırma ayarı "[etkin]" son eki tarafından tanımlanır.|-   [Nasıl yapılır: bir yük testi için etkin çalışma ayarını seçme](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Çalışma ayarı özelliklerini Düzenle:** Farklı Çalıştır seçeneklerini (daha fazla bkz. daha fazla bilgi), test süresini, ısınma süresini, en fazla hata ayrıntısı sayısını belirleme, örnekleme hızı, bağlantı modeli (yalnızca Web performans testleri), sonuç depolama türü, doğrulama düzeyi ve SQL izleme gibi işlemler için çalışma ayarı özelliklerini düzenleyebilirsiniz. Çalışma ayarları, yük testinizin hedeflerini yansıtmalıdır.|-   [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md)<br />-   [Çalışma ayarı özelliklerini değiştirme](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Yük testi çalıştırma ayarlarında test yineleme sayısını belirtin:** **Test yinelemeleri** özelliğini yapılandırarak yük testlerinizin tüm senaryolarında Web performansının ve birim testlerinin tümünün kaç kez çalıştırılacağını belirtebilirsiniz.|-   [Nasıl yapılır: bir çalışma ayarında test yineleme sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Yük testi çalışma ayarı için örnekleme hızını belirtin:** **Örnek hız** özelliğini yapılandırarak yük testinin performans sayacı verilerinin ne sıklıkta toplanacağını belirtebilirsiniz.|-   [Nasıl yapılır: örnek hızı belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zamanlama Ayrıntıları Depolama seçeneğini belirtin:** **Zamanlama Ayrıntıları Depolama** özelliğini yapılandırarak yük testinin ayrıntılarının nasıl kaydedilmesini istediğinizi belirtebilirsiniz.|-   [Nasıl yapılır: zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Sınama kaynağı saklama süresini belirtin:** **Kaynak saklama süresi** özelliğini ayarlayarak belirli bir süre için test kaynaklarını koruyarak test > düzeltmesini > yeniden test etme döngüsünü hızlandırın.|-   [Yük testini hızlandırmak için kaynakları koruyun](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Bağlam parametrelerini kullan:** Bir dizeyi parametreleştirmek için bağlam parametreleri kullanabilirsiniz. Örneğin, yük testiniz parametreli bir Web sunucusu kullanan bir Web performans testi içeriyorsa, farklı bir sunucuya eşlenen çalışma ayarlarına bir bağlam parametresi ekleyebilirsiniz.|-   [Nasıl yapılır: bir çalışma ayarına bağlam parametreleri ekleme](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Test günlüğü özelliklerini yapılandırma:** Verilerin yük testi çalıştırma ayarlarınızla ilişkili günlüğe ne sıklıkla yazıldığını yapılandırabilirsiniz. Bu, günlük birkaç gigabayt haline gelebileceğinden büyük veya karmaşık bir yük testi çalıştırırken önemli olabilir.<br /><br /> Ayrıca, yük testiniz uygulamanızı hata ayıklamada ve çözümlemede yardımcı olmazsa günlük dosyasını otomatik olarak kaydedilecek şekilde yapılandırabilirsiniz.|-   [Yük testi günlük kaydı ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)|
