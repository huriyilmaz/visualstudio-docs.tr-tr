---
title: Ayıklama yöntemi yeniden düzenlemesi (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667538"
---
# <a name="extract-method-refactoring-c"></a>Ayıklama Yöntemi Yeniden Düzenlemesi (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extract yöntemi** , var olan bir üyenin kod parçasındaki yeni bir yöntem oluşturmanın kolay bir yolunu sağlayan bir yeniden düzenleme işlemidir.

 **Extract metodunu**kullanarak, varolan bir üyenin kod bloğunun içinden bir kod seçimini ayıklayarak yeni bir yöntem oluşturabilirsiniz. Yeni, ayıklanan Yöntem seçili kodu içerir ve varolan üyedeki seçili kod, yeni yönteme yapılan bir çağrıyla değiştirilmiştir. Kodun bir parçasını kendi yöntemine dönüştürmek, daha iyi yeniden kullanım ve okunabilirlik için kodu hızlı ve doğru bir şekilde yeniden düzenlemenize olanak tanır.

 **Extract yöntemi** aşağıdaki avantajlara sahiptir:

- Ayrık, yeniden kullanılabilir yöntemleri vurgulayarak en iyi kodlama uygulamalarını teşvik eder.

- İyi bir kuruluş aracılığıyla kendi kendine belgeleme kodunu teşvik eder.

     Açıklayıcı adlar kullanıldığında, üst düzey Yöntemler daha fazla açıklama dizisi gibi okuyabilir.

- Geçersiz kılmayı kolaylaştırmak için daha hassas yöntemlerin oluşturulmasını teşvik eder.

- Kod yinelemeyi azaltır.

### <a name="to-use-extract-method"></a>Extract metodunu kullanmak için

1. Adlı bir konsol uygulaması oluşturun `ExtractMethod` ve ardından `Program` Aşağıdaki örnek kodla değiştirin.

    ```csharp
    class A
    {
        const double PI = 3.141592;

        double CalculatePaintNeeded(double paintPerUnit, double radius)
        {
            // Select any of the following:
            // 1. The entire next line of code.
            // 2. The right-hand side of the next line of code.
            // 3. Just "PI *" of the right-hand side of the next line
            //    of code (to see the prompt for selection expansion).
            // 4.  All code within the method body.
            // ...Then invoke Extract Method.

            double area = PI * radius * radius;

            return area / paintPerUnit;
        }
    }
    ```

2. Ayıklamak istediğiniz kod parçasını seçin:

    ```csharp
    double area = PI * radius * radius;
    ```

3. Yeniden **Düzenle** menüsünde, **yöntemi Ayıkla**' ya tıklayın.

     **Ayıklama yöntemi** iletişim kutusu görüntülenir.

     Alternatif olarak, **ayıklama yöntemi** iletişim kutusunu göstermek için CTRL + R, M klavye kısayolunu de yazabilirsiniz.

     Ayrıca, seçili koda sağ tıklayıp yeniden **Düzenle**' yi işaret edin ve sonra **ayıklama yöntemi** Iletişim kutusunu göstermek için **yöntemi Ayıkla** ' yı tıklayabilirsiniz.

4. Yeni yöntem için `CircleArea` **yeni yöntem adı** kutusuna bir ad belirtin.

     Yeni yöntem imzasının önizlemesi, **Önizleme yöntemi imzası**altında görüntülenir.

5. **Tamam**’a tıklayın.

## <a name="remarks"></a>Açıklamalar
 **Extract metodu** komutunu kullandığınızda, yeni yöntem kaynak üyenin aynı sınıfa sonra eklenir.

## <a name="partial-types"></a>Kısmi türler
 Sınıf kısmi bir tür ise, **ayıklama yöntemi** kaynak üyenin hemen sonrasında yeni yöntemi oluşturur. **Extract yöntemi** , yeni yöntemdeki kod tarafından hiçbir örnek veriye başvurulmuyorsa bir statik yöntem oluşturan yeni yöntemin imzasını belirler.

## <a name="generic-type-parameters"></a>Genel Tür Parametreleri
 Kısıtlanmış olmayan bir genel tür parametresine sahip olan bir yöntemi ayıkladığınızda, `ref` kendisine bir değer atanmadığı takdirde, oluşturulan kod bu parametreye değiştiricisini eklemez. Ayıklanan Yöntem, genel tür bağımsız değişkeni olarak başvuru türlerini destekleyecektir, `ref` değiştiricisini Yöntem imzasında parametreye el ile eklemeniz gerekir.

## <a name="anonymous-methods"></a>Anonim Yöntemler
 Anonim yöntemin dışında bildirildiği veya başvurulan yerel bir değişkene başvuru içeren bir anonim metodun bir parçasını çıkarmaya çalışırsanız, Visual Studio olası semantik değişiklikler hakkında sizi uyarır.

 Anonim bir yöntem yerel bir değişkenin değerini kullandığında, bu değer adsız yöntemin yürütüldüğü anda elde edilir. Anonim bir yöntem başka bir yönteme ayıklandığında, yerel değişkenin değeri ayıklanan yönteme yapılan çağrının bulunduğu anda elde edilir.

 Aşağıdaki örnekte bu anlamsal değişiklik gösterilmektedir. Bu kod yürütülürse, **11** konsola yazdırılır. Kod açıklamaları tarafından işaretlenen kod bölgesini kendi yöntemine ayıklamak için **Extract yöntemini** kullanırsanız ve sonra yeniden düzenlenmiş kodunu çalıştırırsanız, **10** konsola yazdırılır.

```csharp
class Program
{
    delegate void D();
    D d;
    static void Main(string[] args)
    {
        Program p = new Program();
        int i = 10;
        /*begin extraction*/
            p.d = delegate { Console.WriteLine(i++); };
        /*end extraction*/
        i++;
        p.d();
    }
}
```

 Bu durumu geçici olarak çözmek için, sınıfının anonim yöntem alanlarında kullanılan yerel değişkenleri yapın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)