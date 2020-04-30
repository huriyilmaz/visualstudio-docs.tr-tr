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
ms.openlocfilehash: 318b7b8adddd674a9b8ecb93441d69a76ab574dd
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586781"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Sorunlu metotları çağırmaktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
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
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend ve Thread. özgeçmişi öngörülemeyen davranışları nedeniyle kullanım dışı bırakıldı.  <xref:System.Threading> Ad <xref:System.Threading.Monitor>alanındaki <xref:System.Threading.Mutex>diğer sınıfları kullanın, örneğin,, ve <xref:System.Threading.Semaphore> iş parçacıklarını senkronize etmek ya da kaynakları korumak için.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|DangerousGetHandle çağrısını yöntemi, geçerli olmayan bir tanıtıcı döndürebildiğinden bir güvenlik riski taşıyor. DangerousGetHandle çağrısını yönteminin <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> nasıl güvenli <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> bir şekilde kullanılacağı hakkında daha fazla bilgi için bkz. ve yöntemleri.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Bu yöntemler, beklenmeyen konumlardan derleme yükleyebilir. Örneğin, bkz. Suzanne Cook 'ın .NET CLR notları blog gönderileri [LoadFile vs. LoadFrom](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) ve derlemeleri yükleyen yöntemler hakkında BILGI Için MSDN Web sitesinde [bağlama bağlamı seçme](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) .|
|[Cosetproxypaket](https://msdn.microsoft.com/library/ms692692.aspx) (Ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (Ole32)|Yönetilen bir işlemde kullanıcı kodunun yürütülmeye başladığı zaman, Cosetproxypaket güvenilir bir şekilde çağrılamaz. Ortak dil çalışma zamanı (CLR), kullanıcıların P/Invoke işleminin başarılı olmasını engelleyebilen başlatma eylemleri alır.<br /><br /> Yönetilen bir uygulama için Cosetproxyıncall çağrısı yapmanız gerekiyorsa, bir yerel kod (C++) yürütülebilirini kullanarak işlemi başlatmanız, yerel kodda Cosetproxyıncall çağrısı yapmanız ve sonra yönetilen kod uygulamanızı işlem içinde başlatmanız önerilir. (Bir çalışma zamanı sürüm numarası belirttiğinizden emin olun.)|

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, tehlikeli veya sorunlu yönteme çağrıyı kaldırın veya değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca sorunlu yöntemin herhangi bir alternatifi kullanılabilir olmadığında bu kuraldan iletileri bastırmalısınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenilirlik uyarıları](../code-quality/reliability-warnings.md)
