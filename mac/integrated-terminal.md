---
title: Mac için Visual Studio – tümleşik Terminal
description: Mac için Visual Studio içinde tümleşik terminalle çalışma.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/14/2020
ms.topic: how-to
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: c75c00a91ef826ef6000d5cd30f9740bda846030
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804278"
---
# <a name="integrated-terminal"></a>Tümleşik Terminal
Mac için Visual Studio, başlangıçta çözümünüzün kökünde başlayan tümleşik bir terminal penceresi açabilirsiniz. terminal, ön uç görevleri (örneğin: npm, ng veya vue), kapsayıcıları yönetmek, gelişmiş git komutlarını çalıştırmak, Entity Framework komutları yürütmek, dotnet clı çıkışını görüntülemek, NuGet paketleri eklemek ve daha fazlasını yapmak için farklı durumlarda yararlı olabilir. 

Terminali açmak için:
- Terminal penceresini göstermek veya gizlemek için **CTRL + '** klavye kısayolunu kullanın.
- **Görünüm** \> **terminali** menüsünü kullanın.
- Arama çubuğundan **Terminal** komutunu kullanın.

![* Mac için Visual Studio tümleşik terminal başlatıldıktan hemen sonra. *](media/integrated-terminal-intro.png)

Varsayılan olarak, Terminal başlatıldığında şu şekilde olur:
- Çalışma dizinini geçerli çözümün yolu olarak ayarlayın.
- Varsayılan sistem kabuğunu yükleyin.

## <a name="search"></a>Arama
Terminal penceresinin içeriğinde **arama > bul...** menüsünü kullanarak arama yapabilirsiniz.

![* Mac için Visual Studio tümleşik terminalde arama deneyimi *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Terminal klavye kısayolları
|Komutlar|Klavye kısayolları|
|-|-|
|Terminal penceresini göster/gizle|**CTRL + '**|
|Yeni Terminal örneği oluştur|**CTRL + '**|
|Sayfayı yukarı kaydır|**PageUp**|
|Sayfayı aşağı kaydır|**PageDown**|
|Daha önce kullanılan komutlarla geçiş yapın|**↑**, **↓**|
|Yazı tipi boyutunu büyüt|**⌘ +**|
|Yazı tipi boyutunu küçült|**⌘**|

## <a name="multiple-instances"></a>Birden çok örnek
Her zaman terminalin birden çok örneği çalışıyor olabilir. **CTRL + '** klavye kısayolunu kullanarak yeni bir örnek oluşturabilirsiniz. Örnekler arasında geçiş yaparak her bir örneğin sekmesine tıklayın veya **CTRL + TAB** kısayolunu kullanarak pencere Seçici iletişim kutusunu kullanabilirsiniz.

![* Mac için Visual Studio * içindeki birden çok terminal örneği](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Terminal penceresini özelleştirme
### <a name="configuring-the-terminal-font"></a>Terminal yazı tipini yapılandırma
Terminal Içerikleri için kullanılan yazı tipini ve boyutunu, Tercihler > ortam > yazı tipleri bölmesinde değiştirebilirsiniz. Varsayılan olarak, yazı tipi, Menlo normal, boyut 11 kullanılarak Çıkış Penceresi Içeriğiyle aynı olacaktır. Düzenleyici yazı yazılarınızın bağımsız bir yazı tipine ayarlayabilirsiniz.

![* Tümleşik Terminal için yazı tipi ayarlarını özelleştirme *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Sistem Terminali özelleştirmelerini yeniden kullanma
Tümleşik Terminal, macOS sistem terminalinize göre aynı Varsayılanları ve yapılandırmayı kullanır. Yani, Terminal özelleştirmeleriniz (ZSH, Oh-My-ZSH vb.) tümleşik terminalde de çalışır.
