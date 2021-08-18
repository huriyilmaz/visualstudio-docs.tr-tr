---
title: MSBuild 16,0 ' deki yenilikler | Microsoft Docs
description: MSBuild 16,0 için değiştirilen ve güncelleştirilmiş özellikler ve özellikler hakkında bilgi edinin ve sürüm notlarının bağlantısını inceleyin.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 8c0d085acc2d392c6db156be2bc16743774b60d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093676"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 sürümündeki yenilikler

bu makalede MSBuild 16,0 ' deki güncelleştirilmiş özellikler ve özellikler açıklanmaktadır. ayrıntılı sürüm notları için bkz. [MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, Visual Studio her bir sürümünde *\current* klasörüne yüklenir ve yürütülebilir dosyalar *\bin* klasörüdür. örneğin, Visual Studio 2019 Community ile yüklenen *MSBuild.exe* yolu *C:\Program Files (x86) \microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* ' dir. ayrıca, MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell)' i bulmak için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

## <a name="changed-properties"></a>Değiştirilen özellikler

 yeni sürüm numarası nedeniyle aşağıdaki MSBuild özellikleri güncelleştirildi.

- `MSBuildToolsVersion` araçların bu sürümü için "geçerli" olur. derleme sürümü, 15.1.0.0 olan Visual Studio 2017 ile aynıdır.

- `VisualStudioVersion` araçların bu sürümü için "16,0"

## <a name="change-waves"></a>Dalgaları değiştirme

MSBuild 16,8 ' den başlayarak, MSBuild ' de belirli olabilecek ciddi değişikliklerden vazgeçmek isteyip istemediğinizi seçerek seçebilirsiniz. Bkz. [dalgaları değiştirme](change-waves.md).

## <a name="updates"></a>Güncelleştirmeler

MSBuild (ve Visual Studio) artık .NET Framework 4.7.2’yi hedeflemektedir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
