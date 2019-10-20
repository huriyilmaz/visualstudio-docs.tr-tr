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
ms.openlocfilehash: 394fafb0c9185a5e11ba759a5b873236956cf25b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652210"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Yerel kaynakları kapsamak için SafeHandle kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategori|Microsoft. güvenilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Yönetilen kod, yerel kaynaklara erişmek için <xref:System.IntPtr> kullanır.

## <a name="rule-description"></a>Kural Tanımı
 Yönetilen kodda `IntPtr` kullanımı, olası bir güvenlik ve güvenilirlik sorununa işaret edebilir. @No__t_0 tüm kullanımları, onun yerine <xref:System.Runtime.InteropServices.SafeHandle> veya benzer bir teknolojinin kullanılması gerekip gerekmediğini belirleyebilmek için incelenmelidir. @No__t_0, bellek, dosya tanıtıcısı veya bir yuva gibi bir yerel kaynağı temsil ediyorsa, yönetilen kodun sahip olarak kabul edildiği sorunlar meydana gelir. Yönetilen kod kaynağın sahibi ise, bunun bir hata olması durumunda kaynak sızıntısı oluşmasına neden olacağından, onunla ilişkili yerel kaynakları da serbest bırakmalıdır.

 Bu tür senaryolarda, çok iş parçacıklı erişime `IntPtr` ' a izin veriliyorsa ve `IntPtr` tarafından temsil edilen kaynağı serbest bırakma bir yolu sağlandığında güvenlik veya güvenilirlik sorunları da vardır. Bu sorunlar, kaynağın eşzamanlı kullanımı başka bir iş parçacığında yapıldığında kaynak sürümünde `IntPtr` değerinin geri dönüşümünü içerir. Bu, bir iş parçacığının yanlış kaynakla ilişkili verileri okuyabildiği veya yazabileceği yarış koşullarına neden olabilir. Örneğin, türünüz bir `IntPtr` olarak bir işletim sistemi tanıtıcısı depoluyorsa ve kullanıcıların her ikisi de aynı anda **ve bir** tür eşitleme olmadan bu tanıtıcıyı kullanan başka bir yöntemi çağırmasını sağlamasına izin veriyorsa, kodunuzun bir tanıtıcı geri dönüştürme sorunu vardır.

 Bu tanıtıcı geri dönüştürme sorunu, verilerin bozulmasına ve sıklıkla bir güvenlik açığına neden olabilir. `SafeHandle` ve eşdüzey sınıfı <xref:System.Runtime.InteropServices.CriticalHandle>, bu iş parçacığı sorunlarının önlenebilir olması için bir kaynağa yerel tanıtıcıyı kapsüllemek için bir mekanizma sağlar. Buna ek olarak, diğer iş parçacığı sorunları için `SafeHandle` ve eşdüzey sınıfını `CriticalHandle` ' i kullanarak diğer iş parçacığı sorunları için yerel tanıtıcının bir kopyasını içeren yönetilen nesnelerin ömrünü dikkatlice kontrol edebilirsiniz. Bu durumda, genellikle `GC.KeepAlive` ' a yapılan çağrıları kaldırabilirsiniz. @No__t_0 kullandığınızda ve `CriticalHandle` daha az bir dereceye kadar yaptığınız performans yükü, dikkatli bir tasarım aracılığıyla sık azaltılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Yerel kaynaklara erişimi güvenle yönetmek için `IntPtr` kullanımını `SafeHandle` olarak dönüştürün. Örnekler için <xref:System.Runtime.InteropServices.SafeHandle> başvuru konusuna bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarıyı gizmemelisiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable>
