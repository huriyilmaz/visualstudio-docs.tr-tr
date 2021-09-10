---
title: Kod biçimlendirme
description: Bu makalelerde, bu makalede metin düzenleyicisi davranışını değiştirmek için kullanılan çeşitli Mac için Visual Studio
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 20363d5497ea5897cb2685ca838da44b8c21d3df
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964771"
---
# <a name="editor-behavior"></a>Düzenleyici Davranışı

Düzenleyici davranışları, kodun yazıldığı şekilde biçimlendir biçimlendirilmiş olmasına izin verecek şekilde yalıtabilir. Bu eylemler Visual Studio > **Tercihler > Metin > Davranışı** altında ayarlanır ve yaygın olarak kullanılan işlevlerden bazıları aşağıda açıklanmıştır:

![Düzenleyici Davranışı seçenekleri](media/source-editor-image9.png)

* Eşleşen kapanış ayraçları yeni sınıflar, yöntemler veya özellikler oluşturulurken koda otomatik olarak eklenebilir. Bu seçenek seçildiğinde, yazarak `{` otomatik olarak `}` eklenir.
* Hazırda kod biçimlendirmesi, noktalı virgül veya küme ayraçları gibi ayarlanmış biçimlendirme tercihlerine öykünecek karakter basmaları tarafından tetiklenir.
* Dosyayı kaydederek biçimlendirmeyi de tercih edersiniz. Bu sayede istediğiniz gibi kod yazabilir ve IDE'yi mevcut tercihler tarafından ayar olarak kod biçimlendirme sorumluluğunda bırakır.
* Girinti yok, Otomatik veya Akıllı olarak ayarlanmış olabilir. Bunlar şunları yapar:
  * Hiçbiri - baş çizgiyi sonraki satırın başlangıcına ayarlar
  * Otomatik - bir sonraki satırda aynı sütuna köşeyi ayarlar
  * Akıllı - koda göre aşağıdaki satırda girintiler
* Sözcük sonu davranışı işletim sistemleri arasında farklılık gösterir ve gezinti amacıyla metin düzenleyicisinin sözcüklerin nereden başlayacağını veya sona erer olduğunu biliyor olması gerekir. Biçimlendirme Unix veya Windows.

XML, CSS, HTML ve JSON için biçimlendirme kuralları da oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod stili tercihleri (Visual Studio Windows)](/visualstudio/ide/code-styles-and-quick-actions)
