---
title: F1 Yardım tuşunu değiştirme
description: F1 anahtar eşlemesinin nasıl yeniden eşlendiğini veya kaldırılacağını açıklar
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jmartens
ms.technology: vs-ide-general
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 817c281bfbed2e21d390bfcfc7fae1ff1023b0fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137359"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Visual Studio F1 Yardım tuşunu değiştirin

F1 Yardım hizmetinden farklı bir işlev için F1 tuşunu kullanmak istiyorsanız veya yalnızca F1 kullanarak yardım 'ı devre dışı bırakmak istiyorsanız, anahtar eşlemesini kaldırabilir veya değiştirebilirsiniz.

> [!IMPORTANT]
> Performans sorunları nedeniyle F1 yardımını devre dışı bırakmak istiyorsanız, Visual Studio güncelleştirmelerde F1 Yardım hizmetine yönelik geliştirmeleri test edebilmeniz için anahtar eşlemesini geçici olarak değiştirmenizi öneririz. Çoğu senaryoda F1, kod düzenleyicisinden dil anahtar kelimeleri ve API 'Ler için başvuru sayfalarını açmak ya da IDE 'deki Windows veya UI öğeleriyle ilişkili yardım sayfalarını açmak için kolay bir yoldur. Devre dışı bırakırsanız, Visual Studio içinden tüm kullanımlar için devre dışı bırakabilirsiniz.

**F1 yardımını devre dışı bırakmak için:**

1. Visual Studio ' de **araçlar**  >  **seçenekler**' i seçin ve ardından **ortam** altında **klavye**' yi seçin.

1. Komutları **içeren komutları göster** metin kutusunda, komutların görünümünü filtrelemek için **help. F1** yazın.

   ![F1 yardımını devre dışı bırak](../not-in-toc/media/disable-f1-help-key.png)

1. Anahtar eşlemesini kaldırmak için **Kaldır** ' ı seçin.

1. Kısayol tuşuna **basın** metin kutusunu seçin.

1. Klavyenizde, **alt + F1** gibi F1 yardımı için yeni bir anahtara veya tuş birleşimine basın, **ata**' yı seçin ve ardından **Tamam**' ı seçin.

Klavye kısayollarını ayarlama hakkında daha fazla bilgi için bkz. [klavye kısayollarını belirleme ve özelleştirme](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
