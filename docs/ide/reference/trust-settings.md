---
title: dosyalar ve klasörler için güven Ayarlar
description: Visual Studio güvenli tutulacak dosyalar ve klasörler için güven ayarlarını değiştirmeyi öğrenin.
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
ms.openlocfilehash: 6b0f907f7bf6526cbf671c2acb5e4d3d91f6a5ed
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001305"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosyalar ve klasörler için güven ayarlarını yapılandırma

::: moniker range=">=vs-2022"

Visual Studio 2022 ' de, ıde 'de güvenilir olmayan kod açıldığında bir uyarı göstermek için **güven Ayarlar** işlevselliğini yeniden yaptık. 

Yazılım geliştiricileri, kötü amaçlı yazılım tarafından giderek daha fazla hedeflenmiştir. yeni **güven Ayarlar** işlevselliği, bilmediğiniz kodu işlemenin riskleri hakkında daha fazla bilgi sahibi olmak ve içeriği açan kötü amaçlı aktörlere karşı koruma sağlamaya yardımcı olur. (örneğin, depolar, çözümler, projeler ve dosyalar) Visual Studio ile uygulama oluşturma ve çalıştırma gibi senaryoları hedefler. 

**Güvenilen konumlar** özelliği varsayılan olarak etkin değildir. 

## <a name="enable-trusted-locations"></a>Güvenilen konumları etkinleştir

**Güvenilen konumlar** özelliğini etkinleştirmek için şu adımları izleyin:

1. açık **araçlar** > **seçenekler** > **güven Ayarlar**.

2. **Güven ilkeleri** bölmesinde **içerik açmadan önce güven kararı iste**' yi seçin.

:::image type="content" source="media/vs-2022/trusted-settings-options-dialog.png" alt-text="güven Ayarlar seçeneklerini kullanarak güvenilen konumların nasıl etkinleştirileceğini gösteren ekran görüntüsü.":::

> [!NOTE]
> **güveni atla geçici konumlar için denetim Visual Studio otomatik olarak** seçenek varsayılan olarak etkindir, ancak **içerik açmadan önce bir güven kararı gerektir** seçeneği de etkin olmadığı müddetçe hiçbir etkisi olmaz.

etkinleştirildikten sonra, *güvenilir* olarak belirlenmemiş içeriği açmaya çalışırken Visual Studio algılar ve güvenlik etkilerine ilişkin sizi uyaran yeni bir iletişim kutusu gösterir.

:::image type="content" source="media/vs-2022/trusted-settings-warning-dialog.png" alt-text="güven Ayarlar uyarı iletişim kutusunun ekran görüntüsü.":::

## <a name="manage-trust-settings"></a>Güven ayarlarını yönetme

Güvenilen konumların nasıl ekleneceği ve bunları nasıl kaldıracekleri aşağıda verilmiştir.

### <a name="add-trusted-locations"></a>Güvenilen Konum Ekle

özelliği etkinleştirdikten sonra, Visual Studio 2022 ile açtığınız tüm içerikler, **güvenilir konumlar** listesine eklenene kadar güvenilmeyen olarak değerlendirilir.  Bir klasör konumuna doğrudan *Uyarı* iletişim kutusundan güvenebilirsiniz. Aşağıdaki adımları uygulayın:

1. Güven **düzeyi** açılan listesinden, güvenmek istediğiniz klasörü (geçerli klasör veya üst klasör) seçin.

   :::image type="content" source="media/vs-2022/trust-folder-trust-level.png" alt-text="Uyarı iletişim kutusunda bir klasöre nasıl güvenilileceğini gösteren ekran görüntüsü.":::

1. İletişim kutusunda **güven ve devam** düğmesini seçin.

   Visual Studio, klasör yolunu **araç**  > **seçenekleri** > **güven Ayarlar** güvenilen konumlar listesine ekler.

**güvenilen konumlara** ayrıca, **güven Ayarlar** iletişim kutusundan klasörler ekleyebilirsiniz. Aşağıdaki adımları uygulayın:

1. açık **araçlar**  >  **seçenekler**  >  **güven Ayarlar**. **güven Ayarlar** , *uyarı* iletişim kutusundan **güven ayarlarını yönet** ' i seçerek de açabilirsiniz.

2. Sağ **Güvenilen ilkeler** bölmesinde **Klasör Ekle** ' yi seçin.

3. Öğesine gidin ve güvenilen listeye eklemek istediğiniz klasörü seçin.

   Klasör yolu, **Güvenilen konumlar** listesinde görünür. El ile eklediğiniz bu klasör, **Yerel Kullanıcı** **tarafından güvenilen** olarak listelenir.
   
   :::image type="content" source="media/vs-2022/trusted-locations.png" alt-text="* * Güvenilen konumlara * * eklenen bir klasörü gösteren ekran görüntüsü.":::

> [!NOTE]
> **güvenilen konumlar** özelliğini etkinleştirdikten sonra, Visual Studio içinde oluşturduğunuz içeriğin klasör yolu, **güvenilen konumlar** listesine otomatik olarak eklenir. Bu klasör yolu, **sistem** **tarafından güvenilen** olarak listelenir.
> 
> :::image type="content" source="media/vs-2022/trusted-by-values.png" alt-text="* * Güvenilir konumlar * * listesinde * * Yerel Kullanıcı * ve * System * tarafından güvenilen * * değerleri gösteren ekran görüntüsü.":::

### <a name="remove-trusted-locations"></a>Güvenilen konumları kaldır

Güvenilen konumları kaldırmak için şu adımları izleyin:

1. açık **araçlar** > **seçenekler** > **güven Ayarlar**.

2. **Güvenilen konumlar** listesinde kaldırmak istediğiniz yolu seçin ve ardından **Kaldır**' a tıklayın.

   > [!TIP]
   > Birden çok giriş seçmek için, yolları seçerken **Shift** tuşunu basılı tutun.

   Seçilen yollar, **güvenilir konumlar** listesinden kaldırılır.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio, [Web 'e işaret](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))eden projeleri açmadan önce kullanıcı onayını ister. ek güvenlik için, web özniteliği işaretine sahip herhangi bir dosyayı veya klasörü açmadan önce veya *güvenilir* olarak belirlenmemiş bir dosya ya da klasör açmadan önce kullanıcı onayını isteyecek şekilde Visual Studio yapılandırabilirsiniz. Dosya ve klasör denetimleri varsayılan olarak devre dışıdır.

> [!WARNING]
> Dosyayı, klasörü veya çözümü onaylamadan önce güvenilen bir kişiden veya güvenilir bir konumdan geldiğinden emin olmalısınız.

> [!NOTE]
> Visual Studio 2022 ' de, dosyalarda, klasörlerde, projelerde ve çözümlerinde güvenilir olmayan kodların ıde 'de açılmasına her seferinde bir uyarı göstermek için güven Ayarlar işlevselliğini yeniden yaptık. Bu özellik varsayılan olarak devre dışıdır. daha fazla bilgi edinmek için [bu sayfanın Visual Studio 2022 sürümüne](?view=vs-2022&preserve-view=true)bakın.

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
