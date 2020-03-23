---
title: SGen Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: 4305f27435d97c346ce623a21b37f011fd8da0cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632309"
---
# <a name="sgen-task"></a>SGen görevi

Belirtilen derlemedeki türler için bir XML serileştirme derlemesi oluşturur. Bu görev XML Serializer Jeneratör aracını sarar (*Sgen.exe*). Daha fazla bilgi için [Bkz. XML Serializer Generator aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `SGen` açıklanmaktadır.

| Parametre | Açıklama |
|-----------------------------| - |
| `BuildAssemblyName` | Gerekli `String` parametre.<br /><br /> Montaj için serileştirme kodu oluşturmak için. |
| `BuildAssemblyPath` | Gerekli `String` parametre.<br /><br /> Serileştirme kodu oluşturmak için derlemeyolu. |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtirse. Eğer, `false`tam olarak imzalanmış bir derleme istediğinizi belirtir.<br /><br /> Bu parametre, parametre `KeyFile` ile `KeyContainer` kullanılmadığı sürece hiçbir etkisi yoktur. |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme manifestosuna ortak bir anahtar ekleyerek derlemeyi imzalar. Görev daha sonra özel anahtarla son derlemeyi imzalar. |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Bir derlemeyi imzalamak için kullanılacak bir anahtar çifti veya ortak bir anahtar belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı derlemesini oluşturmak için kullanılan Derleyici Platform'u alır veya ayarlar. Bu parametre `x86`, `x64`veya `anycpu`. `anycpu` varsayılan değerdir. |
| `References` | İsteğe bağlı `String[]` parametre.<br /><br /> XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametre.<br /><br /> *Resgen.exe*gibi SDK araçlarına giden yolu belirtir. |
| `SerializationAssembly` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Oluşturulan serileştirme derlemesini içerir. |
| `SerializationAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan serileştirme derlemesinin adını belirtir. |
| `ShouldGenerateSerializer` | Gerekli `Boolean` parametre.<br /><br /> If, `true`SGen görev bir serileştirme derlemesi oluşturmalı. |
| `Timeout` | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir sonlandırıldıktan sonra milisaniye cinsinden süreyi belirtir. Varsayılan `Int.MaxValue`değer, zaman dışında bir dönem olmadığını gösterir. |
| `ToolPath` | İsteğe bağlı `String` parametre.<br /><br /> Görevin temel yürütülebilir dosyayı yükleyeceği konumu belirtir *(sgen.exe).* Bu parametre belirtilmemişse, görev MSBuild çalıştıran çerçevenin sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Types` | İsteğe bağlı `String[]` parametre.<br /><br /> Serileştirme kodu oluşturmak için belirli Türlerin listesini alır veya ayarlar. SGen yalnızca bu türler için serileştirme kodu oluşturur. |
| `UseProxyTypes` | Gerekli `Boolean` parametre.<br /><br /> Eğer `true`, SGen görev yalnızca XML Web hizmeti proxy türleri için serileştirme kodu oluşturur. |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
