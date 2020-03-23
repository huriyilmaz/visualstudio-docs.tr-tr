---
title: OnError Öğesi (MSBuild) | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633089"
---
# <a name="onerror-element-msbuild"></a>OnError öğesi (MSBuild)

Öznitelik başarısız bir görev `ContinueOnError` içinse, `false` bir veya daha fazla hedefin yürütülmesine neden olur.

 \<Proje \<> \<Hedef> OnError>

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
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|
|`ExecuteTargets`|Gerekli öznitelik.<br /><br /> Bir görev başarısız olursa yürütülecek hedefler. Birden fazla hedefi yarı kolonlu olarak ayırın. Belirtilen sırada birden çok hedef yürütülür.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Hedef](../msbuild/target-element-msbuild.md) | MSBuild görevleri için kapsayıcı öğesi. |

## <a name="remarks"></a>Açıklamalar

 MSBuild, `OnError` öğenin `Target` görevlerinden biri `ContinueOnError` `ErrorAndStop` (veya) `false`olarak ayarlanan öznitelikte başarısız olursa öğeyi yürütür. Görev başarısız olduğunda, öznitelikte `ExecuteTargets` belirtilen hedefler yürütülür. Hedefte birden `OnError` fazla öğe varsa, `OnError` görev başarısız olduğunda öğeler sırayla yürütülür.

 Öznitelik hakkında `ContinueOnError` bilgi için [Görev öğesine (MSBuild)](../msbuild/task-element-msbuild.md)bakın. Hedefler hakkında bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md)

## <a name="example"></a>Örnek

 Aşağıdaki kod ve `TaskOne` `TaskTwo` görevleri yürütür. Başarısız `TaskOne` olursa, MSBuild `OnError` öğeyi değerlendirir `OtherTarget` ve hedefi yürütür.

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
- [Hedef](../msbuild/msbuild-targets.md)
