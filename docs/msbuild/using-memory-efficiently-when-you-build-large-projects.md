---
title: Büyük projeler oluşturduğunuzda belleği verimli bir şekilde kullanma | Microsoft Docs
description: Büyük projeler oluştururken MSBuild 'in belleği otomatik olarak nasıl yönettiğini (eski sürümleri kaldırma ve önbellekleri alma gibi) öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 99cee9cfbf779bbee97c00fb76f9670e1d609b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965908"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Büyük projeler oluşturduğunuzda belleği verimli bir şekilde kullanın

Büyük projeler genellikle birçok alt projeyi ve derleme zamanında çok fazla sistem belleği tüketen diğer bağımlılıkları içerir. Kullanılabilir sistem belleği azaltıldı, sistem performansı da azalabilir. MSBuild projelerinin daha eski sürümleri bellekte kaldı. Sürüm 3,5, projelerin eski sürümlerini kaldırdı, ancak derleme sonuçlarını daha sonra almak üzere bir önbellekte bekletir.

 Sürüm 4,0, bu bellek yönetimini otomatik olarak işler, projeleri ve gibi özellikleri kullanmak zorunda kalmadan  `UnloadProjectsOnCompletion` kaydederek `UseResultsCache` .

### <a name="see-also"></a>Ayrıca bkz.

- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
