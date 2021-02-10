---
title: "&apos;MSBuild 16,0 ' deki yenilikler | Microsoft Docs"
description: MSBuild 16,0 için değiştirilen ve güncelleştirilmiş özellikler ve Özellikler ve sürüm notlarına bağlantı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 24b106442456f8bfbd415c4559cba71e463418d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933797"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 sürümündeki yenilikler

Bu makalede, MSBuild 16,0 ' deki güncelleştirilmiş özellikler ve özellikler açıklanmaktadır. Ayrıntılı sürüm notları için bkz. [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, Visual Studio 'nun her bir sürümünde *\Current* klasörüne yüklenir ve yürütülebilir dosyalar *\Bin* klasörüdür. Örneğin, Visual Studio 2019 Community ile yüklenen *MSBuild.exe* yolu *C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* ' dir. Ayrıca, MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell)' i bulmak için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

## <a name="changed-properties"></a>Değiştirilen özellikler

 Yeni sürüm numarası nedeniyle aşağıdaki MSBuild özellikleri güncelleştirildi.

- `MSBuildToolsVersion` araçların bu sürümü için "geçerli" olur. Derleme sürümü, 15.1.0.0 olan Visual Studio 2017 ile aynıdır.

- `VisualStudioVersion` araçların bu sürümü için "16,0"

## <a name="change-waves"></a>Dalgaları değiştirme

MSBuild 16,8 ' den itibaren, MSBuild 'te belirli olabilecek ciddi değişikliklerden vazgeçmek isteyip istemediğinizi seçerek seçebilirsiniz. Bkz. [dalgaları değiştirme](change-waves.md).

## <a name="updates"></a>Güncelleştirmeler

MSBuild (ve Visual Studio) artık .NET Framework 4.7.2’yi hedeflemektedir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
