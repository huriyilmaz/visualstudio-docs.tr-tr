---
title: Yük testi için yük desenleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0836fdb085ab33b2a646d9774c94bd859b5ca5ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590312"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Sanal kullanıcı etkinliklerini modellemek için yük modellerini düzenleme

Yük deseni özellikleri, bir yük testi sırasında benzetilen kullanıcı yükünün nasıl ayarlandığını belirtir. Visual Studio üç yerleşik yük delemi sağlar: sabit, adım ve hedef tabanlı. Yük modelini seçin ve özellikleri yük testi hedefleriniz için uygun düzeylere ayarlayın.

Yük deseni bir senaryonun bileşenidir. Senaryolar, tanımlanmış yük desenleri ile birlikte bir yük testi oluşturur.

> [!NOTE]
> Tüm Yük Desenleri'nde Visual Studio'nun oluşturduğu yük, sanal kullanıcıların simüle edilmiş bir yüküdür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Yük düzenleri

### <a name="constant"></a>Sabit

Sabit yük deseni, yük testi sırasında değişmeyen bir kullanıcı yükünü belirtmek için kullanılır. Örneğin, bir web uygulamasında bir duman testi çalıştırdığınızda, 10 kullanıcıdan oluşan hafif ve sabit bir yük ayarlamak isteyebilirsiniz.

#### <a name="constant-load-pattern-considerations"></a>Sabit yük deseni hususları

Sabit yük deseni, yük testinin çalıştırıldığı sırada aynı kullanıcı yükünü çalıştırmak için kullanılır. Yüksek kullanıcı sayısına sahip sabit bir yük deseni kullanırken dikkatli olun; bunu yapmak, yükleme testinin başında sunucunuza veya sunucularınıza mantıksız ve gerçekçi olmayan bir talep getirebilir. Örneğin, yük testiniz bir giriş sayfasına istekle başlayan bir web testi içeriyorsa ve yük testini sabit bir 1.000 kullanıcı yüküyle ayarlarsanız, yükleme testi ilk 1.000 isteği ana sayfaya mümkün olduğunca hızlı bir şekilde gönderir. Bu web sitenize gerçek dünya erişim gerçekçi bir simülasyon olmayabilir. Bunu azaltmak için, kademeli olarak 1.000 kullanıcıya kadar artan bir adım yükleme deseni kullanmayı düşünün veya Yük Testi Çalıştır Ayarları'nda bir ısınma süresi belirtin. Isınma süresi belirtilirse, yükleme testi ısınma döneminde yükü otomatik olarak kademeli olarak artırır. Daha fazla bilgi için [bkz.](../test/configure-scenario-start-delays.md)

### <a name="step"></a>Adım

Adım yükü deseni, tanımlanan maksimum kullanıcı yüküne kadar zamanla artan bir kullanıcı yükünü belirtmek için kullanılır. Adım yükleri **için, İlk Kullanıcı Sayısı,** **Maksimum Kullanıcı Sayısı,** **Adım Süresi (saniye)** ve **Adım Kullanıcı Sayısı'nı**belirtirsiniz.

Örneğin, bir İlk **Kullanıcı Sayısı,** **100'ün En Fazla Kullanıcı Sayısı,** **10'luk Adım Süresi (saniye)** ve 1 **Adım Kullanıcı Sayısı** 1'den başlayan bir kullanıcı yükü deseni oluşturur, 100 Kullanıcıya ulaşana kadar her 10 saniyede 1 artar.

> [!NOTE]
> Toplam test süresi maksimum kullanıcı yüküne ulaşmak için gereken süreden daha kısaysa, test geçen süreden sonra durur ve **Maksimum Kullanıcı Sayısı** hedefine ulaşmaz.

Sunucu, performansın önemli ölçüde azaldığı bir noktaya ulaşana kadar yükü artırmak için Adım hedefini kullanabilirsiniz. Yük arttıkça, sunucunun sonunda kaynakları tükenecektir. Adım yükü, bunun gerçekleştiği kullanıcı sayısını belirlemek için iyi bir yoldur. Adım yüklemesi ile, aracıların istenen yükü oluşturabilmesini sağlamak için aracı kaynaklarını yakından izlemeniz gerekir.

Normalde, belirli bir yük için iyi ölçümler elde edebilirsiniz, böylece farklı adım süreleri ve adım kullanıcı sayıları olan birkaç çalışır yürütmek gerekir. Sık sık, kullanıcılar eklendikçe yükler her adım için bir başlangıç ani artış gösterir. Yükü bu hızda tutmak, sistem ilk ani artıştan kurtarıldıktan sonra sistem performansını ölçmenize olanak tanır.

#### <a name="step-load-pattern-considerations"></a>Adım yük deseni hususları

