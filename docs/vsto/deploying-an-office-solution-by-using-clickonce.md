---
title: ClickOnce kullanarak Office çözümünü dağıtma
description: ClickOnce kullanırsanız Office çözümünüzü daha az adımda nasıl dağıtabileceğinizi öğrenin. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: eb23c3254d80847298fa12485c8f6df607506138
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148356"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce kullanarak Office çözümünü dağıtma
  ClickOnce kullanırsanız Office çözümünüzü daha az adımda dağıtabilirsiniz. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler. Bununla birlikte, ClickOnce, çözümünüzü bir bilgisayarın her kullanıcısı için ayrı ayrı yüklemenizi gerektirir. bu nedenle, çözümünüzü aynı bilgisayarda çalıştırmak için birden fazla kullanıcı Windows Installer (*.msi*) kullanmayı göz önünde bulundurmanız gerekir.

## <a name="in-this-topic"></a>Bu konuda

- [Çözümü yayımlama](#Publish)

- [Çözüme nasıl güven vermek istediğinize karar verin](#Trust)

- [Kullanıcıların çözümü yüklemesine yardımcı olma](#Helping)

- [Bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)](#Put)

- [bir çözümün belgesini SharePoint çalıştıran bir sunucuya koyma (yalnızca belge düzeyinde özelleştirmeler)](#SharePoint)

- [Özel bir yükleyici oluşturma](#Custom)

- [Güncelleştirme yayımlama](#Update)

- [Bir çözümün yükleme konumunu değiştirme](#Location)

- [Bir çözümü önceki bir sürüme geri alma](#Roll)

  bir Windows Installer dosyası oluşturarak Office çözümünün nasıl dağıtılacağı hakkında daha fazla bilgi için, bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a> Çözümü yayımlama
 çözümünüzü **yayımla sihirbazını** veya **Project tasarımcısını** kullanarak yayımlayabilirsiniz. bu yordamda, tüm yayımlama seçenekleri kümesini sağladığından **Project tasarımcısını** kullanacaksınız. bkz. [Visual Studio&#41;&#40;yayımlama sihirbazı Office geliştirme ](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Çözümü yayımlamak için

1. **Çözüm Gezgini**, projeniz için adlandırılmış düğümü seçin.

2. menü çubuğunda **Project**, *ProjectName* **özellikler**' i seçin.

3. **Project tasarımcısında**, aşağıdaki çizimin gösterdiği **yayımla** sekmesini seçin.

    ![Project tasarımcısının yayımla sekmesi](../vsto/media/vsto-publishtab.png "Project Designer'ın yayımlama sekmesi")

4. **yayımlama klasörü konumu (ftp sunucusu veya dosya yolu)** kutusunda, **Project tasarımcısının** çözüm dosyalarını kopyalamasını istediğiniz klasörün yolunu girin.

    Aşağıdaki yol türlerinden herhangi birini girebilirsiniz.

   - Yerel bir yol (örneğin, *C:\folderadı \ KlasörAdı*).

   - Ağınızdaki bir klasörün Tekdüzen adlandırma kuralı (UNC) yolu (örneğin, *\\ \Sunucuadı \ KlasörAdı*).

   - Bir göreli yol (örneğin, varsayılan olarak projenin yayımlandığı klasör olan *publishfolder \\*).

5. **Yükleme klasörü URL 'si** kutusuna, son kullanıcıların çözümünüzü bulacağı konumun tam yolunu girin.

    Konumu henüz bilmiyorsanız, bu alana hiçbir şey girmeyin. Varsayılan olarak, ClickOnce, kullanıcılarınızın çözümü yüklediği klasörde güncelleştirmeleri arar.

6. **Önkoşullar** düğmesini seçin.

7. **Önkoşullar** iletişim kutusunda, **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** onay kutusunun işaretli olduğundan emin olun.

8. **yüklenecek önkoşulları seçin** listesinde, **Windows Installer 4,5** ve uygun .NET Framework paketinin onay kutularını seçin.

    örneğin, çözümünüz [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] öğesini hedefliyorsa, **Windows Installer 4,5** ve **Microsoft .NET Framework 4,5 Full** onay kutularını seçin.

9. çözümünüz .NET Framework 4,5 ' i hedefliyorsa **Office çalışma zamanı için Visual Studio 2010 araçları** onay kutusunu da seçin.

    > [!NOTE]
    > Varsayılan olarak, bu onay kutusu görünmez. Bu onay kutusunu göstermek için bir Önyükleyici paketi oluşturmanız gerekir. bkz. [Visual Studio 2012 ile Office 2013 VSTO eklentisi için önyükleyici paketi oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. **Önkoşullar için yüklemeyi belirtin** altında, görüntülenen seçeneklerden birini belirleyin ve sonra **Tamam** düğmesini seçin.

     Aşağıdaki tabloda her bir seçenek açıklanmaktadır.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |**Önkoşulları bileşen satıcısının Web sitesinden indir**|Kullanıcıdan, bu önkoşulları satıcının sitesinden indirmesi ve yüklemesi istenir.|
    |**Önkoşulları Uygulamam ile aynı konumdan indir**|Önkoşul yazılımı çözümle birlikte yüklenir. Bu seçeneği tercih ederseniz, Visual Studio sizin için önkoşul paketlerinin tümünü yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
    |**Önkoşulları aşağıdaki konumdan indirin**|Visual Studio tüm önkoşul paketlerini belirttiğiniz konuma kopyalar ve bunları çözümle birlikte yükler.|

     Bkz. [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).

11. **güncelleştirmeler** düğmesini seçin, her son kullanıcının VSTO eklentisinin veya özelleştirmenin güncelleştirmeleri denetlemesini istediğiniz sıklığı belirtin ve sonra **tamam** düğmesini seçin.

    > [!NOTE]
    > Bir CD veya çıkarılabilir sürücü kullanarak dağıtıyorsanız, **güncelleştirmeleri hiçbir şekilde denetle** seçenek düğmesini seçin.

     Bir güncelleştirmeyi yayımlama hakkında daha fazla bilgi için bkz. [güncelleştirme yayımlama](#Update).

12. **Seçenekler düğmesini seçin** , **Seçenekler iletişim kutusundaki seçenekleri gözden** geçirin ve **Tamam** düğmesini seçin.

13. **Şimdi Yayımla** düğmesini seçin.

     Visual Studio, bu yordamda daha önce belirttiğiniz yayımlama klasörüne aşağıdaki klasörleri ve dosyaları ekler.

    - **Uygulama dosyaları** klasörü.

    - Kurulum programı.

    - En son sürümün dağıtım bildirimine işaret eden bir dağıtım bildirimi.

      **Uygulama dosyaları** klasörü, yayımladığınız her sürüm için bir alt klasör içerir. Her bir sürüme özgü alt klasörde aşağıdaki dosyalar bulunur.

    - Uygulama bildirimi.

    - Dağıtım bildirimi.

    - Özelleştirme derlemeleri.

      aşağıdaki çizimde, bir Outlook VSTO eklentisinin publish klasörünün yapısı gösterilmektedir.

      ![Klasör yapısını Yayımla](../vsto/media/publishfolderstructure.png "Klasör Yapısını Yayımlama")

    > [!NOTE]
    > ClickOnce, güvenli olmayan bir uzantı nedeniyle Internet Information Services (ııs) yüklemesinin dosyaları engellememeleri için *. deploy* uzantısını derlemelere ekler. kullanıcı çözümü yüklediğinde ClickOnce *. deploy* uzantısını kaldırır.

14. Çözüm dosyalarını, bu yordamda daha önce belirttiğiniz yükleme konumuna kopyalayın.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Çözüme nasıl güven vermek istediğinize karar verin
 Bir çözümün kullanıcı bilgisayarları üzerinde çalışması için önce, sizin güven kazandırmanız ya da kullanıcıların çözümü yükledikleri sırada bir güvenlik istemine yanıt vermeleri gerekir. Çözüme güven kazandırmak için, bilinen ve güvenilir bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Bkz. [uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin](../vsto/granting-trust-to-office-solutions.md#Signing).

 belge düzeyinde bir özelleştirme dağıtıyorsanız ve belgeyi kullanıcının bilgisayarındaki bir klasöre koymak veya belgeyi bir SharePoint sitesinde kullanılabilir hale getirmek istiyorsanız, Office belgenin konumuna güvendiğinden emin olun. Bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Kullanıcıların çözümü yüklemesine yardımcı olma
 Kullanıcılar, Kurulum programını çalıştırarak, dağıtım bildirimini açarak veya belge düzeyinde özelleştirme sırasında belgeyi doğrudan açarak çözümü yükleyebilir. En iyi uygulama olarak, kullanıcılar çözümünüzü kurulum programını kullanarak yüklemelidir. Diğer iki yaklaşım, önkoşul yazılımının yüklü olduğundan emin değildir. Kullanıcılar belgeyi yükleme konumundan açmak isterse, Office uygulamasının Güven Merkezi'nde bu konumu güvenilir konumlar listesine eklemeleri gerekir.

### <a name="opening-the-document-of-a-document-level-customization"></a>Belge düzeyinde bir özelleştirmenin belgesini açma
 Kullanıcılar, belge düzeyinde bir özelleştirmenin belgesini doğrudan yükleme konumundan açabilirler veya belgeyi kendi yerel bilgisayarlarına kopyalayıp sonra bu kopyayı açabilirler.

 En iyi uygulama olarak, kullanıcılar belgenin bir kopyasını kendi bilgisayarlarında açmalıdır; böylece birden fazla kullanıcı aynı anda aynı kopyayı açmaya çalışmaz. Bu uygulamayı zorunlu tutmak için, kurulum programınızı, belgeyi kullanıcı bilgisayarlarına kopyalayacak şekilde yapılandırabilirsiniz. Bkz. [bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Bir IIS Web sitesinden dağıtım bildirimini açarak çözümü yükler
 Kullanıcılar, web'ten dağıtım bildirimini açmak suretiyle bir Office çözümünü yükleyebilirler. ancak, Internet Information Services (ııs) güvenli bir yüklemesi *. vsto* uzantısına sahip dosyaları engeller. Bir Office çözümünü IIS kullanarak dağıtabilmeniz için önce MIME türü IIS'de tanımlanmalıdır.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0'a .vsto MIME türünü eklemek için

1. ııs 6,0 çalıştıran sunucuda, **başlat**  >  **tüm programlar**  >  **yönetim araçları**  >   **Internet Information Services (ııs) yöneticisi**' ni seçin.

2. Bilgisayar adını, **Web siteleri** klasörünü veya yapılandırmakta olduğunuz Web sitesini seçin.

3. Menü çubuğunda **eylem**  >  **özellikleri**' ni seçin.

4. HTTP **Üst Bilgileri sekmesinde** **MIME** Türleri düğmesini seçin.

5. **MIME Türleri penceresinde** Yeni **düğmesini** seçin.

6. **MIME Türü penceresinde** uzantı olarak **.vsto** girin, MIME türü olarak **application/x-ms-vsto** girin ve yeni ayarları uygulama.

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Ardından tarayıcının disk önbelleğini boşaltarak *.vsto* dosyasını yeniden açmayı denemeniz gerekir.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>.vsto MIME türünü IIS 7.0'a eklemek için

1. IIS 7.0 çalıştıran sunucuda Tüm Programlar Donatılarını  >  **Başlat'ı**  >  **seçin.**

2. Komut İstemi kısayol **menüsünü açın ve Yönetici** olarak  **çalıştır'ı seçin.**

3. Aç **kutusuna** aşağıdaki yolu girin ve Tamam **düğmesini** seçin.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Aşağıdaki komutu girin ve ardından yeni ayarları uygulayın.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Ardından tarayıcının disk önbelleğini boşaltarak *.vsto* dosyasını yeniden açmayı denemeniz gerekir.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)
 Dağıtım sonrası eylem oluşturarak çözüm belgenizi son kullanıcının bilgisayarına kopyaabilirsiniz. Bu şekilde, kullanıcının çözümü yükledikten sonra belgeyi yükleme konumdan bilgisayarına el ile kopyalaması gerekmez. Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturmanız, çözümü derlemek ve yayımlamanız, uygulama bildirimini değiştirmeniz ve uygulama ile dağıtım bildirimini yeniden imzalamanız gerekir.

 Aşağıdaki yordamlar projenizin adının **ExcelWorkbook** olduğunu ve çözümü bilgisayarınızda **C:\publish** adlı oluşturulan bir klasörde yayımlayabilirsiniz.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturma

1. Menü çubuğunda Dosya Yeni **Ekle'yi**  >  **seçin ve**  >  **Project.**

2. Yeni **Uygulama Ekle iletişim Project** kutusunda, **Yüklü** Şablonlar bölmesinde yeni **Windows** seçin.

3. Şablonlar **bölmesinde Sınıf** Kitaplığı **şablonunu** seçin.

4. Ad **alanına** **FileCopyPDA yazın** ve tamam **düğmesini** seçin.

5. Dosya **Çözüm Gezgini** **DosyaCopyPDA projesini** seçin.

6. Menü çubuğunda Başvuru **Ekle'Project**  >  **seçin.**

7. **.NET sekmesinde** ve başvurularını `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument` ekleyin.

8. sınıfını olarak yeniden `FileCopyPDA` adlandırarak dosyanın içeriğini kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Belgeyi kullanıcının masaüstüne kopyalar.

   - Dağıtım _AssemblyLocation bir göreli yoldan dağıtım bildirimi için tam yol olarak değiştirir.

   - Kullanıcı çözümü kaldırırsa, dosyayı siler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs" id="Snippet7":::

### <a name="build-and-publish-the-solution"></a>Çözümü derleme ve yayımlama

1. Dosya **Çözüm Gezgini,** **FileCopyPDA** projesinin kısayol menüsünü açın ve ardından Oluştur'a **tıklayın.**

2. **ExcelWorkbook** projesinin kısayol menüsünü açın ve Oluştur'a **tıklayın.**

3. **ExcelWorkbook** projesinin kısayol menüsünü açın ve Başvuru **Ekle'yi seçin.**

4. Başvuru **Ekle iletişim kutusunda** Projeler  sekmesini, **DosyaCopyPDA'yı** ve ardından Tamam **düğmesini** seçin.

5. Bu **Çözüm Gezgini** **ExcelWorkbook projesini** seçin.

6. Menü çubuğunda Yeni **Klasör'Project**  >  **seçin.**

7. Veri **girin** ve enter **tuşuna basın.**

8. Bu **Çözüm Gezgini** Veri **klasörünü** seçin.

9. Menü çubuğunda Var Olan Öğeyi  >  **Project'ı seçin.**

10. Var Olan **Öğeyi Ekle** iletişim kutusunda **ExcelWorkbook** projesinin çıkış dizinine gidin, **ExcelWorkbook.xlsx** dosyasını seçin ve ardından Ekle **düğmesini** seçin.

11. Bu **Çözüm Gezgini** **dosyanınExcelWorkbook.xlsx** seçin.

12. Özellikler penceresinde **Derleme** Eylemi özelliğini **İçerik,** Çıkış Dizinine **Kopyala** özelliğini ise Kopyala olarak **değiştirin.** 

     Bu adımları tamamlandıktan sonra projeniz aşağıdaki çizime benzer.

     ![Project sonrası eyleminin yapısı.](../vsto/media/vsto-postdeployment.png "Project sonrası eyleminin yapısı.")

13. **ExcelWorkbook projesini yayımlayın.**

### <a name="modify-the-application-manifest"></a>Uygulama bildiriminde değişiklik yapma

1. c:\publish çözüm **dizinini açmak için** **Dosya Gezgini.**

2. Uygulama **Dosyaları klasörünü** açın ve ardından çözümle ilgili en son yayımlanan sürüme karşılık gelen klasörü açın.

3. **ExcelWorkbook.dll.manifest dosyasını** Not Defteri gibi bir metin düzenleyicisinde açın.

4. öğesinin `</vstav3:update>` ardından aşağıdaki kodu ekleyin. öğesinin sınıf özniteliği için `<vstav3:entryPoint>` şu sözdizimini kullanın: *NamespaceName.ClassName*. Aşağıdaki örnekte, ad alanı ve sınıf adları aynı olduğu için sonuçta elde edilen giriş noktası adı `FileCopyPDA.FileCopyPDA` olur.

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

1. **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** **klasöründe, ExcelWorkbook_TemporaryKey.pfx** sertifika dosyasını kopyalayın ve *publishFolder* **\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ klasörüne yapıştırın.

2. Visual Studio komut istemini açın ve ardından dizinleri **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ klasörüne (örneğin, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**) açın.

3. Aşağıdaki komutu çalıştırarak değiştirilmiş uygulama bildirimini imzalayın:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     "ExcelWorkbook.dll.manifest başarıyla imzalandı" iletisi görüntülenir.

4. **c:\publish klasörüne** gidin ve ardından aşağıdaki komutu çalıştırarak dağıtım bildirimini güncelleştirin ve imzalayın:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Önceki örnekte MostRecentVersionNumber yerine çözüm **1_0_0_4** sürümünün en son yayımlanan sürümünün sürüm numarasını girin.

     "ExcelWorkbook.vsto başarıyla imzalandı" iletisi görüntülenir.

5. *ExcelWorkbook.vsto dosyasını* **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentVersionNumber dizinine_ kopyalayın.

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Çözümün belgesini bir çözümü çalıştıran bir sunucuya SharePoint (yalnızca belge düzeyinde özelleştirmeler)
 Belge düzeyinde özelleştirmenizi SharePoint kullanarak son kullanıcılara yayımlayabilirsiniz. Kullanıcılar SharePoint sitesine gidip belgeyi açtığında, çalışma zamanı çözümü paylaşılan ağ klasöründen kullanıcının yerel bilgisayarına otomatik olarak yükler. Çözüm yerel olarak yüklendikten sonra, belge başka bir yere (örneğin, masaüstüne) kopyalansa bile özelleştirme işlevini yerine getirmeye devam eder.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Belgeyi SharePoint çalıştıran bir sunucuya koymak için

1. Çözüm belgesini SharePoint sitesindeki bir belge kitaplığına ekleyin.

2. Aşağıdaki yaklaşımlardan biri için adımları uygulayın:

    - SharePoint çalıştıran sunucuyu, tüm bilgisayarlarda Word veya Excel'deki Güven Merkezi'ne eklemek için Office Yapılandırma Aracı'nı kullanın.

         Bkz. [2010'da Office ilkeleri ve ayarları.](/previous-versions/office/office-2010/cc178946(v=office.14))

    - Her kullanıcının aşağıdaki adımları uygulamasını sağlayın.

        1. Yerel bilgisayarda Word veya Excel'ı açın, Dosya **sekmesini** ve ardından Seçenekler **düğmesini** seçin.

        2. Güven **Merkezi iletişim** kutusunda Güvenilen **Konumlar düğmesini** seçin.

        3. Ağımda **Güvenilen Konumlara İzin Ver (önerilmez) onay** kutusunu ve ardından Yeni konum ekle **düğmesini** seçin.

        4. Yol **kutusuna,** yüklediğiniz belgeyi içeren SharePoint kitaplığının URL'sini girin (örneğin, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             Varsayılan Web sayfasının adını *(default.aspx* veya *AllItems.aspx gibi) ekleyin.*

        5. Bu **konumun alt klasörlerine de güvenilen onay** kutusunu seçin ve ardından Tamam **düğmesini** seçin.

             Kullanıcılar belgeyi SharePoint sitesinden açtığında, belge açılır ve özelleştirme yüklenir. Kullanıcılar belgeyi kendi masaüstlerine kopyalayabilir. Belgedeki özellikler belgenin ağ konumuna işaret ettiğinden, özelleştirme çalışmaya devam edecektir.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Özel yükleyici oluşturma
 Çözümü yayımlarken sizin için oluşturulan kurulum programını kullanmak yerine Office çözümünüz için özel bir yükleyici oluşturabilirsiniz. Örneğin, bir oturum açma betiği kullanarak yükleme işlemini başlatabilirsiniz veya çözümü kullanıcı etkileşimi olmadan yüklemek için bir toplu iş dosyası kullanabilirsiniz. Bu senaryolar en çok, önkoşullar son kullanıcı bilgisayarlarında zaten yüklü olduğunda işe yarar.

 Özel yükleme işleminizin bir parçası olarak, varsayılan olarak aşağıdaki konuma Office çözüm (*VSTOInstaller.exe*) için yükleyici aracını arayın:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Araç bu konumda değilse, bu aracın yolunu **bulmak içinHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** veya **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** kayıt defteri anahtarını kullanabilirsiniz.

 aşağıdaki parametreleri ile birlikte *kullanabilirsinizVSTOinstaller.exe.*

| Parametre | Tanım |
|------------------| - |
| /Install veya /I | Çözümü yükler. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir yol, evrensel adlandırma kuralı (UNC) dosya paylaşımı belirtebilirsiniz. Yerel bir yol (*C:\FolderName\PublishFolder),* göreli yol (*Yayımla \\*) veya tam konum (*\\ \ServerName\FolderName* veya http://<em>ServerName/FolderName ) belirtebilirsiniz.</em> |
| /Uninstall veya /U | Çözümü kaldırır. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda, UNC dosya paylaşımında bir yol belirtebilirsiniz. Yerel bir yol (*c:\FolderName\PublishFolder*), göreli yol (*Yayımla \\*) veya tam konum (*\\ \ServerName\FolderName* veya http://<em>ServerName/FolderName ) belirtebilirsiniz.</em> |
| /Silent veya /S | Kullanıcıdan bir şey girmesini istemeden veya ileti görüntülemeden yükler veya kaldırır. Bir güven istemi gerekirse özelleştirme yüklenmez veya güncelleştirilmez. |
| /Help or /? | Yardım bilgilerini görüntüler. |

 komutlarını *VSTOinstaller.exe* aşağıdaki hata kodları görünebilir.

|Hata Kodu|Tanım|
|----------------|----------------|
|0|Çözüm başarıyla yüklendi ya da kaldırıldı veya VSTOInstaller Yardımı görüntülendi.|
|-100|Bir veya daha fazla komut satırı seçeneği geçerli değildir veya birden çok kez ayarlanmıştır. Daha fazla bilgi için "vstoinstaller /?" girin veya [bkz. Bir çözüm için özel ClickOnce Office oluşturma.](/previous-versions/bb772078(v=vs.110))|
|-101|Bir veya daha fazla komut satırı seçeneği geçerli değildir. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-200|Dağıtım bildirimi URI'si geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-201|Dağıtım bildirimi geçerli olduğundan çözüm yüklenemedi. Daha [fazla çözüm için dağıtım Office bakın.](../vsto/deployment-manifests-for-office-solutions.md)|
|-202|Uygulama bildiriminin Office için Visual Studio Araçları bölümü geçerli olduğundan çözüm yüklenemedi. Daha [fazla çözüm için uygulama Office bakın.](../vsto/application-manifests-for-office-solutions.md)|
|-203|İndirme hatası meydana geldiği için çözüm yüklenemedi. Dağıtım bildiriminin URI'sini veya ağ dosya konumunu denetleyin ve sonra yeniden deneyin.|
|-300|Bir güvenlik özel durumu meydana geldiği için çözüm yüklenemedi. Bkz. [Güvenli Office çözümleri.](../vsto/securing-office-solutions.md)|
|-400|Çözüm yüklenemedi.|
|-401|Çözüm kaldırılamdı.|
|-500|Çözüm yüklenemediğinden ya da kaldırılamadığından veya dağıtım bildirimi indirilemediğinden işlem iptal edildi.|

## <a name="publish-an-update"></a><a name="Update"></a> Güncelleştirme yayımlama
 Bir çözümü güncelleştirmek için, Project **Tasarımcısı'nı** veya Yayımlama Sihirbazı'nı kullanarak yeniden yayımlarsınız ve ardından güncelleştirilmiş çözümü yükleme konuma kopyalayın. Dosyaları yükleme konumuna kopyalarken, önceki dosyaların üzerine yazdığınızdan emin olun.

 Çözümün bir sonraki güncelleştirme denetimi sırasında yeni sürümü otomatik olarak bulup yüklemesi gerekir.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Çözümün yükleme konumunu değiştirme
 Bir çözüm yayımlandıktan sonra yükleme yolunu ekleyebilir veya değiştirebilirsiniz. Yükleme yolunu değiştirmek istemenizin nedeni şunlardan biri veya daha fazlası olabilir:

- Kurulum programı, henüz yükleme yolu bilinmezken derlenmiştir.

- Çözüm dosyaları farklı bir konuma kopyalanmıştır.

- Yükleme dosyalarını barındıran sunucu yeni bir ada veya konuma sahiptir.

  Bir çözümün yükleme yolunu değiştirmek için kurulum programını güncelleştirmelisiniz; daha sonra da kullanıcıların bunu çalıştırması gerekir. Belge düzeyinde özelleştirmeler için, kullanıcıların ayrıca belgelerindeki bir özelliği de yeni konuma işaret edecek şekilde güncelleştirmeleri gerekir.

> [!NOTE]
> Kullanıcılardan belge özelliklerini güncelleştirmelerini istemiyorsanız, kullanıcılardan güncelleştirilmiş belgeyi yükleme konumdan edinlerini sorabilirsiniz.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Kurulum programındaki yükleme konumunu değiştirmek için

1. Bir **Komut İstemi** penceresi açın ve ardından dizinleri yükleme klasörüne kopyalayın.

2. Kurulum programını çalıştırın ve yeni yükleme `/url` yolunu dize olarak alan parametresini dahil edin.

    Aşağıdaki örnekte, Fabrikam web sitesindeki bir konumun yükleme yolunun nasıl değiştirileceği gösterilmektedir; ancak siz bu URL'yi istediğiniz yol ile değiştirebilirsiniz:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Bir ileti ekrana gelir ve yürütülebilir öğenin imzasının geçersiz kılınacağını belirtirse, çözümü imzalamak için kullanılan sertifika artık geçerli değil ve yayımcısı bilinmiyor demektir. Sonuç olarak, kullanıcıların, çözümü yüklemeden önce çözümün kaynağına güvendiklerini onaylamaları gerekecektir.

   > [!NOTE]
   > URL'nin geçerli değerini görüntülemek için `setup.exe /url` çalıştırın.

   Belge düzeyinde özelleştirmeler için, kullanıcıların belgeyi açması ve ardından kendi _AssemblyLocation güncelleştirmeleri gerekir. Aşağıdaki adımlarda kullanıcıların bu görevi nasıl yerine getirecekleri açıklanmaktadır.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Bir belgede _AssemblyLocation özelliğini güncelleştirmek için

1. Dosya **sekmesinde,** aşağıdaki **çizimde gösterildiği** Gibi Bilgi'yi seçin.

     ![Excel'da Bilgi sekmesi](../vsto/media/vsto-infotab.png "Excel'de Bilgi sekmesi")

2. Özellikler **listesinde,** aşağıdaki **çizimde gösterildiği gibi** Gelişmiş Özellikler'i seçin.

     ![Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Excel.")

3. Özellikler **listesinin** Özel **sekmesinde,** aşağıdaki çizimde _AssemblyLocation'yi seçin.

     ![AssemblyLocation özelliği.](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation özelliği.")

     Değer **kutusu** dağıtım bildirimi tanımlayıcısını içerir.

4. Tanımlayıcıdan önce belgenin tam yolunu ve ardından Yol Tanımlayıcısı  |  (örneğin, *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9)* biçiminde bir çubuk girin.

     Bu tanımlayıcıyı biçimlendirme hakkında daha fazla bilgi için bkz. [Özel belge özelliklerine genel bakış.](../vsto/custom-document-properties-overview.md)

5. Tamam **düğmesini** seçin ve sonra belgeyi kaydedin ve kapatın.

6. Çözümü belirtilen konuma yüklemek için, kurulum programını /url parametresi olmadan çalıştırın.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Çözümü önceki bir sürüme geri alma
 Bir çözümü geri aldığınızda, kullanıcıları bu çözümün önceki bir sürümüne geri döndürmüş olursunuz.

#### <a name="to-roll-back-a-solution"></a>Bir çözümü geri almak için

1. Çözümün yükleme konumunu açın.

2. Üst düzey yayımlama klasöründe dağıtım bildirimini *(.vsto dosyası)* silin.

3. Geri almak istediğiniz sürüme ait alt klasörü bulun.

4. O alt klasördeki dağıtım bildirimini üst düzey publish klasörüne kopyalayın.

     Örneğin, Sürüm 1.0.0.1'den sürüm 1.0.0.0'a **OutlookAddIn1** adlı bir çözümü geri almak için **OutlookAddIn1.vsto** dosyasını **OutlookAddIn1_1_0_0_0 klasöründen** kopyalayın. Dosyayı üst düzey yayımlama klasörüne yapıştırın ve önceden orada olan dağıtımlar için sürüme **özgü OutlookAddIn1_1_0_0_1** bildiriminin üzerine yazın.

     Aşağıdaki resimde, bu örnekteki publish (yayımlama) klasörü yapısı gösterilmektedir.

     ![Klasör Yapısını Yayımlama](../vsto/media/publishfolderstructure.png "Klasör Yapısını Yayımlama")

     Kullanıcının uygulamayı ya da özelleştirilmiş belgeyi bir sonraki açışında, dağıtım bildirimindeki değişiklik algılanır. Office çözümünün önceki sürümü ClickOnce önbelleğinden çalışır.

> [!NOTE]
> Yerel veriler çözümün sadece bir önceki sürümü için kaydedilir. İki sürümü geri almak için yerel veriler elde tutmaz. Yerel veriler hakkında daha fazla bilgi için [bkz. Yerel ve uzak verilere ClickOnce erişin.](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümleri yayımlama](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Nasıl Office: Office kullanarak bir ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Nasıl kurulur: ClickOnce Office yükleme](/previous-versions/bb608592(v=vs.110))
- [Nasıl SharePoint kullanarak belge düzeyinde Office çözümü ClickOnce](/previous-versions/bb608595(v=vs.110))
- [ClickOnce office çözümü için özel yükleyici oluşturma](/previous-versions/bb772078(v=vs.110))