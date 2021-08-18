---
title: Windows Yükleyicisi'Office bir Windows dağıtma
description: Visual Studio yükleyicisi oluşturmak için Windows kullanarak, son kullanıcının bilgisayarına yönetici erişimi Office bir Office çözümü dağıtabilirsiniz.
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
ms.openlocfilehash: fc9f2e41b317729234ec335c3d6733ebb0257f2f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130721"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Windows Yükleyicisi'Office bir Windows dağıtma

kullanarak Office Windows yükleyicisi oluşturma hakkında [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] bilgi.

Bir Visual Studio yükleyicisi oluşturmak Windows kullanarak, son kullanıcının bilgisayarına yönetici erişimi Office bir Office çözümü dağıtabilirsiniz. Örneğin, bir çözümü bir bilgisayarın tüm kullanıcıları için yalnızca bir kez yüklemek için böyle bir dosya kullanabilirsiniz. ClickOnce kullanarak Office bir çözüm de dağıtabilirsiniz, ancak bu çözümün bilgisayarın her kullanıcısı için ayrı olarak yüklenmiş olması gerekir.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-topic"></a>Bu konuda

- [Eklenti VSTO indirme](#Download)

- [InstallShield Limited Edition'ı alın](#Obtain)

- [Çözüme güven verme kararını verme](#ApplySecurity)

- [Kurulum projesi oluşturma](#Create)

- [Proje çıktısını ekleme](#Add)

- [Dağıtım ve uygulama bildirimlerini ekleme](#AddD)

- [Bağımlı bileşenleri önkoşul olarak yapılandırma](#Configure)

- [Çözümü kullanıcının bilgisayarına dağıtmak istediğiniz yeri belirtin](#Location)

- [Bir VSTO Eklentiyi Yapılandırma](#ConfigureRegistry)

- [Belge düzeyinde özelleştirme yapılandırma](#ConfigureDocument)

- [Kurulum projesini oluşturma](#Build)

ClickOnce kullanarak bir Office çözümü dağıtma hakkında daha fazla bilgi için bkz. ClickOnce kullanarak Office [çözümü dağıtma.](../vsto/deploying-an-office-solution-by-using-clickonce.md)

kullanarak bir Windows Yükleyicisi dosyası oluşturma hakkında bilgi için bkz. Windows Installer kullanarak Office çözümü için [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] [Visual Studio 2010 Araçları dağıtma.](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))

## <a name="download-samples"></a><a name="Download"></a>Örnekleri indirme
Bu konu aşağıdaki indirilebilir örneklere başvurur.

|Örnek<br /><br />|Açıklama<br /><br />|
|----------|---------------|
|[ExcelAddIn](https://code.msdn.microsoft.com/VSTO-Deploy-an-Office-fbcc09ad)<br /><br />|Uygulamanın Excel VSTO 32 bit veya 64 bit sürümünün çalıştır olduğu bir bilgisayara yük kurabilirsiniz Office.<br /><br />|
|[ExcelWorkbook](https://code.msdn.microsoft.com/VSTO-Deploy-a-Customization-f70fae33)<br /><br />|Bir Excel 32 bit veya 64 bit sürümü çalışan bir bilgisayara yükleyebilirsiniz belge düzeyi özelleştirme Office.<br /><br />|

## <a name="decide-how-to-grant-trust-to-the-solution"></a><a name="ApplySecurity"></a>Çözüme güven verme kararını verme
Bir çözümün kullanıcı bilgisayarlarında çalıştırılamadan önce, aşağıdaki yöntemlerden herhangi birini güven izni vermeli veya kullanıcılar çözümü yüklediğinde bir güven istemine yanıt ver ver çalışmalı.

- Bilinen ve güvenilen bir yayımcıyı tanımlayan bir sertifika kullanarak bildirimleri imzalar. Daha fazla bilgi için [bkz. Uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin.](../vsto/granting-trust-to-office-solutions.md#Signing)

- Çözümü kullanıcının bilgisayarına Program Files dizinine yükleyin.

> [!NOTE]
> Belge düzeyinde özelleştirmeler için belgenin konumunun da güvenilir olması gerekir. Daha fazla bilgi için [bkz. Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

## <a name="get-installshield-limited-edition"></a><a name="Obtain"></a>InstallShield Limited Edition'ı alın

InstallShield Limited Edition 'ı (ISLE) kullanarak bir Windows Yükleyicisi dosyası oluşturabilirsiniz. Bu dosyayı yüklemiş Visual Studio. ISLE, önceki sürümlerinin sunduğu kurulum ve dağıtım için proje şablonlarının Visual Studio değiştirir.

### <a name="to-get-installshield-limited-edition"></a>InstallShield Limited Edition'ı almak için

1. Menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >  

   Yeni **Project** iletişim kutusu açılır.

2. Şablonlar bölmesinde Diğer Project **Türleri'ni genişletin** ve ardından Kurulum ve Dağıtım **şablonunu** seçin.

3. Kurulum ve Dağıtım için proje türleri **listesinde,** **InstallShield Limited Edition'ı** Etkinleştir'i ve ardından Tamam **düğmesini** seçin.

   InstallShield Limited Edition'ın nasıl alınarak ilgili bilgi sağlayan bir sayfa görüntülenir.

4. Bu sayfada İndirme **web sitesine git bağlantısını** seçin.

5. InstallShield Limited Edition indirme sayfasında, uygun alanlara gerekli bilgileri girin ve ardından Şimdi İndir **bağlantısını** seçin.

   Ürünü indirdikten, yükledikten ve etkinleştirdikten sonra **InstallShield Limited Edition Project** şablonu Visual Studio.

## <a name="create-a-setup-project"></a><a name="Create"></a>Kurulum projesi oluşturma

1. içinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dağıtmak Office projesini açın.

   Bu VSTO ilişkili örneklerde **ExcelAddIn** adlı bir proje vardır. Belge düzeyi özelleştirme örnekleri **ExcelWorkbook** adlı bir proje içerir. Bu konu başlığında, Office bu adlardan birini kullanarak çözümünüzle ilgili projenize başvurabilirsiniz.

2. Menü çubuğunda Dosya Yeni **Ekle'yi**  >  **seçin ve**  >  **Project.**

   Yeni **Veri Project** iletişim kutusu açılır.

3. Şablonlar bölmesinde Diğer Project **Türleri'ni genişletin** ve ardından Kurulum ve Dağıtım **şablonunu** seçin.

4. Kurulum ve Dağıtım için proje **türleri** listesinde **YükleShield Limited Edition Project'ı** seçin, projeyi olarak kabul edin ve ardından Tamam **düğmesini** seçin.

   Oluşturduğunuz InstallShield kurulum projesi çözümünüzde görünür.

   Bu konunun örnekleri **OfficeAddInSetup** adlı bir kurulum projesi içerir. Bu konu, aynı adı kullanarak çözümünüzde kurulum projesine başvurur.

## <a name="add-the-project-output"></a><a name="Add"></a>Proje çıktısını ekleme

**OfficeAddInSetup projesini,** projenizin çıkışını içerecek Office yapılandırmış oluruz. Eklenti VSTO için proje çıkışı yalnızca çözüm derlemesi olur. Belge düzeyinde özelleştirme projeleri için proje çıkışı yalnızca çözüm derlemesini değil, aynı zamanda belgenin kendisini de içerir.

### <a name="to-add-the-project-output"></a>Proje çıktısını eklemek için

1. Bu **Çözüm Gezgini** **OfficeAddInSetup** proje düğümünü genişletin ve ardından **aşağıdaki çizimde** gösterildiği Project Yardımcı dosyasını seçin.

   ![Project Çözüm Gezgini'de Yardımcı Dosya](../vsto/media/installshield-projectassistant.png "Project Çözüm Gezgini'de Yardımcı Dosya")

2. Menü çubuğunda Aç'ı   >  **seçin.**

3. **Project yardımcı sayfasının** alt kısmında, aşağıdaki **çizimde gösterildiği** Uygulama Dosyaları düğmesini seçin.

   ![Uygulama Dosyaları düğmesi.](../vsto/media/installshield-applicationfiles.png "Uygulama Dosyaları düğmesi.")

4. Uygulama **Dosyaları sayfasında,** Uygulama Dosyaları **ekle Project düğmesini** seçin.

5. Çıkış **Visual Studio iletişim kutusunda** Birincil Çıkış onay **kutusunu** ve ardından Tamam **düğmesini** seçin.

## <a name="add-the-deployment-and-application-manifests"></a><a name="AddD"></a>Dağıtım ve uygulama bildirimlerini ekleme

1. Uygulama **Dosyaları sayfasında** Dosya Ekle **düğmesini** seçin.

2. Aç **iletişim** kutusunda **ExcelAddIn** projesinin çıkış dizinine gidin.

   Çıkış dizini genellikle, seçtiğiniz derleme yapılandırmasına bağlı olarak proje kök dizininin **bin\release** alt klasörüdür.

3. Çıkış dizininde **ExcelAddIn.vsto** ve **ExcelAddIn.dll.manifest** dosyalarını seçin ve ardından Aç **düğmesini** seçin.

   Uygulama **Dosyaları** sayfası artık aşağıdaki çizimde gösterildiği gibi proje çıkış dosyasını, dağıtım bildirimini ve uygulama bildirimini içerir.

   ![Kurulum projenizin çıkış dosyaları.](../vsto/media/installshield-outputfiles.png "Kurulum projenizin çıkış dosyaları.")

## <a name="configure-the-dependent-components-as-prerequisites"></a><a name="Configure"></a>Bağımlı bileşenleri önkoşul olarak yapılandırma

Kurulum uygulamanıza yalnızca aşağıdaki bileşenleri değil, aynı zamanda çözümünüz için gereken diğer bileşenleri de dahil edin.

- Office çözüm .NET Framework sürümü.

- Office Runtime için Microsoft Visual Studio 2010 Araçları.

### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Önkoşul olarak .NET Framework 4 veya .NET Framework 4.5'i ekleyin

1. Bu **Çözüm Gezgini** **OfficeAddInSetup** proje düğümünü genişletin,  Uygulama Verilerini Belirtin düğümünü genişletin ve ardından aşağıdaki çizimde gösterildiği **Gibi Yeniden** Dağıtılabilirler dosyasını seçin.

   ![Çözüm Gezgini'daki Redistributables dosyası](../vsto/media/installshield-redistributablesfile.png "Çözüm Gezgini'daki Redistributables dosyası")

2. Menü çubuğunda Aç'ı   >  **seçin.**

   **Yeniden Dağıtılabilirler sayfası** açılır.

3. Yeniden dağıtılabilir bileşenler listesinde çözümün hedeflene .NET Framework onay kutusunu seçin.

   Örneğin, çözümünüz hedefi ise, Microsoft .NET Framework [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] **4.5 Tam onay kutusunu** seçin. Bileşeni önkoşul olarak ekleymeden önce InstallShield'in gerektirdiği yeniden dağıtılabilir bileşeni yüklemek isteyip istemediklerini soran bir iletişim kutusu görünebilir. Bu iletişim kutusu görünmüyorsa bileşen bilgisayarınızda zaten var olur.

4. Bu iletişim kutusu görüntülenirse Hayır **düğmesini** seçin.

### <a name="add-the-visual-studio-2010-tools-for-office-runtime"></a><a name="AddToolsForOffice"></a>Office Runtime için Visual Studio 2010 Araçları'Office ekleme

**Redistributables** **sayfası, Microsoft VSTO 2010 Runtime** adlı bir öğe içerir, ancak çalışma zamanının eski bir sürümüne başvurur. Bu nedenle, en son sürüme başvuran bir yapılandırma dosyasını el ile oluşturabilirsiniz. Ardından bu dosyayı Yeniden Dağıtılabilir Öğeler sayfasında görünen diğer tüm öğeler için yapılandırma dosyalarıyla **aynı dizine koyabilirsiniz.**

#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Office için Visual Studio 2010 Araçları'Office önkoşul olarak eklemek için

1. Dosya Not Defteri açın ve aşağıdaki XML'yi bir metin dosyasına yapıştırın.

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

2. Bir GUID'i Visual Studio. Araçlar menüsünde **GUID** **oluştur'a tıklayın.**

3. GUID **oluşturucu programında** Kayıt Defteri Biçimi **seçeneği düğmesini,** Kopyala düğmesini ve **ardından** Çıkış **düğmesini** seçin.

4. Bu Not Defteri GUID'iniz **buraya gider metnini** yerine yapıştırarak değiştirin.

   Dosyanın properties öğesi aşağıdakine benzer. **&lt; &gt;**

   ```xml
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>
   ```

5. DosyaNın menü çubuğunda dosya **Not Defteri'yi**  >  **seçin.**

6. Farklı **Kaydet iletişim** kutusunda Masaüstü klasörünüze **gidin.**

7. Farklı kaydet **türü listesinde Tüm** Dosyalar **(&#42;.&#42;) seçin.**

8. Dosya adı **kutusuna Office** **Runtime.prq için Visual Studio 2010** Araçları yazın ve kaydet **düğmesini** seçin.

   > [!NOTE]
   > Bu dosyayı bir önkoşul dosyası olarak tanımlamak için dosya adının sonuna **.prq'yi** ekleyin.

9. Not Defteri’ni kapatın.

10. Desktop **klasörünüzdeki** *Visual Studio 2010 Tools for Office Runtime.prq* dosyasını bilgisayarınızda aşağıdaki dizinlerden birini kopyalayın.

   32 bit işletim sistemleri için: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites \\*

   64 bit işletim sistemleri için: *%ProgramFiles(x86)%\2013LE\SetupPrerequisites \\*

11. Aşağıdaki **çizimde gösterildiği gibi** InstallShield projesinin Yeniden  Dağıtılabilir sayfasında Yenile düğmesini seçerek yeniden dağıtılabilir bileşenler listesini yenileyin.

   ![Yenile düğmesi.](../vsto/media/installshield-refreshbutton.png "Yenile düğmesi.")

12. Yeniden dağıtılabilir bileşenler listesinde Visual Studio Çalışma Zamanı **için Araçlar** onay kutusunu Office seçin.

   Yeniden dağıtılabilir bileşeni yüklemek isteyip istemediklerini soran bir iletişim kutusu görünebilir. Bu iletişim kutusu görünmüyorsa, bu konunun Çözümü kullanıcının bilgisayarına dağıtmak istediğiniz yeri belirtin [bölümüne](#Location) atlayabilirsiniz.

13. Bu iletişim kutusu görüntülenirse Hayır **düğmesini** seçin.

## <a name="specify-where-to-install-the-solution-on-the-users-computer"></a><a name="Location"></a>Çözümün kullanıcının bilgisayarına nereye yüklln olduğunu belirtme

1. Bu **Çözüm Gezgini** **OfficeAddInSetup** düğümünü genişletin, Kurulum düğümünü düzenle'yi **genişletin** ve ardından Genel **Bilgi dosyasını** seçin.

2. Menü çubuğunda Aç'ı   >  **seçin.**

3. Özellikler listesinde **INSTALLDIR** **özelliğinin** yanındaki Gözat düğmesini seçin.

4. **INSTALLDIR Ayarla** iletişim kutusunda, çözümü yüklemek istediğiniz kullanıcının bilgisayarına bir klasör seçin.

   > [!NOTE]
   > Ayrıca, **INSTALLDIR** Ayarla iletişim kutusunda, listede herhangi bir klasörün kısayol menüsünü açarak alt dizinler oluşturabilirsiniz.

## <a name="configure-a-vsto-add-in"></a><a name="ConfigureRegistry"></a>Bir VSTO Eklentiyi Yapılandırma

VSTO Eklentinizin bilgisayarın tüm kullanıcıları (bilgisayar başına) için mi yoksa yalnızca yükleme yapan kullanıcı için mi (kullanıcı başına) yüklü olacağını belirtebilirsiniz.

Bilgisayar başına yüklemeleri desteklemek için iki ayrı yükleyici oluşturun. Yükleyicileri, Office sürümüne (32 bit ve 64 bit) veya kullanıcının çalıştırmış olduğu Windows sürümüne (32 bit ve 64 bit) göre bölüştersiniz.

Kullanıcı başına yüklemeler, her sürümden bağımsız olarak yalnızca Office Windows gerektirir.

> [!NOTE]
> Bu bölüm yalnızca bir eklenti VSTO geçerlidir. Belge düzeyinde özelleştirme dağıtıyorsanız, hemen Belge düzeyinde özelleştirme yapılandırma [bölümüne gidebilirsiniz.](#ConfigureDocument)

### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Kullanıcı başına veya bilgisayar başına yüklemeleri desteklemek isteyip istemediklerini belirtmek için

1. Bu **Çözüm Gezgini** **OfficeAddInSetup** proje düğümünü genişletin, Kurulumlarınızı Düzenle düğümünü **genişletin** ve ardından Genel Bilgi **dosyasını** seçin.

2. Menü çubuğunda Aç'ı   >  **seçin.**

   Kurulum projesinin özellikleri görüntülenir.

3. **AllUSERS özelliğinin** listesinde, bu çözümün bilgisayarın tüm kullanıcıları için mi yoksa yalnızca çözümü yük eden kullanıcı için mi yüklü olacağını belirtin.

   Geçerli kullanıcıya VSTO yüklemek için **ALLUSERS="" (Kullanıcı başına yükleme) 'yi seçin.** Bilgisayarın tüm VSTO için Uygulama Ekle'yi yüklemek için **ALLUSERS=1 (Makine başına yükleme) 'yi seçin**

   Sonraki yordamda, Office uygulamasının eklentiyi bulması ve yüklemesi için kayıt defteri VSTO oluşturabilirsiniz. Bkz. [Eklentilerini VSTO kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

### <a name="to-create-registry-keys"></a>Kayıt defteri anahtarları oluşturmak için

1. Bu **Çözüm Gezgini,** Project **Yardımcısı düğümünü** seçin.

   Menü çubuğunda Aç'ı   >  **seçin.**

2. **Project yardımcısı sayfasının en** altında, aşağıdaki **çizimde gösterildiği Application Registry** düğmesini seçin.

   ![Uygulama Kayıt Defteri düğmesi.](../vsto/media/installshield-applicationregistry.gif "Uygulama Kayıt Defteri düğmesi.")

   Uygulama **Kayıt Defteri** sayfası görüntülenir.

3. Uygulamanıza **yüklenecek kayıt defteri verilerini yapılandırmak istiyor musunuz?** altında Evet **seçeneği düğmesini** seçin.

4. Hedef **bilgisayarın Kayıt Defteri görünüm listesinde,** oluşturmak istediğiniz yükleyici türünü sağlayan anahtar hiyerarşisini ekleyin.

   Bu bölümde yapılandırılan yol, kullanıcı başına yükleyici veya bilgisayar başına yükleyici oluşturmanıza bağlıdır.

   **Kullanıcı başına yükleyici**

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**

   **Office sürümüne göre bilgisayar başına yükleyiciler**

| Office sürümü<br /><br /> | InstallShield Yapılandırma Yolu<br /><br /> |
|----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Yeni sürümü temel alan bilgisayar başına Windows yükleyiciler**

| Windows sürümü<br /><br /> | InstallShield Yapılandırma Yolu<br /><br /> |
|-----------------------------| - |
| 32 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64 bit<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]
   > 64 bit Windows için bir yükleyici, kullanıcıların 64 bitlik Windows'i çalıştıran bir bilgisayarda Office'nin 32 bit ve 64 bit sürümlerini çalıştırması mümkün olduğundan iki kayıt defteri yolu Windows.

   > [!NOTE]
   > En iyi uygulama olarak, şirket VSTO şirket adıyla Eklenti'yi başlatın. Bu kural, anahtarın benzersiz olma şansını artırır ve başka bir sağlayıcının eklentisinde VSTO çakışma ihtimalini azaltmaktadır. Örneğin, aynı adı alan eklentiler, birbirlerinin kayıt anahtarlarının üzerine yazarak üzerine yaz olabilir. Bu yaklaşım, anahtarın benzersiz olacağını garanti etmemektedir ancak olası ad çakışmalarını azaltan bir yaklaşımdır.

5. Anahtar hiyerarşisini oluşturduktan sonra **SampleCompany.ExcelAddIn** anahtarının kısayol menüsünü açın, Yeni 'yi ve ardından Dize Değeri'ni **seçin.** 

   Yeni dize değeri Hedef **bilgisayarın Kayıt defteri veri listesinde** görünür. Dize değerini yeniden adlandırmak için dize değerinin adı vurgulanır.

6. Değeri Açıklama olarak yeniden **adlandır.**

7. Aşağıdaki değerleri oluşturmak için bu işlemi tekrarlayın.

|Değer Türü<br /><br />|Name<br /><br />|
|--------------|--------|
|Dize Değeri<br /><br />|**Friendlyname**<br /><br />|
|DWORD Değeri<br /><br />|**Loadbehavior**<br /><br />|
|Dize Değeri<br /><br />|**Bildirim**<br /><br />|

8. Açıklama değerinin kısayol **menüsünü açın ve** Değiştir'i **seçin.**

   Verileri **Düzenle** iletişim kutusu görüntülenir.

9. Değer **verileri metin** kutusuna Excel **Demo Eklentisini girin** ve tamam **düğmesini** seçin.

   Bu açıklama, kullanıcı Office uygulamasını açtığında, Seçenekler  iletişim kutusunu açtığında görünür  ve ardından Eklentiler bölmesinde, VSTO Eklentiyi seçer.

10. **FriendlyName** değerinin kısayol menüsünü açın ve Değiştir'i **seçin.**

   Verileri **Düzenle** iletişim kutusu görüntülenir.

11. Değer **verileri metin** kutusuna Excel **Demo Eklentisini girin** ve tamam **düğmesini** seçin.

   Bu dize, **Office** uygulamasında COM Eklentileri iletişim kutusunda görünür. Varsayılan olarak, dizenin değeri VSTO kimliğidir.

12. **LoadBehavior değerinin kısayol menüsünü açın ve** Değiştir'i **seçin.**

   Verileri **Düzenle** iletişim kutusu görüntülenir.

13. Değer **verileri metin** kutusuna **3 girin** ve ardından Tamam **düğmesini** seçin.

   3 değeri, uygulama VSTO eklentiyi yükler. LoadBehavior değerleri hakkında daha fazla bilgi için bkz. VSTO [için kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

14. Bildirim değerinin kısayol menüsünü **açın ve** Değiştir'i **seçin.**

   Verileri **Düzenle** iletişim kutusu görüntülenir.

15. Değer **verileri metin** kutusuna **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal** yazın ve tamam **düğmesini** seçin.

   Office Runtime Visual Studio 2010 Araçları dağıtım bildirimini bulmak için bu yolu kullanır. Bu **yolun [INSTALLDIR]** bölümü, InstallShield kurulum projenizin **Genel** Bilgiler özellik **sayfasındaki INSTALLDIR** özelliğine eşli bir makrodur. Bu özellik, eklentiyi yüklemek için hedef bilgisayarda VSTO belirtir. **|vstolocal** soneki, çözüm yükleme klasöründen değil, ClickOnce sağlar.

> [!IMPORTANT]
> Outlook için VSTO Eklentisinde özel bir form bölgesi Outlook. Daha fazla bilgi için [bkz. Form bölgelerine Outlook girdileri.](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries)

## <a name="configure-a-document-level-customization"></a><a name="ConfigureDocument"></a>Belge düzeyinde özelleştirme yapılandırma

Bu bölüm yalnızca belge düzeyinde özelleştirme dağıtıyorsanız geçerlidir. Bir eklentiyi bir VSTO, Kurulum projesini derleme bölümüne hemen [gidebilirsiniz.](#Build)

Belge düzeyinde özelleştirmeler kayıt defteri anahtarlarını kullanmaz. Bunun yerine, özel belge özellikleri dağıtım bildiriminin konumunu içerir.

Özel özellikleri değiştirmek için belge düzeyi özelleştirmeyi belgeden kaldıran, uygun özellikleri değiştiren ve ardından özelleştirmeyi belgeye yeniden takan bir program oluşturun. Ardından programı çalıştıran özel bir eylem oluşturun ve bu eylemi kurulum projenize ekleyin.

### <a name="to-create-a-program-that-modifies-document-properties"></a>Belge özelliklerini değiştiren bir program oluşturmak için

1. Menü çubuğunda Dosya Yeni **Ekle'yi**  >  **seçin ve**  >  **Project.**

   Yeni **Veri Project** iletişim kutusu görüntülenir.

2. Şablonlar bölmesinde, kullanmak istediğiniz dilin düğümünün altında, Windows **seçin.**

3. Uygulama için proje türleri listesinde **Windows** Konsol Uygulaması **şablonunu** seçin.

4. Projeye **SetExcelDocumentProperties adını ve** ardından Tamam **düğmesini** seçin.

5. Bu **Çözüm Gezgini** Tüm Dosyaları  Göster düğmesini seçin, **SetExcelDocumentProperties** proje düğümü için kısayol menüsünü açın ve Ardından Başvuru Ekle'yi **seçin.**

6. Başvuru **Yöneticisi iletişim** kutusunda **Uzantılar sekmesini** seçin, ardından aşağıdaki derlemelerin yanındaki onay kutusunu ve ardından Tamam **düğmesini** seçin.

   - Microsoft.VisualStudio.Tools.Applications.Runtime

   - Microsoft.VisualStudio.Tools.Applications.ServerDocument

7. Bu **Çözüm Gezgini** **Program.cs** dosyasını (C# uygulamaları için) veya **Module1.vb** dosyasını (Visual Basic seçin.

8. Menü çubuğunda Aç'ı   >  seçin.

9. Dosyanın tamamının içeriğini aşağıdaki kodla değiştirin.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb" id="Snippet1":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs" id="Snippet1":::

10. Projeyi derle.

### <a name="to-add-a-custom-action-that-runs-your-program"></a>Programınızı çalıştıran özel bir eylem eklemek için

1. Bu **Çözüm Gezgini** **OfficeAddInSetup** proje düğümünü genişletin ve ardından **aşağıdaki çizimde** Project Yardımcı dosyasını seçin.

   ![Project Çözüm Gezgini'de Yardımcı Dosya](../vsto/media/installshield-projectassistant.png "Project Çözüm Gezgini'de Yardımcı Dosya")

2. Menü çubuğunda Aç'ı   >  seçin.

3. **Project yardımcı sayfasının alt** kısmında, aşağıdaki **çizimde gösterildiği** Uygulama Dosyaları düğmesini seçin.

   ![Uygulama Dosyaları düğmesi.](../vsto/media/installshield-applicationfiles.png "Uygulama Dosyaları düğmesi.")

4. Uygulama **Dosyaları sayfasında,** **Çıkışlar'Project ekle'yi** seçin.

   Visual Studio **Seçici iletişim** kutusu görüntülenir.

5. **SetExcelDocumentProperties düğümünün** altında Birincil Çıkış **onay** kutusunu ve ardından Tamam **düğmesini** seçin.

6. Bu **Çözüm Gezgini** **OfficeAddInSetup** düğümünün altında Kurulum Gereksinimlerini ve **Eylemlerini** Tanımla düğümünü genişletin ve ardından Özel **Eylemler klasörünü** seçin.

7. Menü çubuğunda Aç'ı   >  seçin.

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

2. Menü çubuğunda Aç'ı   >  seçin.

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
- [Windows Installer Visual Studio bir Office çözümü için Windows 2010 Araçları dağıtma](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))