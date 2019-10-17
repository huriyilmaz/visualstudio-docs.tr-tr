---
title: 'CA1062: Genel yöntemlerin bağımsız değişkenlerini doğrulayın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6019956d37d420b72275223148c2a3468a820884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440711"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Genel yöntemlerin bağımsız değişkenlerini doğrulayın

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategori|Microsoft. Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Dışarıdan görülebilen bir yöntem, bağımsız değişkenin `null` (Visual Basic `Nothing`) olup olmadığını doğrulamadan başvuru bağımsız değişkenlerinden birine başvurur.

## <a name="rule-description"></a>Kural açıklaması

Dışarıdan görünen yöntemlere geçirilen tüm başvuru bağımsız değişkenleri `null` ' a karşı denetlenmelidir. Uygunsa, bağımsız değişken `null` olduğunda <xref:System.ArgumentNullException> oluşturun.

Ortak veya korumalı olarak bildirildiği için bir yöntem bilinmeyen bir derlemeden çağrılabilecek ise, yöntemin tüm parametrelerini doğrulamanız gerekir. Yöntem yalnızca bilinen derlemeler tarafından çağrılabilir şekilde tasarlanmışsa, yöntemi iç yapmanız ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini yöntemi içeren derlemeye uygulamanız gerekir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için her başvuru bağımsız değişkenini `null` ' a karşı doğrulayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Başvuru yapılan parametrenin işlev içindeki başka bir yöntem çağrısı tarafından doğrulandığından eminseniz, bu kuraldan bir uyarıyı gizleyebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kuralı ve kuralını karşılayan bir yöntemi ihlal eden bir yöntemi gösterir.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException(nameof(input));
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException(NameOf(input))
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Örnek

Başvuru nesneleri olan alan veya özellikleri dolduran kopya oluşturucular, CA1062 kuralını da ihlal edebilir. Bu ihlal, kopya oluşturucusuna geçirilen kopyalanmış nesne `null` (Visual Basic `Nothing`) olabileceğinden meydana gelir. İhlalin çözülmesi için, kopyalanmış nesnenin null olup olmadığını denetlemek üzere statik (Visual Basic ile paylaşılan) metodunu kullanın.

Aşağıdaki `Person` sınıfı örneğinde, `Person` kopya oluşturucusuna geçirilen `other` nesnesi `null` olabilir.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Örnek

Aşağıdaki düzeltilen `Person` örneğinde, kopyalama oluşturucusuna geçirilen `other` nesnesi, önce `PassThroughNonNull` yönteminde null değeri denetlenir.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException(nameof(person));
        return person;
    }
}
```
