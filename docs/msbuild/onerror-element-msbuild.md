---
title: HataDurumunda öğe (MSBuild) | Microsoft Docs
description: MSBuild, başarısız bir görev için devam eden özniteliği false olduğunda, bir veya daha fazla hedefin yürütülmesine neden olmak için, bir veya daha fazla hedefin yürütülmesine yol açabilir.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ba50100afaa5a3cebc5a3bc9d59f4e922b8da7b9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108466"
---
# <a name="onerror-element-msbuild"></a>HataDurumunda öğe (MSBuild)

`ContinueOnError`Öznitelik `false` başarısız bir görev için ise, bir veya daha fazla hedefin yürütülmesine neden olur.

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Syntax

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Gerekli öznitelik.<br /><br /> Bir görev başarısız olursa yürütülecek hedefler. Birden çok hedefi noktalı virgülle ayırın. Birden çok hedef belirtilen sırada yürütülür.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Hedef](../msbuild/target-element-msbuild.md) | MSBuild görevler için kapsayıcı öğesi. |

## <a name="remarks"></a>Açıklamalar

 öğesi, öğenin `OnError` `Target` görevlerden biri `ContinueOnError` `ErrorAndStop` (veya) olarak ayarlanan öznitelik ile başarısız `false` olursa, öğesini yürütür MSBuild. Görev başarısız olduğunda, özniteliğinde belirtilen hedefler `ExecuteTargets` yürütülür. Hedefte birden fazla `OnError` öğe varsa, `OnError` görev başarısız olduğunda öğeler sırayla yürütülür.

 Özniteliği hakkında daha fazla bilgi için `ContinueOnError` bkz. [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod `TaskOne` ve `TaskTwo` görevlerini yürütür. `TaskOne`başarısız olursa, MSBuild öğeyi değerlendirir `OnError` ve `OtherTarget` hedefi yürütür.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Targets](../msbuild/msbuild-targets.md)
