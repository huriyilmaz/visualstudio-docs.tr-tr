---
title: Kodlama ve satır sonu karakterleri
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6448b553c1da9e697bca3860cb8507727c99cc08
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588596"
---
# <a name="encodings-and-line-endings"></a>Kodlamalar ve çizgi uçları

Aşağıdaki karakterler Visual Studio'da satır sonu olarak yorumlanır:

- CR LF: Taşıma döndürme + satır beslemesi, Unicode karakterleri 000D + 000A

- LF: Satır besleme, Unicode karakter 000A

- NEL: Sonraki satır, Unicode karakter 0085

- LS: Çizgi ayırıcı, Unicode karakter 2028

- PS: Paragraf ayırıcı, Unicode karakter 2029

Diğer uygulamalardan kopyalanan metin özgün kodlama ve satır sonu karakterlerini tutar. Örneğin, Not Defteri'nden metni kopyalayıp Visual Studio'daki bir metin dosyasına yapıştırdığınızda, metin Not Defteri'ndekiyle aynı ayarlara sahiptir.

Farklı satır sonu karakterleri olan bir dosyayı açtığınızda, tutarsız satır sonu karakterlerinin normalleştirilmesi gerekip gerekmediğini ve hangi satır türünün seçileceğini soran bir iletişim kutusu görebilirsiniz.

## <a name="advanced-save-options"></a>Gelişmiş kaydetme seçenekleri

İstediğiniz satır sonu karakterlerinin türünü belirlemek için **Dosya** > **Gelişmiş Kaydet Seçenekleri** iletişim kutusunu kullanabilirsiniz. Aynı ayarlara sahip bir dosyanın kodlamasını da değiştirebilirsiniz.

![Gelişmiş Kaydet Seçenekleri iletişim kutusu](media/line_endings.png)

> [!NOTE]
> **Dosya** menüsünde **Gelişmiş Kaydet Seçeneklerini** görmüyorsanız, ekleyebilirsiniz. **Araçlar'ı**seçin, **Özelleştirin**ve ardından **Komutlar** sekmesini seçin. Menü **çubuğu** açılır listesinde **Dosya'yı**seçin ve ardından **Komut Ekle** düğmesini seçin. Komut **Ekle** iletişim kutusunda, **Kategoriler**altında **Dosya'yı**seçin ve ardından **Komutlar** listesinde **Gelişmiş Kaydet Seçenekleri'ni**seçin. **Tamam'ı** seçin ve ardından komutu menüdeki herhangi bir yere taşımak için **Aşağı Taşı** düğmesini seçin. **Özelleştir** iletişim kutusunu kapatmak için **Kapat'ı** seçin. Daha fazla bilgi için [menüleri ve araç çubuklarını özelleştir'e](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu)bakın.
>
> Alternatif olarak, **Dosya** > **Kaydet \<dosyasını\> As'ı**seçerek Gelişmiş **Kaydet Seçenekleri** iletişim kutusuna erişebilirsiniz. **Dosyayı Kaydet** iletişim kutusunda, **Kaydet** düğmesinin yanındaki açılır üçgeni seçin ve **kodlama yla Kaydet'i**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
