---
title: MSBuild 16.0'da yeni&#39;| Microsoft Dokümanlar
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652813"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0'daki yenilikler

Bu makalede, MSBuild 16.0'da güncelleştirilmiş özellikler ve özellikler açıklanmaktadır. Ayrıntılı sürüm notları için [MSBuild 16.0'a](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)bakın.

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild Visual Studio'nun her sürümü altında *\Current* klasörüne yüklenir ve yürütülebilir ler *\Bin* alt klasöründedir. Örneğin, Visual Studio 2019 Topluluğu ile yüklenen *MSBuild.exe* yolu *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* Ayrıca MSBuild bulmak için aşağıdaki PowerShell modülü kullanabilirsiniz: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Değiştirilen özellikler

 Aşağıdaki MSBuild özellikleri yeni sürüm numarası nedeniyle güncelleştirildi.

- `MSBuildToolsVersion`araçların bu sürümü için "Geçerli". Montaj sürümü Visual Studio 2017 ile aynıdır, bu da 15.1.0.0'dır.

- `VisualStudioVersion`araçların bu sürümü için "16.0"

## <a name="updates"></a>Güncelleştirmeler

MSBuild (ve Visual Studio) artık .NET Framework 4.7.2’yi hedeflemektedir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="see-also"></a>Ayrıca bkz.

- [Msbuild](../msbuild/msbuild.md)
