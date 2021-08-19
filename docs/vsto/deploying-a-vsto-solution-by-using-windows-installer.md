---
title: Windows Yükleyicisi kullanarak VSTO Çözümü Dağıtma
description: Microsoft Visual Studio projesi kullanarak Office (VSTO) eklenti veya belge düzeyi çözümü Visual Studio Yükleyicisi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/18/2010
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
ms.openlocfilehash: d3145e17eb63417c13ffa9292ec6de50ae3ef88e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130760"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Windows Yükleyicisi kullanarak VSTO Çözümü Dağıtma

## <a name="summary"></a>Özet

Microsoft Visual Studio projesi kullanarak Office (VSTO) eklenti veya belge düzeyi çözümü Visual Studio Yükleyicisi öğrenin.

Wouter van Vugt, Kod Danışmanı

Ted Pattison, Ted Pattison Group

Bu makale, Microsoft tarafından özgün yazarların izniyle güncelleştirildi.

**Uygulama:** Office için Visual Studio Araçları, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Genel Bakış

Yeni bir VSTO geliştirebilir ve bir Windows Yükleyicisi paketi kullanarak çözümü dağıtabilirsiniz. Bu tartışma, basit bir eklenti Office adımlarını içerir.

## <a name="deployment-methods"></a>Dağıtım Yöntemleri

ClickOnce, Eklentileriniz ve çözümleriniz için kurulumlar oluşturmak için kolayca kullanılabilir. Ancak, makine düzeyi Eklentiler gibi yönetim ayrıcalıkları gerektiren Eklentileri yükleyemzebilir.

Yönetim ayrıcalıkları gerektiren eklentiler, Windows Yükleyicisi kullanılarak yüklenebilir, ancak kurulumu oluşturmak için daha fazla çaba gerektirir.

ClickOnce kullanarak bir VSTO çözümü dağıtma hakkında genel ClickOnce için bkz. Office [kullanarak bir ClickOnce.](deploying-an-office-solution-by-using-clickonce.md)

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Office çalışma zamanının hedefini VSTO dağıtma

ClickOnce ve Windows Yükleyici paketlerinin bir çözüm yüklerken aynı ilkel görevleri Office gerekir.

1. Kullanıcı bilgisayarına önkoşul bileşenlerini yükleyin.
2. Çözüm için belirli bileşenleri dağıtın.
3. Eklentiler için kayıt defteri girdileri oluşturun.
4. Çözümün yürütülmesine izin vermek için çözüme güvenin.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Hedef Bilgisayarda Gerekli Önkoşul Bileşenleri

Bu çözümleri çalıştırmak için bilgisayarda yüklü olması gereken yazılımların listesi VSTO:

- Microsoft Office 2010 veya daha yeni bir sürüm.
- Microsoft .NET Framework 4 veya daha yeni bir sürüm.
- Office Runtime için Microsoft Visual Studio 2010 Araçları.
  Çalışma zamanı, Eklentileri ve belge düzeyi çözümleri yöneten bir ortam sağlar. Çalışma Zamanının bir sürümü Microsoft Office ile birlikte sağlanır, ancak eklentiniz ile belirli bir sürümü yeniden dağıtın.
- Katıştırılmış Birlikte Çalışma Türleri Microsoft Office için Birincil Birlikte Çalışma derlemeleri.
- Projeler tarafından başvurulan herhangi bir yardımcı program derlemesi.

### <a name="specific-components-for-the-solution"></a>Çözüm için Belirli Bileşenler

Yükleyici paketinin kullanıcının bilgisayarına şu bileşenleri yüklemesi gerekir:

- Belge Microsoft Office çözümü ekleyebilirsiniz.
- Özelleştirme derlemesi ve gereken tüm derlemeler.
- Yapılandırma dosyaları gibi ek bileşenler.
- Uygulama bildirimi (.manifest).
- Dağıtım bildirimi (.vsto).

### <a name="registry-entries-for-add-ins"></a>Eklentiler için Kayıt Defteri Girdileri

Microsoft Office, eklentileri bulup yüklemek için kayıt defteri girdilerini kullanır. Bu kayıt defteri girdileri dağıtım işleminin bir parçası olarak oluşturulmalısınız. Bu kayıt defteri girdileri hakkında daha fazla bilgi için bkz. VSTO [için kayıt defteri girdileri.](registry-entries-for-vsto-add-ins.md)

