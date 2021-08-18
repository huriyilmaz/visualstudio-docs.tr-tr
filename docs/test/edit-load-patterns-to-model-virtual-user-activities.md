---
title: Yük testi için yük düzenleri
description: Visual Studio sağladığı yerleşik yük desenleri hakkında bilgi edinin. Yük modelini seçin ve yük testiniz için özellikleri uygun düzeyler olarak ayarlayın.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f67e518e5f9701ae011733d796252431ce6c9eda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083836"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Sanal Kullanıcı etkinliklerini modellemek için yük düzenlerini düzenleme

Yük deseninin özellikleri, bir yük testi sırasında benzetimli Kullanıcı yükünün nasıl ayarlanacağını belirtir. Visual Studio üç yerleşik yük düzeni sağlar: sabit, adım ve amaç tabanlı. Yük modelini seçer ve özellikleri yük testi hedefleriniz için uygun düzeyler olarak ayarlayabilirsiniz.

Yük stili bir senaryonun bileşenidir. Senaryolar, tanımlı yük desenleriyle birlikte bir yük testi oluşturur.

> [!NOTE]
> tüm yük desenlerinde, Visual Studio oluşturduğu yük sanal kullanıcıların benzetilen bir yüküne sahiptir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Yük düzenleri

### <a name="constant"></a>Sabit

Sabit yük stili, yük testi sırasında değişmez bir kullanıcı yükünü belirtmek için kullanılır. Örneğin, bir Web uygulamasında bir duman testi çalıştırdığınızda, 10 ' un hafif, sabit bir yükünü ayarlamak isteyebilirsiniz.

#### <a name="constant-load-pattern-considerations"></a>Sabit yük düzeniyle ilgili konular

