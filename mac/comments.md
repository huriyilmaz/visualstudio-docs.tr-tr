---
title: Kodu dışarı açıklama
description: bu makalede, Mac için Visual Studio kaynak düzenleyicisinde yorumların kullanılması açıklanmaktadır
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: reference
ms.openlocfilehash: 266d12d924740740c301dd74aec4358198ab0467
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806410"
---
# <a name="comments"></a>Yorumlar

Hata ayıklarken veya kodla denemeler yaparken, geçici ya da uzun süreli kod blokları yorumu için yararlı olabilir.

Tüm kod bloğunu açıklama olarak eklemek için:

* Kodu seçin ve bağlam menüsünden **satır açıklamalarını aç** ' ı seçin.

VEYA

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

- [açıklama çıkışı kodu (Windows Visual Studio)](/visualstudio/ide/quickstart-editor#comment-out-code)