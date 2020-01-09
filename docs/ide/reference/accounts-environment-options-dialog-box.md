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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595910"
---
# <a name="accounts-environment-options-dialog-box"></a>Hesaplar, ortam, Seçenekler iletişim kutusu

Visual Studio 'da oturum açmak için kullandığınız hesaplarla ilgili çeşitli seçenekleri ayarlamak için bu sayfayı kullanın.

## <a name="personalization-account"></a>Kişiselleştirme hesabı

### <a name="synchronize-settings-across-devices"></a>Ayarları cihazlar arasında eşitler

Ayarlarınızı birden çok makine arasında eşitleyip eşitleyemeyeceğinizi belirtmek için bu seçeneği kullanın. Daha fazla bilgi için bkz. [Eşitlenmiş Ayarlar](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Cihaz kod akışını etkinleştir

Bu seçenek belirlendiğinde, **dosya** > **Hesap ayarları** sayfasında **bir hesap ekle** ' yi seçtiğinizde Visual Studio 'nun davranışı değişir. **Hesabınız Için oturum açma** SAYFASıNDA bir URL ve bir Web tarayıcısına yapıştırmanız için bir kod sağlayan bir iletişim kutusu görüntülenir. Bu seçenek, Visual Studio 'da düzenli olarak oturum açamazsınız, örneğin, Internet Explorer 'ın eski bir sürümünü kullanıyorsanız veya güvenlik duvarınız erişimi kısıtlarsa yararlıdır. Daha fazla bilgi için [birden çok kullanıcı hesabıyla çalışma](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Kayıtlı Azure bulutları

Bu bölümde, Visual Studio 'da oturum açmak için kullandığınız bir veya daha fazla hesaptan erişiminiz olan Azure bulut örnekleri gösterilmektedir. Örneğin, şirketinizin veri merkezinde Azure 'un özel bir örneğine erişiminiz olabilir. Veya Azure Çin 21 Vianet veya Azure ABD kamu gibi Azure 'un bir bağımsız veya kamu örneğine erişiminiz olabilir. Genel Azure bulut örneği listede varsayılan olarak görünür ve kaldıramazsınız.

**Ekle** düğmesini seçerek ek bir Azure bulutu kaydedin. **Yeni Azure bulutu Ekle** iletişim kutusu, bağlantı kurmak için kullanabileceğiniz birkaç Iyi bilinen Azure bulut örneğini listeler veya özel bir Azure uç noktasına URL 'yi girebilirsiniz.

![Yeni Azure bulut örneği Ekle](media/add-new-azure-cloud.png)

Ek bir Azure bulutu kaydettikten sonra, Visual Studio 'da oturum açtığınızda hangi Azure bulutunun oturum açmasını istediğinizi seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok bilgisayar üzerinde ayarları eşitler](../synchronized-settings-in-visual-studio.md)
- [Visual Studio’da oturum açma](../signing-in-to-visual-studio.md)
- [Birden çok kullanıcı hesabıyla çalışma](../work-with-multiple-user-accounts.md)
- [Ortam ayarları](../environment-settings.md)
