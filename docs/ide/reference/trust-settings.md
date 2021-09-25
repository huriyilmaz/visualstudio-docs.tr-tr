---
title: Dosya Ayarlar klasörler için güven dosyaları
description: Dosyaları ve klasörleri güvenli tutmak için dosya ve klasörlerin güven ayarlarını Visual Studio öğrenin.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.date: 09/15/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: cde67d54f7c70935f6012542406834ba6c423d78
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430653"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosya ve klasörler için güven ayarlarını yapılandırma

::: moniker range=">=vs-2022"

Visual Studio 2022'de (Önizleme 2) dosyalarda, klasörlerde, projelerde ve çözümlerde güvenilmeyen kodun IDE'de açılmasına her zaman bir uyarı göstermek için Güven Ayarlar işlevselliğini yeniden gözden geçirdik.

:::image type="content" source="media/vs-2022/trusted-settings-warning-message.png" alt-text="Güven uyarı Ayarlar ekran görüntüsü":::

Özelliği güncelleştirmeye devam ettiyken bu sayfaya daha fazla bilgi ekley edeceğiz. Bu arada, en son haberler için [2022'de](https://devblogs.microsoft.com/visualstudio/improving-developer-security-with-visual-studio-2022/)geliştirici güvenliğini geliştirme blog Visual Studio göz atabilirsiniz.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio Web İşareti olan projeleri açmadan önce [kullanıcı onayı isteminde bulundurabilirsiniz.](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)) Ek güvenlik için, web özniteliğinin Visual Studio veya güvenilir olarak atanmamış herhangi bir dosyayı veya klasörü açmadan önce kullanıcı onayı isteminde bulunacaktır. Dosya ve klasör denetimleri varsayılan olarak devre dışıdır.

> [!WARNING]
> Yine de dosyayı, klasörü veya çözümü onaylamadan önce güvenilir bir kişi veya güvenilir bir konumdan geldiğinden emin olun.

> [!NOTE]
> Visual Studio 2022 'de (Önizleme) dosyalarda, klasörlerde, projelerde ve çözümlerde güvenilmeyen kodun IDE'de açılmasına her zaman bir uyarı göstermek için Güven Ayarlar işlevselliğini yeniden gözden geçirdik. Daha fazla bilgi edinmek için son [2022'de Visual Studio geliştirme](https://devblogs.microsoft.com/visualstudio/improving-developer-security-with-visual-studio-2022/) blog gönderisi'ne bakın.

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güveni Ayarlar** açın ve **sağ bölmede Ayarlar** Yapılandır bağlantısını seçin.

2. Dosyalar ve klasörler için istediğiniz denetim düzeyini seçin. Her biri için farklı denetimler olabilir. Seçenekler şunlardır:

   * **Doğrulama yok:** Visual Studio denetim gerçekleştirmez.

   * **Web özniteliğinin işaretini doğrulayın:** Dosya veya klasör web özniteliğinin işaretine sahipse, Visual Studio ve açma izni ister.

   * **Yolun güvenilir olduğunu doğrulama:** Dosya veya klasör yolu  Güvenilen Yollar listesinin parçası değilse, Visual Studio izin ister ve açma izni ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilen yollar ekleme

Güvenilen yollar eklemek için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güveni Ayarlar** açın ve **sağ bölmede Ayarlar** Yapılandır bağlantısını seçin.

2. Güven **Dosyası** iletişim kutusunda **Ekle'Ayarlar** ve ardından Dosya veya **Klasör'e** **tıklayın.**

3. Güvenilen listeye eklemek istediğiniz dosya veya klasörü bulun ve seçin.

   Dosya veya klasör yolu Güvenilen Yollar **listesinde** görünür.

   ![Güvenilen yollar eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları kaldırma

Güvenilen yolları kaldırmak için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güveni Ayarlar** açın ve **sağ bölmede Ayarlar** Yapılandır bağlantısını seçin.

2. Güvenilen Yollar listesinde kaldırmak istediğiniz yolu seçin **ve kaldır'a** **tıklayın.**

   > [!TIP]
   > Birden çok giriş seçmek için, yolları **seçerken Shift** tuşunu basılı tutun.

   Seçilen yollar Güvenilen Yollar **listesinden** kaldırılır.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'da uygulama oluşturma](../walkthrough-building-an-application.md)
