---
title: Ortak MSBuild öğe meta verileri | Microsoft Docs
description: Bazı MSBuild SDK 'Ları veya hedefleri için anlamı olan, ancak her öğe için varsayılan olarak ayarlanmayan isteğe bağlı öğe meta verileri hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 152967fb99442b58d96016e10d8899b57ef35bf6
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796596"
---
# <a name="common-msbuild-item-metadata"></a>Yaygın MSBuild öğesi meta verileri

Aşağıdaki tabloda bazı MSBuild SDK 'Ları veya hedefleri için anlamı olan, ancak her öğe için varsayılan olarak ayarlanmamış olan isteğe bağlı öğe meta verileri açıklanmaktadır. Bunları, yalnızca kullandığınız SDK veya hedef dosyalar tarafından tanınıyorsa, derleme davranışını etkiler olarak ayarlayabilirsiniz.

| Öğe meta verileri | SDK’lar | Açıklama |
|---------------| ------- | -------------|
|% (Bağlantı)| Tümü |Visual Studio proje sistemi, `Link` Proje ağacında neyin gösterildiklerinizi değiştirmek için meta verileri (varsa) kullanır; **Çözüm Gezgini** bir dosyayı farklı bir mantıksal klasör yapısına koyabilirsiniz.<br />Buna ek olarak, `AssignTargetPath` görev, `Link` kopyalanmış öğelerden biri ise, bir dosyanın kopyalanacağı çıkış dizininde konumunu tespit etmek için ' a bakar.|
|% (Bağlantı tabanı)| .NET Core SDK | Öğe grupları için meta veriler için kullanılacak klasörü ayarlamak için kullanılır `Link` . |

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
- [Yaygın MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md)
- [MSBuild tanınmış öğe meta verileri](msbuild-well-known-item-metadata.md)