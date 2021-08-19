---
title: ImportGroup Öğesi | Microsoft Docs
description: İsteğe MSBuild bir İçeri Aktarma öğeleri koleksiyonunu içermek için ImportGroup öğesini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7c21f9c967203db05a68e79436204aca9878fd42
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143319"
---
# <a name="importgroup-element"></a>ImportGroup öğesi

  
İsteğe bağlı `Import` bir koşul altında gruplu öğeler koleksiyonunu içerir. Daha fazla bilgi için [bkz. Import öğesi (MSBuild)](../msbuild/import-element-msbuild.md).

```xml
<Project>
  <ImportGroup>
```

## <a name="syntax"></a>Syntax

```xml
<ImportGroup Condition="'String A' == 'String B'">
    <Import ... />
    <Import ... />
</ImportGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[İçeri Aktar](../msbuild/import-element-msbuild.md)|Bir proje dosyasının içeriğini başka bir proje dosyasına içeri aktarır.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Bir proje dosyasının gerekli MSBuild öğesi. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, öğesini `ImportGroup` gösterir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
