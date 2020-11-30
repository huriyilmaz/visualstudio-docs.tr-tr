---
title: Yük testi için sayaç kümeleri ve eşik kuralları
description: Yük testinde sayaç kümeleri ve eşik kuralları belirtmeyi öğrenin. Test edilen sunucuları, sayaçların toplanacağı bilgisayar listesine ekleyin.
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
manager: jillfra
ms.openlocfilehash: 04348eb2d88c560e9687c687486e6b44d8394371
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328957"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Yük testinde bilgisayarlar için sayaç kümeleri ve eşik kuralları belirtme

Yük testleri, performans sayacı verilerini çözümlediğinizde kullanışlı olan adlandırılmış sayaç kümeleri sağlar. Sayaç kümeleri teknolojiye göre düzenlenir ve Application, ASP.NET, .NET Application, IIS ve SQL dahil. **Yeni Yük Testi Sihirbazı** kullanarak bir yük testi oluşturduğunuzda, ilk sayaç kümesini eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış ve önemli sayaç kümeleri kümesi sunar. Sayaçlarınızı **Yük Testi Düzenleyicisi** yönetirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testleriniz uzak makineler arasında dağıtılmışsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayaç kümelerine eşlenir. Yük testinizde uzak makinelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Sayaç kümeleri, belirttiğiniz bilgisayarlarda toplanır. Bir sayaç kümesi ile yük testi sırasında kullanılan bir bilgisayar arasındaki ilişki *sayaç kümesi eşlemedir*. Örneğin, test ettiğiniz Web sunucusunda ASP.NET, IIS ve .NET uygulama sayaç kümesi eşlemeleri olabilir.

