---
title: Visual Studio aboneliklerinde Microsoft Windows Sanal Masaüstü avantajı | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Visual Studio aboneliğiniz aracılığıyla Microsoft Windows Sanal Masaüstü'nden nasıl yararlanabileceğinizi öğrenin
ms.openlocfilehash: 87911b1b7b6eb63eb85b64515d5d24755e4656e6
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649729"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Aboneliklerde Windows Sanal Masaüstüne erişin 
Visual Studio aboneleri artık Microsoft Windows Sanal Masaüstü hizmetleri için Azure geliştirme/test bireysel kredilerini kullanabilirler.  
Windows Sanal Masaüstü bulutta çalışan kapsamlı bir masaüstü ve uygulama sanallaştırma hizmetidir. Basitleştirilmiş yönetim, çok oturumlu Windows 10, Office 365 ProPlus için optimizasyonlar ve Uzak Masaüstü Hizmetleri (RDS) ortamları için destek sağlayan tek sanal masaüstü altyapısıdır (VDI). Windows masaüstlerinizi ve uygulamalarınızı Azure'da dakikalar içinde dağıtın ve ölçeklendirin ve yerleşik güvenlik ve uyumluluk özelliklerine sahip olun.
Azure'da Windows Sanal Masaüstü çalıştırdığınızda şunları yapabilirsiniz:
- Ölçeklenebilirlik ile tam bir Windows 10 sağlayan çok oturumlu bir Windows 10 dağıtımı ayarlama
- Office 365 ProPlus'ı sanallaştırın ve çok kullanıcılı sanal senaryolarda çalışacak şekilde optimize edin
- Windows 7 sanal masaüstlerine ücretsiz Genişletilmiş Güvenlik Güncelleştirmeleri sağlayın
- Mevcut Uzak Masaüstü Hizmetleri (RDS) ve Windows Server masaüstü ve uygulamalarınızı herhangi bir bilgisayara taşıyın
- Hem masaüstü hem de uygulamaları sanallaştırma
- Windows 10, Windows Server ve Windows 7 masaüstü ve uygulamalarını birleşik bir yönetim deneyimiyle yönetin Windows Sanal Masaüstü ile neler yapabileceğiniz hakkında daha fazla bilgi için [tanıtım videosunu](https://docs.microsoft.com/azure/virtual-desktop/overview)izleyin.

## <a name="use-windows-virtual-desktop-with-azure"></a>Azure ile Windows Sanal Masaüstü'nü Kullanma 
Visual Studio abonelerinin artık Windows Sanal Masaüstü hizmetleri için ödeme yapmak için Azure aboneliklerini kullanmanın çeşitli yolları vardır:
- [Azure DevTest bireysel kredileri.](vs-azure.md)  Aboneliklerinin bir parçası olarak Azure DevTest bireysel kredialan aboneler, bu kredileri Windows Sanal Masaüstü hizmetleri için ödeme yapmak için kullanabilir.  Aylık kredi tutarı abonelik düzeyine bağlıdır.
- [Azure DevTest You-You-Go abonelikleri](vs-azure-payg.md).  Windows Sanal Masaüstü kullanımınız için sorunsuz bir ödeme yolu için Azure abonelikleri oluşturabilir ve bir ödeme aracı ekleyebilirsiniz. 
- [Azure Kurumsal Sözleşme DevTest teklifi.](azure-ea-devtest.md)  Bu teklifle, Kurumsal Anlaşmalara sahip aboneler, Windows Sanal Masaüstü için Azure ile indirimli fiyatlarla ödeme yapabilir. 

## <a name="requirements"></a>Gereksinimler
Windows Sanal Masaüstü, VM'lerin birlişeceği bir Azure Etkin Dizin (Azure AD) gerektirir.  Kullanıcılar bu Azure REKLAM'ın üyesi olmalıdır.  Azure REKLAMını uygulamak için iki seçenek vardır:
- Azure AD Dizin Hizmetleri.  Çoğu kullanıcı için bu, uygulanması daha kolay bir seçenektir.
- Etki Alanı Denetleyicisi promo'su çalıştıran sanal bir makine.  Bu seçenek, ayarlamak için daha fazla çalışma gerektirir, ancak çoğu kullanıcıya daha düşük bir işletim maliyeti sunar.
Windows Sanal Masaüstü'nü kullanmak için ön koşulların tam listesini görmek için lütfen Windows Sanal [Masaüstüne genel bakış sayfasını](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)ziyaret edin. 

## <a name="get-started"></a>başlarken 
Tüm ön koşullarınız yerinde olduğunda, uygulamanızı yerine getirmek için çeşitli eylemleri tamamlamak istersiniz.  Başlamak için şu öğreticilere göz atın:
- [Windows Sanal Masaüstü kiracı oluşturma](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- Azure portalını kullanarak [ana bilgisayar havuzu oluşturma](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace)
- Windows Sanal Masaüstü için [uygulama gruplarını yönetme](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>Uygunluk
| Abonelik Düzeyi                                                 |     Kanallar                                            | Avantaj                                                          | Yenilen -ebilir?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standart)   | VL, Azure, Perakende, | Kullanılabilir|  Evet          |
| GitHub Enterprise ile Visual Studio Enterprise  | Vl | Kullanılabilir|  Evet          |
| Visual Studio Professional (Standart) | VL, Azure, Perakende                                       | Kullanılabilir                                                             |  Evet             |
| GitHub Enterprise ile Visual Studio Professional | Vl                                       | Kullanılabilir                                        |  Evet           |
| Visual Studio Test Professional (Standart)                         | VL, Perakende                                              | Kullanılabilir|  Evet          |
| MSDN Platformları (Standart)                                          | VL, Perakende                                              | Kullanılabilir                                         |  Evet          |
| Visual Studio Enterprise (Standart)  | NFR<sup>1</sup> |Kullanılamaz  | Yok |
| Visual Studio Enterprise, Visual Studio Professional (aylık bulut) | Azure | Kullanılamaz | Yok |

<sup>1</sup>  *Içerir: Satış için değil (NFR), FTE, En Değerli Profesyonel (MVP), Bölge Direktörü (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> Microsoft artık Cloud Subscriptions'da Visual Studio Professional Annual abonelikleri ve Visual Studio Enterprise Annual abonelikleri sunamaz. Mevcut müşterilerin aboneliklerini yenileme, artırma, azaltma veya iptal etme deneyimi ve yeteneğinde herhangi bir değişiklik olmayacaktır. Yeni müşteriler Visual Studio [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) satın almak için farklı seçenekleri keşfetmek için gitmek için teşvik edilir.

Hangi aboneliği kullandığınızdan emin değil misiniz?  E-posta adresinize [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) atanan tüm abonelikleri görmek için bağlanın. Tüm aboneliklerinizi görmüyorsanız, farklı bir e-posta adresine atanmış bir veya daha fazla nız olabilir.  Bu abonelikleri görmek için bu e-posta adresiyle oturum açmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Windows Sanal Masaüstü belgeleri](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Sonraki adımlar
-   Visual Studio abonelikleri satın almanız gerekiyorsa, şunlara göz atın:
     - Microsoft Mağazası üzerinden [perakende satın alma işlemleri için fiyatlandırma](https://visualstudio.microsoft.com/vs/pricing/)
     - [Toplu Lisanslama programları](https://www.microsoft.com/licensing/default)
-   Windows [Sanal Masaüstü](https://docs.microsoft.com/azure/virtual-desktop/overview) hakkında bilgi edinin 
