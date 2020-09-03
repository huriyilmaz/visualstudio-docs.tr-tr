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
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546295"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nesneleri birden çok kez atmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Yöntem uygulama, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> aynı nesne üzerinde, bazı türlerde bir Close () yöntemi gibi birden çok çağrıya veya bir Dispose eşdeğerine neden olabilecek kod yollarını içerir.

## <a name="rule-description"></a>Kural Tanımı
 Doğru şekilde uygulanan bir <xref:System.IDisposable.Dispose%2A> Yöntem, özel durum oluşturmadan birden çok kez çağrılabilir. Ancak, bu garanti edilmez ve bir <xref:System.ObjectDisposedException?displayProperty=fullName> <xref:System.IDisposable.Dispose%2A> nesne üzerinde birden fazla kez çağırmamalıdır.

## <a name="related-rules"></a>İlgili kurallar
 [CA2000: Kapsamı kaybetmeden önce nesneleri bırakın](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, uygulamayı kod yolundan bağımsız olarak, <xref:System.IDisposable.Dispose%2A> nesne için yalnızca bir kez çağırılabilecek şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. <xref:System.IDisposable.Dispose%2A>Nesnenin güvenli bir şekilde birden çok kez çağrılabilir olduğu bilinse bile, uygulama gelecekte değişebilir.

## <a name="example"></a>Örnek
 İç içe geçmiş `using` deyimler ( `Using` VISUAL BASIC) CA2202 uyarı ihlallerine neden olabilir. İç içe geçmiş iç deyimin IDisposable kaynağı `using` dıştaki deyimin kaynağını içeriyorsa `using` , `Dispose` iç içe kaynak yöntemi içerilen kaynağı serbest bırakır. Bu durum oluştuğunda, `Dispose` dış `using` deyimin yöntemi kaynağı ikinci bir kez atmayı dener.

 Aşağıdaki örnekte, <xref:System.IO.Stream> bir dış using ifadesinde oluşturulan bir nesne, <xref:System.IO.StreamWriter> nesneyi Içeren nesnenin Dispose yönteminde Inner using ifadesinin sonunda serbest bırakılır `stream` . Dış `using` deyimin sonunda, `stream` nesne ikinci kez serbest bırakılır. İkinci sürüm, CA2202 ihlaline neden olur.

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
 Bu sorunu çözmek için `try` / `finally` dış deyimin yerine bir blok kullanın `using` . `finally`Bloğunda, `stream` kaynağın null olmadığından emin olun.

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
 <xref:System.IDisposable?displayProperty=fullName>[Dispose kriteri](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
