---
title: MSBuild 16.0 |'daki | Microsoft Docs
description: MSBuild 16.0 için değiştirilen ve güncelleştirilmiş özellikler hakkında bilgi alın ve sürüm notlarına bağlantı ekleyin.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: cdfb552c53a40b6ad2f2349556396475926900be
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848259"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 sürümündeki yenilikler

Bu makalede MSBuild 16.0'daki güncelleştirilmiş özellikler ve özellikler açıklanmıştır. Ayrıntılı sürüm notları için bkz. [ MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, her bir Visual Studio sürümü altındaki *\Current* klasörüne yüklenir ve yürütülebilir dosyalar *\Bin alt* klasöründe bulunur. Örneğin, *MSBuild.exe* 2019 Community ile yüklenmiş Visual Studio yolu *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* MSBuild: [vssetup.powershell'i](https://github.com/Microsoft/vssetup.powershell)bulmak için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

## <a name="changed-properties"></a>Değiştirilen özellikler

 Aşağıdaki MSBuild özellikleri yeni sürüm numarası nedeniyle güncelleştirildi.

- `MSBuildToolsVersion` araçların bu sürümü için "Geçerli" şeklindedir. Derleme sürümü, 15.1.0.0 olan Visual Studio 2017 ile aynıdır.

- `VisualStudioVersion` araçların bu sürümü için "16.0"

## <a name="change-waves"></a>Dalgaları değiştirme

MSBuild 16.8'den başlayarak, MSBuild'de bazı olası kesintiye neden olabilecek değişiklikleri geri almayı seçerek seçebilirsiniz. Bkz. [Dalgaları değiştirme.](change-waves.md)

## <a name="updates"></a>Güncelleştirmeler

MSBuild (ve Visual Studio) artık .NET Framework 4.7.2’yi hedeflemektedir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
