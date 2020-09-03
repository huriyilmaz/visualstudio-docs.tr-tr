---
title: 'CA2006: yerel kaynakları kapsüllemek için SafeHandle kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fdf3ff02c86a878e9c955d2b3b92879870700efa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521153"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Yerel kaynakları kapsamak için SafeHandle kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Yönetilen kod, <xref:System.IntPtr> yerel kaynaklara erişmek için kullanır.

## <a name="rule-description"></a>Kural Tanımı
 `IntPtr`Yönetilen kodda kullanımı olası bir güvenlik ve güvenilirlik sorununa işaret edebilir. ' Nin tüm kullanımları `IntPtr` <xref:System.Runtime.InteropServices.SafeHandle> , onun yerine bir ya da benzer bir teknolojinin kullanılması gerekip gerekmediğini belirleyebilmek için incelenmelidir. `IntPtr`Yönetilen kodun sahip olarak kabul edildiği bellek, dosya tanıtıcısı veya bir yuva gibi bir yerel kaynağı temsil ediyorsa sorunlar meydana gelir. Yönetilen kod kaynağın sahibi ise, bunun bir hata olması durumunda kaynak sızıntısı oluşmasına neden olacağından, onunla ilişkili yerel kaynakları da serbest bırakmalıdır.

 Bu tür senaryolarda, çok iş parçacıklı erişime izin veriliyorsa `IntPtr` ve tarafından temsil edilen kaynağı serbest bırakma yoluyla güvenlik veya güvenilirlik sorunları da vardır `IntPtr` . Bu sorunlar, `IntPtr` kaynağın eşzamanlı kullanımı başka bir iş parçacığında yapıldığında kaynak sürümündeki değerin geri dönüşümünü içerir. Bu, bir iş parçacığının yanlış kaynakla ilişkili verileri okuyabildiği veya yazabileceği yarış koşullarına neden olabilir. Örneğin, türünüz bir işletim sistemi tanıtıcısını bir olarak depoluyorsa `IntPtr` ve kullanıcıların her zaman ve bu tanıtıcıyı **Close** kullanan başka bir yöntemi aynı anda ve bir tür eşitleme olmadan çağırmasını sağlar.

 Bu tanıtıcı geri dönüştürme sorunu, verilerin bozulmasına ve sıklıkla bir güvenlik açığına neden olabilir. `SafeHandle` ve eşdüzey sınıfı, <xref:System.Runtime.InteropServices.CriticalHandle> Bu tür iş parçacığı sorunlarından kaçınılması için bir kaynağa yerel tanıtıcıyı kapsüllemek için bir mekanizma sağlar. Ek olarak, `SafeHandle` diğer iş parçacığı sorunları için ve alt sınıfını kullanarak, yerel `CriticalHandle` metotların çağrıları üzerinde yerel tanıtıcının bir kopyasını içeren yönetilen nesnelerin ömrünü dikkatlice kontrol edebilirsiniz. Bu durumda, genellikle çağrılarını kaldırabilirsiniz `GC.KeepAlive` . `SafeHandle`Ve kullandığınızda ve daha düşük bir dereceye kadar yaptığınız performans yükü, `CriticalHandle` dikkatli bir tasarım aracılığıyla sık azaltılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 `IntPtr` `SafeHandle` Yerel kaynaklara erişimi güvenle yönetmek için kullanımı öğesine dönüştürün. <xref:System.Runtime.InteropServices.SafeHandle>Örnekler için başvuru konusuna bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarıyı gizmemelisiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable>
