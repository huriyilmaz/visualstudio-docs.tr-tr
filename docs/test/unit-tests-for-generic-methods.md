---
title: Genel Yöntemler için birim testleri
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2158c889aefc85c908aa9ee42d45858fd11d557e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590819"
---
# <a name="unit-tests-for-generic-methods"></a>Genel metotlar için birim testleri

Genel yöntemler için birim testlerini, diğer yöntemler için yaptığınız şekilde tam olarak oluşturabilirsiniz. Aşağıdaki bölümler, genel metotlar için birim testleri oluşturma hakkında bilgi ve örnekler sağlar.

## <a name="type-arguments-and-type-constraints"></a>Tür bağımsız değişkenleri ve tür kısıtlamaları

Visual Studio, gibi genel bir sınıf için bir birim testi oluşturduğunda, `MyList<T>` iki yöntem oluşturur: genel yardımcı ve test yöntemi. `MyList<T>`Bir veya daha fazla tür kısıtlaması varsa, tür bağımsız değişkeninin tüm tür kısıtlamalarını karşılaması gerekir. Test edilen genel kodun tüm izin verilen girişler için beklendiği gibi çalıştığından emin olmak için test yöntemi, test etmek istediğiniz tüm kısıtlamalara sahip genel yardımcı yöntemini çağırır.

## <a name="examples"></a>Örnekler
Aşağıdaki örneklerde, genel türler için birim testleri gösterilmektedir:

- [Oluşturulan test kodunu düzenleyin](#EditingGeneratedTestCode). Bu örnekte, üretilen test kodu ve düzenlenmiş test kodu olmak üzere iki bölüm vardır. Genel bir yöntemden oluşturulan ham test kodunun yararlı bir test yöntemine nasıl düzenleneceğini gösterir.

- [Bir tür kısıtlaması kullanın](#TypeConstraintNotSatisfied). Bu örnekte, bir tür kısıtlaması kullanan genel bir yöntem için birim testi gösterilmektedir. Bu örnekte tür kısıtlaması karşılanmaz.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> Örnek 1: oluşturulan test kodunu Düzenle
Bu bölümdeki test kodu adlı bir kod test yöntemini sınar `SizeOfLinkedList()` . Bu yöntem, bağlantılı listedeki düğüm sayısını belirten bir tamsayı döndürür.

Oluşturulan test kodu bölümünde ilk kod örneği, Visual Studio Enterprise tarafından oluşturulduğu şekliyle düzenlenmemiş test kodunu gösterir. İkinci örnek, bir test kodu düzenlenmiş bölümünde, bu, iki farklı veri türü için SizeOfLinkedList yönteminin çalışmasını nasıl test etmek istediğinizi gösterir `int` `char` .

Bu kod iki yöntemi gösterir:

- test Yardımcısı yöntemi, `SizeOfLinkedListTestHelper<T>()` . Varsayılan olarak, bir test Yardımcısı yönteminin adında "TestHelper" vardır.

- test yöntemi, `SizeOfLinkedListTest()` . Her test yöntemi TestMethod özniteliğiyle işaretlenir.

#### <a name="generated-test-code"></a>Test kodu oluşturuldu
Aşağıdaki test kodu `SizeOfLinkedList()` yönteminden üretildi. Bu, düzenlenmemiş bir test olduğundan, SizeOfLinkedList metodunu doğru bir şekilde test etmek için değiştirilmesi gerekir.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

Yukarıdaki kodda, genel tür parametresi `GenericParameterHelper` . Bu şekilde, aşağıdaki örnekte gösterildiği gibi belirli veri türlerini sağlamak üzere düzenleyebilirsiniz, bu ifadeyi düzenlemeden testi çalıştırabilirsiniz.

#### <a name="edited-test-code"></a>Düzenlenmiş test kodu
Aşağıdaki kodda, test yöntemi ve test Yardımcısı yöntemi, kodu test yönteminin altında başarıyla test etmek üzere düzenlendi `SizeOfLinkedList()` .

##### <a name="test-helper-method"></a>Test Yardımcısı yöntemi
Test Yardımcısı yöntemi, 5. adımda 1. adım etiketini taşıyan koddaki satırlara karşılık gelen aşağıdaki adımları gerçekleştirir.

1. Genel bağlantılı liste oluşturun.

2. Bağlantılı listeye dört düğüm ekleyin. Bu düğümlerin içeriğinin veri türü bilinmiyor.

3. Bağlantılı listenin beklenen boyutunu değişkenine atayın `expected` .

4. Bağlantılı listenin gerçek boyutunu hesaplayın ve değişkenine atayın `actual` .

5. `actual` `expected` Bir onaylama ifadesinde ile karşılaştırın. Gerçek, beklenen değere eşit değilse, test başarısız olur.

##### <a name="test-method"></a>Test yöntemi
Test yöntemi, SizeOfLinkedListTest adlı testi çalıştırdığınızda çağrılan koda derlenir. 6. adım ve 7. adım etiketli koddaki satırlara karşılık gelen aşağıdaki adımları gerçekleştirir.

1. `<int>`Testin değişkenler için çalıştığını doğrulamak için test Yardımcısı yöntemini ne zaman çağırabileceğinizi belirtin `integer` .

2. `<char>`Testin değişkenler için çalıştığını doğrulamak için test Yardımcısı yöntemini ne zaman çağırabileceğinizi belirtin `char` .

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> SizeOfLinkedListTest testi çalıştığında, TestHelper yöntemi iki kez çağrılır. Onaylama bildiriminin her geçmesi için, her seferinde true olarak değerlendirilmelidir. Test başarısız olursa, belirtilen çağrının `<int>` veya belirtilen çağrının başarısız olmasına neden olup olmadığı temizlenmeyebilir `<char>` . Yanıtı bulmak için çağrı yığınını inceleyebilirsiniz veya test yönteminizin kesme noktaları ayarlayabilir ve testi çalıştırırken hata ayıklayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.net çözümünde test çalıştırırken hata ayıklama](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> Örnek 2: tür kısıtlaması kullanma
Bu örnek, karşılanmamış bir tür kısıtlaması kullanan genel bir yöntem için bir birim testi gösterir. İlk bölüm kodun altındaki test projesinden kodu gösterir. Tür kısıtlaması vurgulanır.

İkinci bölüm, test projesinden kodu gösterir.

#### <a name="code-under-test-project"></a>Kod altındaki test projesi

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>Test projesi

Tüm yeni oluşturulan birim testlerinde olduğu gibi, bu birim testine, yararlı sonuçlar döndürmesini sağlamak için sonuçsuz onay deyimleri eklemeniz gerekir. Bunları TestMethod özniteliği ile işaretlenen yönteme eklemeyin, ancak bu test için adlandırılmış olan "TestHelper" yöntemine eklemeyin `DataTestHelper<T>()` .

Bu örnekte, genel tür parametresinin `T` kısıtlaması vardır `where T : Employee` . Bu kısıtlama test yönteminde karşılanmaz. Bu nedenle, `DataTest()` yöntemi, üzerine yerleştirilmiş tür kısıtlamasını sağlama gereksinimine sizi uyaran bir onay açıklaması içerir `T` . Bu onay bildiriminin iletisi aşağıdaki gibi okur: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Diğer bir deyişle, `DataTestHelper<T>()` yöntemi test yönteminden çağırdığınızda, `DataTest()` türünde bir parametre `Employee` veya sınıfından türetilmiş bir sınıf geçirmeniz gerekir `Employee` .

```csharp
using ClassLibrary2;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestProject1
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
