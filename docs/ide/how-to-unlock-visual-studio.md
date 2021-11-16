---
title: Deneme sürümü uzatma veya bir lisansı güncelleştirme
description: Visual Studio ücretsiz deneme sürümünü genişletmeyi, çevrimiçi bir abonelik veya ürün anahtarını kullanarak Visual Studio kilidini açıp eski veya süresi dolmuş bir lisansı güncelleştirmeyi öğrenin.
ms.date: 12/18/2019
ms.topic: how-to
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0d3eb53ec6fc73cb72d31d1dfd31f9ed1fc6e906
ms.sourcegitcommit: bfae1f88c278835e26f3200cfced769be3191fc4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2021
ms.locfileid: "132535067"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Deneme sürümü uzatma veya bir lisansı güncelleştirme

[Visual Studio Professional veya Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) ücretsiz deneme sürümünü 30 gün boyunca değerlendirebilirsiniz. Oturum açarsanız deneme süresini 90 güne genişletebilirsiniz. (Visual Studio Community deneme süresi olmadan ücretsizdir. Ancak, [lisansınızı güncel](#update-a-stale-license)tutmak için düzenli aralıklarla [oturum açmanız](signing-in-to-visual-studio.md) gerekir.)

deneme süresi bittikten sonra Visual Studio kullanmaya devam etmek için, [çevrimiçi bir abonelik](#use-an-online-subscription) veya [ürün anahtarı](#enter-a-product-key)ile bu dosyanın kilidini açın.

## <a name="use-an-online-subscription"></a>Çevrimiçi abonelik kullan

1. ıde 'nin sağ üst köşesindeki **oturum aç** düğmesini seçin (veya Ayarlar **dosya**  >  **hesabı** ' na giderek **hesap Ayarlar** iletişim kutusunu açın ve **oturum aç** düğmesini seçin.

1. Microsoft hesabı veya bir iş ya da okul hesabı için kimlik bilgilerini girin. Visual Studio, hesabınızla ilişkili bir Visual Studio aboneliğini veya Azure DevOps organizasyonunu bulur.

> [!IMPORTANT]
> Visual Studio, **Takım Gezgini** aracı penceresinden bir Azure DevOps kuruluşa bağlandığınızda ilişkili çevrimiçi abonelikleri otomatik olarak arar. bir Azure DevOps kuruluşa bağlandığınızda, hem Microsoft hem de iş veya okul hesaplarını kullanarak oturum açabilirsiniz. bu kullanıcı hesabı için bir çevrimiçi abonelik varsa Visual Studio otomatik olarak ıde 'nin kilidini sizin için açar.

Visual Studio abonelikleri ve nasıl çalıştıkları hakkında daha fazla bilgi için, [abonelikler destek sss](https://visualstudio.microsoft.com/subscriptions/support/) sayfasına bakın.

## <a name="enter-a-product-key"></a>Bir ürün anahtarı girin

1.   >  **hesap Ayarlar** iletişim kutusunu açmak için dosya **hesabı Ayarlar** seçin ve ardından **bir ürün anahtarı bağlantısı olan lisansı** seçin.

1. Belirtilen alana ürün anahtarını girin.

> [!TIP]
> Visual Studio yayın öncesi sürümlerinde ürün anahtarları yoktur. Yayın öncesi sürümleri kullanmak için IDE 'de oturum açmanız gerekir.

Visual Studio Visual Studio ürün anahtarları ve bunların nasıl alınacağı hakkında daha fazla bilgi için bkz. [Visual Studio abonelikleri içindeki ürün anahtarlarını kullanma](/visualstudio/subscriptions/product-keys) sayfası.

## <a name="update-a-stale-license"></a>Eski lisansı güncelleştirme

şöyle bir Visual Studio ileti görebilirsiniz: "lisansınızın eski ve güncelleştirilmiş olması gerekir."

![eski lisans iletisini Visual Studio](../ide/media/vs2017_stale-license.png)

bu ileti, aboneliğiniz hala geçerli olabileceğinden, aboneliğinizin güncel tutulması için Visual Studio tarafından kullanılan lisans belirtecinin yenilenmediği anlamına gelir. Visual Studio, aşağıdaki nedenlerden biri nedeniyle lisansın eski olduğunu bildiriyor:

* Visual Studio kullanmadınız veya internet 'e uzun bir süre boyunca bağlanmadınız.
* Oturumunuz Visual Studio kalmadı.

lisans belirteci eski olmadan önce Visual Studio önce, kimlik bilgilerinizi yeniden girmeniz isteyen bir uyarı iletisi gösterir.

kimlik bilgilerinizi yeniden girmeyin, belirteç eskgeç çalışmaya başlar ve **hesap Ayarlar** iletişim kutusu, belirtecinizin süresi dolmadan kaç gün kaldığını gösterir. Belirtecin süresi dolduktan sonra, Visual Studio kullanmaya devam edebilmeniz için önce hesap için kimlik bilgilerinizi yeniden girmeniz gerekir.

> [!Important]
> sınırlı veya internet erişimi olmayan ortamlarda uzatılmış dönemler için Visual Studio kullanıyorsanız, kesintiye uğramaması için Visual Studio kilidini açmak üzere bir ürün anahtarı kullanmanız gerekir.

## <a name="update-an-expired-license"></a>Süre dolma lisansı güncelleştirme

aboneliğinizin süresi dolmuşsa ve artık Visual Studio erişim haklarınız yoksa, aboneliğinizi yenilemeniz veya aboneliği olan başka bir hesap eklemeniz gerekir. kullanmakta olduğunuz lisans hakkında daha fazla bilgi görmek için **dosya**  >  **hesabı Ayarlar** gidin ve iletişim kutusunun sağ tarafındaki lisans bilgilerine bakın. Farklı bir hesapla ilişkili başka bir aboneliğiniz varsa, **Hesap Ekle** bağlantısı ' nı seçerek bu hesabı iletişim kutusunun sol tarafındaki **tüm hesaplar** listesine ekleyin.

## <a name="get-support"></a>Destek alın

Bazen, şeyler yanlış gider. Bir sorunla karşılaşırsanız, bazı destek seçenekleri aşağıda verilmiştir:

* [Sorun bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak ürün sorunlarını bildirin.
* Abonelikler, hesaplar ve faturalandırma hakkında soruların yanıtlarını, [abonelikler destek SSS](https://visualstudio.microsoft.com/subscriptions/support/)' de bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’da oturum açma](../ide/signing-in-to-visual-studio.md)
* [Visual Studio sürümlerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/)
* [Visual Studio abonelikler hakkında daha fazla bilgi edinin](/visualstudio/subscriptions/)
