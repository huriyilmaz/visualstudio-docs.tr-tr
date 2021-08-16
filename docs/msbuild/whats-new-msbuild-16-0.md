---
title: 16.0 MSBuild'daki | Microsoft Docs
description: MSBuild 16.0 için değiştirilen ve güncelleştirilmiş özellikler hakkında bilgi alın ve sürüm notlarına bağlantı ekleyin.
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
ms.openlocfilehash: 8cd358fddcc5f7ff0b6fbc27c5b046c2e2ee6ccad2a1c5b5deb693a5e1414066
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397104"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 sürümündeki yenilikler

Bu makalede, MSBuild 16.0'daki güncelleştirilmiş özellikler ve özellikler açıklanmıştır. Ayrıntılı sürüm notları için bkz. [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild her sürümü altındaki *\Current* klasörüne yüklenir Visual Studio yürütülebilir dosyalar *\Bin alt* klasöründedir. Örneğin, *MSBuild.exe* 2019 Visual Studio Community ile yüklenmiş Community'nin yolu *C:\Program Files (x86)\Microsoft Visual* Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe'dır. MSBuild: [vssetup.powershell'i](https://github.com/Microsoft/vssetup.powershell)bulmak için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

## <a name="changed-properties"></a>Değiştirilen özellikler

 Aşağıdaki MSBuild sürüm numarası nedeniyle güncelleştirilmiştir.

- `MSBuildToolsVersion` araçların bu sürümü için "Geçerli" şeklindedir. Derleme sürümü, 15.1.0.0 olan Visual Studio 2017 ile aynıdır.

- `VisualStudioVersion` araçların bu sürümü için "16.0"

## <a name="change-waves"></a>Dalgaları değiştirme

16.8 MSBuild başlayarak, 16.8'de olası kesintiye neden olabilecek bazı değişiklikleri geri MSBuild. Bkz. [Dalgaları değiştirme.](change-waves.md)

## <a name="updates"></a>Güncelleştirmeler

MSBuild (ve Visual Studio) artık .NET Framework 4.7.2’yi hedeflemektedir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
