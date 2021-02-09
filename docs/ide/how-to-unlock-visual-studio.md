---
title: Deneme sürümü uzatma veya bir lisansı güncelleştirme
description: Visual Studio 'nun ücretsiz deneme sürümünü genişletmeyi, çevrimiçi bir abonelik veya ürün anahtarını kullanarak Visual Studio 'Yu nasıl kilitleyeceğinizi ve eski veya süresi dolmuş bir lisansı güncelleştirmeyi öğrenin.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 3dd2a688ef70064f44caccfd7c64150b7c649769
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869134"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Deneme sürümü uzatma veya bir lisansı güncelleştirme

[Visual Studio Professional veya Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) ücretsiz deneme sürümünü 30 gün boyunca değerlendirebilirsiniz. Oturum açarsanız deneme süresini 90 güne genişletebilirsiniz. (Visual Studio Community, deneme süresi olmadan ücretsizdir. Ancak, [lisansınızı güncel](#update-a-stale-license)tutmak için düzenli aralıklarla [oturum açmanız](signing-in-to-visual-studio.md) gerekir.)

Deneme süresi bittikten sonra Visual Studio 'Yu kullanmaya devam etmek için, [çevrimiçi bir abonelik](#use-an-online-subscription) veya [ürün anahtarı](#enter-a-product-key)ile bu dosyanın kilidini açın.

## <a name="use-an-online-subscription"></a>Çevrimiçi abonelik kullan

1. IDE 'nin sağ üst köşesindeki **oturum aç** düğmesini seçin (veya **Dosya**  >  **hesabı ayarları** ' na giderek **Hesap ayarları** iletişim kutusunu açın ve **oturum aç** düğmesini seçin).

1. Microsoft hesabı veya bir iş ya da okul hesabı için kimlik bilgilerini girin. Visual Studio, bir Visual Studio aboneliği veya hesabınızla ilişkili bir Azure DevOps organizasyonu bulur.

> [!IMPORTANT]
> **Takım Gezgini** araç penceresinden bir Azure DevOps kuruluşuna bağlandığınızda, Visual Studio ilişkili çevrimiçi abonelikleri otomatik olarak arar. Bir Azure DevOps kuruluşuna bağlandığınızda, hem Microsoft hem de iş veya okul hesaplarını kullanarak oturum açabilirsiniz. Bu Kullanıcı hesabı için çevrimiçi bir abonelik varsa, Visual Studio otomatik olarak IDE 'nin kilidini sizin için açar.

Visual Studio abonelikleri ve nasıl çalıştıkları hakkında daha fazla bilgi için, [abonelik DESTEĞI SSS](https://visualstudio.microsoft.com/subscriptions/support/) sayfasına bakın.

## <a name="enter-a-product-key"></a>Bir ürün anahtarı girin

1.   >  **Hesap ayarları** iletişim kutusunu açmak için dosya **hesabı ayarları** ' nı seçin ve ardından **bir ürün anahtarı bağlantısı olan lisansı** seçin.

1. Belirtilen alana ürün anahtarını girin.

> [!TIP]
> Visual Studio 'nun yayın öncesi sürümlerinde ürün anahtarları yoktur. Yayın öncesi sürümleri kullanmak için IDE 'de oturum açmanız gerekir.

Visual Studio için Visual Studio ürün anahtarları ve bunların nasıl alınacağı hakkında daha fazla bilgi için bkz. [Visual Studio abonelikleri 'nde ürün anahtarlarını kullanma](/visualstudio/subscriptions/product-keys) sayfası.

## <a name="update-a-stale-license"></a>Eski lisansı güncelleştirme

Visual Studio 'da "lisansınızın eski ve güncelleştirilmiş olması gerektiğini belirten bir ileti görebilirsiniz.

![Visual Studio eski lisans iletisi](../ide/media/vs2017_stale-license.png)

Bu ileti, aboneliğiniz hala geçerli olabileceğinden, Visual Studio 'Nun aboneliğinizi güncel tutmak için kullandığı lisans belirtecinin yenilenmediği anlamına gelir. Visual Studio, aşağıdaki nedenlerden biri nedeniyle lisansın eski olduğunu bildiriyor:

* Visual Studio 'Yu kullanmadınız veya internet 'e uzun bir süre boyunca bağlanmadınız.
* Visual Studio oturumunu kapattınız.

Lisans belirteci eski olmadan önce, Visual Studio önce kimlik bilgilerinizi yeniden girmeniz isteyen bir uyarı iletisi gösterir.

Kimlik bilgilerinizi yeniden girmeyin, belirteç eskgeç çalışmaya başlar ve **Hesap ayarları** iletişim kutusu, belirtecinizin süresi dolmadan kaç gün kaldığını gösterir. Belirtecin süresi dolduktan sonra, Visual Studio 'Yu kullanmaya devam edebilmeniz için önce hesap kimlik bilgilerinizi yeniden girmeniz gerekir.

> [!Important]
> Sınırlı veya internet erişimi olmayan ortamlarda genişletilmiş dönemler için Visual Studio kullanıyorsanız, kesintiye uğramamak için Visual Studio 'Nun kilidini açmak üzere bir ürün anahtarı kullanmanız gerekir.

## <a name="update-an-expired-license"></a>Süre dolma lisansı güncelleştirme

Aboneliğinizin süresi dolmuşsa ve Visual Studio için artık erişim haklarınız yoksa, aboneliğinizi yenilemeniz veya aboneliğine sahip başka bir hesap eklemeniz gerekir. Kullanmakta olduğunuz lisans hakkında daha fazla bilgi görmek için, **Dosya**  >  **hesabı ayarları** ' na gidin ve iletişim kutusunun sağ tarafındaki lisans bilgilerine bakın. Farklı bir hesapla ilişkili başka bir aboneliğiniz varsa, **Hesap Ekle** bağlantısı ' nı seçerek bu hesabı iletişim kutusunun sol tarafındaki **tüm hesaplar** listesine ekleyin.

## <a name="get-support"></a>Destek alın

Bazen, şeyler yanlış gider. Bir sorunla karşılaşırsanız, bazı destek seçenekleri aşağıda verilmiştir:

* [Sorun bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak ürün sorunlarını bildirin.
* Abonelikler, hesaplar ve faturalandırma hakkında soruların yanıtlarını, [abonelikler destek SSS](https://visualstudio.microsoft.com/subscriptions/support/)' de bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’da oturum açma](../ide/signing-in-to-visual-studio.md)
* [Visual Studio sürümlerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/)
* [Visual Studio abonelikleri hakkında daha fazla bilgi edinin](/visualstudio/subscriptions/)
