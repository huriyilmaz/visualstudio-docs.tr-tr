---
title: TaskExtension Temel Sınıf | Microsoft Docs
description: Microsoft.Build.Tasks.TaskExtension temel sınıfının bundan devralınan görevlere eklemiş olduğu parametreler hakkında bilgi edinmek.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 56bdde67acb9432cb02e89735a137ca3f094d6cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142773"
---
# <a name="taskextension-base-class"></a>TaskExtension temel sınıfı

Birçok görev sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> devralınır ve bu da sınıftan <xref:Microsoft.Build.Utilities.Task> devralınır. Bu devralma zinciri, görevlerden türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda temel sınıfların parametreleri açıkmektedir.

|Parametre|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|İsteğe <xref:Microsoft.Build.Framework.IBuildEngine> bağlı parametre.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimini belirtir. Derleme altyapısı, görevlerin bu parametreye geri çağrılmalarına izin vermek için bu parametreyi otomatik olarak ayarlar.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|İsteğe <xref:Microsoft.Build.Framework.IBuildEngine2> bağlı parametre.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimini belirtir. Derleme altyapısı, görevlerin bu parametreye geri çağrılmalarına izin vermek için bu parametreyi otomatik olarak ayarlar.<br /><br /> Bu özellik kolaylık sağlar, böylece bu sınıftan devralan görev yazarlarının değerinden değerine türe türetleri `IBuildEngine` `IBuildEngine2` yoktur.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|İsteğe <xref:Microsoft.Build.Framework.IBuildEngine3> bağlı parametre.<br /><br /> Konak tarafından sağlanan derleme altyapısı arabirimini belirtir.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|İsteğe <xref:Microsoft.Build.Framework.ITaskHost> bağlı parametre.<br /><br /> Konak nesne örneğini belirtir (null olabilir). Konak IDE'nin bu belirli görevle bir konak nesnesi ilişkilendirilmişse, derleme altyapısı bu özelliği ayarlar.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|İsteğe <xref:Microsoft.Build.Utilities.TaskLoggingHelper> bağlı salt okunur parametre.<br /><br /> Görev `TaskLoggingHelperExtension` günlüğü yöntemlerini içeren bir nesnesi alır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
