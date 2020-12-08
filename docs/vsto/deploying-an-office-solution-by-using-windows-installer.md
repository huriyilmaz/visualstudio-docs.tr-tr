---
title: Windows Installer kullanarak bir Office çözümünü dağıtma
description: Windows Installer oluşturmak için Visual Studio kullanarak, son kullanıcının bilgisayarında yönetici erişimi gerektiren bir Office çözümünü dağıtabileceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c001b3ce308c9e991cee747bdcab3ad646b226ab
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847123"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Windows Installer kullanarak bir Office çözümünü dağıtma

Kullanarak Office çözümünüz için Windows Installer oluşturma hakkında bilgi edinin [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

Windows Installer oluşturmak için Visual Studio 'yu kullanarak, son kullanıcının bilgisayarında yönetici erişimi gerektiren bir Office çözümünü dağıtabilirsiniz. Örneğin, bir bilgisayarın tüm kullanıcıları için bir çözümü yalnızca bir kez yüklemek üzere bu tür bir dosyayı kullanabilirsiniz. ClickOnce kullanarak bir Office çözümü de dağıtabilirsiniz, ancak bu çözümün bilgisayarın her kullanıcısı için ayrı olarak yüklenmesi gerekir.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-topic"></a>Bu konuda

- [VSTO eklenti örneklerini indirin](#Download)

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

ClickOnce kullanarak bir Office çözümünü dağıtma hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

Kullanarak bir Windows Installer dosyası oluşturma hakkında daha fazla bilgi için [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , bkz. [Windows Installer kullanarak Office Için Visual Studio 2010 araçlarını dağıtma](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10)).

## <a name="download-samples"></a><a name="Download"></a>Örnekleri indirme
Bu konu, aşağıdaki indirilebilir örneklere başvurur.

|Örnek<br /><br />|Açıklama<br /><br />|
|----------|---------------|
|[ExcelAddIn](https://code.msdn.microsoft.com/VSTO-Deploy-an-Office-fbcc09ad)<br /><br />|Office 'in 32-bit veya 64 bit sürümünü çalıştıran bir bilgisayara yükleyebileceğiniz bir Excel VSTO eklentisi.<br /><br />|
|[EX](https://code.msdn.microsoft.com/VSTO-Deploy-a-Customization-f70fae33)<br /><br />|Office 'in 32-bit veya 64 bit sürümünü çalıştıran bir bilgisayara yükleyebileceğiniz bir Excel belge düzeyi özelleştirmesi.<br /><br />|

## <a name="decide-how-to-grant-trust-to-the-solution"></a><a name="ApplySecurity"></a>Çözüme nasıl güven verilileceğine karar verme
Bir çözümün kullanıcı bilgisayarlarında çalışması için, aşağıdaki yollarla güven sağlamanız gerekir, aksi durumda kullanıcılar çözümü yüklerken bir güven istemine yanıt vermelidir.

- Bilinen ve güvenilen bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalayın. Daha fazla bilgi için bkz. [uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin](../vsto/granting-trust-to-office-solutions.md#Signing).

- Çözümü, kullanıcının bilgisayarındaki program files dizinine yükler.

> [!NOTE]
> Belge düzeyi özelleştirmeleri için belge konumunun da güvenilir olması gerekir. Daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="get-installshield-limited-edition"></a><a name="Obtain"></a>InstallShield Limited Edition 'ı al

Visual Studio 'Yu yükledikten sonra ücretsiz olan InstallShield Limited Edition 'ı (IŞLE) kullanarak bir Windows Installer dosyası oluşturabilirsiniz. IŞLE, Visual Studio 'nun önceki sürümlerinin sunduğu kurulum ve dağıtım için proje şablonlarının işlevselliğini değiştirir.

### <a name="to-get-installshield-limited-edition"></a>InstallShield Limited Edition 'ı almak için

1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

2. Şablonlar bölmesinde, **diğer proje türleri**' ni genişletin ve ardından **Kurulum ve dağıtım** şablonu ' nu seçin.

3. **Kurulum ve dağıtım** için proje türleri listesinde **InstallShield Limited Edition 'ı etkinleştir**' i seçin ve **Tamam** düğmesini seçin.

   InstallShield Limited Edition 'ın nasıl alınacağı hakkında bilgi sağlayan bir sayfa görüntülenir.

4. Bu sayfada, **Web sitesini indir bağlantısına gidin** .

5. InstallShield Limited Edition için indirme sayfasında, gerekli bilgileri uygun alanlara girin ve **Şimdi İndir** bağlantısını seçin.

   Ürünü indirdikten, yükledikten ve etkinleştirdikten sonra, Visual Studio 'da **InstallShield Limited Edition proje** şablonu görüntülenir.

## <a name="create-a-setup-project"></a><a name="Create"></a>Kurulum projesi oluşturma

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dağıtmak Istediğiniz Office projesini açın.

   Bu konuyla ilişkili VSTO eklenti örnekleri, **ExcelAddIn** adlı bir proje içerir. Belge düzeyi özelleştirme örnekleri, **ExcelWorkbook** adlı bir proje içerir. Bu konu, bu iki adlardan birini kullanarak çözümünüzdeki Office projesine başvuracaktır.

2. Menü çubuğunda **Dosya**  >  **Ekle**  >  **Yeni proje**' yi seçin.

   **Yeni Proje Ekle** iletişim kutusu açılır.

3. Şablonlar bölmesinde, **diğer proje türleri**' ni genişletin ve ardından **Kurulum ve dağıtım** şablonu ' nu seçin.

4. **Kurulum ve dağıtım** için proje türleri listesinde **InstallShield Limited Edition projesi**' ni seçin, projeyi adlandırın ve **Tamam** düğmesini seçin.

   Oluşturduğunuz InstallShield Kurulum projesi çözümünüzde görüntülenir.

   Bu konunun örnekleri, **OfficeAddInSetup** adlı bir kurulum projesi içerir. Bu konu, çözümünüzde aynı adı kullanarak kurulum projesine başvuracaktır.

## <a name="add-the-project-output"></a><a name="Add"></a>Proje çıkışını ekleyin

Office projenizin çıkışını dahil etmek için **OfficeAddInSetup** projesini yapılandırırsınız. VSTO eklenti projeleri için proje çıktısı yalnızca çözüm derlemesidir. Belge düzeyi özelleştirme projeleri için proje çıktısı yalnızca çözüm derlemesini değil belgenin kendisini de içerir.

### <a name="to-add-the-project-output"></a>Proje çıktısını eklemek için

1. **Çözüm Gezgini**, **OfficeAddInSetup** proje düğümünü genişletin ve ardından aşağıdaki çizimin gösterdiği **Proje Yardımcısı** dosyasını seçin.

   ![Çözüm Gezgini içindeki proje Yardımcısı dosyası](../vsto/media/installshield-projectassistant.png "Çözüm Gezgini içindeki proje Yardımcısı dosyası")

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

3. **Proje Yardımcısı** sayfasının en altında, aşağıdaki çizimin gösterdiği **uygulama dosyaları** düğmesini seçin.

   ![Uygulama dosyaları düğmesi.](../vsto/media/installshield-applicationfiles.png "Uygulama dosyaları düğmesi.")

4. **Uygulama dosyaları** sayfasında, **proje çıktıları Ekle** düğmesini seçin.

5. **Visual Studio çıktı Seçicisi** iletişim kutusunda, **birincil çıkış** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

## <a name="add-the-deployment-and-application-manifests"></a><a name="AddD"></a>Dağıtım ve uygulama bildirimlerini ekleme

1. **Uygulama dosyaları** sayfasında, **Dosya Ekle** düğmesini seçin.

2. **Aç** Iletişim kutusunda **ExcelAddIn** projesinin çıkış dizinine gidin.

   Genellikle, çıkış dizini, seçtiğiniz yapı yapılandırmasına bağlı olarak, proje kök dizininin **bin\release** alt klasörüdür.

3. Çıktı dizininde, **ExcelAddIn. VSTO** ve **ExcelAddIn.dll. manifest** dosyalarını ve sonra **Aç** düğmesini seçin.

   Aşağıdaki çizimde gösterildiği gibi, **uygulama dosyaları** sayfası artık proje çıktı dosyasını, dağıtım bildirimini ve uygulama bildirimini içerir.

   ![Kurulum projenizin çıktı dosyaları.](../vsto/media/installshield-outputfiles.png "Kurulum projenizin çıktı dosyaları.")

## <a name="configure-the-dependent-components-as-prerequisites"></a><a name="Configure"></a>Bağımlı bileşenleri önkoşul olarak yapılandırma

Kurulum uygulamanızda, yalnızca aşağıdaki bileşenleri değil, çözümünüzün çalışması için gerekli tüm diğer bileşenleri de dahil etmeniz gerekir.

- Office çözümünüzün hedeflediği .NET Framework sürümü.

- Office çalışma zamanı için Microsoft Visual Studio 2010 araçları.

### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Önkoşul olarak .NET Framework 4 veya .NET Framework 4,5 ekleyin

1. **Çözüm Gezgini**, **OfficeAddInSetup** proje düğümünü genişletin, **uygulama verilerini belirt** düğümünü genişletin ve ardından aşağıdaki çizimin gösterdiği **yeniden dağıtılabilir** dosyasını seçin.

   ![Çözüm Gezgini içindeki yeniden dağıtılabilir dosyası](../vsto/media/installshield-redistributablesfile.png "Çözüm Gezgini içindeki yeniden dağıtılabilir dosyası")

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

   **Yeniden dağıtılabilir** sayfası açılır.

3. Yeniden dağıtılabilir bileşenler listesinde, çözümünüzün hedeflediği .NET Framework sürümü için uygun onay kutusunu seçin.

   Örneğin, çözümünüz [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] öğesini hedefliyorsa, **Microsoft .NET Framework 4,5 Full** onay kutusunu seçin. Bir önkoşul olarak bileşen ekleyebilmeniz için önce InstallShield 'un gerektirdiği yeniden dağıtılabilir bileşeni yüklemek isteyip istemediğinizi soran bir iletişim kutusu görünür. Bu iletişim kutusu görüntülenmezse, bileşen bilgisayarınızda zaten bulunur.

4. Bu iletişim kutusu görüntülenirse **Hayır** düğmesini seçin.

### <a name="add-the-visual-studio-2010-tools-for-office-runtime"></a><a name="AddToolsForOffice"></a>Office çalışma zamanı için Visual Studio 2010 araçlarını ekleme

**Yeniden dağıtılabilir** sayfası, **Microsoft VSTO 2010 çalışma zamanı** adında bir öğe içerir, ancak çalışma zamanının eski bir sürümüne başvurur. Bu nedenle, en son sürüme başvuran bir yapılandırma dosyası el ile oluşturabilirsiniz. Daha sonra bu dosyayı **yeniden dağıtılabilir** sayfasında görünen diğer tüm öğelerin yapılandırma dosyalarıyla aynı dizine koymanız gerekir.

#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Office çalışma zamanı için Visual Studio 2010 araçlarını bir önkoşul olarak eklemek için

1. Not defteri 'ni açın ve sonra aşağıdaki XML 'i bir metin dosyasına yapıştırın.

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

2. Visual Studio 'da bir GUID oluşturun. **Araçlar** menüsünde **GUID oluştur**' u seçin.

3. **GUID Oluşturucu** programında, **kayıt defteri biçimi** seçenek düğmesini seçin, **Kopyala** düğmesini seçin ve ardından **Çıkış** düğmesini seçin.

4. Not defteri 'nde, GUID **'nizin** yerine bu metni yazın.

   Dosyanızın **&lt; Özellikler &gt;** öğesi aşağıdakilere benzer.

   ```xml
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>
   ```

5. Not defteri 'ndeki menü çubuğunda **Dosya**  >  **Kaydet**' i seçin.

6. **Farklı kaydet** Iletişim kutusunda **Masaüstü** klasörünüze gidin.

7. **Farklı kaydet türü** listesinde tüm dosyalar ' ı **(&#42;. &#42;)** seçin.

8. **Dosya adı** kutusuna **Office Runtime. prq için Visual Studio 2010 araçları**' nı girin ve **Kaydet** düğmesini seçin.

   > [!NOTE]
   > Bu dosyayı önkoşul dosyası olarak tanımlamak için dosya adının sonuna **. prq** eklediğinizden emin olun.

9. Not Defteri’ni kapatın.

10. **Masaüstü** klasörünüzden, *Office Runtime. prq dosyasını Visual Studio 2010 araçları* 'nı bilgisayarınızdaki aşağıdaki dizinlerden birine kopyalayın.

   32 bit işletim sistemleri için: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites \\*

   64 bit işletim sistemleri için: *% ProgramFiles (x86)% \ 2013LE \ Setupönkoşullarını \\*

11. InstallShield projesinin **yeniden dağıtılabilir** sayfasında, aşağıdaki çizimde gösterildiği gibi yeniden dağıtılabilir bileşenlerin listesini yenilemek için **Yenile** düğmesini seçin.

   ![Yenile düğmesi.](../vsto/media/installshield-refreshbutton.png "Yenile düğmesi.")

12. Yeniden dağıtılabilir bileşenler listesinde, **Office çalışma zamanı Için Visual Studio 2010 araçları** onay kutusunu seçin.

   Yeniden dağıtılabilir bileşeni yüklemek isteyip istemediğiniz soran bir iletişim kutusu görünebilir. Bu iletişim kutusu görüntülenmezse, bu konunun [kullanıcının bilgisayarında çözümü dağıtmak istediğiniz yeri belirtin](#Location) ..

13. Bu iletişim kutusu görüntülenirse **Hayır** düğmesini seçin.

## <a name="specify-where-to-install-the-solution-on-the-users-computer"></a><a name="Location"></a>Kullanıcının bilgisayarında çözümün nereye yükleneceğini belirtin

1. **Çözüm Gezgini**, **OfficeAddInSetup** düğümünü genişletin, **kurulumunuzu düzenleyin** düğümünü genişletin ve ardından **genel bilgi** dosyasını seçin.

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

3. Özellikler listesinde, **InstallDir** özelliğinin yanındaki git **düğmesini seçin** .

4. **INSTALLDIR ayarla** iletişim kutusunda, çözümü yüklemek istediğiniz kullanıcının bilgisayarında bir klasör seçin.

   > [!NOTE]
   > Ayrıca, listedeki herhangi bir klasörün kısayol menüsünü açarak **ıNSTALLDIR ayarla** iletişim kutusunda alt dizinler de oluşturabilirsiniz.

## <a name="configure-a-vsto-add-in"></a><a name="ConfigureRegistry"></a>VSTO eklentisini yapılandırma

VSTO eklentisinin bilgisayarın tüm kullanıcıları (bilgisayar başına) için mi yoksa yalnızca yüklemeyi gerçekleştiren kullanıcı için mi (Kullanıcı başına) için mi yükleneceğini belirtebilirsiniz.

Bilgisayar başına yüklemeleri desteklemek istiyorsanız, iki ayrı yükleyici oluşturun. Yükleyicileri Office sürümü (32-bit ve 64 bit) veya kullanıcının çalıştırdığı Windows sürümü (32-bit ve 64-bit) temelinde ayırabilirsiniz.

Kullanıcı başına Yüklemeler Office veya Windows sürümünden bağımsız olarak yalnızca bir yükleyici gerektirir.

> [!NOTE]
> Bu bölüm yalnızca VSTO eklentisini dağıtıyorsanız geçerlidir. Belge düzeyinde bir özelleştirme dağıtıyorsanız, [belge düzeyi özelleştirmesi yapılandırma](#ConfigureDocument) bölümüne hemen gidebilirsiniz.

### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Kullanıcı başına veya bilgisayar başına yüklemeleri desteklemek isteyip istemediğinizi belirtmek için

1. **Çözüm Gezgini**, **OfficeAddInSetup** proje düğümünü genişletin, **kurulumunuzu düzenleyin** düğümünü genişletin ve ardından **genel bilgi** dosyasını seçin.

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

   Kurulum projesinin özellikleri görüntülenir.

3. **ALLUSERS** özelliği listesinde, bu çözümün bilgisayarın tüm kullanıcıları veya yalnızca çözümü yükleyen kullanıcı için yüklenmesini isteyip istemediğinizi belirtin.

   Geçerli Kullanıcı için VSTO eklentisini yüklemek için **ALLUSERS = "" (Kullanıcı başına yükleme)** seçeneğini belirleyin. Bilgisayarın tüm kullanıcıları için VSTO eklentisini yüklemek için **ALLUSERS = 1 (makine başına yükleme)** öğesini seçin.

   Bir sonraki yordamda, Office uygulamasının VSTO eklentisini bulmasını ve yüklemesini sağlamak için kayıt defteri anahtarları oluşturacaksınız. Bkz. [VSTO eklentileri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-create-registry-keys"></a>Kayıt defteri anahtarları oluşturmak için

1. **Çözüm Gezgini**, **Proje Yardımcısı** düğümünü seçin.

   Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

2. **Proje Yardımcısı** sayfasının en altında, aşağıdaki çizimin gösterdiği **uygulama kayıt defteri** düğmesini seçin.

   ![Uygulama kayıt defteri düğmesi.](../vsto/media/installshield-applicationregistry.gif "Uygulama kayıt defteri düğmesi.")

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

   **Windows sürümünü temel alan bilgisayar başına yükleyiciler**

| Windows sürümü<br /><br /> | InstallShield yapılandırma yolu<br /><br /> |
|-----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]
   > 64 bit Windows için bir yükleyici, kullanıcıların 64 bit Windows çalıştıran bir bilgisayarda 32-bit ve 64 bit Office sürümlerini çalıştırmasına olanak sağladığından, iki kayıt defteri yolu gerektirir.

   > [!NOTE]
   > En iyi uygulama olarak, VSTO eklentisinin adını şirketinizin adıyla başlatın. Bu kural, anahtarın benzersiz olma olasılığını artırır ve başka bir tedarikçiden bir VSTO eklentisi ile çakışma olasılığını azaltır. Aynı ada sahip Eklentiler, örneğin, her birinin kayıt anahtarlarının üzerine yazabilir. Bu yaklaşım, anahtarın benzersiz olacağını ve olası ad çakışmalarını azaltabileceğinizi garanti edemez.

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

9. **Değer verisi** metin kutusunda **Excel Tanıtım eklentisi**' ni girin ve **Tamam** düğmesini seçin.

   Bu açıklama Kullanıcı Office uygulamasını açtığında görüntülenir, **Seçenekler** iletişim kutusunu açar ve ardından **Eklentiler** bölmesinde VSTO eklentisini seçer.

10. **FriendlyName** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   **Verileri Düzenle** iletişim kutusu görüntülenir.

11. **Değer verisi** metin kutusunda **Excel Tanıtım eklentisi**' ni girin ve **Tamam** düğmesini seçin.

   Bu dize, Office uygulamasındaki **com eklentileri** iletişim kutusunda görünür. Varsayılan olarak, dizenin değeri VSTO eklenti KIMLIĞIDIR.

12. **LoadBehavior** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   **Verileri Düzenle** iletişim kutusu görüntülenir.

13. **Değer verisi** metin kutusunda **3** girin ve **Tamam** düğmesini seçin.

   3 değeri, uygulama başladığında VSTO eklentisini yükler. LoadBehavior değerleri hakkında daha fazla bilgi için bkz. [VSTO eklentileri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

14. **Bildirim** değeri için kısayol menüsünü açın ve ardından **Değiştir**' i seçin.

   **Verileri Düzenle** iletişim kutusu görüntülenir.

15. **Değer verileri** metin kutusuna **File:///[INSTALLDİR] ExcelAddIn. VSTO | vstolocal** yazın ve **Tamam** düğmesini seçin.

   Office çalışma zamanı için Visual Studio 2010 araçları, dağıtım bildirimini bulmak için bu yolu kullanır. Bu yolun **[INSTALLDİR]** bölümü, InstallShield kurulum projenizin **genel bilgi** özelliği sayfasında **InstallDir** özelliğiyle eşleşen bir makrodur. Bu özellik, VSTO eklentisinin yükleneceği hedef bilgisayardaki konumu belirtir. **| Vstolocal** son eki, çözümünüzün ClickOnce önbelleğinden değil yükleme klasöründen yüklenmesini sağlar.

> [!IMPORTANT]
> Outlook için VSTO eklentisi içinde özel bir form bölgesi oluşturursanız, bölgeyi Outlook 'a kaydetmek için daha fazla kayıt defteri girişi oluşturmanız gerekir. Daha fazla bilgi için bkz. [Outlook form bölgeleri Için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).

## <a name="configure-a-document-level-customization"></a><a name="ConfigureDocument"></a>Belge düzeyi özelleştirmesi yapılandırma

Bu bölüm yalnızca belge düzeyinde bir özelleştirme dağıtıyorsanız geçerlidir. VSTO eklentisi dağıtıyorsanız, [Kurulum projesi oluştur](#Build) bölümüne hemen gidebilirsiniz.

Belge düzeyi özelleştirmeleri, kayıt defteri anahtarlarını kullanmaz. Bunun yerine, özel belge özellikleri dağıtım bildiriminin konumunu içerir.

Özel özellikleri değiştirmek için belgedeki belge düzeyi özelleştirmeyi kaldıran, uygun özellikleri değiştiren ve özelleştirmeyi belgeye yeniden iliştirdiği bir program oluşturursunuz. Ardından programı çalıştıran özel bir eylem oluşturur ve bu eylemi kurulum projenize eklersiniz.

### <a name="to-create-a-program-that-modifies-document-properties"></a>Belge özelliklerini değiştiren bir program oluşturmak için

1. Menü çubuğunda **Dosya**  >  **Ekle**  >  **Yeni proje**' yi seçin.

   **Yeni Proje Ekle** iletişim kutusu görüntülenir.

2. Şablonlar bölmesinde, kullanmak istediğiniz dilin düğümü altında **Windows** klasörünü seçin.

3. **Windows** için proje türleri listesinde **konsol uygulaması** şablonunu seçin.

4. Projeyi **SetExcelDocumentProperties** olarak adlandırın ve ardından **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesini seçin, **SetExcelDocumentProperties** proje düğümü Için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

6. **Başvuru Yöneticisi** iletişim kutusunda, **Uzantılar** sekmesini seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutusunu işaretleyin ve ardından **Tamam** düğmesini seçin.

   - Microsoft. VisualStudio. Tools. Applications. Runtime

   - Microsoft. VisualStudio. Tools. Applications. ServerDocument

7. **Çözüm Gezgini**' de, **program.cs** dosyasını (C# uygulamaları için) veya **Module1. vb** dosyasını (Visual Basic uygulamalar için) seçin.

8. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

9. Tüm dosyanın içeriğini aşağıdaki kodla değiştirin.

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]

10. Projeyi derleyin.

### <a name="to-add-a-custom-action-that-runs-your-program"></a>Programınızı çalıştıran özel bir eylem eklemek için

1. **Çözüm Gezgini**, **OfficeAddInSetup** proje düğümünü genişletin ve ardından aşağıdaki çizimin gösterdiği **Proje Yardımcısı** dosyasını seçin.

   ![Çözüm Gezgini içindeki proje Yardımcısı dosyası](../vsto/media/installshield-projectassistant.png "Çözüm Gezgini içindeki proje Yardımcısı dosyası")

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

3. **Proje Yardımcısı** sayfasının en altında, aşağıdaki çizimin gösterdiği **uygulama dosyaları** düğmesini seçin.

   ![Uygulama dosyaları düğmesi.](../vsto/media/installshield-applicationfiles.png "Uygulama dosyaları düğmesi.")

4. **Uygulama dosyaları** sayfasında, **proje çıktıları Ekle** düğmesini seçin.

   **Visual Studio çıktı Seçicisi** iletişim kutusu görüntülenir.

5. **SetExcelDocumentProperties** düğümü altında **birincil çıkış** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

6. **Çözüm Gezgini**, **OfficeAddInSetup** düğümü altında, **kurulum gereksinimlerini ve eylemleri tanımla** düğümünü genişletin ve ardından **özel eylemler** klasörünü seçin.

7. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

   Olay listesi, ekranın yanındaki bir bölmede görüntülenir.

   > [!NOTE]
   > Yalnızca bu listede görünen birkaç olay InstallShield Limited Edition 'da bulunabilir. Bu yordamda, **Kurulum tamamlandı başarı iletişim kutusu olayından sonra** programını kullanarak programı çalıştıracaksınız.

8. Olaylar listesinde, **yükleme sırasında özel eylemler** altında, **Kurulum tamamlandıktan sonra başarı iletişim kutusu** olayının kısayol menüsünü açın ve sonra **Yeni exe**' yi seçin.

   **NewCustomAction1** adlı özel bir eylem, **Kurulum tamamlandıktan sonra başarı Iletişim kutusu olayından sonra** görünür. Özel eylem için bir dizi özellik, olayların yanındaki bir bölmede görüntülenir.

   > [!IMPORTANT]
   > **Kurulum tamamlandıktan sonra başarı iletişim kutusu** olaylarının ikisi de olaylar listesinde görüntülenir. **Yükleme düğümü sırasında özel eylemler** altında görüntülenen kurulum tamamlandıktan **sonra başarı iletişim kutusu** olayının örneğini seçtiğinizden emin olun.

9. **Kaynak konumu** için listesinde, **ürünle birlikte yüklü**' ı seçin.

10. **Dosya adı** özelliğinin yanındaki **tarayıcı** düğmesini seçin.

11. **Hedef dosya Için araştır** Iletişim kutusunda **SetExcelDocumentProperties. PRIMARY. Output** dosyasına gidin ve **Aç** düğmesini seçin.

    Bu dosyanın konumu, Kurulum projesinin **InstallDir** özelliği için belirttiğiniz klasöre bağlıdır. Örneğin, bu özelliği **[Personfolder] DemoWorkbookApp** adlı bir klasöre ayarlarsanız, **[ProgramFilesFolder] \DemoWorkbookApp** öğesine göz atarak **SetExcelDocumentProperties. Primary. Output** dosyasını bulabilirsiniz.

    Sonraki birkaç adımda, belgenin çözüm KIMLIĞINI alır ve ardından bu KIMLIĞI konsol uygulamasına bir parametre olarak geçireceğiz. Ayrıca belgenin konumunu, dağıtım bildirimini ve belge derlemesini de geçireceğiz.

12. **ExcelWorkbook** projesinin kısayol menüsünü açın ve ardından **Windows Gezgini 'nde klasörü aç** ' ı seçin veya Işletim sisteminize bağlı olarak **Dosya Gezgini 'nde klasörü açın** .

    Çözümünüzü içeren klasör açılır.

13. Çözümünüzün proje dosyasını Not defteri 'nde açın. Visual Basic projeleri için dosyanın adı *ExcelWorkbook. vbproj* olur. C# projeleri için dosyanın adı *ExcelWorkbook. csproj* olur.

14. Proje dosyasında, **&lt; SolutionId &gt;** öğesini arayın, değerini panoya kopyalayın ve Not defteri 'ni kapatın.

    Bu değeri konsol uygulamasına parametre olarak geçirirsiniz.

15. **NewCustomAction1** öğesinin Özellikler sayfasında, **komut satırı** özelliğini aşağıdaki metin satırına ayarlayın.

   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"
   ```

16. **Çözüm kimliğinizi** , panoya KOPYALADıĞıNıZ çözüm kimliğiyle değiştirin.

   > [!IMPORTANT]
   > Bu özel eylemin çalıştırdığı konsol uygulamasının [ıNSTALLDIR] dizinindeki belgelere erişebileceğini doğrulamak için yükleyicinizi test edin. Kullanıcının bilgisayarındaki bazı dizinler, yönetim erişimi gerektirebilir (örneğin, Program Files dizini). Çözümünüzü yönetici erişimi gerektiren bir dizine dağıtıyorsanız, *setup.exe* dosyanın **Özellikler** Iletişim kutusunu açmanız, **Uyumluluk** sekmesini seçmeniz ve ardından yükleyiciyi dağıtmadan önce **Bu programı yönetici olarak çalıştır** onay kutusunu seçmeniz gerekir. Kullanıcıların Kurulum programını Yönetici izinleriyle çalıştırmasını istemiyorsanız, [ıNSTALLDIR] özelliğini kullanıcının zaten erişimi olan **Belgeler** dizini gibi bir dizine ayarlayın. Daha fazla bilgi için, bu konunun [kullanıcının bilgisayarında çözümü nereye yüklemek Istediğinizi belirtin](#Location) .

## <a name="build-the-setup-project"></a><a name="Build"></a>Kurulum projesi oluşturma

1. **Çözüm Gezgini**, **yayın için hazırla** düğümünü genişletin ve ardından **yayınlar** dosyasını seçin.

2. Menü çubuğunda açık **görüntüle**' yi seçin  >  **Open**.

   **Yapı** Gezgini, oluşturmak istediğiniz yayın türünü seçebilmeniz için yan bölmede açılır.

3. **Yapılar** Gezgininde **tekımage** klasörünü seçin.

4. **Yapılar** Gezgini ' nin yanındaki bölmede **Setup.exe** sekmesini seçin.

5. **Setup.exe** Özellik sayfasında, **InstallShield önkoşulları konum** listesinden **Web 'den indir**' i seçin.

6. Menü çubuğunda Configuration Manager **Oluştur**' u seçin  >  **Configuration Manager**.

7. **Etkin çözüm yapılandırması** listesinde **SingleImage** öğesini seçin.

8. **Proje bağlamları** tablosunda, **OfficeAddInSetup** projesinin **yapılandırma** sütununda **SingleImage**' i seçin ve sonra **Kapat** düğmesini seçin.

9. Menü çubuğunda **Build**  >  **Build OfficeAddInSetup** öğesini seçin.

   Derleme tamamlandıktan sonra, **OfficeAddInSetup** projesinin *setup.exe* dosyasını şu konumda bulabilirsiniz: <em>Officeaddınsetupprojectroot</em>**\Officeaddınsetup\express\singleımage\diskımages\disk1 \\**

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım için Office çözüm önkoşulları](/previous-versions/bb608617(v=vs.110))
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md)
- [Özel belge özelliklerine genel bakış](../vsto/custom-document-properties-overview.md)
- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [Belgelere güven verme](../vsto/granting-trust-to-documents.md)
- [Windows Installer kullanarak Office çözümü için Visual Studio 2010 araçları dağıtma](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))