---
title: Unity için kurulum Mac için Visual Studio Araçları
description: Mac için Visual Studio kullanım için Unity araçları ayarlama ve yükleme
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: 7025798689e7541471c56988ef24414005dfe656
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860544"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac için Visual Studio Araçları ayarlama

Bu bölümde, Unity için Mac için Visual Studio araçlarını kullanmaya nasıl başlacağınız açıklanmaktadır.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

### <a name="unity-bundled-installation"></a>Unity paketlenmiş yükleme

Unity 2018,1 ' den başlayarak, Unity için varsayılan C# tümleşik geliştirme ortamı (IDE) Mac için Visual Studio ve Unity hub yükleme aracının yanı sıra Unity Indirme Yardımcısı ' na de dahildir. [Store.Unity.com](https://store.unity.com/)adresinden Unity 'yi indirin.

Yükleme sırasında, Unity ile yüklenecek bileşenler listesinde Mac için Visual Studio işaretli olduğundan emin olun:

#### <a name="unity-hub"></a>Unity hub 'ı

![Unity hub yüklemesi](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity Indirme Yardımcısı

![Unity indirme Yardımcısı yüklemesi](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Mac için Visual Studio güncelleştirmelerini denetle

Unity yüklemesine eklenen Mac için Visual Studio sürümü en son sürüm olmayabilir. En son araçlara ve özelliklere erişiminizin olduğundan emin olmak için güncelleştirmelerin denetlenmesi önerilir.

* [Mac için Visual Studio güncelleştiriliyor](update.md)

### <a name="manual-installation"></a>El ile yükleme

Zaten Unity 5.6.1 veya üzeri bir hesabınız varsa ancak Mac için Visual Studio yoksa, Mac için Visual Studio el ile yükleyebilirsiniz. Tüm Mac için Visual Studio sürümleri, ücretsiz topluluk sürümü de dahil olmak üzere Unity için Mac için Visual Studio Araçları ile paketlenmiştir:

* [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/)adresinden indirin Mac için Visual Studio.
* Unity için Mac için Visual Studio Araçları, yükleme işlemi sırasında otomatik olarak yüklenir.
* Ek yükleme yardımı için [yükleme kılavuzundaki](./installation.md?view=vsmac-2017) adımları izleyin.

> [!NOTE]
> Unity için Mac için Visual Studio Araçları, Unity sürüm 5.6.1 veya üstünü gerektirir. Unity sürümünüzde Unity için Visual Studio Araçları etkinleştirildiğini doğrulamak için Unity menüsünde **Unity hakkında** ' yı seçin ve iletişim kutusunun sol alt kısmındaki "unity Için Microsoft Visual Studio Araçları" metnini arayın.
>
> ![Unity hakkında](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Unity uzantısının Mac için Visual Studio araçlarının etkin olduğunu onaylayın

Unity uzantısı için Mac için Visual Studio Araçları varsayılan olarak etkinleştirilirken, bunu onaylayıp yüklü sürüm numarasını kontrol edebilirsiniz:

1. Visual Studio menüsünden Uzantılar ' ı seçin. **..**

   ![Uzantıları seçin](media/setup-vsmac-tools-unity-image1.png)

2. Oyun geliştirme bölümünü genişletin ve Unity girişi için Mac için Visual Studio Araçları ' nı onaylayın.

   ![Unity girişini görüntüle](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Unity 'yi Mac için Visual Studio ile kullanım için yapılandırma

Unity 2018,1 ' den itibaren, Visual Studio 'Nun Unity 'de varsayılan dış betik Düzenleyicisi olması gerekir. Bunu doğrulayabilirsiniz veya dış betik düzenleyicisini Visual Studio 'ya değiştirebilirsiniz:

1. Unity menüsünden **Tercihler...** seçeneğini belirleyin.

   ![Tercihleri seçin](media/setup-vsmac-tools-unity-image4.png)

2. Tercihler iletişim kutusunda **dış araçlar** sekmesini seçin.

3. Dış betik Düzenleyicisi açılan listesinden, listeleniyorsa **Visual Studio** ' yı seçin, aksi takdirde, **araştır...**' ı seçin.

   ![Visual Studio 'Yu seçin](media/setup-vsmac-tools-unity-image5.png)

4. Eğer **gözatılamıyor...** seçilirse, uygulamalar dizinine gidin ve Visual Studio 'Yu seçip **Aç**' a tıklayın.

   ![Açık Seç](media/setup-vsmac-tools-unity-image6.png)

5. **Dış betik Düzenleyicisi** listesinde Visual Studio seçildikten sonra yapılandırma işlemini gerçekleştirmek için Tercihler iletişim kutusunu kapatın.