---
title: Hesaplanan ve Özel Depolama Özellikleri
description: Etki alanına özgü bir dil (DSL) içinde bulunan tüm etki alanı özelliklerinin diyagramda ve dil gezgininde kullanıcıya nasıl göster gösterebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5a112d515b66262b5981bec8560a83207c5dd38a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055607"
---
# <a name="calculated-and-custom-storage-properties"></a>Hesaplanan ve Özel Depolama Özellikleri
Etki alanına özgü bir dilde (DSL) tüm etki alanı özellikleri kullanıcıya diyagramda ve dil gezgininde görüntülenebilir ve program kodu tarafından erişilebilir. Ancak özellikler, değerlerinin depolandığı şekilde farklılık gösterir.

## <a name="kinds-of-domain-properties"></a>Etki Alanı Özellikleri Türleri
 DSL Tanımı'da, etki alanı **özelliğinin** Tür'lerini aşağıdaki tabloda listelenmiş şekilde ayarlayın:

|Etki Alanı Özellik Tür|Açıklama|
|-|-|
|**Standart** (Varsayılan)|Depoya kaydedilen ve dosyaya seri *hale getirilen* bir etki alanı özelliği.|
|**Hesaplanmış**|Depoya kayıtlı olmayan, ancak diğer değerlerden hesaplanan salt okunur bir etki alanı özelliği.<br /><br /> Örneğin, `Person.Age` üzerinden `Person.BirthDate` hesaplanabilir.<br /><br /> Hesaplamayı gerçekleştiren kodu sağlamanız gerekir. Genellikle, değeri diğer etki alanı özelliklerinden hesaplarsiniz. Ancak dış kaynakları da kullanabilirsiniz.|
|**Özel Depolama**|Doğrudan depoya kaydedilene ancak hem get hem de set ile kaydedilebilir bir etki alanı özelliği.<br /><br /> Değeri alan ve ayaran yöntemleri sağlanız gerekir.<br /><br /> Örneğin, `Person.FullAddress` , ve içinde `Person.StreetAddress` `Person.City` depolanmış `Person.PostalCode` olabilir.<br /><br /> Bir veritabanından değer almak ve ayarlamak gibi dış kaynaklara da erişebilirsiniz.<br /><br /> Kodunuz true olduğunda depoda değer `Store.InUndoRedoOrRollback` ayarlamamalı. Bkz. [İşlemler ve Özel Ayarçılar.](#setters)|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Hesaplanmış veya özel depolama özelliği için kod sağlama
 Etki alanı özelliğinin tür olarak Hesaplanan veya Özel Depolama olarak ayarlanırsa erişim yöntemleri sağlayabilirsiniz. Çözümlerinizi derlemek için gerekenleri bir hata raporuyla bildirebilirsiniz.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Hesaplanan veya Özel Bir Depolama Tanımlamak için

1. DslDefinition.dsl içinde, diyagramda veya DSL Gezgini'nde etki **alanı özelliğini seçin.**

2. Özellikler **penceresinde Tür** alanını Hesaplanan **veya** Özel alan **olarak Depolama.**

     Türünü de istediğiniz gibi **ayarlayandan** emin olun.

3. öğesinin **araç çubuğunda Tüm** Şablonları Dönüştür'e **Çözüm Gezgini.**

4. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     Şu hata iletisini alısınız: "*YourClass,* Get *YourProperty* için bir tanım içeriyor."

5. Hata iletisine çift tıklayın.

     Dsl\GeneratedCode\DomainClasses.cs veya DomainRelationships.cs açılır. Vurgulanan yöntem çağrısının üzerinde, açıklama Get *YourProperty*() için bir uygulama sağlamanızı istenir.

    > [!NOTE]
    > Bu dosya DslDefinition.dsl dosyasından oluşturulur. Bu dosyayı düzenlersanız, Tüm Şablonları Dönüştür'e bir sonraki tıklarsanız **değişiklikleriniz kaybolur.** Bunun yerine, gerekli yöntemi ayrı bir dosyaya ekleyin.

6. CustomCode \\ *YourDomainClass*.cs gibi ayrı bir klasörde bir sınıf dosyası oluşturun veya açın.

     Ad alanının oluşturulan kodla aynı olduğundan emin olun.

7. Sınıf dosyasında, etki alanı sınıfının kısmi bir uygulamasını yazın. sınıfında, aşağıdaki örnekteki gibi eksik `Get` yöntemi için bir tanım yazın:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. **Tür'ler** için Özel **Depolama** olarak ayarlanırsa, bir yöntem de sağlamanız `Set` gerekir. Örnek:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Kodunuz true olduğunda depoda değer `Store.InUndoRedoOrRollback` ayarlamamalı. Bkz. [İşlemler ve Özel Ayarçılar.](#setters)

9. Çözümü derleyin ve çalıştırın.

10. özelliğini test etmek. Geri Al'ın ve **Tekrarla'nın denek** olduğundan **emin olun.**

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> İşlemler ve Özel Ayarçılar
 Yöntemi genellikle etkin bir Depolama içinde çağrıldı olduğundan, Özel Ayar yönteminde Depolama açmak zorunda değildir.

 Ancak, kullanıcı Geri Al veya Yeniden Çalıştır'ı çağırırsa veya bir işlem geri alınırsa Set yöntemi de çağrılabilir. True <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> olduğunda, Set yönteminiz aşağıdaki gibi davran olmalıdır:

- Depoda, diğer etki alanı özelliklerine değer atama gibi değişiklikler yapmama gerekir. Geri alma yöneticisi değerlerini ayarlar.

- Ancak veritabanı veya dosya içeriği gibi dış kaynakları veya depo dışındaki nesneleri güncelleştirmesi gerekir. Bu, bunların depoda bulunan değerlerle zaman uyumlu olarak tutulmasını sağlar.

  Örnek:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 İşlemler hakkında daha fazla bilgi için [bkz. Program Kodunda Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanı Özelliklerinin Özellikleri](../modeling/properties-of-domain-properties.md)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
