---
title: Visual Studio 'da SharePoint araçları için hata ayıklama uzantıları | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1179779d07e7674babc51231ba629d7e25556f89
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584639"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio 'da SharePoint araçları için hata ayıklama uzantıları
  Visual Studio 'nun deneysel örneğinde veya normal örneğinde SharePoint araçları uzantılarında hata ayıklaması yapabilirsiniz. Bir uzantının davranışında sorun gidermeniz gerekiyorsa, ek hata bilgilerini göstermek ve Visual Studio 'Nun SharePoint komutlarını nasıl yürüttüğünü yapılandırmak için kayıt defteri değerlerini de değiştirebilirsiniz.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Visual Studio 'nun deneysel örneğinde hata ayıklama uzantıları
 Visual Studio geliştirme ortamınızı test edilmemiş uzantılar tarafından yanlışlıkla bozulmalardan korumak için, Visual Studio SDK, uzantıları yüklemek ve test etmek için kullanabileceğiniz *deneysel örnek*olarak adlandırılan alternatif bir Visual Studio örneği sağlar. Visual Studio 'nun normal örneğini kullanarak yeni uzantılar geliştirirsiniz, ancak hata ayıklayın ve deneysel örnekte çalıştırın. Daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

 Uzantınızı dağıtmak için VSıX projesi kullanıyorsanız ve VSıX projesi çözümünüzdeki başlangıç projem ise, çözümünüzde hata ayıklarken Visual Studio uzantıyı deneysel örneğe otomatik olarak yükleyip çalıştırır. Başlangıç projesi, birden fazla proje içeren bir çözümde hata ayıkladığınızda başlayan projem. Uzantınızı dağıtmak için VSıX projesi kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Visual Studio 'nun deneysel örneğinde çeşitli uzantı türlerinin nasıl ayıklanmasını gösteren örnekler için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [İzlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [İzlenecek yol: Sunucu Gezgini uzantısında SharePoint istemci nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Visual Studio 'nun normal örneğinde hata ayıklama uzantıları
 Visual Studio 'nun normal örneğinde uzantı projenizde hata ayıklamak istiyorsanız, önce uzantıyı normal örneğe yüklemeniz gerekir. Sonra, hata ayıklayıcıyı ikinci bir Visual Studio işlemine iliştirin. İşiniz bittiğinde, uzantıyı artık geliştirme bilgisayarına yüklemediğinden kaldırabilirsiniz.

#### <a name="to-install-the-extension"></a>Uzantıyı yüklemek için

1. Visual Studio 'nun tüm örneklerini kapatın.

2. Uzantı projesinin yapı çıkış klasöründe, *. vsix* dosyasını çift tıklayarak veya kısayol menüsünü açıp **Aç**' ı seçerek açın:

3. **Visual Studio Uzantı Yükleyicisi** iletişim kutusunda, uzantıyı yüklemek Istediğiniz Visual Studio sürümünü seçin ve ardından **yükleme** düğmesini seçin.

     Visual Studio, uzantı dosyalarını%userprofile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions \\ *Yazar adı* \\ *uzantı adı* \\ *sürümüne*yüklenir. Bu yoldaki son üç klasör `Author` , `Name` `Version` uzantısı için *uzantı. valtmanifest* dosyasındaki, ve öğelerinden oluşturulur.

4. Visual Studio uzantıyı yükledikten sonra **Kapat** düğmesini seçin.

#### <a name="to-debug-the-extension"></a>Uzantının hatalarını ayıklamak için

1. Visual Studio 'Yu yönetici ayrıcalıklarıyla açın ve uzantı projesini açın. Aşağıdaki adımlar, *ilk örnek*olarak Visual Studio 'nun bu örneğine başvurur.

2. Yönetici ayrıcalıklarıyla Visual Studio 'nun başka bir örneğini başlatın. Aşağıdaki adımlar, *ikinci örnek*olarak Visual Studio 'nun bu örneğine başvurur.

3. Visual Studio 'nun ilk örneğine geçin.

4. Menü çubuğunda **Hata Ayıkla**, **İşleme İliştir**' i seçin.

5. **Kullanılabilir süreçler** listesinde *devenv.exe*' yi seçin. Bu giriş, Visual Studio 'nun ikinci örneğini ifade eder; Bu, içindeki proje uzantınızın hatalarını ayıklamak istediğiniz örneğidir.

6. **Ekle** düğmesini seçin.

     Visual Studio, uzantı projesini hata ayıklama modunda çalıştırır.

7. Visual Studio 'nun ikinci örneğine geçin.

8. Uzantınızı yükleyen yeni bir SharePoint projesi oluşturun. Örneğin, liste tanımı proje öğeleri için bir uzantının hatalarını ayıklıyorsanız, bir **liste tanımı** projesi oluşturun.

9. Uzantı kodunuzu test etmek için gerekli adımları gerçekleştirin.

10. Uzantının hata ayıklamasını bitirdiğinizde, Visual Studio 'nun ikinci örneğini kapatın.

#### <a name="to-remove-the-extension"></a>Uzantıyı kaldırmak için

1. Visual Studio 'da, menü çubuğunda **Araçlar**, **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinden uzantının adını seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin.

4. Kaldırma işlemini gerçekleştirmek için **Şimdi yeniden Başlat** düğmesini seçin.

## <a name="debug-sharepoint-commands"></a>SharePoint komutlarında hata ayıkla
 SharePoint Araçları uzantısının parçası olan bir SharePoint komutunda hata ayıklamak istiyorsanız, hata ayıklayıcıyı *vssphost4.exe* işlemine bağlamanız gerekir. Bu, SharePoint komutlarını yürüten 64 bitlik ana bilgisayar işlemidir. SharePoint komutları ve *vssphost4.exe*hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Hata ayıklayıcıyı vssphost4.exe işlemine iliştirmek için

