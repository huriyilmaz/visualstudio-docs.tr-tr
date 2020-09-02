---
title: SGen görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3be3aa5426c2d1283b8b4cded51cc9c2772642ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682097"
---
# <a name="sgen-task"></a>SGen Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen derlemedeki türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur. Bu görev XML Serileştiricisi Oluşturma Aracı (Sgen.exe) sarmalanmış. Daha fazla bilgi için bkz. [XML serileştiricisi oluşturma aracı (Sgen.exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `SGen` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BuildAssemblyName`|Gerekli `String` parametre.<br /><br /> İçin serileştirme kodu oluşturulacak derleme.|  
|`BuildAssemblyPath`|Gerekli `String` parametre.<br /><br /> İçin serileştirme kodu oluşturulacak derlemenin yolu.|  
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , tam olarak imzalanan bir derleme istediğinizi belirtir. `false`Yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtir.<br /><br /> Ya da parametresiyle kullanılmamışsa, bu parametrenin hiçbir etkisi `KeyFile` yoktur `KeyContainer` .|  
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalayacaktır. Görev daha sonra son derlemeyi özel anahtarla imzalayacaktır.|  
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Bir derlemeyi imzalamak için kullanılacak bir anahtar çifti veya ortak anahtar belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.|  
|`Platform`|İsteğe bağlı `String` parametre.<br /><br /> Çıktı derlemesini oluşturmak için kullanılan derleyici platformunu alır veya ayarlar. Bu parametre,, veya değerine sahip `x86` olabilir `x64` `anycpu` . `anycpu` varsayılan değerdir.|  
|`References`|İsteğe bağlı `String[]` parametre.<br /><br /> XML serileştirme gerektiren türleri tarafından başvurulan bir derleme belirtir.|  
|`SdkToolsPath`|İsteğe bağlı `String` parametre.<br /><br /> resgen.exe gibi SDK araçlarının yolunu belirtir.|  
|`SerializationAssembly`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Oluşturulan serileştirme derlemesini içerir.|  
|`SerializationAssemblyName`|İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan serileştirme derlemesinin adını belirtir.|  
|`ShouldGenerateSerializer`|Gerekli `Boolean` parametre.<br /><br /> İse `true` , SGen görevinin bir serileştirme derlemesi oluşturması gerekir.|  
|`Timeout`|İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir.|  
|`ToolPath`|İsteğe bağlı `String` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (sgen.exe) yükleyecek konumu belirtir. Bu parametre belirtilmezse, görev, çalıştıran çerçevenin sürümüne karşılık gelen SDK yükleme yolunu kullanır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`Types`|İsteğe bağlı `String[]` parametre.<br /><br /> İçin serileştirme kodu oluşturmak üzere belirli türlerin bir listesini alır veya ayarlar. SGen yalnızca bu türler için serileştirme kodu oluşturur.|  
|`UseProxyTypes`|Gerekli `Boolean` parametre.<br /><br /> İse `true` , SGen görevi yalnızca XML Web hizmeti proxy türleri için serileştirme kodu oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)
