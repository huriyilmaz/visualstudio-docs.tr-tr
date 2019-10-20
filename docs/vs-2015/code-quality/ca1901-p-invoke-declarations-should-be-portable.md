---
title: 'CA1901: P-Invoke bildirimleri taşınabilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d1b4c0c5bcf22db6558f156fd1acd0be94026b08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661058"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: P/Invoke bildirimleri taşınabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategori|Microsoft. taşınabilirlik|
|Yeni Değişiklik|Parçalama-P/Invoke derlemenin dışında görünüyorsa. Bölünmez olmayan-P/Invoke derlemenin dışında görünür değilse.|

## <a name="cause"></a>Sebep
 Bu kural, her parametrenin boyutunu ve bir P/Invoke dönüş değerini değerlendirir ve 32-bit ve 64 bit platformlarındaki yönetilmeyen koda sıralanmış olarak bunların boyutunun doğru olduğunu doğrular. Bu kuralın en yaygın ihlali, platforma bağımlı, işaretçi boyutunda bir değişkenin gerekli olduğu sabit boyutlu bir tamsayıyı iletmektir.

## <a name="rule-description"></a>Kural Tanımı
 Aşağıdaki senaryolardan biri bu kuralın oluştuğunu ihlal ediyor:

- Dönüş değeri veya parametresi, `IntPtr` olarak yazılması gerektiğinde sabit boyutlu bir tamsayı olarak yazılır.

- Dönüş değeri veya parametresi, sabit boyutlu bir tamsayı olarak yazılması gerektiğinde bir `IntPtr` olarak yazılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 @No__t_2 veya `UInt32` yerine tutamaçları temsil etmek için `IntPtr` veya `UIntPtr` kullanarak bu ihlalin düzelini çözebilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarıyı gizmemelisiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralın ihlaline neden olduğunu gösterir.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 Bu örnekte, `nIconIndex` parametresi, 32 bitlik bir platformda 4 bayt genişliğinde ve 64 bitlik bir platformda 8 bayt genişliğinde olan bir `IntPtr` olarak bildirilmiştir. Aşağıdaki yönetilmeyen bildirimde, `nIconIndex` ' ın tüm platformlarda 4 baytlık işaretsiz bir tamsayı olduğunu görebilirsiniz.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Örnek
 İhlalin giderilmesi için bildirimi aşağıdaki şekilde değiştirin:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Taşınabilirlik Uyarıları](../code-quality/portability-warnings.md)
