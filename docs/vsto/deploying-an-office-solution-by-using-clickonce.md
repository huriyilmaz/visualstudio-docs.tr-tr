---
title: ClickOnce kullanarak Office çözümü dağıtma
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
ms.openlocfilehash: d69e50551f664ab3f3e987f0d113285f50d1315d
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986124"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce kullanarak Office çözümü dağıtma
  ClickOnce kullanıyorsanız Office çözümünüzü daha az adımda dağıtabilirsiniz. Güncelleştirmeleri yayımlarsanız, çözümünüz bunları otomatik olarak algılar ve yükler. Bununla birlikte, ClickOnce, çözümünüzü bir bilgisayarın her kullanıcısı için ayrı ayrı yüklemenizi gerektirir. Bu nedenle, birden fazla Kullanıcı çözümünüzü aynı bilgisayarda çalıştırabileceğinden, Windows Installer ( *. msi*) kullanmayı düşünmelisiniz.

## <a name="in-this-topic"></a>Bu konuda

- [Çözümü yayımlama](#Publish)

- [Çözüme nasıl güven vermek istediğinize karar verin](#Trust)

- [Kullanıcıların çözümü yüklemesine yardımcı olma](#Helping)

- [Bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)](#Put)

- [Bir çözümün belgesini SharePoint çalıştıran bir sunucuya koyma (yalnızca belge düzeyinde özelleştirmeler)](#SharePoint)

- [Özel bir yükleyici oluşturma](#Custom)

- [Güncelleştirme yayımlama](#Update)

- [Bir çözümün yükleme konumunu değiştirme](#Location)

- [Bir çözümü önceki bir sürüme geri alma](#Roll)

  Bir Windows Installer dosyası oluşturarak Office çözümünü dağıtma hakkında daha fazla bilgi için, bkz. [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Publish"></a>Çözümü yayımlama
 Çözümünüzü **Yayımla sihirbazını** veya **Proje tasarımcısını**kullanarak yayımlayabilirsiniz. Bu yordamda, tüm yayımlama seçenekleri kümesini sağladığından **Proje tasarımcısını** kullanacaksınız. Bkz. [Visual &#40;Studio&#41;'da Yayımlama Sihirbazı Office geliştirme](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Çözümü yayımlamak için

1. **Çözüm Gezgini**, projeniz için adlandırılmış düğümü seçin.

2. Menü çubuğunda **Proje**, *ProjectName* **Özellikler**' i seçin.

3. **Proje tasarımcısında**, aşağıdaki çizimin gösterdiği **Yayımla** sekmesini seçin.

    ![Proje Tasarımcısı ' nın Yayımla sekmesi](../vsto/media/vsto-publishtab.png "Proje Tasarımcısı ' nın Yayımla sekmesi")

4. **Yayımlama klasörü konumu (FTP sunucusu veya dosya yolu)** kutusunda, **Proje Tasarımcısı** 'nın çözüm dosyalarını kopyalamasını istediğiniz klasörün yolunu girin.

    Aşağıdaki yol türlerinden herhangi birini girebilirsiniz.

   - Yerel bir yol (örneğin, *C:\folderadı \ KlasörAdı*).

   - Ağınızdaki bir klasörün Tekdüzen adlandırma kuralı (UNC) yolu (örneğin, *\\\Sunucuadı \ KlasörAdı*).

   - Bir göreli yol (örneğin, *publishfolder\\* , bu, projenin varsayılan olarak yayımlandığı klasördür).

5. **Yükleme klasörü URL 'si** kutusuna, son kullanıcıların çözümünüzü bulacağı konumun tam yolunu girin.

    Konumu henüz bilmiyorsanız, bu alana hiçbir şey girmeyin. Varsayılan olarak, ClickOnce, kullanıcılarınızın çözümü yüklediği klasörde güncelleştirmeleri arar.

6. **Önkoşullar** düğmesini seçin.

7. **Önkoşullar** iletişim kutusunda, **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** onay kutusunun işaretli olduğundan emin olun.

8. **Yüklenecek önkoşulları seçin** listesinde, **Windows Installer 4,5** ve uygun .NET Framework paketinin onay kutularını seçin.

    Örneğin, çözümünüz [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]hedefliyorsa, **Windows Installer 4,5** ve **Microsoft .NET Framework 4,5 Full**onay kutularını seçin.

9. Çözümünüz 4,5 .NET Framework hedefliyorsa, **Office çalışma zamanı Için Visual Studio 2010 araçları** onay kutusunu da seçin.

    > [!NOTE]
    > Varsayılan olarak, bu onay kutusu görünmez. Bu onay kutusunu göstermek için bir Önyükleyici paketi oluşturmanız gerekir. Bkz. [Visual Studio 2012 Ile Office 2013 VSTO eklentisi Için önyükleyici paketi oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. **Önkoşullar için yüklemeyi belirtin**altında, görüntülenen seçeneklerden birini belirleyin ve sonra **Tamam** düğmesini seçin.

     Aşağıdaki tabloda her bir seçenek açıklanmaktadır.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |**Önkoşulları bileşen satıcısının Web sitesinden indir**|Kullanıcıdan, bu önkoşulları satıcının sitesinden indirmesi ve yüklemesi istenir.|
    |**Önkoşulları Uygulamam ile aynı konumdan indir**|Önkoşul yazılımı çözümle birlikte yüklenir. Bu seçeneği tercih ederseniz, Visual Studio sizin için önkoşul paketlerinin tümünü yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
    |**Önkoşulları aşağıdaki konumdan indirin**|Visual Studio tüm önkoşul paketlerini belirttiğiniz konuma kopyalar ve bunları çözümle birlikte yükler.|

     Bkz. [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).

11. **Güncelleştirmeler** düğmesini seçin, her son kullanıcının VSTO eklentisinin veya özelleştirmenin güncelleştirmeleri denetlemesini istediğiniz sıklığı belirtin ve sonra **Tamam** düğmesini seçin.

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

      Aşağıdaki çizimde bir Outlook VSTO eklentisinin Yayımla klasörünün yapısı gösterilmektedir.

      ![Klasör yapısını Yayımla](../vsto/media/publishfolderstructure.png "Klasör yapısını Yayımla")

    > [!NOTE]
    > ClickOnce, güvenli olmayan bir uzantı nedeniyle Internet Information Services (IIS) güvenli yüklemesinin dosyaları engelmeyeceği şekilde derlemelere *. deploy* uzantısını ekler. Kullanıcı çözümü yüklediğinde ClickOnce *. deploy* uzantısını kaldırır.

14. Çözüm dosyalarını, bu yordamda daha önce belirttiğiniz yükleme konumuna kopyalayın.

## <a name="Trust"></a>Çözüme nasıl güven vermek istediğinize karar verin
 Bir çözümün kullanıcı bilgisayarları üzerinde çalışması için önce, sizin güven kazandırmanız ya da kullanıcıların çözümü yükledikleri sırada bir güvenlik istemine yanıt vermeleri gerekir. Çözüme güven kazandırmak için, bilinen ve güvenilir bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Bkz. [uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin](../vsto/granting-trust-to-office-solutions.md#Signing).

 Belge düzeyinde bir özelleştirme dağıtıyorsanız ve belgeyi kullanıcının bilgisayarındaki bir klasöre koymak veya belgeyi bir SharePoint sitesinde kullanılabilir hale getirmek istiyorsanız, Office 'in belge konumuna güvendiğinden emin olun. Bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="Helping"></a>Kullanıcıların çözümü yüklemesine yardımcı olma
 Kullanıcılar, Kurulum programını çalıştırarak, dağıtım bildirimini açarak veya belge düzeyinde özelleştirme sırasında belgeyi doğrudan açarak çözümü yükleyebilir. En iyi uygulama olarak, kullanıcılar çözümünüzü kurulum programını kullanarak yüklemelidir. Diğer iki yaklaşım, önkoşul yazılımının yüklü olduğundan emin değildir. Kullanıcılar belgeyi yükleme konumundan açmak isterse, Office uygulamasının Güven Merkezi'nde bu konumu güvenilir konumlar listesine eklemeleri gerekir.

### <a name="opening-the-document-of-a-document-level-customization"></a>Belge düzeyinde bir özelleştirmenin belgesini açma
 Kullanıcılar, belge düzeyinde bir özelleştirmenin belgesini doğrudan yükleme konumundan açabilirler veya belgeyi kendi yerel bilgisayarlarına kopyalayıp sonra bu kopyayı açabilirler.

 En iyi uygulama olarak, kullanıcılar belgenin bir kopyasını kendi bilgisayarlarında açmalıdır; böylece birden fazla kullanıcı aynı anda aynı kopyayı açmaya çalışmaz. Bu uygulamayı zorunlu tutmak için, kurulum programınızı, belgeyi kullanıcı bilgisayarlarına kopyalayacak şekilde yapılandırabilirsiniz. Bkz. [bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Bir IIS Web sitesinden dağıtım bildirimini açarak çözümü yükler
 Kullanıcılar, web'ten dağıtım bildirimini açmak suretiyle bir Office çözümünü yükleyebilirler. Ancak, Internet Information Services (IIS) güvenli bir yüklemesi *. VSTO* uzantısına sahip dosyaları engeller. Bir Office çözümünü IIS kullanarak dağıtabilmeniz için önce MIME türü IIS'de tanımlanmalıdır.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0'a .vsto MIME türünü eklemek için

1. IIS 6,0 çalıştıran sunucuda, > **Başlat** ' ı seçin > **tüm programlar** **YÖNETIM araçları** >  **Internet Information Services (IIS) Yöneticisi**' ni seçin.

2. Bilgisayar adını, **Web siteleri** klasörünü veya yapılandırmakta olduğunuz Web sitesini seçin.

3. Menü çubuğunda **eylem** > **Özellikler**' i seçin.

4. **Http üstbilgileri** sekmesinde **MIME türleri** düğmesini seçin.

5. **MIME türleri** penceresinde **Yeni** düğmesini seçin.

6. **MIME türü** penceresinde, uzantısı olarak **. VSTO** yazın, MIME türü olarak **Application/x-MS-VSTO** girin ve ardından yeni ayarları uygulayın.

    > [!NOTE]
    > Değişikliklerin etkili olması için, World Wide Web Yayımlama Hizmeti'ni yeniden başlatmalı veya çalışan işleminin tekrar geri dönmesini beklemelisiniz. Daha sonra tarayıcının disk önbelleğini boşaltıp *. VSTO* dosyasını yeniden açmayı deneyin.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>IIS 7,0. vsto MIME türünü eklemek için

1. IIS 7,0 çalıştıran sunucuda, **donatılar** > **tüm programlar** > **Başlat** ' ı seçin.

2. **Komut istemi**kısayol menüsünü açın ve ardından **yönetici olarak çalıştır** ' ı seçin.

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

## <a name="Put"></a>Bir çözümün belgesini son kullanıcının bilgisayarına koyma (yalnızca belge düzeyinde özelleştirmeler)
 Bir dağıtım sonrası eylemi oluşturarak çözümünüzün belgesini son kullanıcının bilgisayarına kopyalayabilirsiniz. Bu şekilde, çözümünüzü yükledikten sonra kullanıcının belgeyi yükleme konumundan kendi bilgisayarlarına el ile kopyalaması gerekmez. Dağıtım sonrası eylemini tanımlayan bir sınıf oluşturmanız, çözümü oluşturup yayımlamanız, uygulama bildirimini değiştirmeniz ve uygulamayı ve dağıtım bildirimini yeniden imzalamanız gerekir.

 Aşağıdaki yordamlar, proje adınızın **ExcelWorkbook** olduğunu ve çözümü bilgisayarınızda **C:\publish** adlı oluşturulan bir klasöre yayımladığınızı varsayar.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Dağıtım sonrası eylemi tanımlayan bir sınıf oluşturma

1. Menü çubuğunda **dosya**  >   > **Yeni proje** **Ekle** ' yi seçin.

2. **Yeni Proje Ekle** iletişim kutusunda, **yüklü şablonlar** bölmesinde **Windows** klasörünü seçin.

3. **Şablonlar** bölmesinde, **sınıf kitaplığı** şablonunu seçin.

4. **Ad** alanına **FileCopyPDA**girin ve **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **FileCopyPDA** projesini seçin.

6. Menü çubuğunda, **proje** > **Başvuru Ekle**' yi seçin.

7. **.Net** sekmesinde, `Microsoft.VisualStudio.Tools.Applications.Runtime` ve `Microsoft.VisualStudio.Tools.Applications.ServerDocument`başvuruları ekleyin.

8. Sınıfı `FileCopyPDA`olarak yeniden adlandırın ve sonra dosyanın içeriğini kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Belgeyi kullanıcının masaüstüne kopyalar.

   - Dağıtım bildirimi için _AssemblyLocation özelliğini göreli yoldan tam yola dönüştürür.

   - Kullanıcı çözümü kaldırırsa, dosyayı siler.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Çözümü derleme ve yayımlama

1. **Çözüm Gezgini**, **FileCopyPDA** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

2. **ExcelWorkbook** projesinin kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

3. **ExcelWorkbook** projesinin kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

4. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin, **FileCopyPDA**' ı seçin ve ardından **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **ExcelWorkbook** projesini seçin.

6. Menü çubuğunda, **proje** > **Yeni klasör**' ü seçin.

7. **Veri**girin ve **ENTER** tuşunu seçin.

8. **Çözüm Gezgini**, **veri** klasörünü seçin.

9. Menü çubuğunda, **proje** > **Varolan öğe Ekle**' yi seçin.

10. **Varolan öğe Ekle** iletişim kutusunda, **ExcelWorkbook** projesinin çıkış dizinine gidin, **ExcelWorkbook. xlsx** dosyasını seçin ve sonra **Ekle** düğmesini seçin.

11. **Çözüm Gezgini** **ExcelWorkbook. xlsx** dosyasını seçin.

12. **Özellikler** penceresinde, **derleme eylemi** özelliğini **içerik** olarak değiştirin ve **daha yeniyse kopyalamak**için **Çıkış Dizinine Kopyala** özelliğini değiştirin.

     Bu adımları tamamladığınızda, projeniz aşağıdaki çizime benzeyecektir.

     ![Dağıtım sonrası eyleminin proje yapısı.](../vsto/media/vsto-postdeployment.png "Dağıtım sonrası eyleminin proje yapısı.")

13. **ExcelWorkbook** projesini yayımlayın.

### <a name="modify-the-application-manifest"></a>Uygulama bildiriminde değişiklik yapma

1. **Dosya Gezgini**'ni kullanarak **c:\publish**çözüm dizinini açın.

2. **Uygulama dosyaları** klasörünü açın ve ardından çözümünüzün en son yayımlanmış sürümüne karşılık gelen klasörü açın.

3. **ExcelWorkbook. dll. manifest** dosyasını Not Defteri gibi bir metin düzenleyicisinde açın.

4. `</vstav3:update>` öğesinden sonra aşağıdaki kodu ekleyin. `<vstav3:entryPoint>` öğesinin class özniteliği için şu sözdizimini kullanın: *NamespaceName. ClassName*. Aşağıdaki örnekte, ad alanı ve sınıf adları aynıdır, bu nedenle elde edilen giriş noktası adı `FileCopyPDA.FileCopyPDA`.

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

1. **%USERPROFILE%\k\studio 2013 \ Projeleriexcelworkbook\excelworkbook** klasöründe, **ExcelWorkbook_TemporaryKey. pfx** sertifika dosyasını kopyalayın ve *publishfolder* **\Application Files \ klasörüne yapıştırın.\_** _Mostrecentpublishedversion_ klasörü.

2. Visual Studio komut istemi ' ni açın ve ardından dizinleri **C:\publish\Application Files\ExcelWorkbook**\__Mostrecentpublishedversion_ klasörüne değiştirin (örneğin, **c:\publish\Application Files\ExcelWorkbook_1_0_0 _4**).

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

5. *ExcelWorkbook. VSTO* dosyasını **C:\publish\Application Files\excelworkbook**\__mostrecentversionnumber_ dizinine kopyalayın.

## <a name="SharePoint"></a>Bir çözümün belgesini SharePoint çalıştıran bir sunucuya koyma (yalnızca belge düzeyinde özelleştirmeler)
 Belge düzeyinde özelleştirmenizi SharePoint kullanarak son kullanıcılara yayımlayabilirsiniz. Kullanıcılar SharePoint sitesine gidip belgeyi açtığında, çalışma zamanı çözümü paylaşılan ağ klasöründen kullanıcının yerel bilgisayarına otomatik olarak yükler. Çözüm yerel olarak yüklendikten sonra, belge başka bir yere (örneğin, masaüstüne) kopyalansa bile özelleştirme işlevini yerine getirmeye devam eder.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Belgeyi SharePoint çalıştıran bir sunucuya koymak için

1. Çözüm belgesini SharePoint sitesindeki bir belge kitaplığına ekleyin.

2. Aşağıdaki yaklaşımlardan biri için adımları uygulayın:

    - SharePoint çalıştıran sunucuyu, tüm bilgisayarlarda Word veya Excel'deki Güven Merkezi'ne eklemek için Office Yapılandırma Aracı'nı kullanın.

         Bkz. [Office 2010 'de güvenlik ilkeleri ve ayarları](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Her kullanıcının aşağıdaki adımları uygulamasını sağlayın.

        1. Yerel bilgisayarda Word veya Excel ' i açın, **Dosya** sekmesini seçin ve ardından **Seçenekler** düğmesini seçin.

        2. **Güven Merkezi** Iletişim kutusunda **güvenilir konumlar** düğmesini seçin.

        3. **Ağımdaki Güvenilen konumlara Izin ver (önerilmez)** onay kutusunu seçin ve ardından **Yeni Konum Ekle** düğmesini seçin.

        4. **Yol** kutusuna, karşıya yüklediğiniz belgeyi içeren SharePoint belge kitaplığının URL 'sini girin (örneğin, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             Default *. aspx* veya *AllItems. aspx*gibi varsayılan Web sayfasının adını eklemeyin.

        5. **Bu konumun alt klasörlerinde da güvenilir** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

             Kullanıcılar belgeyi SharePoint sitesinden açtığında, belge açılır ve özelleştirme yüklenir. Kullanıcılar belgeyi kendi masaüstlerine kopyalayabilir. Belgedeki özellikler belgenin ağ konumuna işaret ettiğinden, özelleştirme çalışmaya devam edecektir.

## <a name="Custom"></a>Özel bir yükleyici oluşturma
 Çözümü yayımladığınızda sizin için oluşturulan Kurulum programını kullanmak yerine Office çözümünüz için özel bir yükleyici oluşturabilirsiniz. Örneğin, yüklemeyi başlatmak için bir oturum açma komut dosyası kullanabilir veya bir toplu iş dosyası kullanarak çözümü Kullanıcı etkileşimi olmadan yükleyebilirsiniz. Bu senaryolar en çok, önkoşullar son kullanıcı bilgisayarlarında zaten yüklü olduğunda işe yarar.

 Özel yükleme işleminizin bir parçası olarak, varsayılan olarak aşağıdaki konumda yüklü olan Office çözümleri (*VSTOInstaller. exe*) için yükleyici aracını çağırın:

 *%CommonProgramFiles%\Microsoft Shared\vsto\10.0\vstoınstaller.exe*

 Araç bu konumda değilse, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\vsto Runtime Setup\v4\InstallerPath** veya **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** kayıt defteri ' ni kullanabilirsiniz. Bu aracın yolunu bulmak için gereken anahtar.

 *VSTOinstaller. exe*ile birlikte aşağıdaki parametreleri kullanabilirsiniz.

| Parametre | Tanım |
|------------------| - |
| /Install veya /I | Çözümü yükler. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir evrensel adlandırma kuralı (UNC) dosya paylaşımında bir yol belirtebilirsiniz. Yerel bir yol (*C:\folder\\publishfolder*), göreli bir yol (*Publish\\* ) veya tam bir konum ( *\\\SunucuAdı \ sunucu \ KlasörAdı* veya http://<em>ServerName/KlasörAdı</em>) belirtebilirsiniz. |
| /Uninstall veya /U | Çözümü kaldırır. Bu seçeneğin ardından bir dağıtım bildiriminin konumunu vermelisiniz. Yerel bilgisayarda bir UNC dosya paylaşımında bir yol belirtebilirsiniz. Yerel bir yol (*C:\folder\\publishfolder*), göreli bir yol (*Publish\\* ) veya tam bir konum ( *\\\SunucuAdı \ sunucu \ KlasörAdı* veya http://<em>ServerName/KlasörAdı</em>) belirtebilirsiniz. |
| /Silent veya /S | Kullanıcıdan bir şey girmesini istemeden veya ileti görüntülemeden yükler veya kaldırır. Güven istemi gerekiyorsa, özelleştirme yüklenmez veya güncellenmez. |
| /Help or /? | Yardım bilgilerini görüntüler. |

 *VSTOinstaller. exe dosyasını*çalıştırdığınızda aşağıdaki hata kodları görünebilir.

|Hata Kodu|Tanım|
|----------------|----------------|
|0|Çözüm başarıyla yüklendi ya da kaldırıldı veya VSTOInstaller Yardımı görüntülendi.|
|-100|Bir veya daha fazla komut satırı seçeneği geçerli değil veya birden çok kez ayarlanmış. Daha fazla bilgi için "vstoinstaller/?" girin veya bkz. [bir ClickOnce Office çözümü için özel yükleyici oluşturma](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Bir veya daha fazla komut satırı seçeneği geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-200|Dağıtım bildirimi URI 'SI geçerli değil. Daha fazla bilgi için "vstoinstaller /?" girin.|
|-201|Dağıtım bildirimi geçerli olmadığından çözüm yüklenemedi. Bkz. [Office çözümleri Için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Uygulama bildiriminin Office Visual Studio Araçları bölümü geçerli olmadığından çözüm yüklenemedi. Bkz. [Office çözümleri Için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).|
|-203|Yükleme hatası oluştuğundan çözüm yüklenemedi. Dağıtım bildiriminin URI'sini veya ağ dosya konumunu denetleyin ve sonra yeniden deneyin.|
|-300|Güvenlik özel durumu oluştuğundan çözüm yüklenemedi. Bkz. [güvenli Office çözümleri](../vsto/securing-office-solutions.md).|
|-400|Çözüm yüklenemedi.|
|-401|Çözüm kaldırılamadı.|
|-500|Çözüm yüklenemediğinden ya da kaldırılamadığından veya dağıtım bildirimi indirilemediğinden işlem iptal edildi.|

## <a name="Update"></a>Güncelleştirme yayımlama
 Bir çözümü güncelleştirmek için, **projeyi Proje Tasarımcısı** veya **Yayımla Sihirbazı**' nı kullanarak yeniden yayımlayın ve sonra güncelleştirilmiş çözümü yükleme konumuna kopyalayın. Dosyaları yükleme konumuna kopyalarken, önceki dosyaların üzerine yazdığınızdan emin olun.

 Çözümün bir güncelleştirmeyi bir sonraki sefer denetlemesi, yeni sürümü otomatik olarak bulup yükler.

## <a name="Location"></a>Bir çözümün yükleme konumunu değiştirme
 Bir çözüm yayımlandıktan sonra yükleme yolunu ekleyebilir veya değiştirebilirsiniz. Yükleme yolunu değiştirmek istemenizin nedeni şunlardan biri veya daha fazlası olabilir:

- Kurulum programı, henüz yükleme yolu bilinmezken derlenmiştir.

- Çözüm dosyaları farklı bir konuma kopyalanmıştır.

- Yükleme dosyalarını barındıran sunucu yeni bir ada veya konuma sahiptir.

  Bir çözümün yükleme yolunu değiştirmek için kurulum programını güncelleştirmelisiniz; daha sonra da kullanıcıların bunu çalıştırması gerekir. Belge düzeyinde özelleştirmeler için, kullanıcıların ayrıca belgelerindeki bir özelliği de yeni konuma işaret edecek şekilde güncelleştirmeleri gerekir.

> [!NOTE]
> Kullanıcılardan belge özelliklerini güncelleştirmesini istemek istemiyorsanız, kullanıcılardan güncelleştirilmiş belgeyi yükleme konumundan almasını isteyebilirsiniz.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Kurulum programındaki yükleme konumunu değiştirmek için

1. Bir **komut istemi** penceresi açın ve sonra dizinleri yükleme klasörüyle değiştirin.

2. Kurulum programını çalıştırın ve yeni yükleme yolunu bir dize olarak alan `/url` parametresini ekleyin.

    Aşağıdaki örnekte, Fabrikam web sitesindeki bir konumun yükleme yolunun nasıl değiştirileceği gösterilmektedir; ancak siz bu URL'yi istediğiniz yol ile değiştirebilirsiniz:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Bir ileti ekrana gelir ve yürütülebilir öğenin imzasının geçersiz kılınacağını belirtirse, çözümü imzalamak için kullanılan sertifika artık geçerli değil ve yayımcısı bilinmiyor demektir. Sonuç olarak, kullanıcıların, çözümü yüklemeden önce çözümün kaynağına güvendiklerini onaylamaları gerekecektir.

   > [!NOTE]
   > URL 'nin geçerli değerini göstermek için `setup.exe /url`çalıştırın.

   Belge düzeyi özelleştirmeleri için, kullanıcılar belgeyi açmalı ve sonra _AssemblyLocation özelliğini güncelleştirmelidir. Aşağıdaki adımlarda kullanıcıların bu görevi nasıl yerine getirecekleri açıklanmaktadır.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Bir belgede _AssemblyLocation özelliğini güncelleştirmek için

1. **Dosya** sekmesinde, aşağıdaki çizimin gösterdiği **bilgi**' yi seçin.

     ![Excel 'de bilgi sekmesi](../vsto/media/vsto-infotab.png "Excel 'de bilgi sekmesi")

2. **Özellikler** listesinde, aşağıdaki çizimin gösterdiği **Gelişmiş Özellikler**' i seçin.

     ![Excel 'de gelişmiş özellikler.](../vsto/media/vsto-advanceddocumentproperties.png "Excel 'de gelişmiş özellikler.")

3. **Özellikler** listesindeki **özel** sekmesinde, aşağıdaki çizimde gösterildiği gibi, _AssemblyLocation ' ı seçin.

     ![AssemblyLocation özelliği.](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation özelliği.")

     **Değer** kutusu, dağıtım bildirimi tanımlayıcısını içerir.

4. Tanımlayıcıdan önce, belgenin tam yolunu girin ve ardından bir çubuk, *yol*|*tanımlayıcı* biçiminde (örneğin, *File://ServerName/FolderName/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Bu tanımlayıcıyı biçimlendirme hakkında daha fazla bilgi için bkz. [özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md).

5. **Tamam** düğmesini seçin ve ardından belgeyi kaydedin ve kapatın.

6. Çözümü belirtilen konuma yüklemek için, kurulum programını /url parametresi olmadan çalıştırın.

## <a name="Roll"></a>Bir çözümü önceki bir sürüme geri alma
 Bir çözümü geri aldığınızda, kullanıcıları bu çözümün önceki bir sürümüne geri döndürmüş olursunuz.

#### <a name="to-roll-back-a-solution"></a>Bir çözümü geri almak için

1. Çözümün yükleme konumunu açın.

2. Üst düzey yayımlama klasöründe, dağıtım bildirimini ( *. VSTO* dosyası) silin.

3. Geri almak istediğiniz sürüme ait alt klasörü bulun.

4. O alt klasördeki dağıtım bildirimini üst düzey publish klasörüne kopyalayın.

     Örneğin, **OutlookAddIn1** adlı bir çözümü 1.0.0.1 sürümüne 1.0.0.0 sürümüne geri almak için **OutlookAddIn1. VSTO** dosyasını **Outlookaddın1_1_0_0_0** klasöründen kopyalayın. Zaten orada olan **OutlookAddIn1_1_0_0_1** için sürüme özgü dağıtım bildiriminin üzerine yazarak dosyayı en üst düzey yayınlama klasörüne yapıştırın.

     Aşağıdaki resimde, bu örnekteki publish (yayımlama) klasörü yapısı gösterilmektedir.

     ![Klasör yapısını Yayımla](../vsto/media/publishfolderstructure.png "Klasör yapısını Yayımla")

     Kullanıcının uygulamayı ya da özelleştirilmiş belgeyi bir sonraki açışında, dağıtım bildirimindeki değişiklik algılanır. Office çözümünün önceki sürümü ClickOnce önbelleğinden çalışır.

> [!NOTE]
> Yerel veriler çözümün sadece bir önceki sürümü için kaydedilir. İki sürümü geri alırsanız yerel veriler korunmaz. Yerel veriler hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak verilere erişme](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümlerini yayımlama](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Nasıl yapılır: ClickOnce kullanarak bir Office çözümünü yayımlama](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Nasıl yapılır: ClickOnce Office çözümü yüklemesi](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Nasıl yapılır: ClickOnce kullanarak belge düzeyi Office çözümünü SharePoint sunucusuna yayımlama](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [ClickOnce Office çözümü için özel bir yükleyici oluşturma](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)