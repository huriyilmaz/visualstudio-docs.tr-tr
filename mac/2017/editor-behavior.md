---
title: Kod biçimlendirme
description: bu makalelerde Mac için Visual Studio ' deki metin düzenleyicisi davranışını değiştirmek için kullanılabilecek çeşitli seçenekler açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 416906adf21beee8849d2aae38489d8d212f2f3bfd9982a2c6f11dae94cad064
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121313750"
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
