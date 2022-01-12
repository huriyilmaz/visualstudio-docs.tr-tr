---
title: Kod biçimlendirme
description: bu makalelerde Mac için Visual Studio ' deki metin düzenleyicisi davranışını değiştirmek için kullanılabilecek çeşitli seçenekler açıklanmaktadır
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/06/2018
ms.topic: reference
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: ed82e0cf2e0ecb1694cffccde56d984ddd85bf8b
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803654"
---
# <a name="editor-behavior"></a>Düzenleyici Davranışı

Düzenleyici davranışları kodun yazıldığı şekilde biçimlendirilmesini sağlamak üzere ayarlanabilir. bu eylemler, **Visual Studio > tercihleri > metin düzenleyicisi > davranışı** altında ayarlanır ve daha yaygın olarak kullanılan işlevlerden bazıları aşağıda açıklanmıştır:

![Düzenleyici davranış seçenekleri](media/source-editor-image9.png)

* Yeni sınıflar, Yöntemler veya özellikler oluşturulurken, eşleşen kapatma ayraçları koda otomatik olarak eklenebilir. Bu seçenek belirlendiğinde, yazma `{` otomatik olarak eklenir `}` .
* Anında kod biçimlendirme, ayarlanan biçimlendirme tercihlerine benzeyen noktalı virgül veya küme ayraçları gibi karakter basışları tarafından tetiklenir.
* Ayrıca, dosyayı kaydederken biçimlendirmeyi seçebilirsiniz, bu da kod yazılmasına izin verir ve mevcut tercihlerde ayarlanan kodu biçimlendirmek için IDE 'yi sorumlu halde bırakır.
* Girintileme None, Auto veya Smart olarak ayarlanabilir. Bunlar şunları yapın:
  * Hiçbiri-giriş işaretini sonraki satırın başlangıcına ayarlar
  * Giriş işaretini bir sonraki satırda aynı sütuna otomatik olarak ayarlar
  * Kodu temel alarak aşağıdaki satırdaki akıllı girintiler
* Sözcük bölme davranışı, OSE 'ler arasında farklılık gösterir ve gezinme amacıyla, metin Düzenleyicisi 'nin sözcüklerin başlayacağı veya bitiş zamanlarını bilmeleri gerekir. Biçimlendirme, Unix veya Windows olarak ayarlanabilir.

XML, CSS, HTML ve JSON için biçimlendirme kuralları da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [kod stili tercihleri (Windows Visual Studio)](/visualstudio/ide/code-styles-and-quick-actions)
