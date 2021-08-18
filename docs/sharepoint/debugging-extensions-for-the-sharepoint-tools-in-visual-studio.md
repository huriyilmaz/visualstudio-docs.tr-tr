---
title: Visual Studio |'de SharePoint Araçları için Uzantılarda Hata Ayıklama Microsoft Docs
description: SharePoint araçları için uzantılarda hata Visual Studio. Deneysel SharePoint veya VS'nin normal örneğinde hata ayıklama araçları uzantıları.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f9b6cb0d017fdfade0b78f2d42609a7e52ad9a3b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149487"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio'de SharePoint için uzantılarda hata Visual Studio
  Deneysel örnekte veya SharePoint örneğinde araç uzantılarının hata ayıklaması Visual Studio. Bir uzantının davranışını gidermeniz gerekirse, kayıt defteri değerlerini ek hata bilgileri görüntülecek şekilde değiştirebilir ve bir uzantının Visual Studio nasıl yürütül SharePoint yapılandırabilirsiniz.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Deneysel Visual Studio örneğinde uzantılarda hata ayıklama
 Visual Studio geliştirme ortamınızı test edilmemiş uzantılar tarafından yanlışlıkla bozulmaya karşı korumak için Visual Studio SDK' sı, uzantıları yüklemek ve test etmek için kullanabileceğiniz deneysel örnek *adlı* alternatif bir Visual Studio örneği sağlar. Yeni uzantılar geliştirmek için normal Visual Studio kullanır, ancak deneysel örnekte hata ayıklar ve bunları çalıştırın. Daha fazla bilgi için [bkz. Deneysel Örnek](../extensibility/the-experimental-instance.md).

 Uzantınızı dağıtmak için bir VSIX projesi kullanıyorsanız ve VSIX projesi çözümünüzde başlangıç projesiyse, Visual Studio hata ayıklaması sırasında uzantıyı deneysel örnekte otomatik olarak yük devreder ve çalıştırır. Başlangıç projesi, birden çok proje içeren bir çözümde hata ayıklama işlemi sırasında başlayan projedir. Uzantınızı dağıtmak için VSIX projesi kullanma hakkında daha fazla bilgi için bkz. [SharePoint'de](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)Visual Studio.

 Deneysel örneklerde çeşitli uzantı türlerinde hata ayıklamayı gösteren örnekler Visual Studio aşağıdaki adım adım kılavuzlara bakın:

- [Adım adım kılavuz: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Adım adım kılavuz: Proje oluşturmak için özel SharePoint oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Adım adım kılavuz: SharePoint uzantısında istemci nesne modeline Sunucu Gezgini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Uygulamanın normal örneğinde uzantılarda hata Visual Studio
 Uzantı projenizin hata ayıklaması için normal Visual Studio, önce uzantıyı normal örnekte yükleyin. Ardından, hata ayıklayıcıyı ikinci bir Visual Studio iliştirin. Bitirdikten sonra, artık geliştirme bilgisayarına yüklemesi için uzantıyı kaldırabilirsiniz.

#### <a name="to-install-the-extension"></a>Uzantıyı yüklemek için

1. Tüm örnek örneklerini Visual Studio.

2. Uzantı projesinin derleme çıkış klasöründe, *.vsix* dosyasını çift tıklayarak veya kısayol menüsünü açıp Aç'ı **seçerek açın:**

3. Uzantı **Visual Studio iletişim kutusunda,** uzantıyı yüklemek istediğiniz Visual Studio sürümünü seçin ve ardından Yükle **düğmesini** seçin.

     Visual Studio uzantısı dosyalarını %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions yazar adı \\  \\ *uzantısı adı sürümüne* \\ *yüklür.* Bu yolda yer alan son üç klasör, uzantının `Author` `Name` `Version` *extension.vsixmanifest* dosyasındaki , ve öğelerinden oluşturulur.

4. Uzantıyı Visual Studio sonra Kapat **düğmesini** seçin.

#### <a name="to-debug-the-extension"></a>Uzantıda hata ayıklamak için

1. Yönetici Visual Studio yönetici ayrıcalıklarıyla oturum açın ve uzantı projesini açın. Aşağıdaki adımlarda bu örnek, Visual Studio örneği *olarak ifade etmektedir.*

2. Yönetici ayrıcalıklarıyla Visual Studio bir örnek daha başlat. Aşağıdaki adımlar, bu örnek için Visual Studio örneği *olarak ifade etmektedir.*

3. Uygulamanın ilk örneğine Visual Studio.

4. Menü çubuğunda Hata Ayıkla, İşleme **Ekle'yi seçin.** 

5. Kullanılabilir **İşlemler listesinde,** *devenv.exe.* Bu giriş, uygulamanın ikinci örneğine Visual Studio; Bu, içinde proje uzantınıza hata ayıklamak istediğiniz örnektir.

6. Ekle **düğmesini** seçin.

     Visual Studio projesini hata ayıklama modunda çalıştırır.

7. Uygulamanın ikinci örneğine Visual Studio.

8. Uzantınızı yük SharePoint yeni bir proje oluşturun. Örneğin, liste tanımı proje öğeleri için bir uzantıda hata ayıklarsanız bir Liste Tanımı **projesi** oluşturun.

9. Uzantı kodunuzu test etmek için gereken adımları gerçekleştirin.

10. Uzantıda hata ayıklamayı tamamlarken, uzantının ikinci örneğini Visual Studio.

#### <a name="to-remove-the-extension"></a>Uzantıyı kaldırmak için

1. Bu Visual Studio menü çubuğunda Araçlar, **Uzantılar** ve **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde uzantının adını ve ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı **kaldırmak istediğinizden** emin olmak için Evet düğmesini seçin.

4. Kaldırma işlemini **tamamlamak için** Şimdi Yeniden Başlat düğmesini seçin.

## <a name="debug-sharepoint-commands"></a>Komutlarda SharePoint ayıklama
 SharePoint araçları uzantısının parçası olan bir SharePoint komutunda hata ayıklamak için hata ayıklayıcıyıvssphost4.exe *gerekir.* Bu, komutlarını yürüten 64 bit SharePoint işlemidir. komutlarını ve SharePoint hakkında daha *fazlavssphost4.exe* için bkz. SharePoint nesne [modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Hata ayıklayıcıyı vssphost4.exe eklemek için

1. Yukarıdaki yönergeleri izleyerek uzantının deneysel Visual Studio veya normal Visual Studio hata ayıklamaya başlayabilirsiniz.

2. Hata ayıklayıcısını Visual Studio hata ayıklayıcısı örneğinde, menü çubuğunda Hata **Ayıkla,** İşleme **Ekle'yi seçin.**

3. Kullanılabilir **İşlemler listesinde,** *vssphost.exe.*

    > [!NOTE]
    > vssphost.exe listede görünmüyorsa, uzantıyıvssphost4.exeörneğinde  Visual Studio işlemini başlatmanız gerekir. Genellikle bunu, geliştirme bilgisayarına Visual Studio siteye bağlanmanıza neden SharePoint bir eylem gerçekleştirerek gerçekleştirebilirsiniz. Örneğin, Visual Studio *penceresindeki SharePoint* Bağlantılar düğümü altında bir site bağlantı düğümünü (site URL'sini görüntüleyen bir düğümvssphost4.exegenişletilen bir düğüm) ya da Sunucu Gezgini  **bir** SharePoint  projesine Liste Örneği veya Olay Alıcısı gibi belirli SharePoint proje öğelerini ekleyebilirsiniz. 

4. Ekle **düğmesini** seçin.

5. Hata ayık Visual Studio örneğinde, komutunu yürütmek için gereken adımları gerçekleştirin.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Araç uzantılarında hata ayıklamaya yardımcı olmak SharePoint değerlerini değiştirme
 SharePoint araçlarında bir uzantının Visual Studio ayıklarken, uzantı sorunlarını gidermenize yardımcı olmak için kayıt defterindeki değerleri değiştirebilirsiniz. Değerler,HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools **mevcuttur.** Bu değerler varsayılan olarak mevcut değildir.

 SharePoint araçlarının uzantılarında sorun gidermeye yardımcı olmak için EnableDiagnostics değerini oluşturabilir ve ayarlayabilirsiniz. Aşağıdaki tabloda bu değer açık almaktadır.

|Değer|Açıklama|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD penceresinde tanılama iletilerinin görüntülenmiyor olup olmadığını belirten **bir komut.**<br /><br /> Tanılama iletilerini görüntülemek için bu değeri 1 olarak ayarlayın. İletileri görüntülemeyi durdurmak için bu değeri 0 olarak ayarlayın veya bu değeri silin.<br /><br /> Bir SharePoint tools  uzantısından Çıkış penceresine ileti yazmak için SharePoint proje hizmeti. Daha fazla bilgi için [bkz. SharePoint proje hizmeti.](../sharepoint/using-the-sharepoint-project-service.md)|

 Uzantınız bir SharePoint komutu içerirse, komutun sorunlarını gidermeye yardımcı olmak için ek değerler oluşturabilir ve bu değerleri ayarlayın. Aşağıdaki tabloda bu değerler açık almaktadır.

|Değer|Açıklama|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD hata ayıklayıcıyı en kısa sürede hata ayıklayıcıya eklemenizi sağlayan *bir iletişim kutusuvssphost4.exe* olup olmadığını belirten bir komut dosyası. Hata ayıklamak istediğiniz komut başlatıldıktan hemen sonra vssphost.exe tarafından yürütülürse ve komut yürütülmeden önce hata ayıklayıcıyı el ile eklemek için yeterli zaman yoksa bu yararlı olur. İletişim kutusunu görüntülemek için *vssphost4.exe* başlatıldığında <xref:System.Diagnostics.Debugger.Break%2A> yöntemini çağırabilirsiniz.<br /><br /> Bu davranışı etkinleştirmek için bu değeri 1 olarak ayarlayın. Bu davranışı kapatmak için bu değeri 0 olarak ayarlayın veya bu değeri silin.<br /><br /> Bu değeri 1 olarak ayarlayacak olursanız, Visual Studio'nin başarıyla başlat olmadığının sinyalini beklemeden önce kendinize hata ayıklayıcıyı eklemek için yeterli zaman vermek için HostProcessStartupTimeout değerini *vssphost4.exe* da artırabilirsiniz.|
|ChannelOperationTimeout|REG_DWORD saniye olarak belirten bir Visual Studio komutunun yürütül SharePoint bekler. Komut zamanında yürütülmezse, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> bir olur.<br /><br /> Varsayılan değer 120 saniyedir.|
|HostProcessStartupTimeout|REG_DWORD saniyeler içinde, Visual Studio başarıyla başlatvssphost4.exeiçin beklemesi  gereken zamanı belirtir. Bu *vssphost4.exe* başarılı bir başlangıç olduğunu sinyallemiyorsa, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> bir olur.<br /><br /> Varsayılan değer 60 saniyedir.|
|MaxReceivedMessageSize|REG_DWORD ile arasında geçirilen WCF iletilerinin bayt cinsinden izin verilen en büyük boyutunu belirten Visual Studio *vssphost4.exe.*<br /><br /> Varsayılan değer 1.048.576 bayttır (1 MB).|
|MaxStringContentLength|Visual Studio ve *vssphost4.exe* arasında geçirilen dizelerin bayt cinsinden izin verilen boyut üst sınırını belirten REG_DWORD.<br /><br /> Varsayılan değer 1.048.576 bayttır (1 MB).|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
