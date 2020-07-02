---
title: 'CA1062: ortak yöntemlerin bağımsız değişkenlerini doğrulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533243"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Genel metotların bağımsız değişkenlerini doğrulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir yöntem, bağımsız değişkenin `null` (Visual Basic) olup olmadığını doğrulamadan başvuru bağımsız değişkenlerinden birine başvurur `Nothing` .

## <a name="rule-description"></a>Kural Tanımı
 Dışarıdan görünen yöntemlere geçirilen tüm başvuru bağımsız değişkenleri için gözden geçirilmesi gerekir `null` . Uygunsa, <xref:System.ArgumentNullException> bağımsız değişken olduğunda bir oluşturun `null` .

 Ortak veya korumalı olarak bildirildiği için bir yöntem bilinmeyen bir derlemeden çağrılabilecek ise, yöntemin tüm parametrelerini doğrulamanız gerekir. Yöntemi yalnızca bilinen derlemeler tarafından çağrılabilir şekilde tasarlanmışsa, yöntemi iç yapmanız ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini, yöntemi içeren derlemeye uygulamanız gerekir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için her başvuru bağımsız değişkenini ile karşılaştırarak doğrulayın `null` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Başvuru yapılan parametrenin işlev içindeki başka bir yöntem çağrısı tarafından doğrulandığından eminseniz, bu kuraldan bir uyarıyı gizleyebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralını karşılayan bir yöntemi ihlal eden bir yöntemi gösterir.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Örnek
 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]' De, bu kural, parametreleri doğrulamayı yapan başka bir yönteme geçirmekte olduğunu algılamaz.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Örnek
 Başvuru nesneleri olan alan veya özellikleri dolduran kopya oluşturucular, CA1062 kuralını da ihlal edebilir. Bu ihlal, kopya oluşturucusuna geçirilen kopyalanmış nesne `null` (Visual Basic) olabileceğinden meydana gelir `Nothing` . İhlalin çözülmesi için, kopyalanmış nesnenin null olup olmadığını denetlemek üzere statik (Visual Basic ile paylaşılan) metodunu kullanın.

 Aşağıdaki `Person` sınıf örneğinde, `other` kopya oluşturucuya geçirilen nesne olabilir `Person` `null` .

```

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
 Aşağıdaki düzeltilen `Person` örnekte, `other` Copy oluşturucusuna geçirilen nesne, öncelikle yönteminde null değeri denetlenir `PassThroughNonNull` .

```
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
            throw new ArgumentNullException("person");
        return person;
    }
}
```
