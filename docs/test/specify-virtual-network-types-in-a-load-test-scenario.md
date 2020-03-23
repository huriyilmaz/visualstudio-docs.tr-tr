---
title: Bir Yük Testi Senaryosunda Sanal Ağ Türlerini Belirtme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60fa2bd38f3d7e594e9af7ba8ec544518bdbb920
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115304"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Yük testi senaryosunda sanal ağ türlerini belirtin

*Ağ karışımı,* yük testi senaryosunda yükü daha gerçekçi bir şekilde simüle etmek için bir yol sağlar. Yük, tek bir ağ türü yerine ağ türlerinin heterojen bir karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşimde denecek hakkında daha yakın bir yaklaşım oluşturursunuz.

Ağ karışımı, belirli bir *ağ profilini*çalıştıran sanal bir kullanıcının olasılığını belirtir. Ağ profili, uygulama katmanındaki ağ bant genişliğinin simülasyonudur. Gecikme yi simüle etmez.

Bir yük testi oluşturduğunuzda, birden fazla ağ bağlantısı türü aracılığıyla bu yükün oluşturulduğunu simüle etmek isteyebilirsiniz. Ağ karışımı çeşitli ağ türleri sunar. Farklı ağlar simüle edilir. Bir seçenek `Cable-DSL 1.5Mbps`seçtiğinizde, seçilen bant genişliğini simüle etmek için teste bekleme süreleri enjekte edilir.

Ağ karışımı diğer karışım seçenekleri gibi çalışır. Ağ türü, ağ karışımına dayalı olarak sanal bir kullanıcıyla rasgele ilişkilendirilir. Bu kullanıcının testleri, karışımda belirttiğiniz olasılığı temel alan belirli bir ağ türü kullanılarak çalıştırılır.

Bir ağ karışımı nı belirttikten sonra, ağ türlerini ekleyebilir ve kaldırabilirsiniz. Karışım denetimini kullanarak ağ karışımının dağılımını da değiştirebilirsiniz.

Karışım denetimi, bir senaryodaki ağların dağılımını kolayca ayarlamanızı sağlar.

Daha fazla bilgi için [karışım denetimi hakkında](../test/specify-virtual-network-types-in-a-load-test-scenario.md)bilgi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Gerçek ağ öykünme

Visual Studio, yük testleri de dahil olmak üzere tüm test türleri için yazılım tabanlı gerçek ağ öykünme kullanır. Gerçek ağ öykünme, ağ paketlerinin doğrudan manipülasyonu yla ağ koşullarını simüle eder. Gerçek ağ emülatörü, Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri gerçek ağ öykünme dahil edilmiştir:

- Ağ üzerinden gidiş-dönüş süresi (gecikme süresi)

- Kullanılabilir bant genişliği miktarı

- Kuyruk davranışı

- Paket kaybı

- Paketlerin yeniden sıralanması

- Hata yayılmaları.

Gerçek ağ öykünasyonu, IP adreslerine veya TCP, UDP ve ICMP gibi protokollere dayalı ağ paketlerini filtrelemede esneklik de sağlar.

Gerçek ağ öykünmesi, ağ tabanlı uygulama geliştiricileri ve sınananları tarafından istenilen test ortamını taklit etmek, performansı değerlendirmek, değişimin etkisini tahmin etmek veya teknoloji optimizasyonu hakkında kararlar almak için kullanılabilir. Donanım test yatakları ile karşılaştırıldığında, gerçek ağ öykünme çok daha ucuz ve daha esnek bir çözümdür.

## <a name="to-add-new-networks-to-a-scenario"></a>Senaryoya yeni ağlar eklemek için

1. Bir senaryo için ağ karışımını belirtme işlemi sırasında **Ekle'yi**seçin.

     Kılavuza yeni bir ağ girişi eklenir.

    > [!NOTE]
    > **Ağı Karıştır'ı Edit** iletişim kutusunu görüntülemek için varolan bir senaryoyu sağ tıklatın ve ardından **Ağ Karışımını Edit'i**seçin.

2. Ağ **Türü** sütununda, yeni giriş için oku seçin. İstenilen ağ türünü seçin.

3. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışım denetimi hakkında](../test/specify-virtual-network-types-in-a-load-test-scenario.md)bilgi.

4. Ağ eklemeyi bitirdiğinizde **Tamam'ı**seçin.

## <a name="to-remove-networks-from-a-scenario"></a>Ağları senaryodan kaldırmak için

1. Bir yük testi açın.

2. Ağı kaldırmak istediğiniz senaryoyu sağ tıklatın ve **Ağ Karışımını Edit'i**seçin. **Ağı Karıştır'ı Edit** iletişim kutusu görüntülenir.

3. Kılavuzdaki ağı seçin ve ardından **Kaldır'ı**seçin.

4. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışım denetimi hakkında](../test/specify-virtual-network-types-in-a-load-test-scenario.md)bilgi.

5. Ağları kaldırmayı bitirdiğinizde **Tamam'ı**seçin.

## <a name="about-the-mix-control"></a>Karışım kontrolü hakkında

Karışım denetimi, bir yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yük yüzdesini ayarlamanızı sağlar. Yüzde değerlerini ayarlamak için kaydırıcıları taşıyın. Ağ türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli bir ağ profili çalıştıran sanal bir kullanıcının olasılığını belirtir.

Bir kaydırıcıyı taşıdığınızda, kullanılabilir tüm öğelerin yüzde değerleri değişir. İkiden fazla öğeniz varsa, eklediğiniz veya kaldırdığınız tutar diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Daha sonra, bir kaydırıcıyı taşıdığınızda, eklediğiniz veya kaldırdığınız tutar yalnızca kalan kilitsiz öğelere uygulanır.

**Dağıt** düğmesi, yüzde değerlerini tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğeniz varsa, **Dağıt'ı** seçerek yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.

Kaydırıcıları kullanmak yerine yüzde değerlerini **%** doğrudan sütuna yazmak da mümkündür. Doğrudan yüzde değeri girerseniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Toplam %100'e kadar eklenmediği veya **%** sütuna girilen yüzde değerleri ondalık değerler olduğunda kaydırıcılar devre dışı bırakılır.

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmenizi veya geri dönüp ayarlamanız istenir. Onları oldukları gibi kabul etmeyi seçerseniz, bunlar %100'e eşit olarak eşit olarak değerlendirilecektir.  Örneğin, iki öğeniz varsa ve bunları el ile %80 ve %40 olarak ayarlarsanız, ilk öğe %66,67 (80 120'ye bölünür) olarak ayarlanır ve ikinci öğe %33,33 (40 bölünerek 120'ye bölünür).