Bir yük testinin çalıştırılması sırasında aynı kullanıcı yükünü çalıştırmak için sabit bir yük stili kullanılır. Yüksek kullanıcı sayısına sahip sabit bir yük deseninin kullanılmasıyla ilgili dikkatli olun; Bunun yapılması, yük testinin başlangıcında sunucunuza veya sunucularınıza mantıklı ve gerçekçi olmayan bir talep yerleştirebilir. Örneğin, yük testiniz bir giriş sayfasına yönelik bir istekle başlayan bir Web testi içeriyorsa ve yük testini 1.000 Kullanıcı sabit bir yüküne ayarlarsanız, yük testi ilk 1.000 isteği giriş sayfasına mümkün olduğunca hızlı bir şekilde gönderir. Bu, Web sitenize gerçek dünya erişiminin gerçekçi bir simülasyonu olmayabilir. bunu azaltmak için, aşamalı olarak 1.000 kullanıcıya kadar artan bir adım yükleme modelini kullanmayı veya yük testi çalıştırmasında Ayarlar bir ısınma dönemi belirtmeyi düşünün. Bir ısınma süresi belirtilmişse, yük testi, otomatik olarak yükü, ısınma döneminde otomatik olarak artırır. Daha fazla bilgi için bkz. [senaryo başlangıç gecikmelerini yapılandırma](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Adım

Adım yükü stili, tanımlı en yüksek Kullanıcı yüküne kadar geçen bir kullanıcı yükünü belirtmek için kullanılır. Atlama yükleri için **Ilk Kullanıcı sayısı**, **en yüksek Kullanıcı sayısı**, **adım süresi (saniye)** ve **adım kullanıcı sayısı**' nı belirtirsiniz.

Örneğin, **Ilk Kullanıcı sayısı** , **en yüksek Kullanıcı** sayısı 100, **adım süresi (saniye)** , 10 ve **adım kullanıcı sayısı** 1 olan bir adım yükleme, 1 ' den başlayan bir Kullanıcı yük deseninin yanı sıra, 100 kullanıcıya ulaşıncaya kadar 10 dakikada bir artar.

> [!NOTE]
> Toplam test süresi en fazla Kullanıcı yüküne geçmek için gereken süreden kısaysa, test geçen süreden sonra duraklar ve **en yüksek Kullanıcı sayısı** hedefine ulaşmaz.

Sunucu performansın önemli ölçüde azalcağı bir noktaya ulaşana kadar yükü artırmak için adım hedefini kullanabilirsiniz. Yük arttıkça sunucu sonunda kaynakları tükenir. Adım yükü, bu gerçekleştiği Kullanıcı sayısını belirlemenin iyi bir yoludur. Adımlama yükle birlikte, aracıların istenen yükü üretabileceğinden emin olmak için aracı kaynaklarını yakından izlemeniz gerekir.

Genellikle, belirli bir yük için iyi ölçümler elde edebilmeniz için, farklı adım süreleri ve adım kullanıcı sayısı olan birkaç çalıştırma yapmanız gerekir. Genellikle, Yüklemeler Kullanıcı eklendikçe her adım için bir ilk ani artış gösterir. Yükün bu hızda tutulması, sistem ilk ani kurtarıldığında sistem performansını ölçmenize olanak tanır.

#### <a name="step-load-pattern-considerations"></a>Adım yük düzeniyle ilgili konular

Bir adım yük şekli, yük testi çalışırken, kullanıcı yükü arttıkça performansın nasıl değişeceğini görebileceğiniz şekilde sunucu veya sunuculardaki yükü artırmak için kullanılabilir. Örneğin, kullanıcı yükü 2.000 kullanıcıya arttıkça sunucu veya sunucularınızın nasıl çalıştığını görmek için, aşağıdaki özelliklere sahip bir adım yük modelini kullanarak 10 saatlik bir yük testi çalıştırabilirsiniz:

- **Ilk Kullanıcı sayısı**: 100

- **En fazla kullanıcı sayısı**: 2.000

- **Adım süresi (saniye)**: 1.800

- **Adım Rampa Süresi (saniye)**: 20

- **Adım kullanıcı sayısı**: 100

  Bu ayarlar, 100, 200, 300 ve en fazla 2.000 Kullanıcı yükünde, 30 dakika (1.800 saniye) için yük testini çalıştırır. **Yeni Yük Testi Sihirbazı** seçilmek üzere kullanılamayan bu özelliklerden yalnızca biri olduğundan, **Adım Rampa Süresi** özelliği özel bahsetmeye değecektir. Bu özellik, bir adımdan bir sonrakine (örneğin, 100 ' den 200 ' e kadar) kadar artışın hemen yerine yavaş bir şekilde gerçekleşmesini sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre (her saniyede beş Kullanıcı artışı) üzerinden 100 ' dan 200 kullanıcıya yükseltilir. Daha fazla bilgi için bkz. [nasıl yapılır: adım yükleme deseninin Adım Rampa Süresi özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Hedef tabanlı

Hedef tabanlı yük deseninin adım düzenine benzer ancak performans sayacı eşiklerine göre kullanıcı yükü, düzenli kullanıcı yükleme ayarlamalarına göre ayarlanır. Hedef tabanlı yüklemeler çeşitli farklı amaçlarla faydalıdır:

- Aracılardan çıkış kaplamasını Kapla: aracıların çıkışını en üst düzeye çıkarmak için aracıdaki anahtar sınırlayan ölçümü ölçün. Genellikle CPU olur; Ancak, bellek de olabilir.

- Hedef sunucuda genellikle CPU olan ve daha sonra bu düzeyde üretilen iş kaynak düzeyine ulaşıyor. Bu, sunucuda tutarlı bir kaynak kullanımı düzeyi verilen aktarım hızı karşılaştırmaları gerçekleştirmenizi sağlar.

- Sunucudaki hedef işleme düzeyine ulaşıyor.

  Aşağıdaki tabloda, örnek olarak aşağıdaki özellik ayarlarına sahip hedef tabanlı bir model gösterilmektedir:

|Özellik Grubu|Özellik|Değer|
|-|--------------|-|
|Performans sayacı|Kategori|İşlemci|
|Performans sayacı|Bilgisayar|ContosoServer1|
|Performans sayacı|Sayaç|% İşlemci zamanı|
|Performans sayacı|Örnek|_Total|
|Performans sayacı için hedef Aralık|Üst uç|90|
|Performans sayacı için hedef Aralık|Düşük uç|70|
|Kullanıcı sayısı sınırları|İlk Kullanıcı sayısı|1|
|Kullanıcı sayısı sınırları|En fazla kullanıcı sayısı|100|
|Kullanıcı sayısı sınırları|En fazla kullanıcı sayısı azalışı|5|
|Kullanıcı sayısı sınırları|Maksimum Kullanıcı sayısı artışı|5|
|Kullanıcı sayısı sınırları|En düşük Kullanıcı sayısı|1|

Bu ayarlar, **Yük Testi Çözümleyicisinin** , WebServer01 **sayacının** `% Processor Time` ve arasında dolaşması gibi bir Test çalışması sırasında 1 ile 100 arasında Kullanıcı yükünü ayarlamasına neden olur. `70%``90%.`

Her kullanıcı yükleme ayarlamasının boyutu, **en yüksek Kullanıcı sayısı artışı** ve **en yüksek Kullanıcı sayısı azaltma** ayarlarına göre belirlenir. Kullanıcı sayısı sınırları, **en yüksek Kullanıcı** sayısı ve **En düşük Kullanıcı sayısı** özelliklerine göre ayarlanır.

#### <a name="goal-based-load-pattern-considerations"></a>Hedef tabanlı yük düzeniyle ilgili konular

Hedef tabanlı yük düzeniyle, sisteminizin bazı kaynak kullanımı düzeyine ulaşmadan destekleyebileceği kullanıcı sayısını belirleyebilmek istediğinizde faydalıdır. Bu seçenek, sisteminizdeki sınırlandırma kaynağını (diğer bir deyişle, performans sorunu) zaten belirlediğiniz zaman en iyi şekilde geçerlidir.

Örneğin, sisteminizdeki sınırlayan kaynağın veritabanı sunucunuzdaki CPU olduğunu ve veritabanı sunucusundaki CPU yaklaşık 75 oranında meşgul olduğunda kaç kullanıcının desteklebildiğini görmek istediğinizi varsayalım. "% Işlemci süresi" performans sayacının değerini yüzde 70 ve yüzde 80 arasında tutma hedefi olan bir hedef tabanlı yük düzeni kullanabilirsiniz.

Dikkat etmek gereken bir şey, sistemin aktarım hızını sınırlandıran başka bir kaynaktır. Bu tür kaynaklar, hedef tabanlı yük düzeni tarafından belirtilen hedefe hiçbir zaman ulaşılamayacak şekilde neden olabilir. Ayrıca, Maksimum Kullanıcı Sayısı için belirtilen değere ulaşıncaya kadar kullanıcı **yükü artma** devam eder. Bu genellikle istenen yük değildir, bu nedenle hedef tabanlı yük düzeninde performans sayacı seçimine dikkat edin.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testin ilk yük desenini belirtme:** New Yük Testi Sihirbazı kullanarak bir **yük testi Yük Testi Sihirbazı** bir yük deseni seçersiniz.|-   [Yük desenini değiştirme](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Yük testi için yük desenini düzenleme:** Yük testini oluşturduk sonra, yük desenini **Yük Testi Düzenleyicisi.**|-   [Nasıllı: Adım yükleme deseni için adım rampası zaman özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Yük testi senaryosunu kullanan sanal kullanıcıların web önbelleği verilerini içermesi gerekip gerek olmadığını belirtme:** Yük testinin sanal kullanıcılar için bir web tarayıcısı tarafından gerçekleştirilecek web önbelleğinin benzetimini nasıl etkilediğini değiştirmek için Yeni Kullanıcıların **Yüzdesi** özelliğini değiştirebilirsiniz.|-   [Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Adım yükleme deseni için adım rampası süresi belirtme:** **Step Ramp Time özelliği,** bir adımdan sonrakine (örneğin 100 kullanıcıdan 200 kullanıcıya) kadar olan artışın hemen değil kademeli olarak gerçekleşmesini sağlar.|-   [Nasıllı: Adım yükleme deseni için adım rampası zaman özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Yük desenini değiştirme

Yeni Yük Testi Sihirbazı ile yük testini oluşturduk **sonra,** bir **Yük Testi Düzenleyicisi** ile ilişkili yük düzeni özelliklerini test hedeflerinize uyan düzeylere değiştirmek için Yük Testi Düzenleyicisi'i kullanabilirsiniz.

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

Yük düzeni, yük testi sırasında etkin olan sanal kullanıcı sayısını ve yeni kullanıcıların eklenme oranını belirtir. Kullanılabilir üç desenden birini seçebilirsiniz: adım deseni, sabit ve hedefe dayalı. Daha fazla bilgi için [bkz. Yük testi senaryosunda yük düzenleri olan sanal kullanıcı sayısını belirtme.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

> [!NOTE]
> Yük testi eklentisini kullanarak yük özelliklerinizi program aracılığıyla da değiştirebilirsiniz. Daha fazla bilgi [için, bkz. How to: Create a load test plug-in](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Yük desenini değiştirmek için

1. Yük testi açın.

2. Yük Testi Düzenleyicisi **klasöründeki** Senaryolar klasöründe, için yük desenini düzenlemek istediğiniz senaryoyu genişletin ve senaryonun yük desenini seçin. 

    > [!NOTE]
    > Yük deseni düğümünün ifadesi, yük testinizin senaryo ağacında görüntülendiğinden, yük testini oluşturulduğunda seçtiğiniz yük profilini gösterir. Sabit Yükleme Profili **veya Adım Yükleme** Profili **olabilir.**

3. Özellikler penceresini görüntülemek için **F4** **tuşuna** basın.

     Yük **Düzeni** ve **Parametreler kategorileri** Özellikler **penceresinde** görüntülenir.

4. (İsteğe bağlı) Yük **Düzeni kategorisindeki Pattern** **özelliğini** değiştirme.

     Pattern özelliği  için Step **,** **Constant** ve Goal **Based seçeneklerinizdir.** Yük düzeni türleri hakkında daha fazla bilgi için bkz. Yük testi [senaryosunda yük düzenleri](../test/edit-load-patterns-to-model-virtual-user-activities.md)olan sanal kullanıcı sayısını belirtme.

5. (İsteğe bağlı) Parametreler **kategorisindeki** değerleri değiştirebilirsiniz.

    > [!NOTE]
    > Parametreler için **ayarlayabilirsiniz değerler** Pattern özelliği için seçilen değere **göre** farklılık gösterir.

6. Özellikleri değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra yük testini yeni yük deseniyle çalıştırarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Nasıl olur: Adım yükleme deseni için adım rampası zaman özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)
