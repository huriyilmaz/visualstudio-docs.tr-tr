---
title: Görev temel sınıfı | Microsoft Docs
description: Microsoft. Build. Utilities. Task temel sınıfının, ondan devraldığı görevlere eklediği parametreler hakkında bilgi edinin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726851"
---
# <a name="task-base-class"></a>Görev temel sınıfı

Çoğu görev sonunda <xref:Microsoft.Build.Utilities.Task> sınıfından devralınır. Bu sınıf, bunlardan türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda bu temel sınıfın parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine> parametre.<br /><br /> Görevler için kullanılabilen derleme altyapısı arabirimini belirtir. Yapı altyapısı bu parametreyi otomatik olarak ayarlar ve görevlere geri çağrı yapmasına izin verir.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine2> parametre.<br /><br /> Görevler için kullanılabilen derleme altyapısı arabirimini belirtir. Yapı altyapısı bu parametreyi otomatik olarak ayarlar ve görevlere geri çağrı yapmasına izin verir.<br /><br /> Bu bir kullanışlı özelliktir. bu sınıftan devralan görev yazarlarının değeri ' dan ' a dönüştürmek zorunda değildir `IBuildEngine` `IBuildEngine2` .|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine3> parametre.<br /><br /> Konak tarafından belirtilen derleme altyapısı arabirimini belirtir.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskHost> parametre.<br /><br /> Ana bilgisayar nesne örneğini belirtir (null olabilir). Konak IDE, bu görevle bir ana bilgisayar nesnesi ilişkilendirirse, derleme altyapısı bu özelliği ayarlar.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|İsteğe bağlı <xref:Microsoft.Build.Utilities.TaskLoggingHelper> salt okunurdur parametresi.<br /><br /> Günlük Yardımcısı nesnesi..|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
