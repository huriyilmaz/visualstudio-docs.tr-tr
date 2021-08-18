---
title: Windows Information Protection'den muaf
description: Kurumsal verileri kullanmasına Visual Studio izin Windows Information Protection verilerden muaf tutularak nasıl muaf tutulacaklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: afd3473e26d7bb2c3d729cd3ea4df9a530b3a1bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137436"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>WiP Visual Studio uygulama olarak yapılandırma

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) kurumsal verilerin e-posta, sosyal medya ve genel bulut gibi, kuruluş denetimi dışında uygulamalar aracılığıyla sızmaya karşı korunmasına yardımcı olur. WIP, ortamınız veya diğer uygulamalarınız üzerinde değişiklik yapmadan kuruluşa ait cihazlarda ve kişisel cihazlarda yanlışlıkla veri sızıntısına karşı koruma sağlar.

*WIP* için açık uygulamaların, kurumsal verilerin korumasız ağ konumlara gidip kişisel verilerin şifrelenmesini önlemesi beklenir. Visual Studio, etkin bir uygulama olmadığı için, muaf olmadığı sürece WIP özellikli ortamlarda çalışmaz. WiP özellikli bir makinede çalışma Visual Studio için bu makaledeki adımları izleyin.

## <a name="configure-vs-as-a-wip-exempt-app"></a>VS'yi WIP muaf uygulaması olarak yapılandırma

WiP kısıtlamalarından Visual Studio, ancak yine de kurumsal verileri kullanmasına izin veebilirsiniz. WIP muaf uygulamaları bir IP adresi veya ana bilgisayar adı kullanarak kurumsal bulut kaynaklarına bağlanabilirsiniz. Şifreleme uygulanmaz ve uygulama yerel dosyalara erişebilirsiniz.

Bu Visual Studio WIP'den muaf etmek için, [bir masaüstü uygulamasını muaf tutulacak adımları izleyin.](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy)

## <a name="create-a-wip-exempt-applocker-policy-file"></a>WIP muaf AppLocker ilke dosyası oluşturma

Birden Visual Studio ikili dosya içeren bir [WIP muaf AppLocker ilke dosyası oluşturun.](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard) AppLocker, bir klasör içindeki tüm dosyalar için otomatik olarak kurallar oluşturmanizi sağlar.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>AppCompat'ı bulut Enterprise ilkesine ekleme

Ağ üzerinde kurumsal Visual Studio erişenin nerede olduğunu belirtmek için, korumalı uygulamalarınızı kurumsal verileri nerede bulup gönderebilirsiniz [tanımlamak için bu adımları izleyin.](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data) Ip Windows bulut kaynaklarına bağlantıları engellemesini engellemek için ayara / \* AppCompat \* / dizesini ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [WIP ile uygulama davranışı](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