Kullanıcı yükü arttıkça performansın nasıl değiştiğini görebilmeniz için yük testi çalışırken sunucu veya sunuculardaki yükü artırmak için bir adım yük deseni kullanılabilir. Örneğin, kullanıcı yükü 2.000 kullanıcıya yükselirken sunucunuzun veya sunucularınızın nasıl performans gösterdiğini görmek için, aşağıdaki özelliklere sahip bir adım yük deseni kullanarak 10 saatlik bir yükleme testi çalıştırabilirsiniz:

- **İlk Kullanıcı Sayısı**: 100

- **Maksimum Kullanıcı Sayısı**: 2.000

- **Adım Süresi (saniye)**: 1.800

- **Adım Adım Ramon Süresi (saniye)**: 20

- **Adım Kullanıcı Sayısı**: 100

  Bu ayarlar, 100, 200, 300 ve 2.000 kullanıcıya kadar kullanıcı yüklerinden 30 dakika (1.800 saniye) yük testi çalıştırır. Yeni Yük Testi Sihirbazı'nda seçim için uygun olmayan bu özelliklerden yalnızca biri **New Load Test Wizard**olduğundan, **Adım Rampası Süresi** özelliği özel olarak söz konusu dur. Bu özellik, bir adımdan diğerine (örneğin 100'den 200 kullanıcıya) artışın hemen değil, kademeli olarak gerçekleşmesini sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre içinde 100 kullanıcıdan 200 kullanıcıya yükseltilse (saniyede beş kullanıcı artışı). Daha fazla bilgi için [bkz: Adım yükleme deseni için adım rampası zaman özelliğini belirtin.](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)

### <a name="goal-based"></a>Hedefe dayalı

Hedef tabanlı yük deseni adım desenine benzer, ancak performans sayacı eşiklerine göre kullanıcı yükünü periyodik kullanıcı yükü ayarlamalarına göre ayarlar. Hedef tabanlı yükler çeşitli amaçlar için yararlıdır:

- Aracılardan elde edilen çıktıyı en üst düzeye çıkarmak: Aracıların çıktısını en üst düzeye çıkarmak için aracıüzerindeki anahtar sınırlayıcı ölçütünün ölçülmesi. Genellikle, CPU olduğunu; Ancak, aynı zamanda bellek olabilir.

- Hedef sunucuda genellikle CPU olmak üzere bazı hedef kaynak düzeyine ulaşmak, sonra bu düzeyde iş verisini ölçmek. Bu, sunucuda tutarlı bir kaynak kullanımı düzeyi göz önüne alındığında, iş letme açısından karşılaştırmalar yapmanızı sağlar.

- Sunucuda bir hedef iş düzeyine ulaşma.

  Aşağıdaki tabloda, aşağıdaki özellik ayarlarını içeren hedef tabanlı bir desen gösterilmektedir:

|Özellik Grubu|Özellik|Değer|
|-|--------------|-|
|Performans Sayacı|Kategori|İşlemci|
|Performans Sayacı|Bilgisayar|ContosoServer1|
|Performans Sayacı|Sayaç|% İşlemci zamanı|
|Performans Sayacı|Örnek|_toplam|
|Performans Sayacı için Hedef Aralığı|Yüksek Uç|90|
|Performans Sayacı için Hedef Aralığı|Düşük Uç|70|
|Kullanıcı Sayısı Sınırları|İlk Kullanıcı Sayısı|1|
|Kullanıcı Sayısı Sınırları|Maksimum Kullanıcı Sayısı|100|
|Kullanıcı Sayısı Sınırları|Maksimum Kullanıcı Sayısı Kuru|5|
|Kullanıcı Sayısı Sınırları|Maksimum Kullanıcı Sayısı Artış|5|
|Kullanıcı Sayısı Sınırları|Minimum Kullanıcı Sayısı|1|

Bu **ayarlar, Yük Testi Çözümleyicisinin** bir test çalışması sırasında kullanıcı yükünü 1 ile 100 arasında `% Processor Time` `70%` ayarlamasına neden olur ve WebServer01'in **Sayacı**`90%.`

Her kullanıcı yük ayarlamasının boyutu **Maksimum Kullanıcı Sayısı Artış ve** Maksimum **Kullanıcı Sayısı Artış** ayarlarına göre belirlenir. Kullanıcı sayısı sınırları Maksimum **Kullanıcı Sayısı** ve **Minimum Kullanıcı Sayısı** özellikleri tarafından ayarlanır.

#### <a name="goal-based-load-pattern-considerations"></a>Hedef tabanlı yük deseni hususları

Hedef tabanlı yük deseni, sisteminizin belirli bir kaynak kullanımı düzeyine ulaşmadan önce desteklenebildiği kullanıcı sayısını belirlemek istediğinizde yararlıdır. Bu seçenek, sisteminizdeki sınırlayıcı kaynağı (diğer bir deyişle darboğaz) zaten tanımladığınızda en iyi şekilde çalışır.

