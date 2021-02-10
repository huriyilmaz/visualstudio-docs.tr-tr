---
title: UsingTask öğesi (MSBuild) | Microsoft Docs
description: Bir görev öğesinde başvurulan görevi, görev uygulamasını içeren derleme ile eşleyen MSBuild UsingTask öğesi hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 3adc3d648e73fc1f3596cc7a5c2cb2148a8f611b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960344"
---
# <a name="usingtask-element-msbuild"></a>UsingTask öğesi (MSBuild)

Bir [görev](../msbuild/task-element-msbuild.md) öğesinde başvurulan görevi, görev uygulamasını içeren derlemeye eşler.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntax

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Özellikler ve öğelerin aksine,  `UsingTask` için geçerli olan ilk öğe `TaskName` kullanılacaktır; görevleri geçersiz kılmak için, mevcut bir tane daha önce tanımlamanız gerekir `UsingTask`  .

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Architecture`|İsteğe bağlı öznitelik.<br /><br /> Görevin belirtilen bit durumuyla bir işlemde çalışması gerektiğini belirtir. Geçerli işlem gereksinimi karşılamadığı takdirde, görev bir görev ana bilgisayar işleminde çalıştırılır.<br /><br /> Desteklenen değerler `x86` (32-bit), `x64` (64-bit), `CurrentArchitecture` ve `*` (herhangi bir mimari).|  
|`AssemblyName`|`AssemblyName`Özniteliği ya da `AssemblyFile` özniteliği gereklidir.<br /><br /> Yüklenecek derlemenin adı. Öznitelik, güçlü `AssemblyName` adlandırılmış derlemeleri kabul eder, ancak güçlü adlandırma gerekli değildir. Bu özniteliğin kullanılması, .NET 'teki yöntemi kullanılarak bir derlemeyi yüklemeye eşdeğerdir <xref:System.Reflection.Assembly.Load%2A> .<br /><br /> Özniteliği kullanılırsa bu özniteliği kullanamazsınız `AssemblyFile` .|
|`AssemblyFile`|Ya da `AssemblyName` `AssemblyFile` özniteliği gereklidir.<br /><br /> Derlemenin dosya yolu. Bu öznitelik, tam yolları veya göreli yolları kabul eder. Göreli yollar, öğenin bildirildiği proje dosyasının veya hedef dosyanın dizinine göre belirlenir `UsingTask` . Bu özniteliğin kullanılması, .NET 'teki yöntemi kullanılarak bir derlemeyi yüklemeye eşdeğerdir <xref:System.Reflection.Assembly.LoadFrom%2A> .<br /><br /> Özniteliği kullanılırsa bu özniteliği kullanamazsınız `AssemblyName` .|
|`Runtime`|İsteğe bağlı öznitelik.<br /><br /> Görevin belirtilen sürümün .NET Framework çalışma zamanında çalışması gerektiğini belirtir. Geçerli işlem gereksinimi karşılamadığı takdirde, görev bir görev ana bilgisayar işleminde çalıştırılır. .NET Core MSBuild 'te desteklenmez.<br /><br /> Desteklenen değerler `CLR2` (.NET Framework 3,5), `CLR4` (.NET Framework 4.7.2 veya üzeri), `CurrentRuntime` , ve `*` (herhangi bir çalışma zamanı).|  
|`TaskFactory`|İsteğe bağlı öznitelik.<br /><br /> Derlemede, belirtilen adın örneklerini oluşturmaktan sorumlu sınıfı belirtir `Task` .  Kullanıcı, görev `Task` fabrikasının görevi oluşturmak için aldığı ve kullandığı bir alt öğe olarak da belirtebilir. Öğesinin içeriği, `Task` görev fabrikasına özeldir.|
|`TaskName`|Gerekli öznitelik.<br /><br /> Bir derlemeden başvurulacak görevin adı. Belirsizlikleri mümkünse, bu öznitelik her zaman tam ad alanları belirtmelidir. Belirsizlikleri varsa, MSBuild rastgele bir eşleşme seçer ve bu beklenmedik sonuçlara neden olabilir.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Belirtilen tarafından oluşturulan görevde görüntülenen parametre kümesi `TaskFactory` .|
|[Görev](../msbuild/task-element-msbuild.md)|`TaskFactory`Görevin bir örneğini oluşturmak için öğesine geçirilen veriler.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar

 Ortam değişkenlerine, komut satırı özelliklerine, proje düzeyi özelliklerine ve proje düzeyi öğelere, `UsingTask` doğrudan veya içeri aktarılan bir proje dosyası aracılığıyla proje dosyasında içerilen öğelerde başvurulabilir. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

> [!NOTE]
> `UsingTask`Öğe, MSBuild altyapısına genel olarak kaydedilen *. Tasks* dosyalarından biri geliyorsa, proje düzeyi özellikleri ve öğeleri bir anlamı yoktur. Proje düzeyi değerleri MSBuild 'e Global değildir.

 MSBuild 4,0 ' de, görevler kullanılarak *. overridetask* dosyaları yüklenebilir.

Özel görevi içeren derleme `Task` ilk kullanıldığında yüklenir.

## <a name="example-1"></a>Örnek 1

 Aşağıdaki örnek, `UsingTask` öğesinin bir özniteliğiyle nasıl kullanılacağını gösterir `AssemblyName` .

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

 Aşağıdaki örnek, `UsingTask` öğesinin bir özniteliğiyle nasıl kullanılacağını gösterir `AssemblyFile` .

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Nasıl yapılır: hedefleri ve görevleri yapılandırma](../msbuild/how-to-configure-targets-and-tasks.md)   
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
