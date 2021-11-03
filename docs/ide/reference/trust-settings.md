---
title: Dosya Ayarlar klasörler için güven dosyaları
description: Dosyaları ve klasörleri güvenli tutmak için dosya ve klasörlerin güven ayarlarını Visual Studio öğrenin.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.date: 10/27/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 4e92e449bf947ebbb03e676d6cb77d926c6971d8
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127951"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosya ve klasörler için güven ayarlarını yapılandırma

::: moniker range=">=vs-2022"

2022 Visual Studio de Güven Ayarlar işlevini, güvenilmeyen kod IDE'de her açıldığında uyarı gösterecek şekilde yeniledk.  

Yazılım geliştiricileri, kötü amaçlı yazılımlara karşı giderek daha fazla hedef haline gelir. Yeni **Trust Ayarlar** işlevi, tanımaz kodu işleme riskleriyle ilgili farkındalığı artırmayı amaçlar ve içeriği açmadan (depolar, çözümler, projeler ve dosyalar gibi) farklı senaryoları hedefleyen kötü amaçlı aktörlere karşı koruma sağlamak ve Visual Studio. 

Güvenilen **konumlar** özelliği varsayılan olarak etkin değildir. 

## <a name="enable-trusted-locations"></a>Güvenilen konumları etkinleştirme

Güvenilen **konumlar özelliğini etkinleştirmek** için şu adımları izleyin:

1. Araç **Seçenekleri** > **Güveni'Ayarlar.** > 

2. Güven **İlkeleri bölmesinde,** içeriği **açmadan önce güven kararı gerektir'i seçin.**

:::image type="content" source="media/vs-2022/trusted-settings-options-dialog.png" alt-text="Güven ve Güven seçenekleri kullanılarak güvenilen konumların nasıl etkinleştir Ayarlar ekran görüntüsü.":::

> [!NOTE]
> Otomatik **olarak oluşturulurken geçici konumlar Visual Studio** güven denetimlerini atla seçeneği varsayılan olarak  etkindir, ancak İçerik açılmadan önce güven kararı gerektir seçeneği de etkinleştirilmediği sürece herhangi bir etkisi olmaz.

Etkinleştirildikten sonra Visual Studio olarak belirlenen içeriği açmaya çalışsanız ve güvenlik etkileri konusunda  sizi uyaran yeni bir iletişim kutusu gösterir.

:::image type="content" source="media/vs-2022/trusted-settings-warning-dialog.png" alt-text="Güven ve Uyarı iletişim Ayarlar ekran görüntüsü.":::

## <a name="manage-trust-settings"></a>Güven ayarlarını yönetme

Güvenilen konumları eklemek ve kaldırmak için aşağıdaki gibi bir belgeyi ekleyin.

### <a name="add-trusted-locations"></a>Güvenilen konumlar ekleme

Özelliği etkinleştirdikten sonra, Visual Studio 2022 ile birlikte açmakta olan tüm içeriğe Güvenilir konumlar listesine ekleyene kadar **güvenilmeyen olarak kabul edilir.**  Bir klasöre doğrudan uyarı iletişim kutusundan *güvenebilirsiniz.* Aşağıdaki adımları uygulayın:

1. Güven düzeyi açılan listesinden, güvenmek istediğiniz klasörü (geçerli klasör veya **üst** klasör) seçin.

   :::image type="content" source="media/vs-2022/trust-folder-trust-level.png" alt-text="Uyarı iletişim kutusundan bir klasöre güvenmeyi gösteren ekran görüntüsü.":::

1. İletişim kutusunda **Güven ve devam** düğmesini seçin.

   Visual Studio, Araç Seçenekleri Güveni'nde Güvenilen  **konumlar** listesine > **klasör yolunu** > **Ayarlar.**

Güvenilen konumlar iletişim **kutusundan Güvenilen konumlara** **klasör Ayarlar** de ebilirsiniz. Aşağıdaki adımları uygulayın:

1. Araç **Seçenekleri**  >  **Güveni'Ayarlar.**  >   Ayrıca, uyarı iletişim **kutusundan Ayarlar** ayarlarını **yönet'i seçerek Güven** Yönetimi'ne *de açabilirsiniz.*

2. Sağ **tarafta güven ilkeleri** bölmesinden Klasör **Ekle'yi** seçin.

