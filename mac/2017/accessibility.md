---
title: Erişilebilirlik
description: Bu makalede, Visual Studio for Mac'te erişilebilirlik özellikleri ve bunların nasıl etkinleştirilebileceği tanıtılır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: c0f056643a8cea0c9a5eca9801d2bd008e0793a8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79301687"
---
# <a name="accessibility"></a>Erişilebilirlik

MacOS'taki özelliklere ve yardımcı programlara ek olarak, Visual Studio for Mac aşağıdaki özelliklere sahiptir ve bu da engelli kişiler için daha erişilebilir hale getirir:

- Çözüm ve Editör Pedleri Metin Büyütme
- Editörlerde metin boyutu seçenekleri
- Editörlerde renk özelleştirme
- Klavye kısayol özelleştirme
- Yöntem ve parametreler için kod tamamlama

macOS'taki erişilebilirlik özellikleri hakkında daha fazla bilgi için [Apple'ın web sitesine](https://www.apple.com/accessibility/mac/)bakın.

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Erişilebilirlik özelliklerini kullanma

Mac için Visual Studio'daki Erişilebilirlik özellikleri varsayılan olarak kapatılır. Bunları etkinleştirmek için aşağıdaki adımları yapın:

1. Visual **Studio > Tercihleri > Diğer > Erişilebilirlik**gidin.

2. Aşağıdaki diyagramda gösterildiği gibi **Erişilebilirliği Etkinleştir** onay kutusunu seçin:

    ![Erişilebilirlik onay kutusunu etkinleştirme](media/accessibility-image1.png)

3. Erişilebilirlik özelliklerinin etkili olmasını sağlamak için **Visual Studio'yu Yeniden Başlat** düğmesine basın.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırını kullanabilirsiniz. Bunu yapmak için terminalde aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Erişilebilirliği alabilmeniz için Visual Studio'yı yeniden başlatmanız gerekir.

## <a name="how-to-use-keyboard-navigation"></a>Nasıl Yapılır: Klavye Gezintisini Kullanma

Klavye gezintisi, **Tüm Denetimlere**> **Klavye > > Kısayollarında** Tam Klavye Erişimi seçeneğini ayarlayarak etkinleştirilebilir:

![MacOS'ta sistem tercihleri paneli](media/accessibility-image2.png)

Tam klavye erişimini ayarlamak odak dikdörtgenini açar. Daha sonra denetimleri kullanarak seçebilirsiniz:

- Denetimler arasında ileri gitmek için sekme
- Kaydırma-Sekme denetimler arasında geriye gitmek için
- Okyönünde kontroller arasında taşımak için ok tuşları.

Boşluk çubuğuna basıldığında odaklanmış denetimi etkinleştirir.

## <a name="how-to-enable-and-use-voice-over"></a>Nasıl Kullanılır: Ses Lendirmeyi etkinleştirme ve kullanma

VoiceOver'ı açın veya kapatın **cmd + F5 tuşuna** basın

UI VoiceOver komutlarında gezinmek için aşağıdaki komutları kullanın:

- VoiceOver imlecini Denetimler arasında **taşıyın: Ctrl + Alt + Sol ok tuşu / Sağ ok tuşu**

   VoiceOver denetimlerin adını, bununla ilgili bazı ayrıntıları ve bununla neler yapabileceğinizi okur.

- Gruplar ve denetimler girin (Çözüm Defteri, Araç Kutusu ve diğer Pedler gibi): **Ctrl + Alt + Shift + Aşağı Ok**

   Bir denetimin içine girdikten sonra, **ctrl + Alt + Oklar'ı** kullanarak içinde hareket edebilirsiniz.

macOS'ta VoiceOver'ı kullanma hakkında genel bilgi için aşağıdaki kılavuzlara bakın:

- [VoiceOver ile Başlarken](https://help.apple.com/voiceover/info/guide/10.12/)
- [macOS'ta VoiceOver komutları](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'nun erişilebilirlik özellikleri (Windows'da)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)