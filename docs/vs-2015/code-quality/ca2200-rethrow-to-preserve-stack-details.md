---
title: 'CA2200: yığın ayrıntılarını korumak için yeniden throw | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d20407d7cc708ac785e4a792bf8e64768ea58540
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667386"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir özel durum yeniden oluşturulur ve `throw` bildiriminde özel durum açıkça belirtilir.

## <a name="rule-description"></a>Kural Tanımı
 Bir özel durum oluşturulduktan sonra, içerdiği bilgilerin bir kısmı yığın izgıdır. Yığın izlemesi, özel durumu oluşturan yöntemiyle başlayan ve özel durumu yakalayan yöntemle biten Yöntem çağrısı hiyerarşisinin bir listesidir. @No__t_0 deyimindeki özel durum belirtilerek bir özel durum yeniden oluşturulursa, yığın izlemesi geçerli yöntemde yeniden başlatılır ve özel durumu oluşturan özgün Yöntem ve geçerli yöntem arasındaki yöntem çağrılarının listesi kaybedilir. Özgün yığın izleme bilgilerini özel durumla birlikte tutmak için, özel durumu belirtmeden `throw` ifadesini kullanın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için özel durumu açıkça belirtmeden özel durumu yeniden oluşturun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve `CatchAndRethrowImplicitly` ' i ihlal eden `CatchAndRethrowExplicitly` ' ı bir yöntemi gösterir.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
