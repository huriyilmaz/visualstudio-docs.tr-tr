---
title: Dağıtım güncelleştirmeleri için alternatif konum belirtin
description: dağıtım bildiriminizde ClickOnce uygulamanızın güncelleştirmeleri için alternatif bir konum belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 9c9db27ae54519c56a2c8f7c60454a823c59dfff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160653"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanızı başlangıçta BIR CD veya dosya paylaşımından yükleyebilirsiniz, ancak uygulamanın Web üzerinde düzenli güncelleştirmeleri denetlemesi gerekir. Uygulamanızın ilk yüklemesinden sonra kendisini güncelleştirebilmesi için, dağıtım bildiriminizde güncelleştirmeler için alternatif bir konum belirtebilirsiniz.

> [!NOTE]
> Uygulamanız, bu özelliği kullanmak için yerel olarak yüklenecek şekilde yapılandırılmalıdır. daha fazla bilgi için bkz. [izlenecek yol: el ile ClickOnce uygulaması dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ayrıca, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ağdan bir uygulama yüklerseniz, alternatif bir konum ayarlamak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu konumu hem ilk yükleme hem de sonraki tüm güncelleştirmeler için kullanılmasına neden olur. Uygulamanızı yerel olarak (örneğin, bir CD 'den) yüklerseniz, ilk yükleme özgün medya kullanılarak gerçekleştirilir ve sonraki tüm güncelleştirmeler alternatif konumu kullanacaktır.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows Forms tabanlı yardımcı program) kullanarak güncelleştirmeler için alternatif bir konum belirtin

1. bir .NET Framework komut istemi açın ve şunu yazın:

     **mageui.exe**

2. **Dosya** menüsünde, uygulamanızın dağıtım bildirimini açmak için **Aç** ' ı seçin.

3. **Dağıtım seçenekleri** sekmesini seçin.

4. **Başlatma konumu** adlı metin kutusunda, uygulama güncelleştirmeleri için dağıtım bildirimini içerecek dizine ait URL 'yi girin.

5. Dağıtım bildirimini kaydedin.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe kullanarak güncelleştirmeler için alternatif bir konum belirtin

1. bir .NET Framework komut istemi açın.

2. Aşağıdaki komutu kullanarak güncelleştirme konumunu ayarlayın. Bu örnekte, *HelloWorld.exe. Application* , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] her zaman. Application uzantısına sahip olan uygulama bildiriminin yoludur ve `http://adatum.com/Update/Path` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama güncelleştirmelerini denetleyecek URL 'dir.

    **Mage-Update HelloWorld.exe. application-providerurl http: \/ /adatum.com/Update/Path**

3. Dosyayı kaydedin.

   > [!NOTE]
   > Artık *Mage.exe* dosyayı yeniden imzalamanız gerekir. daha fazla bilgi için bkz. [izlenecek yol: el ile ClickOnce uygulaması dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Uygulamanızı CD gibi çevrimdışı bir ortamdan yüklerseniz ve bilgisayar çevrimiçi ise, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önce `<deploymentProvider>` güncelleştirme konumunun uygulamanın daha yeni bir sürümünü içerip içermediğini anlamak için dağıtım bildiriminde etiketiyle belirtilen URL 'yi kontrol eder. Varsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı ilk yükleme dizininden değil, doğrudan buradan yüklenir ve ortak dil çalışma zamanı (CLR) uygulamanızın güven düzeyini belirler `<deploymentProvider>` . Bilgisayar çevrimdışıysa veya ulaşılamaz durumdaysa, `<deploymentProvider>` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD 'den yükler ve clr, yükleme noktasına göre güven verir; bir CD yüklemesi için bu, uygulamanızın tam güven alacağı anlamına gelir. Sonraki tüm güncelleştirmeler, bu güven düzeyini devralacak.

 Kullanan tüm uygulamalar, uygulamanın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `<deploymentProvider>` farklı bilgisayarlarda farklı güven düzeyleri almadığı şekilde uygulama bildiriminde ihtiyaç duydukları izinleri açıkça bildirmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)