Outlook Özel form bölgelerini görüntülemeye olanak sağlayan eklentiler, form bölgelerinin tanımlarına olanak sağlayan ek kayıt defteri girişleri gerektirir. Kayıt defteri girdileri hakkında daha fazla bilgi için bkz. Form [bölgelerine Outlook girdileri.](registry-entries-for-vsto-add-ins.md#OutlookEntries)

Belge düzeyi çözümler için kayıt defteri girişi gerekmez. Bunun yerine, belge içindeki özellikler özelleştirmeyi bulmak için kullanılır. Bu özellikler hakkında daha fazla bilgi için bkz. [Özel Belge Özelliklerine Genel Bakış.](custom-document-properties-overview.md)

### <a name="trusting-the-vsto-solution"></a>VSTO Çözümüne Güvenme

Özelleştirmenin çalışması için makine tarafından bir çözüme güvenin. Eklentiye, bildirimi bir sertifikayla imzalayarak, ekleme listesiyle bir güven ilişkisi oluşturarak veya bunu makinede güvenilir bir konuma yükleyerek güvenebilirsiniz.

İmzalama için sertifika alma hakkında daha fazla bilgi için bkz. [ClickOnce Deployment ve Authenticode](../deployment/clickonce-and-authenticode.md). Çözümlere güvenme hakkında daha fazla bilgi için, [bkz. Office Kullanarak Çözümlere Güvenme.](trusting-office-solutions-by-using-inclusion-lists.md) Windows Installer dosyanıza özel bir eylemle ekleme Windows ekleyebilirsiniz. Ekleme listesini etkinleştirme hakkında daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Dahil Etme Listesi Güvenliğini Yapılandırma.](how-to-configure-inclusion-list-security.md)

İki seçenek de kullanılmazsa, kullanıcıya çözüme güvenip güvenmeyeceklerine karar vermeleri için bir güven istemi görüntülenir.

Belge düzeyi çözümlerle ilgili güvenlik hakkında daha fazla bilgi için bkz. [Belgelere Güven Verilmesi.](granting-trust-to-documents.md)

## <a name="creating-a-basic-installer"></a>Temel Yükleyici Oluşturma

Kurulum ve Dağıtım proje şablonları, indirilebilir Microsoft Visual Studio [Yükleyici Projeleri](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) uzantısına dahil edilir.

Bir çözüm için bir yükleyici Office için bu görevlerin gerçek olması gerekir:

- Dağıtılacak Office çözümünün bileşenlerini ekleyin.
- Uygulama düzeyinde eklentiler için kayıt defteri anahtarlarını yapılandırma.
- Önkoşul bileşenlerini, son kullanıcılar bilgisayarlarına yüklen için yapılandırma.
- Gerekli önkoşul bileşenlerinin kullanılabilir olduğunu doğrulamak için başlatma koşullarını yapılandırma. Tüm gerekli önkoşullar yüklenmezse, yüklemenin engellenmiş olması için başlatma koşulları kullanılabilir.

İlk adım kurulum projesini oluşturmaktır.

### <a name="to-create-the-addin-setup-project"></a>AddIn Kurulum projesini oluşturmak için

1. Dağıtmak Office addIn Project eklentisini açın. Bu örnekte ExcelAddIn adlı Excel bir eklenti kullanıyoruz.
2. Aç Office Project yeni proje eklemek **için** Dosya  menüsünde Ekle'yi genişletin ve **Yeni Project'ye** tıklayın.
::: moniker range="=vs-2017"
3. Yeni Project Ekle **iletişim** kutusunda,  Project türleri bölmesinde Diğer  Project Türleri'ni genişletin,  ardından Kurulum ve Dağıtım'ı genişletin ve ardından **Visual Studio Yükleyicisi.**
4. Şablonlar **bölmesinde,** yüklü şablonlar **grubundan** **Project'Visual Studio'yi** seçin.
::: moniker-end
::: moniker range="=vs-2019"
3. Yeni **Uygulama Ekle iletişim Project** Kurulum **şablonu'Project** seçin.
4. **İleri**’ye tıklayın.
::: moniker-end

5. Ad **kutusuna** **OfficeAddInSetup yazın.**
::: moniker range="=vs-2017"
6. Yeni **kurulum projesini** oluşturmak için Aç'a tıklayın.
::: moniker-end
::: moniker range="=vs-2019"
6. Yeni **kurulum projesini** oluşturmak için Oluştur'a tıklayın.
::: moniker-end

