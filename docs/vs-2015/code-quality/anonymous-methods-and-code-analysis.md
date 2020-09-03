---
title: Anonim yöntemler ve kod analizi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652220"
---
# <a name="anonymous-methods-and-code-analysis"></a>Anonim Yöntemler ve Kod Analizi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Anonim yöntem* adı olmayan bir yöntemdir. Anonim yöntemler en sık, bir kod bloğunu temsilci parametresi olarak geçirmek için kullanılır.

 Bu konu, kod analizinin, anonim yöntemlerle ilişkili uyarıları ve ölçümleri nasıl işlediğini açıklar.

## <a name="anonymous-methods-declared-in-a-member"></a>Bir üyede belirtilen anonim Yöntemler
 Yöntem veya erişimci gibi bir üyede bildirildiği anonim bir yöntemin uyarıları ve ölçümleri, yöntemi bildiren üyeyle ilişkilendirilir. Bu, yöntemi çağıran üyeyle ilişkili değildir.

 Örneğin, aşağıdaki sınıfta, **anonymousMethod** bildiriminde bulunan tüm uyarılar **Method2**değil **Method1** 'ye karşı yapılmalıdır.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Satır içi anonim Yöntemler
 Bir alana satır içi atama olarak belirtilen anonim bir yöntemin uyarıları ve ölçümleri, Oluşturucu ile ilişkilendirilir. Alan `static` ( `Shared` içinde) olarak bildirilirse [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , uyarılar ve ölçümler sınıf oluşturucusuyla ilişkilendirilir; Aksi takdirde, örnek Oluşturucu ile ilişkilendirilir.

 Örneğin, aşağıdaki sınıfta, **anonymousMethod1** bildiriminde bulunan tüm uyarılar, **sınıfının**örtük olarak oluşturulan varsayılan oluşturucusuna göre oluşturulacaktır. Ancak, **anonymousMethod2** ' de bulunan bulunanlar örtük olarak oluşturulan sınıf oluşturucusuna göre uygulanır.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

 Bir sınıf, birden çok Oluşturucusu olan bir alana değer atayan bir satır içi anonim yöntem içerebilir. Bu durumda, Oluşturucu aynı sınıftaki başka bir oluşturucuya zincirsiz değilse, uyarılar ve ölçümler tüm oluşturucularla ilişkilendirilir.

 Örneğin, aşağıdaki sınıfta, **anonymousMethod** bildiriminde bulunan tüm uyarılar **Sınıf (INT)** ve **sınıfa (dize)** karşı yapılmalıdır, ancak sınıfa ( **)** karşılık gelmelidir.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

 Bu beklenmeyen görünse de, derleyici başka bir oluşturucuya zincirlemeyen her Oluşturucu için benzersiz bir yöntem çıkardığı için bu durum oluşur. Bu davranış nedeniyle, **anonymousMethod** 'da oluşan herhangi bir ihlalin ayrı olarak bastırılmalıdır. Bu Ayrıca, yeni bir oluşturucunun tanıtılmasından sonra **Sınıf (int)** ve **Sınıf (dize)** için daha önce gizlenen uyarıların de yeni oluşturucuya karşı gizlenmesi gerektiğini gösterir.

 Bu soruna geçici bir çözüm olarak iki şekilde çalışabilirsiniz. Tüm oluşturucular zincirinden ortak bir oluşturucuda **anonymousMethod** bildirebilirsiniz. Ya da bunu tüm oluşturucular tarafından çağrılan bir başlatma yönteminde bildirebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
