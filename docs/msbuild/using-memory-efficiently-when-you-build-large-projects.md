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
ms.openlocfilehash: af61c15c8ef65c062c1aab6eba079c613f99b5f8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595238"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Büyük projeler oluşturduğunuzda belleği verimli bir şekilde kullanın
Büyük projeler genellikle birçok alt projeyi ve derleme zamanında çok fazla sistem belleği tüketen diğer bağımlılıkları içerir. Kullanılabilir sistem belleği azaltıldı, sistem performansı da azalabilir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projelerinin daha eski sürümleri bellekte kaldı. Sürüm 3,5, projelerin eski sürümlerini kaldırdı, ancak derleme sonuçlarını daha sonra almak üzere bir önbellekte bekletir.

 Sürüm 4,0, bu bellek yönetimini otomatik olarak işler, projeleri `UnloadProjectsOnCompletion` ve `UseResultsCache`gibi özellikleri kullanmak zorunda kalmadan kaydederek yönetir.

### <a name="see-also"></a>Ayrıca bkz.
- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
