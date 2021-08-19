---
title: Bir Simgenin veya Dekoratörün Görünürlüğünü Denetleme
description: Modelde özelliklerin durumuna bağlı olarak bir simgenin veya dekoratörün görünürlüğünü denetlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 54dd15b59628883d42f28ab9988ae75d0c7bbd52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061369"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir Simgenin veya Dekoratörün Görünürlüğünü Denetleme
*Dekoratör,* etki alanına özgü bir dilde (DSL) bir şekilde görünen bir simge veya metin satırıdır. Modelde özelliklerin durumuna bağlı olarak dekoratörün görünmesini ve kaybolmasını sebilirsiniz. Örneğin, bir Kişiyi temsil eden bir şekil üzerinde, kişinin cinsiyeti, çocuk sayısı gibi farklı simgelerle karşınıza çıkabilir.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir simgenin veya dekoratörün görünürlüğünü denetleme
 Aşağıdaki yordam, bir şekli ve onun bir etki alanı sınıfına eşlemesini zaten tanımlamış olduğunu varsayıyor. Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Bir simgenin veya metin dekoratörün görünürlüğünü kontrol etmek için

1. DSL Tanımı diyagramında, şekil sınıfına görünmesini istediğiniz simgeleri veya metin dekoratörlerini ekleyin.

   1. Şekil sınıfına sağ tıklayın, Ekle'nin **üzerine** gelin ve ardından gerekli dekoratör türüne tıklayın.

   2. Dekoratörün Position **özelliğini** ayarlayın. Birden fazla dekoratör aynı konuma sahip olabilir. Örneğin, aynı konumu paylaşan erkek ve kadın simgeleri olabilir.

   3. Simge **dekoratörün** Varsayılan Simge özelliğini ayarlayın.

2. DSL Tanım diyagramında şekil sınıfı ile etki alanı sınıfı arasındaki gri çizgi olan diyagram öğesi haritasını seçin.

3. DSL Ayrıntıları penceresindeki **Dekoratör** ve Haritalar bir dekoratör seçin. Örneğin, MaleDecorator.

4. Görünürlük **Filtresi kutusunu** işaretleyin.

5. Görünürlüğü denetlemesi gereken etki alanı özelliği anlık etki alanı sınıfında ise, Filtre **Özelliğinin Yolu alanını boş** bırakın.

    Aksi takdirde, açılan menüye tıklayın ve özelliğin bulunduğu ilişkiye veya sınıfa gidin.

   - Hata raporundan kaçınmak için gezinti aracında "*" ile işaretlenmiş bir ilişkide gezinmenize gerek yok.

6. Filtre Özelliğini **bir etki** alanı özelliği olarak ayarlayın. Örneğin, Cinsiyet.

7. Görünürlük **Girişleri listesinde,** dekoratörün görünür olması gereken bu etki alanı özelliğinin değerlerini ekleyin. Örneğin, Erkek.

8. Her simge için adımları tekrarlayın.

9. **Tüm Şablonları Dönüştür,** bir test diyagramı oluşturun ve çalıştırın ve açın.

10. Denetim özelliği değerini değiştirmiyorken dekoratörler görüntüden kalkacaktır.

    Çoğu zaman, görünürlüğün basit bir değer kümesinden daha karmaşık bir formülle denetlenerek denetlenerek tamamlan bir formüle sahip olması gerekir. Örneğin, bir simgenin belirli bir türün bağlantı sayısına bağlı olarak veya bir sayanın belirli bir aralıkta olup olmadığının bağlı olup olmadığının bağlı olduğu bir simgeye sahip olmak. Bu durumda aşağıdaki yordamı kullanın.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Bir formüle göre dekoratörün görünürlüğünü denetleme

1. Etki alanı sınıfına bir hesaplanan etki alanı özelliği ekleyin. Özellikler **penceresinde** aşağıdaki değerleri ayarlayın:

     **IsBrowsable =** `False` **- bu, özelliği kullanıcıdan gizler**    

     **Tür =** `Calculated` **- Bu, değerini hesapan kod sağlay anlamına gelir**    

     **Örneğin,** **DekoratörControl adı**

     **Türü** = `Boolean`

     Daha fazla bilgi için [bkz. Hesaplanan ve Özel Depolama Özellikleri.](../modeling/calculated-and-custom-storage-properties.md)

2. Yeni özelliğin dekoratör görünürlüğünü denetlemesini sağlar.

    1. Etki alanı sınıfından şekle gri çizgi olan diyagram öğesi haritasını seçin. DSL **Ayrıntıları penceresinde** Dekoratör Haritası **sekmesini** açın.

    2. Görünürlük **Filtresi kutusunu** işaretleyin.

    3. Filtre **Özelliği'nin** **içinde, DekoratörDenedenet denetim özelliğini seçin.**

    4. Görünürlük **Girişleri'nin altına** `True` girin.

3. Araç **çubuğunda Tüm Şablonları Dönüştür'e** **Çözüm Gezgini** tıklayın.

4. Derleme **menüsünde Çözümü** **Derleme'ye** tıklayın.

5. Görünen hata raporuna çift tıklayın: "*YourClass,* GetDecoratorControlValue ..." için bir tanım içeriyor.

     Metin düzenleyicisi Dsl\GeneratedCode\DomainClasses.cs üzerinde açılır. Yukarıda vurgulanan hata, yöntem ekleme isteğinde bulunduran bir açıklamadır.

6. Eksik olan ad alanını, sınıfı ve yöntemi not ekleyin.  Örneğin, Company.FamilyTree.Person.GetDecoratorControlValue() .

7. Ayrı bir kod dosyasında eksik yöntemi içeren kısmi bir sınıf tanımı yazın. Örnek:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Modeli program koduyla özelleştirme hakkında daha fazla bilgi için bkz. Program Kodunda [Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

8. Çözümü yeniden oluşturma ve çalıştırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller ve Bağlayıcıları Tanımlama](../modeling/defining-shapes-and-connectors.md)
- [Diyagram Üzerinde Arka Plan Görüntüsü Ayarlama](../modeling/setting-a-background-image-on-a-diagram.md)
- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)