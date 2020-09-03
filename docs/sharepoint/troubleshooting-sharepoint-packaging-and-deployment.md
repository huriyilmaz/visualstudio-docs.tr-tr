---
title: SharePoint paketleme ve dağıtım sorunlarını giderme | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eafac8015b7a2c51279b7a2d664f0e094d2397b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981930"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>SharePoint paketleme ve dağıtım sorunlarını giderme
  Bu konuda, SharePoint çözümlerini paketleyip dağıtırken karşılaşabileceğiniz çeşitli sorunlar ele alınmaktadır.

## <a name="enable-enhanced-debugging"></a>Gelişmiş hata ayıklamayı etkinleştir
 Visual Studio, SharePoint ve diğer katmanlar arasında tanılama yapmak için, EnableDiagnostics kayıt defteri anahtarını kullanarak yığın izlemesini görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [SharePoint Çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Çözüm paketine proje çıktısı ekleme
 Proje çıktısını Paket Tasarımcısı aracılığıyla bir pakete ekleyebilirsiniz. Ancak, proje çıktısını eklediğinizde, projenin platformunun SharePoint çözümünün platformuyla eşleştiğinden emin olun. Bir SharePoint sunucusuna dağıtmak istediğiniz derlemeler için **herhangi BIR CPU** platformu hedefini kullanmanızı öneririz. Daha fazla bilgi için bkz. [derleme sayfası, Proje tasarımcısı &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) ve [Gelişmiş derleyici ayarları iletişim kutusu &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Doğrulama uyarıları ve hataları
 Visual Studio 'daki SharePoint geliştirme araçları, çözüm paketinin doğru biçimlendirildiğini doğrulamak için doğrulama adımları gerçekleştirir. Ayrıca, özellikleriniz ve paketleriniz için özel doğrulama adımları da oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Dağıtım çakışma çözümlemesi
 Bir SharePoint çözümünü dağıtırken, sunucudaki bir öğe çözüm paketinizdeki bir öğe olarak aynı ada, URL 'ye veya KIMLIĞE sahip olduğunda çarpışmalar bulabilirsiniz. Modüller, Web bölümleri, liste örnekleri ve içerik türleri için çakışmaları çözümlemek, raporlamak veya yoksaymak için **dağıtım çakışması çözümü** özelliğini değiştirebilirsiniz.

 Aşağıdaki tabloda **dağıtım çakışması çözümü** özelliğinin ayarları gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|Automatic|Çakışmaları algılar ve çakışmaları otomatik olarak çözer.|
|İstem|Çakışmaları çözümlemeden önce çakışmaları algılar ve geliştiriciyle raporlar.|
|Hiçbiri|Çarpışmaları algılamaz.|

## <a name="differences-between-f5-deployment"></a>F5 dağıtımı arasındaki farklar
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint projenizi test ve hata ayıklama için yerel SharePoint sunucusuna dağıtmak üzere kullandığınızda, tarafından gerçekleştirilen bazı ek adımlar vardır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Dağıtım adımı sırasında Internet Information Service (IIS) ' i sıfırlayın.

2. İş akışlarını otomatik olarak ilişkilendir.

3. Özellik etkinleştirme sırasını paket tasarımcısında hiyerarşiye göre ayarlayın.

   **F5** davranışını daha fazla değiştirmek için özel dağıtım adımları ekleyebilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Visual Web Bölümü dağıtılırken SharePoint sayfasını görüntülemeyi geciktir
 SharePoint sayfasının, veya üzerinde bin klasörüne bir görsel web bölümü dağıtıldığında görünmesi uzun zaman alır [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] . Bir üst düzey dizinde (bin dizini gibi) herhangi bir dosyayı değiştirirseniz [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , tüm Web uygulaması yeniden derlenir. Bu, SharePoint sayfasının işlemesi için 25 saniyeye kadar gecikmeye neden olabilir.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorunu geçici olarak çözmek için aşağıdaki adımları uygulayın:

1. Güncelleştirme KB967535, Microsoft Desteği makalesinde açıklandığı şekilde yüklenir [: Windows Vista ve Windows Server 2008 IÇIN ııs 7,0 ' de ASP.net 'teki iki sorunu gidermeye yönelik bir düzeltme vardır](https://support.microsoft.com/help/967535).

2. Aşağıdaki satırı Web.config dosyasına ekleyin:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>SharePoint proje dağıtımı, "çözümdeki cab dosyası ayıklanamadı" hatasıyla başarısız oluyor
 Herhangi bir SharePoint proje öğesinin adı parantez içeriyorsa, çözümü bir hata ile dağıtımda başarısız olur.

### <a name="error-message"></a>Hata iletisi
 ' Çözüm Ekle ' dağıtım adımında hata oluştu: çözümdeki cab dosyası ayıklanamadı.

### <a name="resolution"></a>Çözüm
 Bu sorunu geçici olarak çözmek için, SharePoint proje öğelerinin adlarındaki tüm parantezleri kaldırın.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Visual Web Bölümü farklı bir Web uygulamasındaki bir siteye dağıtıldığında hata görüntüleniyor
 Bir Visual Web bölümünü, zaten dağıtıldığı bir Web uygulamasındaki bir siteye ilk kez dağıttığınızda (Visual Web bölümünün SiteUrl özelliği değiştirilerek) bir hata alırsınız.

### <a name="error-message"></a>Hata iletisi
 ' Çözüm Ekle ' dağıtım adımında hata oluştu: KIMLIĞI [#] olan bir özellik bu gruba zaten yüklenmiş. Özelliği açıkça yeniden yüklemek için zorla özniteliğini kullanın.

### <a name="resolution"></a>Çözüm
 Bu hata, Visual Web Bölümü özelliklerinin SharePoint 'te geri çekilme yöntemi nedeniyle oluşur. Visual Web bölümünü başarıyla dağıtmak için **F5** tuşunu seçerek çözümü yeniden dağıtın.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>İç içe Kullanıcı denetimleri dağıtıldığında uyarı görüntülenir
 Bu uyarı, bir kullanıcı denetimi veya bir görsel web bölümü ya da başka bir kullanıcı denetimi içeren bir kullanıcı denetimi içeren bir Visual Web bölümü gibi iç içe geçmiş kullanıcı denetimlerine sahip bir SharePoint çözümünü dağıtırken oluşur. Bu uyarı, araç kutusundan sürükleyerek veya kaynak görünümündeki yönergesini kullanarak bir tasarımcıya denetim eklediğinizde oluşur @Register .

### <a name="error-message"></a>Hata iletisi
 Uyarı 1 öğesi ' [*Denetim adı*] ' bilinen bir öğe değil. Web sitesinde bir derleme hatası varsa veya web.config dosyası eksikse bu durum oluşabilir.

### <a name="resolution"></a>Çözüm
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje sistemi, iç içe geçmiş bir kullanıcı denetiminin farkında değilse, IntelliSense sağlayamaz ve uyarıyı yayar. Proje derlenmemişse ve tasarımcı kapatılıp yeniden açılmadıysa veya otomatik geri çek seçeneği etkinse veya hata ayıkladıktan sonra Kullanıcı denetiminin SharePoint kovanına geri çekmesine neden olan, proje sistemi iç içe geçmiş bir kullanıcı denetiminden haberdar değildir.

 Bu uyarıyı kaldırmak için, projeyi derleyin ve sonra tasarımcı 'yı kapatıp yeniden açın ya da proje için otomatik geri çekme seçeneğini devre dışı bırakın. Bunu yapmak için, proje özellikleri iletişim kutusunun **SharePoint** sekmesinde **hata ayıklamadan sonra otomatik olarak geri çek** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)