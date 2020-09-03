---
title: Görev Açıklamaları
description: Kodunuza görev açıklamaları ekleme
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692318"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya şüpheli kodu ya da uyarılarla hızlı geçici çözümleri açıkça açıklamaya yönelik standart bir uygulamadır. Mac için Visual Studio tarafından sunulan varsayılan sinyal belirteçleri TODO, HACK, FIXME ve GERI alınamalardır. Kişiselleştirilmiş belirteçler, aşağıdaki görüntüde gösterildiği gibi **Visual Studio > tercihleri > ortam > görevleri**altında tanımlanabilir:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni bir görev açıklaması eklemek için, Task anahtar sözcüğünü içeren bir açıklama ekleyin. Örneğin:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, **görev listesi** panelinde vurgulayarak bu işaretçilere dikkat çekerek **> Pad > görevine**gidilerek görüntülenebilirler:

![Görev listesi paneli](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi kullanın (Windows üzerinde Visual Studio)](/visualstudio/ide/using-the-task-list)