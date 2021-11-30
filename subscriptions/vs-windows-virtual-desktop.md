---
title: Visual Studio aboneliklerde Microsoft Windows sanal masaüstü | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 10/18/2021
ms.topic: conceptual
description: Visual Studio aboneliğiniz aracılığıyla Microsoft Windows sanal masaüstünden nasıl yararlanalabileceğinizi öğrenin
ms.openlocfilehash: 918e36930f1b42963c87a790f24b4f67bb379a5d
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133257822"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>aboneliklerde sanal masaüstü Windows erişim 
Visual Studio aboneler artık Microsoft Windows sanal masaüstü hizmetleri için Azure geliştirme ve test kredilerini kullanabilir.  

Windows sanal masaüstü, bulutta çalışan kapsamlı bir masaüstü ve uygulama sanallaştırma hizmetidir. basitleştirilmiş yönetim, çoklu oturum Windows 10, Kurumlar için Microsoft 365 Uygulamaları için iyileştirmeler ve Uzak Masaüstü Hizmetleri (RDS) ortamları için destek sunan tek sanal masaüstü altyapısı (vdı). Windows masaüstü ve uygulamalarınızı Azure 'da dakikalar içinde dağıtın ve ölçeklendirin, yerleşik güvenlik ve uyumluluk özellikleri alın.

Azure 'da Windows sanal masaüstü çalıştırdığınızda şunları yapabilirsiniz:
- ölçeklenebilirlik ile tam Windows 10 sağlayan çoklu oturum Windows 10 dağıtımı ayarlama
- Kurumlar için Microsoft 365 Uygulamaları sanallaştırın ve çok kullanıcılı sanal senaryolarda çalıştırmak için iyileştirin
- ücretsiz genişletilmiş güvenlik güncelleştirmeleriyle Windows 7 sanal masaüstü sağlama
- mevcut Uzak Masaüstü Hizmetleri (RDS) ve Windows sunucu masaüstü ve uygulamalarınızı herhangi bir bilgisayara taşıyın
- Masaüstlerini ve uygulamaları sanallaştırın
- Windows 10, Windows Server ve Windows 7 masaüstü ve uygulamaları birleştirilmiş bir yönetim deneyimiyle yönetme Windows sanal masaüstü ile yapabilecekleriniz hakkında daha fazla bilgi için [tanıtım videosunu](/azure/virtual-desktop/overview)izleyin.

