---
title: Yük testi için tarayıcı test karışımı
description: Bir yük testi senaryosunda yükü daha gerçekçi bir şekilde simüle etmek için bir yol veren tarayıcı karışımını düzenlemeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 26098ec0a63d932ed7376ca8c5245c7c39d6ba01
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026752"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Yük testi senaryosunda hangi web tarayıcılarının türlerini belirterek test karışımını düzenleyin

Tarayıcı *karışımı,* yük testi senaryosunda yükü daha gerçekçi bir şekilde simüle etmek için bir yol sağlar. Yük, tek bir web tarayıcısı yerine web tarayıcılarının heterojen bir karışımı kullanılarak oluşturulur. Uygulamalarınız ile kullanılacak web tarayıcıları hakkında daha yakın bir tahmin oluşturursanız.

Tarayıcı karışımı, bir yük testi senaryosunda belirli bir web tarayıcısı türünü çalıştıran bir sanal kullanıcının olasılığını belirtir. Bir yük testi oluşturduktan sonra yükün birden fazla web tarayıcısı üzerinden oluşturularak simülasyonunu yapmak iyi olabilir. Sağlanan web tarayıcısı kümesinden karışımına bir web tarayıcısı türü eklerken, bir web performans testi tarafından gönderilen her HTTP isteğine seçilen web tarayıcısı için ilişkili üst bilgiler kümesi eklenir.

Tarayıcı karışımı diğer karıştırma seçenekleri gibi çalışır. Web tarayıcısı türü, tarayıcı karışımına göre rastgele bir sanal kullanıcıyla ilişkilendirildi. Bu kullanıcının testleri, karışımında belirttiğiniz olasılık temel alarak belirli bir web tarayıcısında çalışır.

Bir tarayıcı karışımı belirttikten sonra, daha sonra karmaya web tarayıcısı türleri ekleyebilir ve kaldırabilirsiniz. Ayrıca, karma denetimi kullanarak tarayıcı karışımının dağıtımını değiştirebilirsiniz. Karma denetimi, bir senaryoda tarayıcıların dağıtımını kolayca ayarlamanıza olanak sağlar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>Senaryoya yeni tarayıcılar ekleme

### <a name="to-add-new-browsers-to-a-scenario"></a>Bir senaryoya yeni tarayıcılar eklemek için

1. Senaryo için tarayıcı karışımını belirtme sürecinde Ekle'yi **seçin.**

     Kılavuza yeni bir tarayıcı girişi eklenir.

    > [!NOTE]
    > Tarayıcı Karışımını **Düzenle iletişim kutusunu** görüntülemek için mevcut bir senaryoya sağ tıklayın ve Ardından Tarayıcı Karışımını **Düzenle'yi seçin.**

2. Tarayıcı **Türü sütununda,** yeni girişin okunu seçin ve istediğiniz tarayıcı türünü seçin.

3. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

4. Tarayıcı eklemeyi bitirdikten sonra Tamam'ı **seçin.**

## <a name="remove-browsers-from-a-scenario"></a>Tarayıcıları bir senaryodan kaldırma

### <a name="to-remove-browsers-from-a-scenario"></a>Tarayıcıları bir senaryodan kaldırmak için

1. Yük testi açın.

2. Tarayıcıyı kaldırmak istediğiniz senaryoya sağ tıklayın ve Ardından Tarayıcı Karışımını **Düzenle'yi seçin.**

     Tarayıcı **Karışımını Düzenle** iletişim kutusu görüntülenir.

3. Kılavuzda tarayıcıyı seçin ve ardından **Kaldır'ı seçin.**

4. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın.

5. Tarayıcıları kaldırmayı bitirdikten sonra Tamam'ı **seçin.**

## <a name="about-the-mix-control"></a>Karma denetimi hakkında

Karma denetimi, yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yük yüzdesini ayarlamanıza olanak sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Tarayıcı türleri için karışımı ayarlamak, bir yük testi senaryosunda belirli bir tarayıcı türünü çalıştıran bir sanal kullanıcının olasılığını belirtir.

Kaydırıcıyı hareket ettirin, kullanılabilir tüm öğelerin yüzde değerleri değişir. İkiden fazla öğeye sahip olursanız, ekley veya kaldır tutarı diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından kaydırıcıyı taşısanız veya kaldırsanız bile yalnızca kilidi açık kalan öğelere uygulanır.

Dağıt **düğmesi,** yüzde değerlerini tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğe varsa Dağıt'ın seçimi yüzde değerlerini 34, 33 ve 33 olarak ayarlar. 

> [!WARNING]
> Dağıt **düğmesi** kilitlenmiş tüm öğeleri geçersiz kılar.

Kaydırıcıları kullanmak yerine yüzde değerlerini doğrudan **%** sütuna da yazabilirsiniz. Yüzde değerini doğrudan girersiniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Kaydırıcılar, toplam %100'e kadar değer eklemezse veya sütuna girilen yüzde değerleri ondalık **%** olduğunda devre dışı bırakılır.

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Bunları olduğu gibi kabul edersiniz, bunlar %100'e prorat edilir.  Örneğin, iki öğeniz varsa ve bunları el ile %80 ve %40 olarak ayarsanız, ilk öğe %66,67(80 bölü 120) olarak, ikinci öğe ise %33,33 (40'a bölünmüş 120) olarak ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
