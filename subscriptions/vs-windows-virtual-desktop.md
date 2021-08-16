---
title: Visual Studio aboneliklerde Microsoft Windows Sanal Masaüstü | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 03/17/2021
ms.topic: conceptual
description: Microsoft Windows Sanal Masaüstü'nden Visual Studio öğrenin
ms.openlocfilehash: aa5a9a251e7f70900e49be75ce785a5c6f318c42d5330a9bc4e7f91078e91310
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364206"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Aboneliklerde Windows Masaüstü'ne erişme 
Visual Studio aboneler artık Microsoft Sanal Masaüstü hizmetleri için Azure geliştirme ve test bireysel Windows kullanabilir.  
Windows Sanal Masaüstü, bulutta çalışan kapsamlı bir masaüstü ve uygulama sanallaştırma hizmetidir. Basitleştirilmiş yönetim, çoklu oturum Windows 10, Kurumlar için Microsoft 365 Uygulamaları için iyileştirmeler ve Uzak Masaüstü Hizmetleri (RDS) ortamları için destek sunan tek sanal masaüstü altyapısıdır (VDI). Azure'da Windows ve uygulamalarınızı dakikalar içinde dağıtın ve ölçeklendirin ve yerleşik güvenlik ve uyumluluk özellikleri edinin.
Azure'da Sanal Masaüstü'Windows şu şekilde çalıştırabilirsiniz:
- Ölçeklenebilirlik ile tam bir Windows 10 çoklu oturum Windows 10 dağıtım ayarlama
- Sanal Kurumlar için Microsoft 365 Uygulamaları ve çok kullanıcılı sanal senaryolarda çalıştıracak şekilde iyileştirme
- Ücretsiz Windows 7 sanal masaüstleri sağlama
- Var olan Uzak Masaüstü Hizmetleri (RDS) ve Windows Server masaüstlerini ve uygulamalarını herhangi bir bilgisayara getirme
- Hem masaüstlerini hem de uygulamaları sanallaştırma
- Windows 10, Windows Server ve Windows 7 masaüstü ve uygulamalarınızı birleşik bir yönetim deneyimiyle yönetme Windows Sanal Masaüstü ile neler gerçekleştirebilirsiniz hakkında daha fazla bilgi için giriş [videosunu izleyin.](/azure/virtual-desktop/overview)

## <a name="use-windows-virtual-desktop-with-azure"></a>Azure Windows Sanal Masaüstü'leri kullanma 
Visual Studio aboneler artık Sanal Masaüstü hizmetleri için ödeme yapmak üzere Azure aboneliklerini Windows yollara sahip:
- [Azure DevTest bireysel kredileri.](vs-azure.md)  Aboneliklerinin bir parçası olarak Azure DevTest bireysel kredileri alan aboneler bu kredileri kullanarak Sanal Masaüstü Windows için ödemelerini kullanabilir.  Aylık kredi tutarı, abonelik düzeyine bağlıdır.
- [Azure DevTest Go Olarak Öde abonelikleri.](vs-azure-payg.md)  Azure abonelikleri oluşturabilir ve sanal sanal masaüstü kullanımınız için ödeme yapmak için sorunsuz bir Windows aracı iliştirebilirsiniz. 
- [Azure Kurumsal Anlaşma DevTest teklifi.](azure-ea-devtest.md)  Bu teklifle, Enterprise Sözleşmelerine sahip aboneler, Azure ile Windows Desktop için indirimli fiyatlandırma üzerinden ödemelerini kullanabilir. 

## <a name="requirements"></a>Gereksinimler
Windows Sanal Masaüstü, Azure Active Directory bir sanal makine (Azure AD) gerektirir.  Kullanıcıların bu Azure AD'ye üye olması gerekir.  Azure AD'nin uygulanması için iki seçenek vardır:
- Azure AD Dizin Hizmetleri.  Çoğu kullanıcı için bu, uygulanması daha kolay bir seçenektir.
- Etki Alanı Denetleyicisi promosyonu çalıştıran bir sanal makine.  Bu seçenek, ayarlamak için daha fazla çalışma gerektirir, ancak çoğu kullanıcıya daha düşük bir işletim maliyeti sunar.
Sanal Masaüstü'leri kullanmaya ilişkin önkoşulların tam Windows için lütfen sanal Windows genel [bakış sayfasını ziyaret edin.](/azure/virtual-desktop/overview#requirements) 