Varsayılan olarak, performans sayaçları denetleyicide ve aracılarda toplanır. Daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Test edilen sunucuları, sayaçların toplanacağı bilgisayar listesine eklemeniz önemlidir. Daha sonra, önemli sistem verileri, yük testi sırasında toplanır ve izlenir.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için sayaç kümelerini yönetme:** Yük testinizi oluşturduktan sonra, Yük Testi Düzenleyicisi sayaç kümesini düzenleyebilirsiniz. Sayaç kümelerini yönetmek, performans verilerini toplamak istediğiniz bilgisayar kümesini seçmeyi ve her bir bilgisayardan toplanacak bir dizi sayaç kümesi atamayı içerir. Sayaçlarınızı Yük Testi Düzenleyicisi yönetirsiniz.|-   [Nasıl yapılır: sayaç kümelerini yönetme](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Yük testinize sayaç kümeleri ekleyin:** **Yeni Yük Testi Sihirbazı** bir yük testi oluşturduğunuzda, ilk sayaç kümesini eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri kümesi sunar. Yük testi oluşturduktan sonra, Yük Testi Düzenleyicisi kullanarak mevcut sayaç kümelerine yeni sayaçlar ekleyebilirsiniz.|-   [Nasıl yapılır: sayaç kümelerine sayaç ekleme](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Nasıl yapılır: özel sayaç kümeleri ekleme](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Yük testiniz için sayaçları kullanarak bir eşik kuralı belirtin:** Eşik kuralı, bir yük testi sırasında sistem kaynak kullanımını izlemek için bireysel bir performans sayacı üzerinde ayarlanan bir kuraldır. Sayaç kümesi tanımları birçok ana performans sayacı için önceden tanımlanmış eşik kuralları içerir. Yük testlerinde eşik kuralları bir performans sayacı değerini sabit bir değerle veya başka bir performans sayacı değeriyle karşılaştırır.|-   [Nasıl yapılır: eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Sayaç kümelerinin eşlendiği bilgisayarlara kolay adlar atayın:** Bilgisayara kolayca tanınan bir ad uygulamanızı sağlayan bilgisayar etiketleri ekleyebilirsiniz. Etiketler, Yük Testi Düzenleyicisi ağacın **sayaç kümesi eşlemeleri** düğümünde görüntülenir. Daha önemli olan Etiketler, paydaşların bilgisayarın yük testinde hangi rolün olduğunu belirlemesine yardımcı olan Excel raporlarında görüntülenir. Örneğin, "Web 'de Sunucu1, lab2" veya "Phoenix ofisinde SQL Sunucu2" gibi.<br /><br /> Daha fazla bilgi için bkz. [Test karşılaştırmaları veya eğilim analizi Için rapor yükleme testleri sonuçları](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Sayaç kümelerini kullanma

Yük testi araçları, zaman içinde sayaçları kullanarak performans verilerini toplar ve grafiğini çizin. Sayaç verileri, bir yük testi çalıştırması sırasında Kullanıcı tarafından belirtilen aralıklarda toplanır. Daha fazla bilgi için bkz. [nasıl yapılır: örnek hızını belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Çalışma zamanında sayaçları görüntüleyebilir veya *Yük Testi Çözümleyicisini* kullanarak bir yük testi çalıştırdıktan sonra bunları görüntüleyebilirsiniz.

Sayaç verileri, sunucuda ve testin çalıştırıldığı herhangi bir bilgisayarda toplanır. Testlerinizin çalıştırılacağı bir aracı bilgisayarları kümesi ayarladıysanız, sayaçlar bu bilgisayarlarda da toplanır.

Üç sayaç kategorisi vardır: yüzdeler, sayılar ve ortalamalar. Bazı örnekler şunlardır% CPU kullanımı, kilit sayısı SQL Server ve saniye başına IIS isteği.

![Yük testi sayaç kümeleri](../test/media/loadtestcountersets.png)

Bireysel HTTP istekleri için performans verileri, bir testi çalıştıran bilgisayar tarafından bildirilir. bir aracı bilgisayar gibi. İstekler için, ortalama bayt, yanıt süresi ve saniye başına Isteklerin ortalama süresi gibi verileri izleyebilirsiniz.

Bir Web sunucusundaki performans verilerinin toplanmasını kolaylaştırmak için Visual Studio Enterprise, yük testlerinde kullanım teknolojisine bağlı olarak önceden tanımlanmış, adlandırılmış sayaç kümeleri de sağlar. Bu kümeler, IIS, ASP.NET veya SQL Server çalıştıran bir sunucuyu analiz ettiğinizde faydalıdır. Varsayılan sayaç kümesinde sağlanmayan sayaçlar Yük Testi Düzenleyicisi kullanılarak eklenebilir. Bu bilgisayarlarda kaynak kullanımını izleyebilmeniz için yük testinize test edilen bilgisayarları veya sunucuları eklemeniz önemlidir. Daha fazla bilgi için bkz. [nasıl yapılır: sayaç kümelerini yönetme](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Yük çalıştırmalarının sonuç analizi, hangi verilerin toplanacaklarını, eşik kurallarının nerede ayarlanacağını ve bir ölçünün uygulamada belirli bir sorunu yansıtmaya nasıl söyleyeceğinizi öğrenmek için belirli bir alana yönelik etki alanına özgü bilgi gerektirir. Daha fazla bilgi için bkz. [eşik kuralları hakkında](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Performans sayacı örnekleme aralığı konuları

Yük testinin uzunluğuna bağlı olarak yük testi çalıştırma ayarlarındaki **örnek hız** özelliği için uygun bir değer seçin. Beş saniyelik varsayılan değer gibi daha küçük bir örnek hız, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için örnek hızının artırılması, toplanan veri miktarını azaltır. Daha fazla bilgi için bkz. [nasıl yapılır: örnek hızını belirtme](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Örnek ücretler için bazı yönergeler aşağıda verilmiştir.

|Yük testi süresi|Önerilen örnek hızı|
|-|-----------------------------|
|\< 1 saat|5 saniye|
|1 − 8 saat|15 saniye|
|8 − 24 saat|30 saniye|
|> 24 saat|60 saniye|

## <a name="store-performance-data"></a>Performans verilerini depolayın

Yük testi çalıştırması sırasında, performans sayacı verileri toplanır ve *load test sonuçları deposunda* depolanır. Daha fazla bilgi için bkz. yük testi sonuçları [deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Eşik kuralları hakkında

*Eşik kuralı* , bir yük testi sırasında sistem kaynak kullanımını izlemek için bireysel bir performans sayacı üzerinde ayarlanan bir kuraldır. Sayaç kümesi tanımları birçok ana performans sayacı için önceden tanımlanmış eşik kuralları içerir. Daha fazla bilgi için bkz. [yük testlerinde performans sayacı verilerini çözümlemeye yardımcı olması için sayaç kümelerini kullanma](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Eşik kuralları ve Düzeyler

Yük testlerinizde eşik kuralları oluştururken, iki tür kural arasında seçim yapabilirsiniz:

Compare sabiti &mdash; bir performans sayacı değerini sabit değerle karşılaştırın.

Sayaçları Karşılaştır &mdash; bir performans sayacı değerini başka bir performans sayacı değeriyle karşılaştırın.

Eşik kuralları oluştururken kural düzeylerini de ayarlarsınız. Düzeyler, uyarı eşiği ve kritik eşiklerdir. Bir yük testi çalıştırması görüntülediğinizde, uyarı düzeyi eşik ihlalleri sarı bir simgeyle belirtilir ve kritik düzey eşik ihlalleri kırmızı bir sembol ile belirtilir.

## <a name="the-alert-if-over-property"></a>Eğer Özellik üzerindeyken uyarır

Bir eşiği aşan bir sorun olduğunu belirtmek için özelliği **true** olarak ayarlandıysa **uyarıyı** ayarlayın. Örneğin, eşik kuralı **% Işlemci zamanı** üzerinde ayarlandıysa ve değer 90 ' den büyükse uyarılmak Istiyorsanız, sabit kural türünü **Karşılaştır** ' ı kullanın, **kritik eşik değerini** 90 olarak ayarlayın ve **true** **ise uyarıyı** ayarlayın.

Eşiğin altına düşülecek bir sorun olduğunu belirtmek için, özelliği **false** olarak ayarlandıysa **uyarıyı** ayarlayın. Örneğin, eşik kuralı **istekler/sn** üzerinde ayarlandıysa ve değer 50 ' in altındaysa uyarılmak Istiyorsanız, sabit kural türünü **Karşılaştır** ' ı kullanın, **kritik eşik değerini** 50 olarak ayarlayın ve **false** **ise uyarı** olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
