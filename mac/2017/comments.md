---
title: Kodu dışarı açıklama
description: Bu makalede, Mac için Visual Studio kaynak düzenleyicisinde yorumların kullanılması açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: 44eee75b4803b4317bb7d3cd02cb19b55f41a067
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85949995"
---
# <a name="comments"></a>Yorumlar

Hata ayıklarken veya kodla denemeler yaparken, geçici ya da uzun süreli kod blokları yorumu için yararlı olabilir.

Tüm kod bloğunu açıklama olarak eklemek için:

* Kodu seçin ve bağlam menüsünden **satır açıklamalarını aç** ' ı seçin.

OR

* `cmd + /`Seçili kodda KeyBinding 'i kullanın.

Bu yöntemler kodun bölümlerini açıklamaya ve açıklama eklemek için kullanılabilir. C# dosyalarında, kod bölgelerinin açıklamalı ve açıklama kaldırmamaları, ancak yine de gerçek Yorumları korurken ek satır açıklamaları eklenebilir.

![çok düzeyli açıklamalar](media/source-editor-image8.png)

Açıklamalar Ayrıca, gelecekteki geliştiricilerle etkileşime girebilen kod belgeleme için de yararlıdır. Bunlar genellikle her dilde aşağıdaki şekilde eklenen çok satırlı açıklamalar biçiminde yapılır:

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Açıklama çıkışı kodu (Windows üzerinde Visual Studio)](/visualstudio/ide/quickstart-editor#comment-out-code)