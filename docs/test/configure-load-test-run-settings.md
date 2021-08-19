---
title: Yük Testi Çalıştırma Ayarlarını Yapılandırma
description: Yük testinin çalışma yolunu etkileyen özellikler olan çalıştırma ayarları hakkında bilgi edinebilirsiniz. Çalıştırma ayarları, çalışma sayfasındaki kategorilere Özellikler penceresi.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 0c3231bcd9f9ce5da8ee85323bca058c82829662
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140134"
---
# <a name="configure-load-test-run-settings"></a>Yük testi çalıştırma ayarlarını yapılandırma

*Çalıştırma ayarları,* yük testinin çalışma yolunu etkileyen bir özellik kümesidir. Çalıştırma ayarları, Özellikler penceresindeki kategorilere **göre** düzenlenmiştir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir yük testinde birden fazla çalıştırma ayarına sahip olabilir, ancak çalıştırma başına yalnızca bir çalıştırma ayarı etkin olabilir. Diğer çalıştırma ayarları, sonraki test çalıştırmaları için kullanmak üzere alternatif bir ayar seçmenin hızlı bir yolunu sağlar.

İlk çalıştırma ayarı, New Yük Testi Sihirbazı kullanılarak bir **yük testi oluşturulduğunda oluşturulur.**

![Yük Testi Çalıştırma Ayarlar](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-|
|**Yük teste daha fazla çalıştırma ayarı ekleyin:** Yeni Yük Testi Sihirbazı'yi çalıştırarak oluşturulan çalıştırma ayarına **ek** olarak, testi farklı koşullar altında çalıştırabilirsiniz.|-   [Nasıl kullanılır: Yük testinde ek çalıştırma ayarları ekleme](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Yük testiyle birlikte kullanmak üzere etkin çalıştırma ayarını belirtin:** Yük testiyle birlikte kullanmak istediğiniz çalıştırma ayarını seçmek için aşağıdaki Yük Testi Düzenleyicisi. Etkin çalıştırma ayarı "[Active]" soneki ile tanımlanır.|-   [Nasıllı: Yük testi için etkin çalıştırma ayarını seçme](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Çalıştırma ayarı özelliklerini düzenleme:** Günlüğe kaydetme seçenekleri (daha fazla bilgi için aşağıya bakın), testin uzunluğunu, isınma süresini, bildirilen maksimum hata ayrıntısı sayısını, örnekleme oranını, bağlantı modelini (yalnızca web performans testleri), sonuç depolama türünü, doğrulama düzeyini ve SQL izleme gibi özellikler için çalıştırma ayarı özelliklerinizi düzenleyebilirsiniz. Çalıştırma ayarları, yük testinizin hedeflerini yansıtacak şekilde ayara tıklayın.|-   [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md)<br />-   [Çalıştırma ayarı özelliklerini değiştirme](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Yük testi çalıştırma ayarlarında test yinelemesi sayısını belirtin:** Test Yinelemeleri özelliğini yapılandırarak yük testlerinin tüm senaryolarında tüm web performansının ve birim testlerinin çalıştırılama **sayısını belirtebilirsiniz.**|-   [Nasıl: Bir çalıştırma ayarında test yinelemesi sayısını belirtme](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Yük testi çalıştırma ayarı için örnekleme oranını belirtin:** Örnek Hızı özelliğini yapılandırarak yük testinin performans sayacı verilerini toplama **sıklıklarını belirtebilirsiniz.**|-   [Nasıl: Örnek oranını belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zamanlama ayrıntıları depolama seçeneğini belirtin:** Timing Details Depolama özelliğini yapılandırarak yük testinin ayrıntılarının nasıl **Depolama** belirtebilirsiniz.|-   [Nasıl: Zamanlama ayrıntıları depolama özelliğini belirtme](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Test kaynağı saklama dönemini belirtin:** Kaynak Saklama Süresi > ayar > test kaynaklarını belirli bir süre boyunca koruyarak test ve yeniden test döngüsünü düzeltme testi **hızını** hızlandırın.|-   [Yük testlerini hızlandırmak için kaynakları koruma](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts&preserve-view=true)|
|**Bağlam parametrelerini kullanın:** Bir dizeyi parametreleştirmek için bağlam parametrelerini kullanabilirsiniz. Örneğin, yük testinde parametreli web sunucusu kullanan bir web performans testi varsa, farklı bir sunucuyla eşilen çalıştırma ayarlarına bir bağlam parametresi eklemek için kullanabilirsiniz.|-   [Nasıl olur: Çalıştırma ayarına bağlam parametreleri ekleme](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Test günlüğü özelliklerini yapılandırma:** Verilerin yük testi çalıştırma ayarlarıyla ilişkili günlüğe ne sıklıkta yazıldığı yapılandırabilirsiniz. Günlük birkaç gigabayt haline geldiğinden, büyük veya karmaşık bir yük testi çalıştırıyorken bu önemli olabilir.<br /><br /> Ayrıca yük testin hata ayıklama ve uygulama analizinde yardımcı olması için günlük dosyasını otomatik olarak kaydediyecek şekilde de yapılandırabilirsiniz.|-   [Yük testi günlük ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)|