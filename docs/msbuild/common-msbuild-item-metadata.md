---
title: ortak MSBuild öğesi meta verileri | Microsoft Docs
description: bazı MSBuild sdk 'ları veya hedefleri için anlamlı olan, ancak her öğe için varsayılan olarak ayarlanmayan isteğe bağlı öğe meta verileri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f4a893a516d8c9237e2dd4ebf06812fcbcd02de9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055099"
---
# <a name="common-msbuild-item-metadata"></a>Yaygın MSBuild öğesi meta verileri

aşağıdaki tabloda bazı MSBuild sdk 'ları veya hedefleri için anlamı olan, ancak her öğe için varsayılan olarak ayarlanmamış olan isteğe bağlı öğe meta verileri açıklanmaktadır. Bunları, yalnızca kullandığınız SDK veya hedef dosyalar tarafından tanınıyorsa, derleme davranışını etkiler olarak ayarlayabilirsiniz.

| Öğe meta verileri | SDK | Açıklama |
|---------------| ------- | -------------|
|% (Bağlantı)| Tümü |Visual Studio proje sistemi, `Link` proje ağacında neyin gösterdiklerinizi değiştirmek için meta verileri (varsa) kullanır; **Çözüm Gezgini** bir dosyayı farklı bir mantıksal klasör yapısına koyabilirsiniz.<br />Buna ek olarak, `AssignTargetPath` görev, `Link` kopyalanmış öğelerden biri ise, bir dosyanın kopyalanacağı çıkış dizininde konumunu tespit etmek için ' a bakar.|
|% (Bağlantı tabanı)| .NET Core SDK | Öğe grupları için meta veriler için kullanılacak klasörü ayarlamak için kullanılır `Link` . |

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [MSBuild tanınmış öğe meta verileri](msbuild-well-known-item-metadata.md)