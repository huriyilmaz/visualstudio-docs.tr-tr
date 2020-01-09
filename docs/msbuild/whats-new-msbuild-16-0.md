---
title: "&#39;MSBuild 16,0 ' deki yenilikler | Microsoft Docs"
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 3e6ecfc1c08f30eb0232f230d955967d95bc32ee
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566975"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16,0 ' deki yenilikler

Bu makalede, MSBuild 16,0 ' deki güncelleştirilmiş özellikler ve özellikler açıklanmaktadır. Ayrıntılı sürüm notları (yalnızca taslak) için bkz. [MSBuild 16,0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, Visual Studio 'nun her bir sürümünde *\Current* klasörüne yüklenir. Örneğin, *C:\Program Files (x86) \Microsoft Visual Studio\Current\Enterprise\MSBuild*. MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell)' i bulmak Için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

## <a name="changed-properties"></a>Değiştirilen özellikler

 Yeni sürüm numarası nedeniyle aşağıdaki MSBuild özellikleri güncelleştirildi.

- araçların bu sürümü için `MSBuildToolsVersion` "geçerli". Derleme sürümü, 15.1.0.0 olan Visual Studio 2017 ile aynıdır.

- araçların bu sürümü için `VisualStudioVersion` "16,0"

## <a name="updates"></a>Güncelleştirmeler

MSBuild (ve Visual Studio) artık .NET Framework 4.7.2’yi hedeflemektedir. Yeni MSBuild API özelliklerini kullanmak istiyorsanız bütünleştirilmiş kodunuz da yükseltilmelidir, ancak mevcut kod çalışmaya devam eder.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild](../msbuild/msbuild.md)
