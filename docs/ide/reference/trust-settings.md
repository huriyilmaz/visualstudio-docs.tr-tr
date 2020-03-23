---
title: Dosya ve Klasörler için Güven Ayarları
description: Visual Studio'nun güvenliğini sağlamak için dosya ve klasörlerin güven ayarlarını nasıl değiştireceğinizi öğrenin.
author: abuchholtzau
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 011673bca7be569b5b350dc264148d5a7890d39c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62789650"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosya ve klasörler için güven ayarlarını yapılandırma

Visual Studio [web işareti](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))ne var projeleri açmadan önce kullanıcı onayı ister. Daha fazla güvenlik için, web özniteliğinin işaretine sahip veya *güvenilir*olarak atanmadı herhangi bir dosya veya klasörü açmadan önce Kullanıcı onayı istenecek şekilde Visual Studio'yu da yapılandırabilirsiniz. Dosya ve klasör denetimleri varsayılan olarak devre dışı bırakılır.

> [!WARNING]
> Dosyayı, klasörün veya çözümün onaylanmadan önce güvenilir bir kişiden veya güvenilir bir konumdan geldiğinden emin olmalısınız.

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için aşağıdaki adımları izleyin:

1. **Araçlar** > **Seçenekleri** > **Güven Ayarları'nı** açın ve sağ bölmedeki **Güven Ayarlarını Yapılandır** bağlantısını seçin.

2. Dosya ve klasörler için istediğiniz denetim düzeyini seçin. Her biri için farklı çekler olabilir. Seçenekler şunlardır:

   * **Doğrulama yok**: Visual Studio herhangi bir denetim gerçekleştirmez.

   * **Web özniteliğinin işaretini doğrulayın**: Dosya veya klasörweb özniteliğinin işaretine sahipse, Visual Studio bloklar ve açmak için izin ister.

   * **Doğrula yolu güvenilirdir**: Dosya veya klasör yolu **Güvenilen Yollar** listesinin bir parçası değilse, Visual Studio engeller ve açmak için izin ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilen yollar ekleme

Güvenilen yollar eklemek için aşağıdaki adımları izleyin:

1. **Araçlar** > **Seçenekleri** > **Güven Ayarları'nı** açın ve sağ bölmedeki **Güven Ayarlarını Yapılandır** bağlantısını seçin.

2. **Güven Ayarları** iletişim kutusunda **Ekle'yi** tıklatın ve ardından **Dosya** veya **Klasör'ü**seçin.

3. Güvenilen ler listesine eklemek istediğiniz dosya veya klasöre gidin ve seçin.

   Dosya veya klasör yolu **Güvenilen Yollar** listesinde görünür.

   ![Güvenilen yollar eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları kaldırma

Güvenilen yolları kaldırmak için aşağıdaki adımları izleyin:

1. **Araçlar** > **Seçenekleri** > **Güven Ayarları'nı** açın ve sağ bölmedeki **Güven Ayarlarını Yapılandır** bağlantısını seçin.

2. **Güvenilen Yollar** listesinde kaldırmak istediğiniz yolu seçin ve ardından **Kaldır'ı**tıklatın.

   > [!TIP]
   > Birden çok giriş seçmek için, yolları seçerken **Shift'i** basılı tutun.

   Seçili yollar **Güvenilen Yollar** listesinden kaldırılır.
