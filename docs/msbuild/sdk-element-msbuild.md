---
title: SDK öğesi (MSBuild) | Microsoft Docs
description: MSBuild proje Sdk 'sına başvuran MSBuild Sdk öğesi için sözdizimi, öznitelikler ve öğeler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2f4af21014bd749897bf8872fc09c934f1e6ecf9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108362"
---
# <a name="sdk-element-msbuild"></a>SDK öğesi (MSBuild)

MSBuild proje SDK 'sına başvurur.

 \<Project> \<Sdk>

## <a name="syntax"></a>Syntax

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli öznitelik.<br /><br /> Proje SDK 'sının adı.|
|`Version`|İsteğe bağlı öznitelik.<br /><br /> Proje SDK 'sının sürümü|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="see-also"></a>Ayrıca bkz.

- [nasıl yapılır: MSBuild projesi SDK 'ya başvurma](../msbuild/how-to-use-project-sdk.md)
- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
