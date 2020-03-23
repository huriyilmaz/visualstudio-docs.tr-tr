---
title: Yorum kodu
description: Bu makalede, Mac için Visual Studio kaynak editörü yorumları kullanarak açıklanır
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 2966d8b89a2609d3fbfc2b6b4561288433641ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67693106"
---
# <a name="comments"></a>Yorumlar

Hata ayıklama veya kod deneme, geçici veya uzun vadeli kod blokları yorum yapmak yararlı olabilir.

Tüm kod bloğunu açıklamayapmak için:

* Kodu seçin ve bağlam menüsünden **Satır Yorumu(lar)** olarak seçin

OR

* Seçili `cmd + /` koddaki anahtar bağlamayı kullanın.

Bu yöntemler, kodun yorum ve yorum olmayan bölümleri için kullanılabilir. C# dosyalarında, kod bölgelerinin yorumlanmasına ve yorumlanamamasına olanak tanıyan ek satır yorumları düzeyleri eklenebilir ve gerçek yorumları korur:

![çok düzeyli yorumlar](media/source-editor-image8.png)

Açıklamalar, kodun etkileşimde bulunabilir gelecekteki geliştiriciler için belgelemek için de yararlıdır. Bunlar genellikle her dilde aşağıdaki şekilde eklenen çok satırlı yorumlar şeklinde yapılır:

**C #**

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

- [Yorum kodu (Windows'ta Visual Studio)](/visualstudio/ide/quickstart-editor#comment-out-code)