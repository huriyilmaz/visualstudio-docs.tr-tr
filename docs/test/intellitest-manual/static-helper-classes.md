---
title: Statik yardımcı sınıfları | Microsoft IntelliTest geliştirici test aracı
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: dd57ecafa0b4da56366faa83d52c39ca556e421a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653143"
---
# <a name="static-helper-classes"></a>Statik yardımcı sınıfları

IntelliTest, [parametreli birim testleri](test-generation.md#parameterized-unit-testing)yazarken kullanılabilecek bir statik yardımcı sınıf kümesi sağlar:

* [Pexvarsay](#pexassume): girişler üzerinde varsayımları tanımlamak için kullanılır ve istenmeyen girdileri filtrelemek için faydalıdır
* [Pexassertion](#pexassert): test çatısı bir tane sağlamıyorsa kullanılmak üzere basit bir onaylama sınıfı
* [PexChoose](#pexchoose): IntelliTest 'in yönettiği ek test girişlerinin akışı
* [Pexgözlem:](#pexobserve)somut değerleri günlüğe kaydeder ve isteğe bağlı olarak bunları üretilen kodda doğrular

Bazı sınıflar, IntelliTest mantık yürütme altyapısıyla düşük düzeyde etkileşimde bulunabilmeniz için izin verir:

* [Pexsembolicvalue](#pexsymbolicvalue): değişkenlerde sembolik kısıtlamaları İnceleme veya değiştirme yardımcı programları

<a name="pexassume"></a>
## <a name="pexassume"></a>Pexvarsay

[Parametreli birim testlerinde](test-generation.md#parameterized-unit-testing) [önkoşulları](test-generation.md#precondition)gibi varsayımları ifade etmek için kullanılan statik bir sınıf. Bu sınıfın yöntemleri, istenmeyen test girişlerini filtrelemek için kullanılabilir.

Kabul edilen koşul bazı test girişleri için Tutulmasa, bir **PexAssumeFailedException** oluşturulur. Bu, testin sessizce yoksayılmasına neden olur.

**Örnek**

Şu parametreli test, **j = 0**olarak kabul etmez:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Açıklamalarının**

Yukarıdaki kod, neredeyse eşittir:

```csharp
     if (j==0)
          return;
```

hata veren bir **Pexın** , test çalışması olmadan sonuçları vermez. **İf** Ifadesinde, IntelliTest, **IF** **ifadesinin dalını kapsayacak** şekilde ayrı bir test durumu oluşturur.

**Pexvarsay** Ayrıca dize, dizi ve koleksiyonlardaki varsayımlar için özel iç içe sınıflar içerir.

<a name="pexassert"></a>
## <a name="pexassert"></a>Pexonaylama

[Parametreli birim testlerinde](test-generation.md#parameterized-unit-testing) [Sonkoşulları](test-generation.md#postcondition)gibi onayları ifade etmek için kullanılan statik bir sınıf.

Onaylanan koşul bazı test girdileri içermiyorsa, bir **PexAssertFailedException** atılır ve bu da testin başarısız olmasına neden olur.

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

Bir teste yardımcı giriş değerleri sağlayan statik bir sınıf, [parametreli modülleri](input-generation.md#parameterized-mocks)uygulamak için kullanılabilir.

**PexChoose** sınıfı, bir testin belirli giriş değerleri için başarılı veya başarısız olup olmadığını belirlemede yardımcı değildir. **PexChoose** , *seçenek*olarak da adlandırılan giriş değerlerini sağlar. Bu, giriş değerlerini kısıtlamak ve bir testin ne zaman başarılı veya başarısız olduğunu tanımlayan onaylamaları yazmak için hala kullanıcıya kadar sürer.

**İşlem modları**

**PexChoose** sınıfı iki modda çalışabilir:

* IntelliTest, [giriş oluşturma](input-generation.md)sırasında testin sembolik analizini ve sınanan kodu gerçekleştiriyor olsa da, Chooser rastgele değerler döndürür ve IntelliTest her bir değerin testte ve sınanan kodda nasıl kullanıldığını izler. IntelliTest, testte ve test edilen koddaki farklı yürütme yollarını tetiklemek için ilgili değerleri oluşturur.

* Belirli test çalışmaları için oluşturulan kod, seçim sağlayıcısını belirli bir şekilde ayarlar, böylece böyle bir test çalışmasının yeniden yürütülmesi belirli bir yürütme yolunu tetiklemeye yönelik belirli seçimler oluşturur.

**Kullanımıyla**

* Basit çağrı **PexChoose. Value** yeni bir değer oluşturmak için:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Adlandırılmış değerlerin günlüğe kaydedilecek statik bir sınıf.

IntelliTest kodu inceleyince, hesaplanan değerleri biçimli dize gösterimlerini kullanarak kaydetmek için **Pexgözlemkullanılır** . Değerler benzersiz adlarla ilişkilendirilir.

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
## <a name="pexsymbolicvalue"></a>Pexsembolicvalue

Parametrelerin kısıtlamalarını yoksaymak ve değerlerle ilişkili sembolik bilgileri yazdırmak için kullanılan statik bir sınıf.

**Kullanımıyla**

Normalde, IntelliTest yürütme sırasında kodun tüm yürütme yollarını kapsamaya çalışır. Ancak, özellikle de varsayım ve onaylama koşullarını hesaplarken, olası tüm durumları araştırmamalıdır.

**Örnek**

Bu örnek, **Pexvarsay. Arrays. ElementsAreNotNull** yönteminin uygulamasını gösterir.
Yönteminde, farklı boyutlarda dizi boyutları oluşturmaya çalışan IntelliTest 'i önlemek için dizi değerinin lengh üzerindeki kısıtlamaları yoksayabilirsiniz. Kısıtlamalar yalnızca burada yok sayılır. Sınanan kod farklı dizi uzunlukları için farklı davrandıysa, IntelliTest, sınanan kodun kısıtlamalarından farklı boyutlardaki diziler üretemiyor.

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

## <a name="got-feedback"></a>Geri bildirim alındı mı?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)' na gönderin.