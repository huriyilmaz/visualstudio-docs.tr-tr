---
title: SGen Görev | Microsoft Docs
description: XML Seri MSBuild aracı sarmalama ve türleri için xml serileştirme derlemesi oluşturmak için SGen görevini nasıl Sgen.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c90e98ae3164c6f975ba5c960c7eb9e6e03e350b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136657"
---
# <a name="sgen-task"></a>SGen görevi

Belirtilen derlemede türler için bir XML serileştirme derlemesi oluşturur. Bu görev XML Seri Hale Getirici Oluşturucu aracını sarmalar (*Sgen.exe*). Daha fazla bilgi için [bkz. XML Seri Hale Getirici Oluşturucu aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `SGen` almaktadır.

| Parametre | Açıklama |
|-----------------------------| - |
| `BuildAssemblyName` | Gerekli `String` parametre.<br /><br /> Serileştirme kodu oluşturmak için derleme. |
| `BuildAssemblyPath` | Gerekli `String` parametre.<br /><br /> Serileştirme kodu oluşturmak için derlemenin yolu. |
| `DelaySign` | İsteğe `Boolean` bağlı parametre.<br /><br /> `true`ise, ortak anahtarı yalnızca derlemeye yer almak istediğiniz belirtir. ise, `false` tam olarak imzalanmış bir derleme istediğiniz belirtir.<br /><br /> veya parametresiyle kullanılmadıkça bu parametrenin `KeyFile` hiçbir etkisi `KeyContainer` olmaz. |
| `KeyContainer` | İsteğe `String` bağlı parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine bir ortak anahtar ekerek derlemeyi imzalar. Görev daha sonra özel anahtarla son derlemeyi imzalar. |
| `KeyFile` | İsteğe `String` bağlı parametre.<br /><br /> Bir derlemeyi imzalamak için bir anahtar çifti veya bir ortak anahtar belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. |
| `Platform` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış derlemesi oluşturmak için kullanılan Derleyici Platformunu alır veya ayarlar. Bu parametre , veya `x86` `x64` değerine sahip `anycpu` olabilir. `anycpu` varsayılan değerdir. |
| `References` | İsteğe `String[]` bağlı parametre.<br /><br /> XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. |
| `SdkToolsPath` | İsteğe `String` bağlı parametre.<br /><br /> SDK araçlarının yolunu belirtir, örneğin *resgen.exe.* |
| `SerializationAssembly` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Oluşturulan serileştirme derlemesi içerir. |
| `SerializationAssemblyName` | İsteğe `String` bağlı parametre.<br /><br /> Oluşturulan serileştirme derlemenin adını belirtir. |
| `ShouldGenerateSerializer` | Gerekli `Boolean` parametre.<br /><br /> ise, `true` SGen görevi bir serileştirme derlemesi oluşturması gerekir. |
| `Timeout` | İsteğe `Int32` bağlı parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılma süresini milisaniye cinsinden belirtir. Varsayılan değer, `Int.MaxValue` zaman dışında nokta olmadığını gösteren değeridir. |
| `ToolPath` | İsteğe `String` bağlı parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı yükley olduğu konumu belirtir (*sgen.exe).* Bu parametre belirtilmezse, görev çalışan çerçevenin sürümüne karşılık gelen SDK yükleme yolunu MSBuild. |
| `Types` | İsteğe `String[]` bağlı parametre.<br /><br /> Serileştirme kodu oluşturmak için belirli Türler listesini alır veya ayarlar. SGen yalnızca bu türler için serileştirme kodu üretir. |
| `UseProxyTypes` | Gerekli `Boolean` parametre.<br /><br /> ise, `true` SGen görevi yalnızca XML Web hizmeti proxy türleri için serileştirme kodu üretir. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
