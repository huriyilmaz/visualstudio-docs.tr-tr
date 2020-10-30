---
title: SGen görevi | Microsoft Docs
description: MSBuild 'in, XML serileştirici Oluşturucu aracı Sgen.exe sarmalayarak türler için bir XML serileştirme derlemesi oluşturmak üzere SGen görevini nasıl kullandığını öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de2437306dba50a1f93b0b94d86af6351b17c0b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048344"
---
# <a name="sgen-task"></a>SGen görevi

Belirtilen derlemedeki türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur. Bu görev, XML serileştirici Oluşturucu aracını ( *Sgen.exe* ) sarmalanmış. Daha fazla bilgi için bkz. [XML serileştirici Oluşturucu aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `SGen` .

| Parametre | Açıklama |
|-----------------------------| - |
| `BuildAssemblyName` | Gerekli `String` parametre.<br /><br /> İçin serileştirme kodu oluşturulacak derleme. |
| `BuildAssemblyPath` | Gerekli `String` parametre.<br /><br /> İçin serileştirme kodu oluşturulacak derlemenin yolu. |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtir. İse `false` , tam olarak imzalanan bir derleme istediğinizi belirtir.<br /><br /> Ya da parametresiyle kullanılmamışsa, bu parametrenin hiçbir etkisi `KeyFile` yoktur `KeyContainer` . |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalayacaktır. Görev daha sonra son derlemeyi özel anahtarla imzalayacaktır. |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Bir derlemeyi imzalamak için kullanılacak bir anahtar çifti veya ortak anahtar belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı derlemesini oluşturmak için kullanılan derleyici platformunu alır veya ayarlar. Bu parametre,, veya değerine sahip `x86` olabilir `x64` `anycpu` . `anycpu` varsayılan değerdir. |
| `References` | İsteğe bağlı `String[]` parametre.<br /><br /> XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametre.<br /><br /> *resgen.exe* gibi SDK araçlarının yolunu belirtir. |
| `SerializationAssembly` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Oluşturulan serileştirme derlemesini içerir. |
| `SerializationAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan serileştirme derlemesinin adını belirtir. |
| `ShouldGenerateSerializer` | Gerekli `Boolean` parametre.<br /><br /> İse `true` , SGen görevinin bir serileştirme derlemesi oluşturması gerekir. |
| `Timeout` | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir. |
| `ToolPath` | İsteğe bağlı `String` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı ( *sgen.exe* ) yükleyecek konumu belirtir. Bu parametre belirtilmezse, görev MSBuild çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Types` | İsteğe bağlı `String[]` parametre.<br /><br /> İçin serileştirme kodu oluşturmak üzere belirli türlerin bir listesini alır veya ayarlar. SGen yalnızca bu türler için serileştirme kodu oluşturur. |
| `UseProxyTypes` | Gerekli `Boolean` parametre.<br /><br /> İse `true` , SGen görevi yalnızca XML Web hizmeti proxy türleri için serileştirme kodu oluşturur. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
