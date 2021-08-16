---
title: Windows Information Protection muaf tut
description: hala kurumsal verileri kullanmasına izin verirken Windows Information Protection Visual Studio muaf tutma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0bd76144ba847a3ca191bb3be55d032b9bebd8c690d57ec5c95f01861fb4b469
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413251"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Visual Studio, wıp muaf tutulan uygulama olarak yapılandırma

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (wıp), kurumsal verilerin e-posta, sosyal medya ve genel bulut gibi uygulamalar aracılığıyla, kurumsal denetimin dışından sızmasını korumanıza yardımcı olur. WıP, ortamınızda veya diğer uygulamalarda değişiklik yapılmasına gerek kalmadan, kuruluşa ait cihazlarda ve kişisel cihazlarda yanlışlıkla veri sızıntılarına karşı korunmaya yardımcı olur.

Kurumsal verilerin korumasız ağ konumlarına gitmesini önlemek ve kişisel verileri şifrelemeyi önlemek için, WıP için *zenginetilen* uygulamalar beklenmektedir. Visual Studio, önceden bir uygulama değildir, bu nedenle muaf tutulan ortamlarda çalışmaz. Visual Studio wıp özellikli bir makinede çalışmasını sağlamak için bu makaledeki adımları izleyin.

## <a name="configure-vs-as-a-wip-exempt-app"></a>WıP muaf tutulan uygulama olarak VS 'yi yapılandırma

Visual Studio wıp kısıtlamalarından muaf tutabilirsiniz, ancak yine de kurumsal verileri kullanmasına izin verebilirsiniz. WıP muaf tutulan uygulamalar, bir IP adresi veya ana bilgisayar adı kullanarak kurumsal bulut kaynaklarına bağlanabilir. Hiçbir şifreleme uygulanmaz ve uygulama yerel dosyalara erişebilir.

Visual Studio wıp 'ten muaf tutmak için, [bir masaüstü uygulamasını muaf tutmak için adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy)izleyin.

## <a name="create-a-wip-exempt-applocker-policy-file"></a>WıP muaf olmayan AppLocker ilke dosyası oluşturma

Visual Studio birden çok ikilisi içerdiğinden, [wıp muaf bir AppLocker ilke dosyası oluşturun](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker, bir klasör içindeki tüm dosyalar için otomatik olarak kurallar oluşturmanıza olanak sağlar.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Enterprise bulut kaynak ilkesine AppCompat ekleme

Visual Studio ağınızdaki kurumsal verilere erişebileceği yeri belirtmek için, [korumalı uygulamalarınızın kurumsal verileri bulabileceği ve gönderebileceği yeri tanımlamak üzere aşağıdaki adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data)izleyin. Windows, bir ıp adresi aracılığıyla bulut kaynaklarına bağlantıları engellemeyi durdurmak için, bu \* ayara/AppCompat/dize eklediğinizden emin olun \* .

## <a name="see-also"></a>Ayrıca bkz.

- [WıP ile uygulama davranışı](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
