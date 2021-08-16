---
title: Windows Installer kullanarak Office çözümünü dağıtma
description: Windows Installer oluşturmak için Visual Studio kullanarak, son kullanıcının bilgisayarında yönetici erişimi gerektiren bir Office çözümü dağıtabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6d14564e2e3552bde0844bac02db6682def2d0ad95a3eb125b6d709ce34dd10e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366347"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Windows Installer kullanarak Office çözümünü dağıtma

kullanarak Office çözümünüz için Windows Installer oluşturma hakkında bilgi edinin [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

bir Windows Installer oluşturmak için Visual Studio kullanarak, son kullanıcının bilgisayarında yönetici erişimi gerektiren bir Office çözümü dağıtabilirsiniz. Örneğin, bir bilgisayarın tüm kullanıcıları için bir çözümü yalnızca bir kez yüklemek üzere bu tür bir dosyayı kullanabilirsiniz. ayrıca, ClickOnce kullanarak bir Office çözümü dağıtabilirsiniz, ancak bu çözümün bilgisayarın her kullanıcısı için ayrı olarak yüklenmesi gerekir.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-topic"></a>Bu konuda

- [VSTO eklentisi örneklerini indirin](#Download)

- [InstallShield Limited Edition 'ı al](#Obtain)

- [Çözüme nasıl güven verilileceğine karar verme](#ApplySecurity)

- [Kurulum projesi oluşturma](#Create)

- [Proje çıkışını ekleyin](#Add)

- [Dağıtım ve uygulama bildirimlerini ekleme](#AddD)

- [Bağımlı bileşenleri önkoşul olarak yapılandırma](#Configure)

- [Kullanıcının bilgisayarında çözümü nereye dağıtmak istediğinizi belirtin](#Location)

- [VSTO eklentisini yapılandırma](#ConfigureRegistry)

- [Belge düzeyi özelleştirmesi yapılandırma](#ConfigureDocument)

- [Kurulum projesi oluşturma](#Build)

ClickOnce kullanarak Office çözümünün nasıl dağıtılacağı hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

kullanarak bir Windows Installer dosyası oluşturma hakkında daha fazla bilgi için [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , bkz. [Windows Installer kullanarak Office çözümü için Visual Studio 2010 araçlarını dağıtma](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10)).

## <a name="download-samples"></a><a name="Download"></a>Örnekleri indirme
Bu konu, aşağıdaki indirilebilir örneklere başvurur.

|Örnek<br /><br />|Açıklama<br /><br />|
|----------|---------------|
|[ExcelAddIn](https://code.msdn.microsoft.com/VSTO-Deploy-an-Office-fbcc09ad)<br /><br />|Office 32 bit veya 64 bit sürümünü çalıştıran bir bilgisayara yükleyebileceğiniz bir Excel VSTO eklentisi.<br /><br />|
|[EX](https://code.msdn.microsoft.com/VSTO-Deploy-a-Customization-f70fae33)<br /><br />|Office 32 bit veya 64 bit sürümünü çalıştıran bir bilgisayara yükleyebileceğiniz Excel belge düzeyi özelleştirmesi.<br /><br />|

## <a name="decide-how-to-grant-trust-to-the-solution"></a><a name="ApplySecurity"></a>Çözüme nasıl güven verilileceğine karar verme
Bir çözümün kullanıcı bilgisayarlarında çalışması için, aşağıdaki yollarla güven sağlamanız gerekir, aksi durumda kullanıcılar çözümü yüklerken bir güven istemine yanıt vermelidir.

- Bilinen ve güvenilen bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Daha fazla bilgi için bkz. [uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin](../vsto/granting-trust-to-office-solutions.md#Signing).

- Çözümü, kullanıcının bilgisayarındaki program files dizinine yükler.

> [!NOTE]
> Belge düzeyi özelleştirmeleri için belge konumunun da güvenilir olması gerekir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="get-installshield-limited-edition"></a><a name="Obtain"></a>InstallShield Limited Edition 'ı al

Visual Studio yüklediyseniz ücretsiz olan ınstallshield Limited Edition 'ı (işle) kullanarak bir Windows Installer dosyası oluşturabilirsiniz. işle, Visual Studio önceki sürümlerinin sunulacağı kurulum ve dağıtım için proje şablonlarının işlevselliğini değiştirir.

### <a name="to-get-installshield-limited-edition"></a>InstallShield Limited Edition 'ı almak için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

   **yeni Project** iletişim kutusu açılır.

2. şablonlar bölmesinde, **diğer Project türleri**' ni genişletin ve ardından **kurulum ve dağıtım** şablonu ' nu seçin.

3. **Kurulum ve dağıtım** için proje türleri listesinde **InstallShield Limited Edition 'ı etkinleştir**' i seçin ve **Tamam** düğmesini seçin.

   InstallShield Limited Edition 'ın nasıl alınacağı hakkında bilgi sağlayan bir sayfa görüntülenir.

4. Bu sayfada, **Web sitesini indir bağlantısına gidin** .

5. InstallShield Limited Edition için indirme sayfasında, gerekli bilgileri uygun alanlara girin ve **Şimdi İndir** bağlantısını seçin.

   ürünü indirdikten, yükledikten ve etkinleştirdikten sonra, **ınstallshield Limited Edition Project** şablonu Visual Studio görüntülenir.

## <a name="create-a-setup-project"></a><a name="Create"></a>Kurulum projesi oluşturma

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dağıtmak istediğiniz Office projeyi açın.

   bu konuyla ilişkili VSTO eklenti örnekleri, **exceladdın** adlı bir proje içerir. Belge düzeyi özelleştirme örnekleri, **ExcelWorkbook** adlı bir proje içerir. bu konu, bu iki adlardan birini kullanarak çözümünüzdeki Office projesine başvuracaktır.

2. menü çubuğunda **dosya**  >  **ekle**  >  **yeni Project**' yi seçin.

   **yeni Project ekle** iletişim kutusu açılır.

3. şablonlar bölmesinde, **diğer Project türleri**' ni genişletin ve ardından **kurulum ve dağıtım** şablonu ' nu seçin.

4. **kurulum ve dağıtım** için proje türleri listesinde **ınstallshield Limited Edition Project** seçin, projeyi adlandırın ve **tamam** düğmesini seçin.

   Oluşturduğunuz InstallShield Kurulum projesi çözümünüzde görüntülenir.

   Bu konunun örnekleri, **OfficeAddInSetup** adlı bir kurulum projesi içerir. Bu konu, çözümünüzde aynı adı kullanarak kurulum projesine başvuracaktır.

## <a name="add-the-project-output"></a><a name="Add"></a>Proje çıkışını ekleyin

**officeaddınsetup** projesini, Office projenizin çıkışını içerecek şekilde yapılandırırsınız. VSTO eklenti projeleri için proje çıktısı yalnızca çözüm derlemesidir. Belge düzeyi özelleştirme projeleri için proje çıktısı yalnızca çözüm derlemesini değil belgenin kendisini de içerir.

### <a name="to-add-the-project-output"></a>Proje çıktısını eklemek için

1. **Çözüm Gezgini**, **officeaddınsetup** proje düğümünü genişletin ve ardından aşağıdaki çizimin gösterdiği **Project yardımcısı** dosyasını seçin.

   ![Project Çözüm Gezgini yardımcı dosyası](../vsto/media/installshield-projectassistant.png "Project Çözüm Gezgini'de Yardımcı Dosya")

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  .

3. **Project yardımcısı** sayfasının en altında, aşağıdaki çizimin gösterdiği **uygulama dosyaları** düğmesini seçin.

   ![Uygulama dosyaları düğmesi.](../vsto/media/installshield-applicationfiles.png "Uygulama Dosyaları düğmesi.")

4. **uygulama dosyaları** sayfasında **Project çıktıları ekle** düğmesini seçin.

5. **Visual Studio çıkış seçicisi** iletişim kutusunda, **birincil çıkış** onay kutusunu seçin ve ardından **tamam** düğmesini seçin.

## <a name="add-the-deployment-and-application-manifests"></a><a name="AddD"></a>Dağıtım ve uygulama bildirimlerini ekleme

1. **Uygulama dosyaları** sayfasında, **Dosya Ekle** düğmesini seçin.

2. **Aç** Iletişim kutusunda **ExcelAddIn** projesinin çıkış dizinine gidin.

   Genellikle, çıkış dizini, seçtiğiniz yapı yapılandırmasına bağlı olarak, proje kök dizininin **bin\release** alt klasörüdür.

3. Çıktı dizininde, **ExcelAddIn. VSTO** ve **ExcelAddIn.dll. manifest** dosyalarını ve sonra **Aç** düğmesini seçin.

   Aşağıdaki çizimde gösterildiği gibi, **uygulama dosyaları** sayfası artık proje çıktı dosyasını, dağıtım bildirimini ve uygulama bildirimini içerir.

   ![Kurulum projenizin çıktı dosyaları.](../vsto/media/installshield-outputfiles.png "Kurulum projenizin çıkış dosyaları.")

## <a name="configure-the-dependent-components-as-prerequisites"></a><a name="Configure"></a>Bağımlı bileşenleri önkoşul olarak yapılandırma

Kurulum uygulamanızda, yalnızca aşağıdaki bileşenleri değil, çözümünüzün çalışması için gerekli tüm diğer bileşenleri de dahil etmeniz gerekir.

- Office çözümünüzün hedeflediği .NET Framework sürümü.

- Office çalışma zamanına yönelik Microsoft Visual Studio 2010 araçları.

### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>önkoşul olarak .NET Framework 4 veya .NET Framework 4,5 ekleyin

1. **Çözüm Gezgini**, **OfficeAddInSetup** proje düğümünü genişletin, **uygulama verilerini belirt** düğümünü genişletin ve ardından aşağıdaki çizimin gösterdiği **yeniden dağıtılabilir** dosyasını seçin.

   ![Çözüm Gezgini içindeki yeniden dağıtılabilir dosyası](../vsto/media/installshield-redistributablesfile.png "Çözüm Gezgini'daki Redistributables dosyası")

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  .

   **Yeniden dağıtılabilir** sayfası açılır.

3. yeniden dağıtılabilir bileşenler listesinde, çözümünüzün hedeflediği .NET Framework sürümü için uygun onay kutusunu seçin.

   örneğin, çözümünüz [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ' i hedefliyorsa, **Microsoft .NET Framework 4,5 tam** onay kutusunu seçin. Bir önkoşul olarak bileşen ekleyebilmeniz için önce InstallShield 'un gerektirdiği yeniden dağıtılabilir bileşeni yüklemek isteyip istemediğinizi soran bir iletişim kutusu görünür. Bu iletişim kutusu görüntülenmezse, bileşen bilgisayarınızda zaten bulunur.

4. Bu iletişim kutusu görüntülenirse **Hayır** düğmesini seçin.

### <a name="add-the-visual-studio-2010-tools-for-office-runtime"></a><a name="AddToolsForOffice"></a>Office çalışma zamanı için Visual Studio 2010 araçlarını ekleyin

**yeniden dağıtılabilir** sayfası, **Microsoft VSTO 2010 çalışma zamanı** adında bir öğe içerir, ancak çalışma zamanının eski bir sürümüne başvurur. Bu nedenle, en son sürüme başvuran bir yapılandırma dosyası el ile oluşturabilirsiniz. Daha sonra bu dosyayı **yeniden dağıtılabilir** sayfasında görünen diğer tüm öğelerin yapılandırma dosyalarıyla aynı dizine koymanız gerekir.

#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Office çalışma zamanına yönelik Visual Studio 2010 araçlarını bir önkoşul olarak eklemek için

1. Not Defteri açın ve sonra aşağıdaki XML 'i bir metin dosyasına yapıştırın.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <SetupPrereq>
   <conditions>
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>
   </conditions>
   <files>
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>
   </files>
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">
   </execute>
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>

   </SetupPrereq>
   ```

2. Visual Studio bir GUID oluşturun. **Araçlar** menüsünde **GUID oluştur**' u seçin.

3. **GUID Oluşturucu** programında, **kayıt defteri biçimi** seçenek düğmesini seçin, **Kopyala** düğmesini seçin ve ardından **Çıkış** düğmesini seçin.

4. Not Defteri ' de, guıd **'nizin** yerine, guid 'sini yapıştırarak yazın.

   Dosyanızın **&lt; Özellikler &gt;** öğesi aşağıdakilere benzer.

   ```xml
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>
   ```

5. Not Defteri menü çubuğunda **dosya**  >  **kaydet**' i seçin.

6. **Farklı kaydet** Iletişim kutusunda **Masaüstü** klasörünüze gidin.

7. **Farklı kaydet türü** listesinde tüm dosyalar ' ı **(&#42;. &#42;)** seçin.

8. **dosya adı** kutusunda, **Office Runtime. prq için Visual Studio 2010 araçlar** girin ve **kaydet** düğmesini seçin.

   > [!NOTE]
   > Bu dosyayı önkoşul dosyası olarak tanımlamak için dosya adının sonuna **. prq** eklediğinizden emin olun.

9. Not Defteri’ni kapatın.

10. **masaüstü** klasörünüzden, *Office Runtime. prq dosyası için Visual Studio 2010 araçlarını* bilgisayarınızdaki aşağıdaki dizinlerden birine kopyalayın.

   32 bit işletim sistemleri için: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites \\*

   64 bit işletim sistemleri için: *% ProgramFiles (x86)% \ 2013LE \ Setupönkoşullarını \\*

11. InstallShield projesinin **yeniden dağıtılabilir** sayfasında, aşağıdaki çizimde gösterildiği gibi yeniden dağıtılabilir bileşenlerin listesini yenilemek için **Yenile** düğmesini seçin.

   ![Yenile düğmesi.](../vsto/media/installshield-refreshbutton.png "Yenile düğmesi.")

12. yeniden dağıtılabilir bileşenler listesinde, **Office Runtime için Visual Studio 2010 araçlar** onay kutusunu seçin.

   Yeniden dağıtılabilir bileşeni yüklemek isteyip istemediğiniz soran bir iletişim kutusu görünebilir. Bu iletişim kutusu görüntülenmezse, bu konunun [kullanıcının bilgisayarında çözümü dağıtmak istediğiniz yeri belirtin](#Location) ..

13. Bu iletişim kutusu görüntülenirse **Hayır** düğmesini seçin.

## <a name="specify-where-to-install-the-solution-on-the-users-computer"></a><a name="Location"></a>Kullanıcının bilgisayarında çözümün nereye yükleneceğini belirtin

1. **Çözüm Gezgini**, **OfficeAddInSetup** düğümünü genişletin, **kurulumunuzu düzenleyin** düğümünü genişletin ve ardından **genel bilgi** dosyasını seçin.

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  .

3. Özellikler listesinde, **InstallDir** özelliğinin yanındaki git **düğmesini seçin** .

4. **INSTALLDIR ayarla** iletişim kutusunda, çözümü yüklemek istediğiniz kullanıcının bilgisayarında bir klasör seçin.

   > [!NOTE]
   > Ayrıca, listedeki herhangi bir klasörün kısayol menüsünü açarak **ıNSTALLDIR ayarla** iletişim kutusunda alt dizinler de oluşturabilirsiniz.

## <a name="configure-a-vsto-add-in"></a><a name="ConfigureRegistry"></a>VSTO eklentisini yapılandırma

VSTO eklentisinin bilgisayarın tüm kullanıcıları (bilgisayar başına) için mi yoksa yalnızca yüklemeyi gerçekleştiren kullanıcı için mi (kullanıcı başına) için mi yükleneceğini belirtebilirsiniz.

Bilgisayar başına yüklemeleri desteklemek istiyorsanız, iki ayrı yükleyici oluşturun. yükleyicileri Office sürüme (32 bit ve 64 bit) veya kullanıcının çalıştırdığı Windows sürümüne (32-bit ve 64-bit) göre ayırabilirsiniz.

kullanıcı başına yüklemeler Office veya Windows sürümden bağımsız olarak yalnızca bir yükleyici gerektirir.

> [!NOTE]
> bu bölüm yalnızca bir VSTO eklentisi dağıtıyorsanız geçerlidir. Belge düzeyinde bir özelleştirme dağıtıyorsanız, [belge düzeyi özelleştirmesi yapılandırma](#ConfigureDocument) bölümüne hemen gidebilirsiniz.

### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Kullanıcı başına veya bilgisayar başına yüklemeleri desteklemek isteyip istemediğinizi belirtmek için

1. **Çözüm Gezgini**, **OfficeAddInSetup** proje düğümünü genişletin, **kurulumunuzu düzenleyin** düğümünü genişletin ve ardından **genel bilgi** dosyasını seçin.

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  .

   Kurulum projesinin özellikleri görüntülenir.

3. **ALLUSERS** özelliği listesinde, bu çözümün bilgisayarın tüm kullanıcıları veya yalnızca çözümü yükleyen kullanıcı için yüklenmesini isteyip istemediğinizi belirtin.

   geçerli kullanıcı için VSTO eklentisini yüklemek için **allusers = "" (kullanıcı başına yükleme)** seçeneğini belirleyin. bilgisayarın tüm kullanıcıları için VSTO eklentisini yüklemek için **allusers = 1 (makine başına yükleme)** öğesini seçin.

   bir sonraki yordamda, Office uygulamasının VSTO eklentisini bulmasını ve yüklemesini sağlamak için kayıt defteri anahtarları oluşturacaksınız. [VSTO eklentileri için kayıt defteri girdilerine](../vsto/registry-entries-for-vsto-add-ins.md)bakın.

### <a name="to-create-registry-keys"></a>Kayıt defteri anahtarları oluşturmak için

1. **Çözüm Gezgini** **Project yardımcısı** düğümünü seçin.

   Menü çubuğunda açık **görüntüle**' yi seçin  >  .

2. **Project yardımcısı** sayfasının en altında, aşağıdaki çizimin gösterdiği **uygulama kayıt defteri** düğmesini seçin.

   ![Uygulama kayıt defteri düğmesi.](../vsto/media/installshield-applicationregistry.gif "Uygulama Kayıt Defteri düğmesi.")

   **Uygulama kayıt defteri** sayfası görüntülenir.

3. **Uygulamanızın yükleneceği kayıt defteri verilerini yapılandırmak istiyor musunuz?** altında **Evet** seçenek düğmesini seçin.

4. **Hedef bilgisayarın kayıt defteri görünümü** listesinde, oluşturmak istediğiniz yükleyicinin türünü sağlayan anahtar hiyerarşisini ekleyin.

   Bu bölümde yapılandırdığınız yol, Kullanıcı başına yükleyici veya bilgisayar başına bir yükleyici oluşturup oluşturamayacağını gösterir.

   **Kullanıcı başına yükleyici**

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**

   **Office sürümüne dayalı bilgisayar başına yükleyiciler**

| Office sürümü<br /><br /> | InstallShield yapılandırma yolu<br /><br /> |
|----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Windows sürümüne dayalı bilgisayar başına yükleyiciler**

| Windows sürümü<br /><br /> | InstallShield yapılandırma yolu<br /><br /> |
|-----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]
   > 64 bit Windows yükleyicisi, kullanıcıların 64-bit Windows çalıştıran bir bilgisayarda 32-bit ve 64 bit Office sürümlerini çalıştırmasına olanak sağladığından, iki kayıt defteri yolu gerektirir.

   > [!NOTE]
   > en iyi uygulama olarak, VSTO eklentisinin adını şirketinizin adıyla başlatın. bu kural, anahtarın benzersiz olma olasılığını artırır ve başka bir tedarikçiden bir VSTO eklentisi ile çakışma olasılığını azaltır. Aynı ada sahip Eklentiler, örneğin, her birinin kayıt anahtarlarının üzerine yazabilir. Bu yaklaşım, anahtarın benzersiz olacağını ve olası ad çakışmalarını azaltabileceğinizi garanti edemez.

5. Anahtarların hiyerarşisini oluşturduktan sonra **SampleCompany. ExcelAddIn** anahtarı için kısayol menüsünü açın, **Yeni**' yi ve ardından **dize değeri**' ni seçin.

   Yeni dize değeri, **hedef bilgisayarın kayıt defteri verileri** listesinde görünür. Dize değerinin adı, yeniden adlandırabilmeniz için vurgulanır.

6. Değeri **Açıklama** olarak yeniden adlandırın.

7. Aşağıdaki değerleri oluşturmak için bu işlemi tekrarlayın.

|Değer Türü<br /><br />|Name<br /><br />|
|--------------|--------|
|Dize değeri<br /><br />|**FriendlyName**<br /><br />|
|DWORD değeri<br /><br />|**LoadBehavior**<br /><br />|
|Dize değeri<br /><br />|**Bildirim**<br /><br />|

8. **Açıklama** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   **Verileri Düzenle** iletişim kutusu görüntülenir.

9. **değer verileri** metin kutusuna **Excel Demo eklentisi** girin ve **tamam** düğmesini seçin.

   bu açıklama kullanıcı Office uygulamayı açtığında görüntülenir, **seçenekler** iletişim kutusunu açar ve ardından **eklentiler** bölmesinde VSTO eklentisini seçer.

10. **FriendlyName** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   **Verileri Düzenle** iletişim kutusu görüntülenir.

11. **değer verileri** metin kutusuna **Excel Demo eklentisi** girin ve **tamam** düğmesini seçin.

   bu dize, Office uygulamasındaki **COM eklentileri** iletişim kutusunda görünür. varsayılan olarak, dizenin değeri VSTO eklenti kimliğidir.

12. **LoadBehavior** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   **Verileri Düzenle** iletişim kutusu görüntülenir.

13. **Değer verisi** metin kutusunda **3** girin ve **Tamam** düğmesini seçin.

   3 değeri, uygulama başladığında VSTO eklentisini yükler. LoadBehavior değerleri hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

14. **Bildirim** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   Verileri **Düzenle** iletişim kutusu görüntülenir.

15. Değer **verileri metin** kutusuna **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal** yazın ve tamam **düğmesini** seçin.

   Office Runtime için Visual Studio 2010 Araçları dağıtım bildirimini bulmak için bu yolu kullanır. Bu **yolun [INSTALLDIR]** bölümü, InstallShield kurulum projenizin **Genel** Bilgiler özellik **sayfasındaki INSTALLDIR** özelliğine eşli bir makrodur. Bu özellik, eklentiyi yüklemek için hedef bilgisayarda VSTO belirtir. **|vstolocal** soneki, çözüm yükleme klasörünün yükleme klasöründen yüklendiğinden emin ClickOnce sağlar.

> [!IMPORTANT]
> Outlook için VSTO Eklentisinde özel bir form bölgesi Outlook. Daha fazla bilgi için [bkz. Form bölgelerine Outlook girdileri.](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries)

## <a name="configure-a-document-level-customization"></a><a name="ConfigureDocument"></a>Belge düzeyinde özelleştirme yapılandırma

Bu bölüm yalnızca belge düzeyinde özelleştirme dağıtıyorsanız geçerlidir. VSTO Eklentisini dağıtıyorsanız Kurulum projesini derleme [bölümüne hemen gidebilirsiniz.](#Build)

Belge düzeyinde özelleştirmeler kayıt defteri anahtarlarını kullanmaz. Bunun yerine, özel belge özellikleri dağıtım bildiriminin konumunu içerir.

Özel özellikleri değiştirmek için belge düzeyi özelleştirmeyi belgeden kaldıran, uygun özellikleri değiştiren ve ardından özelleştirmeyi belgeye yeniden takan bir program oluşturun. Ardından programı çalıştıran özel bir eylem oluşturun ve bu eylemi kurulum projenize ekleyin.

### <a name="to-create-a-program-that-modifies-document-properties"></a>Belge özelliklerini değiştiren bir program oluşturmak için

1. Menü çubuğunda Dosya Yeni **Ekle'yi**  >  **seçin ve**  >  **Project.**

   Yeni **Veri Project** iletişim kutusu görüntülenir.

2. Şablonlar bölmesinde, kullanmak istediğiniz dilin düğümünün altında, Windows **seçin.**

3. Uygulamanın proje türleri listesinde **Windows** Konsol Uygulaması **şablonunu** seçin.

4. Projeye **SetExcelDocumentProperties adını ve** ardından Tamam **düğmesini** seçin.

5. Bu **Çözüm Gezgini** Tüm Dosyaları  Göster düğmesini seçin, **SetExcelDocumentProperties** proje düğümü için kısayol menüsünü açın ve Ardından Başvuru Ekle'yi **seçin.**

6. Başvuru **Yöneticisi iletişim** kutusunda **Uzantılar sekmesini** seçin, ardından aşağıdaki derlemelerin yanındaki onay kutusunu ve ardından Tamam **düğmesini** seçin.

   - Microsoft.VisualStudio.Tools.Applications.Runtime

   - Microsoft.VisualStudio.Tools.Applications.ServerDocument

7. Bu **Çözüm Gezgini** **Program.cs** dosyasını (C# uygulamaları için) veya **Module1.vb** dosyasını (Visual Basic seçin.

8. Menü çubuğunda Aç'ı   >  **seçin.**

9. Dosyanın tamamının içeriğini aşağıdaki kodla değiştirin.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb" id="Snippet1":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs" id="Snippet1":::

10. Projeyi derle.

### <a name="to-add-a-custom-action-that-runs-your-program"></a>Programınızı çalıştıran özel bir eylem eklemek için

1. Bu **Çözüm Gezgini** **OfficeAddInSetup** proje düğümünü genişletin ve ardından **aşağıdaki çizimde** gösterildiği Project Yardımcı dosyasını seçin.

   ![Project Çözüm Gezgini'de Yardımcı Dosya](../vsto/media/installshield-projectassistant.png "Project Çözüm Gezgini'de Yardımcı Dosya")

2. Menü çubuğunda Aç'ı   >  **seçin.**

3. **Project yardımcı sayfasının** alt kısmında, aşağıdaki **çizimde gösterildiği** Uygulama Dosyaları düğmesini seçin.

   ![Uygulama Dosyaları düğmesi.](../vsto/media/installshield-applicationfiles.png "Uygulama Dosyaları düğmesi.")

4. Uygulama **Dosyaları sayfasında,** Uygulama Dosyaları **ekle Project düğmesini** seçin.

   Visual Studio **Seçici iletişim** kutusu görüntülenir.

5. **SetExcelDocumentProperties düğümünün** altında Birincil Çıkış **onay** kutusunu ve ardından Tamam **düğmesini** seçin.

6. Bu **Çözüm Gezgini** **OfficeAddInSetup** düğümünün altında Kurulum Gereksinimlerini ve **Eylemlerini** Tanımla düğümünü genişletin ve ardından Özel **Eylemler klasörünü** seçin.

7. Menü çubuğunda Aç'ı   >  **seçin.**

   Ekranın yan tarafındaki bölmede olayların listesi görüntülenir.

   > [!NOTE]
   > Bu listede yalnızca birkaç olay InstallShield Limited Edition'da kullanılabilir. Bu yordamda Kurulum Tamamlandıktan Sonra Başarı iletişim kutusunu **kullanarak programı çalıştırabilirsiniz.**

8. Olay listesinde, Yükleme Sırasında Özel **Eylemler'in** altında Kurulum  Başarıyı Tamamlandıktan Sonra iletişim kutusu olayı için kısayol menüsünü açın ve Yeni **EXE'yi seçin.**

   Kurulumun Tamamlandıktan Sonra Başarı iletişim kutusunun altında **NewCustomAction1** adlı **özel bir eylem** görüntülenir. Özel eylemin bir dizi özelliği, olayların yanındaki bölmede görünür.

   > [!IMPORTANT]
   > Kurulum **Tamamlandıktan Sonra İki Başarılı iletişim** kutusu olayları olay listesinde görünür. Yükleme Sırasında Özel Eylemler düğümü altında görüntülenen **Kurulumun BaşarıYı** Tamamlandıktan Sonra iletişim kutusunun **örneğini seçtiğinizden emin** olun.

9. Kaynak Konumu özelliğinin **listesinde Ürünle** **Birlikte Yüklendi'yi seçin.**

10. Dosya **Adı özelliğinin** yanındaki Gözat **düğmesini** seçin.

11. Hedef **Dosyaya Gözat iletişim** kutusunda **SetExcelDocumentProperties.Primary.output** dosyasına göz atarak Aç **düğmesini** seçin.

    Bu dosyanın konumu, kurulum projesinin **INSTALLDIR** özelliği için belirttiğiniz klasöre bağlıdır. Örneğin, bu özelliği **[PersonalFolder]DemoWorkbookApp** adlı bir klasöre ayarsanız, **[ProgramFilesFolder]\DemoWorkbookApp** dizinine göz atarak **SetExcelDocumentProperties.Primary.output** dosyasını bulabilirsiniz.

    Sonraki birkaç adımda belgenin çözüm kimliğini alır ve ardından bu kimliği konsol uygulamasına parametre olarak iletirsiniz. Ayrıca belgenin konumunu, dağıtım bildirimini ve belge derlemesini de geçeceksiniz.

12. **ExcelWorkbook** projesinin kısayol menüsünü açın ve ardından işletim sisteminize **bağlı olarak Windows Gezgini'nde** Klasör **Aç** veya Dosya Gezgini Aç'ı seçin.

    Çözümlerinizi içeren klasör açılır.

13. Çözümle ilgili proje dosyasını Not Defteri. Diğer Visual Basic için dosyanın adı *ExcelWorkbook.vbproj'dır.* C# projeleri için dosyanın adı *ExcelWorkbook.csproj'dır.*

14. Proje dosyasında **&lt; SolutionID &gt;** öğesini bulun, değerini Pano'ya kopyalayın ve ardından bu öğeyi Not Defteri.

    Bu değeri konsol uygulamasına parametre olarak iletirsiniz.

15. **NewCustomAction1'in** özellikler sayfasında Komut Satırı **özelliğini** aşağıdaki metin satırına ayarlayın.

   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"
   ```

16. Çözüm **Kimliğiniz'i** Panoya kopyalanan çözüm kimliğiyle değiştirin.

   > [!IMPORTANT]
   > Yükleyicinizi test etmek için bu özel eylemin çalıştır olduğu konsol uygulamasının [INSTALLDIR] dizininde belgelere erişe olduğunu doğrulayın. Kullanıcının bilgisayarına bağlı bazı dizinler yönetim erişimi (örneğin, Program Dosyaları dizini) gerektirir. Çözümlerinizi yönetim erişimi gerektiren bir dizine dağıtıyorsanız, *yükleyiciyi* dağıtmadan öncesetup.exedosyasının Özellikler  iletişim kutusunu açmalı,  Uyumluluk sekmesini ve ardından Bu programı yönetici olarak çalıştır onay kutusunu seçmeniz gerekir.  Kullanıcıların kurulum programını yönetim izinleri ile çalıştırmalarını istemiyorsanız, [INSTALLDIR] özelliğini kullanıcının zaten erişimi olan bir dizine **(Örneğin Belgeler** dizini) ayarlayın. Daha fazla bilgi için bu [konunun Kullanıcının bilgisayarına](#Location) Çözümü Yüklemek istediğiniz Yeri Belirtin bölümüne bakın.

## <a name="build-the-setup-project"></a><a name="Build"></a>Kurulum projesini oluşturma

1. Bu **Çözüm Gezgini** Yayın için **Hazırla düğümünü** genişletin ve ardından Sürümler **dosyasını** seçin.

2. Menü çubuğunda Aç'ı   >  **seçin.**

   **Derlemeler** gezgini, oluşturmak istediğiniz yayın türünü seçesiniz diye bir yan bölmede açılır.

3. Derlemeler **gezgininde** **SingleImage klasörünü** seçin.

4. Derlemeler gezgininin yanındaki **bölmede** Derlemeler **sekmesiniSetup.exe** seçin.

5. Uygulama **Setup.exe** sayfasında, **InstallShield Önkoşulları Konumu** listesinden **Web'den İndir'i seçin.**

6. Menü çubuğunda Derleme ve **oluşturma'Yapılandırma Yöneticisi.**  >  

7. Etkin çözüm yapılandırma listesinde **SingleImage'ı seçin.** 

8. Project **bağlamlar** tablosunda **OfficeAddInSetup** projesinin Yapılandırma sütununda **SingleImage**'ı ve ardından Kapat **düğmesini** seçin. 

9. Menü çubuğunda Derleme   >  **OfficeAddInSetup seçeneğini belirleyin.**

   Derleme tamamlandıktan sonra **OfficeAddInSetup** projesinin *setup.exe* dosyasını şu konumda bulun: <em>OfficeAddInSetupProjectRoot</em>**\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1 \\**

## <a name="see-also"></a>Ayrıca bkz.

- [Office için çözüm önkoşulları](/previous-versions/bb608617(v=vs.110))
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [VSTO Eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md)
- [Özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md)
- [Çözüme güven Office ver](../vsto/granting-trust-to-office-solutions.md)
- [Belgelere güven izni ver](../vsto/granting-trust-to-documents.md)
- [Visual Studio Office Installer'ı kullanarak Office için Windows 2010 Araçları dağıtma](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))