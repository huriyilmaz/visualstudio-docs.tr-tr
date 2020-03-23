---
title: Birlik için Mac Araçları için Kurulum Visual Studio
description: Mac için Visual Studio'da kullanılmak üzere Unity araçları nın kurulumu ve yüklenmesi
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 1981141a01848dc7fac09913548f205a04ce618e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79303346"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac Araçları için Visual Studio'u ayarlama

Bu bölümde, Visual Studio for Mac Tools for Unity'yi kullanmaya nasıl başlarız açıklanmaktadır.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio’yu yükleyin

### <a name="unity-bundled-installation"></a>Birlik Paketli Kurulum

Unity 2018.1 ile başlayan Visual Studio for Mac, Unity için varsayılan C# tümleşik geliştirme ortamıdır (IDE) ve Unity Download Assistant'ın yanı sıra Unity Hub yükleme aracına da dahildir. [store.unity.com'dan](https://store.unity.com/)Unity indirin.

Yükleme sırasında, Mac için Visual Studio'nun Unity ile yüklenmesi gereken bileşenler listesinde işaretlendiğinden emin olun:

#### <a name="unity-hub"></a>Birlik Merkezi

![unity hub kurulumu](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Birlik İndirme Asistanı

![unity download asistan yükleme](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Mac için Visual Studio Güncellemeleri olup yok

Visual Studio for Mac sürümü Unity yüklemesi ile birlikte en son olmayabilir. En son araçlara ve özelliklere erişebildiğinizden emin olmak için güncelleştirmeleri denetlemeniz önerilir.

* [Mac için Visual Studio'nun güncellenmesi](update.md)

### <a name="manual-installation"></a>El ile yükleme

Unity 5.6.1 veya üzeri zatenniz varsa, ancak Mac için Visual Studio'nuz yoksa, Mac için Visual Studio'yu el ile yükleyebilirsiniz. Mac için Visual Studio'nun tüm sürümleri, ücretsiz Topluluk sürümü de dahil olmak üzere Mac Tools for Unity için Visual Studio ile birlikte verilir:

* [Visualstudio.microsoft.com'dan](https://visualstudio.microsoft.com/)Mac için Visual Studio'dan indirin.
* Mac Araçlar için Unity için Visual Studio yükleme işlemi sırasında otomatik olarak yüklenir.
* Ek yükleme yardımı için [yükleme kılavuzundaki](/visualstudio/mac/installation) adımları izleyin.

> [!NOTE]
> Visual Studio for Mac Tools for Unity için Unity sürümü 5.6.1 veya üzeri gerektirir. Unity sürümünüzde Visual Studio Tools for Unity'nin etkinleştirildiğinden doğrulamak için, Unity menüsünden **Birlik Hakkında'yı** seçin ve iletişim kutusunun sol alt kısmındaki "Microsoft Visual Studio Tools for Unity enabled" metnini arayın.
>
> ![Birlik Hakkında](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Mac Tools for Unity uzantısı için Visual Studio'nun etkinleştirildiğinden onaylayın

Mac Tools for Unity uzantısı için Visual Studio varsayılan olarak etkinleştirilirken, bunu onaylayabilir ve yüklü sürüm numarasını kontrol edebilirsiniz:

1. Visual Studio menüsünden **Uzantılar'ı seçin...**.

   ![Uzantıları Seçin](media/setup-vsmac-tools-unity-image1.png)

2. Oyun Geliştirme bölümünü genişletin ve Unity girişi için Mac Tools için Visual Studio'yu onaylayın.

   ![Birlik Girişini Görüntüle](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Mac için Visual Studio ile kullanım için Birliği Yapılandır

Unity 2018.1 ile başlayan Visual Studio, Unity'de varsayılan dış komut dosyası düzenleyicisi olmalıdır. Bunu onaylayabilir veya harici komut dosyası düzenleyicisini Visual Studio olarak değiştirebilirsiniz:

1. Birlik menüsünden **Tercihler...** seçeneğini belirleyin.

   ![Tercihleri Seçin](media/setup-vsmac-tools-unity-image4.png)

2. Tercihler iletişim kutusunda Dış **Araçlar** sekmesini seçin.

3. Harici Komut Dosyası Düzenleyicisi açılır listesinden, listelenmişse **Visual Studio'yu** seçin, aksi takdirde **Gözat'ı seçin...**.

   ![Visual Studio'yı seçin](media/setup-vsmac-tools-unity-image5.png)

4. **Gözat...** seçildiyse, Uygulamalar dizinine gidin ve Visual Studio'yu seçin ve ardından **Aç'ı**tıklatın.

   ![Aç'ı Seçin](media/setup-vsmac-tools-unity-image6.png)

5. Visual Studio **Dış Komut Dosyası Düzenleyicisi** listesinde seçildikten sonra yapılandırma işlemini tamamlamak için Tercihler iletişim kutusunu kapatın.