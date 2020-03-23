---
title: MSBuild .targets Dosyalar | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633362"
---
# <a name="msbuild-targets-files"></a>MSBuild .targets dosyaları

MSBuild, sık karşılaşılan senaryolar için öğeler, özellikler, hedefler ve görevler içeren birkaç *.hedef* dosyası içerir. Bu dosyalar, bakım ve okunabilirliği basitleştirmek için otomatik olarak çoğu Visual Studio proje dosyasına aktarılır.

 Projeler genellikle yapı işlemini tanımlamak için bir veya daha fazla *.hedef* dosyasını içe aktarın. Örneğin Visual Studio tarafından oluşturulan bir C# *projesi, Microsoft.Common.targets'ı*içe aktaran *Microsoft.CSharp.targets'ı* içe aktarır. C# projesinin kendisi, bu projeye özgü öğeleri ve özellikleri tanımlar, ancak c# projesinin standart yapı kuralları içe aktarılan *.targets* dosyalarında tanımlanır.

 Değer, `$(MSBuildToolsPath)` bu ortak *.hedef* dosyalarının yolunu belirtir. 4.0 `ToolsVersion` ise, dosyalar aşağıdaki konumdadır: * \<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\ *

> [!NOTE]
> Kendi hedeflerinizi nasıl oluşturabilirsiniz hakkında bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md) Proje dosyasını başka `Import` bir proje dosyasına eklemek için öğenin nasıl kullanılacağı hakkında bilgi için alma [öğesi (MSBuild)](../msbuild/import-element-msbuild.md) ve [Nasıl Yapılır'a bakın: Aynı hedefi birden çok proje dosyasında kullanın.](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)

## <a name="common-targets-files"></a>Ortak .hedefler dosyaları

| *.targets* dosyası | Açıklama |
|---------------------------------| - |
| *Targets* | Visual Basic ve C# projeleri için standart yapı işlemindeki adımları tanımlar.<br /><br /> *Microsoft.CSharp.targets* ve *Microsoft.VisualBasic.targets* dosyaları tarafından alınan aşağıdaki deyimi içerir:`<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.hedefleri* | Visual C# projeleri için standart yapı işlemindeki adımları tanımlar.<br /><br /> Visual C# proje dosyaları (*.csproj)* tarafından içe aktarılan ve aşağıdaki ifadeyi içeren:`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Visual Basic projeleri için standart yapı işlemindeki adımları tanımlar.<br /><br /> Visual Basic proje dosyaları (*.vbproj)* tarafından içe aktarılan ve aşağıdaki ifadeyi içeren:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Dizin.Build.targets

*Directory.Build.targets,* bir dizin altındaki projelere özelleştirmeler sağlayan kullanıcı tanımlı bir dosyadır. Bu dosya, **importDirectoryBuildTargets** özelliği **yanlış**olarak ayarlıdeğilse *Microsoft.Common.targets'dan* otomatik olarak alınır. Daha fazla bilgi için [yapınızı özelleştirin.](customize-your-build.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Alma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
