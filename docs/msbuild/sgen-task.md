---
title: SGen görevi | Microsoft Docs
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
ms.openlocfilehash: a97133892926e60adc1d9f0165415868732066ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595130"
---
# <a name="sgen-task"></a>SGen görevi
Belirtilen derlemedeki türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur. Bu görev, XML serileştirici Oluşturucu aracı 'nı (*SGen. exe*) sarmalanmış. Daha fazla bilgi için bkz. [XML serileştirici Oluşturucu aracı (SGen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `SGen` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|-----------------------------| - |
| `BuildAssemblyName` | Gerekli `String` parametresi.<br /><br /> İçin serileştirme kodu oluşturulacak derleme. |
| `BuildAssemblyPath` | Gerekli `String` parametresi.<br /><br /> İçin serileştirme kodu oluşturulacak derlemenin yolu. |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, yalnızca ortak anahtarı derlemeye koymak istediğinizi belirtir. `false`, tam olarak imzalanan bir derleme istediğinizi belirtir.<br /><br /> `KeyFile` veya `KeyContainer` parametresiyle kullanılmamışsa bu parametrenin hiçbir etkisi yoktur. |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalayacaktır. Görev daha sonra son derlemeyi özel anahtarla imzalayacaktır. |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Bir derlemeyi imzalamak için kullanılacak bir anahtar çifti veya ortak anahtar belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı derlemesini oluşturmak için kullanılan derleyici platformunu alır veya ayarlar. Bu parametre `x86`, `x64`veya `anycpu`değerine sahip olabilir. Varsayılan değer `anycpu`. |
| `References` | İsteğe bağlı `String[]` parametresi.<br /><br /> XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametresi.<br /><br /> *Resgen. exe*gibi SDK araçlarının yolunu belirtir. |
| `SerializationAssembly` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Oluşturulan serileştirme derlemesini içerir. |
| `SerializationAssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan serileştirme derlemesinin adını belirtir. |
| `ShouldGenerateSerializer` | Gerekli `Boolean` parametresi.<br /><br /> `true`, SGen görevinin bir serileştirme derlemesi oluşturması gerekir. |
| `Timeout` | İsteğe bağlı `Int32` parametresi.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer, zaman aşımı süresi olmadığını belirten `Int.MaxValue`. |
| `ToolPath` | İsteğe bağlı `String` parametresi.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (*SGen. exe*) yükleneceği konumu belirtir. Bu parametre belirtilmezse, görev, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Types` | İsteğe bağlı `String[]` parametresi.<br /><br /> İçin serileştirme kodu oluşturmak üzere belirli türlerin bir listesini alır veya ayarlar. SGen yalnızca bu türler için serileştirme kodu oluşturur. |
| `UseProxyTypes` | Gerekli `Boolean` parametresi.<br /><br /> `true`, SGen görevi yalnızca XML Web hizmeti proxy türleri için serileştirme kodu oluşturur. |

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
