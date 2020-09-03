---
title: MSBuild En Iyi yöntemleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181123"
---
# <a name="msbuild-best-practices"></a>MSBuild En İyi Yöntemleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild betikleri yazmak için aşağıdaki en iyi yöntemleri öneririz:  
  
- Varsayılan özellik değerleri `Condition` , varsayılan değeri komut satırında geçersiz kılınabilen bir özellik bildirerek değil, özniteliği kullanılarak en iyi şekilde işlenir. Örneğin,  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- Öğeleri seçtiğinizde Joker karakterlerden kaçının. Bunun yerine, dosyaları açıkça belirtin. Bu, dosya ekleme veya silme sırasında oluşabilecek hataların izlenmesini kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
