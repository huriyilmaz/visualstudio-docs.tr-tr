---
title: Hedefin Görev Elemanı (MSBuild) | Microsoft Dokümanlar
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a4ec2203430045c083b46b2eea8d3e884a4b794
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263181"
---
# <a name="task-element-of-target-msbuild"></a>Hedefin Görev öğesi (MSBuild)

MSBuild görevinin bir örneğini oluşturur ve yürütür. Öğe adı oluşturulan görevin adı ile belirlenir.

 \<Proje \<> Hedef>

## <a name="syntax"></a>Sözdizimi

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|
|`ContinueOnError`|İsteğe bağlı öznitelik. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **doğru**. Bir görev başarısız olduğunda, [Hedef](../msbuild/target-element-msbuild.md) öğe ve yapısonraki görevler yürütmeye devam eder ve görevden gelen tüm hatalar uyarı olarak kabul edilir.<br />-   **HataandContinue**. Bir görev başarısız olduğunda, `Target` öğe ve yapı sonraki görevler yürütmeye devam eder ve görevden tüm hatalar hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, `Target` öğe ve yapıda kalan görevler yürütülmez ve tüm `Target` öğe ve yapı başarısız olmuş olarak kabul edilir.<br /><br /> .NET Framework'ün 4.5'ten önceki `true` `false` sürümleri yalnızca değerleri ve değerleri desteklemişti.<br /><br /> Daha fazla bilgi için [bkz: Görevlerdeki hataları yoksay.](../msbuild/how-to-ignore-errors-in-tasks.md)|
|`Parameter`|Görev sınıfı öznitelik ile etiketlenmiş bir `[Required]` veya daha fazla özellik içeriyorsa gereklidir.<br /><br /> Değeri olarak parametre değerini içeren kullanıcı tanımlı görev parametresi. `Task` Öğede, görev sınıfındaki bir .NET özelliğine her öznitelik eşlenemesiyle herhangi bir sayıda parametre olabilir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Çıktı](../msbuild/output-element-msbuild.md)|Görevden çıktıları proje dosyasında depolar. Bir görevde sıfır `Output` veya daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Hedef](../msbuild/target-element-msbuild.md) | MSBuild görevleri için kapsayıcı öğesi. |

## <a name="remarks"></a>Açıklamalar

 MSBuild proje dosyasındaki bir `Task` öğe görevin bir örneğini oluşturur, üzerinde özellikler ayarlar ve çalıştırın. Öğe, `Output` proje dosyasının başka bir yerinde kullanılacak özelliklerde veya öğelerde çıktı parametrelerini depolar.

 Bir [görevin](../msbuild/onerror-element-msbuild.md) üst `Target` öğesinde OnError öğeleri varsa, görev başarısız olursa ve `ContinueOnError` `false`değeri . Görevler hakkında daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği [Csc görev](../msbuild/csc-task.md) sınıfının bir örneğini oluşturur, altı özellik ayarlar ve görevi yürütür. Yürütmeden sonra, nesnenin `OutputAssembly` özelliğinin değeri adlı `FinalAssemblyName`bir öğe listesine yerleştirilir.

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
