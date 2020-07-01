---
title: Dotfuscator Community’yi yükleme
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive çözümleri, PreEmptive Protection, koruma, topluluk sürümü, gizleme, .NET, ücretsiz, Visual Studio 2017, Visual Studio 2019, Visual Studio, Install
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
description: Visual Studio 'ya dahil edilen Dotfuscator topluluğunun ücretsiz kopyasını yüklemeyi öğrenin.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: befa47e5718d3d2f5d492c49e173b22fc63310e0
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769680"
---
# <a name="install-dotfuscator-community"></a>Dotfuscator Community’yi yükleme

Dotfuscator topluluğu, Visual Studio 'nun isteğe bağlı bir bileşenidir.
Bu yönergeler nasıl yükleneceğini açıklar.

> [!NOTE]
> Visual Studio 'nun sürümleriyle birlikte sunulan Dotfuscator topluluğunun sürümlerine ek olarak, PreEmptive çözümleri de belirli aralıklarla Web sitesinde güncelleştirilmiş sürümler sağlar.
> Visual Studio 'dan yüklemek yerine **en son sürümü** doğrudan indirmek Isterseniz, **[Dotfuscator İndirmeleri sayfasına gitmek için buraya tıklayın][download]**.

## <a name="within-visual-studio"></a>Visual Studio içinde

::: moniker range="vs-2019"

Visual Studio IDE 'den Dotfuscator topluluğunu yükleyebilirsiniz:

1. **Arama kutusuna** (CTRL + Q) yazın `dotfuscator` . <br/> <br/> ![Arama kutusu](media/install_in_vs19_12.png) <br/> <br/>

2. Gösterilen arama sonuçlarında, *Bileşenler* başlığı altında **Install preemptive Protection-Dotfuscator**' ı seçin.
   * Bunun yerine bkz. *menü* başlığı, **preemptive Protection-Dotfuscator topluluğu**altında, Dotfuscator topluluğu zaten yüklü. [Başlamak için bu][get-started]seçeneği belirleyin.

3. Visual Studio Yükleyicisi bir pencere, Dotfuscator Community 'yi yüklemek için önceden yapılandırılmış olarak başlatılır.
   > [!NOTE]
   > Devam etmek için yönetici kimlik bilgilerini sağlamanız gerekebilir.

4. Visual Studio Yükleyicisi penceresinde, *yüklensin*' e tıklayın. <br/> <br/> ![Yükle'ye tıklayın](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Visual Studio IDE 'den Dotfuscator topluluğunu yükleyebilirsiniz:

1. **Hızlı Başlat** (CTRL + Q) arama çubuğunda yazın `dotfuscator` . <br/> <br/> ![Hızlı Başlat](media/install_from_vs_12.png) <br/> <br/>

2. Gösterilen hızlı başlatma sonuçlarında, *Install* başlığı altında **preemptive Protection-Dotfuscator (bireysel bileşen)** öğesini seçin.
   * Bunun yerine, *menüler* başlığı altında **Araçlar-preemptive Protection-Dotfuscator**' ın altında, DOTFUSCATOR CE zaten yüklüdür. [Başlamak için bu][get-started]seçeneği belirleyin.

3. Visual Studio Yükleyicisi bir pencere, Dotfuscator CE 'yi yüklemek için önceden yapılandırılmış olarak başlatılır.
   > [!NOTE]
   > Devam etmek için yönetici kimlik bilgilerini sağlamanız gerekebilir.

4. Visual Studio Yükleyicisi penceresinde, *yüklensin*' e tıklayın. <br/> <br/> ![Yükle'ye tıklayın](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Yükleme tamamlandıktan sonra [Dotfuscator Community kullanmaya başlayabilirsiniz][get-started].

## <a name="during-visual-studio-installation"></a>Visual Studio yüklemesi sırasında

Visual Studio 'Yu henüz yüklemediyseniz, yükleyiciyi [Visual Studio Web sitesinden][vs-install]alabilirsiniz.
Çalıştırıldığında, seçilen Visual Studio sürümü için yükleme seçenekleri görüntülenir.

::: moniker range="vs-2019"

![Yükleme seçenekleri](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Yükleme seçenekleri](media/install_ui_17.png)

::: moniker-end

Ardından, Visual Studio 'nun tek bir bileşeni olarak Dotfuscator topluluğunu yükleyebilirsiniz:

1. **Ayrı bileşenler** sekmesini seçin.
2. *Kod araçları*altında *preemptive Protection-Dotfuscator* öğesini kontrol edin.<br/> <br/> ![Bireysel bileşenler](media/install_individually_12.png) <br/> <br/>
3. *Özet* panelinde, *tek tek bileşenler* bölümünde *preemptive Protection-Dotfuscator* görüntülenir. <br/> <br/> ![Özet bölmesi](media/install_individually_3.png) <br/> <br/>
4. Ortamınız için uygun olan diğer yükleme ayarlarını yapılandırın.
5. Visual Studio 'Yu yüklemeye hazırsanız, *install* düğmesine tıklayın.

Yükleme tamamlandıktan sonra Dotfuscator Community kullanmaya başlayabilirsiniz. Ayrıntılar için, bkz. [Tam kapsamlı Dotfuscator Community Kullanıcı Kılavuzu’nun Kullanmaya Başlama Sayfası][get-started].

## <a name="see-also"></a>Ayrıca bkz.

[Tam Dotfuscator topluluk Kullanıcı Kılavuzu 'ndaki bu konu](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
