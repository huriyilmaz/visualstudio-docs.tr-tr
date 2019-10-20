---
title: Windows Information Protection muaf tut
ms.date: 06/01/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab08ea1f3a4c66c026de781f2d39a0bc9d08af96
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650863"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Visual Studio 'Yu WıP muaf tutulan bir uygulama olarak yapılandırma

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP), kurumsal verilerin e-posta, sosyal medya ve genel bulut gibi kurumsal denetim dışındaki uygulamalar aracılığıyla sızmasını korumanıza yardımcı olur. WıP, ortamınızda veya diğer uygulamalarda değişiklik yapılmasına gerek kalmadan, kuruluşa ait cihazlarda ve kişisel cihazlarda yanlışlıkla veri sızıntılarına karşı korunmaya yardımcı olur.

Kurumsal verilerin korumasız ağ konumlarına gitmesini önlemek ve kişisel verileri şifrelemeyi önlemek için, WıP için *zenginetilen* uygulamalar beklenmektedir. Visual Studio önceden tanıtılan bir uygulama değildir; bu nedenle, muaf tutulması için etkin olmayan ortamlarda çalışmaz. Visual Studio 'Nun WıP özellikli bir makinede çalışmasını sağlamak için bu makaledeki adımları izleyin.

## <a name="configure-vs-as-a-wip-exempt-app"></a>WıP muaf tutulan uygulama olarak VS 'yi yapılandırma

Visual Studio 'Yu WıP kısıtlamalarından muaf tutabilirsiniz, ancak yine de kurumsal verileri kullanmasına izin verebilirsiniz. WıP muaf tutulan uygulamalar, bir IP adresi veya ana bilgisayar adı kullanarak kurumsal bulut kaynaklarına bağlanabilir. Hiçbir şifreleme uygulanmaz ve uygulama yerel dosyalara erişebilir.

Visual Studio 'Yu WıP 'ten muaf tutmak için, [bir masaüstü uygulamasını muaf tutmak için adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy)izleyin.

## <a name="create-a-wip-exempt-applocker-policy-file"></a>WıP muaf olmayan AppLocker ilke dosyası oluşturma

Visual Studio birden çok ikili dosya içerdiğinden, [WIP muaf bir AppLocker ilke dosyası oluşturun](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker, bir klasör içindeki tüm dosyalar için otomatik olarak kurallar oluşturmanıza olanak sağlar.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Kurumsal bulut kaynak ilkesine AppCompat ekleme

Visual Studio 'Nun ağınızdaki kurumsal verilere erişebileceği yeri belirtmek için, [korumalı uygulamalarınızın kurumsal verileri bulabileceği ve gönderebileceği yeri tanımlamak üzere aşağıdaki adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data)izleyin. Windows 'un bir IP adresi aracılığıyla bulut kaynaklarına bağlantıları engellemesini durdurmak için,/\*AppCompat \*/dizesini ayara eklediğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [WıP ile uygulama davranışı](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)