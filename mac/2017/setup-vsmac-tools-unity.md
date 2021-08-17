---
title: Unity Mac için Visual Studio Araçları'nı ayarlama
description: Unity araçlarını Mac için Visual Studio'de kullanmak üzere ayarlama ve yükleme
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: 06e0b027709373487c4a46540daa8e67db344f42ddf8b87af05174f6b6937a07
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439733"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac için Visual Studio Araçları ayarlama

Bu bölümde Unity için Mac için Visual Studio kullanmaya başlama açıklandı.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

### <a name="unity-bundled-installation"></a>Unity Paketli Yüklemesi

Unity 2018.1'den başlayarak Mac için Visual Studio, Unity için varsayılan C# tümleşik geliştirme ortamıdır (IDE) ve Unity İndirme Yardımcısı ile Unity Hub yükleme aracına dahildir. [store.unity.com'den Unity'store.unity.com.](https://store.unity.com/)

Yükleme sırasında, unity Mac için Visual Studio bileşenleri listesinden emin olun:

#### <a name="unity-hub"></a>Unity Hub

![unity hub yüklemesi](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity İndirme Yardımcısı

![unity indirme yardımcısı yüklemesi](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Güncelleştirmeleri denetleme Mac için Visual Studio

Unity yüklemesine Mac için Visual Studio sürümü en son sürümde yer alıyor olabilir. En son araçlara ve özelliklere erişiminiz olduğundan emin olmak için güncelleştirmeleri denetlemenizi öneririz.

* [Güncelleştirme Mac için Visual Studio](update.md)

### <a name="manual-installation"></a>El ile yükleme

Unity 5.6.1 veya üzeri bir sürümüne sahipsiniz ancak Mac için Visual Studio yüklü Mac için Visual Studio yükleyebilirsiniz. Tüm Mac için Visual Studio sürümleri, ücretsiz Mac için Visual Studio sürümü de dahil olmak üzere Unity için Community paketlenmiştir:

* visualstudio.microsoft.com'Mac için Visual Studio [indirin.](https://visualstudio.microsoft.com/)
* Mac için Visual Studio Unity araçları yükleme işlemi sırasında otomatik olarak yüklenir.
* Ek yükleme yardımı için [yükleme kılavuzunda](./installation.md?view=vsmac-2017&preserve-view=true) yer alan adımları izleyin.

> [!NOTE]
> Mac için Visual Studio Unity için araçlar Unity sürüm 5.6.1 veya üzerini gerektirir. Unity Unity için Visual Studio Araçları etkinleştirildiğinden emin olmak için Unity menüsünden **Unity** Hakkında'ya tıklayın ve iletişim kutusunun sol alt kısmında "Unity için Microsoft Visual Studio Araçları etkinleştirildi" metnini seçin.
>
> ![Unity hakkında](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Unity için Mac için Visual Studio araçlarının etkinleştirildiğinden onaylayın

Unity Mac için Visual Studio Araçları uzantısı varsayılan olarak etkinleştirilmelidir, ancak bunu onaylayabilir ve yüklü sürüm numarasını kontrol edin:

1. Yeni Visual Studio **Uzantılar... öğesini seçin.**

   ![Uzantılar'ı seçin](media/setup-vsmac-tools-unity-image1.png)

2. Oyun Geliştirme bölümünü genişletin ve Unity için Mac için Visual Studio girişini onaylayın.

   ![Unity Girişini Görüntüleme](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Unity'yi Mac için Visual Studio ile kullanım için yapılandırma

Unity 2018.1'den Visual Studio, Unity'de varsayılan dış betik düzenleyicisi olması gerekir. Bunu onaylayabilir veya dış betik düzenleyicisini şu şekilde Visual Studio:

1. Unity **menüsünden Tercihler...** öğesini seçin.

   ![Tercihler'i seçin](media/setup-vsmac-tools-unity-image4.png)

2. Tercihler iletişim kutusunda Dış Araçlar **sekmesini** seçin.

3. Dış Betik Düzenleyicisi açılan listesinden, **listelenmişse** Visual Studio'yi seçin, aksi takdirde **Gözat... seçeneğini seçin.**

   ![Yeni bir Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Gözat... **seçildiyse** Uygulamalar dizinine gidin ve Visual Studio'a **tıklayın.**

   ![Aç'ı seçin](media/setup-vsmac-tools-unity-image6.png)

5. Dış Visual Studio Düzenleyicisi listesinde bir **uygulama seçtikten** sonra, yapılandırma işlemini tamamlamak için Tercihler iletişim kutusunu kapatın.