---
title: 'CA2202: nesneleri birden çok kez atma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667399"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nesneleri birden çok kez atmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Yöntem uygulama, aynı nesne üzerinde <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> birden çok çağrıya veya bazı türlerde Close () yöntemi gibi bir Dispose eşdeğerine neden olabilecek kod yolları içerir.

## <a name="rule-description"></a>Kural Tanımı
 Doğru uygulanmış bir <xref:System.IDisposable.Dispose%2A> yöntemi, özel durum oluşturmadan birden çok kez çağrılabilir. Ancak, bu garanti edilmez ve bir <xref:System.ObjectDisposedException?displayProperty=fullName> üretmemek için bir nesne üzerinde birden çok kez <xref:System.IDisposable.Dispose%2A> çağırmamalıdır.

## <a name="related-rules"></a>İlgili kurallar
 [CA2000: Kapsamı kaybetmeden önce verileri atın](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, uygulamayı kod yolundan bağımsız olarak değiştirin, <xref:System.IDisposable.Dispose%2A> nesne için yalnızca bir kez çağırılır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Nesne için <xref:System.IDisposable.Dispose%2A> çok kez güvenle çağrılabilir olarak bilinse bile, uygulama gelecekte değişebilir.

## <a name="example"></a>Örnek
 İç içe `using` deyimleri (Visual Basic `Using`), CA2202 uyarı ihlallerine neden olabilir. İç içe geçmiş iç `using` ifadesinin IDisposable kaynağı, dış `using` ifadesinin kaynağını içeriyorsa, iç içe geçmiş kaynağın `Dispose` yöntemi içerilen kaynağı serbest bırakır. Bu durum oluştuğunda, dış `using` ifadesinin `Dispose` yöntemi, kaynağını ikinci kez atmayı dener.

 Aşağıdaki örnekte, bir dıştaki using ifadesinde oluşturulan <xref:System.IO.Stream> nesnesi, `stream` nesnesini içeren <xref:System.IO.StreamWriter> nesnesinin Dispose yönteminde yer alan Inner using ifadesinin sonunda serbest bırakılır. Dış `using` ifadesinin sonunda, `stream` nesnesi ikinci kez serbest bırakılır. İkinci sürüm, CA2202 ihlaline neden olur.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Örnek
 Bu sorunu çözmek için, dış `using` ifadesinin yerine bir `try` / `finally` bloğunu kullanın. @No__t_0 bloğunda, `stream` kaynağının null olmadığından emin olun.

```
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable?displayProperty=fullName> [Dispose deseninin](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
