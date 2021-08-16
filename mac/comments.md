---
title: Kodu açıklamaya alma
description: Bu makalede, uygulamanın kaynak düzenleyicisinde yorumların Mac için Visual Studio
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: 0207c616069fdec1e0fdca0e9efcc1a7bf99a2e5dd60e6b13a24b1515be0cc6b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407203"
---
# <a name="comments"></a>Yorumlar

Hata ayıklarken veya kodla denemeler sırasında, kod bloklarını geçici veya uzun süreli olarak açıklama olarak yapmak yararlı olabilir.

Bir kod bloğunda açıklama yapmak için:

* Kodu seçin ve **bağlam menüsünden Satır Açıklamalarını** Aç/Kaldır'ı seçin

OR

* Seçilen `cmd + /` kodda tuş bağlamayı kullanın.

Bu yöntemler, kodun bölümlerini açıklama ve açıklamadan çekmek için kullanılabilir. C# dosyalarında, kod bölgelerinin açıklama satırı ve açıklamalarını almalarına olanak sağlarken, diğer yandan da gerçek açıklamalar korunarak ek satır açıklaması düzeyleri eklenebilir:

![çok düzeyli açıklamalar](media/source-editor-image8.png)

Açıklamalar, gelecekteki geliştiriciler için kodla etkileşim kuracakları belgelerde de kullanışlıdır. Bunlar genellikle her dilde aşağıdaki şekilde eklenen çok satırlı açıklamalar şeklinde yapılır:

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

- [Kodu açıklama Visual Studio (Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)