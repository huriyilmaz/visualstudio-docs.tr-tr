---
title: Task öğesi (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: d17dde15fdfcc00890338eadf603f02352697363
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631880"
---
# <a name="task-element-msbuild"></a>Task öğesi (MSBuild)

MSBuild görevi örneğini oluşturur ve yürütür. Öğe adı, oluşturulmakta olan görevin adına göre belirlenir.

 \<Proje > \<hedefi >

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
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|İsteğe bağlı öznitelik. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** ya da **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki kalan görevler yürütülmez ve tüm `Target` öğesi ve derleme başarısız olduğu kabul edilir.<br /><br /> 4,5 öncesindeki .NET Framework sürümleri yalnızca `true` ve `false` değerlerini destekliyordu.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Task sınıfı, `[Required]` özniteliğiyle etiketlenmiş bir veya daha fazla özellik içeriyorsa gereklidir.<br /><br /> Değer olarak parametre değerini içeren Kullanıcı tanımlı bir görev parametresi. `Task` öğesinde, her öznitelik, görev sınıfındaki bir .NET özelliği ile eşlemesiyle herhangi bir sayıda parametre olabilir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Çıktı](../msbuild/output-element-msbuild.md)|Projedeki çıkışları proje dosyasında depolar. Bir görevde sıfır veya daha fazla öğe `Output` olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Hedef](../msbuild/target-element-msbuild.md) | MSBuild görevleri için kapsayıcı öğesi. |

## <a name="remarks"></a>Açıklamalar

 MSBuild proje dosyasındaki `Task` öğesi bir görevin örneğini oluşturur, üzerinde özellikleri ayarlar ve yürütür. `Output` öğesi, proje dosyasında başka bir yerde kullanılacak olan özellikler veya öğelerde çıkış parametrelerini depolar.

 Bir görevin üst `Target` [öğesinde herhangi bir](../msbuild/onerror-element-msbuild.md) II öğesi varsa, görev başarısız olursa ve `ContinueOnError` `false`bir değere sahipse bunlar yine de değerlendirilir. Görevler hakkında daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, [Csc görev](../msbuild/csc-task.md) sınıfının bir örneğini oluşturur, özelliklerin altıyı ayarlar ve görevi yürütür. Yürütmeden sonra, nesnesinin `OutputAssembly` özelliğinin değeri, `FinalAssemblyName`adlı bir öğe listesine yerleştirilir.

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
