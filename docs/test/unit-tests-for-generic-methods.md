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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590819"
---
# <a name="unit-tests-for-generic-methods"></a>Genel metotlar için birim testleri

Genel yöntemler için birim testleri oluşturabilirsiniz, tıpkı diğer yöntemlerde yaptığınız gibi. Aşağıdaki bölümlerde genel yöntemler için birim testleri oluşturma hakkında bilgi ve örnekler verilmiştir.

## <a name="type-arguments-and-type-constraints"></a>Yazı bağımsız değişkenleri ve tür kısıtlamaları

Visual Studio genel bir sınıf için bir birim `MyList<T>`testi oluşturduğunda, örneğin, iki yöntem oluşturur: genel bir yardımcı ve bir test yöntemi. Bir `MyList<T>` veya daha fazla tür kısıtlaması varsa, tür bağımsız değişkeni tüm tür kısıtlamalarını karşılamalıdır. Test altındaki genel kodun tüm izin verilen girişler için beklendiği gibi çalıştığından emin olmak için, test yöntemi test etmek istediğiniz tüm kısıtlamaları içeren genel yardımcı yöntemi çağırır.

## <a name="examples"></a>Örnekler
Aşağıdaki örnekler, jenerikler için birim testlerini göstermektedir:

- [Oluşturulan test kodunu edin.](#EditingGeneratedTestCode) Bu örnekte oluşturulan test kodu ve düzenlenen test kodu olmak üzere iki bölüm vardır. Genel bir yöntemden oluşturulan ham test kodunun yararlı bir test yöntemine nasıl dönüştürülür şekilde yapılacağını gösterir.

- [Bir tür kısıtlaması kullanın.](#TypeConstraintNotSatisfied) Bu örnek, tür kısıtlaması kullanan genel bir yöntem için bir birim testi gösterir. Bu örnekte, tür kısıtlaması tatmin edilmez.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a>Örnek 1: Oluşturulan test kodunu düzenleme
Bu bölümdeki test kodu, test altında bir `SizeOfLinkedList()`kod yöntemini sınar. Bu yöntem, bağlı listedeki düğüm sayısını belirten bir tamsayı döndürür.

Oluşturulan Test Kodu bölümündeki ilk kod örneği, Visual Studio Enterprise tarafından oluşturulan düzenlenmemiş test kodunu gösterir. Düzenlenen Test Kodu bölümündeki ikinci örnek, iki farklı veri türü için SizeOfLinkedList yönteminin işleyişini `int` `char`nasıl test edebileceğini gösterir ve .

Bu kod iki yöntemi göstermektedir:

- bir test yardımcı `SizeOfLinkedListTestHelper<T>()`yöntemi, . Varsayılan olarak, bir test yardımcısı yönteminin adında "TestHelper" vardır.

- bir test `SizeOfLinkedListTest()`yöntemi, . Her test yöntemi TestYöntemi özniteliği ile işaretlenir.

#### <a name="generated-test-code"></a>Oluşturulan test kodu
`SizeOfLinkedList()` Yöntemden aşağıdaki test kodu oluşturuldu. Bu düzenlenmemiş oluşturulan test olduğundan, SizeOfLinkedList yöntemini doğru bir şekilde sınamak için değiştirilmesi gerekir.

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

Önceki kodda, genel tür parametresi `GenericParameterHelper`. Aşağıdaki örnekte gösterildiği gibi, belirli veri türlerini sağlamak için düzenleyebilirsiniz, ancak bu deyimi düzenlemeden testi çalıştırabilirsiniz.

#### <a name="edited-test-code"></a>Düzenlenen test kodu
Aşağıdaki kodda, test yöntemi ve test yardımcısı yöntemi, kod altında test yöntemini `SizeOfLinkedList()`başarıyla test etmek için düzenlendi.

##### <a name="test-helper-method"></a>Test yardımcı yöntemi
Test yardımcısı yöntemi, adım 1'den adım 5'e kadar etiketli koddaki satırlara karşılık gelen aşağıdaki adımları gerçekleştirir.

1. Genel bir bağlantılı liste oluşturun.

2. Bağlı listeye dört düğüm ekleyin. Bu düğümlerin içeriğinin veri türü bilinmiyor.

3. Bağlı listenin beklenen boyutunu değişkene `expected`atayın.

4. Bağlı listenin gerçek boyutunu hesaplayın ve değişkene `actual`atayın.

5. Bir `actual` `expected` Assert deyimiyle karşılaştırın. Gerçek beklenene eşit değilse, test başarısız olur.

##### <a name="test-method"></a>Test yöntemi
Test yöntemi, SizeOfLinkedListTest adlı testi çalıştırdığınızda çağrılan koda derlenir. Adım 6 ve adım 7 etiketli koddaki satırlara karşılık gelen aşağıdaki adımları gerçekleştirir.

1. Testin değişkenler için çalıştığını doğrulamak için `<int>` `integer` test yardımcısı yöntemini ne zaman çağırdığınızı belirtin.

2. Testin değişkenler için çalıştığını doğrulamak için `<char>` `char` test yardımcısı yöntemini ne zaman çağırdığınızı belirtin.

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
> SizeOfLinkedListTest testi her çalıştığında, TestHelper yöntemi iki kez çağrılır. İddia deyimi, testin geçmesi için her seferinde doğru olarak değerlendirilmelidir. Test başarısız olursa, belirtilen aramanın mı yoksa `<int>` belirtilen `<char>` aramanın başarısız olmasına neden olup olmadığı belli olmayabilir. Yanıtı bulmak için, arama yığınını inceleyebilir veya test yönteminizde kesme noktaları ayarlayabilir ve testi çalıştırırken hata ayıklama sağlayabilirsiniz. Daha fazla bilgi için [bkz: ASP.NET çözümünde bir test çalıştırırken hata ayıklama.](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b)

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a>Örnek 2: Bir tür kısıtlaması kullanma
Bu örnek, memnun olmayan bir tür kısıtlaması kullanan genel bir yöntem için bir birim testi gösterir. İlk bölümde, test altındaki kod projesinin kodu gösterilmektedir. Tür kısıtlaması vurgulanır.

İkinci bölümde test projesinden kod gösterilmektedir.

#### <a name="code-under-test-project"></a>Kod-under-test projesi

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

Yeni oluşturulan tüm birim testlerinde olduğu gibi, yararlı sonuçlar döndürmesi için bu birim testine sonuçsuz Assert ifadeleri eklemeniz gerekir. Bunları TestMethod özniteliği ile işaretlenmiş yönteme değil, bu test için adı verilen `DataTestHelper<T>()`"TestHelper" yöntemine eklersiniz.

Bu örnekte, genel tür `T` parametresi kısıtlamavardır. `where T : Employee` Bu kısıtlama test yönteminde karşılanmaz. Bu nedenle, `DataTest()` yöntem, üzerine `T`yerleştirilen tür kısıtlamasını sağlama gereksinimine karşı sizi uyaran bir Assert deyimi içerir. Bu Assert deyiminin iletisi aşağıdaki gibidir:`("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Başka bir deyişle, `DataTestHelper<T>()` yöntemtest yöntemini aradiğinizde, `DataTest()`bir tür `Employee` parametresini veya türetilmiş bir sınıfı geçmeniz `Employee`gerekir.

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

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
