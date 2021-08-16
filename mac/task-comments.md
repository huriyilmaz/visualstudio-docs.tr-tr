---
title: Görev Açıklamaları
description: Kodunuza görev açıklamaları ekleme
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 0e2aedf52974529864650fabe6d83db2a60b50cd15156e0cc2e96583261de3ed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349307"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya şüpheli kodu ya da uyarılarla hızlı geçici çözümleri açıkça açıklamaya yönelik standart bir uygulamadır. Mac için Visual Studio tarafından sunulan varsayılan sinyal belirteçleri TODO, hack, fixme ve geri alınamalardır. kişiselleştirilmiş belirteçler, aşağıdaki görüntüde gösterildiği gibi **Visual Studio > tercihleri > ortam > görevleri** altında tanımlanabilir:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni bir görev açıklaması eklemek için, Task anahtar sözcüğünü içeren bir açıklama ekleyin. Örnek:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, **> görevleri görüntüle** menüsü kullanılarak görüntülenebilen **Görev Listesi** pencerede vurgulayarak bu işaretçilere dikkat çekecek:

![Tek bir TODO öğesini gösteren görev listesi penceresi](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesi (Visual Studio Windows) kullanın](/visualstudio/ide/using-the-task-list)