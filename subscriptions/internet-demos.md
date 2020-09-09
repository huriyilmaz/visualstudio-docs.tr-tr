---
title: Terminal Hizmetleri aracılığıyla Internet gösterilerini desteklemek için ürün anahtarlarını kullanma | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 09/08/2020
ms.topic: conceptual
description: Terminal Hizmetleri aracılığıyla Internet gösterileri 'nı desteklemek ve RDS erişimini etkinleştirmek için ürün anahtarları kullanmayı öğrenin
ms.openlocfilehash: 35cda937aac7282756a1d6397b914c03e16b14fe
ms.sourcegitcommit: f8d14fab194fcb30658f23f700da07d35ffc9d4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89561318"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Terminal Hizmetleri aracılığıyla Internet gösterileri
Visual Studio aboneliği sayesinde, son kullanıcılara, Terminal Hizmetleri (Windows Server 2003 veya Windows Server 2008) veya Uzak Masaüstü Hizmetleri (Windows Server 2008 R2 ve üzeri) aracılığıyla programlarınızın Internet gösterimlerine erişim izni verebilirsiniz. En fazla 200 anonim kullanıcı, gösteriminizi bu şekilde aynı anda erişebilir. Tanıtımın üretim verilerini kullanmamalıdır. Visual Studio aboneleri, uygulamalarını son kullanıcılara gösterecek şekilde lisanslanır. Terminal Hizmetleri (TS) veya Uzak Masaüstü Hizmetleri (RDS) kullanan bu Internet tanıtımı, yazılım Visual Studio abonelikleri aracılığıyla lisanslantığında, Visual Studio aboneliği olmayan son kullanıcıların tanıtım uygulamasıyla etkileşime girebileceği tek senaryodur.

Bu, Visual Studio abonelerinin gerektiğinde çok sayıda RDS veya TS bağlantısı kullanabileceği geliştirme ve test haklarına ek niteliğindedir.

## <a name="enabling-rds-access"></a>RDS erişimini etkinleştirme
Visual Studio aboneleri, [abone portalındaki](https://my.visualstudio.com?wt.mc_id=o~msft~docs) [ürün anahtarları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sekmesinde sağlanan bir ürün anahtarı girerek bir Windows sunucusuna erişebilen kullanıcı sayısını artırabilir. Ürün anahtarı almak için ürün anahtarları sayfasına bağlanın ve çalıştırmakta olduğunuz Windows Server sürümüne gidin. "Windows Server < sürümü > R2 Uzak Masaüstü Hizmetleri < Kullanıcı veya cihaz > bağlantıları" ' nı bulun ve **talep anahtarı** bağlantısına tıklayın. Örneğin, Windows Server 2012 R2 üzerinde RDS kullanıyorsanız ve dağıtımınız Kullanıcı Cal 'Lerini kullanıyorsa, "Windows Server 2012 Uzak Masaüstü Hizmetleri Kullanıcı bağlantıları (50)" öğesini seçin.
Her bir türden beş anahtar Windows Server 2008 R2 için kullanılabilir ve her anahtar 20 bağlantıyı destekleyecektir. Windows Server 2012 R2 için, her tür için dört anahtar sağlanır ve her biri 50 bağlantıyı destekleyecektir.

## <a name="to-enable-additional-connections-in-windows-server"></a>Windows Server 'da ek bağlantıları etkinleştirmek için:
1. Sunucu Yöneticisi'ni açın.
2. Sol gezinti bölmesindeki sunucular listesini açın.
3. Lisans sunucunuza sağ tıklayıp "lisansları yüklensin" seçeneğini belirleyin.
4. Sihirbazdaki adımları izleyin.  Anlaşma türünü seçerken, "lisans paketi (Retail)" öğesini seçin ve portaldan aldığınız ürün anahtarını girin.

Son kullanıcılar, aşağıdaki koşullar karşılandığında RDS aracılığıyla uygulamalara erişim sağlayabilir:
- Kullanıcılar anonim (kimliği doğrulanmamış bir durumda) olmalıdır.
- Bağlantılar Internet üzerinden olmalıdır.
- Uygulama gösterileri için 200 adede kadar eşzamanlı kullanıcı bağlantısı kullanılabilir.
- Kullanıcı bağlantılarını etkinleştirmek için ürün anahtarları bir Visual Studio abonesi tarafından alınmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Server belgeleri](https://docs.microsoft.com/windows-server/)
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
RDS dağıtımı için yardıma ihtiyacınız varsa, ' de **Uzak Masaüstü Hizmetleri (RDS) 2012 oturum dağıtımında** çok parçalı blog serisine göz atın https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf . 

Sorularınız varsa lütfen [Microsoft Uzak Masaüstü Services forumunu](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)ziyaret edin.
