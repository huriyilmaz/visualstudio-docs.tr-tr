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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115304"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Yük testi senaryosunda sanal ağ türlerini belirtme

*Ağ karışımı* , yük testi senaryosunda yükün daha gerçekçi bir şekilde benzetimini yapmanızı sağlar. Yük, tek bir ağ türü yerine farklı ağ türleri karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşime gireceğini daha yakından bir şekilde oluşturursunuz.

Ağ karışımı, belirli bir *ağ profilini*çalıştıran bir sanal kullanıcının olasılığını belirtir. Ağ profili, uygulama katmanında ağ bant genişliğinin bir simülasyonu olur. Gecikme süresini benzemez.

Bir yük testi oluşturduğunuzda, yükün birden fazla ağ bağlantısı türü aracılığıyla üretilmekte olduğunu benzetmek isteyebilirsiniz. Ağ karışımı birkaç ağ türü sunar. Farklı ağlar benzetilir. `Cable-DSL 1.5Mbps`gibi bir seçenek belirlediğinizde, seçili bant genişliğinin benzetimini yapmak için bekleme süreleri teste eklenir.

Ağ karışımı diğer karıştırma seçenekleri gibi çalışmaktadır. Ağ türü, ağ karışımına bağlı olarak bir sanal kullanıcıyla ilişkili rastgele bir şekilde seçilir. Bu kullanıcının testleri, karışımında belirttiğiniz olasılığa bağlı olarak belirli bir ağ türü kullanılarak çalıştırılır.

Bir ağ karışımı belirtduktan sonra ağ türlerini ekleyebilir ve kaldırabilirsiniz. Ayrıca, Karışım denetimini kullanarak ağ karışımının dağıtımını de değiştirebilirsiniz.

Karışım denetimi, bir senaryodaki ağların dağıtımını kolayca ayarlamanıza olanak sağlar.

Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Gerçek ağ öykünmesi

Visual Studio, yük testleri de dahil olmak üzere tüm test türleri için yazılım tabanlı doğru ağ öykünmesi kullanır. Gerçek ağ öykünmesi ağ paketlerinin doğrudan düzenlenmesiyle ağ koşullarının benzetimini yapar. Gerçek ağ öykünücü Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri gerçek ağ öykünmesine dahil edilir:

- Ağ üzerinden gidiş dönüş süresi (gecikme)

- Kullanılabilir bant genişliği

- Sıraya alma davranışı

- Paket kaybı

- Paketlerin yeniden sıralanması

- Hata yayılmaları.

Gerçek ağ öykünmesi aynı zamanda IP adresleri veya TCP, UDP ve ICMP gibi protokollere dayanan ağ paket filtrelemelerinde esneklik sağlar.

Gerçek ağ öykünmesi, ağ tabanlı uygulama geliştiricileri ve test ediciler tarafından istenen bir test ortamına öykünmek, performansı değerlendirmek, değişikliğin etkisini tahmin etmek veya teknoloji iyileştirmesi hakkında kararlar almak için kullanılabilir. Donanım test yataklarıyla karşılaştırıldığında gerçek ağ öykünmesi çok daha ucuz ve daha esnek bir çözüm ' dir.

## <a name="to-add-new-networks-to-a-scenario"></a>Bir senaryoya yeni ağlar eklemek için

1. Bir senaryo için ağ karışımını belirtme işlemi sırasında **Ekle**' yi seçin.

     Kılavuza yeni bir ağ girişi eklenir.

    > [!NOTE]
    > **Ağ karışımını düzenle** iletişim kutusunu göstermek için, var olan bir senaryoya sağ tıklayın ve sonra **ağ karışımını düzenle**' yi seçin.

2. **Ağ türü** sütununda, yeni giriş için oku seçin. İstediğiniz ağ türünü seçin.

3. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Ağ ekleme işiniz bittiğinde **Tamam**' ı seçin.

## <a name="to-remove-networks-from-a-scenario"></a>Bir senaryodan ağları kaldırmak için

1. Bir yük testi açın.

2. Ağı kaldırmak istediğiniz senaryoya sağ tıklayın ve **ağ karışımını düzenle**' yi seçin. **Ağ karışımını düzenle** iletişim kutusu görüntülenir.

3. Kılavuzdaki ağı seçin ve ardından **Kaldır**' ı seçin.

4. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışımı denetimi ile ilgili](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Ağları kaldırmayı tamamladığınızda **Tamam**' ı seçin.

## <a name="about-the-mix-control"></a>Karışım denetimi hakkında

Karışım denetimi, yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yükün yüzdesini ayarlamanıza olanak sağlar. Yüzde değerlerini ayarlamak için kaydırıcıları taşıyın. Ağ türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli bir ağ profilini çalıştıran bir sanal kullanıcının olasılığını belirtir.

Bir kaydırıcı taşıdığınızda, tüm kullanılabilir öğeleri yüzde değerlerini değiştirin. İkiden fazla öğe varsa, ekleme veya kaldırma miktarı diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, ekleme veya kaldırma miktarı yalnızca kilidi kalan tüm öğeleri uygulanır.

**Dağıt** düğmesi tüm öğeler arasında eşit yüzde değerlerini ayırmak için kullanılır. Örneğin, üç öğeye sahipseniz seçme **Dağıt** yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.

Yüzde değerlerini doğrudan yazmak mümkündür **%** Kaydırıcıları kullanmak yerine sütun. Bir yüzde değeri doğrudan giriyorsanız, diğer öğeler otomatik olarak ayarlar değil.

> [!NOTE]
> Toplam % 100 eklemez veya girilen yüzde değerleri kaydırıcılar devre dışı **%** ondalıksa sütun.

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini kabul etmeniz veya geri dönüp bunları ayarlamanız istenir. Oldukları gibi bunları kabul etmeyi seçerseniz, % 100 olarak dağıtılır.  Örneğin, iki öğeniz varsa ve el ile bunları %80 ve % 40 olarak ayarlarsanız, ilk öğeye (120 bölünmüş 80) % 66.67 ayarlayın ve ikinci öğe %33.33 (40 120 bölünmüş) ayarlayın.
