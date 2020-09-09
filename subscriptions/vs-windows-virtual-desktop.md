---
title: Visual Studio aboneliklerinde Microsoft Windows sanal masaüstü | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 09/08/2020
ms.topic: conceptual
description: Visual Studio aboneliğiniz aracılığıyla Microsoft Windows sanal masaüstü 'nden nasıl yararlanabileceğinizi öğrenin
ms.openlocfilehash: f598aca8d277ca443b10dac289fae756ccd95432
ms.sourcegitcommit: f8d14fab194fcb30658f23f700da07d35ffc9d4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89561370"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Aboneliklerde Windows sanal masaüstüne erişme 
Visual Studio aboneleri artık Microsoft Windows Sanal Masaüstü Hizmetleri için Azure geliştirme ve test kredilerini kullanabiliyor.  
Windows sanal masaüstü, bulutta çalışan kapsamlı bir masaüstü ve uygulama sanallaştırma hizmetidir. Basitleştirilmiş Yönetim, çoklu oturum Windows 10, kurumsal Microsoft 365 uygulamalar için iyileştirmeler ve Uzak Masaüstü Hizmetleri (RDS) ortamları için destek sunan tek sanal masaüstü altyapısı (VDı). Windows Masaüstü ve uygulamalarınızı Azure 'da dakikalar içinde dağıtın ve ölçeklendirin, yerleşik güvenlik ve uyumluluk özellikleri alın.
Azure 'da Windows sanal masaüstü 'Nü çalıştırdığınızda şunları yapabilirsiniz:
- Ölçeklenebilirlik ile tam bir Windows 10 sunan çoklu oturum Windows 10 dağıtımı ayarlama
- Microsoft 365 uygulamalarını kuruluşa sanallaştırın ve bunu çok kullanıcılı sanal senaryolarda çalışacak şekilde iyileştirin
- Ücretsiz genişletilmiş güvenlik güncelleştirmeleri ile Windows 7 sanal masaüstlerini sağlama
- Mevcut Uzak Masaüstü Hizmetleri (RDS) ve Windows Server Masaüstlerinizi ve uygulamalarınızı herhangi bir bilgisayara getirme
- Masaüstlerini ve uygulamaları sanallaştırın
- Windows 10, Windows Server ve Windows 7 Masaüstü ve uygulamalarını birleştirilmiş bir yönetim deneyimiyle yönetme Windows sanal masaüstü ile yapabilecekleriniz hakkında daha fazla bilgi Için [tanıtım videosunu](https://docs.microsoft.com/azure/virtual-desktop/overview)izleyin.

## <a name="use-windows-virtual-desktop-with-azure"></a>Azure ile Windows sanal masaüstü 'Nü kullanma 
Visual Studio aboneleri artık Windows Sanal Masaüstü Hizmetleri için ödeme yapmak üzere Azure aboneliklerini kullanmanın birkaç yolu vardır:
- [Azure DevTest bireysel kredileri](vs-azure.md).  Aboneliklerinin bir parçası olarak Azure DevTest bireysel kredileri alan aboneler, bu kredileri Windows Sanal Masaüstü Hizmetleri için ödeme yapmak üzere kullanabilir.  Aylık kredi miktarı abonelik düzeyine bağlıdır.
- [Azure DevTest Kullandıkça Öde abonelikleri](vs-azure-payg.md).  Windows sanal masaüstü kullanımınız için sorunsuz bir yola sahip olmak üzere Azure abonelikleri oluşturabilir ve bir ödeme aracı ekleyebilirsiniz. 
- [Azure Kurumsal Anlaşma DevTest teklifi](azure-ea-devtest.md).  Bu teklifle, kurumsal sözleşmeleri olan aboneler Azure ile indirimli fiyatlandırmayla Windows sanal masaüstü için ödeme yapabilir. 

## <a name="requirements"></a>Gereksinimler
Windows sanal masaüstü, VM 'Lerin katılacağını Azure Active Directory (Azure AD) gerektirir.  Kullanıcılar bu Azure AD 'nin üyesi olmalıdır.  Azure AD 'yi uygulamak için iki seçenek vardır:
- Azure AD Dizin Hizmetleri.  Çoğu kullanıcı için bu, uygulamak daha kolay bir seçenektir.
- Bir etki alanı denetleyicisi promosyon çalıştıran bir sanal makine.  Bu seçenek, daha fazla iş ayarlanmasını gerektirir, ancak çoğu kullanıcıya daha düşük bir işletim maliyeti sunar.
Windows sanal masaüstü kullanımıyla ilgili önkoşulların tam listesini görmek için lütfen Windows sanal masaüstü [genel bakış sayfasını](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)ziyaret edin. 

## <a name="get-started"></a>başlarken 
Tüm ön koşullar gerçekleşirken, uygulamanızı yerine getirmek için birkaç eylemi tamamlamayı tercih edersiniz.  Başlamak için şu öğreticilere göz atın:
- [Windows sanal masaüstü kiracısı oluşturma](https://docs.microsoft.com/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- Azure portal kullanarak [bir konak havuzu oluşturma](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace)
- Windows sanal masaüstü için [uygulama gruplarını yönetme](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>Önceliği
| Abonelik düzeyi                                                 |     Kanallar                                            | Avantaj                                                          | Yenilenebilir?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standart)   | VL, Azure, perakende, | Kullanılabilir|  Yes          |
| GitHub Enterprise ile Visual Studio Enterprise  | VL | Kullanılabilir|  Yes          |
| Visual Studio Professional (Standart) | VL, Azure, perakende                                       | Kullanılabilir                                                             |  Yes             |
| GitHub Enterprise ile Visual Studio Professional | VL                                       | Kullanılabilir                                        |  Yes           |
| Visual Studio Test Professional (Standart)                         | VL, perakende                                              | Kullanılabilir|  Yes          |
| MSDN Platformları (Standart)                                          | VL, perakende                                              | Kullanılabilir                                         |  Yes          |
| Visual Studio Enterprise (Standart)  | NFR<sup>1</sup> |Kullanılamaz  | Yok |
| Visual Studio Enterprise, Visual Studio Professional (aylık bulut) | Azure | Kullanılamaz | Yok |

<sup>1</sup>  *şunları içerir: iş için değil (NFR), FTE, en DEĞERLI profesyonel (MVP), bölgesel Müdürü (RD), Microsoft iş ortağı ağı (MPN), Visual Studio Endüstri ortağı (VSIP), Microsoft Sertifikalı Trainer, BizSpark, Imagine*

> [!NOTE]
> Microsoft artık Visual Studio Professional yıllık abonelikler ve Visual Studio Enterprise yıllık abonelikleri bulut aboneliklerinde sunmayacaktır. Mevcut müşteriler deneyiminde değişiklik yapılmaz ve aboneliklerini yenileyebilme, artırma, azaltma veya iptal etme imkanına sahip olmayacaktır. Yeni müşterilerin, [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) Visual Studio 'yu satın almaya yönelik farklı seçeneklere göz atın.

Hangi aboneliğin kullanmakta olduğunuzdan emin değil misiniz?  [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs)E-posta adresinize atanan tüm abonelikleri görmek için bağlantısını yapın. Tüm aboneliklerinizi görmüyorsanız, farklı bir e-posta adresine atanmış bir veya daha fazla sahip olabilirsiniz.  Bu abonelikleri görmek için bu e-posta adresiyle oturum açmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Windows Sanal Masaüstü belgeleri](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Sonraki adımlar
-   Visual Studio abonelikleri satın almanız gerekiyorsa, kullanıma alın:
     - Microsoft Store aracılığıyla [perakende satın alımları Için fiyatlandırma](https://visualstudio.microsoft.com/vs/pricing/)
     - [Toplu Lisanslama programları](https://www.microsoft.com/licensing/default)
-   [Windows sanal masaüstü](https://docs.microsoft.com/azure/virtual-desktop/overview) hakkında bilgi edinin 
