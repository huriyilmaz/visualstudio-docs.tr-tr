---
title: Unity için Araçlar Mac için Visual Studio Kurulumu
description: Ayarlama ve kullanmak için Unity araçları, Mac için Visual Studio yükleme
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d490b4c1268beb4a5ad55263cb186d838005f718
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408552"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac araçları için Visual Studio'yu ayarlama

Bu bölümde, Visual Studio için Unity için Mac araçları ile çalışmaya başlamak açıklanmaktadır.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

### <a name="unity-bundled-installation"></a>Unity paket yükleme

Unity 2018.1 ile başlayarak, Mac için Visual Studio varsayılan değer C# Unity için tümleşik geliştirme ortamı (IDE) ve Unity indirme Yardımcısı'nın yanı sıra Unity hub'ı yükleme aracı dahil edilir. [Store.Unity.com](https://store.unity.com/)adresinden Unity 'yi indirin.

Yükleme sırasında Mac için Visual Studio ile Unity yüklenecek bileşenlerin listesini işaretlendiğinden emin olun:

#### <a name="unity-hub"></a>Unity Hub

![Unity hub'ı yükleme](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity Yükleme Yardımcısı

![Unity Yükleme Yardımcısı'nı yükleme](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Mac için Visual Studio Güncelleştirmeleri denetle

Unity yükleme işlemine dahil Mac için Visual Studio sürümü, en son olmayabilir. En son araçlara ve özelliklere erişiminiz olduğundan emin olmak için güncelleştirmeleri denetlemeniz önerilir.

* [Mac için Visual Studio güncelleştiriliyor](update.md)

### <a name="manual-installation"></a>El ile yükleme

Unity 5.6.1 zaten varsa veya yukarıdaki ancak Mac için Visual Studio yüklü, Mac için Visual Studio el ile yükleyebilirsiniz. Mac için Visual Studio'nun tüm sürümlerinde Visual Studio ile ücretsiz Community sürümü dahil olmak üzere, Unity için Mac araçları paketlendi:

* [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/)adresinden indirin Mac için Visual Studio.
* Unity için Araçlar Mac için Visual Studio yükleme işlemi sırasında otomatik olarak yüklenir.
* Ek yükleme yardımı için [yükleme kılavuzundaki](/visualstudio/mac/installation/?view=vsmac-2017) adımları izleyin.

> [!NOTE]
> Unity için Mac araçları Visual Studio Unity sürüm 5.6.1 gerektirir veya üzeri. Unity sürümünüzde Unity için Visual Studio Araçları etkinleştirildiğini doğrulamak için Unity menüsünde **Unity hakkında** ' yı seçin ve iletişim kutusunun sol alt kısmındaki "unity Için Microsoft Visual Studio Araçları" metnini arayın.
>
> ![Unity hakkında](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Visual Studio için Unity uzantısı Mac araçları etkinleştirilmiş olduğunu doğrulayın

Visual Studio için Unity uzantısı Mac araçları varsayılan olarak etkinleştirilmesi gerekir, ancak bunu doğrulamak ve yüklü sürüm numarasını kontrol edin:

1. Visual Studio menüsünden Uzantılar ' ı seçin. **..**

   ![Uzantıları seçin](media/setup-vsmac-tools-unity-image1.png)

2. Oyun Geliştirme bölümü genişletin ve Visual Studio için Unity girişi için Mac araçları onaylayın.

   ![Unity girişi görünümü](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Unity Mac için Visual Studio ile kullanılacak şekilde yapılandırma

Unity 2018.1 itibarıyla Visual Studio, Unity'de varsayılan dış kod düzenleyicisi olmalıdır. Bunu doğrulamak veya Visual Studio için dış Kod Düzenleyicisi'ni değiştirin:

1. Unity menüsünden **Tercihler...** seçeneğini belirleyin.

   ![Tercihler'i seçme](media/setup-vsmac-tools-unity-image4.png)

2. Tercihler iletişim kutusunda **dış araçlar** sekmesini seçin.

3. Dış betik Düzenleyicisi açılan listesinden, listeleniyorsa **Visual Studio** ' yı seçin, aksi takdirde, **araştır...** ' ı seçin.

   ![Visual Studio'yu seçme](media/setup-vsmac-tools-unity-image5.png)

4. Eğer **gözatılamıyor...** seçilirse, uygulamalar dizinine gidin ve Visual Studio 'Yu seçip **Aç**' a tıklayın.

   ![Aç'ı seçin](media/setup-vsmac-tools-unity-image6.png)

5. **Dış betik Düzenleyicisi** listesinde Visual Studio seçildikten sonra yapılandırma işlemini gerçekleştirmek için Tercihler iletişim kutusunu kapatın.