## <a name="get-started"></a>başlarken 
Tüm önkoşullar karşılandıktan sonra, uygulamanıza devam etmek için çeşitli eylemleri tamamlamak gerekir.  Çalışmaya başlamaya için şu öğreticilere göz at:
- [Windows Sanal Masaüstü kiracısı oluşturma](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Konak havuzunu kullanarak](/azure/virtual-desktop/create-host-pools-azure-marketplace) konak havuzu Azure portal
- [Windows](/azure/virtual-desktop/manage-app-groups) Sanal Masaüstü için uygulama gruplarını yönetme

## <a name="eligibility"></a>Uygunluk
| Abonelik Düzeyi                                                 |     Kanallar                                            | Avantaj                                                          | Yenilen -ebilir?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standart)   | VL, Azure, Perakende, | Kullanılabilir|  Yes          |
| Visual Studio Enterprise ile abonelik GitHub Enterprise  | Vl | Kullanılabilir|  Yes          |
| Visual Studio Professional (Standart) | VL, Azure, Perakende                                       | Kullanılabilir                                                             |  Yes             |
| Visual Studio Professional aboneliği GitHub Enterprise | Vl                                       | Kullanılabilir                                        |  Yes           |
| Visual Studio Test Professional (Standart)                         | VL, Perakende                                              | Kullanılabilir|  Yes          |
| MSDN Platformları (Standart)                                          | VL, Perakende                                              | Kullanılabilir                                         |  Yes          |
| Visual Studio Enterprise (Standart)  | NFR<sup>1</sup> |Kullanılamaz  | Yok |
| Visual Studio Enterprise, Visual Studio Professional (aylık bulut) | Azure | Kullanılamaz | Yok |

<sup>1</sup>*Şunları içerir: Resale (NFR), FTE, En Değerli Professional (MVP), Bölgesel Direktörü (RD), Microsoft İş Ortağı Ağı (MPN), Visual Studio Endüstri İş Ortağı (VSIP), Microsoft Sertifikalı Eğitimci, BizSpark, Imagine, NFR Basic* için Değil  

> [!NOTE]
> Microsoft artık Bulut Abonelikleri'Visual Studio Professional yıllık abonelikler Visual Studio Enterprise yıllık abonelikler sunmaktadır. Mevcut müşterilerin deneyimi ve aboneliklerini yenileme, artırma, azaltma veya iptal etme becerilerinde bir değişiklik olmayacaktır. Yeni müşterilerin satın almak için farklı seçenekleri [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) keşfetmeye gitmeleri Visual Studio.

Hangi aboneliği kullanmakta olduğundan emin değil misiniz?  Bağlan [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) e-posta adresinize atanan tüm abonelikleri görmek için adresine tıklayın. Tüm aboneliklerinizi görmüyorsanız, farklı bir e-posta adresine atanmış bir veya daha fazla aboneliğiniz olabilir.  Bu abonelikleri görmek için bu e-posta adresiyle oturum açmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Azure belgeleri](/azure/)
- [Windows Sanal Masaüstü belgeleri](/azure/virtual-desktop/)
- [Visual Studio abonelik desteği](https://my.visualstudio.com/gethelp)

## <a name="next-steps"></a>Sonraki adımlar
-   Abonelik satın almak Visual Studio göz atabilirsiniz:
     - [Microsoft Store aracılığıyla perakende](https://visualstudio.microsoft.com/vs/pricing/) alışverişleri için fiyatlandırma
     - [Toplu Lisanslama programları](https://www.microsoft.com/licensing/default)
-   Windows [Sanal Masaüstü hakkında bilgi](/azure/virtual-desktop/overview)