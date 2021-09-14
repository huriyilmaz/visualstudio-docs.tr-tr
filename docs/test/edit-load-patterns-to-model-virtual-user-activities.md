---
title: Yük testi için yük desenleri
description: Uygulamanın sağladığı yerleşik yük desenleri hakkında Visual Studio öğrenin. Yük desenini seçin ve özellikleri yük testiniz için uygun düzeylere ayarlayın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634257"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Sanal kullanıcı etkinliklerini modellemek için yük desenlerini düzenleme

Yük düzeni özellikleri, sanal kullanıcı yükünün yük testi sırasında nasıl ayar olduğunu belirtir. Visual Studio üç yerleşik yük deseni sağlar: sabit, adım ve hedef tabanlı. Yük desenini seçer ve özellikleri yük testi hedefleriniz için uygun düzeylere ayarlarsiniz.

Yük düzeni bir senaryonun bileşenidir. Senaryolar, tanımlanan yük düzenleriyle birlikte bir yük testi içerir.

> [!NOTE]
> Tüm Yük Düzenleri'Visual Studio sanal kullanıcıların sanal yükü oluşturulur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Yük düzenleri

### <a name="constant"></a>Sabit

Sabit yük düzeni, yük testi sırasında değişmeyen bir kullanıcı yükü belirtmek için kullanılır. Örneğin, bir web uygulamasında duman testi çalıştırarak 10 kullanıcının hafif, sabit bir yükünü ayarlamak iyi olabilir.

#### <a name="constant-load-pattern-considerations"></a>Sabit yük düzeniyle ilgili dikkat edilmesi gerekenler

Bir yük testinin çalışması sırasında aynı kullanıcı yükünü çalıştırmak için sabit bir yük düzeni kullanılır. Yüksek kullanıcı sayısına sahip sabit bir yük düzeni kullanırken dikkatli olun; bunu yapmak, yük testinin başında sunucunuza veya sunucularınıza makul olmayan ve gerçekçi olmayan bir talepte bulundurabilir. Örneğin, yük testinde giriş sayfasına yapılan istekle başlayan bir web testi varsa ve yük testini 1.000 kullanıcılık sabit bir yük ile ayarıyorsanız, yük testi giriş sayfasına ilk 1.000 isteği mümkün olan en hızlı şekilde göndermektedir. Bu, web sitenize gerçek dünya erişiminin gerçekçi bir simülasyonu olabilir. Bunu azaltmak için kademeli olarak 1.000 kullanıcıya kadar artıran bir adımlı yük düzeni kullanmayı göz önünde bulundurabilirsiniz veya Yük Testi Çalıştırması çalışma süresinde bir Ayarlar. Isınma süresi belirtilirse yük testi, isınma dönemi boyunca yükü kademeli olarak otomatik olarak artıracaktır. Daha fazla bilgi için [bkz. Senaryo başlatma gecikmelerini yapılandırma.](../test/configure-scenario-start-delays.md)

### <a name="step"></a>Adım

Adım yükleme düzeni, tanımlanan maksimum kullanıcı yüküne kadar olan süreyle birlikte artıran bir kullanıcı yükü belirtmek için kullanılır. Adımlama yükleri için İlk Kullanıcı **Sayısı,** En Fazla Kullanıcı **Sayısı,** Adım **Süresi (saniye)** ve Adım Kullanıcı **Sayısı'larını belirtirsiniz.**

Örneğin, İlk Kullanıcı  Sayısı bir, En  Fazla Kullanıcı Sayısı 100, Adım Süresi **(saniye)**  değeri 10 ve Adım Kullanıcı Sayısı 1 olan bir Adım yükü, 1 ile başlayan bir kullanıcı yükü deseni oluşturur ve 100 Kullanıcı'ya ulaşana kadar her 10 saniyede bir 1 artar.

