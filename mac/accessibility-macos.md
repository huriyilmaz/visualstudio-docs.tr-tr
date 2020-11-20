---
title: MacOS erişilebilirlik seçeneklerini kullanma
description: MacOS erişilebilirlik seçeneklerini ve yüksek karşıtlık, klavye gezintisi ve VoiceOver gibi özellikleri kullanma
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998392"
---
# <a name="accessibility-features-of-macos"></a>MacOS erişilebilirlik özellikleri

macOS, kullanıcıların değişen yetenekler konusunda yardımcı olacak çok sayıda özelliği olan erişilebilir bir işletim sistemidir. Bu özellikler arasında yüksek karşıtlık modu, klavye gezintisi ve VoiceOver (macOS ekran okuyucusu) bulunur.

## <a name="enable-accessibility-features"></a>Erişilebilirlik özelliklerini etkinleştir

Mac için Visual Studio, yardımcı teknolojiler için destek varsayılan olarak kapalıdır. Erişilebilirlik desteğini etkinleştirmek için:

1. **Visual Studio (menü)**  >  **tercihleri**  >  **Other**' ne gidin ve **Erişilebilirlik**' i seçin.

1. **Erişilebilirliği etkinleştir** onay kutusunu seçin.

   ![Erişilebilirliği etkinleştir seçiliyken erişilebilirlik tercihlerinin ekran görüntüsü](media/accessibility-preferences.png)

1. Apple 'ın yardımcı teknolojileri desteğini etkinleştirmek için **Visual Studio 'Yu yeniden Başlat** ' ı seçin.

Alternatif olarak, erişilebilirlik özelliklerini etkinleştirmek için komut satırını da kullanabilirsiniz. Bunu yapmak için terminalde aşağıdaki komutu girin:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Bu ayarı komut satırı ile değiştirdikten sonra, Visual Studio 'Yu yeniden başlatmanız gerekir.

## <a name="increase-the-contrast-in-macos"></a>MacOS 'taki karşıtlığı artırma

Mac için Visual Studio macOS 'ta artan karşıtlığı destekler, UI öğelerinin kontrastını artırır ve anahatlar daha fazla tanımlanmış hale getirir. Bunu etkinleştirmek için:

1. **Sistem tercihlerini** açın.

1. **Erişilebilirlik**' e gidin ve **görüntüle**' yi seçin.

1. **Karşıtlığı artır** onay kutusunu seçin.
