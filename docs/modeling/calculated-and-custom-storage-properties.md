---
title: Hesaplanan ve Özel Depolama Özellikleri
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52915f0bac2bd172daf909541ecfa86396d90a5d
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115192"
---
# <a name="calculated-and-custom-storage-properties"></a>Hesaplanan ve Özel Depolama Özellikleri
Etki alanına özgü dil (DSL) içindeki tüm etki alanı özellikleri, diyagramda ve dil gezgininizde kullanıcıya görüntülenebilir ve program kodu tarafından erişilebilir. Ancak özellikler, değerlerinin depolandığı şekilde farklılık gösterir.

## <a name="kinds-of-domain-properties"></a>Etki alanı özelliklerinin türleri
 DSL tanımında, aşağıdaki tabloda listelendiği gibi bir etki alanı özelliği **türünü** ayarlayabilirsiniz:

|Alan özelliği türü|Açıklama|
|-|-|
|**Standart** (varsayılan)|*Depoya* kaydedilen ve dosyaya serileştirilmiş bir alan özelliği.|
|**Hesapla**|Depoda kaydedilmemiş ancak diğer değerlerden hesaplanan salt bir salt okunurdur.<br /><br /> Örneğin, `Person.Age` `Person.BirthDate`hesaplanabilir.<br /><br /> Hesaplamayı gerçekleştiren kodu sağlamanız gerekir. Genellikle, diğer etki alanı özelliklerinden değeri hesaplayabilirsiniz. Ancak dış kaynakları da kullanabilirsiniz.|
|**Özel depolama**|Doğrudan depoya kaydedilmemiş, ancak hem Get hem de set olabilecek bir etki alanı özelliği.<br /><br /> Değeri alan ve ayarlamış olan yöntemleri sağlamanız gerekir.<br /><br /> Örneğin, `Person.FullAddress` `Person.StreetAddress`, `Person.City`ve `Person.PostalCode`depolanabilir.<br /><br /> Ayrıca, dış kaynaklara erişebilirsiniz. Örneğin, bir veritabanından değerler almak ve ayarlamak için.<br /><br /> `Store.InUndoRedoOrRollback` true olduğunda kodunuzun depodaki değerleri ayarlaması gerekmez. Bkz. [işlemler ve özel ayarlayıcılar](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Hesaplanmış veya özel bir depolama özelliği için kod sağlama
 Bir etki alanı özelliğinin türünü hesaplanmış veya özel depolama olarak ayarlarsanız, erişim yöntemleri sağlamanız gerekir. Çözümünüzü oluşturduğunuzda bir hata raporu, size gerekli olanları bildirir.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Hesaplanan veya özel bir depolama özelliği tanımlamak için

1. DslDefinition. dsl ' de, diyagramda veya **DSL Gezgini**' nde etki alanı özelliğini seçin.

2. **Özellikler** penceresinde, **tür** alanını **hesaplanan** veya **özel depolama**olarak ayarlayın.

     Ayrıca **türünü** istediğiniz gibi ayarladığınızdan emin olun.

3. **Çözüm Gezgini**araç çubuğundan **Tüm Şablonları Dönüştür** ' e tıklayın.

4. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

     Şu hata iletisini alıyorsunuz: "*YourClass* , Get*yourproperty*için bir tanım içermiyor."

5. Hata iletisine çift tıklayın.

     Dsl\GeneratedCode\DomainClasses.cs veya DomainRelationships.cs açılır. Vurgulanan yöntem çağrısının üzerinde, bir yorum Get*Yourproperty*() için bir uygulama sağlamanızı ister.

    > [!NOTE]
    > Bu dosya DslDefinition. dsl 'den oluşturulur. Bu dosyayı düzenlerseniz, **Tüm Şablonları Dönüştür**' e tıkladığınızda yaptığınız değişiklikler kaybedilir. Bunun yerine, gerekli yöntemi ayrı bir dosyaya ekleyin.

6. Sınıf dosyasını ayrı bir klasörde oluşturun veya açın, örneğin CustomCode\\*YourDomainClass*. cs.

     Ad alanının oluşturulan kodla aynı olduğundan emin olun.

7. Sınıf dosyasında, etki alanı sınıfının kısmi bir uygulamasını yazın. Sınıfında, aşağıdaki örneğe benzer eksik `Get` yöntemi için bir tanım yazın:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. **Türü** **özel depolama**olarak ayarlarsanız Ayrıca bir `Set` yöntemi sağlamanız gerekecektir. Örneğin:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     `Store.InUndoRedoOrRollback` true olduğunda kodunuzun depodaki değerleri ayarlaması gerekmez. Bkz. [işlemler ve özel ayarlayıcılar](#setters).

9. Çözümü derleyin ve çalıştırın.

10. Özelliği test edin. **Geri almayı** ve **yinelemeyi**denediğinizden emin olun.

## <a name="setters"></a>İşlemler ve özel ayarlayıcılar
 Özel depolama özelliğinin set yönteminde bir işlem açmanız gerekmez, çünkü Yöntem genellikle etkin bir işlem içinde çağırılır.

 Ancak, Kullanıcı geri alma veya yeniden yapma işlemini çağrılırsa veya bir işlem geri alınırsa set yöntemi de çağrılabilir. <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> true olduğunda, set yönteminiz aşağıdaki gibi davranır:

- Diğer etki alanı özelliklerine değer atama gibi, depoda değişiklik yapmamalıdır. Geri alma Yöneticisi, değerlerini ayarlayacaktır.

- Ancak, veritabanı veya dosya içerikleri gibi dış kaynakları veya mağaza dışındaki nesneleri güncelleştirmelidir. Bu, depodaki değerlerle eşitlenmiş olduklarından emin olur.

  Örneğin:

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

 İşlemler hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanı Özelliklerinin Özellikleri](../modeling/properties-of-domain-properties.md)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