1. Yukarıdaki yönergeleri izleyerek uzantınızın, Visual Studio 'nun deneysel örneğinde veya normal Visual Studio örneğinde hata ayıklamaya başlayın.

2. Hata ayıklayıcıyı çalıştırdığınız Visual Studio örneğinde, menü çubuğunda **Hata Ayıkla**, **İşleme İliştir**' i seçin.

3. **Kullanılabilir süreçler** listesinde *vssphost.exe*' yi seçin.

    > [!NOTE]
    > vssphost.exe listede görünmezse, uzantıyı çalıştırdığınız Visual Studio örneğinde *vssphost4.exe* işlemini başlatmanız gerekir... Genellikle bunu, Visual Studio 'Nun geliştirme bilgisayarındaki SharePoint sitesine bağlanmasına neden olan bir eylem gerçekleştirerek yapabilirsiniz. Örneğin, bir site bağlantı düğümünü (bir site URL 'SI görüntüleyen bir düğüm) **Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümü altında veya **liste örneği** veya **olay alıcı** öğeleri gibi belirli SharePoint proje öğelerini bir SharePoint projesine eklediğinizde, Visual Studio *vssphost4.exe* başlar.

4. **Ekle** düğmesini seçin.

5. Hata ayıklanan Visual Studio örneğinde, komutunuz yürütmek için gerekli adımları gerçekleştirin.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>SharePoint araçları uzantılarında hata ayıklamasına yardımcı olmak için kayıt defteri değerlerini değiştirme
 Visual Studio 'da SharePoint araçlarının bir uzantısında hata ayıkladığınızda, uzantının sorunlarını gidermenize yardımcı olması için kayıt defterindeki değerleri değiştirebilirsiniz. Değerler **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\11.0\SharePointTools** anahtarında bulunur. Bu değerler varsayılan olarak bulunmaz.

 SharePoint araçlarının herhangi bir uzantısında sorun gidermeye yardımcı olmak için EnableDiagnostics değerini oluşturup ayarlayabilirsiniz. Aşağıdaki tabloda bu değer açıklanmaktadır.

|Değer|Açıklama|
|-----------|-----------------|
|EnableDiagnostics|Tanılama iletilerinin **Çıkış** penceresinde görüntülenip görüntülenmeyeceğini belirten REG_DWORD.<br /><br /> Tanılama iletilerini göstermek için bu değeri 1 olarak ayarlayın. İletileri görüntülemeyi durdurmak için bu değeri 0 olarak ayarlayın veya bu değeri silin.<br /><br /> Bir SharePoint Araçları uzantısından **Çıkış** penceresine iletiler yazmak için SharePoint proje hizmetini kullanın. Daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).|

 Uzantınız bir SharePoint komutu içeriyorsa, komutun sorunlarını gidermeye yardımcı olmak için ek değerler oluşturabilir ve ayarlayabilirsiniz. Aşağıdaki tabloda bu değerler açıklanmaktadır.

|Değer|Açıklama|
|-----------|-----------------|
|AttachDebuggerToHostProcess|Bir iletişim kutusunun görüntülenip görüntülenmeyeceğini belirten REG_DWORD, hata ayıklayıcıyı başladıktan hemen sonra *vssphost4.exe* iliştirmenizi sağlar. Hata ayıklamak istediğiniz komut başladıktan hemen sonra vssphost.exe yürütülürse ve komut yürütülmeden önce hata ayıklayıcıyı el ile iliştirmek için yeterli zaman yoksa, bu yararlı olur. İletişim kutusunu göstermek için *vssphost4.exe* <xref:System.Diagnostics.Debugger.Break%2A> yöntemi başladığında çağırır.<br /><br /> Bu davranışı etkinleştirmek için, bu değeri 1 olarak ayarlayın. Bu davranışı kapatmak için, bu değeri 0 olarak ayarlayın veya bu değeri silin.<br /><br /> Bu değeri 1 olarak ayarlarsanız, Visual Studio 'Nun başarıyla başlatıldığını sinyalin *vssphost4.exe* beklemesi için, hata ayıklayıcısını eklemek üzere bir kez daha tanımak Için HostProcessStartupTimeout değerini de artırmak isteyebilirsiniz.|
|ChannelOperationTimeout|Visual Studio 'Nun bir SharePoint komutunun yürütülmesi için beklediği süreyi saniye cinsinden belirten REG_DWORD. Komut zamanında yürütülemez, bir oluşturulur <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> .<br /><br /> Varsayılan değer 120 saniyedir.|
|HostProcessStartupTimeout|Visual Studio 'Nun *vssphost4.exe* başarıyla başlatıldığını işaret etmek için bekleyeceği süreyi saniye cinsinden belirten REG_DWORD. *vssphost4.exe* , zaman içinde başarılı bir başlangıç sinyalini işaret etmez, bir oluşturulur <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> .<br /><br /> Varsayılan değer 60 saniyedir.|
|Değerini|REG_DWORD, Visual Studio ile *vssphost4.exe*arasında geçirilen WCF iletilerinin izin verilen en büyük boyutunu bayt cinsinden belirtir.<br /><br /> Varsayılan değer 1.048.576 bayttır (1 MB).|
|MaxStringContentLength|REG_DWORD, Visual Studio ile *vssphost4.exe*arasında geçirilen dizelerin bayt olarak izin verilen en büyük boyutunu belirtir.<br /><br /> Varsayılan değer 1.048.576 bayttır (1 MB).|

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint araçlarını Visual Studio 'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio 'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
