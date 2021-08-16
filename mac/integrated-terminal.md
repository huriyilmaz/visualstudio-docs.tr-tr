---
title: Mac için Visual Studio – Tümleşik Terminal
description: Mac için Visual Studio'da Tümleşik Terminal ile çalışma.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: 0dd93498967139083ed8828ee6d6757db52584874b9c93855604d06b8c6eacd0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407354"
---
# <a name="integrated-terminal"></a>Tümleşik Terminal
Bu Mac için Visual Studio başlangıçta çözümünün kökünden başlayarak tümleşik bir terminal penceresi açabilirsiniz. Terminal ön uç görevlerini (npm, ng veya vue gibi) çalıştırma, kapsayıcıları yönetme, gelişmiş git komutları çalıştırma, Entity Framework komutlarını yürütme, dotnet CLI çıkışını görüntüleme, NuGet paketleri ekleme gibi farklı durumlar için yararlı olabilir. 

Terminali açmak için:
- Terminal penceresini göstermek veya gizlemek için **Ctrl + '** klavye kısayolunu kullanın.
- Terminali **Görüntüle** \> **menüsünü** kullanın.
- Arama **çubuğundan terminal** komutunu kullanın.

![*Mac için Visual Studio hemen sonra tümleşik terminal. *](media/integrated-terminal-intro.png)

Varsayılan olarak, terminali başlattığında şu şekilde olur:
- Çalışma dizinini geçerli çözümün yoluna ayarlayın.
- Varsayılan sistem kabuğunu yükleme.

## <a name="search"></a>Arayın
Ara ve **Bul...** menüsünü kullanarak terminal penceresinin > arayabilirsiniz.

![*Tümleşik Terminalde Mac için Visual Studio deneyimi*](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Terminal Klavye Kısayolları
|Komutlar|Klavye kısayolları|
|-|-|
|Terminal penceresini gösterme/gizleme|**Ctrl+ '**|
|Yeni terminal örneği oluşturma|**Ctrl+'**|
|Sayfayı yukarı kaydır|**PageUp**|
|Sayfayı aşağı kaydırma|**PageDown**|
|Daha önce kullanılan komutlarda döngü|**↓**, **↓**|
|Yazı tipi boyutunu büyüt|**⌘+**|
|Yazı tipi boyutunu küçült|**⌘-**|

## <a name="multiple-instances"></a>Birden çok örnek
Terminalin birden çok örneği herhangi bir zamanda çalışıyor olabilir. **Ctrl+'** klavye kısayolunu kullanarak yeni bir örnek oluşturabilirsiniz. Örnekler arasında geçiş yapmak için her örneğin sekmesine tıklar veya **Ctrl+sekme** kısayolunu kullanarak pencere seçici iletişim kutusunu kullanabilirsiniz.

![*Birden çok terminal örneği Mac için Visual Studio*](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Terminal penceresini özelleştirme
### <a name="configuring-the-terminal-font"></a>Terminal Yazı Tipini Yapılandırma
Tercihler ve Ortam ayarları ve Yazı Tipleri bölmesinde Terminal İçeriği için kullanılan yazı > > değiştirebilirsiniz. Varsayılan olarak yazı tipi, Menlo Normal ve 11 Çıkış Penceresi İçerikler ile aynı olur. Düzenleyici yazı tipinize bakarak istediğiniz yazı tipine göre değiştirebilirsiniz.

![*Tümleşik terminal için yazı tipi ayarlarını özelleştirme*](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Sistem terminali özelleştirmelerini yeniden kullanılabilir
Tümleşik terminal, macOS sistem terminali ile aynı varsayılanları ve yapılandırmayı kullanır. Bu, terminal özelleştirmeleriniz (zsh, ah-my-zsh vb.) tümleşik terminalde de çalışır.
