---
title: 'DA0010: pahalı GetHashCode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0a2947f0bd6758de62a4a11d78390d38a503271
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919039"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Pahalı GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [DA0010: pahalı GetHashCode](/visualstudio/profiling/da0010-expensive-gethashcode).  

|||  
|-|-|  
|Kural Kimliği|DA0010|  
|Kategori|.NET Framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET belleği|  
|İleti|GetHashCode işlevleri bir tek EAP olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse karma kod işlevinin karmaşıklığını azaltın.|  
|Mesaj türü|Uyarı|  
  
## <a name="cause"></a>Sebep  
 Türün GetHashCode yöntemine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıyla veya yöntemin belleği ayırır.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Karma, büyük bir koleksiyondaki belirli bir öğeyi hızlı bir şekilde bulmanın bir tekniğidir. Karma tablolar çok büyük olabileceğinden ve yüksek oranda erişim desteklebildiğinden, karma tabloları son derece etkili olmalıdır. Bu gereksinimin bir engel, .NET Framework GetHashCode yöntemlerinin bellek ayırmamalıdır. Bellek ayırma, atık toplayıcıdaki yükü artırır ve ayırma isteğinin sonucu olarak çöp toplamayı çalıştırmak için gerekli hale gelirse, olası gecikmelerle yöntemi ortaya çıkarır.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Metodun karmaşıklığını azaltın.
