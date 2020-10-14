---
title: VSTU ile Unity günlük geri aramasını paylaşma | Microsoft Docs
description: Kendi konsolunu Visual Studio 'ya aktarmak için Unity için Visual Studio Araçları (VSTU) ile kaydettirilen bir kayıt ile Unity günlük geri aramasını paylaşabilirsiniz.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 88abc27ad757487ae8f65b8bbb66d4dfee9791cc
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039878"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>VSTU ile Unity günlük geri aramasını paylaşma
Unity için Visual Studio Araçları, kendi konsolunu Visual Studio 'ya akıkabilmek için Unity ile bir günlük geri çağırma kaydeder. Düzenleyici betikleriniz Ayrıca Unity ile bir günlük geri çağırma işlemini kaydettiğinin, VSTU geri çağırması geri çağırmanızı etkileyebilir. Bu olasılığa engel olmak için, bir `VisualStudioIntegration.LogCallback` olayı, VSTU ile birlikte çalışmak üzere kullanın.

## <a name="demonstrates"></a>Gösteriler
 Unity için Visual Studio Araçları tarafından oluşturulan Unity günlük geri aramasını paylaşma.

## <a name="example"></a>Örnek

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>Ayrıca bkz.
 [Örnek: proje dosyası oluşturma](../cross-platform/customize-project-files-created-by-vstu.md)
