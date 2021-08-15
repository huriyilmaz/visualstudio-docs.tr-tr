---
title: Statik yardımcı sınıfları | Microsoft IntelliTest Geliştirici Test Aracı
description: IntelliTest'in parametreli birim testleri yazma için sağladığı statik yardımcı sınıflar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 62e58da2d6bf5e188231c3d46580e8202d97a6bfeaa1246c9d040dd2a2160e85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366517"
---
# <a name="static-helper-classes"></a>Statik yardımcı sınıfları

IntelliTest, parametreli birim testleri yazmada kullanılan bir statik [yardımcı sınıf kümesi sağlar:](test-generation.md#parameterized-unit-testing)

* [PexAssume:](#pexassume)girişler üzerinde varsayımları tanımlamak için kullanılır ve istenmeyen girişleri filtrelemek için yararlıdır
* [PexAssert:](#pexassert)test çerçeveniz bir onay sınıfı sağlanmasa kullanmak için basit bir onay sınıfıdır
* [PexChoose:](#pexchoose)IntelliTest tarafından yönetilen ek test girişlerinin akışı
* [PexObserve:](#pexobserve)somut değerleri günlüğe kaydeder ve isteğe bağlı olarak bunları oluşturulan kodda doğrular

Bazı sınıflar, IntelliTest gerekçe altyapısıyla alt düzeyde etkileşim kurmana olanak sağlar:

* [PexSymbolicValue:](#pexsymbolicvalue)değişkenler üzerinde sembolik kısıtlamaları incelemeye veya değiştirmeye yönelik yardımcı programlar

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Parametreli birim testlerinde önkoşullar gibi varsayımları ifade etmek [için kullanılan statik bir sınıf.](test-generation.md#parameterized-unit-testing) [](test-generation.md#precondition) Bu sınıfın yöntemleri, istenmeyen test girişlerini filtrelemek için kullanılabilir.

Varsayılan koşul bazı test girişlerini tutmsa, **PexAssumeFailedException** olur. Bu, testin sessizce yoksay sınanmasına neden olur.

**Örnek**

Aşağıdaki parametreli test **j=0'ı dikkate amayacak:**

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Açıklamalar**

Yukarıdaki kod aşağıdakilere neredeyse eşdeğerdir:

```csharp
     if (j==0)
          return;
```

başarısız bir **PexAssume'un** test sonucu elde edilemez. If deyiminde  IntelliTest, if deyiminin o zaman dallarını kapsayacak şekilde **ayrı** bir test **durumu** üretir.

**PexAssume** ayrıca dize, dizi ve koleksiyon varsayımları için özel iç içe geçmiş sınıflar içerir.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Parametreli birim testlerinde sonkoşullar gibi [onayları](test-generation.md#postcondition)ifade etmek [için kullanılan statik bir sınıf.](test-generation.md#parameterized-unit-testing)

Onaylandırılan koşul bazı test girişlerini tutmayacaksa, testin başarısız olması için **pexAssertFailedException** ortaya çıktı.

**Örnek**

Aşağıdaki, bir tamsayının mutlak değerinin pozitif olduğunu onaylar:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Bir teste yardımcı giriş değerleri temin eden statik sınıf, Parametreli Sahteleri [uygulamak için kullanılabilir.](input-generation.md#parameterized-mocks)

**PexChoose** sınıfı, bir testin belirli giriş değerleri için başarılı veya başarısız olup olmadığını belirlemeye yardımcı olmaz. **PexChoose** yalnızca seçim olarak da adlandırılan giriş değerleri *sağlar.* Giriş değerlerini kısıtlamak ve testin başarılı veya başarısız olduğunu tanımlayan onaylar yazmak yine de kullanıcıya göredir.

**İşlem modları**

**PexChoose** sınıfı iki modda çalışır:

* IntelliTest, giriş oluşturma sırasında testin ve test [](input-generation.md)edilen kodun sembolik bir analizini gerçekleştirirken, seçimci rastgele değerler döndürür ve IntelliTest her değerin testte ve test edilen kodda nasıl kullanılı olduğunu izler. IntelliTest, testte ve test edilen kodda farklı yürütme yollarını tetiklemek için ilgili değerler üretir.

* Belirli test örnekleri için oluşturulan kod, seçim sağlayıcısını belirli bir şekilde ayarlar, böylece böyle bir test örneğinin yeniden yürütülmesi belirli bir yürütme yolunu tetiklemek için belirli seçimler yapacaktır.

**Kullanım**

* Yeni bir **değer oluşturmak için PexChoose.Value** basit çağrısı:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Adlandırılmış değerleri günlüğe günlüğe alan statik bir sınıf.

IntelliTest kodu araştıran **PexObserve,** biçimlendirilmiş dize gösterimlerini kullanarak hesaplanan değerleri kaydetmek için kullanılır. Değerler benzersiz adlarla ilişkilendirildi.

```csharp
PexObserve.Value<string>("result", result);
```

**Örnek**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Parametrelerle ilgili kısıtlamaları yoksaymak ve değerlerle ilişkili sembolik bilgileri yazdırmak için kullanılan statik bir sınıf.

**Kullanım**

Normalde, IntelliTest yürütme sırasında kodun tüm yürütme yollarını kapatmaya çalışır. Ancak, özellikle de varsayım ve onaylama koşulları hesaplanırken, olası tüm örnekleri incelemez.

**Örnek**

Bu örnek **PexAssume.Arrays.ElementsAreNotNull yönteminin uygulamasını** gösterir.
yönteminde, IntelliTest'in farklı dizi boyutları üretmeye çalışmasını önlemek için dizi değerinin yalıtılmasıyla ilgili kısıtlamaları yoksayabilirsiniz. Kısıtlamalar yalnızca burada yoksayılır. Test edilen kod farklı dizi uzunlukları için farklı davranırsa, IntelliTest test edilen kodun kısıtlamalarından farklı boyutlu diziler oluşturamaz.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.
