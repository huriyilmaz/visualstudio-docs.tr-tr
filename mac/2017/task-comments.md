---
title: Görev Açıklamaları
description: Kodunuza görev yorumları ekleme
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 4f7f3d1567972c3841af6deb37677a7e01cdb825
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962273"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya sorgulanabilir kodu açıkça açıklamaya veya uyarılarla hızlı geçici çözümlere açıkça açıklama yapmak standart bir uygulamadır. Bu belirteçler tarafından sağlanan varsayılan sinyal Mac için Visual Studio TODO, HACK, FIXME ve UNDONE'dır. Kişiselleştirilmiş belirteçler, aşağıdaki **görüntüde Visual Studio > > Ortam > Görevleri** altında tanımlanabilir:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni görev açıklaması eklemek için görev anahtar sözcüğünü içeren bir açıklama ekleyin. Örnek:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, görev için Görünüm > **Pad'leri'ne** giderek görüntülen Görev Listesi panelinin içinde vurgular ve bu > dikkat **çeker:**

![Görev listesi paneli](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi kullanma (Visual Studio Windows)](/visualstudio/ide/using-the-task-list)