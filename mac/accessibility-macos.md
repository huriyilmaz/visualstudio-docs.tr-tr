---
title: MacOS erişilebilirlik seçeneklerini kullanma
description: MacOS erişilebilirlik seçeneklerini ve yüksek karşıtlık, klavye gezintisi ve VoiceOver gibi özellikleri kullanma
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: e03a4271ee81213ac387b58603acdb5053a50a524a741a4c60b50990ce0cd2f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121350008"
---
# <a name="accessibility-features-of-macos"></a>MacOS erişilebilirlik özellikleri

macOS, kullanıcıların değişen yetenekler konusunda yardımcı olacak çok sayıda özelliği olan erişilebilir bir işletim sistemidir. Bu özellikler arasında yüksek karşıtlık modu, klavye gezintisi ve VoiceOver (macOS ekran okuyucusu) bulunur.

## <a name="enable-accessibility-features"></a>Erişilebilirlik özelliklerini etkinleştir

Mac için Visual Studio, yardımcı teknolojiler için destek varsayılan olarak kapalıdır. Erişilebilirlik desteğini etkinleştirmek için:

1. **Visual Studio (menü)**  >  **tercihleri**  >  ' ne gidin ve **erişilebilirlik**' i seçin.

1. **Erişilebilirliği etkinleştir** onay kutusunu seçin.

   ![Erişilebilirliği etkinleştir seçiliyken erişilebilirlik tercihlerinin ekran görüntüsü](media/accessibility-preferences.png)

1. Apple 'ın yardımcı teknolojileri desteğini etkinleştirmek için **Visual Studio yeniden başlat** ' ı seçin.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırını da kullanabilirsiniz. Bunu yapmak için terminalde aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Bu ayarı komut satırı aracılığıyla değiştirdikten sonra Visual Studio yeniden başlatmanız gerekir.

## <a name="increase-the-contrast-in-macos"></a>MacOS 'taki karşıtlığı artırma

Mac için Visual Studio macos 'ta artan karşıtlığı destekler, uı öğelerinin kontrastını artırır ve anahatlar daha fazla tanımlanmış hale getirir. Bunu etkinleştirmek için:

1. **Sistem tercihlerini** açın.

1. **Erişilebilirlik**' e gidin ve **görüntüle**' yi seçin.

1. **Karşıtlığı artır** onay kutusunu seçin.
