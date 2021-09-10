---
title: macOS erişilebilirlik seçeneklerini kullanma
description: MacOS erişilebilirlik seçeneklerini ve yüksek karşıtlık, klavye gezintisi ve VoiceOver gibi özellikleri kullanma
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964743"
---
# <a name="accessibility-features-of-macos"></a>macOS'un erişilebilirlik özellikleri

macOS, çeşitli özelliklere sahip kullanıcılara yardımcı olacak çeşitli özelliklere sahip erişilebilir bir işletim sistemidir. Bu özellikler arasında yüksek karşıtlık modu, klavye gezintisi ve VoiceOver (macOS ekran okuyucusu) yer alır.

## <a name="enable-accessibility-features"></a>Erişilebilirlik özelliklerini etkinleştirme

Bu Mac için Visual Studio yardımcı teknolojiler için destek varsayılan olarak kapalıdır. Erişilebilirlik desteğini etkinleştirmek için:

1. Visual Studio **(menü) Tercihler**  >  **Diğer'e**  >  **gidin ve** Erişilebilirlik'i **seçin.**

1. Erişilebilirliği **Etkinleştir onay** kutusunu seçin.

   ![Erişilebilirliği Etkinleştir'in seçili olduğu Erişilebilirlik Tercihleri'nin ekran görüntüsü](media/accessibility-preferences.png)

1. **Apple'Visual Studio** yardımcı teknolojileri için desteği etkinleştirmek için Yeniden Başlat'ı seçin.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırı kullanabilirsiniz. Bunu yapmak için terminale aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Bu ayarı komut satırı aracılığıyla değiştirdikten sonra, bu ayarı yeniden başlatmanız Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>macOS'ta karşıtlığı artırma

Mac için Visual Studio macOS'ta daha fazla karşıtlığı destekler, kullanıcı arabirimi öğelerinin karşıtlıkını artırır ve ana hatları daha tanımlı hale gelir. Bunu etkinleştirmek için:

1. Sistem **Tercihleri'ne açın.**

1. **Erişilebilirlik'e gidin** ve Görüntüle'yi **seçin.**

1. **Karşıtlığı artır onay** kutusunu seçin.
