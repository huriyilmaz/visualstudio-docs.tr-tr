---
title: 'CA2139: Saydam yöntemler HandleProcessCorruptingExceptions özniteliğini kullanamaz özniteliğini kullanamaz | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 233e4366befd2a5a0d5690b14198ac13e2fcc957
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546490"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Saydam metotlar HandleProcessCorruptingExceptions özniteliğini kullanamaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Saydam bir yöntem, <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> özniteliğiyle işaretlenir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, saydam olan ve özniteliği kullanarak bir işlem bozulmasını işlemeye çalışır olan herhangi bir yöntemi harekete geçirilir <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> . İşlem bozulmayan özel durum, özel durumların CLR sürüm 4,0 özel durum sınıflandırmasıdır <xref:System.AccessViolationException> . HandleProcessCorruptedStateExceptionsAttribute özniteliği, sadece kritik güvenlik yöntemleri tarafından kullanılır ve saydam bir yöntem uygulanırsa yoksayılır. İşlem bozulmayan özel durumları işlemek için, bu yöntem güvenlik açısından kritik veya güvenli güvenlik açısından kritik hale gelmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> özniteliğini kaldırın veya yöntemi <xref:System.Security.SecurityCriticalAttribute> ya da özniteliğiyle işaretleyin <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Bu örnekte, saydam bir yöntem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> özniteliğiyle işaretlenir ve kuralı başarısız olur. Yöntemi veya özniteliğiyle de işaretlenmiş olmalıdır <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]
