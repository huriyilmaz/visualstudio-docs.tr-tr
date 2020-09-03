---
title: 'CA2106: güvenli onaylar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547751"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Onay deyimlerinin güvenliğini sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir yöntem izin ileri sürer ve güvenlik önlemi olmayan çağrı üzerinde gerçekleşir.

## <a name="rule-description"></a>Kural Tanımı
 Güvenlik denetimleri yapmadan herhangi bir güvenlik izni ileri sürmek, kodunuzdaki güvenlik zayıflıklarını yararlanılabilir bırakır. Güvenlik yığını, bir güvenlik izni belirtildiğine göre ilerleme gösterir. Arayan üzerinde herhangi bir denetim gerçekleştirmeksizin bir izin belirtirseniz, çağıran, izinlerinizi kullanarak kodu dolaylı olarak yürütebilir. Güvenlik denetimleri olmadan Onaylamalar yalnızca, onay için zararlı bir şekilde kullanılmadığından emin olduğunuzda izin verilebilir. Çağırdığınız kod zararsız ise veya kullanıcılar, çağırdığınız koda rastgele bilgi geçiremezse bir onaylama işlemi zararsız olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yönteme veya bildirim türüne bir güvenlik talebi ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı yalnızca dikkatli bir güvenlik incelemesi sonrasında gizleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Güvenli Kodlama Yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
