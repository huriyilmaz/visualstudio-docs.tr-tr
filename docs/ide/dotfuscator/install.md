---
title: Dotfuscator Community’yi yükleme
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, free, Visual Studio 2017, Visual Studio 2019, Visual Studio, install
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Visual Studio'da yer alan Dotfuscator Community'nin ücretsiz kopyasını nasıl yükleyebilirsiniz öğrenin.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: bb659976126713a11594ad1b4aeb536510744c38
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596820"
---
# <a name="install-dotfuscator-community"></a>Dotfuscator Community’yi yükleme

Dotfuscator Community Visual Studio'nun isteğe bağlı bir bileşenidir.
Bu yönergeler nasıl yüklenir açıklayınız.

> [!NOTE]
> Visual Studio sürümleri ile gönderilen Dotfuscator Topluluk sürümlerine ek olarak, PreEmptive Solutions da periyodik kendi web sitesinde güncelleştirilmiş sürümleri sağlar.
> Visual Studio'dan yüklemek yerine **en son sürümü** doğrudan indirmek istiyorsanız, **[Dotfuscator İndirmeler sayfasına gitmek için buraya tıklayın.][download]**

## <a name="within-visual-studio"></a>Visual Studio içinde

::: moniker range="vs-2019"

Visual Studio IDE'den Dotfuscator Topluluğu'nu yükleyebilirsiniz:

1. Arama **Kutusuna** (Ctrl+Q) `dotfuscator`yazın. <br/> <br/> ![Arama Kutusu](media/install_in_vs19_12.png) <br/> <br/>

2. Gösterilen arama sonuçlarında, *Bileşenler* başlığı **altında, PreEmptive Protection - Dotfuscator'u seçin.**
   * Bunun yerine, *Menüler* başlığı altında, **PreEmptive Koruma - Dotfuscator Topluluk,** sonra Dotfuscator Topluluk zaten yüklenir bakın. [Başlamak][get-started]için bu seçeneği seçin.

3. Bir Visual Studio Installer penceresi başlatacak, önceden Dotfuscator Topluluk yüklemek için yapılandırılmış.
   > [!NOTE]
   > Devam etmek için yönetici kimlik bilgilerini sağlamanız gerekebilir.

4. Visual Studio Yükleyici penceresinde *Yükle'yi*tıklatın. <br/> <br/> ![Yükle'ye tıklayın](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Visual Studio IDE'den Dotfuscator Topluluğu'nu yükleyebilirsiniz:

1. Hızlı **Başlatma** (Ctrl+Q) arama `dotfuscator`çubuğunda. <br/> <br/> ![Hızlı Başlat](media/install_from_vs_12.png) <br/> <br/>

2. Gösterilen Hızlı Başlatma sonuçlarında, *Yükle* başlığı altında **PreEmptive Protection - Dotfuscator (Bireysel Bileşen)** seçeneğini belirleyin.
   * Bunun yerine, *Menüler* başlığı altında, **Araçlar - PreEmptive Koruma - Dotfuscator,** sonra Dotfuscator CE zaten yüklü görürseniz. [Başlamak][get-started]için bu seçeneği seçin.

3. Bir Visual Studio Installer pencere başlatacak, önceden Dotfuscator CE yüklemek için yapılandırılmış.
   > [!NOTE]
   > Devam etmek için yönetici kimlik bilgilerini sağlamanız gerekebilir.

4. Visual Studio Yükleyici penceresinde *Yükle'yi*tıklatın. <br/> <br/> ![Yükle'ye tıklayın](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Yükleme tamamlandıktan sonra [Dotfuscator Community'yi kullanmaya başlayabilirsiniz.][get-started]

## <a name="during-visual-studio-installation"></a>Görsel Stüdyo Kurulumu Sırasında

Visual Studio'yu henüz yüklemediyseniz, yükleyiciyi [Visual Studio web sitesinden edinebilirsiniz.][vs-install]
Çalıştırıldığında, seçilen Visual Studio sürümü için yükleme seçeneklerini görüntüler.

::: moniker range="vs-2019"

![Yükleme seçenekleri](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Yükleme seçenekleri](media/install_ui_17.png)

::: moniker-end

Daha sonra Visual Studio'nun bireysel bir bileşeni olarak Dotfuscator Topluluğu'nu yükleyebilirsiniz:

1. Bireysel **bileşenleri** sekmesini seçin.
2. *Kod araçları*altında, PreEmptive Protection kontrol edin *- Dotfuscator* öğesi.<br/> <br/> ![Tek tek bileşenler](media/install_individually_12.png) <br/> <br/>
3. *Özet* paneli, *Bireysel Bileşenler* bölümünün altında *PreEmptive Protection - Dotfuscator'u* görüntüler. <br/> <br/> ![Özet bölme](media/install_individually_3.png) <br/> <br/>
4. Ortamınız için uygun olan diğer yükleme ayarlarını yapılandırın.
5. Visual Studio'yu yüklemeye hazır olduğunuzda *Yükle* düğmesini tıklatın.

Yükleme tamamlandıktan sonra Dotfuscator Community'yi kullanmaya başlayabilirsiniz. Ayrıntılar için, bkz. [Tam kapsamlı Dotfuscator Community Kullanıcı Kılavuzu’nun Kullanmaya Başlama Sayfası][get-started].

## <a name="see-also"></a>Ayrıca bkz.

[Tam Dotfuscator Topluluk Kullanım Kılavuzu bu konu](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
