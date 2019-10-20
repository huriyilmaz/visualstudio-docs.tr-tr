---
title: 'CA1725: parametre adları temel bildirimle eşleşmelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 128069bb24dfc8b1c11963e33c9541701b0eea15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653749"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Parametre adları taban yöntem ile eşleşmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir metodun bir parametresinin adı, metodun temel bildirimindeki parametre adı veya metodun arabirim bildiriminde parametrenin adı ile eşleşmez değil.

## <a name="rule-description"></a>Kural Tanımı
 Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için parametreyi temel bildirimle eşleşecek şekilde yeniden adlandırın. Bu çözüm, COM görünebilir yöntemlerine yönelik bir son değişiklik.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk edilen kitaplıklarda COM görünebilir Yöntemler hariç, bu kuraldan bir uyarıyı bastırmayın.
