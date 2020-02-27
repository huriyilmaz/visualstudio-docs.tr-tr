---
title: Büyük projeler oluşturduğunuzda belleği verimli bir şekilde kullanma | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631321"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Büyük projeler oluşturduğunuzda belleği verimli bir şekilde kullanın

Büyük projeler genellikle birçok alt projeyi ve derleme zamanında çok fazla sistem belleği tüketen diğer bağımlılıkları içerir. Kullanılabilir sistem belleği azaltıldı, sistem performansı da azalabilir. MSBuild projelerinin daha eski sürümleri bellekte kaldı. Sürüm 3,5, projelerin eski sürümlerini kaldırdı, ancak derleme sonuçlarını daha sonra almak üzere bir önbellekte bekletir.

 Sürüm 4,0, bu bellek yönetimini otomatik olarak işler, projeleri `UnloadProjectsOnCompletion` ve `UseResultsCache`gibi özellikleri kullanmak zorunda kalmadan kaydederek yönetir.

### <a name="see-also"></a>Ayrıca bkz.

- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