3. Güvenilen listeye eklemek istediğiniz klasöre gidin ve klasörü seçin.

   Klasör yolu Güvenilen **konumlar listesinde** görünür. El ile ekleyceniz bu klasör, Yerel **Kullanıcı Tarafından Güvenilen** olarak **listelenir.**
   
   :::image type="content" source="media/vs-2022/trusted-locations.png" alt-text="**Güvenilen konumlara** eklenen klasörü gösteren ekran görüntüsü.":::

> [!NOTE]
> Güvenilen konumlar özelliğini **etkinleştirdikten** sonra, Visual Studio içerik için klasör yolu otomatik olarak Güvenilen **konumlar listesine** eklenir. Bu klasör yolu Sistem Tarafından **Güvenilen olarak** **listelenir.**
> 
> :::image type="content" source="media/vs-2022/trusted-by-values.png" alt-text="**Güvenilen konumlar** listesinde *Yerel Kullanıcı* ve *Sistem* **Güvenilen Tarafından** değerlerini gösteren ekran görüntüsü.":::

### <a name="remove-trusted-locations"></a>Güvenilen konumları kaldırma

Güvenilen konumları kaldırmak için şu adımları izleyin:

1. Araç **Seçenekleri** > **Güveni'Ayarlar.** > 

2. Güvenilen konumlar listesinde kaldırmak istediğiniz yolu **seçin ve** kaldır'a **tıklayın.**

   > [!TIP]
   > Birden çok giriş seçmek için, yolları **seçerken Shift** tuşunu basılı tutun.

   Seçilen yollar Güvenilen **konumlar listesinden** kaldırılır.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio Web İşareti olan projeleri açmadan önce kullanıcı [onayı isteminde bulundurabilirsiniz.](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)) Ek güvenlik için, web özniteliğinin Visual Studio veya güvenilir olarak atanmamış herhangi bir dosyayı veya klasörü açmadan önce kullanıcı onayı isteminde bulunacaktır. Dosya ve klasör denetimleri varsayılan olarak devre dışıdır.

> [!WARNING]
> Yine de dosyayı, klasörü veya çözümü onaylamadan önce güvenilir bir kişi veya güvenilir bir konumdan geldiğinden emin olun.

> [!NOTE]
> Visual Studio 2022 RC'de, dosyalarda, klasörlerde, projelerde ve çözümlerde güvenilmeyen kodun IDE'de açılmasına her zaman yönelik bir uyarı göstermek için Güven Ayarlar işlevini yeniden gözden geçirdik. Bu özellik varsayılan olarak devre dışıdır. Daha fazla bilgi edinmek için bu [Visual Studio 2022 sürümüne bakın.](?view=vs-2022&preserve-view=true)

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güven Ayarlar'ı** açın ve sağ **bölmede Ayarlar** Yapılandır bağlantısını seçin.

2. Dosya ve klasörler için istediğiniz denetim düzeyini seçin. Her biri için farklı denetimler olabilir. Seçenekler şunlardır:

   * **Doğrulama yok:** Visual Studio denetim gerçekleştirmez.

   * **Web özniteliğinin işaretini doğrulayın:** Dosya veya klasör web özniteliğinin işaretine sahipse, Visual Studio ve açma izni ister.

   * **Yolun güvenilir olduğunu doğrulama:** Dosya veya klasör yolu  Güvenilen Yollar listesinin parçası değilse, Visual Studio izin ister ve açma izni ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilen yollar ekleme

Güvenilen yollar eklemek için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güven Ayarlar'ı** açın ve sağ **bölmede Ayarlar** Yapılandır bağlantısını seçin.

2. Güven **Dosyası** iletişim kutusunda **Ekle'Ayarlar** ve ardından Dosya veya **Klasör'e** **tıklayın.**

3. Güvenilen listeye eklemek istediğiniz dosya veya klasörü bulun ve seçin.

   Dosya veya klasör yolu Güvenilen Yollar **listesinde** görünür.

   ![Güvenilen yollar eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları kaldırma

Güvenilen yolları kaldırmak için şu adımları izleyin:

1. Araç **Seçenekleri** >  > **Güven Ayarlar'ı** açın ve sağ **bölmede Ayarlar** Yapılandır bağlantısını seçin.

2. Güvenilen Yollar listesinde kaldırmak istediğiniz yolu seçin **ve kaldır'a** **tıklayın.**

   > [!TIP]
   > Birden çok giriş seçmek için, yolları **seçerken Shift** tuşunu basılı tutun.

   Seçilen yollar Güvenilen Yollar **listesinden** kaldırılır.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'da uygulama oluşturma](../walkthrough-building-an-application.md)
