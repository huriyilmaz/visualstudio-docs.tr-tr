---
title: Unity Log Callback'i VSTU ile paylaşın | Microsoft Dokümanlar
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: aa8a4a229102a6a9439ffb36582cd03e322a086b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815671"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Unity günlük geri aramasını VSTU ile paylaşın
Visual Studio Tools for Unity konsolunu Visual Studio'ya aktarabilmek için Unity ile günlük geri arama kaydeder. Düzenleyici komut dosyalarınız da Unity ile günlük geri arama sıyrıkları kaydederse, VSTU geri araması geri aramanızı etkileyebilir. Bu olasılığı önlemek `VisualStudioIntegration.LogCallback` için, vstu ile işbirliği yapmak için olayı kullanın.

## <a name="demonstrates"></a>Gösteriler
 Visual Studio Tools for Unity tarafından oluşturulan Unity Log Callback nasıl paylaşılır?

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
 [Örnek: Proje dosyası oluşturma](../cross-platform/customize-project-files-created-by-vstu.md)
