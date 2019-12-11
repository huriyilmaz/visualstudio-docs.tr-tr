---
title: Kod biçimlendirme
description: Bu makalelerde Mac için Visual Studio ' deki metin Düzenleyicisi davranışını değiştirmek için kullanılabilecek çeşitli seçenekler açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: dca21119a73c03b63a273f7b4c22d70ecdb2a583
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984675"
---
# <a name="editor-behavior"></a>Düzenleyici Davranışı

Düzenleyici davranışları kodun yazıldığı şekilde biçimlendirilmesini sağlamak üzere ayarlanabilir. Bu eylemler **Visual Studio > tercihleri > metin düzenleyicisi > davranışı**altında ayarlanır ve daha yaygın olarak kullanılan işlevlerden bazıları aşağıda açıklanmıştır:

![Düzenleyici davranış seçenekleri](media/source-editor-image9.png)

* Yeni sınıflar, Yöntemler veya özellikler oluşturulurken, eşleşen kapatma ayraçları koda otomatik olarak eklenebilir. Bu seçenek belirlendiğinde `{` yazmak `}`otomatik olarak eklenir.
* Anında kod biçimlendirme, ayarlanan biçimlendirme tercihlerine benzeyen noktalı virgül veya küme ayraçları gibi karakter basışları tarafından tetiklenir.
* Ayrıca, dosyayı kaydederken biçimlendirmeyi seçebilirsiniz, bu da kod yazılmasına izin verir ve mevcut tercihlerde ayarlanan kodu biçimlendirmek için IDE 'yi sorumlu halde bırakır.
* Girintileme None, Auto veya Smart olarak ayarlanabilir. Bunlar şunları yapın:
  * Hiçbiri-giriş işaretini sonraki satırın başlangıcına ayarlar
  * Giriş işaretini bir sonraki satırda aynı sütuna otomatik olarak ayarlar
  * Kodu temel alarak aşağıdaki satırdaki akıllı girintiler
* Sözcük bölme davranışı, OSE 'ler arasında farklılık gösterir ve gezinme amacıyla, metin Düzenleyicisi 'nin sözcüklerin başlayacağı veya bitiş zamanlarını bilmeleri gerekir. Biçimlendirme UNIX veya Windows olarak ayarlanabilir.

XML, CSS, HTML ve JSON için biçimlendirme kuralları da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod stili tercihleri (Windows üzerinde Visual Studio)](/visualstudio/ide/code-styles-and-quick-actions)
