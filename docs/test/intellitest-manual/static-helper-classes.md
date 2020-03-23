---
title: Statik yardımcı sınıflar | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5010761213cf79756cf8da3d2fffe60dd0b61efd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302618"
---
# <a name="static-helper-classes"></a>Statik yardımcı sınıfları

IntelliTest, [parametreli birim testleri](test-generation.md#parameterized-unit-testing)yazarken kullanılabilecek bir statik yardımcı sınıfı kümesi sağlar:

* [PexAssume](#pexassume): girişler üzerindeki varsayımları tanımlamak için kullanılır ve istenmeyen girişleri filtrelemek için yararlıdır
* [PexAssert](#pexassert): test çerçeveniz bir tane sağlamazsa kullanım için basit bir assertion class
* [PexSelect](#pexchoose): IntelliTest'in yönettiği ek test girişleri akışı
* [PexObserve](#pexobserve): somut değerleri kaydeder ve isteğe bağlı olarak, oluşturulan kodda doğrular

Bazı sınıflar, IntelliTest akıl yürütme motoruyla düşük düzeyde etkileşimkurmanızı sağlar:

* [PexSymbolicValue](#pexsymbolicvalue): değişkenler üzerindeki sembolik kısıtlamaları incelemek veya değiştirmek için yardımcı programlar

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

[Parametreli birim testlerinde](test-generation.md#parameterized-unit-testing)ön [koşullar](test-generation.md#precondition)gibi varsayımları ifade etmek için kullanılan statik bir sınıf. İstenmeyen test girişlerini filtrelemek için bu sınıfın yöntemleri kullanılabilir.

Varsayılan koşul bazı test girişi için tutmuyorsa, bir **PexAssumeFailedException** atılır. Bu, testin sessizce yoksayılmasına neden olur.

**Örnek**

Aşağıdaki parametreli test **j=0**dikkate almayacak:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Açıklamalar**

Yukarıdaki kod neredeyse eşdeğerdir:

```csharp
     if (j==0)
          return;
```

başarısız bir **PexAssume** hiçbir test durumda sonuçları dışında. **If** deyimi durumunda, IntelliTest **if** deyiminin **sonradaki** dalını kapsayacak ayrı bir test çalışması oluşturur.

**PexAssume** ayrıca dize, diziler ve koleksiyonlar üzerinde varsayımlar için özel iç içe sınıfları içerir.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

[Parametreli birim testlerinde](test-generation.md#parameterized-unit-testing) [postconditions](test-generation.md#postcondition)gibi iddiaları ifade etmek için kullanılan statik bir sınıf.

Öne sürülen durum bazı test girişi için tutmuyorsa, bir **PexAssertFailedException** atılır ve bu da testin başarısız lığa neden olur.

**Örnek**

Aşağıdaki, bir tamsedinin mutlak değerinin pozitif olduğunu iddia eder:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

[Parametreli Mocks'ı](input-generation.md#parameterized-mocks)uygulamak için kullanılabilecek bir teste yardımcı giriş değerleri sağlayan statik bir sınıf.

**PexChoose** sınıfı, bir testin belirli giriş değerleri için geçip geçmediğini veya başarısız olup olmadığını belirlemede yardımcı olmaz. **PexChoose** sadece *seçenek*olarak da adlandırılır giriş değerleri sağlar. Giriş değerlerini kısıtlamak ve bir testin ne zaman geçtiğini veya başarısız olacağını tanımlayan öneler yazmak yine de kullanıcıya kalmış.

**İşlem modları**

**PexChoose** sınıfı iki modda çalışabilir:

* IntelliTest [giriş oluşturma](input-generation.md)sırasında testve test kodunun sembolik bir analizini gerçekleştirirken, seçici rasgele değerler döndürür ve IntelliTest her değerin testte ve test kodunda nasıl kullanıldığını izler. IntelliTest test ve test kodufarklı yürütme yolları tetiklemek için ilgili değerler oluşturur.

* Belirli test servis talepleri için oluşturulan kod, seçim sağlayıcısını belirli bir şekilde ayarlar, böylece böyle bir test çalışmasının yeniden yürütülmesi belirli bir yürütme yolunu tetiklemek için belirli seçimler yapar.

**Kullanım**

* Yeni bir değer oluşturmak için Basit arama **PexChoose.Value:**

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Adlandırılmış değerleri günlüğe kaydetmek için statik bir sınıf.

IntelliTest kodu keşfettiğinde, **PexObserve** biçimlendirilmiş dize gösterimlerini kullanarak hesaplanan değerleri kaydetmek için kullanılır. Değerler benzersiz adlarla ilişkilidir.

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

Parametrelerüzerindeki kısıtlamaları yoksaymak ve değerlerle ilişkili sembolik bilgileri yazdırmak için kullanılan statik bir sınıf.

**Kullanım**

Normalde, IntelliTest yürütme sırasında kodun tüm yürütme yollarını kapsayacak şekilde çalışır. Ancak, özellikle varsayım ve iddia koşulları bilgisayar, tüm olası durumlarda keşfetmek gerekir.

**Örnek**

Bu **örnek, PexAssume.Arrays.ElementsAreNotNull** yönteminin uygulanmasını gösterir.
Yöntemde, IntelliTest'in farklı dizi boyutları oluşturmaya çalışmasından kaçınmak için dizi değerinin lengh üzerindeki kısıtlamaları yoksuzlarsınız. Kısıtlamalar yalnızca burada yoksayılır. Sınanan kod farklı dizi uzunlukları için farklı şekilde davranılırsa, IntelliTest sınanan kodun kısıtlamalarından farklı boyutlu diziler oluşturamaz.

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

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