Visual Studio yeni kurulum projesi için Dosya Sistemi Gezgini'ni açar. Dosya Sistemi Gezgini, kurulum projesine dosya eklemenize olanak sağlar.

   ![Kurulum projesi için Dosya Sistemi Gezgini'nin ekran görüntüsü](media/setup-project-figure-1.png)

   **Şekil 1: Kurulum projesi için Dosya Sistemi Gezgini**

Kurulum projesinin ExcelAddIn'i dağıtması gerekir. Kurulum projesine ExcelAddIn proje çıktısını ekleyerek bu görev için kurulum projesini yapılandırabilirsiniz.

### <a name="to-add-the-exceladdin-project-output"></a>ExcelAddIn proje çıktısını eklemek için

1. Dosyanın **Çözüm Gezgini** **OfficeAddInSetup'a** sağ tıklayın, Ekle'ye  tıklayın ve ardından **Çıktı'Project tıklayın.**
2. Çıkış **Grubu ekle Project** proje **listesinden ExcelAddIn** ve Birincil **Çıkış'ı seçin.**
3. Proje **çıktısını** kurulum projesine eklemek için Tamam'a tıklayın.

    ![Çıkış Grubu Ekle iletişim Project Kurulum Project ekran görüntüsü](media/setup-project-figure-2.png)

    **Şekil 2: Kurulum Project Çıkış Project Ekle iletişim kutusu**

Kurulum projesinin dağıtım bildirimini ve uygulama bildirimini dağıtması gerekir. Bu iki dosyayı kurulum projesine ExcelAddIn projesinin çıkış klasöründen tek başına dosyalar olarak ekleyin.

### <a name="to-add-the-deployment-and-application-manifests"></a>Dağıtım ve uygulama bildirimlerini eklemek için

1. Dosyanın **Çözüm Gezgini** **OfficeAddInSetup'a** sağ tıklayın, Ekle'ye ve **Dosya'ya** **tıklayın.**
2. Dosya **Ekle iletişim** kutusunda **ExcelAddIn çıkış dizinine** gidin. Genellikle çıkış dizini, seçilen **\\ derleme yapılandırmasına** bağlı olarak proje kök dizininin bin sürümü alt klasörüdür.
3. **ExcelAddIn.vsto** ve **ExcelAddIn.dll.manifest** dosyalarını seçin ve  Aç'a tıklar ve bu iki dosyayı kurulum projesine ekleyin.

    ![Çözüm Gezgini'daki Uygulama ve dağıtım bildirimlerinin ekran Çözüm Gezgini](media/setup-project-figure-3.jpg)

    **Şekil 3: Eklenti için uygulama ve dağıtım bildirimleri Çözüm Gezgini**

ExcelAddIn'e başvurmak, ExcelAddIn'in gerektirdiği tüm bileşenleri içerir. Bu bileşenlerin doğru şekilde kaydedilene izin vermek için önkoşul paketleri kullanılarak hariç tutularak dağıtılması gerekir. Ayrıca, yükleme başlamadan önce Yazılım Lisans Koşulları görüntüleniyor ve kabul edilmeli.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>ExcelAddIn projesi bağımlılıklarını dışlamak için

1. **Çözüm Gezgini**, **officeaddınsetup** düğümünde, **Microsoft .NET Framework** hariç **algılanan bağımlılıklar** öğesinin altındaki tüm bağımlılık öğelerini veya **\*.Utilities.dll** biten herhangi bir derlemeyi seçin. Yardımcı programlar derlemeleri, uygulamanızla birlikte dağıtılmaları anlamına gelir.
2. Gruba sağ tıklayın ve **Özellikler**' i seçin.
3. **Özellikler** penceresinde, bağımlı derlemeleri Kurulum projesinden dışlamak Için **hariç tut** özelliğini **true** olarak değiştirin. Yardımcı program derlemelerinin dışlanmadığından emin olun.

    ![Hariç tutulacak bağımlılıkları gösteren Çözüm Gezgini ekran görüntüsü](media/setup-project-figure-4.jpg)

    **Şekil 4: bağımlılıkları dışlama**

önyükleyici olarak da bilinen bir kurulum programı ekleyerek önkoşul bileşenlerini yüklemek için Windows Installer paketinizi yapılandırabilirsiniz. Bu kurulum programı önyükleme olarak adlandırılan bir işlem olan önkoşul bileşenlerini yükleyebilir.

**ExcelAddIn** Için, eklentinin doğru şekilde çalıştırılabilmesi için önce bu önkoşulların yüklenmesi gerekir:

- Office çözümünün hedeflediği Microsoft .NET Framework sürümü.
- Office çalışma zamanına yönelik Microsoft Visual Studio 2010 araçları.

Bağımlı bileşenleri önkoşul olarak yapılandırmak için

1. **Çözüm Gezgini** **OfficeAddInSetup** projesine sağ tıklayın ve **Özellikler**' i seçin.
2. **OfficeAddInSetup Özellik sayfaları** iletişim kutusu görüntülenir.
3. **Önkoşullar** düğmesine tıklayın.
4. önkoşullar iletişim kutusunda, .NET Framework için doğru sürümü ve Office çalışma zamanı için Microsoft Visual Studio araçlarını seçin.

    ![Önkoşullar Iletişim kutusunun ekran görüntüsü](media/setup-project-figure-5.png)

    **Şekil 5: Önkoşullar Iletişim kutusu**

    > [!NOTE]
    >Visual Studio kurulum Project yapılandırılan önkoşul paketlerinden bazıları seçili derleme yapılandırmasına bağımlıdır. Kullandığınız her yapı yapılandırması için doğru Önkoşul bileşenlerini seçmeniz gerekir.

Microsoft Office, kayıt defteri anahtarlarını kullanarak eklentileri bulur. HKEY \_ geçerli \_ Kullanıcı kovanındaki anahtarlar, her bir kullanıcı için eklentiyi kaydetmek üzere kullanılır. HKEY \_ Local makine Hive altındaki anahtarlar, \_ makinenin tüm kullanıcıları için eklentiyi kaydettirmek üzere kullanılır. kayıt defteri anahtarları hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Kayıt defterini yapılandırmak için

1. **Çözüm Gezgini** **OfficeAddInSetup**' a sağ tıklayın.
2. **Görünümü** genişlet.
3. Kayıt Defteri Düzenleyicisi penceresini açmak için **kayıt defteri** ' ne tıklayın.
4. **Kayıt defteri (OfficeAddInSetup)** düzenleyicisinde, **HKEY \_ Local \_ MACHINE** ve ardından **Software**' i genişletin.
5. **HKEY \_ Local \_ makine \\ yazılımı** altında bulunan **\[ Manufacturer \]**? anahtarını silin.
6. **HKEY \_ geçerli \_ Kullanıcı** ve ardından **Software**' i genişletin.
7. **HKEY \_ geçerli \_ Kullanıcı \\ yazılımı** altında bulunan **\[ üretici \]** anahtarını silin.
8. Eklenti yüklemesine kayıt defteri anahtarları eklemek için **Kullanıcı/makine Hive** anahtarına sağ tıklayın, **Yeni anahtar**' ı seçin. Yeni anahtarın adı için metin **yazılımını** kullanın. Yeni oluşturulan **yazılım** anahtarına sağ tıklayıp **Microsoft** metin ile yeni bir anahtar oluşturun.
9. Eklenti kaydı için gereken tüm anahtar hiyerarşisini oluşturmak için benzer bir işlem kullanın:

    **kullanıcı/makine Hive \\ yazılımı \\ Microsoft \\ Office \\ Excel \\ addıns \\ samplecompany. exceladdın**

    Şirket adı genellikle, benzersizlik sağlamak için eklentinin adının öneki olarak kullanılır.

10. **SampleCompany. ExcelAddIn** anahtarına sağ tıklayın, **Yeni**' yi seçin ve **dize değeri**' ne tıklayın. Ad için metin **açıklamasını** kullanın.
11. Üç değer daha eklemek için bu adımı kullanın:
    - Tür **dizesi** **FriendlyName**
    - **DWORD** türünde **LoadBehavior**
    - **Dize** türü **bildirimi**

12. Kayıt defteri düzenleyicisinde **Açıklama** değerine sağ tıklayın ve **Özellikler penceresi**' ne tıklayın. **özellikler penceresinde**, Value özelliği için **Excel Demo eklentisi** girin.
13. Kayıt defteri düzenleyicisinde **FriendlyName** anahtarı ' nı seçin. **özellikler penceresinde** **değer** özelliğini **Excel Demo eklentisi** olarak değiştirin.
14. Kayıt defteri düzenleyicisinde **LoadBehavior** anahtarını seçin. **Özellikler penceresinde** **değer** özelliğini 3 olarak değiştirin **.** LoadBehavior için 3 değeri, eklentinin ana bilgisayar uygulamasının başlangıcında yüklenmesi gerektiğini gösterir. yükleme davranışı hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](registry-entries-for-vsto-add-ins.md).

15. Kayıt defteri düzenleyicisinde **bildirim** anahtarını seçin. **Özellikler penceresinde**, **Value** özelliğini **FILE:///[targetı] ExcelAddIn. VSTO | vstolocal** olarak değiştirin

    ![Kayıt defteri düzenleyicisinin ekran görüntüsü](media/setup-project-figure-6.png)

    **Şekil 6: kayıt defteri anahtarlarını ayarlama**

      VSTO çalışma zamanı, dağıtım bildirimini bulmak için bu kayıt defteri anahtarını kullanır. [TARGETDıR] makrosu, eklentinin yüklendiği klasörle birlikte değişir. Makronun sonunda \ karakteri bulunur, bu nedenle dağıtım bildiriminin dosya adı \ karakteri olmadan ExcelAddIn. VSTO olmalıdır.
      **vstolocal** soneki, eklentinin ClickOnce önbelleği yerine bu konumdan yüklenmesi gereken VSTO çalışma zamanına söyler. bu soneki kaldırmak, çalışma zamanının özelleştirmeyi ClickOnce önbelleğine kopyalamasına neden olur.

   >[!WARNING]
   >Visual Studio 'de kayıt defteri Düzenleyicisi ile ilgili çok dikkatli olmanız gerekir. Örneğin, yanlışlıkla yanlış anahtar için DeleteAtUninstall ayarlarsanız, kayıt defterinin etkin bir bölümünü silebilir, Kullanıcı bilgisayarından tutarsız, hatta daha kötü bir durumda bırakabilir.

Office-bit sürümleri, eklentileri aramak için 64 bit kayıt defteri kovanını kullanacaktır. 64 Eklentileri 64 bit kayıt defteri Hive altına kaydetmek için, Kurulum projesinin hedef platformunun yalnızca 64 bit olarak ayarlanması gerekir.

1. Çözüm Gezgini ' nde **OfficeAddInSetup** projesini seçin.
2. **Özellikler** penceresine gidin ve **TargetPlatform** özelliğini **x64** olarak ayarlayın.

Office hem 32-bit hem de 64-bit sürümleri için bir eklenti yüklemek, iki ayrı msı paketi oluşturmanızı gerektirir. Biri 32 bit için, diğeri 64 bit için.

  ![Eklentileri 64-bit Office kaydetmek için hedef platformu gösteren Özellikler penceresinin ekran görüntüsü](media/setup-project-figure-7.jpg)

  **Şekil 7: eklentileri 64 bit Office kaydetmek için hedef platform**

Eklentiyi veya çözümü yüklemek için MSI paketi kullanılıyorsa, yüklenmesi gereken önkoşul olmadan yüklenebilir. Önkoşullar yüklü değilse eklentinin yüklenmesini engellemek için, MSI içindeki başlatma koşullarını kullanabilirsiniz.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>VSTO çalışma zamanını algılamak için bir başlatma koşulu yapılandırın

1. **Çözüm Gezgini** **OfficeAddInSetup**' a sağ tıklayın.
2. **Görünümü** genişlet.
3. **Başlatma koşulları**' na tıklayın.
4. **Başlatma koşulları (OfficeAddInSetup)** düzenleyicisinde, **hedef makinede gereksinimler**' e sağ tıklayın ve ardından **kayıt defteri başlatma koşulu Ekle**' ye tıklayın. bu arama koşulu, VSTO çalışma zamanının yüklediği bir anahtarın kayıt defterinde arama yapabilir. Daha sonra anahtarın değeri, adlandırılmış bir özellik aracılığıyla yükleyicinin çeşitli parçaları tarafından kullanılabilir. Başlatma koşulu, belirli bir değeri denetlemek için arama koşulu tarafından tanımlanan özelliği kullanır.
5. **Başlatma koşulları (OfficeAddInSetup)** düzenleyicisinde, RegistryEntry1 arama koşulu **Ara** ' yı seçin, koşulu sağ tıklatın ve **Özellikler penceresi**' ni seçin.

6. **Özellikler** penceresinde, aşağıdaki özellikleri ayarlayın:
   1. **VSTO 2010 çalışma zamanını aramak** için **(ad)** değerini ayarlayın.
   2. **Özelliğin** değerini **Vstoruntimeredist** olarak değiştirin.
   3. **RegKey** değerini **yazılım \\ Microsoft \\ VSTO çalışma zamanı kurulumu \\ v4R** olarak ayarlayın
   4. **Kök** özelliği **vsdrrHKLM** olarak ayarlayın.
   5. **Değer** özelliğini **Sürüm** olarak değiştirin.

7. **Başlatma koşulları (OfficeAddInSetup)** düzenleyicisinde, **condition1** başlatma koşulunu seçin, koşulu sağ tıklatın ve **Özellikler penceresi**' ni seçin.
8. Özellikler penceresi, aşağıdaki özellikleri ayarlayın:
   1. **VSTO 2010 çalışma zamanı kullanılabilirliğini doğrulamak** için **(ad)** ayarlayın.
   2. **Koşulun** değerini **Vstoruntimeredist \> = "10.0.30319"** olarak değiştirin
   3. **InstallUrl** özelliğini boş bırakın.
   4.  **Office çalışma zamanı için Visual Studio 2010 araçlarına ileti ayarlayın. Eklentiyi yüklemek için lütfen Setup.exe çalıştırın**.

        ![Çalışma zamanı kullanılabilirliğini doğrula başlatma koşulunun Özellikler penceresinin ekran görüntüsü](media/setup-project-figure-8.jpg)

        **Şekil 8: çalışma zamanı kullanılabilirliğini doğrula başlatma koşulunun Özellikler penceresi**

 yukarıdaki başlatma koşulu, önyükleyici paketi tarafından yüklendiğinde VSTO çalışma zamanının varlığını açıkça denetler.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Office tarafından yüklenen VSTO çalışma zamanını algılamak için bir başlatma koşulu yapılandırın

1. **Başlatma koşulları (OfficeAddInSetup)** düzenleyicisinde, **Arama hedef makine**' ye sağ tıklayın ve ardından **kayıt defteri araması Ekle**' ye tıklayın.
2. **RegistryEntry1 arama koşullarını** ara'yı seçin, koşula sağ tıklayın ve Özellikler **Penceresi'ni seçin.**
3. Özellikler **penceresinde** şu özellikleri ayarlayın:
    1. **(Ad)** değerini Office VSTO **Runtime için ara olarak ayarlayın.**
    2. Özelliğin değerini  **OfficeRuntime olarak değiştirme.**
    3. **RegKey** değerini SOFTWARE Microsoft VSTO **Runtime Setup \\ \\ \\ v4 olarak ayarlayın.**
    4. Root özelliğini **vsdrrHKLM olarak bırakın.** 
    5. Value **özelliğini Sürüm** olarak **değiştirme.**

4. Başlatma Koşulları **(OfficeAddInSetup)** düzenleyicisinde, daha önce tanımlanan **VSTO 2010 Çalışma** Zamanı kullanılabilirlik başlatma koşullarını doğrula'yı seçin, koşula sağ tıklayın ve Özellikler Penceresi'ni **seçin.**

5. Condition özelliğinin **değerini** **VSTORUNTIMEREDIST \> ="10.0.30319" VEYA OFFICERUNTIME \> ="10.0.21022" olarak değiştirir.** Sürüm numaraları, Eklentinizin gerektirdiği çalışma zamanının sürümlerine bağlı olarak sizin için farklı olabilir.

    ![Başlatma koşulu için Özellikler Windows ekran görüntüsü](media/setup-project-figure-9.jpg)
  
    **Şekil 9: Redist Windows Çalışma Zamanı Kullanılabilirliğini Doğrulama veya başlatma koşulu Office özellikleri**

Bir Eklenti 4.NET Framework veya daha yeni bir sürümü hedeflerse, başvurulan Birincil Birlikte Çalışma Derlemeleri'nin (PIA) içindeki Türler, VSTO ekli olabilir.

Aşağıdaki adımları gerçekleştirerek Birlikte Çalışma Türlerinin Eklentinize ekli olup olamayacaklarını kontrol etmek için:

1. Çözüm Gezgini'de Başvurular Düğümünü genişletin
2. PIA başvurularından birini seçin, örneğin **Office.**
3. F4'e basarak veya Derlemeler bağlam menüsünden Özellikler'i seçerek özellikler pencerelerini görüntüleme.
4. Embed Interop Types **özelliğinin değerini kontrol edin.**

Değer True olarak **ayarlanırsa** Türler ekli olur ve Kurulum projesini oluşturmak [**için bölümüne atlayabilirsiniz.**](#to-build-the-setup-project)

Daha fazla bilgi için [bkz. Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Başlatma koşullarını, belirli PIA'lar için Office yapılandırmak için

1. Başlatma Koşulları **(OfficeAddInSetup)** düzenleyicisinde, Hedef Makinede Gereksinimler'e sağ tıklayın ve ardından Yükleyici Başlatma **Koşulu'Windows Ekle'ye tıklayın.** Bu başlatma koşulu, belirli Office kimliğini arayarak belirli bir PIA'yı arar.
2. Başlatma koşulu özelliklerini **göstermek için Bileşen1'i** ara'ya sağ tıklayın ve Özellikler Penceresi'ne tıklayın. 
3. Özellikler **Penceresinde şu** özellikleri ayarlayın:

    1. **(Name)** özelliğinin değerini Paylaşılan **PIA için ara Office değiştirme**
    2. ComponentID değerini, **kullanmakta** Office Bileşen Kimliği olarak değiştirebilirsiniz. Bileşen Kimliklerinin listesini aşağıdaki tabloda bulabilirsiniz, örneğin **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. **Property** özelliğinin değerini **HASSHAREDPIA olarak değiştirir.**

4. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde **Koşul1'e** sağ  tıklayın ve Başlatma koşulu özelliklerini göstermek için Özellikler Penceresi'ne tıklayın.

5. Condition1'in **şu özelliklerini değiştirin:**

    1. **(Ad) ifadesini Paylaşılan** **PIA kullanılabilirliğini Office olarak değiştirebilirsiniz.**
    2. Koşulu  **HASSHAREDPIA olarak değiştirme.**
    3. **InstallUrl'i boş** bırakın.
    4. **İletiyi,** mevcut **değil iletisiyle etkileşim kurmak Excel gerekli bir bileşen olarak değiştirebilirsiniz. Lütfen setup.exe.**

    ![Paylaşılan PIA başlatma koşullarını doğrulama Office Özellikler Penceresinin ekran görüntüsü](media/setup-project-figure-10.jpg)
  
    **Şekil 10: Paylaşılan PIA başlatma Office doğrulama için Özellikler Penceresi**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Microsoft Office için Birincil Birlikte Çalışma Derlemelerinin Bileşen Microsoft Office

|Birincil birlikte çalışma derlemesi|Office 2010|Office 2013|Office 2013 (64 bit)|Office 2016|Office 2016 (64 bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5HITCD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5HITCD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Akıllı Etiket|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office Paylaşılan|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Son başlatma koşullarının ekran görüntüsü](media/setup-project-figure-11.jpg)

  **Şekil 11: Son başlatma koşulları**

ExcelAddIn yüklemesi için başlatma koşullarını daha da daraltabilirsiniz. Örneğin, gerçek hedef uygulamanın yüklü olup Office yararlı olabilir.

### <a name="to-build-the-setup-project"></a>Kurulum projesini derlemek için

1. Dosyanın **Çözüm Gezgini** **OfficeAddInSetup** projesine sağ tıklayın ve Derleme'ye **tıklayın.**
2. Windows **Gezgini'ni** kullanarak **OfficeAddInSetup** projesinin çıkış dizinine gidin ve seçili derleme yapılandırmasına bağlı olarak Yayın veya Hata Ayıklama klasörüne gidin. Klasördeki tüm dosyaları, kullanıcıların erişebilirsiniz bir konuma kopyalayın.

ExcelAddIn kurulumunu test etmek için

1. **OfficeAddInSetup'ı kopya istediğiniz konuma** gidin.
2. **OfficeAddInSetup** setup.exe yüklemek için setup.exe dosyasına çift tıklayın. Görünen tüm Yazılım Lisans Koşulları'nı kabul edin ve eklentiyi kullanıcı bilgisayarına yüklemek için kurulum sihirbazını tamamlayın.

Bu Excel Office, kurulum sırasında belirtilen konumdan yük olmalı ve çalışmalı.

## <a name="additional-requirements-for-document-level-solutions"></a>Belge Düzeyi Çözümler için Ek Gereksinimler

Belge düzeyinde çözümlerin dağıtımı, Windows Yükleyicisi kurulum projesinde birkaç farklı yapılandırma adımı gerektirir.

Belge düzeyinde bir çözüm dağıtmak için gereken temel adımların listesi:

- Visual Studio Kurulum Project.
- Belge düzeyi çözüme birincil çıktıyı ekleyin. Birincil çıkış, belgeyi Microsoft Office içerir.
- Dağıtım ve uygulama bildirimlerini gevşek dosyalar olarak ekleyin.
- Bağımlı bileşenleri yükleyici paketinden hariç tut (herhangi bir yardımcı program derlemesi dışında).
- Önkoşul paketlerini yapılandırma.
- Başlatma koşullarını yapılandırma.
- Kurulum projesini derleme ve sonuçları dağıtım konuma kopyalama.
- Kurulumu yürüterek kullanıcı bilgisayarına belge düzeyinde çözümü dağıtın.
- Gerekirse özel belge özelliklerini güncelleştirin.

### <a name="changing-the-location-of-the-deployed-document"></a>Dağıtılan Belgenin Konumunu Değiştirme

Belge düzeyi Office bulmak için bir belge içindeki özellikler kullanılır. Belge, VSTO derlemesi ile aynı klasöre yüklenirse, herhangi bir değişiklik gerekmez. Ancak, farklı bir klasöre yüklendiyse, kurulum sırasında bu özelliklerin güncelleştirilmiş olması gerekir.

Bu belge özellikleri hakkında daha fazla bilgi için bkz. [Özel Belge Özelliklerine Genel Bakış.](custom-document-properties-overview.md)

Bu özellikleri değiştirmek için kurulum sırasında özel bir eylem kullanabilirsiniz.

Aşağıdaki örnekte ExcelWorkbookProject adlı belge düzeyinde bir çözüm ve ExcelWorkbookSetup adlı bir kurulum projesi ılmaktadır. ExcelWorkbookSetup projesi, kayıt defteri anahtarlarını ayarlama dışında yukarıda açıklanan adımların aynısı kullanılarak yapılandırılır.

Özel eylem projesini çözüme eklemek Visual Studio için

1. Yeni bir .NET Konsolu projesi eklemek için, Office Belge **Dağıtımı Project** sağ **Çözüm Gezgini**
2. **Ekle'yi** genişletin ve Yeni **Project.**
3. Konsol Uygulaması şablonunu seçin ve projeye **AddCustomizationCustomAction adını girin.**

    ![Çözüm Gezgini - AddCustomizationCustomAction ekran görüntüsü](media/setup-project-figure-15.jpg)
  
    **Şekil 12: Çözüm Gezgini - EkleCustomizationCustomAction**

4. Bu derlemelere bir Başvuru ekleyin:
    1. System.ComponentModel
    2. System.Configuration. Yüklemek
    3. Microsoft.VisualStudio.Tools.Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Bu kodu Program.cs veya Program.vb'ye kopyalayın

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Belgeye özelleştirme eklemek için, belge düzeyi çözüme sahip VSTO kimliğiniz gerekir. Bu değer, Visual Studio alınır.

Çözüm kimliğini almak için

1. Belge **düzeyinde çözümü** **derlemek ve çözüm** kimliği özelliğini proje dosyasına eklemek için Derleme menüsünde Çözümü Derleme'ye tıklayın.
2. Dosya **Çözüm Gezgini** **ExcelWorkbookProject** belge düzeyi projesine sağ tıklayın
3. Proje dosyasına dosyanın içinden erişmek için **UnloadProject'e** Visual Studio.

    ![Belge Çözüm Gezgini Kaldırma Excel Ekran Görüntüsü](media/setup-project-figure-16.jpg)

    **Şekil 13: Belge Excel Kaldırma**

4. Komut **Çözüm Gezgini** **ExcelWorkbookProject'e** sağ tıklayın ve **DüzenleExcelWorkbookProject.vbproj** veya **ExcelWorkbookProject.csproj'u Düzenle'ye tıklayın.**
5. **ExcelWorkbookProject** **düzenleyicisinde, PropertyGroup** öğesinin içinde **SolutionID öğesini** bulun.
6. Bu öğenin GUID değerini kopyalayın.

    ![SolutionID'i Alma](media/setup-project-figure-17.jpg)

    **Şekil 14: SolutionID alma**

7. Dosyanın **Çözüm Gezgini** **ExcelWorkbookProject'e sağ tıklayın ve** yeniden **yükle'ye Project.**
8. **ExcelWorkbookProject** düzenleyicisini kapatmak için görüntülenen iletişim kutusunda Evet'e tıklayın. 
9. Çözüm **Kimliği,** Özel Eylem Yükle'de kullanılır.

Son adım, Yükleme ve Kaldırma adımları için özel **eylemi** **yapılandırmaktır.**

### <a name="to-configure-the-setup-project"></a>Kurulum projesini yapılandırmak için

1. dosyanın **Çözüm Gezgini** **ExcelWorkbookSetup'a** sağ tıklayın, Ekle'yi  genişletin ve Çıkış'Project **tıklayın.**
2. Çıkış **Grubu Ekle Project iletişim** kutusunda, **Project** **EkleCustomizationCustomAction 'a tıklayın.**
3. Birincil **Çıkış'ı** seçin **ve** iletişim kutusunu kapatmak ve özel eylemi içeren derlemeyi kurulum projesine eklemek için Tamam'a tıklayın.

    ![Belge Bildirimi Özel Eylemi - Çıkış Grubu Project Ekle penceresinin ekran görüntüsü](media/setup-project-figure-18.jpg)

    **Şekil 15: Belge Bildirimi Özel Eylemi - Project Grubu Ekleme**

4. Dosyanın **Çözüm Gezgini** **ExcelWorkbookSetup'a sağ tıklayın.**
5. **Görünüm'i** genişletin ve Özel **Eylemler'e tıklayın.**
6. Özel Eylemler **(ExcelWorkbookSetup)** düzenleyicisinde Özel Eylemler'e sağ tıklayın ve **Özel** Eylem **Ekle'ye tıklayın.**
7. Uygulama **Klasöründe Öğe Project** iletişim kutusunda, Arama **listesinde** Uygulama Klasörü'ne **tıklayın.** **AddCustomizationCustomAction(active)** yolundan Birincil  Çıktı'yı seçin ve Özel eylemi Yükleme adımına eklemek için Tamam'a tıklayın.
8. Yükleme düğümü **altında,** **AddCustomizationCustomAction(Active)** öğesinin Birincil çıktısı'na sağ tıklayın ve Yeniden Adlandır'a **tıklayın.** Özel eyleme **Belgeyi Belgelerim'e kopyala adını ve özelleştirmeyi ekleyin.**
9. Kaldır **düğümünün altında** **AddCustomizationCustomAction(Active)** öğesinin Birincil çıktısı'na sağ tıklayın ve Yeniden Adlandır'a **tıklayın.** Özel eylemi Belgeler **klasöründen belgeyi kaldır olarak ad girin.**

    ![Belge Bildirimi Özel Eylemleri penceresinin ekran görüntüsü](media/setup-project-figure-19.jpg)

    **Şekil 16: Belge Bildirimi Özel Eylemleri**

10. Özel Eylemler **(ExcelWorkbookSetup)** düzenleyicisinde, Belgeyi Belgelerime kopyala'ya sağ tıklayın ve özelleştirme **ekleyin ve** Özellikler Penceresi'ne **tıklayın.**
11. **CustomActionData** **Özellikleri** penceresinde, özelleştirme DLL'lerinin konumunu, dağıtım bildirimini ve Microsoft Office girin. SolutionID de gereklidir.
12. Herhangi bir kurulum hatalarını bir dosyaya günlüğe eklemek isterseniz LogFile parametresini dahil edin.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Belgeyi Belgelerime Kopyalamak için Özel Eylemin Ekran Özellikler penceresi](media/setup-project-figure-20.jpg)

    **Şekil 17: Belgelerime Belge Kopyalamaya Özel Eylem**

13. Kaldırma için Özel Eylem belgenin adına ihtiyaç gösterir; **Bunu CustomActionData** içinde aynı documentLocation parametresini kullanarak sekleyebilirsiniz

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. **ExcelWorkbookSetup projesini derle ve dağıt.**
15. Belgelerim **klasörüne** bakın ve ExcelWorkbookProject.xlsx açın.

## <a name="additional-resources"></a>Ek Kaynaklar

[Nasıl kurulur: Office için Visual Studio Araçları Çalışma Zamanı'Office için Visual Studio Araçları yükleme](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Birincil Birlikte Çalışma Derlemeleri](office-primary-interop-assemblies.md)

[VSTO Eklentileri için kayıt defteri girdileri](registry-entries-for-vsto-add-ins.md)

[Özel Belge Özelliklerine Genel Bakış](custom-document-properties-overview.md)

[Windows Registry'de Form Bölgeleri Belirtme](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Belgelere Güven Verme](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Yazarlar Hakkında

Wouter van Vugt, Office Open XML teknolojilerine sahip bir Microsoft MVP'si ve Office Business Applications, Microsoft Office ve ilgili .NET teknolojileriyle SharePoint Office Business Applications (OBA) oluşturmaya odaklanan bağımsız bir danışmandır.
Wouter, MSDN gibi geliştirici topluluğu sitelerine sık katkıda bulunan bir [kullanıcıdır.](/previous-versions/office/developer/office-2007/bb879915(v=office.12)) Birçok teknik yazı ve makalenin yanı sıra Open XML: Explained e-book (Açıklandı e-kitabı) başlıklı bir kitabı da yayımladı.
Wouter, çeşitli kanallardan son teknoloji teknik içerikler sunan Bir Felemenkçe şirket olan Code-Focusing'ın kurucusudur. Wouter hakkında daha fazla bilgi için blog gönderisini okuyun.

Ted Pattison bir MVP SharePoint yazar, eğitmen ve Ted Pattison Grubunun kurucusudur. 2005 yılında Ted, Microsoft'un Geliştirici Platformu Destekçiliği grubu tarafından Windows SharePoint Services 3.0 ve Microsoft Office SharePoint Server 2007 için Ascend geliştirici eğitim müfredatı yazması için işe alındı. O zamandan beri Ted tamamen profesyonel geliştiricileri 2007 SharePoint eğittirdi. Ted, Microsoft Press için Inside Windows SharePoint Services 3.0 başlıklı ve iş çözümlerinin geliştirilmesi için geliştirme platformu olarak SharePoint üzerine odaklanan bir kitap yazmayı tamamladı. Ted ayrıca MSDN Magazine için Office Space başlıklı geliştirici odaklı bir sütun yazar.
