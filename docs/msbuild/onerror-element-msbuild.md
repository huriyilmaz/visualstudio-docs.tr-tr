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
ms.openlocfilehash: b2ddf970225d96291f76935838a743ba358eff0f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594883"
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

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Gerekli öznitelik.<br /><br /> Bir görev başarısız olursa yürütülecek hedefler. Birden çok hedefi noktalı virgülle ayırın. Birden çok hedef belirtilen sırada yürütülür.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Hedef](../msbuild/target-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevler için kapsayıcı öğesi. |

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], `Target` öğesinin görevlerden biri `ErrorAndStop` (veya `false`) olarak ayarlanan `ContinueOnError` özniteliğiyle başarısız olursa `OnError` öğesini yürütür. Görev başarısız olduğunda, `ExecuteTargets` özniteliğinde belirtilen hedefler yürütülür. Hedefte birden fazla `OnError` öğesi varsa, görev başarısız olduğunda `OnError` öğeleri sırayla yürütülür.

 `ContinueOnError` özniteliği hakkında daha fazla bilgi için bkz. [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).

## <a name="example"></a>Örnek
 Aşağıdaki kod `TaskOne` ve `TaskTwo` görevlerini yürütür. `TaskOne` başarısız olursa, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] `OnError` öğesini değerlendirir ve `OtherTarget` hedefini yürütür.

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
