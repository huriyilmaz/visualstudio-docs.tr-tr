---
title: Kodu açıklamaya alma
description: Bu makalede, uygulamanın kaynak düzenleyicisinde yorumların Mac için Visual Studio
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: a0aa3de91f1a2c75d73409d89f3cbc8894faacab
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964760"
---
# <a name="comments"></a>Yorumlar

Hata ayıklarken veya kodla denemeler sırasında, kod bloklarını geçici veya uzun süreli olarak açıklama olarak yapmak yararlı olabilir.

Bir kod bloğunda açıklama yapmak için:

* Kodu seçin ve **bağlam menüsünden** Satır Açıklamalarını Aç/Kaldır'ı seçin

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