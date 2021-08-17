---
title: VCToolTask Sınıf | Microsoft Docs
description: VCToolTask temel sınıfının bundan devralınan görevlere ekleyen çeşitli parametreler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e8444755cf0d3e3b5d900f756189f1e0b8128d6b7d6b8d22f940b2b710882cce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397195"
---
# <a name="vctooltask-base-class"></a>VCToolTask temel sınıfı

Çoğu görev sonuçta sınıfından ve <xref:Microsoft.Build.Utilities.Task> [ToolTask sınıfından](/dotnet/api/microsoft.build.utilities.tooltask) devralınır. Bu sınıf, görevlerden türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **VCToolTask** temel sınıfının parametreleri açık almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|**İsteğe \<string, ToolSwitch> bağlı Sözlük** parametresi.|
|**AdditionalOptions**|İsteğe **bağlı dize** parametresi.|
|**EffectiveWorkingDirectory**|İsteğe **bağlı dize** parametresi.|
|**EnableErrorListRegex**|İsteğe **bağlı bool** parametresi.<br/><br/>`true` varsayılan değerdir.|
|**ErrorListRegex**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**ErrorListListExclusion**|İsteğe **bağlı ITaskItem[]** parametresi.|
|**GenerateCommandLine**|İsteğe **bağlı dize** parametresi.<br/><br/>**CommandLineFormat biçimi** *[default* = CommandLineFormat.ForBuildLog] ve **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default] değerlerini kullanır.|
|**GenerateCommandLineExceptSwitches**|İsteğe **bağlı dize** parametresi.<br/><br/>**string[]** *switchesToRemove*, **CommandLineFormat** *biçimi* [default = CommandLineFormat.ForBuildLog] ve **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default] değerlerini kullanır.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)<br/>
[Görevler](../msbuild/msbuild-tasks.md)
