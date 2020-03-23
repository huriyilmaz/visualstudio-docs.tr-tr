---
title: Deneme sürümü uzatma veya bir lisansı güncelleştirme
description: Visual Studio'nun ücretsiz deneme sürümünü nasıl genişleteceklerini, Visual Studio'nun kilidini açmak için çevrimiçi abonelik veya ürün anahtarını nasıl kullanacağınızı ve eski veya süresi dolmuş bir lisansı nasıl güncelleştirini öğrenin.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027573"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Deneme sürümü uzatma veya bir lisansı güncelleştirme

[Visual Studio Professional veya Visual Studio Enterprise'ın](https://visualstudio.microsoft.com/vs/compare/) ücretsiz deneme sürümünü 30 gün boyunca değerlendirebilirsiniz. Oturum açsanız deneme süresini 90 güne uzatabilirsiniz. (Visual Studio Community deneme süresi olmadan ücretsizdir. Ancak, lisansınızı güncel tutmak için düzenli olarak [oturum açmanız](signing-in-to-visual-studio.md) [gerekmektedir](#update-a-stale-license).)

Deneme süresi sona erdikten sonra Visual Studio'u kullanmaya devam etmek için, [çevrimiçi abonelik](#use-an-online-subscription) veya [ürün anahtarıyla](#enter-a-product-key)kilidini açın.

## <a name="use-an-online-subscription"></a>Çevrimiçi abonelik kullanma

1. IDE'nin sağ üst köşesindeki **Oturum Aç** düğmesini seçin (veya **Hesap Ayarları** iletişim kutusunu açmak için **Dosya** > **Hesap Ayarları'na** gidin ve ardından **Oturum Aç** düğmesini seçin).

1. Microsoft hesabı veya iş veya okul hesabının kimlik bilgilerini girin. Visual Studio, hesabınızla ilişkili bir Visual Studio aboneliği veya Azure DevOps kuruluşu bulur.

> [!IMPORTANT]
> Visual Studio, **Team Explorer** araç penceresinden bir Azure DevOps kuruluşuna bağlandığınızda ilişkili çevrimiçi abonelikleri otomatik olarak arar. Bir Azure DevOps kuruluşuna bağlandığınızda, hem Microsoft'u hem de iş veya okul hesaplarını kullanarak oturum açabilirsiniz. Bu kullanıcı hesabı için çevrimiçi bir abonelik varsa, Visual Studio sizin için Otomatik olarak IDE kilidini açar.

Visual Studio abonelikleri ve nasıl çalıştıkları hakkında daha fazla bilgi için [Abonelikleri Destek SSS](https://visualstudio.microsoft.com/subscriptions/support/) sayfasına bakın.

## <a name="enter-a-product-key"></a>Bir ürün anahtarı girin

1. **Hesap Ayarları** iletişim kutusunu açmak için **Dosya** > **Hesabı Ayarları'nı** seçin ve ardından Ürün **Anahtarı bağlantısıyla Lisansı** seçin.

1. Sağlanan alana ürün anahtarını girin.

> [!TIP]
> Visual Studio'nun ön sürüm sürümlerinde ürün anahtarları yoktur. Ön sürüm sürümlerini kullanmak için IDE'de oturum açmanız gerekir.

Visual Studio için Visual Studio ürün anahtarları ve bunları nasıl alacağınız hakkında daha fazla bilgi için Visual Studio abonelikleri sayfasında [ürün anahtarlarını kullanma](/visualstudio/subscriptions/product-keys) sayfasına bakın.

## <a name="update-a-stale-license"></a>Eski bir lisansı güncelleştirme

Visual Studio'da "Lisansınız bayatladı ve güncellenmesi gerekiyor" yazan bir ileti görebilirsiniz.

![Visual Studio bayat lisans mesajı](../ide/media/vs2017_stale-license.png)

Bu ileti, aboneliğiniz hala geçerli olsa da Visual Studio'nun aboneliğinizi güncel tutmak için kullandığı lisans belirteci nin yenilenmediğini belirtir. Visual Studio, aşağıdaki nedenlerden biri nedeniyle lisansın bayat olduğunu bildirir:

* Visual Studio'yu kullanmadınız veya uzun bir süre internete bağlanmadın.
* Visual Studio'dan çıkış imzaladın.

Lisans belirteci eskimeden önce Visual Studio, kimlik bilgilerinizi yeniden girmenizi isteyen bir uyarı iletisi gösterir.

Kimlik bilgilerinizi yeniden girmezseniz, belirteç eskimeye başlar ve **Hesap Ayarları** iletişim kutusu, belirteç süresinin dolmasına kaç gün kaldığını bildirir. Jetonuzun süresi dolduktan sonra, Visual Studio'yu kullanmaya devam etmeden önce hesap için kimlik bilgilerinizi yeniden girmeniz gerekir.

> [!Important]
> Visual Studio'yı sınırlı veya internet erişimi olmayan ortamlarda uzun süre kullanıyorsanız, kesintiye uğramamak için Visual Studio'nun kilidini açmak için bir ürün anahtarı kullanmalısınız.

## <a name="update-an-expired-license"></a>Süresi dolan bir lisansı güncelleştirme

Aboneliğinizin süresi dolduysa ve Artık Visual Studio'ya erişim haklarınız yoksa, aboneliğinizi yenilemeniz veya aboneliği olan başka bir hesap eklemeniz gerekir. Kullandığınız lisans hakkında daha fazla bilgi görmek için **Dosya** > **Hesabı Ayarları'na** gidin ve iletişim kutusunun sağ tarafındaki lisans bilgilerine bakın. Farklı bir hesapla ilişkili başka bir aboneliğiniz varsa, **hesap ekle** bağlantısını seçerek bu hesabı iletişim kutusunun sol tarafındaki **Tüm Hesaplar** listesine ekleyin.

## <a name="get-support"></a>Destek alın

Bazen işler ters gider. Bir sorunla karşılaşırsanız, bazı destek seçenekleri şunlardır:

* Sorun Bildir aracını kullanarak ürün sorunlarını [bildirin.](how-to-report-a-problem-with-visual-studio.md)
* [Abonelikleri Destek SSS'sinde](https://visualstudio.microsoft.com/subscriptions/support/)abonelikler, hesaplar ve faturalandırma yla ilgili soruların yanıtlarını bulun.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’da oturum açma](../ide/signing-in-to-visual-studio.md)
* [Visual Studio sürümlerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/)
* [Visual Studio abonelikleri hakkında daha fazla bilgi edinin](/visualstudio/subscriptions/)
