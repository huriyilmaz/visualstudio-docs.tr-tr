---
title: Yük testi için Sayaç Kümeleri ve Eşik Kuralları
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
ms.openlocfilehash: 440bc01b52269c477d9d2f2194fd831041f1d20d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596326"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Yük testindeki bilgisayarlar için sayaç kümeleri ve eşik kuralları belirtin

Yük testleri, performans sayacı verilerini çözümlediğinizde yararlı olan adlandırılmış sayaç kümeleri sağlar. Sayaç kümeleri teknolojiye göre düzenlenir ve Application, ASP.NET, .NET Application, IIS ve SQL'i içerir. **Yeni Yük Testi Sihirbazı'nı**kullanarak bir yük testi oluşturduğunuzda, bir başlangıç sayaç kümesi eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış ve önemli sayaç kümeleri sunar. Yük Testi Düzenleyicisi'nde sayaçlarınızı yönetirsiniz. **Load Test Editor**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Yük testleriniz uzak makinelere dağıtılırsa, denetleyici ve aracı sayaçları denetleyici ve aracı sayAcı kümelerine eşlenir. Yük testinizde uzak makinelerin nasıl kullanılacağı hakkında daha fazla bilgi için test [denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)hakkında bilgi alın.

Sayaç kümeleri belirttiğiniz bilgisayarlarda toplanır. Bir sayaç kümesi ile yük testi sırasında kullanılan bir bilgisayar arasındaki ilişki, *sayaç kümesi eşlemidir.* Örneğin, test ettiğiniz web sunucusunda ASP.NET, IIS ve .NET uygulama sayacı eşlemeleri olabilir.

