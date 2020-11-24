---
title: Yük testi senaryosu için test karışımı
description: Web performansı ve birim testlerinin seçiminin ve bu testlerin dağılımının birleşimi olan bir senaryonun test karışımını nasıl düzenleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6681b8aead05a180df04b1c3953002aa832a281
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441384"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Yük testi senaryosuna hangi Web performansı, birim ve kodlanmış UI testlerinin ekleneceğini belirlemek için test karışımını düzenleyin

Bir senaryonun *Test karışımı* , senaryoda yer alan Web performansı ve birim testlerinin seçiminin bir birleşimidir ve bu testlerin senaryoda bu testlerin dağıtılması. Dağıtım, bir yük testi çalıştırması sırasında belirli bir testin bir sanal kullanıcı tarafından seçileme olasılığını belirtebileceğiniz bir ayardır.

Bir yük testine bir test kümesi ekledikten sonra, *Test karışımı* diğer karıştırma seçenekleri gibi çalışmaktadır. Bir Sanal Kullanıcı, karışımda belirttiğiniz olasılığa göre rastgele bir testi seçer. Örneğin, karışımında yüzde 50 olan iki testiniz varsa, yeni bir Sanal Kullanıcı ilk testi yaklaşık olarak bir kez çalıştırmayı seçer. 50/50 karışımında, bir test uzun ve diğeri kısaysa, uzun testten daha fazla yük gelir.

Karışıma testler ekledikten sonra bunları kaldırabilirsiniz. Ayrıca, Karışım denetimini kullanarak test karışımının dağıtımını değiştirebilirsiniz. Karışım denetimi, bir senaryodaki testlerin dağıtımını kolayca ayarlamanıza olanak sağlar.

> [!NOTE]
> Dağıtım, bir yük testi çalıştırması sırasında belirli bir testin bir sanal kullanıcı tarafından seçilme olasılığının bir ölçümüdür. Dağıtım bir yüzde olarak ifade edilir. Bu nedenle, bir senaryoda yer alan tüm testlerin dağıtım numaralarının toplamı 100 ' dir. Örneğin, bir senaryo yalnızca bir test içeriyorsa, bu test için dağıtım yüzde 100 ' dir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Mevcut bir senaryoda bir test karışımına yeni testler ekleme

Yeni **Yük Testi Sihirbazı** kullanarak yeni bir senaryo oluşturduğunuzda, yeni senaryonun test karışımına eklemek için Web performansını ve birim testlerini belirtebilirsiniz.

**Yük Testi Düzenleyicisi** kullanarak senaryonun metin karışımına daha fazla Web performansı ve birim testi ekleyebilirsiniz.

![Var olan bir yük testine test ekleme](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Mevcut senaryoya daha fazla test eklemek için

1. Bir yük testi açın.

2. **Yük Testi Düzenleyicisi**, var olan bir senaryoya sağ tıklayıp **Test Ekle**' yi seçin.

     **Testler ekle** iletişim kutusu görüntülenir. Çözümünüzde zaten olmayan çözümünüzdeki tüm Web performansı, birim ve kodlanmış UI testleri senaryoya eklemek için kullanılabilir.

3. **Kullanılabilir testler** bölmesinde, eklemek istediğiniz Web performansı, birim ve kodlanmış UI testlerini seçin. Testleri **Seçili testler** bölmesine eklemek için sağ oku seçin.

4. Testleri eklemeyi bitirdiğinizde **Tamam**' ı seçin.

     Testler test karışımına eklenir. Test karışımındaki testlere otomatik olarak yeni bir dağıtım atanır.

5. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için bkz. [karışım denetimi hakkında](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Senaryolardan testleri kaldırma
![Varolan bir yük testinin bir testini kaldırma](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Bir senaryodan testleri kaldırmak için

1. Bir yük testi açın.

2. **Yük Testi Düzenleyicisi**, yük testi ağacında, testi kaldırmak istediğiniz senaryoya sağ tıklayın ve **test karışımını düzenle**' yi seçin. **Test karışımını düzenle** iletişim kutusu görüntülenir.

3. Kılavuzda Web performansı, birim veya kodlanmış UI testini seçin ve ardından **Kaldır**' ı seçin.

    > [!NOTE]
    > Testi kaldırdıktan sonra, test karışımını tercih ettiğiniz dağıtıma ayarlayın.

4. Testleri kaldırmayı bitirdiğinizde **Tamam**' ı seçin.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a> Karıştırma denetimi hakkında
Karışım denetimi, yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yükün yüzdesini ayarlamanıza olanak sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Testler için karışımı ayarlamak, bir sanal kullanıcının bir yük testi senaryosunda belirli bir testi çalıştırma olasılığını belirtir.

Kaydırıcıyı taşıdığınızda, tüm kullanılabilir öğelerin yüzde değerleri değişir. İkiden fazla öğe varsa, eklediğiniz veya kaldırdığınız miktar diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Ardından, bir kaydırıcıyı taşıdığınızda, eklediğiniz veya kaldırdığınız miktar yalnızca kalan kilitlenmemiş öğeler için geçerlidir.

**Dağıt** düğmesi, yüzdeleri tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğe varsa **Dağıt** ' ı seçtiğinizde, yüzde değerleri 34, 33 ve 33 olarak ayarlanır.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan tüm öğeleri geçersiz kılar.

Ayrıca, kaydırıcıları kullanmak yerine, yüzde değerlerini doğrudan sütuna yazmak mümkündür **%** . Doğrudan bir yüzde değeri girerseniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Toplam %100 ' e kadar veya sütuna girilen yüzde değerleri ondalıksa kaydırıcıları devre dışı bırakılır **%** .

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Bunları olduğu gibi kabul etmek istiyorsanız, bunlar %100 'e eşit olarak dağıtılır.  Örneğin, iki öğe varsa ve bunları el ile %80 ve %40 olarak ayarlarsanız, ilk öğe% 66,67 olarak ayarlanır (80 olarak 120) ve ikinci öğe% 33,33 olarak ayarlanır (40, 120 olarak bölünür).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleniyor](../test/edit-load-test-scenarios.md)
