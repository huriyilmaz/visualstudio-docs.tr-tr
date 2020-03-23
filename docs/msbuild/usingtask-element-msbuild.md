---
title: UsingTask Öğesi (MSBuild) | Microsoft Dokümanlar
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
ms.openlocfilehash: 22d61fe30e9eb68697f073ca0bcfbcc515e513dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431455"
---
# <a name="usingtask-element-msbuild"></a>UsingTask öğesi (MSBuild)

[Görev](../msbuild/task-element-msbuild.md) öğesinde başvurulan görevi, görev uygulamasını içeren derlemeyle eşler.

 \<Proje \<> UsingTask>

## <a name="syntax"></a>Sözdizimi

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Özellikleri ve öğeleri aksine, bir `UsingTask` `TaskName` için geçerli ilk *öğe* kullanılır; görevleri geçersiz kılmak için varolandan `UsingTask` *önce* yeni bir tane tanımlamanız gerekir.

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`AssemblyName`|`AssemblyName` Öznitelik veya `AssemblyFile` öznitelik gereklidir.<br /><br /> Yüklenecek derlemenin adı. Öznitelik, `AssemblyName` güçlü adlandırma gerekli olmasa da, güçlü adlandırılmış derlemeleri kabul eder. Bu özniteliği kullanmak, .NET'teki <xref:System.Reflection.Assembly.Load%2A> yöntemi kullanarak bir derlemeyüklemeye eşdeğerdir.<br /><br /> Öznitelik kullanılırsa `AssemblyFile` bu özniteliği kullanamazsınız.|
|`AssemblyFile`|Ya `AssemblyName` öznitelik `AssemblyFile` gereklidir.<br /><br /> Derlemenin dosya yolu. Bu öznitelik tam yolları veya göreli yolları kabul eder. Göreli yollar, öğenin beyan edildiği proje dosyasıveya `UsingTask` hedef dosyasının dizinine göredir. Bu özniteliği kullanmak, .NET'teki <xref:System.Reflection.Assembly.LoadFrom%2A> yöntemi kullanarak bir derlemeyüklemeye eşdeğerdir.<br /><br /> Öznitelik kullanılırsa `AssemblyName` bu özniteliği kullanamazsınız.|
|`TaskFactory`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen `Task` adın örneklerini oluşturmaktan sorumlu derlemedeki sınıfı belirtir.  Kullanıcı, görev fabrikasının görevi oluşturmak için aldığı ve kullandığı bir alt öğe `Task` olarak da bir öğe belirtebilir. İçeriği görev `Task` fabrikasına özgüdir.|
|`TaskName`|Gerekli öznitelik.<br /><br /> Bir derlemeden başvurulan görevin adı. Belirsizlikler mümkünse, bu öznitelik her zaman tam ad alanları belirtmelidir. Belirsizlikler varsa, MSBuild beklenmeyen sonuçlara neden olabilecek rasgele bir eşleşme seçer.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirmek için koşul. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ParametreGrubu](../msbuild/parametergroup-element.md)|Belirtilen `TaskFactory`tarafından oluşturulan görevde görünen parametreler kümesi.|
|[Görev](../msbuild/task-element-msbuild.md)|Görevin bir örneğini `TaskFactory` oluşturmak için aktarılan veriler.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar

 Ortam değişkenleri, komut satırı özellikleri, proje düzeyi özellikleri ve proje düzeyi `UsingTask` öğeleri, proje dosyasında yer alan öğelere doğrudan veya içe aktarılan proje dosyası aracılığıyla başvurulabilir. Daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

> [!NOTE]
> `UsingTask` Öğe MSBuild altyapısına genel olarak kaydedilmiş *.tasks* dosyalarından birinden geliyorsa proje düzeyinde özelliklerive öğelerin hiçbir anlamı yoktur. PROJE düzeyi değerleri MSBuild için genel değildir.

 MSBuild 4.0'da, görevleri kullanmak *.geçersiz kılınan görev* dosyalarından yüklenebilir.

Özel görevi içeren derleme ilk `Task` kullanıldığında yüklenir.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öznitelik `UsingTask` ile `AssemblyName` öğenin nasıl kullanılacağını gösterir.

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

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öznitelik `UsingTask` ile `AssemblyFile` öğenin nasıl kullanılacağını gösterir.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
