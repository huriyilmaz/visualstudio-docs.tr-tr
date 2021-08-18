---
title: MSBuild .targets Files | Microsoft Docs
description: Yaygın senaryolar MSBuild, özellikler, hedefler ve görevler içeren .targets dosyaları hakkında bilgi edinmek için.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b30aaf73a49c1ef75f0778e619cbfb4a4b69846d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093637"
---
# <a name="msbuild-targets-files"></a>MSBuild .targets dosyaları

MSBuild *senaryolar için öğeleri,* özellikleri, hedefleri ve görevleri içeren birkaç .targets dosyası içerir. Bu dosyalar bakım ve okunabilirliği basitleştirmek Visual Studio proje dosyalarının çoğuna otomatik olarak aktarılır.

 Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *.targets* dosyası içeri aktarıyor. Örneğin, Visual Studio tarafından oluşturulan bir C# projesi *Microsoft.Common.targets'i içeri aktaran Microsoft.CSharp.targets'i* *içeri aktaracak.* C# projesi, o projeye özgü öğeleri ve özellikleri tanımlar, ancak bir C# projesinin standart derleme kuralları, içe aktarılan *.targets dosyalarında* tanımlanır.

 değeri, `$(MSBuildToolsPath)` bu ortak *.targets dosyalarının yolunu* belirtir. `ToolsVersion`4.0 ise, dosyalar şu konumdadır: *\<WindowsInstallationPath> \Microsoft.NET\Framework\v4.0.30319 \\*

> [!NOTE]
> Kendi hedeflerinizi oluşturma hakkında bilgi için bkz. [Hedefler.](../msbuild/msbuild-targets.md) öğesini kullanarak başka bir proje dosyasına proje dosyası ekleme hakkında bilgi için bkz. Import `Import` [element (MSBuild)](../msbuild/import-element-msbuild.md) and [How to: Use](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)same target in multiple project files .

## <a name="common-targets-files"></a>Ortak .targets dosyaları

| *.targets* dosyası | Açıklama |
|---------------------------------| - |
| *Targets* | Visual Basic ve C# projeleri için standart derleme işlemi adımlarını tanımlar.<br /><br /> Aşağıdaki deyimi içeren *Microsoft.CSharp.targets* ve *Microsoft.VisualBasic.targets* dosyaları tarafından içe aktarıldı: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Visual C# projeleri için standart derleme işlemi adımlarını tanımlar.<br /><br /> Aşağıdaki deyimi içeren Visual C# proje dosyaları (*.csproj*) tarafından içe aktarıldı: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Projelerin standart derleme sürecindeki adımları Visual Basic tanımlar.<br /><br /> Aşağıdaki deyimi Visual Basic proje dosyaları (*.vbproj*) tarafından içe aktarıldı:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets,* bir dizin altındaki projelere özelleştirmeler sağlayan kullanıcı tanımlı bir dosyadır. **ImportDirectoryBuildTargets** özelliği false olarak ayarlanmadıkça bu dosya *Microsoft.Common.targets'tan* otomatik olarak içeri **aktarılır.** Daha fazla bilgi için [derlemenizi özelleştirme.](customize-your-build.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Import öğesi (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
