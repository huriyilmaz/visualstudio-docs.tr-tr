---
title: ClickOnce kullanarak Office çözümü ClickOnce
description: Office kullanarak Office daha az adımda nasıl dağıtabilirsiniz ClickOnce. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler.
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
ms.openlocfilehash: 84c3740a1fd51863c782942a12d9863d3bf448c85379f89b82268a01847f0b44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121297054"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce kullanarak Office çözümü ClickOnce
  Office Office daha az adımda dağıt ClickOnce abilirsiniz. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler. Bununla birlikte, ClickOnce, çözümünüzü bir bilgisayarın her kullanıcısı için ayrı ayrı yüklemenizi gerektirir. Bu nedenle, birden fazla kullanıcı Windows aynı *bilgisayarda çalıştıracaksa, Windows* Yükleyicisi'ni (.msi) kullanmayı göz önünde bulundurabilirsiniz.

## <a name="in-this-topic"></a>Bu konuda

- [Çözümü yayımlama](#Publish)

- [Çözüme nasıl güven vermek istediğinize karar verme](#Trust)

- [Kullanıcıların çözümü yüklemesi için yardım](#Helping)

- [Çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)](#Put)

- [Çözümün belgesini bir çözümü çalıştıran bir sunucuya SharePoint (yalnızca belge düzeyinde özelleştirmeler)](#SharePoint)

- [Özel bir yükleyici oluşturma](#Custom)

- [Güncelleştirme yayımlama](#Update)

- [Çözümün yükleme konumunu değiştirme](#Location)

- [Çözümü önceki bir sürüme geri alma](#Roll)

  Windows Installer dosyası oluşturarak bir Office çözümü dağıtma hakkında daha fazla bilgi için bkz. Windows Yükleyicisi kullanarak Office [çözümü dağıtma.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="publish-the-solution"></a><a name="Publish"></a> Çözümü yayımlama
 Yayımlama Sihirbazı'nı veya  Project **Designer'ı kullanarak Project yayımabilirsiniz.** Bu yordamda, yayımlama seçeneklerinin **tam Project sağladığı** için Project Designer'ın kullanıladır. Bkz. [Visual Studio&#41;'de &#40;Office yayımlama sihirbazı. ](../vsto/publish-wizard-office-development-in-visual-studio.md)

#### <a name="to-publish-the-solution"></a>Çözümü yayımlamak için

1. Bu **Çözüm Gezgini** projeniz için adlandırılmış düğümü seçin.

2. Menü çubuğunda , *ProjectName* **Project** seçeneğini **belirleyin.**

3. Project **Tasarımcısı'nda,** aşağıdaki **çizimde** gösterildiği Gibi Yayımla sekmesini seçin.

    ![Project Designer'ın yayımlama sekmesi](../vsto/media/vsto-publishtab.png "Project tasarımcısının yayımla sekmesi")

4. Yayımlama **Klasörü Konumu (ftp sunucusu veya** dosya yolu) kutusuna, **Project Designer'ın** çözüm dosyalarını kopyalaması için istediğiniz klasörün yolunu girin.

    Aşağıdaki yol türlerinden herhangi birini girebilirsiniz.

   - Yerel yol (örneğin, *C:\FolderName\FolderName*).

   - Ağ üzerinde bir klasörün Tekdü Adlandırma Kuralı (UNC) yolu (örneğin, *\\ \ServerName\FolderName*).

   - Göreli yol (örneğin, projenin varsayılan olarak yayımladığı klasör olan *PublishFolder). \\*

5. Yükleme **Klasörü URL'si** kutusuna, son kullanıcıların çözümlerinizi bulacakları konumun tam yolunu girin.

    Konumu henüz bilmiyorsanız bu alana hiçbir şey girmeyin. Varsayılan olarak, ClickOnce, kullanıcılarınızın çözümü yüklediği klasörde güncelleştirmeleri arar.

6. **Önkoşullar düğmesini** seçin.

7. **Önkoşullar** iletişim kutusunda Önkoşul bileşenlerini yüklemek için **kurulum programı oluştur onay kutusunun** seçili olduğundan emin olun.

8. Yükleme **önkoşullarını seçin listesinde,** Windows **Installer 4.5** ve uygun .NET Framework seçin.

    Örneğin, çözümünüz hedefi ise, Windows [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Installer **4.5** ve Microsoft .NET Framework **4.5 Tam** onay kutularını seçin.

9. Çözümünüz .NET Framework 4.5'i hedeflese, **Visual Studio Çalışma Zamanı için Visual Studio 2 Office 010 Araçları onay** kutusunu da seçin.

    > [!NOTE]
    > Varsayılan olarak, bu onay kutusu görünmez. Bu onay kutusunu göstermek için bir Önyükleyici paketi oluşturmanız gerekir. Bkz. [2012 ile Office 2013 VSTO](create-vsto-add-ins-for-office-by-using-visual-studio.md)önyükleyici Visual Studio paketi oluşturma.

10. **Önkoşullar için yükleme konumunu belirtin** altında, görünen seçeneklerden birini belirleyin ve ardından Tamam **düğmesini** seçin.

     Aşağıdaki tabloda her bir seçenek açıklanmaktadır.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |**Bileşen satıcısının web sitesinden önkoşulları indirme**|Kullanıcıdan, bu önkoşulları satıcının sitesinden indirmesi ve yüklemesi istenir.|
    |**Önkoşulları uygulamam ile aynı konumdan indirme**|Önkoşul yazılımı çözümle birlikte yüklenir. Bu seçeneği tercih ederseniz, Visual Studio sizin için önkoşul paketlerinin tümünü yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
    |**Önkoşulları aşağıdaki konumdan indirin**|Visual Studio tüm önkoşul paketlerini belirttiğiniz konuma kopyalar ve bunları çözümle birlikte yükler.|

     Bkz. [Önkoşullar iletişim kutusu.](../ide/reference/prerequisites-dialog-box.md)

11. Güncelleştirmeler **düğmesini** seçin, her bir son kullanıcının güncelleştirmeleri denetlemesi için VSTO veya özelleştirmeyi ne sıklıkta görmek istediğinizi belirtin ve ardından **Tamam düğmesini** seçin.

    > [!NOTE]
    > Cd veya çıkarılabilir sürücü kullanarak dağıtıyorsanız Güncelleştirmeleri hiçbir zaman denetleme **seçeneğini** belirtin.

     Bir güncelleştirmeyi yayımlama hakkında bilgi için bkz. [Güncelleştirme yayımlama.](#Update)

12. Seçenekler **düğmesini** seçin, Seçenekler iletişim kutusundaki **seçenekleri gözden** geçirin ve ardından Tamam **düğmesini** seçin.

13. Şimdi **Yayımla düğmesini** seçin.

     Visual Studio, bu yordamda daha önce belirttiğiniz yayımlama klasörüne aşağıdaki klasörleri ve dosyaları ekler.

    - Uygulama **Dosyaları** klasörü.

    - Kurulum programı.

    - En son sürümün dağıtım bildirimine işaret eden bir dağıtım bildirimi.

      Uygulama **Dosyaları klasörü,** yayımlamış her sürüm için bir alt klasör içerir. Her bir sürüme özgü alt klasörde aşağıdaki dosyalar bulunur.

    - Uygulama bildirimi.

    - Dağıtım bildirimi.

    - Özelleştirme derlemeleri.

      Aşağıdaki çizimde, Outlook VSTO Eklentisinde yayımla klasörünün yapısı gösterilmiştir.

      ![Klasör Yapısını Yayımlama](../vsto/media/publishfolderstructure.png "Klasör yapısını Yayımla")

    > [!NOTE]
    > ClickOnce derlemelere *.deploy* uzantısını ekler, böylece güvenli Internet Information Services (IIS) güvenli olmayan bir uzantı nedeniyle dosyaları engellemez. Kullanıcı çözümü yükleyene ClickOnce *.deploy uzantısını* kaldırır.

14. Çözüm dosyalarını, bu yordamda daha önce belirttiğiniz yükleme konumuna kopyalayın.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Çözüme nasıl güven vermek istediğinize karar verme
 Bir çözümün kullanıcı bilgisayarları üzerinde çalışması için önce, sizin güven kazandırmanız ya da kullanıcıların çözümü yükledikleri sırada bir güvenlik istemine yanıt vermeleri gerekir. Çözüme güven kazandırmak için, bilinen ve güvenilir bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Bkz. [Uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin.](../vsto/granting-trust-to-office-solutions.md#Signing)

 Belge düzeyinde özelleştirme dağıtıyorsanız ve belgeyi kullanıcının bilgisayarına bir klasöre koymak veya belgeyi SharePoint sitesinde kullanılabilir hale Office emin olun. Bkz. [Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Kullanıcıların çözümü yüklemesi için yardım
 Kullanıcılar kurulum programını çalıştırarak, dağıtım bildirimini açarak veya belge düzeyinde özelleştirme sırasında belgeyi doğrudan açarak çözümü yükleyebilir. En iyi uygulama olarak, kullanıcılar çözümünüzü kurulum programını kullanarak yüklemelidir. Diğer iki yaklaşım, önkoşul yazılımının yüklü olduğundan emin değildir. Kullanıcılar belgeyi yükleme konumundan açmak isterse, Office uygulamasının Güven Merkezi'nde bu konumu güvenilir konumlar listesine eklemeleri gerekir.

### <a name="opening-the-document-of-a-document-level-customization"></a>Belge düzeyinde bir özelleştirmenin belgesini açma
 Kullanıcılar, belge düzeyinde bir özelleştirmenin belgesini doğrudan yükleme konumundan açabilirler veya belgeyi kendi yerel bilgisayarlarına kopyalayıp sonra bu kopyayı açabilirler.

 En iyi uygulama olarak, kullanıcılar belgenin bir kopyasını kendi bilgisayarlarında açmalıdır; böylece birden fazla kullanıcı aynı anda aynı kopyayı açmaya çalışmaz. Bu uygulamayı zorunlu tutmak için, kurulum programınızı, belgeyi kullanıcı bilgisayarlarına kopyalayacak şekilde yapılandırabilirsiniz. Bkz. [Çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Iis web sitesinden dağıtım bildirimini açarak çözümü yükleyin
 Kullanıcılar, web'ten dağıtım bildirimini açmak suretiyle bir Office çözümünü yükleyebilirler. Ancak, *.vsto* uzantısına Internet Information Services (IIS) güvenli bir yüklemesi dosyaları engelleyebilir. Bir Office çözümünü IIS kullanarak dağıtabilmeniz için önce MIME türü IIS'de tanımlanmalıdır.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0'a .vsto MIME türünü eklemek için

1. IIS 6.0 çalıştıran sunucuda Tüm Programları Başlat YönetimSelsel Araçlar  >    >    >   **(IIS) Yöneticisi Internet Information Services 'yi seçin.**

2. Bilgisayar adını, **Web Siteleri** klasörünü veya yapılandırmakta olduğunu web sitesini seçin.

3. Menü çubuğunda Eylem **Özellikleri'ne**  >  **tıklayın.**

4. **Http üstbilgileri** sekmesinde **MIME türleri** düğmesini seçin.

5. **MIME türleri** penceresinde **Yeni** düğmesini seçin.

6. **MIME türü** penceresinde, uzantısı olarak **. VSTO** yazın, MIME türü olarak **Application/x-MS-VSTO** girin ve ardından yeni ayarları uygulayın.

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Daha sonra tarayıcının disk önbelleğini boşaltıp *. VSTO* dosyasını yeniden açmayı deneyin.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>IIS 7,0. vsto MIME türünü eklemek için

1. IIS 7,0 çalıştıran sunucuda   >  **tüm programlar**  >  **aksesuarları**' nı Başlat ' ı seçin.

2. **Komut istemi** kısayol menüsünü açın ve ardından **yönetici olarak çalıştır** ' ı seçin.

3. **Aç** kutusuna aşağıdaki yolu girin ve **Tamam** düğmesini seçin.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Aşağıdaki komutu girin ve ardından yeni ayarları uygulayın.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Daha sonra tarayıcının disk önbelleğini boşaltıp *. VSTO* dosyasını yeniden açmayı deneyin.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)
 Bir dağıtım sonrası eylemi oluşturarak çözümünüzün belgesini son kullanıcının bilgisayarına kopyalayabilirsiniz. Bu şekilde, çözümünüzü yükledikten sonra kullanıcının belgeyi yükleme konumundan kendi bilgisayarlarına el ile kopyalaması gerekmez. Dağıtım sonrası eylemini tanımlayan bir sınıf oluşturmanız, çözümü oluşturup yayımlamanız, uygulama bildirimini değiştirmeniz ve uygulamayı ve dağıtım bildirimini yeniden imzalamanız gerekir.

 Aşağıdaki yordamlar, proje adınızın **ExcelWorkbook** olduğunu ve çözümü bilgisayarınızda **C:\publish** adlı oluşturulan bir klasöre yayımladığınızı varsayar.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturma

1. menü çubuğunda **dosya**  >  **ekle**  >  **yeni Project**' yi seçin.

2. **yeni Project ekle** iletişim kutusunda, **yüklü şablonlar** bölmesinde **Windows** klasörünü seçin.

3. **Şablonlar** bölmesinde, **sınıf kitaplığı** şablonunu seçin.

4. **Ad** alanına **FileCopyPDA** girin ve **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **FileCopyPDA** projesini seçin.

6. menü çubuğunda **Project**  >  **başvuru ekle**' yi seçin.

7. **.Net** sekmesinde, ve başvurularını ekleyin `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument` .

8. Sınıfını olarak yeniden adlandırın `FileCopyPDA` ve sonra dosyanın içeriğini kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Belgeyi kullanıcının masaüstüne kopyalar.

   - Dağıtım bildirimi için _AssemblyLocation özelliğini göreli yoldan tam yola dönüştürür.

   - Kullanıcı çözümü kaldırırsa, dosyayı siler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs" id="Snippet7":::

### <a name="build-and-publish-the-solution"></a>Çözümü derleme ve yayımlama

1. **Çözüm Gezgini**, **FileCopyPDA** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

2. **ExcelWorkbook** projesinin kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

3. **ExcelWorkbook** projesinin kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

4. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin, **FileCopyPDA**' ı seçin ve ardından **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **ExcelWorkbook** projesini seçin.

6. menü çubuğunda   >  **yeni klasör** Project ' yi seçin.

7. **Veri** girin ve **ENTER** tuşunu seçin.

8. **Çözüm Gezgini**, **veri** klasörünü seçin.

9. menü çubuğunda **Project**  >  **varolan öğe ekle**' yi seçin.

10. **Varolan öğe Ekle** iletişim kutusunda, **ExcelWorkbook** projesinin çıkış dizinine gidin, **ExcelWorkbook.xlsx** dosyasını seçin ve sonra **Ekle** düğmesini seçin.

11. **Çözüm Gezgini** **ExcelWorkbook.xlsx** dosyasını seçin.

12. **Özellikler** penceresinde, **derleme eylemi** özelliğini **içerik** olarak değiştirin ve **daha yeniyse kopyalamak** için **Çıkış Dizinine Kopyala** özelliğini değiştirin.

     Bu adımları tamamladığınızda, projeniz aşağıdaki çizime benzeyecektir.

     ![dağıtım sonrası eyleminin Project yapısı.](../vsto/media/vsto-postdeployment.png "dağıtım sonrası eyleminin Project yapısı.")

13. **ExcelWorkbook** projesini yayımlayın.

### <a name="modify-the-application-manifest"></a>Uygulama bildiriminde değişiklik yapma

1. **Dosya Gezgini**'ni kullanarak **c:\publish** çözüm dizinini açın.

2. **Uygulama dosyaları** klasörünü açın ve ardından çözümünüzün en son yayımlanmış sürümüne karşılık gelen klasörü açın.

3. **ExcelWorkbook.dll. manifest** dosyasını Not Defteri gibi bir metin düzenleyicisinde açın.

4. Öğesinden sonra `</vstav3:update>` aşağıdaki kodu ekleyin. Öğesinin sınıf özniteliği için `<vstav3:entryPoint>` şu sözdizimini kullanın: *NamespaceName. ClassName*. Aşağıdaki örnekte, ad alanı ve sınıf adları aynıdır, bu nedenle sonuçtaki giriş noktası adı olur `FileCopyPDA.FileCopyPDA` .

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

1. **%userprofile%\documents\ Visual Studio 2013 \ \ excel \ kullanıcılar \ ExcelWorkbook** klasöründe, **ExcelWorkbook_TemporaryKey. pfx** sertifika dosyasını kopyalayın ve *publishfolder* **\application files\excelworkbook** \_ _mostrecentpublishedversion_ klasörüne yapıştırın.

2. Visual Studio komut istemi ' ni açın ve ardından dizinleri **c:\publish\application files\excelworkbook** \_ _mostrecentpublishedversion_ klasörüne (örneğin, **c:\publish\application files \ ExcelWorkbook_1_0_0_4**) değiştirin.

3. Aşağıdaki komutu çalıştırarak değiştirilmiş uygulama bildirimini imzalayın:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     "ExcelWorkbook.dll.manifest başarıyla imzalandı" iletisi görüntülenir.

4. **C:\publish** klasörünü değiştirin ve ardından aşağıdaki komutu çalıştırarak dağıtım bildirimini güncelleştirin ve imzalayın:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Önceki örnekte, MostRecentVersionNumber ' ı çözümünüzün en son yayınlanan sürümünün sürüm numarasıyla değiştirin (örneğin, **1_0_0_4**).

     "ExcelWorkbook.vsto başarıyla imzalandı" iletisi görüntülenir.

5. *ExcelWorkbook. VSTO* dosyasını **c:\publish\Application files\excelworkbook** \_ _mostrecentversionnumber_ dizinine kopyalayın.

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>bir çözümün belgesini SharePoint çalıştıran bir sunucuya koyma (yalnızca belge düzeyinde özelleştirmeler)
 Belge düzeyinde özelleştirmenizi SharePoint kullanarak son kullanıcılara yayımlayabilirsiniz. Kullanıcılar SharePoint sitesine gidip belgeyi açtığında, çalışma zamanı çözümü paylaşılan ağ klasöründen kullanıcının yerel bilgisayarına otomatik olarak yükler. Çözüm yerel olarak yüklendikten sonra, belge başka bir yere (örneğin, masaüstüne) kopyalansa bile özelleştirme işlevini yerine getirmeye devam eder.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Belgeyi SharePoint çalıştıran bir sunucuya koymak için

1. Çözüm belgesini SharePoint sitesindeki bir belge kitaplığına ekleyin.

2. Aşağıdaki yaklaşımlardan biri için adımları uygulayın:

    - SharePoint çalıştıran sunucuyu, tüm bilgisayarlarda Word veya Excel'deki Güven Merkezi'ne eklemek için Office Yapılandırma Aracı'nı kullanın.

         bkz. [Office 2010 güvenlik ilkeleri ve ayarları](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Her kullanıcının aşağıdaki adımları uygulamasını sağlayın.

        1. yerel bilgisayarda, Word 'ü veya Excel açın, **dosya** sekmesini seçin ve ardından **seçenekler** düğmesini seçin.

        2. **Güven Merkezi** Iletişim kutusunda **güvenilir konumlar** düğmesini seçin.

        3. **Ağımdaki Güvenilen konumlara Izin ver (önerilmez)** onay kutusunu seçin ve ardından **Yeni Konum Ekle** düğmesini seçin.

        4. **yol** kutusuna, karşıya yüklediğiniz belgeyi içeren SharePoint belge kitaplığının URL 'sini girin (örneğin, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             Default *. aspx* veya *AllItems. aspx* gibi varsayılan Web sayfasının adını eklemeyin.

        5. **Bu konumun alt klasörlerinde da güvenilir** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

             Kullanıcılar belgeyi SharePoint sitesinden açtığında, belge açılır ve özelleştirme yüklenir. Kullanıcılar belgeyi kendi masaüstlerine kopyalayabilir. Belgedeki özellikler belgenin ağ konumuna işaret ettiğinden, özelleştirme çalışmaya devam edecektir.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Özel bir yükleyici oluşturma
 çözümü yayımladığınızda sizin için oluşturulan kurulum programını kullanmak yerine Office çözümünüz için özel bir yükleyici oluşturabilirsiniz. Örneğin, yüklemeyi başlatmak için bir oturum açma komut dosyası kullanabilir veya bir toplu iş dosyası kullanarak çözümü Kullanıcı etkileşimi olmadan yükleyebilirsiniz. Bu senaryolar en çok, önkoşullar son kullanıcı bilgisayarlarında zaten yüklü olduğunda işe yarar.

 özel yükleme işleminizin bir parçası olarak, varsayılan olarak aşağıdaki konumda yüklü olan Office çözümleri (*VSTOInstaller.exe*) için yükleyici aracını çağırın:

 *%CommonProgramFiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Araç bu konumda değilse, bu aracın yolunu bulmak için **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** veya **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** kayıt defteri anahtarını kullanabilirsiniz.

 *VSTOinstaller.exe* ile aşağıdaki parametreleri kullanabilirsiniz.

| Parametre | Tanım |
|------------------| - |
| /Install veya /I | Çözümü yükler. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir evrensel adlandırma kuralı (UNC) dosya paylaşımında bir yol belirtebilirsiniz. Yerel bir yol (*C:\folder\\publishfolder*), göreli bir yol (*Yayımla \\*) veya tam bir konum (*\\ \Sunucuadı* \ KlasörAdı veya http://<em>ServerName/KlasörAdı</em>) belirtebilirsiniz. |
| /Uninstall veya /U | Çözümü kaldırır. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir UNC dosya paylaşımında bir yol belirtebilirsiniz. Yerel bir yol (*C:\folder\\publishfolder*), göreli bir yol (*Yayımla \\*) veya tam bir konum (*\\ \Sunucuadı* \ KlasörAdı veya http://<em>ServerName/KlasörAdı</em>) belirtebilirsiniz. |
| /Silent veya /S | Kullanıcıdan bir şey girmesini istemeden veya ileti görüntülemeden yükler veya kaldırır. Güven istemi gerekiyorsa, özelleştirme yüklenmez veya güncellenmez. |
| /Help or /? | Yardım bilgilerini görüntüler. |

 *VSTOinstaller.exe* çalıştırdığınızda aşağıdaki hata kodları görünebilir.

|Hata Kodu|Tanım|
|----------------|----------------|
|0|Çözüm başarıyla yüklendi ya da kaldırıldı veya VSTOInstaller Yardımı görüntülendi.|
|-100|Bir veya daha fazla komut satırı seçeneği geçerli değil veya birden çok kez ayarlanmış. Daha fazla bilgi için "vstoinstaller/?" girin veya bkz. [bir ClickOnce Office çözümü için özel yükleyici oluşturma](/previous-versions/bb772078(v=vs.110)).|
|-101|Bir veya daha fazla komut satırı seçeneği geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-200|Dağıtım bildirimi URI 'SI geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-201|Dağıtım bildirimi geçerli olmadığından çözüm yüklenemedi. [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)' ne bakın.|
|-202|uygulama bildiriminin Office için Visual Studio Araçları bölümü geçerli olmadığından çözüm yüklenemedi. [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)bölümüne bakın.|
|-203|Yükleme hatası oluştuğundan çözüm yüklenemedi. Dağıtım bildiriminin URI'sini veya ağ dosya konumunu denetleyin ve sonra yeniden deneyin.|
|-300|Güvenlik özel durumu oluştuğundan çözüm yüklenemedi. bkz. [Secure Office solutions](../vsto/securing-office-solutions.md).|
|-400|Çözüm yüklenemedi.|
|-401|Çözüm kaldırılamadı.|
|-500|Çözüm yüklenemediğinden ya da kaldırılamadığından veya dağıtım bildirimi indirilemediğinden işlem iptal edildi.|

## <a name="publish-an-update"></a><a name="Update"></a> Güncelleştirme yayımlama
 bir çözümü güncelleştirmek için **Project tasarımcısı** veya **yayımla sihirbazı**' nı kullanarak yeniden yayımlayın ve sonra güncelleştirilmiş çözümü yükleme konumuna kopyalayın. Dosyaları yükleme konumuna kopyalarken, önceki dosyaların üzerine yazdığınızdan emin olun.

 Çözümün bir güncelleştirmeyi bir sonraki sefer denetlemesi, yeni sürümü otomatik olarak bulup yükler.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Bir çözümün yükleme konumunu değiştirme
 Bir çözüm yayımlandıktan sonra yükleme yolunu ekleyebilir veya değiştirebilirsiniz. Yükleme yolunu değiştirmek istemenizin nedeni şunlardan biri veya daha fazlası olabilir:

- Kurulum programı, henüz yükleme yolu bilinmezken derlenmiştir.

- Çözüm dosyaları farklı bir konuma kopyalanmıştır.

- Yükleme dosyalarını barındıran sunucu yeni bir ada veya konuma sahiptir.

  Bir çözümün yükleme yolunu değiştirmek için kurulum programını güncelleştirmelisiniz; daha sonra da kullanıcıların bunu çalıştırması gerekir. Belge düzeyinde özelleştirmeler için, kullanıcıların ayrıca belgelerindeki bir özelliği de yeni konuma işaret edecek şekilde güncelleştirmeleri gerekir.

> [!NOTE]
> Kullanıcılardan belge özelliklerini güncelleştirmesini istemek istemiyorsanız, kullanıcılardan güncelleştirilmiş belgeyi yükleme konumundan almasını isteyebilirsiniz.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Kurulum programındaki yükleme konumunu değiştirmek için

1. Bir **komut istemi** penceresi açın ve sonra dizinleri yükleme klasörüyle değiştirin.

2. Kurulum programını çalıştırın ve `/url` Yeni yükleme yolunu bir dize olarak alan parametresini ekleyin.

    Aşağıdaki örnekte, Fabrikam web sitesindeki bir konumun yükleme yolunun nasıl değiştirileceği gösterilmektedir; ancak siz bu URL'yi istediğiniz yol ile değiştirebilirsiniz:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Bir ileti ekrana gelir ve yürütülebilir öğenin imzasının geçersiz kılınacağını belirtirse, çözümü imzalamak için kullanılan sertifika artık geçerli değil ve yayımcısı bilinmiyor demektir. Sonuç olarak, kullanıcıların, çözümü yüklemeden önce çözümün kaynağına güvendiklerini onaylamaları gerekecektir.

   > [!NOTE]
   > URL 'nin geçerli değerini göstermek için, öğesini çalıştırın `setup.exe /url` .

   Belge düzeyi özelleştirmeleri için, kullanıcıların belgeyi açması ve sonra _AssemblyLocation özelliğini güncelleştirmesi gerekir. Aşağıdaki adımlarda kullanıcıların bu görevi nasıl yerine getirecekleri açıklanmaktadır.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Bir belgede _AssemblyLocation özelliğini güncelleştirmek için

1. **Dosya** sekmesinde, aşağıdaki çizimin gösterdiği **bilgi**' yi seçin.

     ![Excel bilgi sekmesi](../vsto/media/vsto-infotab.png "Excel bilgi sekmesi")

2. **Özellikler** listesinde, aşağıdaki çizimin gösterdiği **Gelişmiş Özellikler**' i seçin.

     ![Excel gelişmiş özellikler.](../vsto/media/vsto-advanceddocumentproperties.png "Excel.")

3. **Özellikler** listesindeki **özel** sekmesinde, aşağıdaki çizimde gösterildiği gibi _AssemblyLocation ' yi seçin.

     ![AssemblyLocation özelliği.](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation özelliği.")

     **Değer** kutusu, dağıtım bildirimi tanımlayıcısını içerir.

4. Tanımlayıcıdan önce, belgenin tam yolunu girin ve ardından bir çubuk, biçim *yolu* | *tanımlayıcısında* (örneğin, *File://ServerName/FolderName/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Bu tanımlayıcıyı biçimlendirme hakkında daha fazla bilgi için bkz. [özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md).

5. **Tamam** düğmesini seçin ve ardından belgeyi kaydedin ve kapatın.

6. Çözümü belirtilen konuma yüklemek için, kurulum programını /url parametresi olmadan çalıştırın.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Bir çözümü önceki bir sürüme geri alma
 Bir çözümü geri aldığınızda, kullanıcıları bu çözümün önceki bir sürümüne geri döndürmüş olursunuz.

#### <a name="to-roll-back-a-solution"></a>Bir çözümü geri almak için

1. Çözümün yükleme konumunu açın.

2. Üst düzey yayımlama klasöründe, dağıtım bildirimini ( *. VSTO* dosyası) silin.

3. Geri almak istediğiniz sürüme ait alt klasörü bulun.

4. O alt klasördeki dağıtım bildirimini üst düzey publish klasörüne kopyalayın.

     Örneğin, **OutlookAddIn1** adlı bir çözümü 1.0.0.1 sürümüne 1.0.0.0 sürümüne geri almak için **OutlookAddIn1. VSTO** dosyasını **Outlookaddın1_1_0_0_0** klasöründen kopyalayın. Zaten orada olan **OutlookAddIn1_1_0_0_1** için sürüme özgü dağıtım bildiriminin üzerine yazarak dosyayı en üst düzey yayınlama klasörüne yapıştırın.

     Aşağıdaki resimde, bu örnekteki publish (yayımlama) klasörü yapısı gösterilmektedir.

     ![Klasör yapısını Yayımla](../vsto/media/publishfolderstructure.png "Klasör Yapısını Yayımlama")

     Kullanıcının uygulamayı ya da özelleştirilmiş belgeyi bir sonraki açışında, dağıtım bildirimindeki değişiklik algılanır. Office çözümünün önceki sürümü ClickOnce önbelleğinden çalışır.

> [!NOTE]
> Yerel veriler çözümün sadece bir önceki sürümü için kaydedilir. İki sürümü geri alırsanız yerel veriler korunmaz. yerel veriler hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak verilere erişme](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümleri yayımlama](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [nasıl yapılır: ClickOnce kullanarak Office çözümünü yayımlama](/previous-versions/bb386095(v=vs.110))
- [nasıl yapılır: ClickOnce Office çözümü yüklemesi](/previous-versions/bb608592(v=vs.110))
- [nasıl yapılır: ClickOnce kullanarak bir SharePoint sunucusuna belge düzeyinde Office çözümü yayımlama](/previous-versions/bb608595(v=vs.110))
- [ClickOnce office çözümü için özel bir yükleyici oluşturma](/previous-versions/bb772078(v=vs.110))