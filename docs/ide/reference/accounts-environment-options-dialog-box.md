---
title: Hesap seçenekleri başvurusu
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595910"
---
# <a name="accounts-environment-options-dialog-box"></a>Hesaplar, Çevre, Seçenekler iletişim kutusu

Visual Studio'da oturum açmanız için kullandığınız hesaplarla ilgili çeşitli seçenekler ayarlamak için bu sayfayı kullanın.

## <a name="personalization-account"></a>Kişiselleştirme hesabı

### <a name="synchronize-settings-across-devices"></a>Ayarları cihazlar arasında eşitleme

Ayarlarınızı birden çok makine arasında eşitleyip eşitlemeyeceğinizi belirtmek için bu seçeneği kullanın. Daha fazla bilgi için [Senkronize ayarlara](../../ide/synchronized-settings-in-visual-studio.md)bakın.

### <a name="enable-device-code-flow"></a>Aygıt kodu akışını etkinleştirme

Bu seçenek seçildiğinde, **Dosya** > **Hesabı Ayarları** sayfasında hesap **ekle'yi** seçtiğinizde Visual Studio'nun davranışı değişir. **Hesap sayfanızda Oturum Aç'ı** görmek yerine, size oturum açmak için bir URL ve oturum açmak için bir web tarayıcısına yapıştıracak bir kod veren bir iletişim kutusu sunulur. Bu seçenek, Visual Studio'da düzenli olarak oturum açamadığınız durumlarda (örneğin, Internet Explorer'ın eski bir sürümünü kullanıyorsanız veya güvenlik duvarınız erişimi kısıtlıyorsa) yararlıdır. Daha fazla bilgi için bkz: [Birden çok kullanıcı hesabıyla çalışma.](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow)

## <a name="registered-azure-clouds"></a>Kayıtlı Azure bulutları

Bu bölümde, Visual Studio'da oturum açtırmak için kullandığınız hesaplardan biri veya birkaçı aracılığıyla erişebildiğiniz Azure bulut örnekleri gösterilmektedir. Örneğin, şirketinizin veri merkezinde özel bir Azure örneğine erişiminiz olabilir. Veya Azure China 21 Vianet veya Azure ABD Hükümeti gibi azure'un egemen veya devlet tarafından bir örneğine erişebilirsiniz. Genel Azure bulut örneği listede varsayılan olarak görünür ve bunu kaldıramazsınız.

**Ekle** düğmesini seçerek ek bir Azure bulutu kaydedin. **Yeni Azure Bulutu Ekle** iletişim kutusu, bağlanabileceğiniz birkaç tanınmış Azure bulut örneğini listeler veya URL'yi özel bir Azure bitiş noktasına girebilirsiniz.

![Yeni Azure bulut örneği ekleme](media/add-new-azure-cloud.png)

Ek bir Azure bulutu kaydettikten sonra, Visual Studio'da oturum açtığınızda hangi Azure bulutunda oturum açtırabileceğinizi seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayarları birden çok bilgisayarda eşitleme](../synchronized-settings-in-visual-studio.md)
- [Visual Studio’da oturum açma](../signing-in-to-visual-studio.md)
- [Birden çok kullanıcı hesabıyla çalışma](../work-with-multiple-user-accounts.md)
- [Ortam ayarları](../environment-settings.md)
