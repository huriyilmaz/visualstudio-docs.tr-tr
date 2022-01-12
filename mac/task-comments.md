---
title: Görev Açıklamaları
description: Kodunuza görev yorumları ekleme
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/09/2020
ms.topic: reference
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: aaa1c68e1089e3ff1df131df2fac84ecbf426551
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805825"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya sorgulanabilir kodu açıkça açıklamaya veya uyarılarla hızlı geçici çözümlere açıkça açıklama yapmak standart bir uygulamadır. Bu belirteçler tarafından sağlanan varsayılan sinyal Mac için Visual Studio TODO, HACK, FIXME ve UNDONE'dır. Kişiselleştirilmiş belirteçler, aşağıdaki **görüntüde Visual Studio >**> Ortam > Görevleri altında tanımlanabilir:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni görev açıklaması eklemek için görev anahtar sözcüğünü içeren bir açıklama ekleyin. Örneğin:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, Görev Listesi Görevleri Görüntüle menüsü kullanılarak **görüntülen** Görev Listesi vurgular ve bu **> dikkat** çeker:

![Tek bir TODO öğesini gösteren Görev listesi penceresi](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi kullanma (Visual Studio Windows)](/visualstudio/ide/using-the-task-list)