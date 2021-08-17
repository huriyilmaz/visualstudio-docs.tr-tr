---
title: Büyük projeleri derlemek için belleği verimli bir şekilde | Microsoft Docs
description: Büyük MSBuild eski sürümleri kaldırma ve önbellekleri alma gibi belleği otomatik olarak nasıl yöneteceklerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 18e1cf21168a25bdc25ba0556ef62aa681fc0ad001b4c448631fe637d03cc7c8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369494"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Büyük projeler derlemek için belleği verimli bir şekilde kullanma

Büyük projeler genellikle birçok alt proje ve diğer bağımlılıklar içerir ve bu da derleme zamanında çok fazla sistem belleği tüketir. Kullanılabilir sistem belleği azaldığı zaman sistem performansı da düşebilir. MSBuild projelerinin eski sürümleri bellekte kaldı. Sürüm 3.5, projelerin eski sürümlerini kaldırdı, ancak daha sonra almak için önbellekte derleme sonuçları bulundu.

 Sürüm 4.0, bu bellek yönetimini otomatik olarak işler ve gibi özellikleri kullanmak zorunda kalmadan  `UnloadProjectsOnCompletion` projelerin tasarruf `UseResultsCache` eder.

### <a name="see-also"></a>Ayrıca bkz.

- [Birden çok proje paralel olarak derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
