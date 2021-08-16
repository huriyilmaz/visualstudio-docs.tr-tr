---
title: Dosya Ayarlar klasörler için güven dosyaları
description: Dosyaları ve klasörleri güvenli tutmak için dosya ve klasörlerin güven ayarlarını Visual Studio öğrenin.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.date: 07/22/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: ba2e171a60be856fe083ac66e073524190343c5d788ebbed14a07db41755a3ee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412178"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosya ve klasörler için güven ayarlarını yapılandırma

::: moniker range=">=vs-2022"

Visual Studio 2022'de (Önizleme 2) dosyalarda, klasörlerde, projelerde ve çözümlerde güvenilmeyen kodlar IDE'de açılmasına yakın olduğunda bir uyarı göstermek için Güven Ayarlar işlevselliğini yeniden gözden geçirdik.

:::image type="content" source="media/vs-2022/trusted-settings-warning-message.png" alt-text="Güven ve uyarı Ayarlar ekran görüntüsü":::

Özelliği güncelleştirmeye devam ettiyken buraya daha fazla bilgi ekley edeceğiz. Bizi izlemeye devam edin!

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio Web İşareti olan projeleri açmadan önce kullanıcı [onayı isteminde bulundurabilirsiniz.](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)) Ek güvenlik için, web özniteliğinin Visual Studio veya güvenilir olarak atanmamış herhangi bir dosyayı veya klasörü açmadan önce kullanıcı onayı isteminde bulunacaktır. Dosya ve klasör denetimleri varsayılan olarak devre dışıdır.

> [!WARNING]
> Yine de dosyayı, klasörü veya çözümü onaylamadan önce güvenilir bir kişi veya güvenilir bir konumdan geldiğinden emin olun.

> [!NOTE]
> Visual Studio 2022 'de (Önizleme) dosyalarda, klasörlerde, projelerde ve çözümlerde güvenilmeyen kodun IDE'de açılmasına yakın olduğunda Güven Ayarlar işlevini yeniden gözden geçirdik. Daha fazla bilgi edinmek için Visual Studio [2022 Preview sürüm notlarının](/visualstudio/releases/2022/release-notes-preview#trustedlocations-170P2)"Güvenilen Konumlar" bölümüne bakın.

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güveni Ayarlar** açın ve sağ bölmede **Ayarlar** Yapılandır bağlantısını seçin.

2. Dosya ve klasörler için istediğiniz denetim düzeyini seçin. Her biri için farklı denetimler olabilir. Seçenekler şunlardır:

   * **Doğrulama yok:** Visual Studio denetim gerçekleştirmez.

   * **Web özniteliğinin işaretini doğrulayın:** Dosya veya klasör web özniteliğinin işaretine sahipse, Visual Studio ve açma izni ister.

   * **Yolun güvenilir olduğunu doğrulama:** Dosya veya klasör yolu  Güvenilen Yollar listesinin bir parçası değilse Visual Studio izin ister ve açma izni ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilen yollar ekleme

Güvenilen yollar eklemek için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güveni Ayarlar** açın ve sağ bölmede **Ayarlar** Yapılandır bağlantısını seçin.

2. Güven **Dosyası** iletişim kutusunda **Ekle'Ayarlar** ve ardından Dosya veya **Klasör'e** **tıklayın.**

3. Güvenilen listeye eklemek istediğiniz dosya veya klasörü bulun ve seçin.

   Dosya veya klasör yolu Güvenilen Yollar **listesinde** görünür.

   ![Güvenilen yollar eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları kaldırma

Güvenilen yolları kaldırmak için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güveni Ayarlar** açın ve sağ bölmede **Ayarlar** Yapılandır bağlantısını seçin.

2. Güvenilen Yollar listesinde kaldırmak istediğiniz yolu seçin **ve kaldır'a** **tıklayın.**

   > [!TIP]
   > Birden çok giriş seçmek için, yolları **seçerken Shift** tuşunu basılı tutun.

   Seçilen yollar Güvenilen Yollar **listesinden** kaldırılır.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'de uygulama oluşturma](../walkthrough-building-an-application.md)
