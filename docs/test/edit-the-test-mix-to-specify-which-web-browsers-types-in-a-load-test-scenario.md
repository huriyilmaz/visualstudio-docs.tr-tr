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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114527"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Yük testi senaryosunda hangi Web tarayıcılarının türlerini belirtmek için test karışımını düzenleyin

*Tarayıcı karışımı* , yük testi senaryosunda yükün daha gerçekçi bir şekilde benzetimini yapmanızı sağlar. Yükleme tek bir Web tarayıcısı yerine bir Web tarayıcıları heterojen karışımı kullanılarak oluşturulur. Uygulamalarınızla birlikte kullanılacak Web tarayıcılarıyla daha yakından bir yaklaşıma oluşturursunuz.

Tarayıcı karışımı, bir yük testi senaryosunda belirli bir Web tarayıcı türü çalıştıran bir sanal kullanıcının olasılığını belirtir. Bir yük testi oluşturduğunuzda, yükün birden fazla Web tarayıcısı aracılığıyla oluşturulmasını taklit etmek isteyebilirsiniz. Sunulan Web tarayıcıları kümesinden karışıma bir Web tarayıcı türü eklediğinizde, bir Web başarım testi tarafından gönderilen her HTTP isteğine seçili Web tarayıcısı için bir dizi ilişkili üst bilgi eklenir.

Tarayıcı karışımı diğer karıştırma seçenekleri gibi çalışmaktadır. Web tarayıcı türü, tarayıcı karışımına bağlı olarak bir sanal kullanıcı ile rasgele ilişkilendirilir. Bu kullanıcının testleri, karışımında belirttiğiniz olasılığa bağlı olarak belirli bir Web tarayıcısında çalıştırılır.

Bir tarayıcı karışımı belirledikten sonra, daha sonra karışıma Web tarayıcı türlerini ekleyebilir ve kaldırabilirsiniz. Ayrıca, Karışım denetimini kullanarak tarayıcı karışımının dağıtımını değiştirebilirsiniz. Karışım denetimi, tarayıcıların bir senaryoya dağıtımını kolayca ayarlamanıza olanak sağlar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Senaryoya yeni tarayıcılar ekleme

### <a name="to-add-new-browsers-to-a-scenario"></a>Senaryoya yeni tarayıcılar eklemek için

1. Bir senaryo için tarayıcı karışımını belirtme sürecinde, **Ekle**' yi seçin.

     Kılavuza yeni bir tarayıcı girişi eklenir.

    > [!NOTE]
    > **Tarayıcı karışımını düzenle** iletişim kutusunu göstermek için, mevcut bir senaryoya sağ tıklayın ve ardından **tarayıcı karışımını düzenle**' yi seçin.

2. **Tarayıcı türü** sütununda, yeni giriş için oku seçin ve istediğiniz tarayıcı türünü seçin.

3. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

4. Tarayıcıları eklemeyi bitirdiğinizde **Tamam**' ı seçin.

## <a name="remove-browsers-from-a-scenario"></a>Senaryolardan tarayıcıları kaldırma

### <a name="to-remove-browsers-from-a-scenario"></a>Bir senaryodan tarayıcıları kaldırmak için

1. Bir yük testi açın.

2. Tarayıcıyı kaldırmak istediğiniz senaryoya sağ tıklayın ve ardından **tarayıcı karışımını düzenle**' yi seçin.

     **Tarayıcı karışımını düzenle** iletişim kutusu görüntülenir.

3. Kılavuzdaki tarayıcıyı seçin ve ardından **Kaldır**' ı seçin.

4. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

5. Tarayıcıları kaldırmayı tamamladığınızda **Tamam**' ı seçin.

## <a name="about-the-mix-control"></a>Karıştırma denetimi hakkında

Karışım denetimi, yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yükün yüzdesini ayarlamanıza olanak sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Tarayıcı türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli bir tarayıcı türünü çalıştıran bir sanal kullanıcının olasılığını belirtir.

Kaydırıcıyı taşıdığınızda, tüm kullanılabilir öğelerin yüzde değerleri değişir. İkiden fazla öğe varsa, eklediğiniz veya kaldırdığınız miktar diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, eklediğiniz veya kaldırdığınız miktar yalnızca kalan kilitlenmemiş öğeler için geçerlidir.

**Dağıtım** düğmesi, yüzde değerlerini tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğe varsa **Dağıt** ' ı seçtiğinizde, yüzde değerleri 34, 33 ve 33 olarak ayarlanır.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan tüm öğeleri geçersiz kılar.

Ayrıca, kaydırıcıları kullanmak yerine, yüzde değerlerini doğrudan sütuna yazmak mümkündür **%** . Doğrudan bir yüzde değeri girerseniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Toplam %100 ' e kadar veya sütuna girilen yüzde değerleri ondalıksa kaydırıcıları devre dışı bırakılır **%** .

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Bunları olduğu gibi kabul etmek istiyorsanız, bunlar %100 'e eşit olarak dağıtılır.  Örneğin, iki öğe varsa ve bunları el ile %80 ve %40 olarak ayarlarsanız, ilk öğe% 66,67 olarak ayarlanır (80 olarak 120) ve ikinci öğe% 33,33 olarak ayarlanır (40, 120 olarak bölünür).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
