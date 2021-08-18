---
title: Görev Temel Sınıf | Microsoft Docs
description: Microsoft.Build.Utilities.Task temel sınıfının bu sınıftan devralınan görevlere ekleyen parametreleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8d033a3cfd993ffb31af49f0276637302b7fc819
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142851"
---
# <a name="task-base-class"></a>Görev temel sınıfı

Çoğu görev sonuçta sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu sınıf, görevlerden türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda bu temel sınıfın parametreleri açık almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|İsteğe <xref:Microsoft.Build.Framework.IBuildEngine> bağlı parametre.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimini belirtir. Derleme altyapısı, görevlerin bu parametreye geri çağrılmalarına izin vermek için bu parametreyi otomatik olarak ayarlar.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|İsteğe <xref:Microsoft.Build.Framework.IBuildEngine2> bağlı parametre.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimini belirtir. Derleme altyapısı, görevlerin bu parametreye geri çağrılmalarına izin vermek için bu parametreyi otomatik olarak ayarlar.<br /><br /> Bu özellik kolaylık sağlar, böylece bu sınıftan devralan görev yazarlarının değerinden değerine türe türetir. `IBuildEngine` `IBuildEngine2`|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|İsteğe <xref:Microsoft.Build.Framework.IBuildEngine3> bağlı parametre.<br /><br /> Konak tarafından sağlanan derleme altyapısı arabirimini belirtir.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|İsteğe <xref:Microsoft.Build.Framework.ITaskHost> bağlı parametre.<br /><br /> Konak nesne örneğini belirtir (null olabilir). Konak IDE'nin bu belirli görevle bir konak nesnesi ilişkilendirilmişse, derleme altyapısı bu özelliği ayarlar.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|İsteğe <xref:Microsoft.Build.Utilities.TaskLoggingHelper> bağlı salt okunur parametre.<br /><br /> Günlük yardımcı nesnesi..|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
