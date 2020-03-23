---
title: R kodu için IntelliSense
description: Visual Studio IntelliSense, R kodu yazarken işlevler, nesne üyeleri, kod parçacıkları ve tamamlamalar hakkında bilgi görüntüler.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 854f7d410e327ca92d0c5156d89bc21765e13cc7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999047"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense, kod yazarken çağırabileceğiniz işlevler, nesnelerin üyeleri, işlev bağımsız değişkenleri ve [kod parçacıkları](code-snippets-for-r.md) hakkında bilgileri doğrudan görünümünüzde görüntüler. Ayrıca, siz yazarken olası tamamlanmaları görüntüler ve **Sekme** veya **Enter** tuşlarına bastığında tamamlar **(Gelişmiş** sekmesi için [Düzenleyici seçeneklerine](editing-r-code-in-visual-studio.md#editor-options) bakın). IntelliSense hem düzenleyici hem de [etkileşimli pencerede](interactive-repl-for-r-in-visual-studio.md)mevcuttur.

![İşlev imzası gösteren IntelliSense](media/intellisense-function-signature.png)

Bir işlev veya başka bir deyim yazarken, IntelliSense zaten girdiğiniz şeye göre filtrelenmiş (büyük/küçük harf duyarlı) bir otomatik tamamlama menüsü sağlar:

![IntelliSense otomatik tamamlama menüsü](media/intellisense-auto-complete-menu.png)

**Sekme** (veya **Enter**, veya **Boşluk**, seçeneklerin nasıl ayarlıştına bağlı olarak) tuşuna bastığınızda, açılan göreve seçilen öğeeklenir. Ok tuşları ile seçimi değiştirebilirsiniz.

IntelliSense ayrıca R nesnelerinin üyeleri için öneriler de sunar:

![Nesne üyeleri için IntelliSense önerileri](media/intellisense-auto-complete-r-objects.png)

**ESC** tuşuna basıldığında menü tamamen kapatın. **Ctrl**+**Space**ile geri getirebilir.

Bir işlev `(` çağrısının açılışını yazmak `)` kapanışı ekler ve daha önce gösterildiği gibi imza yardımı getirir:

![Bir işlev için IntelliSense imza yardımı](media/intellisense-function-signature.png)

Yine, **ESC** pop-up reddeder; fonksiyon imzaları için **Ctrl**+**Shift**+**Space**ile tekrar gündeme getirebilirsiniz.

> [!Tip]
> Parametre altındaki metni gizlemede yardımcı oluyorsa, parametrenin metnin saydam olmasına yardımcı olmak için **Ctrl** tuşuna basın ve basılı tutun.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Kullanıcı tanımlı fonksiyonlar ve değişkenler için IntelliSense

IntelliSense, ad-parametre tamamlama da dahil olmak üzere aynı dosyadaki kullanıcı tanımlı işlevler için geçerlidir:

![Kullanıcı tanımlı işlevler için IntelliSense](media/intellisense-same-file-functions.png)

![Kullanıcı tanımlı fonksiyonlar için IntelliSense parametre tamamlama](media/intellisense-parameter-completion.png)

IntelliSense aynı dosyadaki ve geçerli oturumdaki değişkenler için de geçerlidir:

![IntelliSense değişken tamamlama](media/intellisense-variable-completion.png)

> [!Note]
> Etkileşimli pencerede, IntelliSense geçerli R oturumunda yalnızca adları dikkate alır ve projenizdeki dosyaları yok sayar.

## <a name="code-suggestions"></a>Kod önerileri

Kenar boşluğunda bir ampul (akıllı etiket olarak adlandırılır) göründüğünde, Visual Studio yaygın olarak kullanılan bir eylem için bir kısayol olduğunu önerir. Örneğin, bir ampul görmek için `library` düzenleyicibir deyim içeren bir satır üzerinde gezinmek. Ampul seçiminde kullanılabilir seçenekler görüntülenir:

![Editörde R için akıllı etiketler](media/intellisense-smart-tags.png)
