---
title: VCToolTask sınıfı | Microsoft Docs
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
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591677"
---
# <a name="vctooltask-base-class"></a>VCToolTask temel sınıfı

Çoğu görev, sonunda <xref:Microsoft.Build.Utilities.Task> sınıfından ve [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) sınıfından devralınır. Bu sınıf, bunlardan türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **Vctooltask** temel sınıfının parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Activetoolanahtardeğerleri**|İsteğe **bağlı \<string, ToolSwitch> Sözlük** parametresi.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.|
|**Efektte WorkingDirectory**|İsteğe bağlı **dize** parametresi.|
|**EnableErrorListRegex**|İsteğe bağlı **bool** parametresi.<br/><br/>`true` varsayılan değerdir.|
|**ErrorListRegex**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**Errorlistlistexclusiyon**|İsteğe bağlı **ıtaskitem []** parametresi.|
|**GenerateCommandLine**|İsteğe bağlı **dize** parametresi.<br/><br/>Değer **commandlineformat** *biçimi* [varsayılan = Commandlineformat. forbuildlog] ve **escapeformat** *escapeformat* [varsayılan = escapeformat. Default] değerlerini kullanır.|
|**Generatecommandlineexceptanahtarlarý**|İsteğe bağlı **dize** parametresi.<br/><br/>**[]** *Anahtar/[] anahtar/* dize değerlerini kullanır, **CommandLineFormat** *biçimi* [varsayılan = Commandlineformat. forbuildlog] ve **EscapeFormat** *escapeformat* [varsayılan = escapeformat. Default].|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)<br/>
[Görevler](../msbuild/msbuild-tasks.md)
