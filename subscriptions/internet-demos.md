---
title: Visual Studio aboneliklerde Terminal hizmetleri aracılığıyla ınternet gösterileri | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/21/2021
ms.topic: conceptual
description: Terminal Hizmetleri aracılığıyla Internet gösterileri 'nı desteklemek ve RDS erişimini etkinleştirmek için ürün anahtarları kullanmayı öğrenin
ms.openlocfilehash: b264fa3ab65992a5b9e22fbf4be6ae4096ecead9120f8467bc5498d9958a0b17
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392919"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Terminal Hizmetleri aracılığıyla Internet gösterileri
Visual Studio abonelikle, son kullanıcılara, Terminal hizmetleri (Windows server 2003 veya Windows server 2008) veya Uzak Masaüstü Hizmetleri (Windows server 2008 R2 ve üzeri) aracılığıyla programlarınızın ınternet gösterimlerine erişim sağlayabilirsiniz. En fazla 200 anonim kullanıcı, gösteriminizi bu şekilde aynı anda erişebilir. Tanıtımın üretim verilerini kullanmamalıdır. Visual Studio aboneler, uygulamalarını son kullanıcılara gösterecek şekilde lisanslanır. Terminal hizmetleri (TS) veya Uzak Masaüstü Hizmetleri (RDS) kullanan bu ınternet tanıtımı, yazılım Visual Studio abonelikleri aracılığıyla lisanslantığında, Visual Studio aboneliği olmayan son kullanıcıların tanıtım uygulamasıyla etkileşime girebileceği tek senaryodur.

bu, Visual Studio abonelerin gerektiğinde çok sayıda RDS veya TS bağlantısı kullanabileceği geliştirme ve test haklarına ek niteliğindedir.

## <a name="enabling-rds-access"></a>RDS erişimini etkinleştirme
Visual Studio aboneler, [abone portalındaki](https://my.visualstudio.com?wt.mc_id=o~msft~docs) [ürün anahtarları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sekmesinde sağlanan bir ürün anahtarı girerek, RDS aracılığıyla bir Windows sunucusuna erişebilen kullanıcı sayısını artırabilir. ürün anahtarı almak için ürün anahtarları sayfasına bağlanın ve çalıştırmakta olduğunuz Windows sunucu sürümüne gidin. "Windows Server < sürümü > R2 Uzak Masaüstü Hizmetleri < kullanıcı veya cihaz > bağlantıları" ' nı bulun ve **talep anahtarı** bağlantısına tıklayın. örneğin, Windows Server 2012 R2 üzerinde RDS kullanıyorsanız ve dağıtımınız kullanıcı cal 'lerini kullanıyorsa, "Windows Server 2012 Uzak Masaüstü Hizmetleri kullanıcı bağlantıları (50)" öğesini seçin.
her bir türden beş anahtar Windows Server 2008 R2 için kullanılabilir ve her anahtar 20 bağlantıyı destekleyecektir. Windows Server 2012 R2 için, her tür için dört anahtar sağlanır ve her biri 50 bağlantıyı destekleyecektir.

## <a name="to-enable-additional-connections-in-windows-server"></a>Windows sunucuda ek bağlantıları etkinleştirmek için:
1. Sunucu Yöneticisi'ni açın.
2. Sol gezinti bölmesindeki sunucular listesini açın.
3. Lisans sunucunuza sağ tıklayıp "lisansları yüklensin" seçeneğini belirleyin.
4. Sihirbazdaki adımları izleyin.  Anlaşma türünü seçerken, "lisans paketi (Retail)" öğesini seçin ve portaldan aldığınız ürün anahtarını girin.

Son kullanıcılar, aşağıdaki koşullar karşılandığında RDS aracılığıyla uygulamalara erişim sağlayabilir:
- Kullanıcılar anonim (kimliği doğrulanmamış bir durumda) olmalıdır.
- Bağlantılar Internet üzerinden olmalıdır.
- Uygulama gösterileri için 200 adede kadar eşzamanlı kullanıcı bağlantısı kullanılabilir.
- kullanıcı bağlantılarını etkinleştirmek için ürün anahtarları bir Visual Studio abonesi tarafından alınmalıdır.

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio abonelikleriyle ilgili satış, abonelik, hesap ve faturalandırma konusunda yardım için, [Visual Studio abonelik desteğiyle](https://aka.ms/vssubscriberhelp)iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Sunucu belgeleri](/windows-server/)
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
RDS dağıtımı için yardıma ihtiyacınız varsa, ' de **Uzak Masaüstü Hizmetleri (RDS) 2012 oturum dağıtımında** çok parçalı blog serisine göz atın https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf . 

sorularınız varsa lütfen [Microsoft Uzak Masaüstü Services forumunu](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)ziyaret edin.