---
title: UsingTask Öğesi (MSBuild) | Microsoft Docs
description: Bir görev MSBuild başvurulan görevi, görev uygulamasını içeren derlemeye eşleen usingTask öğesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5b382711223b61999a199fe7e926ecedc12fb5ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136605"
---
# <a name="usingtask-element-msbuild"></a>UsingTask öğesi (MSBuild)

Haritalar öğesinde başvurulan [görevi, görev](../msbuild/task-element-msbuild.md) uygulamasını içeren derlemeye geri gönderme.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntax

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Özelliklerden ve öğelerden *farklı olarak,* öğesine uygulanan ilk öğe kullanılır; görevleri geçersiz kılmak için mevcut öğeden `UsingTask` önce yeni `TaskName` `UsingTask` *bir* tanımlamanız gerekir.

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Architecture`|İsteğe bağlı öznitelik.<br /><br /> Görevin belirtilen bitlik sürecinde çalışması gerektiğini belirtir. Geçerli işlem gereksinimi karşılamıyorsa, görev bunu yapar bir görev konak işlemi içinde çalıştır.<br /><br /> Desteklenen değerler `x86` (32 bit), `x64` (64 bit), `CurrentArchitecture` ve (herhangi bir `*` mimari) değerleridir.|  
|`AssemblyName`|özniteliği `AssemblyName` veya `AssemblyFile` özniteliği gereklidir.<br /><br /> Yüklenecek derlemenin adı. özniteliği, `AssemblyName` güçlü adlandırma gerekli değildir ancak güçlü adlandırılmış derlemeleri kabul eder. Bu özniteliğin kullanımı, .NET'te yöntemini kullanarak bir <xref:System.Reflection.Assembly.Load%2A> derlemeyi yüklemeye eşdeğerdir.<br /><br /> Öznitelik kullanılıyorsa bu özniteliği `AssemblyFile` kullanılamaz.|
|`AssemblyFile`|veya `AssemblyName` özniteliği `AssemblyFile` gereklidir.<br /><br /> Derlemenin dosya yolu. Bu öznitelik tam yolları veya göreli yolları kabul eder. Göreli yollar, proje dosyasının dizinine veya öğesinin bildir olduğu `UsingTask` hedefler dosyasına göredir. Bu özniteliğin kullanımı, .NET'te yöntemini kullanarak bir <xref:System.Reflection.Assembly.LoadFrom%2A> derlemeyi yüklemeye eşdeğerdir.<br /><br /> Öznitelik kullanılıyorsa bu özniteliği `AssemblyName` kullanılamaz.|
|`Runtime`|İsteğe bağlı öznitelik.<br /><br /> Görevin belirtilen sürümün çalışma zamanında .NET Framework gerektiğini belirtir. Geçerli işlem gereksinimi karşılamıyorsa, görev bunu yapar bir görev konak işlemi içinde çalıştır. .NET Core'da MSBuild.<br /><br /> Desteklenen değerler `CLR2` (.NET Framework 3.5), `CLR4` (.NET Framework 4.7.2 veya daha yüksek), `CurrentRuntime` ve (herhangi bir `*` çalışma zamanı).|  
|`TaskFactory`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen adın örneklerini oluşturmakla sorumlu derlemede sınıfını `Task` belirtir.  Kullanıcı, görev fabrikasının `Task` görevi oluşturmak için aldığı ve kullandığı bir alt öğe olarak da belirtebilirsiniz. içeriğinin, `Task` görev fabrikasına özgü olduğu.|
|`TaskName`|Gerekli öznitelik.<br /><br /> Bir derlemeden başvurulecek görevin adı. Belirsizlikler mümkünse, bu öznitelik her zaman tam ad alanlarını belirtmektedir. Belirsizlikler varsa, MSBuild rastgele bir eşleşme seçer ve bu da beklenmeyen sonuçlar üretebilir.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Belirtilen tarafından oluşturulan görev üzerinde görünen parametre `TaskFactory` kümesi.|
|[Görev](../msbuild/task-element-msbuild.md)|Görevin bir örneğini oluşturmak `TaskFactory` için 'e geçirilen veriler.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Bir proje dosyasının gerekli MSBuild öğesi. |

## <a name="remarks"></a>Açıklamalar

 Ortam değişkenleri, komut satırı özellikleri, proje düzeyi özellikleri ve proje düzeyi öğelerine doğrudan veya içe aktarılan bir proje dosyası aracılığıyla proje dosyasına dahil edilen `UsingTask` öğelere başvurabilirsiniz. Daha fazla bilgi için bkz. [Görevler.](../msbuild/msbuild-tasks.md)

> [!NOTE]
> Project altyapıyla genel olarak kaydedilen .MSBuild tasks dosyalarından biri geliyorsa, öğenin bir anlamı `UsingTask` yoktur.  Project düzeyi değerler, verilerle genel MSBuild.

 Bu MSBuild 4.0'da, *.overridetask* dosyalarından görevler yüklenebilir.

Özel görevi içeren derleme, ilk kez `Task` kullanılırken yüklenir.

## <a name="example-1"></a>Örnek 1

 Aşağıdaki örnek, öğesinin bir `UsingTask` özniteliğiyle nasıl kullanıla bir `AssemblyName` gösterir.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example-2"></a>Örnek 2

 Aşağıdaki örnek, öğesinin bir `UsingTask` özniteliğiyle nasıl kullanıla bir `AssemblyFile` gösterir.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Nasıl yapılandırılır: Hedefleri ve görevleri yapılandırma](../msbuild/how-to-configure-targets-and-tasks.md)   
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