## <a name="use-windows-virtual-desktop-with-azure"></a>Azure ile Windows sanal masaüstü 'nü kullanma 
Visual Studio aboneler artık Windows sanal masaüstü hizmetleri için ödeme yapmak üzere Azure aboneliklerini kullanmanın birkaç yolu vardır:
- [Azure DevTest bireysel kredileri](/azure/devtest/offer/quickstart-individual-credit).  aboneliklerinin bir parçası olarak Azure devtest bireysel kredileri alan aboneler, bu kredilerin Windows sanal masaüstü hizmetleri için ödeme yapmak için kullanabilir.  Aylık kredi miktarı abonelik düzeyine bağlıdır.
- [Azure DevTest Kullandıkça Öde abonelikleri](https://azure.microsoft.com/offers/ms-azr-0023p/).  Azure abonelikleri oluşturabilir ve bir ödeme aracı ekleyebilirsiniz ve bu sayede Windows sanal masaüstü kullanımınız için sorunsuz bir şekilde ödeme yapabilirsiniz. 
- [Azure Kurumsal Anlaşma devtest teklifi](/azure/devtest/offer/quickstart-create-enterprise-devtest-subscriptions).  bu teklifle, Enterprise sözleşmeleri olan aboneler Azure ile Windows sanal masaüstü için indirimli fiyatlandırmadan ödeme yapabilir. 

## <a name="requirements"></a>Gereksinimler
Windows sanal masaüstü, vm 'lerin katıldığı bir Azure Active Directory (Azure AD) gerektirir.  Kullanıcılar bu Azure AD 'nin üyesi olmalıdır.  Azure AD 'yi uygulamak için iki seçenek vardır:
- Azure AD Dizin Hizmetleri.  Çoğu kullanıcı için bu, uygulamak daha kolay bir seçenektir.
- Bir etki alanı denetleyicisi promosyon çalıştıran bir sanal makine.  Bu seçenek, daha fazla iş ayarlanmasını gerektirir, ancak çoğu kullanıcıya daha düşük bir işletim maliyeti sunar.
Windows sanal masaüstü kullanımıyla ilgili önkoşulların tam listesini görmek için lütfen Windows sanal masaüstüne [genel bakış sayfasını](/azure/virtual-desktop/overview#requirements)ziyaret edin. 

## <a name="get-started"></a>başlarken 
Tüm ön koşullar gerçekleşirken, uygulamanızı yerine getirmek için birkaç eylemi tamamlamayı tercih edersiniz.  Başlamak için şu öğreticilere göz atın:
- [Windows sanal masaüstü kiracısı oluşturma](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- Azure portal kullanarak [bir konak havuzu oluşturma](/azure/virtual-desktop/create-host-pools-azure-marketplace)
- Windows sanal masaüstü için [uygulama gruplarını yönetme](/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>Önceliği
| Abonelik düzeyi                                                 |     Kanallar                                            | Avantaj                                                          | Yenilenebilir?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (standart)   | VL, Azure, perakende, | Kullanılabilir|  Yes          |
| GitHub Enterprise aboneliği Visual Studio Enterprise  | VL | Kullanılabilir|  Yes          |
| Visual Studio Professional (standart) | VL, Azure, perakende                                       | Kullanılabilir                                                             |  Yes             |
| GitHub Enterprise aboneliği Visual Studio Professional | VL                                       | Kullanılabilir                                        |  Yes           |
| Visual Studio Test Professional (standart)                         | VL, perakende                                              | Kullanılabilir|  Yes          |
| MSDN Platformları (Standart)                                          | VL, perakende                                              | Kullanılabilir                                         |  Yes          |
| Visual Studio Enterprise (standart)  | NFR<sup>1</sup> |Kullanılamaz  | Yok |
| Visual Studio Enterprise, Visual Studio Professional (aylık bulut) | Azure | Kullanılamaz | Yok |

<sup>1</sup>*şunları içerir: for satıl (nfr), fte, en değerli Professional (MVP), bölgesel müdürü (RD), Microsoft İş Ortağı Ağı (mpn), Visual Studio sektör ortağı (vsıp), Microsoft sertifikalı trainer, BizSpark, Imagine, nfr Basic*  

> [!NOTE]
> Microsoft artık Visual Studio Professional yıllık abonelikler ve Visual Studio Enterprise yıllık abonelikleri bulut aboneliklerinde sunmayacaktır. Mevcut müşteriler deneyiminde değişiklik yapılmaz ve aboneliklerini yenileyebilme, artırma, azaltma veya iptal etme imkanına sahip olmayacaktır. [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/)Visual Studio satın alma konusunda farklı seçenekleri araştırmak için yeni müşterilerin ' e gitmesi önerilir.

Hangi aboneliğin kullanmakta olduğunuzdan emin değil misiniz?  [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs)e-posta adresinize atanan tüm abonelikleri görmek için Bağlan. Tüm aboneliklerinizi görmüyorsanız, farklı bir e-posta adresine atanmış bir veya daha fazla sahip olabilirsiniz.  Bu abonelikleri görmek için bu e-posta adresiyle oturum açmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Azure belgeleri](/azure/)
- [Windows Sanal Masaüstü belgeleri](/azure/virtual-desktop/)
- [Visual Studio abonelik desteği](https://my.visualstudio.com/gethelp)

## <a name="next-steps"></a>Sonraki adımlar
-   Visual Studio abonelikleri satın almanız gerekiyorsa, kullanıma alın:
     - Microsoft Store aracılığıyla [perakende satın alımları Için fiyatlandırma](https://visualstudio.microsoft.com/vs/pricing/)
     - [Toplu Lisanslama programları](https://www.microsoft.com/licensing/default)
-   [sanal masaüstü Windows](/azure/virtual-desktop/overview) hakkında bilgi edinin