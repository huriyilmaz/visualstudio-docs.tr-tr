---
title: 'DA0011: pahalı CompareTo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ed433612498a6b7d4b87291311d7fd6efcb0974
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918379"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Pahalı CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [DA0011: pahalı CompareTo](/visualstudio/profiling/da0011-expensive-compareto).  
  
|||  
|-|-|  
|Kural Kimliği|DA0011|  
|Kategori|.NET Framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> .NET belleği|  
|İleti|CompareTo işlevleri, ucuz olmalı ve herhangi bir bellek ayırmamalıdır. Mümkünse, CompareTo işlevi karmaşıklığını azaltın.|  
|Kural türü|Uyarı|  
  
## <a name="cause"></a>Sebep  
 Türün CompareTo yöntemi pahalıdır veya bellek ayırır.  
  
## <a name="rule-description"></a>Kural Tanımı  
 CompareTo metotları etkili olmalıdır ve bellek ayırmamalıdır.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 CompareTo yönteminin karmaşıklığını azaltın.