Varsayılan olarak, performans sayaçları denetleyici ve aracılar üzerinde toplanır. Daha fazla bilgi için test [denetleyicileri ve test aracıları'na](configure-test-agents-and-controllers-for-load-tests.md)bakın.

Test altındaki sunucuları sayaçları toplamak için bilgisayarlar listesine eklemeniz önemlidir. Daha sonra, herhangi bir önemli sistem verileri toplanır ve yük testi sırasında izlenir.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için sayaç kümelerini yönetin:** Yük testinizi oluşturduktan sonra, Yük Testi Düzenleyicisi'ndeki Sayaç Kümesini ayarlayabilirsiniz. Sayaç kümelerini yönetmek, performans verileri toplamak istediğiniz bilgisayar kümesini seçmeyi ve her bir bilgisayardan toplanacak bir sayaç kümeleri kümesi atamayı içerir. Yük Testi Düzenleyicisi'nde sayaçlarınızı yönetirsiniz.|-   [Nasıl Yapılsın: Sayaç kümelerini yönetme](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Yük testinize sayaç kümeleri ekleyin:** **Yeni Yük Testi Sihirbazı**ile bir yük testi oluşturduğunuzda, bir başlangıç sayaç kümesi eklersiniz. Bunlar, yük testiniz için önceden tanımlanmış sayaç kümeleri sunar. Bir yük testi oluşturduktan sonra, Yük Testi Düzenleyicisi'ni kullanarak varolan sayaç kümelerine yeni sayaçlar ekleyebilirsiniz.|-   [Nasıl yapılsın: Sayaç kümelerine sayaç ekleme](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Nasıl yapılsın: Özel sayaç setleri ekleme](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Yük testiniz için sayaçları kullanarak bir eşik kuralı belirtin:** Eşik kuralı, yük testi sırasında sistem kaynağı kullanımını izlemek için tek bir performans sayacına ayarlanan bir kuraldır. Sayaç kümesi tanımları, birçok önemli performans sayacı için önceden tanımlanmış eşik kuralları içerir. Yük testlerinde eşik kuralları, performans sayacı değerini sabit bir değer veya başka bir performans sayacı değeriyle karşılaştırır.|-   [Nasıl yapılı: Eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Sayaç kümelerinin eşlendiği bilgisayarlara uygun adlar atayın:** Kolayca tanınan bir adı bir bilgisayara uygulamanızı sağlayan bilgisayar etiketleri ekleyebilirsiniz. Etiketler, Yük Testi Düzenleyicisi'ndeki ağacın **Sayaç Kümesi Eşlemeler** düğümünde görüntülenir. Daha da önemlisi, etiketler Excel raporlarında, hissedarların bilgisayarın yük testinde ne gibi "Web Server1 in lab2" veya "SQL Server2 in Phoenix office" gibi rolünü belirlemesine yardımcı olur.<br /><br /> Daha fazla bilgi için, [test karşılaştırmaları veya eğilim çözümlemesi için Rapor yük testleri sonuçlarına](../test/compare-load-test-results.md)bakın.||

## <a name="use-counter-sets"></a>Sayaç kümelerini kullanma

Yük testi araçları zaman içinde sayaçları kullanarak performans verilerini toplar ve grafik. Sayaç verileri, yük testi çalışması sırasında kullanıcıtarafından belirtilen aralıklarla toplanır. Daha fazla bilgi için [bkz: Örnek oranını belirtin.](../test/how-to-specify-the-sample-rate-for-a-load-test.md) Sayaçları çalışma zamanında görüntüleyebilir veya *Yük Testi Çözümleyicisi'ni*kullanarak çalıştırılabilen bir yük testinden sonra görebilirsiniz.

Sayaç verileri sunucuda ve testin çalıştırıldığı herhangi bir bilgisayarda toplanır. Testlerinizi çalıştırabileceğiniz bir aracı bilgisayar kümesi kurduysanız, sayaçlar da bu bilgisayarlarda toplanır.

Üç sayaç kategorisi vardır: yüzdeler, sayımlar ve ortalamalar. Bazı örnekler % CPU kullanımı, SQL Server kilit sayıları ve saniyede IIS istekleridir.

![Yük Testi Sayıcı Setleri](../test/media/loadtestcountersets.png)

Tek tek HTTP isteklerine ait performans verileri, bir testi çalıştıran bilgisayar tarafından bildirilir. aracı bilgisayar gibi. İstekler için, Ortalama Önce Bayt, Yanıt Süresi ve Saniye Başına İstekler gibi verileri izleyebilirsiniz.

Visual Studio Enterprise, bir web sunucusunda performans verilerinin toplanmasını kolaylaştırmak için yük testlerinde kullanılmak üzere teknolojiye dayalı önceden tanımlanmış, adlandırılmış sayaç kümeleri de sağlar. Bu kümeler, IIS, ASP.NET veya SQL Server çalıştıran bir sunucuanaliz ederken yararlıdır. Varsayılan sayaç kümesinde sağlanmayan sayaçlar Yük Testi Düzenleyicisi kullanılarak eklenebilir. Bu bilgisayarlarda kaynak kullanımını izleyebildiğinizden emin olmak için test altındaki bilgisayarları veya sunucuları yükleme testinize eklemeniz önemlidir. Daha fazla bilgi için [bkz: Sayaç kümelerini yönetin.](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)

Yük çalıştırmalarının sonuç analizi, hangi verilerin toplanacak, eşik kurallarının nerede ayarlandığı ve bir ölçümün uygulamada belirli bir sorunu ne zaman yansıttığının nasıl belirleneceğini bilmek için sık sık belirli bir alanın etki alanına özgü bilgisini gerektirir. Daha fazla bilgi için [eşik kuralları hakkında](#about-threshold-rules)bkz.

### <a name="performance-counter-sampling-interval-considerations"></a>Performans sayacı örnekleme aralığı değerlendirmeleri

Yük testinizin uzunluğuna bağlı olarak yük testi çalıştırma ayarlarında **Örnek Oran** özelliği için uygun bir değer seçin. Beş saniyenin varsayılan değeri gibi daha küçük bir örneklem hızı, yük testi sonuçları veritabanında daha fazla alan gerektirir. Daha uzun yük testleri için, örneklem oranının artırılması toplanan veri miktarını azaltır. Daha fazla bilgi için [bkz: Örnek oranını belirtin.](../test/how-to-specify-the-sample-rate-for-a-load-test.md)

Aşağıda örnek oranları için bazı kurallar verilmiştir.

|Yük testi süresi|Önerilen örnek oran|
|-|-----------------------------|
|\<1 Saat|5 saniye|
|1−8 Saat|15 saniye|
|8−24 Saat|30 saniye|
|> 24 Saat|60 saniye|

## <a name="store-performance-data"></a>Performans verilerini depolama

Yük testi çalışması sırasında, performans sayacı verileri toplanır ve *Yük Testi Sonuçları Deposu'nda*depolanır. Daha fazla bilgi için bkz: [Yük testi sonuçları deposundaki yük testi sonuçlarını yönet.](../test/manage-load-test-results-in-the-load-test-results-repository.md)

## <a name="about-threshold-rules"></a>Eşik kuralları hakkında

*Eşik kuralı,* yük testi sırasında sistem kaynağı kullanımını izlemek için tek bir performans sayacına ayarlanan bir kuraldır. Sayaç kümesi tanımları, birçok önemli performans sayacı için önceden tanımlanmış eşik kuralları içerir. Daha fazla bilgi için bkz: [Yük testlerinde performans sayacı verilerini analiz etmeye yardımcı olmak için sayaç kümelerini kullan.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

## <a name="threshold-rules-and-levels"></a>Eşik kuralları ve düzeyleri

Yük testlerinizde eşik kuralları oluşturduğunuzda, iki tür kural arasından seçim yapabilirsiniz:

Sabit&mdash;karşıla performans sayacı değerini sabit bir değerle karşılaştırın.

Sayaçları&mdash;Karşılaştır Bir performans sayacı değerini başka bir performans sayacı değeriyle karşılaştırın.

Eşik kuralları oluşturduğunuzda, kuralın düzeylerini de ayarlarsınız. Düzeyleri uyarı eşiği ve kritik eşik vardır. Bir yük testi çalışmasını görüntülediğinizde, uyarı düzeyi eşik ihlalleri sarı bir sembolle gösterilir ve kritik düzey eşik ihlalleri kırmızı bir sembolle gösterilir.

## <a name="the-alert-if-over-property"></a>Özellik Üzerinde Ise Uyarısı

Bir eşiği aşmanın bir sorun olduğunu belirtmek için **Uyarı Yı** True özelliğini **True** olarak ayarlayın. Örneğin, eşik kuralı **% İşlemci Zamanı'nda**ayarlanmışsa ve değer 90'dan büyükse uyarı lağvetmek istiyorsanız, **Sabiti Karşılaştır** kuralı türünü kullanın, **Kritik Eşik Değerini** 90 olarak ayarlayın ve Varsa **Doğru'yu uyarıyı** ayarlayın. **True**

Bir eşiğin altına düşmenin sorun olduğunu belirtmek için **Alert If Özelliği'ni** **False** olarak ayarlayın. Örneğin, eşik kuralı **İstekler/Ssk'te**ayarlanmışsa ve değer 50'nin altındaysa uyarılmak istiyorsanız, **Sabiti Karşılaştır** kuralı türünü kullanın, **Kritik Eşik Değerini** 50 olarak ayarlayın ve **Yanlış**Varsa **Uyarısı'nı** ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılı: Eşik kuralı ekleme](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Eşik kuralı ihlallerini analiz edin](../test/analyze-threshold-rule-violations-in-load-tests.md)
