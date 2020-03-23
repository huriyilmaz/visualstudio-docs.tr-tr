---
title: ClickOnce'ı kullanarak Office çözümlerini dağıtma
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416568"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce'ı kullanarak Office çözümlerini dağıtma
  ClickOnce'yi kullanırsanız Office çözümünüzü daha az adımda dağıtabilirsiniz. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler. Bununla birlikte, ClickOnce, çözümünüzü bir bilgisayarın her kullanıcısı için ayrı ayrı yüklemenizi gerektirir. Bu nedenle, birden fazla kullanıcı aynı bilgisayarda çözüm çalışacaksa Windows Installer (*.msi*) kullanmayı düşünmelisiniz.

## <a name="in-this-topic"></a>Bu konuda

- [Çözümü yayımla](#Publish)

- [Çözüme nasıl güven vermek istediğinize karar verin](#Trust)

- [Kullanıcıların çözümü yüklemesine yardımcı olun](#Helping)

- [Bir çözüm belgesini son kullanıcının bilgisayarına koyun (yalnızca belge düzeyinde özelleştirmeler)](#Put)

- [Çözüm belgesini SharePoint çalıştıran bir sunucuya koyun (yalnızca belge düzeyinde özelleştirmeler)](#SharePoint)

- [Özel bir yükleyici oluşturma](#Custom)

- [Güncelleştirme yayımlama](#Update)

- [Çözümün yükleme konumunu değiştirme](#Location)

- [Çözümü önceki bir sürüme geri alma](#Roll)

  Bir Windows Installer dosyası oluşturarak Office çözümlerini nasıl dağıtılabilirsiniz hakkında daha fazla bilgi için [bkz.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="publish-the-solution"></a><a name="Publish"></a>Çözümü yayımla
 Yayımlama **Sihirbazı'nı** veya Proje **Tasarımcısı'nı**kullanarak çözümünüzü yayımlayabilirsiniz. Bu yordamda, tam yayımlama seçenekleri kümesi sağladığından **Proje Tasarımcısı'nı** kullanırsınız. Bkz. [Visual Studio&#41;'da &#40;Office geliştirme sihirbazı yayımla. ](../vsto/publish-wizard-office-development-in-visual-studio.md)

#### <a name="to-publish-the-solution"></a>Çözümü yayımlamak için

1. **Çözüm Gezgini'nde,** projeniz için adlandırılmış düğümü seçin.

2. Menü çubuğunda **Project**, *ProjectName* **Properties**'i seçin.

3. Proje **Tasarımcısı'nda,** aşağıdaki çizimde gösterdiği **Yayımla** sekmesini seçin.

    ![Proje Tasarımcısı'nın yayımlama sekmesi](../vsto/media/vsto-publishtab.png "Proje Tasarımcısı'nın yayımlama sekmesi")

4. **Yayımlama Klasörü Konumu (ftp sunucusu veya dosya yolu)** kutusuna, **Proje Tasarımcısı'nın** çözüm dosyalarını kopyalamasını istediğiniz klasörün yolunu girin.

    Aşağıdaki yol türlerinden herhangi birini girebilirsiniz.

   - Yerel bir yol (örneğin, *C:\FolderName\FolderName).*

   - Abunuzdaki bir klasöre tek düzen adlandırma kuralı (UNC) yolu (örneğin, * \\\ServerName\FolderName).*

   - Göreceli bir yol (örneğin, *PublishFolder\\*, projenin varsayılan olarak yayımlandığı klasördür).

5. Yükleme **Klasörü URL** kutusuna, son kullanıcıların çözümünüzü bulacağı konumun tam nitelikli yolunu girin.

    Henüz yerini bilmiyorsanız, bu alana hiçbir şey girmeyin. Varsayılan olarak, ClickOnce, kullanıcılarınızın çözümü yüklediği klasörde güncelleştirmeleri arar.

6. **Önkoşullar** düğmesini seçin.

7. **Önkoşullar** iletişim kutusunda, ön koşul bileşenleri onay kutusunu **yüklemek için kurulum programı oluştur'un** seçildiğinden emin olun.

8. Listeyi **hangi ön koşulları yükleyeceğini seç'te,** **Windows Installer 4.5** onay kutularını ve uygun .NET Framework paketini seçin.

    Örneğin, çözümünüz [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] **Windows Installer 4.5** ve Microsoft **.NET Framework 4.5'in**onay kutularını tam olarak hedefliyorsa.

9. Çözümünüz .NET Framework 4.5'i hedefliyorsa, Office Runtime onay kutusunu **görsel stüdyo 2010 Araçları'nı** da seçin.

    > [!NOTE]
    > Varsayılan olarak, bu onay kutusu görünmüyor. Bu onay kutusunu göstermek için bir Önyükleyici paketi oluşturmanız gerekir. Visual [Studio 2012 ile Office 2013 VSTO Eklentisi için Bootstrapper paketi oluşturun'](create-vsto-add-ins-for-office-by-using-visual-studio.md)a bakın.

10. **Ön koşullar için yükleme konumunu belirtin,** görünen seçeneklerden birini seçin ve ardından **Tamam** düğmesini seçin.

     Aşağıdaki tabloda her bir seçenek açıklanmaktadır.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |**Bileşen satıcısının web sitesinden ön koşulları indirin**|Kullanıcıdan, bu önkoşulları satıcının sitesinden indirmesi ve yüklemesi istenir.|
    |**Ön koşulları uygulamamla aynı konumdan indirin**|Önkoşul yazılımı çözümle birlikte yüklenir. Bu seçeneği tercih ederseniz, Visual Studio sizin için önkoşul paketlerinin tümünü yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
    |**Ön koşulları aşağıdaki konumdan indirin**|Visual Studio tüm önkoşul paketlerini belirttiğiniz konuma kopyalar ve bunları çözümle birlikte yükler.|

     Bkz. [Önkoşullar iletişim kutusu.](../ide/reference/prerequisites-dialog-box.md)

11. **Güncelleştirmeler** düğmesini seçin, her son kullanıcının VSTO Eklentisini veya özelleştirmesini güncelleştirmeleri denetlemek için ne sıklıkta istediğinizi belirtin ve ardından **Tamam** düğmesini seçin.

    > [!NOTE]
    > Cd veya çıkarılabilir bir sürücü kullanarak dağıtım yapıyorsunuz, **güncelleştirmeleri asla denetleme** seçeneğini seçin.

     Güncelleştirmenin nasıl yayımlandırılabildiğini öğrenmek için [bkz.](#Update)

12. **Seçenekler** düğmesini seçin, **Seçenekler** iletişim kutusundaki seçenekleri gözden geçirin ve ardından **Tamam** düğmesini seçin.

13. Şimdi **Yayımla** düğmesini seçin.

     Visual Studio, bu yordamda daha önce belirttiğiniz yayımlama klasörüne aşağıdaki klasörleri ve dosyaları ekler.

    - **Uygulama Dosyaları** klasörü.

    - Kurulum programı.

    - En son sürümün dağıtım bildirimine işaret eden bir dağıtım bildirimi.

      **Uygulama Dosyaları** klasörü, yayımladırdığınız her sürüm için bir alt klasör içerir. Her bir sürüme özgü alt klasörde aşağıdaki dosyalar bulunur.

    - Uygulama bildirimi.

    - Dağıtım bildirimi.

    - Özelleştirme derlemeleri.

      Aşağıdaki resimde, Outlook VSTO Eklentisi için yayımlama klasörünün yapısı gösterilmektedir.

      ![Klasör Yapısını Yayımla](../vsto/media/publishfolderstructure.png "Klasör Yapısını Yayımla")

    > [!NOTE]
    > ClickOnce, Güvenli olmayan bir uzantı nedeniyle dosyaları engellememesi için *.deploy* uzantısını derlemelere ekler. Kullanıcı çözümü yüklediğinde ClickOnce *.deploy* uzantısını kaldırır.

14. Çözüm dosyalarını, bu yordamda daha önce belirttiğiniz yükleme konumuna kopyalayın.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Çözüme nasıl güven vermek istediğinize karar verin
 Bir çözümün kullanıcı bilgisayarları üzerinde çalışması için önce, sizin güven kazandırmanız ya da kullanıcıların çözümü yükledikleri sırada bir güvenlik istemine yanıt vermeleri gerekir. Çözüme güven kazandırmak için, bilinen ve güvenilir bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Bkz. [Uygulama ve dağıtım bildirimlerini imzalayarak çözüme güven.](../vsto/granting-trust-to-office-solutions.md#Signing)

 Belge düzeyinde özelleştirme dağıtıyorsanız ve belgeyi kullanıcının bilgisayarındaki bir klasöre koymak veya belgeyi SharePoint sitesinde kullanılabilir hale getirmek istiyorsanız, Office'in belgenin konumuna güvendiğinden emin olun. Bkz. [Belgelere Güven](../vsto/granting-trust-to-documents.md)hibesi.

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Kullanıcıların çözümü yüklemesine yardımcı olun
 Kullanıcılar, kurulum programını çalıştırarak, dağıtım bildirimini açarak veya belge düzeyinde özelleştirme sırasında belgeyi doğrudan açarak çözümü yükleyebilir. En iyi uygulama olarak, kullanıcılar çözümünüzü kurulum programını kullanarak yüklemelidir. Diğer iki yaklaşım, ön koşul yazılımının yüklenmesini sağlamaz. Kullanıcılar belgeyi yükleme konumundan açmak isterse, Office uygulamasının Güven Merkezi'nde bu konumu güvenilir konumlar listesine eklemeleri gerekir.

### <a name="opening-the-document-of-a-document-level-customization"></a>Belge düzeyinde bir özelleştirmenin belgesini açma
 Kullanıcılar, belge düzeyinde bir özelleştirmenin belgesini doğrudan yükleme konumundan açabilirler veya belgeyi kendi yerel bilgisayarlarına kopyalayıp sonra bu kopyayı açabilirler.

 En iyi uygulama olarak, kullanıcılar belgenin bir kopyasını kendi bilgisayarlarında açmalıdır; böylece birden fazla kullanıcı aynı anda aynı kopyayı açmaya çalışmaz. Bu uygulamayı zorunlu tutmak için, kurulum programınızı, belgeyi kullanıcı bilgisayarlarına kopyalayacak şekilde yapılandırabilirsiniz. Bkz. [Bir çözüm belgesini son kullanıcının bilgisayarına koyun (yalnızca belge düzeyinde özelleştirmeler)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Bir IIS web sitesinden dağıtım bildirimini açarak çözümü yükleyin
 Kullanıcılar, web'ten dağıtım bildirimini açmak suretiyle bir Office çözümünü yükleyebilirler. Ancak, Internet Information Services (IIS) güvenli bir yükleme *.vsto* uzantısı olan dosyaları engeller. Bir Office çözümünü IIS kullanarak dağıtabilmeniz için önce MIME türü IIS'de tanımlanmalıdır.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0'a .vsto MIME türünü eklemek için

1. IIS 6.0 çalıştıran sunucuda, **Start** > **Tüm Programları** > Başlat**İdari Araçlar** >  **Internet Bilgi Hizmetleri (IIS) Yöneticisi'ni**seçin.

2. Bilgisayar adını, **Web Siteleri** klasörünü veya yapılandırmakta olduğunuz web sitesini seçin.

3. Menü çubuğunda **Eylem** > **Özellikleri'ni**seçin.

4. HTTP **Üstbilgi** sekmesinde **MIME Türleri** düğmesini seçin.

5. **MIME Türleri** penceresinde **Yeni** düğmesini seçin.

6. **MIME Türü** penceresinde, uzantısı olarak **.vsto** girin, MIME türü olarak **uygulama/x-ms-vsto** girin ve ardından yeni ayarları uygulayın.

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Daha sonra tarayıcının disk önbelleğini temizleyip *.vsto* dosyasını yeniden açmayı denemeniz gerekir.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>IIS 7.0'a .vsto MIME türünü eklemek için

1. IIS 7.0'ı çalıştıran sunucuda**Tüm Programları** >  **Başlat** > **Aksesuarları'nı**seçin.

2. **Komut İstemi**için kısayol menüsünü açın ve ardından **yönetici olarak Çalıştır'ı seçin.**

3. **Aç** kutusunda, aşağıdaki yolu girin ve ardından **Tamam** düğmesini seçin.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Aşağıdaki komutu girin ve ardından yeni ayarları uygulayın.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Daha sonra tarayıcının disk önbelleğini temizleyip *.vsto* dosyasını yeniden açmayı denemeniz gerekir.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Bir çözüm belgesini son kullanıcının bilgisayarına koyun (yalnızca belge düzeyinde özelleştirmeler)
 Dağıtım sonrası eylem oluşturarak çözümünüzün belgesini son kullanıcının bilgisayarına kopyalayabilirsiniz. Bu şekilde, kullanıcının çözümünüzü yükledikten sonra belgeyi yükleme konumundan bilgisayarına el ile kopyalaması gerekemez. Dağıtım sonrası eylemi tanımlayan, çözümü oluşturan ve yayımlayan, uygulama bildirimini değiştiren ve uygulama ve dağıtım bildirimini yeniden imzalayan bir sınıf oluşturmanız gerekir.

 Aşağıdaki yordamlar, proje adınızın **ExcelWorkbook** olduğunu ve çözümü bilgisayarınızda **C:\publish** adlı oluşturulmuş bir klasörde yayımladığınızı varsayar.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturma

1. Menü çubuğunda **Dosya** > **Add** > **Ekle Yeni Proje'yi**seçin.

2. Yeni **Proje Ekle** iletişim kutusunda, **Yüklü Şablonlar** bölmesinde **Windows** klasörünü seçin.

3. **Şablonlar** bölmesinde **Sınıf Kitaplığı** şablonu'nu seçin.

4. **Ad** **alanına, FileCopyPDA'yı**girin ve ardından **Tamam** düğmesini seçin.

5. **Solution Explorer'da** **FileCopyPDA** projesini seçin.

6. Menü çubuğunda, **Project** > **Add Reference'ı**seçin.

7. **.NET** sekmesinde, başvuru `Microsoft.VisualStudio.Tools.Applications.Runtime` ekleyin `Microsoft.VisualStudio.Tools.Applications.ServerDocument`ve.

8. Sınıfı `FileCopyPDA`yeniden adlandırın ve ardından dosyanın içeriğini kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Belgeyi kullanıcının masaüstüne kopyalar.

   - _AssemblyLocation özelliğini göreceli bir yoldan dağıtım bildirimi için tam nitelikli bir yola değiştirir.

   - Kullanıcı çözümü kaldırırsa, dosyayı siler.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Çözümü derleme ve yayımlama

1. **Solution**Explorer'da, **FileCopyPDA** projesinin kısayol menüsünü açın ve ardından **Oluştur'u**seçin.

2. **ExcelWorkbook** projesi için kısayol menüsünü açın ve ardından **Oluştur'u**seçin.

3. **ExcelWorkbook** projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle'yi**seçin.

4. Başvuru **Ekle** iletişim kutusunda **Projeler** sekmesini seçin, **FileCopyPDA'yı**seçin ve ardından **Tamam** düğmesini seçin.

5. **Çözüm Gezgini'nde** **ExcelWorkbook** projesini seçin.

6. Menü çubuğunda**Yeni** **Klasör Projesi'ni** > seçin.

7. **Verileri**girin ve ardından **Enter** tuşunu seçin.

8. **Çözüm Gezgini'nde** **Veri** klasörünü seçin.

9. Menü çubuğunda,**Varolan Öğeyi** **Ekle'yi** > seçin.

10. **Varolan Öğe Ekle** iletişim kutusunda, **ExcelWorkbook** projesinin çıktı dizinine göz atın, **ExcelWorkbook.xlsx** dosyasını seçin ve sonra **Ekle** düğmesini seçin.

11. **Solution Explorer'da** **ExcelWorkbook.xlsx** dosyasını seçin.

12. **Özellikler** penceresinde, Yapı **Eylemi** özelliğini **İçerik** ve Kopyala Çıktı **Dizini** özelliğini **yeniyse Kopyala'ya**değiştirin.

     Bu adımları tamamladığınızda, projeniz aşağıdaki çizime benzeyecektir.

     ![Dağıtım sonrası eylemin proje yapısı.](../vsto/media/vsto-postdeployment.png "Dağıtım sonrası eylemin proje yapısı.")

13. **ExcelWorkbook** projesini yayımlayın.

### <a name="modify-the-application-manifest"></a>Uygulama bildiriminde değişiklik yapma

1. **Dosya Gezgini'ni**kullanarak çözüm dizini açın, **c:\publish**.

2. Uygulama **Dosyaları** klasörünü açın ve ardından çözümünüzün en son yayımlanmış sürümüne karşılık gelen klasörü açın.

3. **ExcelWorkbook.dll.manifest** dosyasını Not Defteri gibi bir metin düzenleyicisinde açın.

4. Öğeden `</vstav3:update>` sonra, aşağıdaki kodu ekleyin. `<vstav3:entryPoint>` Öğenin sınıf özniteliği için aşağıdaki sözdizimini kullanın: *NamespaceName.ClassName*. Aşağıdaki örnekte, ad alanı ve sınıf adları aynıdır, bu nedenle `FileCopyPDA.FileCopyPDA`ortaya çıkan giriş noktası adı .

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini yeniden imzalama

1. **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** klasöründe, **ExcelWorkbook_TemporaryKey.pfx** sertifika dosyasını kopyalayın ve *yayımla klasörüne* yapıştırın **\Uygulama Dosyaları\ExcelWorkbook**\__MostRecentPublishedVersion_ klasörüne yapıştırın.

2. Visual Studio komut istemini açın ve ardından dizinleri **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ klasörü (örneğin, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4)** olarak değiştirin.

3. Aşağıdaki komutu çalıştırarak değiştirilmiş uygulama bildirimini imzalayın:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     "ExcelWorkbook.dll.manifest başarıyla imzalandı" iletisi görüntülenir.

4. **C:\publish** klasörüne değiştirin ve ardından aşağıdaki komutu çalıştırarak dağıtım bildirimini güncelleştirin ve imzalayın:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Önceki örnekte, MostRecentVersionNumber'ı çözümünüzün en son yayımlanmış sürümünün sürüm numarasıyla değiştirin (örneğin, **1_0_0_4).**

     "ExcelWorkbook.vsto başarıyla imzalandı" iletisi görüntülenir.

5. *ExcelWorkbook.vsto* dosyasını **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ dizinine kopyalayın.

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Çözüm belgesini SharePoint çalıştıran bir sunucuya koyun (yalnızca belge düzeyinde özelleştirmeler)
 Belge düzeyinde özelleştirmenizi SharePoint kullanarak son kullanıcılara yayımlayabilirsiniz. Kullanıcılar SharePoint sitesine gidip belgeyi açtığında, çalışma zamanı çözümü paylaşılan ağ klasöründen kullanıcının yerel bilgisayarına otomatik olarak yükler. Çözüm yerel olarak yüklendikten sonra, belge başka bir yere (örneğin, masaüstüne) kopyalansa bile özelleştirme işlevini yerine getirmeye devam eder.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Belgeyi SharePoint çalıştıran bir sunucuya koymak için

1. Çözüm belgesini SharePoint sitesindeki bir belge kitaplığına ekleyin.

2. Aşağıdaki yaklaşımlardan biri için adımları uygulayın:

    - SharePoint çalıştıran sunucuyu, tüm bilgisayarlarda Word veya Excel'deki Güven Merkezi'ne eklemek için Office Yapılandırma Aracı'nı kullanın.

         [Bkz. Office 2010'da Güvenlik ilkeleri ve ayarları.](/previous-versions/office/office-2010/cc178946(v=office.14))

    - Her kullanıcının aşağıdaki adımları uygulamasını sağlayın.

        1. Yerel bilgisayarda Word veya Excel'i açın, **Dosya** sekmesini seçin ve ardından **Seçenekler** düğmesini seçin.

        2. Güven **Merkezi** iletişim **kutusunda, Güvenilen Konumlar** düğmesini seçin.

        3. **Ağımdaki Güvenilir Konumlara İzin Ver (önerilmez)** onay kutusunu seçin ve ardından **yeni konum ekle** düğmesini seçin.

        4. **Yol** kutusuna, yüklediğiniz belgeyi içeren SharePoint belge kitaplığı URL'sini *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*girin (örneğin, ).

             Varsayılan Web sayfasının adını *varsayılan.aspx* veya *AllItems.aspx*gibi eklemeyin.

        5. Bu **konumun Alt Klasörleri'ni** seçin, güvenilen onay kutusu da vardır ve sonra **Tamam** düğmesini seçin.

             Kullanıcılar belgeyi SharePoint sitesinden açtığında, belge açılır ve özelleştirme yüklenir. Kullanıcılar belgeyi kendi masaüstlerine kopyalayabilir. Belgedeki özellikler belgenin ağ konumuna işaret ettiğinden, özelleştirme çalışmaya devam edecektir.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Özel bir yükleyici oluşturma
 Çözümü yayımladığınızda sizin için oluşturulan kurulum programını kullanmak yerine Office çözümünüz için özel bir yükleyici oluşturabilirsiniz. Örneğin, yüklemeyi başlatmak için komut dosyasında bir oturum açma kullanabilirsiniz veya kullanıcı etkileşimi olmadan çözümü yüklemek için bir toplu iş dosyası kullanabilirsiniz. Bu senaryolar en çok, önkoşullar son kullanıcı bilgisayarlarında zaten yüklü olduğunda işe yarar.

 Özel yükleme işleminizin bir parçası olarak, varsayılan olarak aşağıdaki konuma yüklenen Office çözümleri *(VSTOInstaller.exe)* için yükleyici aracını arayın:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Araç bu konumda değilse, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** veya **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** kayıt defteri anahtarını kullanarak bu araca giden yolu bulabilirsiniz.

 Aşağıdaki parametreleri *VSTOinstaller.exe*ile kullanabilirsiniz.

| Parametre | Tanım |
|------------------| - |
| /Install veya /I | Çözümü yükler. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir yol, evrensel bir adlandırma kuralı (UNC) dosya paylaşımı belirtebilirsiniz. Yerel bir yol *(C:\FolderName\PublishFolder*), göreli bir yol (*Yayımla\\*), veya tam nitelikli bir konum (*\\\ServerName\FolderName* veya http://<em>ServerName/FolderName</em>) belirtebilirsiniz. |
| /Uninstall veya /U | Çözümü kaldırır. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir yol, bir UNC dosya paylaşımı olabilir belirtebilirsiniz. Yerel bir yol *(c:\FolderName\PublishFolder*), göreli bir yol (*Yayımla\\*), veya tam nitelikli bir konum (*\\\ServerName\FolderName* veya http://<em>ServerName/FolderName</em>) belirtebilirsiniz. |
| /Silent veya /S | Kullanıcıdan bir şey girmesini istemeden veya ileti görüntülemeden yükler veya kaldırır. Güven istemi gerekiyorsa, özelleştirme yüklü veya güncelleştirilir. |
| /Help or /? | Yardım bilgilerini görüntüler. |

 *VSTOinstaller.exe*çalıştırdığınızda, aşağıdaki hata kodları görünebilir.

|Hata Kodu|Tanım|
|----------------|----------------|
|0|Çözüm başarıyla yüklendi ya da kaldırıldı veya VSTOInstaller Yardımı görüntülendi.|
|-100|Bir veya daha fazla komut satırı seçeneği geçerli değildir veya birden fazla kez ayarlanmıştır. Daha fazla bilgi için "vstoinstaller /?" girin. veya [clickonce Office çözümü için özel bir yükleyici oluşturma'ya](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)bakın.|
|-101|Bir veya daha fazla komut satırı seçeneği geçerli değildir. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-200|Dağıtım bildirimi URI geçerli değildir. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-201|Dağıtım bildirimi geçerli olmadığından çözüm yüklenemedi. [Bkz. Office çözümleri için Dağıtım bildirimleri.](../vsto/deployment-manifests-for-office-solutions.md)|
|-202|Uygulama bildiriminin Office için Görsel Stüdyo Araçları bölümü geçerli olmadığından çözüm yüklenemedi. [Office çözümleri için Uygulama bildirimlerine](../vsto/application-manifests-for-office-solutions.md)bakın.|
|-203|Bir indirme hatası oluştuğu için çözüm yüklenemedi. Dağıtım bildiriminin URI'sini veya ağ dosya konumunu denetleyin ve sonra yeniden deneyin.|
|-300|Bir güvenlik özel durumu oluştuğuiçin çözüm yüklenemedi. [Bkz. Güvenli Office çözümleri.](../vsto/securing-office-solutions.md)|
|-400|Çözüm yüklenemedi.|
|-401|Çözüm kaldırılamaz.|
|-500|Çözüm yüklenemediğinden ya da kaldırılamadığından veya dağıtım bildirimi indirilemediğinden işlem iptal edildi.|

## <a name="publish-an-update"></a><a name="Update"></a>Güncelleştirme yayımlama
 Bir çözümü güncelleştirmek için, Proje **Tasarımcısı** veya **Yayımlama Sihirbazı'nı**kullanarak çözümü yeniden yayımlarsınız ve ardından güncelleştirilmiş çözümü yükleme konumuna kopyalarsınız. Dosyaları yükleme konumuna kopyalarken, önceki dosyaların üzerine yazdığınızdan emin olun.

 Bir sonraki güncelleştirmeyi çözüm denetlemesi, yeni sürümü otomatik olarak bulur ve yükler.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Çözümün yükleme konumunu değiştirme
 Bir çözüm yayımlandıktan sonra yükleme yolunu ekleyebilir veya değiştirebilirsiniz. Yükleme yolunu değiştirmek istemenizin nedeni şunlardan biri veya daha fazlası olabilir:

- Kurulum programı, henüz yükleme yolu bilinmezken derlenmiştir.

- Çözüm dosyaları farklı bir konuma kopyalanmıştır.

- Yükleme dosyalarını barındıran sunucu yeni bir ada veya konuma sahiptir.

  Bir çözümün yükleme yolunu değiştirmek için kurulum programını güncelleştirmelisiniz; daha sonra da kullanıcıların bunu çalıştırması gerekir. Belge düzeyinde özelleştirmeler için, kullanıcıların ayrıca belgelerindeki bir özelliği de yeni konuma işaret edecek şekilde güncelleştirmeleri gerekir.

> [!NOTE]
> Kullanıcılardan belge özelliklerini güncelleştirmelerini istemek istemiyorsanız, kullanıcılardan güncelleştirilmiş belgeyi yükleme konumundan almalarını isteyebilirsiniz.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Kurulum programındaki yükleme konumunu değiştirmek için

1. Komut **İstemi** penceresini açın ve ardından dizinleri yükleme klasörüne değiştirin.

2. Kurulum programını çalıştırın ve `/url` yeni yükleme yolunu dize olarak alan parametreyi ekleyin.

    Aşağıdaki örnekte, Fabrikam web sitesindeki bir konumun yükleme yolunun nasıl değiştirileceği gösterilmektedir; ancak siz bu URL'yi istediğiniz yol ile değiştirebilirsiniz:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Bir ileti ekrana gelir ve yürütülebilir öğenin imzasının geçersiz kılınacağını belirtirse, çözümü imzalamak için kullanılan sertifika artık geçerli değil ve yayımcısı bilinmiyor demektir. Sonuç olarak, kullanıcıların, çözümü yüklemeden önce çözümün kaynağına güvendiklerini onaylamaları gerekecektir.

   > [!NOTE]
   > URL'nin geçerli değerini görüntülemek `setup.exe /url`için çalıştırın.

   Belge düzeyinde özelleştirmeler için, kullanıcıların belgeyi açmaları ve ardından _AssemblyLocation özelliğini güncelleştirmeleri gerekir. Aşağıdaki adımlarda kullanıcıların bu görevi nasıl yerine getirecekleri açıklanmaktadır.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Bir belgede _AssemblyLocation özelliğini güncelleştirmek için

1. **Dosya** sekmesinde, aşağıdaki çizimde gösterdiği **Bilgi'yi**seçin.

     ![Excel'de bilgi sekmesi](../vsto/media/vsto-infotab.png "Excel'de bilgi sekmesi")

2. **Özellikler** listesinde, aşağıdaki resimde gösterdiği **Gelişmiş Özellikler'i**seçin.

     ![Excel'de Gelişmiş Özellikler.](../vsto/media/vsto-advanceddocumentproperties.png "Excel'de Gelişmiş Özellikler.")

3. **Özellikler** listesindeki **Özel** sekmesinde, aşağıdaki çizimde gösterildiği gibi _AssemblyLocation'ı seçin.

     ![AssemblyLocation özelliği.](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation özelliği.")

     **Değer** kutusu dağıtım bildirimi tanımlayıcısını içerir.

4. Tanımlayıcıdan önce, *belgenin*|tam nitelikli yolunu girin ve ardından bir çubuk, Yol*Tanımlayıcısı* biçiminde (örneğin, *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9.*

     Bu tanımlayıcının nasıl biçimlendirilenhakkında daha fazla bilgi için [bkz.](../vsto/custom-document-properties-overview.md)

5. **Tamam** düğmesini seçin ve ardından belgeyi kaydedip kapatın.

6. Çözümü belirtilen konuma yüklemek için, kurulum programını /url parametresi olmadan çalıştırın.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Çözümü önceki bir sürüme geri alma
 Bir çözümü geri aldığınızda, kullanıcıları bu çözümün önceki bir sürümüne geri döndürmüş olursunuz.

#### <a name="to-roll-back-a-solution"></a>Bir çözümü geri almak için

1. Çözümün yükleme konumunu açın.

2. Üst düzey yayımlama klasöründe dağıtım bildirimini *(.vsto* dosyası) silin.

3. Geri almak istediğiniz sürüme ait alt klasörü bulun.

4. O alt klasördeki dağıtım bildirimini üst düzey publish klasörüne kopyalayın.

     Örneğin, 1.0.0.1 sürümünden sürüm 1.0.0.0.0'a **OutlookAddIn1** adı verilen bir çözümü geri almak **için, OutlookAddIn1.vsto** dosyasını **OutlookAddIn1_1_0_0_0** klasöründen kopyalayın. Dosyayı en üst düzey yayımlama klasörüne yapıştırın ve zaten orada olan **OutlookAddIn1_1_0_0_1** için sürüme özgü dağıtım bildiriminin üzerine yazın.

     Aşağıdaki resimde, bu örnekteki publish (yayımlama) klasörü yapısı gösterilmektedir.

     ![Klasör Yapısını Yayımla](../vsto/media/publishfolderstructure.png "Klasör Yapısını Yayımla")

     Kullanıcının uygulamayı ya da özelleştirilmiş belgeyi bir sonraki açışında, dağıtım bildirimindeki değişiklik algılanır. Office çözümünün önceki sürümü ClickOnce önbelleğinden çalışır.

> [!NOTE]
> Yerel veriler çözümün sadece bir önceki sürümü için kaydedilir. İki sürümü geri döndürerseniz, yerel veriler tutulmaz. Yerel veriler hakkında daha fazla bilgi için [ClickOnce uygulamalarında yerel ve uzak verilere eriş'e](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerini dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümlerini yayımla](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Nasıl yapılı: ClickOnce'yi kullanarak Office çözümlerini yayımlama](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Nasıl yapılı: ClickOnce Office çözümü yükleme](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Nasıl yapilir: ClickOnce'yi kullanarak sharepoint sunucusuna belge düzeyinde office çözümlerini yayımlama](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [ClickOnce office çözümü için özel bir yükleyici oluşturma](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)