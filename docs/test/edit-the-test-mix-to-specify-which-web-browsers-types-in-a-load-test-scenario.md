---
title: Yük testi için tarayıcı test karışımı
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 394331ae06760e0547cfc2b5a37a6dcd357e3614
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114527"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Yükleme testi senaryosunda hangi web tarayıcılarının türlerini belirlemek için test karışımını düzenleme

*Tarayıcı karışımı,* yük testi senaryosunda yükü daha gerçekçi bir şekilde simüle etmek için bir yol sağlar. Yük tek bir web tarayıcısı yerine web tarayıcılarının heterojen bir karışımı kullanılarak oluşturulur. Uygulamalarınızda kullanılacak web tarayıcılarının daha yakın bir tahminini oluşturursunuz.

Tarayıcı karışımı, yükleme testi senaryosunda belirli bir web tarayıcısı türünü çalıştıran sanal bir kullanıcının olasılığını belirtir. Bir yük testi oluşturduğunuzda, yükün birden fazla web tarayıcısı aracılığıyla oluşturulduğunu simüle etmek isteyebilirsiniz. Sağlanan web tarayıcıları kümesinden karışıma bir web tarayıcısı türü eklediğinizde, seçilen web tarayıcısı için ilişkili üstbilgi kümesi, bir web performans testi tarafından gönderilen her HTTP isteğine eklenir.

Tarayıcı karışımı diğer karışım seçenekleri gibi çalışır. Bir web tarayıcısı türü, tarayıcı karışımına bağlı olarak sanal bir kullanıcıyla rasgele ilişkilendirilir. Bu kullanıcının testleri, karışımda belirttiğiniz olasılığı temel alan belirli bir web tarayıcısında çalıştırılır.

Bir tarayıcı karışımı belirttikten sonra, daha sonra karışıma web tarayıcısı türlerini ekleyebilir ve kaldırabilirsiniz. Ayrıca, karıştırma denetimini kullanarak tarayıcı karışımının dağıtımını da değiştirebilirsiniz. Karışım denetimi, bir senaryoda tarayıcıların dağıtımını kolayca ayarlamanızı sağlar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Senaryoya yeni tarayıcılar ekleme

### <a name="to-add-new-browsers-to-a-scenario"></a>Senaryoya yeni tarayıcılar eklemek için

1. Bir senaryo için tarayıcı karışımı nı belirtme sürecinde yken **Ekle'yi**seçin.

     Kılavuza yeni bir tarayıcı girişi eklenir.

    > [!NOTE]
    > **Tarayıcı Karıştır'ı Edit** iletişim kutusunu görüntülemek için varolan bir senaryoyu sağ tıklatın ve ardından **Tarayıcı Karışımını Edit'i**seçin.

2. Tarayıcı **Türü** sütununda, yeni giriş için oku seçin ve istediğiniz tarayıcı türünü seçin.

3. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

4. Tarayıcı eklemeyi bitirdiğinizde **Tamam'ı**seçin.

## <a name="remove-browsers-from-a-scenario"></a>Tarayıcıları senaryodan kaldırma

### <a name="to-remove-browsers-from-a-scenario"></a>Tarayıcıları bir senaryodan kaldırmak için

1. Bir yük testi açın.

2. Tarayıcıyı kaldırmak istediğiniz senaryoyu sağ tıklatın ve ardından **Tarayıcı Karışımını Edit'i**seçin.

     **Tarayıcı Karıştır'ı Edit** iletişim kutusu görüntülenir.

3. Kılavuzdaki tarayıcıyı seçin ve ardından **Kaldır'ı**seçin.

4. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

5. Tarayıcıları kaldırmayı bitirdiğinizde **Tamam'ı**seçin.

## <a name="about-the-mix-control"></a>Karışım kontrolü hakkında

Karışım denetimi, bir yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yük yüzdesini ayarlamanızı sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Tarayıcı türleri için karışımı ayarlamak, yükleme testi senaryosunda belirli bir tarayıcı türü çalıştıran sanal bir kullanıcının olasılığını belirtir.

Bir kaydırıcıyı taşıdığınızda, kullanılabilir tüm öğelerin yüzde değerleri değişir. İkiden fazla öğeniz varsa, eklediğiniz veya kaldırdığınız tutar diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Daha sonra, bir kaydırıcıyı taşıdığınızda, eklediğiniz veya kaldırdığınız tutar yalnızca kalan kilitsiz öğelere uygulanır.

**Dağıt** düğmesi, yüzde değerlerini tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğeniz varsa, **Dağıt'ı** seçerek yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.

Kaydırıcıları kullanmak yerine yüzde değerlerini **%** doğrudan sütuna yazmak da mümkündür. Doğrudan yüzde değeri girerseniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Toplam %100'e kadar eklenmediği veya **%** sütuna girilen yüzde değerleri ondalık değerler olduğunda kaydırıcılar devre dışı bırakılır.

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Onları oldukları gibi kabul etmeyi seçerseniz, bunlar %100'e eşit olarak eşit olarak değerlendirilecektir.  Örneğin, iki öğeniz varsa ve bunları el ile %80 ve %40 olarak ayarlarsanız, ilk öğe %66,67 (80 120'ye bölünür) olarak ayarlanır ve ikinci öğe %33,33 (40 bölünerek 120'ye bölünür).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
