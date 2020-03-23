---
title: Windows Bilgi Korumasından muaf
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4eb454f641b5bef7273464d605fb194f650790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588570"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Visual Studio'yı WIP'den muaf bir uygulama olarak yapılandırın

[Windows Bilgi Koruması](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP), kurumsal verilerin e-posta, sosyal medya ve genel bulut gibi kurumsal kontrolün dışında olan uygulamalar aracılığıyla sızdırılmasına karşı korunmasına yardımcı olur. WIP, ortamınızda veya diğer uygulamalarda değişiklik gerektirmeden, kuruluşa ait cihazlarda ve kişisel cihazlarda kazara veri sızıntısına karşı koruma sağlar.

WIP için *aydınlanmış* uygulamaların kurumsal verilerin korunmasız ağ konumlarına girmesini engellemesi ve kişisel verileri şifrelemesini önlemesi beklenir. Visual Studio aydınlanmış bir uygulama değildir, bu nedenle siz muaf olmadıkça WIP özellikli ortamlarda çalışmaz. Visual Studio'nun WIP özellikli bir makinede çalışmasını sağlamak için bu makaledeki adımları izleyin.

## <a name="configure-vs-as-a-wip-exempt-app"></a>VS'yi WIP'den muaf bir uygulama olarak yapılandırın

Visual Studio'dan WIP kısıtlamalarından muaf olabilir, ancak yine de kurumsal verileri kullanmasına izin verebilirsiniz. WIP'den muaf uygulamalar, bir IP adresi veya ana bilgisayar adı kullanarak kurumsal bulut kaynaklarına bağlanabilir. Şifreleme uygulanmaz ve uygulama yerel dosyalara erişebilir.

Visual Studio'yu WIP'den muaf tutmak [için bir masaüstü uygulamasından muaf tutmak için aşağıdaki adımları](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy)izleyin.

## <a name="create-a-wip-exempt-applocker-policy-file"></a>WIP'den muaf AppLocker ilke dosyası oluşturma

Visual Studio birden çok ikili içerdiğinden, [WIP'den muaf bir AppLocker ilke dosyası oluşturun.](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard) AppLocker, bir klasördeki tüm dosyalar için otomatik olarak kurallar oluşturmanıza olanak tanır.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Kurumsal bulut kaynak ilkesine AppCompat ekleme

Visual Studio'nun anızdaki kurumsal verilere nerede erişebileceğini belirtmek [için, korumalı uygulamalarınızın kurumsal verileri nerede bulup gönderebileceğini tanımlamak için](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data)aşağıdaki adımları izleyin. Windows'un IP adresi aracılığıyla bulut kaynaklarına bağlantılarını engellemesini engellemek\*için,\*ayara / AppCompat / dize eklediğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [WIP ile uygulama davranışı](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