Örneğin, sisteminizdeki sınırlayıcı kaynağın veritabanı sunucunuzdaki CPU olduğunu bildiğinizi ve veritabanı sunucusundaki CPU yaklaşık yüzde 75 meşgul olduğunda kaç kullanıcının desteklenebileceğini görmek istediğinizi varsayalım. Performans sayacı "%İşlemci Süresi" değerini yüzde 70 ile yüzde 80 arasında tutma yı hedefleyen hedef tabanlı bir yük deseni kullanabilirsiniz.

Dikkat etmek için bir şey başka bir kaynak sistemin iş kısmını sınırlayan olmasıdır. Bu tür kaynaklar, hedef tabanlı yük deseni tarafından belirtilen hedefe asla ulaşılamamasını neden olabilir. Ayrıca, **Maksimum Kullanıcı Sayısı** için belirtilen değere ulaşılıncaya kadar kullanıcı yükü yükselmeye devam edecektir. Bu genellikle istenilen yük değildir, bu nedenle hedef tabanlı yük desenindeki performans sayacının seçimine dikkat edin.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testiniz için ilk yük deseni belirtilmesi:** **Yeni Yük Testi Sihirbazı'nı**kullanarak bir yük testi oluşturduğunuzda, bir yük deseni seçersiniz.|-   [Yük deseni değiştirme](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Yük testiniz için yük deseni düzenleme:** Yük testinizi oluşturduktan **sonra, Yük Testi**Düzenleyicisi'ndeki yük modelini düzenleyebilirsiniz.|-   [Nasıl yapılı: Adım yükleme deseni için adım rampası zaman özelliğini belirtin](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Yük testi senaryonuzdaki sanal kullanıcıların web önbelleği verilerini içerip içermemesi gerektiğini belirtme:** Yük testinin sanal kullanıcılar için bir web tarayıcısı tarafından gerçekleştirilecek web önbelleğe alma biçimini etkileyecek şekilde **yeni Kullanıcılar özelliğinin yüzdesini** değiştirebilirsiniz.|-   [Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtin](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Adım yük deseni için adım rampası süresini belirtme:** **Step Ramp Time** özelliği, bir adımdan diğerine (örneğin 100'den 200 kullanıcıya) artışın hemen değil, kademeli olarak gerçekleşmesini sağlar.|-   [Nasıl yapılı: Adım yükleme deseni için adım rampası zaman özelliğini belirtin](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Yük deseni değiştirme

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, bir senaryoyla ilişkili yük desen özelliklerini test hedeflerinize uygun düzeylere değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

> [!NOTE]
> Yük testi senaryo özelliklerinin ve açıklamalarının tam listesi için [bkz.](../test/load-test-scenario-properties.md)

Yük deseni, yükleme testi sırasında etkin olan sanal kullanıcı sayısını ve yeni kullanıcıların eklenme oranını belirtir. Kullanılabilir üç desen arasından seçim yapabilirsiniz: adım deseni, sabit ve hedefe dayalı. Daha fazla bilgi için bkz. Yük [testi senaryosunda yük desenli sanal kullanıcı sayısını belirtin.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

> [!NOTE]
> Ayrıca, yük testi eklentisi kullanarak yük özelliklerinizi programlı olarak değiştirebilirsiniz. Daha fazla bilgi için [bkz: Yük testi eklentisi oluşturun.](../test/how-to-create-a-load-test-plug-in.md)

### <a name="to-change-the-load-pattern"></a>Yük deseni değiştirmek için

1. Bir yük testi açın.

2. Yükleme **Testi**Düzenleyicisi'nde, *Senaryolar* klasöründe, yüklemek istediğiniz senaryoyu genişletin ve senaryo için yük deseni seçin.

    > [!NOTE]
    > Yük testinizin senaryo ağacında görüntülendiği gibi yük deseni düğümünün ifadelenmesi, yük testini oluşturduğunuzda seçtiğiniz yük profilini yansıtır. Sabit Yük **Profili** veya **Adım Yük Profili**olabilir.

3. **Özellikler** penceresini görüntülemek için **F4** tuşuna basın.

     **Yük Deseni** ve **Parametreler** kategorileri **Özellikler** penceresinde görüntülenir.

4. (İsteğe bağlı) **Yük Deseni** kategorisinde **Desen** özelliğini değiştirin.

     **Desen** özelliği için seçimleriniz **Adım,** **Sabit**ve **Hedef Tabanlı'dır.** Yük deseni türleri hakkında daha fazla bilgi için [bkz.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

5. (İsteğe bağlı) **Parametreler** kategorisinde değerleri değiştirin.

    > [!NOTE]
    > **Parametreler** için ayarlayabildiğiniz **değerler, Desen** özelliği için seçilen değere göre farklılık gösterir.

6. Özellikleri değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin. Daha sonra yeni yük deseni ile yük testi çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtin](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Nasıl yapılı: Adım yükleme deseni için adım rampası zaman özelliğini belirtin](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)
