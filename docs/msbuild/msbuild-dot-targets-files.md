---
title: MSBuild. targets dosyaları | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633362"
---
# <a name="msbuild-targets-files"></a>MSBuild. targets dosyaları

MSBuild, yaygın senaryolar için öğeleri, özellikleri, hedefleri ve görevleri içeren birkaç *. targets* dosyası içerir. Bu dosyalar, bakım ve okunabilirlik basitleşmesi için Visual Studio proje dosyalarına otomatik olarak aktarılır.

 Projeler genellikle derleme işlemlerini tanımlamak için bir veya daha fazla *. targets* dosyasını içeri aktarır. Örneğin, Visual C# Studio tarafından oluşturulan bir proje *Microsoft. Common. targets*'ı Içeri aktaran *Microsoft. CSharp. targets* içeri aktarır. C# Projenin kendisi bu projeye özgü öğeleri ve özellikleri tanımlar, ancak C# projenin standart yapı kuralları içeri aktarılan *. targets* dosyalarında tanımlanır.

 `$(MSBuildToolsPath)` değeri, bu ortak *. targets* dosyalarının yolunu belirtir. `ToolsVersion` 4,0 ise, dosyalar şu konumdadır: *\<Windowsınstallationpath > \Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Kendi hedeflerinizi oluşturma hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md). Proje dosyasını başka bir proje dosyasına eklemek için `Import` öğesinin nasıl kullanılacağı hakkında bilgi için, bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md) ve [nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Ortak. targets dosyaları

| *. targets* dosyası | Açıklama |
|---------------------------------| - |
| *Microsoft. Common. targets* | Visual Basic ve C# projeleri için standart derleme işlemindeki adımları tanımlar.<br /><br /> Aşağıdaki ifadeyi içeren *Microsoft. CSharp. targets* ve *Microsoft. VisualBasic. targets* dosyaları tarafından içeri aktarılır: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft. CSharp. targets* | Görsel C# projeler için standart derleme işlemindeki adımları tanımlar.<br /><br /> Aşağıdaki ifadeyi içeren C# görsel proje dosyaları ( *. csproj*) tarafından içeri aktarıldı: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft. VisualBasic. targets* | Visual Basic projeleri için standart derleme işlemindeki adımları tanımlar.<br /><br /> Aşağıdaki ifadeyi içeren Visual Basic proje dosyaları ( *. vbproj*) tarafından içeri aktarıldı: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory. Build. targets

*Directory. Build. targets* , bir dizin altındaki projelere özelleştirmeler sağlayan Kullanıcı tanımlı bir dosyadır. **Importdirectorybuildtargets** özelliği **false**olarak ayarlanmadığı takdirde bu dosya *Microsoft. Common. targets* öğesinden otomatik olarak içeri aktarılır. Daha fazla bilgi için [yapınızı özelleştirin](customize-your-build.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
