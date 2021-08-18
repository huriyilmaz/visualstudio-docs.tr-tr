---
title: R kodu için IntelliSense
description: Visual Studio Siz R kodu yazarak IntelliSense işlevler, nesne üyeleri, kod parçacıkları ve tamamlamalar hakkında bilgi görüntüler.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: a635ac8cc95648d1885239661c4b7edf4167692b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060693"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense, siz kod yazma sırasında çağırabilirsiniz işlevler, nesnelerin [](code-snippets-for-r.md) üyeleri, işlev bağımsız değişkenleri ve kod parçacıkları hakkında bilgileri doğrudan görünümde görüntüler. Ayrıca, siz yazarak olası tamamlamaları görüntüler ve **Sekme** veya **Enter** tuşlarına basıldıklarında tamamlanır [(bkz.](editing-r-code-in-visual-studio.md#editor-options) Gelişmiş sekmesi için **Düzenleyici seçenekleri).** IntelliSense hem düzenleyicide hem de etkileşimli [penceresinde kullanılabilir.](interactive-repl-for-r-in-visual-studio.md)

![İşlev imzasını gösteren IntelliSense](media/intellisense-function-signature.png)

Bir işlev veya başka bir deyim yazarken IntelliSense, girdiğinize göre filtrelenmiş (büyük/küçük harfe duyarlı) bir otomatik tamamlama menüsü sağlar:

![IntelliSense otomatik tamamlama menüsü](media/intellisense-auto-complete-menu.png)

Seçeneklerin nasıl **ayarlanır?** seçeneğine bağlı olarak  **Sekme** tuşuna basılarak (veya Enter veya Boşluk) açılan menüye seçilen öğeyi ekler. Seçimi ok tuşlarıyla değiştirebilirsiniz.

IntelliSense ayrıca R nesnelerinin üyeleri için öneriler sağlar:

![Nesne üyeleri için IntelliSense önerileri](media/intellisense-auto-complete-r-objects.png)

**ESC tuşuna** basılarak menü tamamen açılır. Ctrl Tuşu ile yeniden + **açabilirsiniz.**

Bir işlev `(` çağrısının açılışını yazmak kapanışı `)` ekler ve daha önce gösterildiği gibi imza yardımı getirir:

![Bir işlev için IntelliSense imzası yardımı](media/intellisense-function-signature.png)

ESC **tekrar** açılır pencereyi sildi; işlev imzaları için **Ctrl** Shift Tuşu ile yeniden +  + **açabilirsiniz.**

> [!Tip]
> Parametre, metnin altındaki metni karartmanıza yardımcı olursa, parametre yardım metninin saydam hale geldi **ctrl** tuşuna basın ve basılı tutun.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Kullanıcı tanımlı işlevler ve değişkenler için IntelliSense

IntelliSense, ad-parametre tamamlama da dahil olmak üzere aynı dosyada kullanıcı tanımlı işlevler için geçerlidir:

![Kullanıcı tanımlı işlevler için IntelliSense](media/intellisense-same-file-functions.png)

![Kullanıcı tanımlı işlevler için IntelliSense parametre tamamlama](media/intellisense-parameter-completion.png)

IntelliSense aynı dosyada ve geçerli oturumda yer alan değişkenler için de geçerlidir:

![IntelliSense değişken tamamlama](media/intellisense-variable-completion.png)

> [!Note]
> Etkileşimli pencerede IntelliSense yalnızca geçerli R oturumundaki adları dikkate alıyor ve projenizin dosyalarını yoksayıyor.

## <a name="code-suggestions"></a>Kod önerileri

Kenar boşluğunda bir ampul (akıllı etiket olarak adlandırılan) Visual Studio yaygın olarak kullanılan bir eylem için bir kısayol olduğunu öneren bir durum vardır. Örneğin, bir ampul görmek için düzenleyicide `library` deyimi içeren bir satırın üzerine gelin. Ampul seçerek kullanılabilir seçenekler görüntülenir:

![Düzenleyicide R için akıllı etiketler](media/intellisense-smart-tags.png)
