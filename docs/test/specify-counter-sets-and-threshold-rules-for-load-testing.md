---
title: Yük testi için Sayaç Kümeleri ve Eşik Kuralları
description: Yük testinde sayaç kümelerini ve eşik kurallarını belirtmeyi öğrenin. Test altındaki sunucuları, sayaçların toplanmayacakları bilgisayar listesine ekleyin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 70e74129590f867d15c83d1419762d7162474c5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054203"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Yük testinde bilgisayarlar için sayaç kümeleri ve eşik kuralları belirtme

Yük testleri, performans sayacı verilerini analiz etmek için yararlı olan adlandırılmış sayaç kümeleri sağlar. Sayaç kümeleri teknolojiye göre düzenlenmiştir ve Application, ASP.NET, .NET Application, IIS ve SQL. New Yük Testi Sihirbazı kullanarak bir **yük testi sanız,** ilk sayaç kümesi eklersiniz. Bunlar, yük testi için önceden tanımlanmış ve önemli sayaç kümeleri kümesi sağlar. Sayaçlarınızı **Yük Testi Düzenleyicisi.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testlerinizi uzak makinelere dağıtıyorsanız, denetleyici ve aracı sayaçları denetleyici ve aracı sayaç kümeleri ile eşlenmiş olur. Yük testinde uzak makineleri kullanma hakkında daha fazla bilgi için bkz. Test denetleyicileri [ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)

Sayaç kümeleri, belirttiğiniz bilgisayarlarda toplanmış. Bir sayaç kümesi ile yük testi sırasında kullanılan bir bilgisayar arasındaki ilişki, bir sayaç kümesi *eşlemesidir.* Örneğin, test etmekte olduğunu web sunucusunda ASP.NET, IIS ve .NET uygulama sayacı kümesi eşlemeleri olabilir.

Varsayılan olarak, performans sayaçları denetleyicide ve aracılarda toplanır. Daha fazla bilgi için [bkz. Test denetleyicileri ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)

