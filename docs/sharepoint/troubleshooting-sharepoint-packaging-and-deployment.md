---
title: paketleme ve dağıtım SharePoint sorunlarını giderme | Microsoft Docs
description: SharePoint çözümlerini paketleyip dağıtırken karşılaşabileceğiniz çeşitli sorunları anlayın ve giderin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636822"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>paketleme ve dağıtım SharePoint sorunlarını giderme
  bu konuda SharePoint çözümlerini paketleyip dağıtırken karşılaşabileceğiniz çeşitli sorunlar ele alınmaktadır.

## <a name="enable-enhanced-debugging"></a>Gelişmiş hata ayıklamayı etkinleştir
 Visual Studio, SharePoint ve diğer katmanları arasında tanılama yapmak için, enablediagnostics kayıt defteri anahtarını kullanarak yığın izlemesini görüntüleyebilirsiniz. daha fazla bilgi için bkz. [SharePoint çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Çözüm paketine proje çıktısı ekleme
 Proje çıktısını Paket Tasarımcısı aracılığıyla bir pakete ekleyebilirsiniz. ancak, proje çıktısını eklediğinizde, projenin platformunun SharePoint çözümünün platformuyla eşleştiğinden emin olun. bir SharePoint sunucusuna dağıtmak istediğiniz derlemeler için **herhangi bir CPU** platformu hedefini kullanmanızı öneririz. daha fazla bilgi için bkz. [derleme sayfası, Project tasarımcı &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) ve [gelişmiş derleyici Ayarlar iletişim kutusu ](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)&#40;Visual Basic&#41;.

## <a name="validation-warnings-and-errors"></a>Doğrulama uyarıları ve hataları
 Visual Studio SharePoint geliştirme araçları, çözüm paketinin doğru biçimlendirildiğini doğrulamak için doğrulama adımları gerçekleştirir. Ayrıca, özellikleriniz ve paketleriniz için özel doğrulama adımları da oluşturabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Dağıtım çakışma çözümlemesi
 bir SharePoint çözümü dağıttığınızda, sunucudaki bir öğe, çözüm paketinizdeki bir öğe olarak aynı ada, URL 'ye veya kimliğe sahip olduğunda çarpışmalar bulabilirsiniz. Modüller, Web bölümleri, liste örnekleri ve içerik türleri için çakışmaları çözümlemek, raporlamak veya yoksaymak için **dağıtım çakışması çözümü** özelliğini değiştirebilirsiniz.

 Aşağıdaki tabloda **dağıtım çakışması çözümü** özelliğinin ayarları gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|Automatic|Çakışmaları algılar ve çakışmaları otomatik olarak çözer.|
|İstem|Çakışmaları çözümlemeden önce çakışmaları algılar ve geliştiriciyle raporlar.|
|Hiçbiri|Çarpışmaları algılamaz.|

## <a name="differences-between-f5-deployment"></a>F5 dağıtımı arasındaki farklar
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]test ve hata ayıklama için SharePoint projenizi yerel SharePoint sunucusuna dağıtmak için kullandığınızda, tarafından gerçekleştirilen bazı ek adımlar vardır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Dağıtım adımı sırasında Internet Information Service (IIS) ' i sıfırlayın.

2. İş akışlarını otomatik olarak ilişkilendir.

