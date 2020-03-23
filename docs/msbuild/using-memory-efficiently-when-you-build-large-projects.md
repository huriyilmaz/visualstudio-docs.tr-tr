---
title: Büyük Projeler Oluştururken Belleği Verimli Kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631321"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Büyük projeler oluştururken belleği verimli bir şekilde kullanın

Büyük projeler genellikle birçok alt proje ve diğer bağımlılıklar içerir, bu da yapı zamanında çok sayıda sistem belleği tüketebilir. Kullanılabilir sistem belleği azaltıldığında, sistem performansı da azaltılabilir. MSBuild projelerinin eski sürümleri bellekte kaldı. Sürüm 3.5, projelerin eski sürümlerini kaldırmış, ancak daha sonra alma için bir önbellek oluşturma sonuçları korunmuştur.

 Sürüm 4.0 bu bellek yönetimini otomatik olarak işler ve bu `UnloadProjectsOnCompletion` `UseResultsCache`tür özellikleri kullanmak zorunda projeleri kaydeder.

### <a name="see-also"></a>Ayrıca bkz.

- [Paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