Sayaçların toplanmayacak bilgisayarlar listesine test altındaki sunucuları eklemeniz önemlidir. Ardından, tüm önemli sistem verileri yük testi sırasında toplanır ve izlenir.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testi için sayaç kümelerini yönetme:** Yük testini oluşturduk sonra, sayaç kümesinde sayaç Yük Testi Düzenleyicisi. Sayaç kümelerini yönetmek, performans verilerini toplamak istediğiniz bilgisayar kümelerini seçmeyi ve her bir bilgisayardan toplamak için bir sayaç kümesi atamayı içerir. Sayaçlarınızı veri Yük Testi Düzenleyicisi.|-   [Nasıl: Sayaç kümelerini yönetme](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Yük teste sayaç kümeleri ekleyin:** New Yük Testi Sihirbazı ile bir **yük testi** oluşturdukta, ilk sayaç kümesi eklersiniz. Bunlar, yük testi için önceden tanımlanmış sayaç kümeleri kümesi sağlar. Yük testi oluşturdukta, yeni sayaçları mevcut sayaç kümelerini kullanarak yeni sayaçlar Yük Testi Düzenleyicisi.|-   [Nasıl yapılanlar: Sayaç kümelerini ekleme](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Nasıl yapılanlar: Özel sayaç kümeleri ekleme](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Yük testinde sayaçları kullanarak bir eşik kuralı belirtin:** Eşik kuralı, yük testi sırasında sistem kaynağı kullanımını izlemek için tek bir performans sayacında ayarlanmış bir kuraldır. Sayaç kümesi tanımları, birçok önemli performans sayacı için önceden tanımlanmış eşik kuralları içerir. Yük testlerinde eşik kuralları, performans sayacı değerini sabit değerle veya başka bir performans sayacı değeriyle karşılaştırıldığında.|-   [Nasıl: Eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Sayaç kümelerini eşlenen bilgisayarlara kolay adlar attayın:** Bir bilgisayara kolayca tanınan bir ad uygulamanıza olanak sağlayan bilgisayar etiketleri ekleme. Etiketler, kümedeki **ağacın** Sayaç Kümesi Eşlemeleri düğümünde Yük Testi Düzenleyicisi. Daha da önemlisi, paydaşların yük testinde bilgisayarın hangi rolüne sahip olduğunu tanımlamasına yardımcı olan Excel raporlarında etiketler görüntülenir; örneğin, "lab2'de Web Server1" veya "Phoenix ofisinde SQL Server2".<br /><br /> Daha fazla bilgi için [bkz. Test karşılaştırmaları veya eğilim analizi için yük testi sonuçlarını bildirme.](../test/compare-load-test-results.md)||

## <a name="use-counter-sets"></a>Sayaç kümelerini kullanma

Yük testi araçları zaman içinde sayaçları kullanarak performans verilerini toplar ve graflar. Sayaç verileri, yük testi çalıştırması sırasında kullanıcı tarafından belirtilen aralıklarla toplanır. Daha fazla bilgi için, [bkz. How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Sayaçları çalışma zamanında görüntülenebilir veya Yük Testi Çözümleyicisi'nin kullanarak bir yük testi çalıştırması sonrasında *görüntü yapabilirsiniz.*

Sayaç verileri sunucuda ve testin çalıştır olduğu herhangi bir bilgisayarda toplanmış. Testlerinizi çalıştırmak için bir dizi aracı bilgisayar ayarladıysanız, bu bilgisayarlarda sayaçlar da toplanmış olur.

Üç sayaç kategorisi vardır: yüzdeler, sayımlar ve ortalamalar. Bazı örnekler CPU kullanımı, SQL Server sayısı ve saniye başına IIS istekleridir.

![Yük Testi Sayaç Kümeleri](../test/media/loadtestcountersets.png)

Tek tek HTTP istekleri için performans verileri, test çalıştıran bilgisayar tarafından raporlandı. aracı bilgisayar gibi. İstekler için Ortalama İlk Bayta Kadar Süre, Yanıt Süresi ve Saniye Başına İstek sayısı gibi verileri izleyebilirsiniz.

Web sunucusunda performans verilerini toplamayı kolaylaştırmak için, Visual Studio Enterprise testlerde kullanmak üzere teknolojiye dayalı önceden tanımlanmış, adlandırılmış sayaç kümeleri de sağlar. Bu kümeler IIS, ASP.NET veya SQL Server çalıştıran bir sunucuyu analiz ASP.NET. Varsayılan sayaç kümesinde sağlanmaz sayaçlar, Yük Testi Düzenleyicisi. Bu bilgisayarlarda kaynak kullanımını izleyemediklerinden emin olmak için, yük testinize bilgisayarları veya sunucuları test altına eklemeniz önemlidir. Daha fazla bilgi için, [bkz. How to: Manage counter sets](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Yük çalıştırmalarının sonuç analizi genellikle belirli bir alanla ilgili etki alanına özgü bilgi sahibi olmak için hangi verilerin toplanacak, eşik kurallarının nerede ayarlanacak ve ölçümün uygulamada belirli bir sorunu ne zaman yansıtdığının nasıl anlanacaklarını bilmek gerekir. Daha fazla bilgi için [bkz. Eşik kuralları hakkında.](#about-threshold-rules)

### <a name="performance-counter-sampling-interval-considerations"></a>Performans sayacı örnekleme aralığıyla ilgili dikkat edilmesi gerekenler

Yük testi çalıştırma ayarlarında **Örnek Hızı** özelliği için yük testnizin uzunluğuna göre uygun bir değer seçin. Varsayılan beş saniyelik değer gibi daha küçük bir örnek oranı, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için örnek oranının artırılması toplanan veri miktarını azaltır. Daha fazla bilgi için, [bkz. How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek hızlar için bazı yönergeler aşağıda vemektedir.

|Yük testi süresi|Önerilen örnek hızı|
|-|-----------------------------|
|\< 1 Saat|5 saniye|
|1-8 Saat|15 saniye|
|8-24 Saat|30 saniye|
|> 24 Saat|60 saniye|

## <a name="store-performance-data"></a>Performans verilerini depolama

Yük testi çalıştırması sırasında performans sayacı verileri toplanır ve Load *Test Sonuçları Deposunda depolanır.* Daha fazla bilgi için [yük testi sonuçları deposundaki yük testi sonuçlarını yönetme.](../test/manage-load-test-results-in-the-load-test-results-repository.md)

## <a name="about-threshold-rules"></a>Eşik kuralları hakkında

Eşik *kuralı,* yük testi sırasında sistem kaynağı kullanımını izlemek için tek bir performans sayacında ayarlanmış bir kuraldır. Sayaç kümesi tanımları, birçok önemli performans sayacı için önceden tanımlanmış eşik kuralları içerir. Daha fazla bilgi için [bkz. Yük testlerinde performans sayacı verilerini analiz etmeye yardımcı olmak için sayaç kümelerini kullanma.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

## <a name="threshold-rules-and-levels"></a>Eşik kuralları ve düzeyleri

Yük testlerinde eşik kuralları 2 tür kuraldan birini seçersiniz:

Sabiti &mdash; Karşılaştırma Performans sayacı değerini sabit değerle karşılaştırın.

Sayaçları Karşılaştırma &mdash; Performans sayacı değerini başka bir performans sayacı değeriyle karşılaştırın.

Eşik kuralları oluşturmak için kuralın düzeylerini de ayarlayın. Düzeyler uyarı eşiği ve kritik eşiktir. Bir yük testi çalıştırması görüntüde uyarı düzeyi eşik ihlalleri sarı bir sembolle, kritik düzey eşiği ihlalleri ise kırmızı bir sembolle gösterilir.

## <a name="the-alert-if-over-property"></a>Alert If Over özelliği

Eşiği **aşmanın bir sorun** olduğunu belirtmek için Alert If Over özelliğini **True** olarak ayarlayın. Örneğin, eşik kuralı **%** İşlemci Zamanı olarak ayarlanmışsa ve değer 90'dan büyükse uyarı  almak için Sabiti  Karşılaştır kural türünü kullanın, Kritik  Eşik Değerini 90 olarak ayarlayın ve Uyarı Over değerini True olarak **ayarlayın.**

Eşiğin **altına düşmesinin** bir **sorun olduğunu** belirtmek için Alert If Over özelliğini False olarak ayarlayın. Örneğin eşik kuralı **İstekler/Sn** olarak ayarlanmışsa ve değer 50'nin altında ise uyarı  almak için Sabiti  Karşılaştır kural türünü kullanın, Kritik  Eşik Değerini 50 olarak ayarlayın ve Uyarı Fazla Ise Değerini False olarak **ayarlayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl: Eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Eşik kuralı ihlallerini analiz etme](../test/analyze-threshold-rule-violations-in-load-tests.md)
