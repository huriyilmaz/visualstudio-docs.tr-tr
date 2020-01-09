---
title: UsingTask öğesi (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bd62738a89b38adb6cd01d6a33d661e95144d34
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565272"
---
# <a name="usingtask-element-msbuild"></a>UsingTask öğesi (MSBuild)
Bir [görev](../msbuild/task-element-msbuild.md) öğesinde başvurulan görevi, görev uygulamasını içeren derlemeye eşler.

 \<Proje > \<UsingTask >

## <a name="syntax"></a>Sözdizimi

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Özellikler ve öğelerin aksine, bir `TaskName` için geçerli olan *ilk* `UsingTask` öğesi kullanılacaktır; görevleri geçersiz kılmak için, mevcut bir `UsingTask` *önce* yeni bir tanımlamanız gerekir.

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`AssemblyName`|`AssemblyName` özniteliği ya da `AssemblyFile` özniteliği gereklidir.<br /><br /> Yüklenecek derlemenin adı. `AssemblyName` özniteliği kesin adlandırılmış derlemeler kabul eder, ancak güçlü adlandırma gerekli değildir. Bu özniteliğin kullanılması, .NET 'teki <xref:System.Reflection.Assembly.Load%2A> yöntemi kullanılarak bir derlemeyi yüklemeye eşdeğerdir.<br /><br /> `AssemblyFile` özniteliği kullanılırsa bu özniteliği kullanamazsınız.|
|`AssemblyFile`|`AssemblyName` ya da `AssemblyFile` özniteliği gereklidir.<br /><br /> Derlemenin dosya yolu. Bu öznitelik, tam yolları veya göreli yolları kabul eder. Göreli yollar, `UsingTask` öğesinin bildirildiği proje dosyasının veya hedef dosyanın dizinine göre belirlenir. Bu özniteliğin kullanılması, .NET 'teki <xref:System.Reflection.Assembly.LoadFrom%2A> yöntemi kullanılarak bir derlemeyi yüklemeye eşdeğerdir.<br /><br /> `AssemblyName` özniteliği kullanılırsa bu özniteliği kullanamazsınız.|
|`TaskFactory`|İsteğe bağlı öznitelik.<br /><br /> Derlemede, belirtilen `Task` adının örneklerini oluşturmaktan sorumlu sınıfı belirtir.  Kullanıcı, görev fabrikasının görevi oluşturmak için aldığı ve kullandığı bir alt öğe olarak bir `TaskBody` da belirtebilir. `TaskBody` içeriği, görev fabrikasına özeldir.|
|`TaskName`|Gerekli öznitelik.<br /><br /> Bir derlemeden başvurulacak görevin adı. Belirsizlikleri mümkünse, bu öznitelik her zaman tam ad alanları belirtmelidir. Belirsizlikleri varsa, MSBuild rastgele bir eşleşme seçer ve bu beklenmedik sonuçlara neden olabilir.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Belirtilen `TaskFactory`tarafından oluşturulan görevde görüntülenen parametre kümesi.|
|[Görev](../msbuild/task-element-msbuild.md)|Görevin bir örneğini oluşturmak için `TaskFactory` geçirilen veriler.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar
 Ortam değişkenlerine, komut satırı özelliklerine, proje düzeyi özelliklerine ve proje düzeyi öğelere, doğrudan veya içeri aktarılan bir proje dosyası aracılığıyla proje dosyasında içerilen `UsingTask` öğelerinde başvurulabilir. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

> [!NOTE]
> `UsingTask` öğe, MSBuild altyapısına genel olarak kaydedilen *. Tasks* dosyalarından birinden geliyorsa, proje düzeyi Özellikler ve öğelerin hiçbir anlamı yoktur. Proje düzeyi değerleri MSBuild 'e Global değildir.

 MSBuild 4,0 ' de, görevler kullanılarak *. overridetask* dosyaları yüklenebilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `AssemblyName` özniteliğiyle `UsingTask` öğesinin nasıl kullanılacağını gösterir.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody>
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `AssemblyFile` özniteliğiyle `UsingTask` öğesinin nasıl kullanılacağını gösterir.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
