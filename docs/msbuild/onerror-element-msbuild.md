---
title: HataDurumunda öğe (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18edfe06a4f2cb98fcb41e93c920b03c53daea8c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633089"
---
# <a name="onerror-element-msbuild"></a>HataDurumunda öğesi (MSBuild)

Hatalı bir görevde `ContinueOnError` özniteliği `false`, bir veya daha fazla hedefin yürütülmesine neden olur.

 \<Proje > \<hedef > \<

## <a name="syntax"></a>Sözdizimi

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
| [Hedef](../msbuild/target-element-msbuild.md) | MSBuild görevleri için kapsayıcı öğesi. |

## <a name="remarks"></a>Açıklamalar

 MSBuild, `Target` öğesinin görevlerden biri `ErrorAndStop` (veya `false`) `ContinueOnError` özniteliği ile başarısız olursa, `OnError` öğesini yürütür. Görev başarısız olduğunda, `ExecuteTargets` özniteliğinde belirtilen hedefler yürütülür. Hedefte birden fazla `OnError` öğesi varsa, görev başarısız olduğunda `OnError` öğeleri sırayla yürütülür.

 `ContinueOnError` özniteliği hakkında daha fazla bilgi için bkz. [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod `TaskOne` ve `TaskTwo` görevlerini yürütür. `TaskOne` başarısız olursa, MSBuild `OnError` öğesini değerlendirir ve `OtherTarget` hedefini yürütür.

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

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Hedefler](../msbuild/msbuild-targets.md)
