---
title: Kod biçimlendirme
description: Bu makale, Mac için Visual Studio metin düzenleyicisi davranışını değiştirmek için kullanılabilecek çeşitli seçenekleri açıklar
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: dca21119a73c03b63a273f7b4c22d70ecdb2a583
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984675"
---
# <a name="editor-behavior"></a>Düzenleyici Davranışı

Düzenleyici davranışları, kodun yazıldığı gibi biçimlendirilmesine izin verecek şekilde ayarlanabilir. Bu eylemler **Visual Studio > Tercihleri > Metin Düzenleyici> Davranışı**altında ayarlanır ve daha sık kullanılan işlevlerden bazıları aşağıda açıklanmıştır:

![Düzenleyici Davranış seçenekleri](media/source-editor-image9.png)

* Yeni sınıflar, yöntemler veya özellikler oluştururken eşleşen kapanış ayraçları koda otomatik olarak eklenebilir. Bu seçenek seçildiğinde, `{` yazma otomatik `}`olarak .
* Anında kod biçimlendirme, ayarlanan biçimlendirme tercihlerini taklit edecek yarı-iki nokta üst üste veya parantez gibi karakter baskıları tarafından tetiklenir.
* Ayrıca, kodu kaydederken biçimlendirmeyi seçebilirsiniz, bu da kodun istenilen şekilde yazılmasına izin verir ve Kodu varolan tercihlere göre ayarlandığı şekilde biçimlendirmekten IDE'yi sorumlu bırakır.
* Girintisi Yok, Otomatik veya Akıllı olarak ayarlanabilir. Bunlar aşağıdakileri yapar:
  * Yok - bir sonraki satırın başlangıcına caret ayarlar
  * Otomatik - bir sonraki satırda aynı sütuna caret ayarlar
  * Akıllı - koda dayalı aşağıdaki satırdaki girintiler
* Sözcük kırma davranışı, OS'ler arasında farklılık gösterir ve gezinme amacıyla metin düzenleyicisinin sözcüklerin nerede başladığını veya nerede bitdiğini bilmesi gerekir. Biçimlendirme Unix veya Windows olarak ayarlanabilir.

XML, CSS, HTML ve JSON için biçimlendirme kuralları da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod stili tercihleri (Windows'ta Visual Studio)](/visualstudio/ide/code-styles-and-quick-actions)
