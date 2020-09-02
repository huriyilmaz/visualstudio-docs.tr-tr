---
title: Dosyalar ve klasörler için güven ayarları
description: Visual Studio 'Nun güvenliğini sağlamak için dosyalar ve klasörler için güven ayarlarını değiştirme hakkında bilgi edinin.
author: 2percentsilk
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
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88197393"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosyalar ve klasörler için güven ayarlarını yapılandırma

Visual Studio, [Web 'e işaret](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))eden projeleri açmadan önce Kullanıcı onayını ister. Ek güvenlik için, Visual Studio 'Yu, Web özniteliği işaretine sahip herhangi bir dosya veya klasörü açmadan önce Kullanıcı onayını isteyecek şekilde yapılandırabilir veya *güvenilir*olarak belirlenmemiştir. Dosya ve klasör denetimleri varsayılan olarak devre dışıdır.

> [!WARNING]
> Dosyayı, klasörü veya çözümü onaylamadan önce güvenilen bir kişiden veya güvenilir bir konumdan geldiğinden emin olmalısınız.

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için şu adımları izleyin:

1. **Araçlar**  >  **Seçenekler**  >  **güven ayarları** ' nı açın ve sağ bölmedeki **güven ayarlarını yapılandır** bağlantısını seçin.

2. Dosya ve klasörler için istediğiniz denetimlerin düzeyini seçin. Her biri için farklı denetimlerine sahip olabilirsiniz. Seçenekler şunlardır:

   * **Doğrulama yok**: Visual Studio hiçbir denetim gerçekleştirmez.

   * **Web özniteliğinin Işaretini doğrulayın**: dosya veya klasörün web özniteliğinin işareti varsa, Visual Studio bunları engeller ve açmak için izin ister.

   * **Yolun güvenilir olduğunu doğrulama**: dosya veya klasör yolu **Güvenilen yollar** listesinin bir parçası değilse, Visual Studio blok ve açma izni ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilen yollar ekleme

Güvenilen yollar eklemek için aşağıdaki adımları izleyin:

1. **Araçlar**  >  **Seçenekler**  >  **güven ayarları** ' nı açın ve sağ bölmedeki **güven ayarlarını yapılandır** bağlantısını seçin.

2. **Güven ayarları** Iletişim kutusunda **Ekle** ' ye tıklayın ve ardından **Dosya** veya **klasör**' i seçin.

3. ' A gidin ve güvenilen listeye eklemek istediğiniz dosya veya klasörü seçin.

   Dosya veya klasör yolu, **Güvenilen yollar** listesinde görünür.

   ![Güvenilen yollar eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları kaldır

Güvenilen yolları kaldırmak için şu adımları izleyin:

1. **Araçlar**  >  **Seçenekler**  >  **güven ayarları** ' nı açın ve sağ bölmedeki **güven ayarlarını yapılandır** bağlantısını seçin.

2. **Güvenilen yollar** listesinde kaldırmak istediğiniz yolu seçin ve ardından **Kaldır**' a tıklayın.

   > [!TIP]
   > Birden çok giriş seçmek için, yolları seçerken **Shift** tuşunu basılı tutun.

   Seçilen yollar, **Güvenilen yollar** listesinden kaldırılır.
