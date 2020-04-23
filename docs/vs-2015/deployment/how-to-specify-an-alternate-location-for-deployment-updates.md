---
title: 'Nasıl yapilir: Dağıtım Güncelleştirmeleri için Alternatif Konum Belirt | Microsoft Dokümanlar'
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
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037226"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Nasıl yapılır: Dağıtım Güncelleştirmeleri için Alternatif Bir Konum Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] başlangıçta bir CD veya dosya paylaşımından yükleyebilirsiniz, ancak uygulamanın Web'deki periyodik güncelleştirmeleri denetlemesi gerekir. Uygulamanızın ilk yüklemesinden sonra Web'den kendisini güncelleştirebilmeleri için dağıtım bildiriminizdeki güncelleştirmeler için alternatif bir konum belirtebilirsiniz.  
  
> [!NOTE]
> Uygulamanız bu özelliği kullanmak için yerel olarak yüklemek için yapılandırılmalıdır. Daha fazla bilgi için [Walkthrough: ClickOnce Uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)' ya bakın. Ayrıca, ağdan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama yüklerseniz, alternatif bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] konum ayarlamak, hem ilk yükleme hem de sonraki tüm güncelleştirmeler için bu konumun kullanılmasına neden olur. Uygulamanızı yerel olarak yüklerseniz (örneğin, cd'den), ilk yükleme özgün ortam kullanılarak gerçekleştirilir ve sonraki tüm güncelleştirmeler alternatif konumu kullanır.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows Forms tabanlı yardımcı program) kullanarak güncelleştirmeler için alternatif bir konum belirtme  
  
1. Bir .NET Framework komut istemi ve türü açın:  
  
     **Mageuı.exe**  
  
2. **Dosya** menüsünde, uygulamanızın dağıtım bildirimini açmak için **Aç'ı** seçin.  
  
3. Dağıtım **Seçenekleri** sekmesini seçin.  
  
4. **Başlat Konumu**adlı metin kutusuna, uygulama güncelleştirmeleri için dağıtım bildirimini içerecek dizinin URL'sini girin.  
  
5. Dağıtım bildirimini kaydedin.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe kullanarak güncelleştirmeler için alternatif bir konum belirtme  
  
1. Bir .NET Framework komut istemi açın.  
  
2. Aşağıdaki komutu kullanarak güncelleştirme konumunu ayarlayın. Bu örnekte, **HelloWorld.exe.application** her [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zaman .application uzantısı olan uygulama bildiriminize giden yoldur ve `http://adatum.com/Update/Path` uygulama güncelleştirmelerini [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] denetleyecek URL'dir.  
  
     **Mage -Update HelloWorld.exe.application -ProviderUrl http:\//adatum.com/Update/Path**  
  
3. Dosyayı kaydedin.  
  
    > [!NOTE]
    > Şimdi mage.exe ile dosyayı yeniden imzalamanız gerekiyor. Daha fazla bilgi için [Walkthrough: ClickOnce Uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)' ya bakın.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulamanızı CD gibi çevrimdışı bir ortamdan yüklerseniz ve bilgisayar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] çevrimiçiyse, güncelleştirme konumunun uygulamanın daha yeni bir sürümünü içerip içermediğinizi belirlemek için önce dağıtım bildiriminde `<deploymentProvider>` etikette belirtilen URL'yi denetler. Varsa, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı ilk yükleme dizininden değil, doğrudan oradan yükler ve ortak dil çalışma süresi (CLR) uygulamanızın güven `<deploymentProvider>`düzeyini kullanarak belirler. Bilgisayar çevrimdışıysa veya `<deploymentProvider>` erişilenemezse [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] CD'den yükler ve CLR yükleme noktasına göre güven verir; CD yüklemesi için bu, uygulamanızın tam güven aldığı anlamına gelir. Sonraki tüm güncelleştirmeler bu güven düzeyini devralır.  
  
 Kullanan [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `<deploymentProvider>` tüm uygulamalar, uygulamanın farklı bilgisayarlarda farklı güven düzeyleri almaması için, gereksinim duydukları izinleri uygulama bildirimlerinde açıkça bildirmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Walkthrough: ClickOnce Uygulamasını El Ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce Dağıtım Bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Uygulamaları nın Güvenliğini Sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce Güncelleştirme Stratejisini Seçme](../deployment/choosing-a-clickonce-update-strategy.md)
