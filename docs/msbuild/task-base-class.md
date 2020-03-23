---
title: Görev Taban Sınıfı | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7d6e0870f809a30bc3feb7ecb7a7302b7729124
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631958"
---
# <a name="task-base-class"></a>Görev taban sınıfı

Birçok görev sonuçta <xref:Microsoft.Build.Utilities.Task> sınıftan devralınır. Bu sınıf, bunlardan türeyen görevlere çeşitli parametreler ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda bu taban sınıfın parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine> parametre.<br /><br /> Görevlerin kullanabileceği yapı altyapısı arabirimini belirtir. Yapı motoru, görevlerin geri çağrılmasını sağlamak için bu parametreyi otomatik olarak ayarlar.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine2> parametre.<br /><br /> Görevlerin kullanabileceği yapı altyapısı arabirimini belirtir. Yapı motoru, görevlerin geri çağrılmasını sağlamak için bu parametreyi otomatik olarak ayarlar.<br /><br /> Bu, bu sınıftan devralan görev yazarlarının değeri 'den ' `IBuildEngine` `IBuildEngine2`e ' ye dökmek zorunda kalmaması için bir kolaylık özelliğidir.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine3> parametre.<br /><br /> Ana bilgisayar tarafından sağlanan yapı motoru arabirimini belirtir.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskHost> parametre.<br /><br /> Ana bilgisayar nesnesi örneğini belirtir (null olabilir). Ana bilgisayar IDE bu özel görevle bir ana bilgisayar nesnesi ilişkilendirmişse yapı altyapısı bu özelliği ayarlar.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|İsteğe bağlı <xref:Microsoft.Build.Utilities.TaskLoggingHelper> salt okunur parametresi.<br /><br /> Günlüğe kaydetme yardımcı nesnesi...|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
