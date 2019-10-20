---
title: 'CA1031: genel özel durum türlerini yakalamayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2696446ee2b257b78559909c0cba672cded39943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661890"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Genel özel durum türlerini yakalamayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_0 veya <xref:System.SystemException?displayProperty=fullName> gibi genel bir özel durum `catch` ifadesinde yakalanır veya `catch()` gibi genel bir catch yan tümcesi kullanılır.

## <a name="rule-description"></a>Kural Tanımı
 Genel özel durum yakalanmamalı.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, daha belirli bir özel durumu yakalayın veya `catch` bloğundaki son bildiri olarak genel özel durumu yeniden oluşturun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Genel özel durum türlerini yakalama, kitaplık kullanıcısının çalışma zamanı sorunlarını gizleyebilir ve hata ayıklamayı daha zor hale getirebilirsiniz.

> [!NOTE]
> @No__t_0 başlayarak, ortak dil çalışma zamanı (CLR) artık işletim sisteminde oluşan bozuk durum özel durumlarını ve yönetilen kod tarafından işlenmek üzere [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] erişim ihlalleri gibi yönetilen kodu teslim eder. @No__t_0 veya sonraki sürümlerde bir uygulamayı derlemek ve bozulmuş durum özel durumlarının işlenmesini sürdürmek istiyorsanız, <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> özniteliğini bozuk durum özel durumunu işleyen yönteme uygulayabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü ve `catch` bloğunu doğru bir şekilde uygulayan bir türü gösterir.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
