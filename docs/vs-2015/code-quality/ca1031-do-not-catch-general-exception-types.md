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
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542408"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Genel özel durum türlerini yakalamayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ya da gibi genel bir özel durum ya da gibi bir <xref:System.Exception?displayProperty=fullName> <xref:System.SystemException?displayProperty=fullName> `catch` genel catch yan tümcesi `catch()` kullanılır.

## <a name="rule-description"></a>Kural Tanımı
 Genel özel durum yakalanmamalı.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, daha belirli bir özel durumu yakalayın veya bloktaki son deyimle genel özel durumu yeniden oluşturun `catch` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Genel özel durum türlerini yakalama, kitaplık kullanıcısının çalışma zamanı sorunlarını gizleyebilir ve hata ayıklamayı daha zor hale getirebilirsiniz.

> [!NOTE]
> İle başlayarak [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] , ortak dil çalışma zamanı (CLR) artık işletim sisteminde oluşan bozuk durum özel durumlarını ve ' deki erişim ihlalleri gibi yönetilen kod tarafından işlenecek şekilde yönetilen kodu teslim eder [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] . [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]Veya sonraki sürümlerde bir uygulamayı derlemek ve bozulmuş durum özel durumlarının işlenmesini sürdürmek istiyorsanız, <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> özniteliği bozuk durum özel durumunu işleyen yönteme uygulayabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü ve bloğu doğru bir şekilde uygulayan bir türü gösterir `catch` .

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2200: Yığın ayrıntılarını korumak için yeniden fırlatın](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
