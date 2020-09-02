---
title: 'Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037226"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Nasıl yapılır: Dağıtım Güncelleştirmeleri için Alternatif Bir Konum Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulamanızı başlangıçta BIR CD veya dosya paylaşımından yükleyebilirsiniz, ancak uygulamanın Web üzerinde düzenli güncelleştirmeleri denetlemesi gerekir. Uygulamanızın ilk yüklemesinden sonra kendisini güncelleştirebilmesi için, dağıtım bildiriminizde güncelleştirmeler için alternatif bir konum belirtebilirsiniz.  
  
> [!NOTE]
> Uygulamanız, bu özelliği kullanmak için yerel olarak yüklenecek şekilde yapılandırılmalıdır. Daha fazla bilgi için bkz. [Izlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ayrıca, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ağdan bir uygulama yüklerseniz, alternatif bir konum ayarlamak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bu konumu hem ilk yükleme hem de sonraki tüm güncelleştirmeler için kullanılmasına neden olur. Uygulamanızı yerel olarak (örneğin, bir CD 'den) yüklerseniz, ilk yükleme özgün medya kullanılarak gerçekleştirilir ve sonraki tüm güncelleştirmeler alternatif konumu kullanacaktır.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows Forms tabanlı yardımcı program) kullanarak güncelleştirmeler için alternatif bir konum belirtme  
  
1. Bir .NET Framework komut istemi açın ve şunu yazın:  
  
     **mageui.exe**  
  
2. **Dosya** menüsünde, uygulamanızın dağıtım bildirimini açmak için **Aç** ' ı seçin.  
  
3. **Dağıtım seçenekleri** sekmesini seçin.  
  
4. **Başlatma konumu**adlı metin kutusunda, uygulama güncelleştirmeleri için dağıtım bildirimini içerecek dizine ait URL 'yi girin.  
  
5. Dağıtım bildirimini kaydedin.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe kullanarak güncelleştirmeler için alternatif bir konum belirtme  
  
1. Bir .NET Framework komut istemi açın.  
  
2. Aşağıdaki komutu kullanarak güncelleştirme konumunu ayarlayın. Bu örnekte, **HelloWorld.exe. Application** , [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] her zaman. Application uzantısına sahip olan uygulama bildiriminin yoludur ve `http://adatum.com/Update/Path` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama güncelleştirmelerini denetleyecek URL 'dir.  
  
     **Mage-güncelleştirme HelloWorld.exe. Application-ProviderUrl http: \/ /adatum.com/Update/Path**  
  
3. Dosyayı kaydedin.  
  
    > [!NOTE]
    > Artık Mage.exe dosyayı yeniden imzalamanız gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulamanızı CD gibi çevrimdışı bir ortamdan yüklerseniz ve bilgisayar çevrimiçi ise, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] önce `<deploymentProvider>` güncelleştirme konumunun uygulamanın daha yeni bir sürümünü içerip içermediğini anlamak için dağıtım bildiriminde etiketiyle belirtilen URL 'yi kontrol eder. Varsa, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı ilk yükleme dizininden değil, doğrudan buradan yüklenir ve ortak dil çalışma zamanı (CLR) uygulamanızın güven düzeyini belirler `<deploymentProvider>` . Bilgisayar çevrimdışıysa veya ulaşılamaz durumdaysa, `<deploymentProvider>` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] CD 'den yükler ve clr, yükleme noktasına göre güven verir; bir CD yüklemesi için bu, uygulamanızın tam güven alacağı anlamına gelir. Sonraki tüm güncelleştirmeler, bu güven düzeyini devralacak.  
  
 Kullanan tüm uygulamalar, uygulamanın [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `<deploymentProvider>` farklı bilgisayarlarda farklı güven düzeyleri almadığı şekilde uygulama bildiriminde ihtiyaç duydukları izinleri açıkça bildirmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce Güncelleştirme Stratejisini Seçme](../deployment/choosing-a-clickonce-update-strategy.md)
