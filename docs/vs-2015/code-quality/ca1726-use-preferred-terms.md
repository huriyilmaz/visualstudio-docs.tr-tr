---
title: 'CA1726: tercih edilen terimleri kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96e0614bc5c08c83008af4e67a2aa865f08f74f3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547816"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Tercih edilen terimleri kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1726: tercih edilen terimleri kullanın](/visualstudio/code-quality/ca1726-use-preferred-terms).

|Öğe|Değer|
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Parçalara ayırma-derlemeler üzerinde harekete geçirildiğinde<br /><br /> Tür parametrelerinde harekete geçirildiğinde, bozmasız|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir tanımlayıcının adı, tercih edilen terim varolduğunda alternatif olarak bir terim içerir. Alternatif olarak, ad Işaret veya bayraklarını içerir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, bir tanımlayıcıyı belirteçlere ayrıştırır. Her bir tek belirteç ve her bitişik çift belirteci birleşimi, kurala ve özel sözlüklerin kullanım dışı bölümüne yerleştirilmiş koşullarla karşılaştırılır. Aşağıdaki tabloda, kuralda yerleşik olan koşullar ve tercih edilen alternatifler gösterilmektedir.

|Kullanılmayan dönem|Tercih edilen dönem|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` veya `Flags`|Bir değiştirme dönemi yoktur. Kullanmayın.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için terimi tercih edilen alternatif terim ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca tanımlayıcının adı kasıtlı olarak belirtilmişse ve özellikle de tercih edilen dönem yerine özgün terimiyle ilişkili olduğunda bu kuraldan bir uyarı gizleyin.

## <a name="related-rules"></a>İlgili kurallar
 [Adlandırma uyarıları](../code-quality/naming-warnings.md)
