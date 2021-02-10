---
title: TaskExtension temel sınıfı | Microsoft Docs
description: Microsoft. Build. Tasks. TaskExtension temel sınıfının, ondan devraldığı görevlere eklediği parametreler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6692cb16b3861d72bf713c22b2ecfb2ee95bc036
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965986"
---
# <a name="taskextension-base-class"></a>TaskExtension temel sınıfı

Birçok görev <xref:Microsoft.Build.Tasks.TaskExtension> , sınıfından devralan sınıfından devralır <xref:Microsoft.Build.Utilities.Task> . Bu devralma zinciri, bunlardan türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda temel sınıfların parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine> parametre.<br /><br /> Görevler için kullanılabilen derleme altyapısı arabirimini belirtir. Yapı altyapısı bu parametreyi otomatik olarak ayarlar ve görevlere geri çağrı yapmasına izin verir.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine2> parametre.<br /><br /> Görevler için kullanılabilen derleme altyapısı arabirimini belirtir. Yapı altyapısı bu parametreyi otomatik olarak ayarlar ve görevlere geri çağrı yapmasına izin verir.<br /><br /> Bu bir kullanışlı özelliktir. bu sınıftan devralan görev yazarlarının değeri ' dan ' a dönüştürmek zorunda değildir `IBuildEngine` `IBuildEngine2` .|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine3> parametre.<br /><br /> Konak tarafından belirtilen derleme altyapısı arabirimini belirtir.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskHost> parametre.<br /><br /> Ana bilgisayar nesne örneğini belirtir (null olabilir). Konak IDE, bu görevle bir ana bilgisayar nesnesi ilişkilendirirse, derleme altyapısı bu özelliği ayarlar.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|İsteğe bağlı <xref:Microsoft.Build.Utilities.TaskLoggingHelper> salt okunurdur parametresi.<br /><br /> `TaskLoggingHelperExtension`Görev günlüğü yöntemlerini içeren bir nesne alır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
