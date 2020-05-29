---
title: Mac için Visual Studio – tümleşik Terminal
description: Mac için Visual Studio, macOS 'ta iOS, Android, Mac ve Xamarin. Forms için ASP.NET Core Web siteleri ve Xamarin projeleri gibi .NET uygulamaları oluşturmaya yönelik tümleşik bir geliştirme ortamı sağlar.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185205"
---
# <a name="integrated-terminal"></a>Tümleşik Terminal
Mac için Visual Studio, başlangıçta çözümünüzün kökünde başlayan tümleşik bir Terminal penceresi açabilirsiniz. Terminal, ön uç görevleri (örneğin, NPM, NG veya Vue), kapsayıcıları yönetmek, gelişmiş git komutlarını çalıştırmak, Entity Framework komutları yürütmek, benzersiz CLı çıkışını görüntülemek, NuGet paketleri eklemek ve daha fazlası için farklı türlerde durumlar için yararlı olabilir. 

Terminali açmak için:
- Terminal penceresini göstermek veya gizlemek için **CTRL + '** klavye kısayolunu kullanın.
- **Görünüm** \> **bölmeleri** \> **Terminal** menüsünü kullanın.
- Arama çubuğundan **Terminal** komutunu kullanın.

![* Mac için Visual Studio tümleşik Terminal başlatıldıktan hemen sonra. *](media/integrated-terminal-intro.png)

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
|Yazı tipi boyutunu artır|**⌘ +**|
|Yazı tipi boyutunu azalt|**⌘**|

## <a name="multiple-instances"></a>Birden çok örnek
Her zaman terminalin birden çok örneği çalışıyor olabilir. **CTRL + '** klavye kısayolunu kullanarak yeni bir örnek oluşturabilirsiniz. Örnekler arasında geçiş yaparak her bir örneğin sekmesine tıklayın veya **CTRL + TAB** kısayolunu kullanarak pencere Seçici iletişim kutusunu kullanabilirsiniz.

![* Mac için Visual Studio * içindeki birden çok Terminal örneği](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Terminal penceresini özelleştirme
### <a name="configuring-the-terminal-font"></a>Terminal yazı tipini yapılandırma
Terminal Içerikleri için kullanılan yazı tipini ve boyutunu, Tercihler > ortam > yazı tipleri bölmesinde değiştirebilirsiniz. Varsayılan olarak, yazı tipi çıkış paneli Içeriğiyle aynı olacaktır. Menlo normal, boyut 11 kullanılarak. Düzenleyici yazı yazılarınızın bağımsız bir yazı tipine ayarlayabilirsiniz.

![* Tümleşik Terminal için yazı tipi ayarlarını özelleştirme *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Sistem Terminali özelleştirmelerini yeniden kullanma
Tümleşik Terminal, macOS sistem terminalinize göre aynı Varsayılanları ve yapılandırmayı kullanır. Yani, Terminal özelleştirmeleriniz (ZSH, Oh-My-ZSH vb.) tümleşik terminalde de çalışır.
