---
title: Büyük projeler oluşturduğunuzda belleği verimli bir şekilde kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28d9f3d43faa53731b101dfdf58fe1e68a0920c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178297"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Büyük Projeler Derlerken Belleği Verimli Şekilde Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Büyük projeler genellikle birçok alt proje ve diğer bağımlılıkları içerir ve bunlar derleme zamanında çok fazla sistem belleği tüketebilir. Kullanılabilir sistem belleği azaltıldı, sistem performansı da azalabilir. Projelerin daha eski sürümleri [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bellekte kalır veya sürüm 3,5 ' de projeler kaldırılmıştır, ancak derleme sonuçlarını daha sonra almak üzere bir önbellekte bekletir.  
  
 Sürüm 4,0, bu bellek yönetimini otomatik olarak işler, projeleri ve gibi özellikleri kullanmak zorunda kalmadan  `UnloadProjectsOnCompletion` kaydederek `UseResultsCache` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
