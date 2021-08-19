---
title: Genel Yöntemler için birim testleri
description: Genel yöntemler için birim testi oluşturma örnekleri ve hakkında bu bilgileri kullanarak genel yöntemler için birim testleri oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8870ac1bbfd7195ae850046279deaf9196ab450b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115258"
---
# <a name="unit-tests-for-generic-methods"></a>Genel metotlar için birim testleri

Genel yöntemler için diğer yöntemlerde olduğu gibi birim testleri de üretebilirsiniz. Aşağıdaki bölümlerde, genel yöntemler için birim testleri oluşturma hakkında bilgi ve örnekler verilmiştir.

## <a name="type-arguments-and-type-constraints"></a>Tür bağımsız değişkenleri ve tür kısıtlamaları

Bir Visual Studio gibi bir genel sınıf için birim testi oluşturması iki yöntem üretir: genel yardımcı ve `MyList<T>` test yöntemi. Bir `MyList<T>` veya daha fazla tür kısıtlaması varsa, tür bağımsız değişkeninin tüm tür kısıtlamalarını karşılaması gerekir. Test altındaki genel kodun izin verilen tüm girişlerde beklendiği gibi çalışmasını sağlamak için test yöntemi, test etmek istediğiniz tüm kısıtlamalarla birlikte genel yardımcı yöntemini çağırabilir.

## <a name="examples"></a>Örnekler
Aşağıdaki örnekler genel türler için birim testlerini göstermektedir:

- [Oluşturulan test kodunu düzenleyin.](#EditingGeneratedTestCode) Bu örnekte, Oluşturulan Test Kodu ve Düzenlenen Test Kodu olmak için iki bölüm vardır. Genel bir yöntemden oluşturulan ham test kodunun yararlı bir test yönteminde nasıl düzenlenmemiş olduğunu gösterir.

- [Tür kısıtlaması kullanın.](#TypeConstraintNotSatisfied) Bu örnek, tür kısıtlaması kullanan genel bir yöntem için birim testini gösterir. Bu örnekte tür kısıtlaması karşılanmaz.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> Örnek 1: Oluşturulan test kodunu düzenleme
Bu bölümdeki test kodu, adlı bir test altında kod yöntemini test `SizeOfLinkedList()` ediyor. Bu yöntem, bağlantılı listede düğüm sayısını belirten bir tamsayı döndürür.

İlk kod örneği, Oluşturulan Test Kodu bölümünde, örnek tarafından oluşturulan ve oluşturulmamış test kodunu Visual Studio Enterprise. İkinci örnek, Düzenlenen Test Kodu bölümünde iki farklı veri türü (ve) için SizeOfLinkedList yönteminin çalışmasını test etmek için nasıl test edekleyebilirsiniz? `int` `char`

Bu kod iki yöntemi göstermektedir:

- bir test yardımcı yöntemi, `SizeOfLinkedListTestHelper<T>()` . Varsayılan olarak, bir test yardımcı yönteminin adı "TestHelper" olur.

- bir test yöntemi, `SizeOfLinkedListTest()` . Her test yöntemi TestMethod özniteliğiyle işaretlenir.

#### <a name="generated-test-code"></a>Oluşturulan test kodu
Aşağıdaki test kodu yönteminden `SizeOfLinkedList()` oluşturulmuş. Bu, oluşturulmamış test olduğundan, SizeOfLinkedList yöntemini doğru şekilde test etmek için değiştirilmelidir.

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

Yukarıdaki kodda, genel tür parametresi `GenericParameterHelper` olur. Aşağıdaki örnekte gösterildiği gibi belirli veri türlerini sağlamak için düzenleyebilirsiniz ancak bu deyimi düzenlemeden testi çalıştırabilirsiniz.

#### <a name="edited-test-code"></a>Düzenlenen test kodu
Aşağıdaki kodda test yöntemi ve test yardımcı yöntemi, test altındaki kodu başarıyla test etmek için `SizeOfLinkedList()` düzenlenmiştir.

##### <a name="test-helper-method"></a>Test yardımcı yöntemi
Test yardımcı yöntemi, 1. adımdan 5. adıma kadar etiketlenmiş kod satırlarına karşılık gelen aşağıdaki adımları gerçekleştirir.

1. Genel bir bağlantılı liste oluşturun.

2. Bağlantılı listeye dört düğüm ekleyin. Bu düğümlerin içeriğinin veri türü bilinmiyor.

3. Bağlantılı listenin beklenen boyutunu değişkenine `expected` attayın.

4. Bağlantılı listenin gerçek boyutunu hesaplar ve değişkenine `actual` atar.

5. Assert `actual` `expected` deyiminde ile karşılaştırın. Gerçek değer beklenene eşit olmazsa test başarısız olur.

##### <a name="test-method"></a>Test yöntemi
Test yöntemi, SizeOfLinkedListTest adlı testi çalıştırarak çağrılan koda derlenmiş olur. 6. ve 7. adım etiketli kod satırlarına karşılık gelen aşağıdaki adımları gerçekleştirir.

1. Testin `<int>` değişkenler için çalıştığını doğrulamak için test yardımcı yöntemini ne zaman çağırarak `integer` belirtebilirsiniz.

2. Testin `<char>` değişkenler için çalıştığını doğrulamak için test yardımcı yöntemini ne zaman çağırarak `char` belirtebilirsiniz.

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
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> SizeOfLinkedListTest testi her çalıştır çalıştırıldık, TestHelper yöntemi iki kez çağrılır. Testin başarılı olması için assert deyiminin her zaman true olarak değerlendirmesi gerekir. Test başarısız olursa, belirtilen çağrının mı yoksa belirtilen çağrının başarısız olup `<int>` olmadığı net bir şekilde `<char>` belirlenemilebilir. Yanıtı bulmak için çağrı yığınını inceler veya test yönteminize kesme noktaları ayarp testi çalıştırırken hata ayıklarsanız. Daha fazla bilgi için, [bkz. How to: Debug while running a test in an ASP.NET solution](/previous-versions/ms243172(v=vs.140)).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> Örnek 2: Tür kısıtlaması kullanma
Bu örnekte, karşılanmaz bir tür kısıtlaması kullanan genel bir yöntem için birim testi gösterir. İlk bölümde test altındaki kod projesinden kodlar yer almaktadır. Tür kısıtlaması vurgulanır.

İkinci bölümde test projesinden kodlar yer almaktadır.

#### <a name="code-under-test-project"></a>Test kapsamında kod projesi

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

#### <a name="test-project"></a>Projeyi test etmek

Yeni oluşturulan tüm birim testlerinde olduğu gibi, yararlı sonuçlar elde etmek için bu birim testinde de kesin olmayan Assert deyimleri eklemeniz gerekir. Bunları TestMethod özniteliğiyle işaretlenmiş yönteme değil, bu test için olarak adlandırılmış olan "TestHelper" yöntemine `DataTestHelper<T>()` eklersiniz.

Bu örnekte, genel tür parametresi `T` kısıtlamasına `where T : Employee` sahip. Bu kısıtlama test yönteminde karşılanmaz. Bu nedenle yöntemi, üzerinde yerleştirilen tür kısıtlamasını sağlamak için sizi uyaran `DataTest()` bir Assert deyimi `T` içerir. Bu Assert deyiminin iletisi şu şekilde okunur: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Başka bir deyişle, test yönteminden yöntemini çağırarak türünden veya sınıfından `DataTestHelper<T>()` `DataTest()` türetilen bir sınıf `Employee` parametresini geçmeniz `Employee` gerekir.

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

- [Kodunuzu birim testi](../test/unit-test-your-code.md)