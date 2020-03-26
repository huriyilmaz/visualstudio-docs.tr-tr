---
title: Terminal Hizmetleri aracılığıyla internet gösterilerini desteklemek için ürün anahtarlarını kullanma | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/09/2020
ms.topic: conceptual
description: Terminal Hizmetleri aracılığıyla internet gösterilerini desteklemek ve RDS erişimini etkinleştirmek için ürün anahtarlarını nasıl kullanacağınızı öğrenin
ms.openlocfilehash: 2d5f23f0d161ee9f50569e0ff7f8ce585c8c49ff
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232434"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Terminal Hizmetleri ile Internet gösterileri
Visual Studio aboneliği ile, son kullanıcılara Terminal Hizmetleri (Windows Server 2003 veya Windows Server 2008) veya Uzak Masaüstü Hizmetleri (Windows Server 2008 R2 ve sonrası) aracılığıyla programlarınızın Internet gösterilerine erişimini sağlayabilirsiniz. En fazla 200 anonim kullanıcı aynı anda gösterinize bu şekilde erişebilir. Gösteriniz üretim verilerini kullanmamalıdır. Visual Studio aboneleri son kullanıcılara uygulamalarını göstermek için lisanslıdır. Terminal Hizmetleri (TS) veya Uzak Masaüstü Hizmetleri (RDS) kullanan bu Internet gösterimi, Visual Studio aboneliği olmayan son kullanıcıların, yazılım Visual üzerinden lisanslandığında gösteri uygulamasıyla etkileşimde bulunduğu tek senaryodur Stüdyo abonelikleri.

Bu, Visual Studio abonelerinin gerektiği kadar RDS veya TS bağlantısı kullanabileceği geliştirme/test haklarına ek olarak yapılır.

## <a name="enabling-rds-access"></a>RDS Erişimini Etkinleştirme
Visual Studio [aboneleri, abone portalındaki](https://my.visualstudio.com?wt.mc_id=o~msft~docs) [Ürün Anahtarları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sekmesine sağlanan bir ürün anahtarını girerek RDS üzerinden Windows Server'a erişebilen kullanıcı sayısını artırabilir. Bir ürün anahtarı edinmek için Ürün Tuşları sayfasına bağlanın ve çalıştırmakta olduğunuz Windows Server sürümüne gidin. Kullanıcı veya aygıt > bağlantıları < R2 Uzak Masaüstü Hizmetleri > "Windows Server < sürümünü" bulun ve **Talep Anahtarı** bağlantısını tıklayın. Örneğin, Windows Server 2012 R2'de RDS kullanıyorsanız ve dağıtımınız kullanıcı CAL'lerini kullanıyorsa, "Windows Server 2012 Uzak Masaüstü Hizmetleri kullanıcı bağlantıları (50)" seçeneğini belirleyin.
Windows Server 2008 R2 için her türden beş anahtar kullanılabilir ve her anahtar 20 bağlantıyı destekler. Windows Server 2012 R2 için, her tür için dört anahtar sağlanır ve her biri 50 bağlantıyı destekler.

## <a name="to-enable-additional-connections-in-windows-server"></a>Windows Server'da ek bağlantıları etkinleştirmek için:
1. Sunucu Yöneticisi'ni açın.
2. Sol gezinme bölmesinde Sunucular listesini açın.
3. Lisans sunucunuza sağ tıklayın ve "Lisans Yükle"yi seçin.
4. Sihirbazdaki adımları izleyin.  Anlaşma türünü seçerken "Lisans Paketi (perakende)" seçeneğini belirleyin ve MY portalından aldığınız ürün anahtarını girin.

Aşağıdaki koşullar yerine getirildiğinde son kullanıcılar RDS üzerinden erişim uygulamalarına bağlanabilir:
- Kullanıcılar anonim olmalıdır (kimliği doğrulanamayan bir durumda).
- Bağlantılar Internet üzerinden olmalıdır.
- Uygulamanın gösterileri için en fazla 200 eşzamanlı kullanıcı bağlantısı kullanılabilir.
- Kullanıcı bağlantılarını etkinleştirmek için ürün anahtarları Visual Studio abonesi tarafından alınmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Server documenation](https://docs.microsoft.com/windows-server/)
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
RDS dağıtmak için kılavuza ihtiyacınız varsa, Uzak Masaüstü **Hizmetleri (RDS) 2012 oturum dağıtımında** çok parçalı blog serisine https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerfgöz atın. 

Herhangi bir sorunuz varsa, lütfen [Microsoft Uzak Masaüstü Hizmetleri forumuna](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)ziyaret edin.
