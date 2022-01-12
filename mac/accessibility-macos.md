---
title: macOS erişilebilirlik seçeneklerini kullanma
description: MacOS erişilebilirlik seçeneklerini ve yüksek karşıtlık, klavye gezintisi ve VoiceOver gibi özellikleri kullanma
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: c581a1ec20734dd1d9292589b07853cb5a6136a1
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806397"
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
