---
title: Paketleme SharePoint Dağıtım sorunlarını | Microsoft Docs
description: Farklı çözümleri paketler ve dağıtırken karşılaş olabileceğiniz çeşitli SharePoint düzeltin.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6d02271664f9a259754c19c9ae90612b76e1645c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156259"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Paketleme SharePoint dağıtım sorunlarını giderme
  Bu konu, çözümlerini paketlerken ve dağıtırken karşılaş olabileceğiniz çeşitli SharePoint kapsar.

## <a name="enable-enhanced-debugging"></a>Gelişmiş hata ayıklamayı etkinleştirme
 Yığın izlemesini Visual Studio, SharePoint ve diğer katmanlar arasında tanılama yapmak için EnableDiagnostics kayıt defteri anahtarını kullanabilirsiniz. Daha fazla bilgi için [bkz. Hata ayıklama SharePoint.](../sharepoint/debugging-sharepoint-solutions.md)

## <a name="add-project-output-to-the-solution-package"></a>Çözüm paketine proje çıkışı ekleme
 Paket Tasarımcısı aracılığıyla proje çıkışını bir pakete eklemek için. Ancak proje çıktısını eklerken, projenin platformunun, proje çözümünün platformuyla eş SharePoint olun. Bir sunucuya dağıtmak istediğiniz derlemeler için Herhangi bir **CPU** platformu hedefini SharePoint öneririz. Daha fazla bilgi için, [bkz. Derleme Sayfası, Project Tasarımcısı &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) Gelişmiş Derleyici [Ayarlar İletişim Kutusu &#40;Visual Basic&#41;. ](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

## <a name="validation-warnings-and-errors"></a>Doğrulama uyarıları ve hataları
 Aşağıdaki SharePoint geliştirme araçları Visual Studio doğrulama adımlarını gerçekleştirecek ve çözüm paketinin doğru şekilde oluşturulmuş olduğunu doğrular. Özellikler ve paketleriniz için özel doğrulama adımları da oluşturabilirsiniz. Daha fazla bilgi için, [bkz. How to: Create custom feature and package validation rules for SharePoint solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Dağıtım çakışması çözümü
 Bir SharePoint dağıtımında, sunucu üzerinde bir öğenin çözüm paketinizin bir öğesiyle aynı adı, URL'yi veya kimliği olduğunda çakışmalar bulabilirsiniz. Modüller, Web **bölümleri,** liste örnekleri ve içerik türleri için çakışmaları çözümlemek, rapor etmek veya yoksaymak için Dağıtım ÇakışmaSı Çözümleme özelliğini değiştirebilirsiniz.

 Aşağıdaki tabloda, Dağıtım Çakışma Çözümlemesi **özelliğinin ayarları gösterir.**

|Değer|Açıklama|
|-----------|-----------------|
|Automatic|Çakışmaları algılar ve çakışmaları otomatik olarak çözer.|
|İstem|Çakışmaları algılar ve çakışmaları çözmeden önce bunları geliştiriciye raporlar.|
|Hiçbiri|Çakışmaları algılamaz.|

## <a name="differences-between-f5-deployment"></a>F5 dağıtımı arasındaki farklar
 test ve hata ayıklama için SharePoint yerel SharePoint sunucusuna dağıtmak için kullanırken, tarafından gerçekleştirilen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bazı ek adımlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vardır.

1. Dağıtım adımı sırasında Internet Information Service'i (IIS) sıfırlayın.

2. İş akışlarını otomatik olarak ilişkilendirme.

3. Özellik etkinleştirme siparişlerini Paket Tasarımcısı'nda hiyerarşiye göre ayarlayın.

   **F5** davranışını daha fazla değiştirmek için özel dağıtım adımları abilirsiniz. Daha fazla bilgi için [bkz. Adım adım: Proje oluşturmak için özel SharePoint oluşturma.](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Görsel web SharePoint dağıtırken bir sayfayı görüntüleme gecikmesi
 Görsel SharePoint, veya üzerinde Bin klasörüne bir Visual Web bölümü dağıtırken bu sayfanın görünmesi [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] uzun [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] sürer. Bin dizini gibi bir üst düzey dizinde herhangi bir dosya [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] değiştirirsanız, Web uygulamasının tamamı yeniden derlemeler. Bu, sayfanın işlemesi için en fazla 25 SharePoint gecikmeye neden olabilir.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için aşağıdaki adımları gerçekleştirin:

1. DÜZELTME: Microsoft Desteği Vista ve Windows [Server 2008 için IIS 7.0'daki ASP.NET'daki](https://support.microsoft.com/help/967535)iki sorunu düzeltmek için bir düzeltme, Windows makalesinde açıklanan şekilde KB967535 güncelleştirmesini yükleyin.

2. Aşağıdaki satırı Web.config ekleyin:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint dağıtımı "Çözümde cab dosyası ayıklanamadı" hatasıyla başarısız oluyor
 Herhangi bir proje öğesinin SharePoint parantez içeriyorsa, çözümü dağıtımda hatayla başarısız olur.

### <a name="error-message"></a>Hata iletisi
 'Çözüm Ekle' dağıtım adımlarında hata oluştu: Çözümde cab dosyası ayıklanamadı.

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için proje öğelerinin adlarında parantezleri SharePoint kaldırın.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Farklı bir web uygulamasındaki bir siteye görsel web bölümü dağıtırken hata oluştu
 Bir görsel Web bölümünü, şu anda dağıtıldığında (görsel Web parçasının SiteUrl özelliğini değiştirerek) dışında bir Web uygulamasındaki bir siteye ilk kez dağıtıldığında bir hata alırsınız.

### <a name="error-message"></a>Hata iletisi
 'Çözüm Ekle' dağıtım adımlarında hata oluştu: Bu çiftte [#] kimliğine sahip bir özellik zaten yüklü. Özelliği açıkça yeniden yüklemek için force özniteliğini kullanın.

### <a name="resolution"></a>Çözüm
 Bu hata, görsel Web bölümü özelliklerinin geri çekiliyor olması nedeniyle SharePoint. Görsel Web bölümünü başarıyla dağıtmak için **F5** anahtarını seçerek çözümü yeniden dağıtın.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>İç içe kullanıcı denetimleri dağıtırken uyarı görüntülenir
 Bu uyarı, kullanıcı denetimi içeren bir görsel Web bölümü veya görsel Web bölümü ya da başka bir kullanıcı denetimi içeren kullanıcı denetimi gibi iç içe kullanıcı denetimlerine sahip bir SharePoint çözümü dağıtarak oluşur. Bu uyarı, bir tasarımcıya denetim eklemek için Araç Kutusundan sürükleyerek veya Kaynak görünümünde @Register yönergesini kullanarak oluşur.

### <a name="error-message"></a>Hata iletisi
 Uyarı 1 '[*Denetim Adı*]' öğesi bilinen bir öğe değil. Bu durum, Web sitesinde bir derleme hatası varsa veya web.config eksikse oluşabilir.

### <a name="resolution"></a>Çözüm
 Proje sistemi iç içe bir kullanıcı denetimine sahip değilse [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] IntelliSense sağlayamaz ve uyarıyı yalıtır. Proje oluşturmamışsa ve tasarımcı kapat ve yeniden açmamışsa ya da otomatik geri alma seçeneği etkinse, hata ayıklamadan sonra kullanıcı denetimi SharePoint hive'dan geri çekiliyorsa proje sistemi iç içe kullanıcı denetiminden haberdar değildir.

 Bu uyarıyı kaldırmak için projeyi derlemeniz, ardından tasarımcıyı kapatıp yeniden açmanız veya proje için otomatik geri çekme seçeneğini devre dışı bırakmanız gerekir. Bunu yapmak için proje özellikleri iletişim kutusunun Hata **ayıklamadan** sonra otomatik **geri SharePoint** onay kutusunun işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)