> [!NOTE]
> Toplam test süresi, maksimum kullanıcı yüküne ulaşmak için gereken süreden kısa ise geçen sürenin ardından test durur ve Maksimum Kullanıcı Sayısı hedefine **ulaşmaz.**

Sunucu performansın önemli ölçüde azaldığını bir noktaya ulaşana kadar yükü artırmak için Adım hedef'i kullanabilirsiniz. Yük arttıkça sunucunun sonunda kaynakları da yok olur. Adım yükü, bunun oluştuğu kullanıcı sayısını belirlemek için iyi bir yol sağlar. Adımlama yüküyle, aracıların istenen yükü oluştura olduğundan emin olmak için aracı kaynaklarını yakından izlemelisiniz.

Normalde, verilen yük için iyi ölçümler elde etmek için farklı adım süreleri ve adım kullanıcı sayıları olan birkaç çalıştırma yürütmelisiniz. Genellikle yükler, kullanıcılar eklendiklerine göre her adım için ilk ani artışları gösterir. Yükü bu hıza sahip tutmak, sistem ilk ani artıştan kurtarıldıktan sonra sistem performansını ölçmeye olanak sağlar.

#### <a name="step-load-pattern-considerations"></a>Adım yükü düzeniyle ilgili dikkat edilmesi gerekenler

Kullanıcı yükü arttıkça performansın nasıl değişiklik gösterir olduğunu görmek için yük testi çalıştırtıkça sunucu veya sunucu üzerindeki yükü artırmak için adımlı yük düzeni kullanılabilir. Örneğin, kullanıcı yükü 2.000 kullanıcıya arttıkça sunucu veya sunucularının nasıl performans sergileyecelerini görmek için, aşağıdaki özelliklere sahip bir adım yükleme düzeni kullanarak 10 saatlik bir yük testi çalıştırabilirsiniz:

- **İlk Kullanıcı Sayısı:** 100

- **En Fazla Kullanıcı Sayısı:** 2.000

- **Adım Süresi (saniye):** 1.800

- **Step Ramp Time (saniye)**: 20

