---
title: dosyalar ve klasörler için güven Ayarlar
description: Visual Studio güvenli tutulacak dosyalar ve klasörler için güven ayarlarını değiştirmeyi öğrenin.
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
ms.openlocfilehash: 900e6c829234c534e01e1512aef9ca3ba4a41447
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048667"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosyalar ve klasörler için güven ayarlarını yapılandırma

::: moniker range=">=vs-2022"

Visual Studio 2022 ' de (önizleme 2), dosyalarda, klasörlerde, projelerde ve çözümlerinde güvenilir olmayan kodların ıde 'de açılmasına her seferinde bir uyarı göstermek için güven Ayarlar işlevselliğini yeniden yaptık.

:::image type="content" source="media/vs-2022/trusted-settings-warning-message.png" alt-text="güven Ayarlar uyarı iletisinin ekran görüntüsü":::

Özelliği güncelleştirmeye devam ettiğimiz için buraya daha fazla bilgi ekleyeceğiz. Bizi izlemeye devam edin!

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio, [Web 'e işaret](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))eden projeleri açmadan önce kullanıcı onayını ister. ek güvenlik için, web özniteliği işaretine sahip herhangi bir dosyayı veya klasörü açmadan önce veya *güvenilir* olarak belirlenmemiş bir dosya ya da klasör açmadan önce kullanıcı onayını isteyecek şekilde Visual Studio yapılandırabilirsiniz. Dosya ve klasör denetimleri varsayılan olarak devre dışıdır.

> [!WARNING]
> Dosyayı, klasörü veya çözümü onaylamadan önce güvenilen bir kişiden veya güvenilir bir konumdan geldiğinden emin olmalısınız.

> [!NOTE]
> Visual Studio 2022 ' de (önizleme), dosyalarda, klasörlerde, projelerde ve çözümlerde güvenilir olmayan kodların ıde 'de açılmasına her seferinde bir uyarı göstermek için güven Ayarlar işlevselliğini yeniden yaptık. daha fazla bilgi için, [Visual Studio 2022 Preview sürüm notlarının](/visualstudio/releases/2022/release-notes-preview#trustedlocations-170P2)"güvenilen konumlar" bölümüne bakın.

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için şu adımları izleyin:

1. **araçlar** > **seçenekler** > **güven Ayarlar** açın ve sağ bölmedeki **güveni yapılandır Ayarlar** bağlantısını seçin.

2. Dosya ve klasörler için istediğiniz denetimlerin düzeyini seçin. Her biri için farklı denetimlerine sahip olabilirsiniz. Seçenekler şunlardır:

   * **doğrulama yok**: Visual Studio hiçbir denetim gerçekleştirmez.

   * **web özniteliğinin işaretini doğrulayın**: dosya veya klasör web özniteliğinin işaretine sahipse, Visual Studio bloklar ve açma izni ister.

   * **yolun güvenilir olduğunu doğrulama**: dosya veya klasör yolu **güvenilen yollar** listesinin bir parçası değilse, Visual Studio engeller ve açma izni ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilen yollar ekleme

Güvenilen yollar eklemek için aşağıdaki adımları izleyin:

1. **araçlar** > **seçenekler** > **güven Ayarlar** açın ve sağ bölmedeki **güveni yapılandır Ayarlar** bağlantısını seçin.

2. **güven Ayarlar** iletişim kutusunda **ekle** ' ye tıklayın ve ardından **dosya** veya **klasör**' ü seçin.

3. ' A gidin ve güvenilen listeye eklemek istediğiniz dosya veya klasörü seçin.

   Dosya veya klasör yolu, **Güvenilen yollar** listesinde görünür.

   ![Güvenilen yollar eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları kaldır

Güvenilen yolları kaldırmak için şu adımları izleyin:

1. **araçlar** > **seçenekler** > **güven Ayarlar** açın ve sağ bölmedeki **güveni yapılandır Ayarlar** bağlantısını seçin.

2. **Güvenilen yollar** listesinde kaldırmak istediğiniz yolu seçin ve ardından **Kaldır**' a tıklayın.

   > [!TIP]
   > Birden çok giriş seçmek için, yolları seçerken **Shift** tuşunu basılı tutun.

   Seçilen yollar, **Güvenilen yollar** listesinden kaldırılır.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio bir uygulama oluşturun](../walkthrough-building-an-application.md)
