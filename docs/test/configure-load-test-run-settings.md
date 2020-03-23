---
title: Yük Testi Çalıştırma Ayarlarını Yapılandırma
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ffc9d6c2e563fcd16a61e91eaa94889de8607efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595988"
---
# <a name="configure-load-test-run-settings"></a>Yük testi çalıştırma ayarlarını yapılandırma

*Çalıştırma ayarları,* yük testinin çalışma şeklini etkileyen özellikler kümesidir. Çalıştırma ayarları **Özellikler** penceresindeki kategorilere göre düzenlenir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir yük testinde birden fazla çalıştırma ayarı olabilir, ancak çalışma ayarlarından yalnızca biri çalıştır başına etkin olabilir. Diğer çalıştırma ayarları, sonraki test çalıştırmaları için kullanılacak alternatif bir ayar seçmek için hızlı bir yol sağlar.

Yeni Yük Testi Sihirbazı'nı kullanarak bir **New Load Test Wizard**yük testi oluşturduğunuzda ilk çalıştırma ayarı oluşturulur.

![Test Çalıştır Ayarlarını Yükle](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-|
|**Yük testinize daha fazla çalıştırma ayarı ekleyin:** **Yeni Yük Testi Sihirbazı'nı**çalıştırdığınızda oluşturulan çalıştırma ayarına ek olarak, testi farklı koşullarda çalıştırabilmek için yük testinize daha fazla çalıştırma ayarı ekleyebilirsiniz.|-   [Nasıl yapılır: Yük testine ek çalışma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Yük testiile kullanılacak etkin çalıştırma ayarını belirtin:** Yük Testi Düzenleyicisi'ni kullanarak yük testiile kullanmak istediğiniz çalışma ayarını seçebilirsiniz. Etkin çalıştırma ayarı "[Etkin]" soneki ile tanımlanır.|-   [Nasıl seçilir: Yük testi için etkin çalışma ayarını seçin](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Çalıştır ayarı özelliklerini edin:** Günlük seçenekleri (aşağıya bakın), testin uzunluğunu, ısınma süresini, bildirilen maksimum hata ayrıntısı sayısını, örnekleme oranını, bağlantı modelini (yalnızca web performans testleri), sonuç depolama türü, doğrulama düzeyi ve SQL izleme gibi şeyler için çalışma ayar özelliklerini ayarlayabilirsiniz. Çalıştırma ayarları yük testinizin hedeflerini yansıtmalıdır.|-   [Test çalıştırma ayarları özelliklerini yükleyin](../test/load-test-run-settings-properties.md)<br />-   [Çalışma ayar özelliklerini değiştirme](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Yük testi çalıştırma ayarlarında test yineleme sayısını belirtin:** **Test Yinelemeleri** özelliğini yapılandırarak, yük testlerinizin tüm senaryolarında tüm web performansını ve birim testlerini kaç kez çalıştırabileceğinizi belirtebilirsiniz.|-   [Nasıl yapılacağını: Çalışma ayarında test yinelemelerinin sayısını belirtin](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Yük testi çalıştırma ayarı için örnekleme oranını belirtin:** **Örnek Hızı** özelliğini yapılandırarak yük testinin performans sayacı verilerini ne sıklıkta toplayabileceğini belirtebilirsiniz.|-   [Nasıl yapılı: Örnek oranını belirtin](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zamanlama ayrıntıları depolama seçeneğini belirtin:** **Zamanlama Ayrıntıları Depolama** özelliğini yapılandırarak kaydedilen yük testinin ayrıntılarını nasıl istediğinizi belirtebilirsiniz.|-   [Nasıl yapılsın: Zamanlama ayrıntıları depolama özelliğini belirtin](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Test kaynağı bekletme süresini belirtin:** **Kaynak Saklama Süresi** özelliğini ayarlayarak test kaynaklarını belirli bir süre boyunca saklayarak test > yeniden test döngüsünü > düzeltin.|-   [Yük testini hızlandırmak için kaynakları koruyun](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Bağlam parametrelerini kullanın:** Bir dize parametrelendirmek için bağlam parametrelerini kullanabilirsiniz. Örneğin, yük testiniz parametreli bir web sunucusu kullanan bir web performans testi içeriyorsa, farklı bir sunucuyla eşleşen çalışma ayarlarına bağlam parametresi ekleyebilirsiniz.|-   [Nasıl kullanılır: Çalışma ayarına bağlam parametreleri ekleme](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Test günlüğü özelliklerini yapılandırma:** Yük testi çalıştırma ayarlarınızla ilişkili günlüklere verilerin ne sıklıkta yazıldığını yapılandırabilirsiniz. Günlük birkaç gigabayt olabilir, çünkü büyük veya karmaşık bir yük testi çalıştırırken bu önemli olabilir.<br /><br /> Ayrıca, yükleme testinizin hata ayıklama ve uygulamanızı çözümlemede yardımcı olmayı başaramaması durumunda günlük dosyasını otomatik olarak kaydedilecek şekilde yapılandırabilirsiniz.|-   [Yük testi günlüğe kaydetme ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)|
