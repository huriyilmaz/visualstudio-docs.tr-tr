---
title: Görev Açıklamaları
description: Kodunuza görev açıklamaları ekleme
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493536"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya şüpheli kodu ya da uyarılarla hızlı geçici çözümleri açıkça açıklamaya yönelik standart bir uygulamadır. Mac için Visual Studio tarafından sunulan varsayılan sinyal belirteçleri TODO, HACK, FIXME ve GERI alınamalardır. Kişiselleştirilmiş belirteçler, aşağıdaki görüntüde gösterildiği gibi **Visual Studio > tercihleri > ortam > görevleri** altında tanımlanabilir:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni bir görev açıklaması eklemek için, Task anahtar sözcüğünü içeren bir açıklama ekleyin. Örneğin:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, **> görevleri görüntüle** menüsü kullanılarak görüntülenebilen **görev listesi** pencerede vurgulayarak bu işaretçilere dikkat çekecek:

![Tek bir TODO öğesini gösteren görev listesi penceresi](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi kullanın (Windows üzerinde Visual Studio)](/visualstudio/ide/using-the-task-list)