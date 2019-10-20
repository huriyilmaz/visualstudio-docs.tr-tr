---
title: CA5122 P-Invoke bildirimleri güvenli kritik olmamalıdır | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5d064f3d2bb382f1131d4e2365077f3db0b2e0ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669032"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 P/Invoke bildirimleri güvenli kritik olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 P/Invoke bildirimi <xref:System.Security.SecuritySafeCriticalAttribute> ile işaretlendi:

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke
   }
```

 Bu örnekte, `C.Beep(...)` bir güvenlik güvenli kritik yöntemi olarak işaretlendi.

## <a name="rule-description"></a>Kural Tanımı
 Güvenlik duyarlı işlem gerçekleştirildiğinde yöntemler SecuritySafeCritical olarak işaretlenir ancak saydam mod kullanılarak da güvenli olur. Güvenlik saydamlık modelinin temel kurallarından biri saydam kod P/Invoke aracılığıyla yerel koda hiçbir zaman doğrudan çağırmaz. Bu nedenle, P/Invoke güvenlik güvenli kritik olarak işaretleme çağırmak için saydam kodu etkinleştirmez ve güvenlik çözümlemesi için yanıltıcıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 P/Invoke saydam kodu kullanılabilir yapmak için güvenlik güvenli kritik sarmalayıcı yöntemini kullanır:

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.
