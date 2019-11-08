---
title: Erişilebilirlik
description: Bu makalede Mac için Visual Studio erişilebilirlik özellikleri ve bunların nasıl etkinleştiribilecekleri açıklanır.
author: conceptdev
ms.author: crdun
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 19104cb090ff2a115afefe994bd53c93d2baaf5d
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714428"
---
# <a name="accessibility"></a>Erişilebilirlik

MacOS 'taki özellik ve yardımcı programlara ek olarak, Mac için Visual Studio aşağıdaki özelliklere sahiptir ve Engelli kişiler için daha erişilebilir hale getirir:

- Çözüm ve düzenleyici defterlerindeki metin büyütme
- Düzenleyicilerde metin boyutu seçenekleri
- Düzenleyicilerde renk özelleştirmesi
- Klavye kısayolu özelleştirmesi
- Yöntemler ve parametreler için kod tamamlama

MacOS 'taki erişilebilirlik özellikleri hakkında daha fazla bilgi için [Apple 'ın Web sitesine](https://www.apple.com/accessibility/mac/)bakın.

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Mac için Visual Studio erişilebilirlik özelliklerini kullanma

Mac için Visual Studio erişilebilirlik özellikleri varsayılan olarak kapalıdır. Bunları etkinleştirmek için aşağıdaki adımları uygulayın:

1. **Diğer > erişilebilirliği > Visual Studio > tercihleri**' ne gidin.

2. Aşağıdaki diyagramda gösterildiği gibi **erişilebilirliği etkinleştir** onay kutusunu seçin:

    ![Erişilebilirlik onay kutusunu Etkinleştir](media/accessibility-image1.png)

3. Erişilebilirlik özelliklerinin etkili olması için **Visual Studio 'Yu yeniden Başlat** düğmesine basın.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırını da kullanabilirsiniz. Bunu yapmak için terminalde aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Erişilebilirliği etkinleştirdikten sonra Visual Studio 'Yu yeniden başlatmanız gerekir.

## <a name="how-to-use-keyboard-navigation"></a>Nasıl yapılır: klavye gezintisini kullanma

Klavye gezintisi, **sistem tercihleri > klavye > kısayolları** **Tüm denetimlerine**ayarlanarak etkinleştirilebilir:

![MacOS 'ta sistem tercihleri paneli](media/accessibility-image2.png)

Tam klavye erişimi ayarı odak dikdörtgenini açar. Ardından, kullanarak denetimleri seçebilirsiniz:

- Denetimlerle ileri git sekmesi
- Denetimlerle geriye doğru gitmek için SHIFT-TAB
- Okların yönündeki denetimler arasında hareket etmek için ok tuşları.

Boşluk çubuğuna basıldığında odaklanmış denetim etkinleştirilir.

## <a name="how-to-enable-and-use-voice-over"></a>Nasıl yapılır: sesi etkinleştirme ve kullanma

VoiceOver aç veya **Kapat düğmesine basın**

UI VoiceOver komutlarıyla gezinmek için aşağıdaki komutları kullanın:

- VoiceOver imlecini denetimler arasında taşı: **Ctrl + alt + sol ok tuşu/sağ ok tuşu**

   VoiceOver, denetimlerin adını, onunla ilgili bazı ayrıntıları ve bununla yapabileceklerinizi okur.

- Grupları ve denetimleri girin (Çözüm Bölmesi, araç kutusu ve diğer Pad 'ler gibi): **CTRL + ALT + SHIFT + aşağı ok**

   Bir denetimin içinde bir kez, içinde gezinmek için **Ctrl + Alt + ok** tuşlarını kullanabilirsiniz.

MacOS 'ta VoiceOver kullanma hakkında genel bilgi için aşağıdaki kılavuzlara bakın:

- [VoiceOver kullanmaya başlama](https://help.apple.com/voiceover/info/guide/10.12/)
- [MacOS içindeki VoiceOver komutları](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'nun erişilebilirlik özellikleri (Windows üzerinde)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)