- **Adım Kullanıcı Sayısı:** 100

  Bu ayarlar yük testini 100, 200, 300 ve 2.000'e kadar kullanıcı yükünde 30 dakika (1.800 saniye) çalıştırmaktadır. Step **Ramp Time** özelliği, New Yük Testi Sihirbazı'da seçilene bu özelliklerden yalnızca **biri olduğundan, bu özellikten bahsetmeye değer Yük Testi Sihirbazı.** Bu özellik, bir adımdan sonrakine (örneğin, 100 kullanıcıdan 200 kullanıcıya) artışın hemen değil kademeli olarak gerçekleşmesini sağlar. Örnekte, kullanıcı yükü 20 saniyelik bir süre boyunca 100 kullanıcıdan 200 kullanıcıya (her saniye beş kullanıcı artışı) artırılabilir. Daha fazla bilgi için, [bkz. How to: Specify the step ramp time property for a step load pattern](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Hedef tabanlı

Hedef tabanlı yük deseni adım desenini andırır, ancak kullanıcı yükünü performans sayacı eşiklerine ve düzenli kullanıcı yükü ayarlamalarına göre ayarlar. Hedef tabanlı yükler çeşitli amaçlar için yararlıdır:

- Aracıların çıktısını en üst düzeye çıkarma: Aracıların çıkışını en üst düzeye çıkarmak için aracıda anahtar sınırlama ölçümlerini ölçün. Genellikle CPU'dır; Ancak bu bellek de olabilir.

- Hedef sunucuda genellikle CPU olmak kaydıyla hedef kaynak düzeyine ulaşıyor ve aktarım hızını bu düzeyde ölçülmektedir. Bu, sunucudaki tutarlı bir kaynak kullanımı düzeyine göre aktarım hızının çalıştır-çalıştır karşılaştırmalarını yapmaya olanak sağlar.

- Sunucuda bir hedef aktarım hızı düzeyine ulaşma.

  Aşağıdaki tabloda, aşağıdaki özellik ayarlarıyla hedef tabanlı bir desen gösteren bir örnek yer alır:

|Özellik Grubu|Özellik|Değer|
|-|--------------|-|
|Performans Sayacı|Kategori|İşlemci|
|Performans Sayacı|Bilgisayar|ContosoServer1|
|Performans Sayacı|Sayaç|% İşlemci zamanı|
|Performans Sayacı|Örnek|_Toplam|
|Performans Sayacı için Hedef Aralık|Yüksek Uç|90|
|Performans Sayacı için Hedef Aralık|Alt Uç|70|
|Kullanıcı Sayısı Sınırları|İlk Kullanıcı Sayısı|1|
|Kullanıcı Sayısı Sınırları|En Fazla Kullanıcı Sayısı|100|
|Kullanıcı Sayısı Sınırları|En Fazla Kullanıcı Sayısı GeriLeme|5|
|Kullanıcı Sayısı Sınırları|Maksimum Kullanıcı Sayısı Artışı|5|
|Kullanıcı Sayısı Sınırları|En Az Kullanıcı Sayısı|1|

Bu ayarlar, **Yük Testi** Çözümleyicisi'nin test çalıştırması sırasında kullanıcı yükünü 1 ile  100 arasında ayarlamasına neden olur ve `% Processor Time` WebServer01 sayacı ile arasında görünür `70%``90%.`

Her kullanıcı yükü ayarlamanın boyutu En Fazla Kullanıcı Sayısı Artışı ve **En Fazla** Kullanıcı Sayısı **Azaltma ayarlarına göre** belirlenir. Kullanıcı sayısı sınırları En Fazla Kullanıcı Sayısı **ve En Düşük** Kullanıcı Sayısı **özelliklerine göre** ayarlanır.

#### <a name="goal-based-load-pattern-considerations"></a>Hedef tabanlı yük düzeniyle ilgili dikkat edilmesi gerekenler

Hedef tabanlı yük düzeni, sistemin belirli bir kaynak kullanımı düzeyine ulaşmadan önce destekleyene kullanıcı sayısını belirlemek istediğiniz durumlarda kullanışlıdır. Bu seçenek en iyi şekilde, sisteminiz içinde sınırlayıcı kaynağı (yani performans sorunu) zaten belirlediyseniz çalışır.

Örneğin, sisteminiz içinde sınırlayıcı kaynağın veritabanı sunucunuzda CPU olduğunu ve veritabanı sunucusundaki CPU yaklaşık yüzde 75 meşgul olduğunda kaç kullanıcının desteklenecen olduğunu görmek istediğinizi varsayalım. "%Processor Time" performans sayacının değerini yüzde 70 ile yüzde 80 arasında tutma hedefine sahip hedef tabanlı bir yük düzeni kullanabilirsiniz.

Dikkat etmek gereken bir şey, sistemin aktarım hızını sınırlandıran başka bir kaynaktır. Bu tür kaynaklar, hedef tabanlı yük düzeni tarafından belirtilen hedefe hiçbir zaman ulaşılamayacak şekilde neden olabilir. Ayrıca, Maksimum Kullanıcı Sayısı için belirtilen değere ulaşıncaya kadar kullanıcı **yükü artma** devam eder. Bu genellikle istenen yük değildir, bu nedenle hedef tabanlı yük düzeninde performans sayacı seçimine dikkat edin.

## <a name="tasks"></a>Görevler

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Yük testin ilk yük desenini belirtme:** New Yük Testi Sihirbazı kullanarak bir **yük testi Yük Testi Sihirbazı** bir yük deseni seçersiniz.|-   [Yük desenini değiştirme](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Yük testi için yük desenini düzenleme:** Yük testini oluşturdukta, yük desenini **Yük Testi Düzenleyicisi.**|-   [Nasıl olur: Adım yükleme deseni için adım rampası zaman özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Yük testi senaryosunu kullanan sanal kullanıcıların web önbelleği verilerini içermesi gerekip gerek olmadığını belirtme:** Yük testinin sanal kullanıcılar için bir web tarayıcısı tarafından gerçekleştirilecek web önbelleğinin benzetimini nasıl etkilediğini değiştirmek için Yeni Kullanıcıların **Yüzdesi** özelliğini değiştirebilirsiniz.|-   [Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Adım yükleme deseni için adım rampası süresi belirtme:** **Step Ramp Time özelliği,** bir adımdan sonrakine (örneğin 100 kullanıcıdan 200 kullanıcıya) kadar olan artışın hemen değil kademeli olarak gerçekleşmesini sağlar.|-   [Nasıl olur: Adım yükleme deseni için adım rampası zaman özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Yük desenini değiştirme

Yeni Yük Testi Sihirbazı ile yük testini oluşturduk **sonra,** **Yük Testi Düzenleyicisi** senaryoyla ilişkili yük düzeni özelliklerini test hedeflerinizi karşılayacak düzeylere değiştirmek için Yük Testi Düzenleyicisi'i kullanabilirsiniz.

> [!NOTE]
> Yük testi senaryosu özelliklerinin ve açıklamalarının tam listesi için bkz. [Yük testi senaryosu özellikleri.](../test/load-test-scenario-properties.md)

Yük düzeni, yük testi sırasında etkin olan sanal kullanıcı sayısını ve yeni kullanıcıların eklenme oranını belirtir. Kullanılabilir üç desenden birini seçebilirsiniz: adım deseni, sabit ve hedefe dayalı. Daha fazla bilgi için [bkz. Yük testi senaryosunda yük düzenleri olan sanal kullanıcı sayısını belirtme.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

> [!NOTE]
> Yük testi eklentisini kullanarak yük özelliklerinizi program aracılığıyla da değiştirebilirsiniz. Daha fazla bilgi [için, bkz. How to: Create a load test plug-in](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Yük desenini değiştirmek için

1. Yük testi açın.

2. Aşağıdaki **Yük Testi Düzenleyicisi,** *Senaryolar* klasöründe, için yük desenini düzenlemek istediğiniz senaryoyu genişletin ve senaryonun yük desenini seçin.

    > [!NOTE]
    > Yük deseni düğümünün ifadesi, yük testinizin senaryo ağacında görüntülendiğinden, yük testini oluşturulduğunda seçtiğiniz yük profilini gösterir. Sabit Yükleme Profili **veya Adım Yükleme** Profili **olabilir.**

3. Özellikler penceresini görüntülemek için **F4** **tuşuna** basın.

     Yük **Düzeni** ve **Parametreler kategorileri** Özellikler **penceresinde** görüntülenir.

4. (İsteğe bağlı) Yük **Düzeni kategorisindeki Pattern** **özelliğini** değiştirme.

     Pattern özelliği  için Step **,** **Constant** ve Goal **Based seçeneklerinizdir.** Yük düzeni türleri hakkında daha fazla bilgi için bkz. Yük testi senaryosunda yük düzenleri olan sanal [kullanıcı sayısını belirtme.](../test/edit-load-patterns-to-model-virtual-user-activities.md)

5. (İsteğe bağlı) Parametreler **kategorisindeki** değerleri değiştirebilirsiniz.

    > [!NOTE]
    > Parametreler için **ayarlayabilirsiniz değerler** Pattern özelliği için seçilen değere **göre** farklılık gösterir.

6. Özellikleri değiştirmeyi bitirdikten sonra Dosya menüsünde **Kaydet'i** seçin.  Daha sonra yük testini yeni yük deseniyle çalıştırarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [Nasıl kullanılır: Web önbelleği verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Nasıl olur: Adım yükleme deseni için adım rampası zaman özelliğini belirtme](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)
