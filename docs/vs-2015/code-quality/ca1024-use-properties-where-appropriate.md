---
title: 'CA1024: uygun yerlerde özellikleri kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b190e007cfdb016e54148cf0295c68baf68c5033
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661958"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Uygun yerlerde özellikler kullan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir yöntemin `Get` ile başlayan bir adı vardır, hiçbir parametre kullanmaz ve dizi olmayan bir değer döndürür.

## <a name="rule-description"></a>Kural Tanımı
 Çoğu durumda, özellikler verileri ve yöntemleri eylemler gerçekleştirir. Özellikler, alanları gibi erişilir, bu da daha kolay kullanılmasını sağlar. Bu koşullardan biri mevcutsa, bir özellik olmak için bir yöntem iyi bir adaydır:

- Bağımsız değişken almaz ve bir nesnenin durum bilgilerini döndürür.

- Bir nesnenin durumunun bir bölümünü ayarlamak için tek bir bağımsız değişkeni kabul eder.

  Özellikler alanlar gibi davranmalıdır; yöntemi değilse, bir özelliğe değiştirilmemelidir. Yöntemler aşağıdaki durumlarda özelliklerden daha iyidir:

- Yöntemi zaman alan bir işlem gerçekleştirir. Yöntemi, bir alanın değerini ayarlamak ya da almak için gereken zamandan daha yavaştır perceivably.

- Yöntemi bir dönüştürme gerçekleştirir. Bir alana erişmek, depoladığı verilerin dönüştürülmüş bir sürümünü döndürmez.

- Get yönteminin bir observable yan etkisi vardır. Bir alanın değerini almak hiçbir yan efekt oluşturmaz.

- Yürütmenin sırası önemlidir. Bir alanın değerini ayarlamak, diğer işlemlerin oluşumuna bağlı değildir.

- Yöntemi art arda iki kez çağırmak farklı sonuçlar oluşturur.

- Yöntemi statiktir, ancak çağıran tarafından değiştirilebilen bir nesne döndürür. Bir alanın değerini almak, çağıranın alan tarafından depolanan verileri değiştirmesine izin vermez.

- Yöntemi bir dizi döndürür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yöntemini bir özelliği olarak değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yöntem daha önce listelenen ölçütlerden en az birini karşılıyorsa, bu kuraldan bir uyarı gizleyin.

## <a name="controlling-property-expansion-in-the-debugger"></a>Hata ayıklayıcıda Özellik genişletmeyi denetleme
 Programcıların bir özelliği kullanmaktan kaçınmasının nedeni, hata ayıklayıcının otomatik olarak genişletmesine engel olmasıdır. Örneğin, özelliği büyük bir nesne ayırmayı veya bir P/Invoke çağırmayı içerebilir, ancak aslında herhangi bir observable yan etkisi olmayabilir.

 @No__t_0 uygulayarak hata ayıklayıcının özellikleri otomatik olarak genişletmesinin engellenmesini sağlayabilirsiniz. Aşağıdaki örnek, bir örnek özelliğine uygulanan bu özniteliği gösterir.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, özelliklerine dönüştürülmesi gereken çeşitli yöntemler ve bunlar gibi davranmamaları nedeniyle olmaması gereken birkaç yöntem içerir.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
