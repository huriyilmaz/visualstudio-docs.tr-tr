---
title: Görev Açıklamaları
description: Kodunuza görev yorumları ekleme
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964843"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya sorgulanabilir kodu açıkça açıklamaya veya uyarılarla hızlı geçici çözümlere açıkça açıklama yapmak standart bir uygulamadır. Bu belirteçler tarafından sağlanan varsayılan sinyal Mac için Visual Studio TODO, HACK, FIXME ve UNDONE'dır. Kişiselleştirilmiş belirteçler, aşağıdaki **görüntüde Visual Studio >**> Ortam > Görevleri altında tanımlanabilir:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni görev açıklaması eklemek için görev anahtar sözcüğünü içeren bir açıklama ekleyin. Örnek:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, Görev Listesi Görevleri Görüntüle menüsü kullanılarak görüntülen  Görev Listesi vurgular ve **bu > dikkat** çeker:

![Tek bir TODO öğesini gösteren Görev listesi penceresi](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi kullanma (Visual Studio Windows)](/visualstudio/ide/using-the-task-list)