---
title: Sanal ağ türlerini belirtin (yük testi)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: b505ae281042264d909b72ff0f7911381a2d8ad8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809878"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Yük testi senaryosunda sanal ağ türlerini belirtme

*Ağ karışımı* , yük testi senaryosunda yükün daha gerçekçi bir şekilde benzetimini yapmanızı sağlar. Yük, tek bir ağ türü yerine farklı ağ türleri karışımı kullanılarak oluşturulur. Son kullanıcıların uygulamalarınızla nasıl etkileşime gireceğini daha yakından bir şekilde oluşturursunuz.

Ağ karışımı, belirli bir *ağ profilini*çalıştıran bir sanal kullanıcının olasılığını belirtir. Ağ profili, uygulama katmanında ağ bant genişliğinin bir simülasyonu olur. Gecikme süresini benzemez.

Bir yük testi oluşturduğunuzda, yükün birden fazla ağ bağlantısı türü aracılığıyla üretilmekte olduğunu benzetmek isteyebilirsiniz. Ağ karışımı birkaç ağ türü sunar. Farklı ağlar benzetilir. Gibi bir seçenek belirlediğinizde `Cable-DSL 1.5Mbps` , seçili bant genişliğinin benzetimini yapmak için bekleme süreleri teste eklenir.

Ağ karışımı diğer karıştırma seçenekleri gibi çalışmaktadır. Ağ türü, ağ karışımına bağlı olarak bir sanal kullanıcıyla ilişkili rastgele bir şekilde seçilir. Bu kullanıcının testleri, karışımında belirttiğiniz olasılığa bağlı olarak belirli bir ağ türü kullanılarak çalıştırılır.

Bir ağ karışımı belirtduktan sonra ağ türlerini ekleyebilir ve kaldırabilirsiniz. Ayrıca, Karışım denetimini kullanarak ağ karışımının dağıtımını de değiştirebilirsiniz.

Karışım denetimi, bir senaryodaki ağların dağıtımını kolayca ayarlamanıza olanak sağlar.

Daha fazla bilgi için bkz. [karışım denetimi hakkında](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Gerçek ağ öykünmesi

Visual Studio, yük testleri de dahil olmak üzere tüm test türleri için yazılım tabanlı doğru ağ öykünmesi kullanır. Gerçek ağ öykünmesi, ağ paketlerinin doğrudan işlemesini sağlayarak ağ koşullarına benzetir. Gerçek ağ öykünücüsü, Ethernet gibi güvenilir bir fiziksel bağlantı kullanarak hem kablolu hem de kablosuz ağların davranışını taklit edebilir. Aşağıdaki ağ öznitelikleri, gerçek ağ öykünmesine dahil edilir:

- Ağ üzerinden gidiş dönüş süresi (gecikme)

- Kullanılabilir bant genişliği miktarı

- Sıraya alma davranışı

- Paket kaybı

- Paketlerin yeniden sıralanması

- Hata yayılmaları.

Gerçek ağ öykünmesi, ağ paketlerinin IP adresleri veya TCP, UDP ve ıCMP gibi protokollere göre filtrelenmesi için esneklik de sağlar.

Gerçek ağ öykünmesi, ağ tabanlı uygulama geliştiricileri ve test ediciler tarafından istenen bir test ortamına öykünmek, performansı değerlendirmek, değişikliğin etkisini tahmin etmek veya teknoloji iyileştirmesi hakkında kararlar almak için kullanılabilir. Gerçek ağ öykünmesi, donanım test bedine kıyasla, çok daha ucuz ve esnek bir çözümdür.

## <a name="to-add-new-networks-to-a-scenario"></a>Bir senaryoya yeni ağlar eklemek için

1. Bir senaryo için ağ karışımını belirtme işlemi sırasında **Ekle**' yi seçin.

     Kılavuza yeni bir ağ girişi eklenir.

    > [!NOTE]
    > **Ağ karışımını düzenle** iletişim kutusunu göstermek için, var olan bir senaryoya sağ tıklayın ve sonra **ağ karışımını düzenle**' yi seçin.

2. **Ağ türü** sütununda, yeni giriş için oku seçin. İstediğiniz ağ türünü seçin.

3. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için bkz. [karışım denetimi hakkında](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Ağ ekleme işiniz bittiğinde **Tamam**' ı seçin.

## <a name="to-remove-networks-from-a-scenario"></a>Bir senaryodan ağları kaldırmak için

1. Bir yük testi açın.

2. Ağı kaldırmak istediğiniz senaryoya sağ tıklayın ve **ağ karışımını düzenle**' yi seçin. **Ağ karışımını düzenle** iletişim kutusu görüntülenir.

3. Kılavuzdaki ağı seçin ve ardından **Kaldır**' ı seçin.

4. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için bkz. [karışım denetimi hakkında](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Ağları kaldırmayı tamamladığınızda **Tamam**' ı seçin.

## <a name="about-the-mix-control"></a>Karıştırma denetimi hakkında

Karışım denetimi, yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yükün yüzdesini ayarlamanıza olanak sağlar. Yüzde değerlerini ayarlamak için kaydırıcıları taşıyın. Ağ türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli bir ağ profilini çalıştıran bir sanal kullanıcının olasılığını belirtir.

Kaydırıcıyı taşıdığınızda, tüm kullanılabilir öğelerin yüzde değerleri değişir. İkiden fazla öğe varsa, eklediğiniz veya kaldırdığınız miktar diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, eklediğiniz veya kaldırdığınız miktar yalnızca kalan kilitlenmemiş öğeler için geçerlidir.

**Dağıtım** düğmesi, yüzde değerlerini tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğe varsa **Dağıt** ' ı seçtiğinizde, yüzde değerleri 34, 33 ve 33 olarak ayarlanır.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan tüm öğeleri geçersiz kılar.

Ayrıca, kaydırıcıları kullanmak yerine, yüzde değerlerini doğrudan sütuna yazmak mümkündür **%** . Doğrudan bir yüzde değeri girerseniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Toplam %100 ' e kadar veya sütuna girilen yüzde değerleri ondalıksa kaydırıcıları devre dışı bırakılır **%** .

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini kabul etmeniz veya geri dönüp bunları ayarlamanız istenir. Bunları olduğu gibi kabul etmek istiyorsanız, bunlar %100 'e eşit olarak dağıtılır.  Örneğin, iki öğe varsa ve bunları el ile %80 ve %40 olarak ayarlarsanız, ilk öğe% 66,67 olarak ayarlanır (80 olarak 120) ve ikinci öğe% 33,33 olarak ayarlanır (40, 120 olarak bölünür).
