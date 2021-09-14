---
title: Unity için kurulum Mac için Visual Studio araçları
description: Mac için Visual Studio kullanım için Unity araçları ayarlama ve yükleme
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: f423b77f8464b05b81be2ff7cdb08a2d8b007e0d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726006"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac için Visual Studio araçları ayarlama

bu bölümde, Unity için Mac için Visual Studio araçlarını kullanmaya nasıl başlacağınız açıklanmaktadır.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

### <a name="unity-bundled-installation"></a>Unity paketlenmiş yükleme

unity 2018,1 ' den başlayarak, unity için varsayılan C# tümleşik geliştirme ortamı (ıde) Mac için Visual Studio ve unity Hub yükleme aracının yanı sıra unity indirme yardımcısı ' na de dahildir. [Store.Unity.com](https://store.unity.com/)adresinden Unity 'yi indirin.

yükleme sırasında, Unity ile yüklenecek bileşenler listesinde Mac için Visual Studio işaretli olduğundan emin olun:

#### <a name="unity-hub"></a>Unity hub 'ı

![Unity hub yüklemesi](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity Indirme Yardımcısı

![Unity indirme Yardımcısı yüklemesi](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Mac için Visual Studio güncelleştirmelerini denetle

Unity yüklemesine eklenen Mac için Visual Studio sürümü en son sürüm olmayabilir. En son araçlara ve özelliklere erişiminizin olduğundan emin olmak için güncelleştirmelerin denetlenmesi önerilir.

* [Mac için Visual Studio güncelleştiriliyor](update.md)

### <a name="manual-installation"></a>El ile yükleme

zaten Unity 5.6.1 veya üzeri bir hesabınız varsa ancak Mac için Visual Studio yoksa, Mac için Visual Studio el ile yükleyebilirsiniz. tüm Mac için Visual Studio sürümleri, ücretsiz Community sürümü de dahil olmak üzere Unity için Mac için Visual Studio araçları ile paketlenmiştir:

* [visualstudio.microsoft.com](https://visualstudio.microsoft.com/)adresinden indirin Mac için Visual Studio.
* Mac için Visual Studio Unity araçları, yükleme işlemi sırasında otomatik olarak yüklenir.
* Ek yükleme yardımı için [yükleme kılavuzundaki](./installation.md?view=vsmac-2017&preserve-view=true) adımları izleyin.

> [!NOTE]
> Mac için Visual Studio Unity için Araçlar Unity sürüm 5.6.1 veya üstünü gerektirir. unity sürümünüzde Unity için Visual Studio Araçları etkinleştirildiğini doğrulamak için unity menüsünde **unity hakkında** ' yı seçin ve iletişim kutusunun sol alt kısmındaki "unity için Microsoft Visual Studio araçları" metnini arayın.
>
> ![Unity hakkında](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Unity uzantısının Mac için Visual Studio araçlarının etkin olduğunu onaylayın

Unity uzantısı için Mac için Visual Studio araçları varsayılan olarak etkinleştirilirken, bunu onaylayıp yüklü sürüm numarasını kontrol edebilirsiniz:

1. Visual Studio menüsünde **uzantılar...**' ı seçin.

   ![Uzantıları seçin](media/setup-vsmac-tools-unity-image1.png)

2. oyun geliştirme bölümünü genişletin ve Unity girişi için Mac için Visual Studio araçları ' nı onaylayın.

   ![Unity girişini görüntüle](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Unity 'yi Mac için Visual Studio ile kullanım için yapılandırma

unity 2018,1 ' den başlayarak, unity 'de varsayılan dış betik düzenleyicisi Visual Studio olmalıdır. Bunu doğrulayabilirsiniz veya dış betik düzenleyicisini Visual Studio olarak değiştirebilirsiniz:

1. Unity menüsünden **Tercihler...** seçeneğini belirleyin.

   ![Tercihleri seçin](media/setup-vsmac-tools-unity-image4.png)

2. Tercihler iletişim kutusunda **dış araçlar** sekmesini seçin.

3. dış betik düzenleyicisi açılan listesinden, listeleniyorsa **Visual Studio** seçin, aksi takdirde, **araştır...**' ı seçin.

   ![Visual Studio seçin](media/setup-vsmac-tools-unity-image5.png)

4. eğer **gözatılamıyor...** seçilirse, uygulamalar dizinine gidin ve Visual Studio seçin ve sonra **aç**' a tıklayın.

   ![Açık Seç](media/setup-vsmac-tools-unity-image6.png)

5. **dış betik düzenleyicisi** listesinde Visual Studio seçildikten sonra, yapılandırma işlemini gerçekleştirmek için tercihler iletişim kutusunu kapatın.