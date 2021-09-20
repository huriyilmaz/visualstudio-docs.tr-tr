---
title: Visual Studio aboneliklerde Terminal Hizmetleri aracılığıyla İnternet tanıtımları| Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/21/2021
ms.topic: conceptual
description: Terminal Hizmetleri aracılığıyla İnternet tanıtımlarını desteklemek ve RDS erişimini etkinleştirmek için ürün anahtarlarını kullanmayı öğrenin
ms.openlocfilehash: 0391de091cd3b836fbe38afce903b52584da4b5a
ms.sourcegitcommit: c2afe12aaf04456846613550b367cf86eb082f4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2021
ms.locfileid: "128002308"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Terminal Hizmetleri aracılığıyla İnternet tanıtımları
Bir Visual Studio aboneliğiyle, son kullanıcılara Terminal Hizmetleri (Windows Server 2003 veya Windows Server 2008) veya Uzak Masaüstü Hizmetleri (Windows Server 2008 R2 ve sonrası) aracılığıyla programlarının İnternet tanıtımlarına erişim izni ve ardından izin verilir. Gösteriminize aynı anda 200'e kadar anonim kullanıcı bu şekilde erişebilirsiniz. Gösteriminiz üretim verilerini kullanmamalı. Visual Studio aboneler uygulamalarını son kullanıcılara göstermek için lisanslıdır. Terminal Hizmetleri (TS) veya Uzak Masaüstü Hizmetleri (RDS) kullanan bu İnternet gösterimi, Visual Studio aboneliği olmayan son kullanıcıların, yazılım Visual Studio abonelikleri aracılığıyla lisanslandıklarında tanıtım uygulamasıyla etkileşim kuramalarına neden olan tek senaryodur.

Bu, geliştirme/test haklarına ek olarak, Visual Studio sayıda RDS veya TS bağlantısı kullanabilir.

## <a name="enabling-rds-access"></a>RDS Erişimini Etkinleştirme
Visual Studio aboneler, abone portalının Ürün Anahtarları sekmesine verilen bir ürün anahtarını girerek RDS aracılığıyla [](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) Windows Sunucusuna erişen kullanıcı [sayısını artırabilir.](https://my.visualstudio.com?wt.mc_id=o~msft~docs) Bir ürün anahtarı almak için Ürün Anahtarları sayfasına bağlanarak aşağı kaydırarak Windows Server'ın sürümüne gidin. "Windows Server < sürümü > R2 Uzak Masaüstü Hizmetleri < bağlantılarda >" seçeneğini bulun ve Talep Anahtarı **bağlantısına** tıklayın. Örneğin, Windows Server 2012 R2 üzerinde RDS kullanıyorsanız ve dağıtımınız kullanıcı CAL'lerini kullanıyorsa, "Windows Server 2012 Uzak Masaüstü Hizmetleri bağlantıları (50)" seçin.
Windows Server 2008 R2 için her türün beş anahtarı kullanılabilir ve her anahtar 20 bağlantı destekler. Bu Windows Server 2012 R2 için her tür için dört anahtar sağlır ve her biri 50 bağlantı destekler.

## <a name="to-enable-additional-connections-in-windows-server"></a>Windows Server'da ek bağlantıları etkinleştirmek için:
1. Sunucu Yöneticisi'ni açın.
2. Sol gezinti bölmesinde Sunucular listesini açın.
3. Lisans sunucunuza sağ tıklayın ve "Lisansları Yükle"yi seçin.
4. Sihirbazdaki adımları izleyin.  Sözleşme türünü seçerseniz "Lisans Paketi (perakende)" öğesini seçin ve MY portalında edinilen ürün anahtarını girin.

Son kullanıcılar, aşağıdaki koşullar karşı olursa RDS üzerinden uygulamalara bağlanabilirsiniz:
- Kullanıcıların anonim olması (kimliği doğrulanmamış bir durumda) olması gerekir.
- Bağlantıların İnternet üzerinden olması gerekir.
- Uygulamanın tanıtımları için en fazla 200 eş zamanlı kullanıcı bağlantısı kullanılabilir.
- Kullanıcı bağlantılarını etkinleştirmek için ürün anahtarlarının bir abone tarafından Visual Studio gerekir.

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio Abonelikleri için satış, abonelikler, hesaplar ve faturalama ile ilgili yardım için destek [Visual Studio ile iletişime geçin.](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Sunucu belgeleri](/windows-server/)
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
RDS'yi dağıtmak için yardıma ihtiyacınız varsa, Uzak Masaüstü Hizmetleri **(RDS) 2012** oturum dağıtımı ile ilgili çok bölümlü blog serisine göz https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf atabilirsiniz. 

Sorularınız varsa lütfen Microsoft Uzak Masaüstü [Services forumlarını ziyaret edin.](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)