---
title: 'CA2001: sorunlu yöntemleri çağırmaktan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba64c27cde5f335f32cca362417078a5c9ed13e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538586"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Sorunlu metotları çağırmaktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir üye olası tehlikeli ya da sorunlu yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Gereksiz ve potansiyel olarak tehlikeli Yöntem çağrıları yapmaktan kaçının.

 Bu kuralın ihlali, bir üye aşağıdaki yöntemlerden birini çağırdığında oluşur.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC çağrılıyor. Toplama, uygulama performansını önemli ölçüde etkileyebilir ve nadiren gereklidir. Daha fazla bilgi için bkz. MSDN 'de [Riko Marianı 'Nin performans](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) ve blog girişi.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend ve Thread. özgeçmişi öngörülemeyen davranışları nedeniyle kullanım dışı bırakıldı.  Ad alanındaki diğer sınıfları kullanın, örneğin,, <xref:System.Threading> <xref:System.Threading.Monitor> <xref:System.Threading.Mutex> ve <xref:System.Threading.Semaphore> iş parçacıklarını senkronize etmek ya da kaynakları korumak için.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle çağrısını yöntemi, geçerli olmayan bir tanıtıcı döndürebildiğinden bir güvenlik riski taşıyor. <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> DangerousGetHandle çağrısını yönteminin nasıl güvenli bir şekilde kullanılacağı hakkında daha fazla bilgi için bkz. ve yöntemleri.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Bu yöntemler, beklenmeyen konumlardan derleme yükleyebilir. Örneğin, bkz. Suzanne Cook 'ın .NET CLR notları blog gönderileri [LoadFile vs. LoadFrom](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) ve derlemeleri yükleyen yöntemler hakkında BILGI Için MSDN Web sitesinde [bağlama bağlamı seçme](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) .|
|[Cosetproxypaket](https://msdn.microsoft.com/library/ms692692.aspx) (Ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (Ole32)|Yönetilen bir işlemde kullanıcı kodunun yürütülmeye başladığı zaman, Cosetproxypaket güvenilir bir şekilde çağrılamaz. Ortak dil çalışma zamanı (CLR), kullanıcıların P/Invoke işleminin başarılı olmasını engelleyebilen başlatma eylemleri alır.<br /><br /> Yönetilen bir uygulama için Cosetproxyıncall çağrısı yapmanız gerekiyorsa, bir yerel kod (C++) yürütülebilirini kullanarak işlemi başlatmanız, yerel kodda Cosetproxyıncall çağrısı yapmanız ve sonra yönetilen kod uygulamanızı işlem içinde başlatmanız önerilir. (Bir çalışma zamanı sürüm numarası belirttiğinizden emin olun.)|

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, tehlikeli veya sorunlu yönteme çağrıyı kaldırın veya değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca sorunlu yöntemin herhangi bir alternatifi kullanılabilir olmadığında bu kuraldan iletileri bastırmalısınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenilirlik uyarıları](../code-quality/reliability-warnings.md)
