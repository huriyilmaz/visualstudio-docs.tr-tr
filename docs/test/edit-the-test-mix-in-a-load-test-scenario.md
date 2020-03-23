---
title: Yük Testi Senaryosu için test karışımı
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
ms.openlocfilehash: 4a52d660140416ce829493a733171cfcf64ebbe4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595936"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Yükleme testi senaryosuna hangi web performansı, birim ve kodlanmış Kullanıcı Arabirimi testlerini ekleyip içerecek lerini belirtmek için test karışımını düzenleme

Bir senaryonun *test karışımı,* senaryoda bulunan web performansı ve birim testlerinin seçimi ve senaryodaki bu testlerin dağılımının bir birleşimidir. Dağıtım, yük testi çalışması sırasında belirli bir testin sanal bir kullanıcı tarafından seçilme olasılığını belirtebileceğiniz bir ayardır.

Bir yükleme testine bir dizi test ekledikten sonra, *test karışımı* diğer karışım seçenekleri gibi çalışır. Sanal bir kullanıcı, karışımda belirttiğiniz olasılığı temel alan bir testi rasgele seçer. Örneğin, her biri karışımda yüzde 50 olmak üzere iki testiniz varsa, yeni bir sanal kullanıcı ilk testi yaklaşık olarak yarı zamanlı olarak çalıştırmayı seçer. 50/50 karışımında, bir test uzun, diğeri kısa ise, uzun testten daha fazla yük gelir.

Karışıma testler ekledikten sonra, bunları kaldırabilirsiniz. Ayrıca karışım denetimini kullanarak test karışımının dağılımını değiştirebilirsiniz. Karışım denetimi, bir senaryodaki testlerin dağıtımını kolayca ayarlamanızı sağlar.

> [!NOTE]
> Dağıtım, yük testi çalışması sırasında belirli bir testin sanal bir kullanıcı tarafından seçilme olasılığının bir ölçüsüdür. Dağılım yüzde olarak ifade edilir. Bu nedenle, bir senaryoda bulunan tüm testler için dağıtım numaralarıtoplamı 100'dür. Örneğin, bir senaryo yalnızca bir test içeriyorsa, bu testin dağılımı yüzde 100'dür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Varolan bir senaryoda test karışımına yeni testler ekleme

**Yeni Yük Testi Sihirbazı'nı**kullanarak yeni bir senaryo oluşturduğunuzda, yeni senaryonun test karışımına eklemek için web performansını ve birim testlerini belirtebilirsiniz.

Yük Testi Düzenleyicisi'ni kullanarak senaryonun metin karışımına **Load Test Editor**daha fazla web performansı ve birim testleri ekleyebilirsiniz.

![Varolan bir yük testine test ekleme](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Varolan bir senaryoya daha fazla test eklemek için

1. Bir yük testi açın.

2. Load **Test Editor'da**varolan bir senaryoyu sağ tıklatın ve ardından **Testler Ekle'yi**seçin.

     **Testler Ekle** iletişim kutusu görüntülenir. Çözümünüzde zaten senaryonuzda bulunmayan tüm web performansı, birim ve kodlanmış UI testleri senaryoya eklemek için kullanılabilir.

3. Kullanılabilir **testler** bölmesinde, eklemek istediğiniz web performansı, birim ve kodlanmış UI testlerini seçin. **Testleri Seçili testler** bölmesine eklemek için doğru oku seçin.

4. Test eklemeyi bitirdiğinizde **Tamam'ı**seçin.

     Testler test karışımına eklenir. Test karışımındaki testlere otomatik olarak yeni bir dağıtım atanır.

5. (İsteğe bağlı) Test dağıtımını belirtmek için karıştırma denetimini ayarlayın. Daha fazla bilgi için [karışım denetimi hakkında](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)bilgi.

## <a name="remove-tests-from-a-scenario"></a>Testleri senaryodan kaldırma
![Bir testi varolan bir yük testinden kaldırma](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Bir senaryodan testleri kaldırmak için

1. Bir yük testi açın.

2. Yük **Testi**Düzenleyicisi'nde, yük testi ağacında, bir testi kaldırmak istediğiniz senaryoyu sağ tıklatın ve **Test Karışımını Edit'i**seçin. **Test Mix'i Edit iletişim** kutusu görüntülenir.

3. Kılavuzda web performansı, birim veya kodlanmış UI testini seçin ve ardından **Kaldır'ı**seçin.

    > [!NOTE]
    > Testi kaldırdıktan sonra, test karışımını tercih ettiğiniz dağılıma göre ayarlayın.

4. Kaldırma testlerini bitirdiğinizde **Tamam'ı**seçin.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a>Karışım Kontrolü Hakkında
Karışım denetimi, bir yük testi senaryosunda testler, tarayıcı türleri veya ağ türleri arasında dağıtılan yük yüzdesini ayarlamanızı sağlar. Yüzde değerleri kaydırıcılar hareket ettirilerek ayarlanır. Testler için karışımı ayarlamak, bir sanal kullanıcının bir yük testi senaryosunda belirli bir testi çalıştırma olasılığını belirtir.

Bir kaydırıcıyı taşıdığınızda, kullanılabilir tüm öğelerin yüzde değerleri değişir. İkiden fazla öğeniz varsa, eklediğiniz veya kaldırdığınız tutar diğer öğeler arasında eşit olarak dağıtılır. Bu davranışı geçersiz kılmak mümkündür. Belirli bir öğe için kilit sütunundaki onay kutusunu seçerseniz, o öğe için belirtilen yüzde değerini kilitlersiniz. Daha sonra, bir kaydırıcıyı taşıdığınızda, eklediğiniz veya kaldırdığınız tutar yalnızca kalan kilitsiz öğelere uygulanır.

**Dağıt** düğmesi, yüzdeleri tüm öğeler arasında eşit olarak ayırmak için kullanılır. Örneğin, üç öğeniz varsa, **Dağıt'ı** seçerek yüzde değerlerini 34, 33 ve 33 olarak ayarlar.

> [!WARNING]
> **Dağıt** düğmesi kilitli olan öğeleri geçersiz kılar.

Kaydırıcıları kullanmak yerine yüzde değerlerini **%** doğrudan sütuna yazmak da mümkündür. Doğrudan yüzde değeri girerseniz, diğer öğeler otomatik olarak ayarlanmaz.

> [!NOTE]
> Toplam %100'e kadar eklenmediği veya **%** sütuna girilen yüzde değerleri ondalık değerler olduğunda kaydırıcılar devre dışı bırakılır.

Yüzde değerlerini el ile girdiğinizde, tüm öğelerin toplamının %100 olduğundan emin olmanız gerekir. Bir karışımı kaydettiğinizde, toplam %100 değilse, yüzde değerlerini oldukları gibi kabul etmeniz veya geri gidip onları ayarlamanız istenir. Onları oldukları gibi kabul etmeyi seçerseniz, bunlar %100'e eşit olarak eşit olarak değerlendirilecektir.  Örneğin, iki öğeniz varsa ve bunları el ile %80 ve %40 olarak ayarlarsanız, ilk öğe %66,67 (80 120'ye bölünür) olarak ayarlanır ve ikinci öğe %33,33 (40 bölünerek 120'ye bölünür).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