3. Özellik etkinleştirme sırasını paket tasarımcısında hiyerarşiye göre ayarlayın.

   **F5** davranışını daha fazla değiştirmek için özel dağıtım adımları ekleyebilirsiniz. daha fazla bilgi için bkz. [izlenecek yol: SharePoint projeleri için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>visual web bölümü dağıtırken SharePoint sayfasını görüntülemeyi geciktir
 SharePoint sayfanın, veya üzerindeki Bin klasörüne görsel bir Web bölümü dağıtıldığında görünmesi uzun zaman alır [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] . Bir üst düzey dizinde (bin dizini gibi) herhangi bir dosyayı değiştirirseniz [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , tüm Web uygulaması yeniden derlenir. bu, SharePoint sayfasının işlemesi için 25 saniyeye kadar gecikmeye neden olabilir.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorunu geçici olarak çözmek için aşağıdaki adımları uygulayın:

1. güncelleştirme KB967535, Microsoft Desteği makalesinde açıklandığı şekilde yüklenir [: Windows Vista ve Windows Server 2008 için ııs 7,0 ' de ASP.NET iki sorunu gidermeye yönelik bir düzeltme sunulmaktadır](https://support.microsoft.com/help/967535).

2. Aşağıdaki satırı Web.config dosyasına ekleyin:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint proje dağıtımı, "çözümdeki cab dosyası ayıklanamadı" hatasıyla başarısız oluyor
 herhangi bir SharePoint proje öğesinin adı parantez içeriyorsa, çözümü bir hata ile dağıtımda başarısız olur.

### <a name="error-message"></a>Hata iletisi
 ' Çözüm Ekle ' dağıtım adımında hata oluştu: çözümdeki cab dosyası ayıklanamadı.

### <a name="resolution"></a>Çözüm
 bu sorunu geçici olarak çözmek için SharePoint proje öğelerinin adlarındaki tüm parantezleri kaldırın.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Visual Web Bölümü farklı bir Web uygulamasındaki bir siteye dağıtıldığında hata görüntüleniyor
 Bir Visual Web bölümünü, zaten dağıtıldığı bir Web uygulamasındaki bir siteye ilk kez dağıttığınızda (Visual Web bölümünün SiteUrl özelliği değiştirilerek) bir hata alırsınız.

### <a name="error-message"></a>Hata iletisi
 ' Çözüm Ekle ' dağıtım adımında hata oluştu: KIMLIĞI [#] olan bir özellik bu gruba zaten yüklenmiş. Özelliği açıkça yeniden yüklemek için zorla özniteliğini kullanın.

### <a name="resolution"></a>Çözüm
 Bu hata, görsel Web Bölümü özelliklerinin SharePoint geri çekilmesi nedeniyle oluşur. Visual Web bölümünü başarıyla dağıtmak için **F5** tuşunu seçerek çözümü yeniden dağıtın.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>İç içe Kullanıcı denetimleri dağıtıldığında uyarı görüntülenir
 bu uyarı, bir kullanıcı denetimi veya bir görsel web bölümü ya da başka bir kullanıcı denetimi içeren bir kullanıcı denetimi içeren bir visual web bölümü gibi iç içe geçmiş kullanıcı denetimleri olan bir SharePoint çözümü dağıttığınızda oluşur. Bu uyarı, araç kutusundan sürükleyerek veya kaynak görünümündeki yönergesini kullanarak bir tasarımcıya denetim eklediğinizde oluşur @Register .

### <a name="error-message"></a>Hata iletisi
 Uyarı 1 öğesi ' [*Denetim adı*] ' bilinen bir öğe değil. Web sitesinde bir derleme hatası varsa veya web.config dosyası eksikse bu durum oluşabilir.

### <a name="resolution"></a>Çözüm
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje sistemi, iç içe geçmiş bir kullanıcı denetiminin farkında değilse, IntelliSense sağlayamaz ve uyarıyı yayar. proje derlenmemişse ve tasarımcı kapatılıp yeniden açılmadıysa ya da otomatik geri çek seçeneği etkinse veya hata ayıkladıktan sonra kullanıcı denetiminin SharePoint hive geri çekmesine neden olan bir iç içe geçmiş kullanıcı denetimi, proje sistemi tarafından farkında değildir.

 Bu uyarıyı kaldırmak için, projeyi derleyin ve sonra tasarımcı 'yı kapatıp yeniden açın ya da proje için otomatik geri çekme seçeneğini devre dışı bırakın. bunu yapmak için, proje özellikleri iletişim kutusunun **SharePoint** sekmesinde **hata ayıklamadan sonra otomatik olarak geri çek** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)