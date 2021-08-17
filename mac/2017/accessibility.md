---
title: Erişilebilirlik
description: Bu makalede, Mac için Visual Studio özellikleri ve nasıl etkinleştirilleri açıklanmıştır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.topic: overview
ms.openlocfilehash: 889003b822026ac5418e482a0817cc0b9c09d453100dd713e0efd512ce97932d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423272"
---
# <a name="accessibility"></a>Erişilebilirlik

macOS'ta özelliklere ve yardımcı Mac için Visual Studio ek olarak, Mac için Visual Studio engelli kişiler için daha erişilebilir hale geldi:

- Çözüm ve Düzenleyici Pad'lerde Metin Düzenleyici
- Düzenleyicilerde metin boyutu seçenekleri
- Düzenleyicilerde renk özelleştirme
- Klavye kısayolunu özelleştirme
- Yöntemler ve parametreler için kod tamamlama

macOS'ta erişilebilirlik özellikleri hakkında daha fazla bilgi için [Apple'ın web sitesine bakın.](https://www.apple.com/accessibility/mac/)

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Erişilebilirlik özelliklerini kullanma

Mac için Visual Studio erişilebilirlik özellikleri varsayılan olarak kapalıdır. Bunları etkinleştirmek için aşağıdaki adımları uygulayın:

1. Diğer Visual Studio > **Erişilebilirlik >'> gidin.**

2. Aşağıdaki **diyagramda** gösterildiği gibi Erişilebilirliği Etkinleştir onay kutusunu seçin:

    ![Erişilebilirliği etkinleştir onay kutusu](media/accessibility-image1.png)

3. Erişilebilirlik özelliklerinin **Visual Studio** için Yeniden Başlat düğmesine basın.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırı kullanabilirsiniz. Bunu yapmak için terminale aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Erişilebilirliği başlattıktan sonra yeniden başlatmanız Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Nasıl: Klavye gezintisini kullanma

Klavye gezintisi, Sistem Tercihleri'> Klavye > Tüm Denetimlere **Kısayollar'da Tam Klavye** Erişimi seçeneği **ayarlarak etkinleştirilebilir:**

![macos'ta sistem tercihleri paneli](media/accessibility-image2.png)

Tam klavye erişimi ayarı odak dikdörtgenini etkinleştirir. Ardından şunları kullanarak denetimleri seçin:

- Denetimler arasında ilerlemek için sekme
- Shift-Tab geriye doğru gitme
- Okların yönünde denetimler arasında hareket etmek için ok tuşları.

Boşluk çubuğuna basılarak odaklanmış denetim etkinleştirildi.

## <a name="how-to-enable-and-use-voice-over"></a>Nasıl: SesLendirmeyi etkinleştirme ve kullanma

VoiceOver'i açma veya kapatma **cmd + F5 tuşlarına basın**

VoiceOver kullanıcı arabirimi komutları arasında gezinmek için aşağıdaki komutları kullanın:

- VoiceOver imlecini Denetimler arasında taşıma: **Ctrl + Alt + Sol ok tuşu / Sağ ok tuşu**

   VoiceOver denetimlerin adını, bu denetimle ilgili bazı ayrıntıları ve bu denetimle neler yapalarını okur.

- Gruplar ve denetimler girin (Çözüm Bölmesi, Araç Kutusu ve diğer **Pad'ler** gibi): Ctrl + Alt + Shift + Aşağı Ok

   Bir denetimin içinde gezinmek için **Ctrl + Alt + Ok** tuşlarını kullanabilirsiniz.

macOS'ta VoiceOver kullanma hakkında genel bilgi için aşağıdaki kılavuzlara bakın:

- [Başlarken VoiceOver ile çalışma](https://help.apple.com/voiceover/info/guide/10.12/)
- [macOS'ta VoiceOver komutları](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio erişilebilirlik özellikleri (Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)