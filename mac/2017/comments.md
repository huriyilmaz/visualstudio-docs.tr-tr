---
title: Kodu açıklama
description: Bu makalede, Mac için Visual Studio kaynak düzenleyicisinde yorumların kullanılması açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 038c2bf7205ccc642d613893635b9323afe613b9
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74982638"
---
# <a name="comments"></a>Açıklamalar

Hata ayıklarken veya kodla denemeler yaparken, geçici ya da uzun süreli kod blokları yorumu için yararlı olabilir.

Tüm kod bloğunu açıklama olarak eklemek için:

* Kodu seçin ve bağlam menüsünden **satır açıklamalarını aç** ' ı seçin.

VEYA

* Seçili kodda `cmd + /` KeyBinding kullanın.

Bu yöntemler kodun bölümlerini açıklamaya ve açıklama eklemek için kullanılabilir. C# Dosyalarda, kod bölgelerinin açıklamalı ve açıklama kaldırmamaları, ancak yine de gerçek Yorumları korurken ek satır açıklamaları eklenebilir.

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