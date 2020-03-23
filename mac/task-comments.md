---
title: Görev Açıklamaları
description: Kodunuza görev yorumları ekleme
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692318"
---
# <a name="task-comments"></a>Görev Açıklamaları

Kod yazarken, tamamlanmamış veya şüpheli kodu veya uyarılarla hızlı geçici çözüm le açıkça yorum yapmak standart bir uygulamadır. Visual Studio tarafından Mac için sağlanan varsayılan sinyal belirteçleri TODO, HACK, FIXME ve UNDONE'dir. Kişiselleştirilmiş belirteçler **Visual Studio > Tercihleri > Çevre > Görevleri**altında tanımlanabilir , aşağıdaki resimde gösterildiği gibi:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni bir görev yorumu eklemek için, görev anahtar sözcüklerini içeren bir açıklama ekleyin. Örnek:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio, **Görev Listesi** defterinde vurgulayarak bu işaretçilere dikkat çeker, bu da **> Pad'leri > Görev'e göz**gezdirerek görüntülenebilir:

![Görev listesi defteri](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Listesini Kullanma (Windows'ta Visual Studio)](/visualstudio/ide/using-the-task-list)