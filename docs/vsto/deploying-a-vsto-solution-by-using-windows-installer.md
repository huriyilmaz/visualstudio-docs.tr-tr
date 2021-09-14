---
title: Windows Installer kullanarak VSTO çözümünü dağıtma
description: bir Visual Studio Yükleyicisi projesi kullanarak Office (VSTO) eklenti veya belge düzeyi çözümü için Microsoft Visual Studio araçları dağıtmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634145"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Windows Installer kullanarak VSTO çözümünü dağıtma

## <a name="summary"></a>Özet

bir Visual Studio Yükleyicisi projesi kullanarak Office (VSTO) eklenti veya belge düzeyi çözümü için Microsoft Visual Studio araçları dağıtmayı öğrenin.

Wouter van Vugt, kod Counsel

Ted Pattison, Ted Pattison grubu

Bu makale, Microsoft tarafından özgün yazarlardan izniyle güncelleştirildi.

**uygulama hedefi:** Office için Visual Studio Araçları, Microsoft Office Microsoft Visual Studio.

## <a name="overview"></a>Genel Bakış

bir VSTO çözümü geliştirebilir ve çözümü bir Windows Installer paketi kullanarak dağıtabilirsiniz. bu tartışma basit bir Office eklentisi dağıtmaya yönelik adımları içerir.

## <a name="deployment-methods"></a>Dağıtım yöntemleri

ClickOnce, eklentiler ve çözümleriniz için kurulum oluşturmak üzere kolayca kullanılabilir. Ancak, makine düzeyi eklentileri gibi yönetim ayrıcalıkları gerektiren eklentileri yükleyemez.

yönetici ayrıcalıkları gerektiren eklentiler Windows Installer kullanılarak yüklenebilir, ancak kurulumu oluşturmak için daha fazla çaba gerektirir.

ClickOnce kullanarak VSTO çözümünün nasıl dağıtılacağı konusunda genel bir bakış için bkz. [ClickOnce kullanarak Office çözümü dağıtma](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>VSTO çalışma zamanını hedefleyen Office çözümlerini dağıtma

ClickOnce ve Windows Installer paketlerinin Office çözümü yüklerken aynı ilkel görevlerini yapması gerekir.

1. Önkoşul bileşenlerini Kullanıcı bilgisayarına yükler.
2. Çözüme yönelik belirli bileşenleri dağıtın.
3. Eklentiler için kayıt defteri girişleri oluşturun.
4. Yürütülmesine izin vermek için çözüme güvenin.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Hedef bilgisayarda gerekli önkoşul bileşenleri

VSTO çözümleri çalıştırmak için bilgisayarda yüklü olması gereken yazılım listesi aşağıdadır:

- Microsoft Office 2010 veya sonraki bir sürümü.
- Microsoft .NET Framework 4 veya daha yeni bir sürüm.
- Office çalışma zamanına yönelik Microsoft Visual Studio 2010 araçları.
  Çalışma zamanı, eklentileri ve belge düzeyi çözümlerini yöneten bir ortam sağlar. çalışma zamanının bir sürümü Microsoft Office ile birlikte sevk edebilir, ancak eklentile belirli bir sürümü yeniden dağıtmak isteyebilirsiniz.
- katıştırılmış birlikte çalışma türleri kullanmıyorsanız Microsoft Office için birincil birlikte çalışma derlemeleri.
- Projeler tarafından başvurulan yardımcı program derlemeleri.

### <a name="specific-components-for-the-solution"></a>Çözüme yönelik belirli bileşenler

Yükleyici paketinin bu bileşenleri kullanıcının bilgisayarına yüklemesi gerekir:

- belge düzeyi çözüm oluşturursanız Microsoft Office belge.
- Özelleştirme derlemesi ve gereken derlemeler.
- Yapılandırma dosyaları gibi ek bileşenler.
- Uygulama bildirimi (. manifest).
- Dağıtım bildirimi (. VSTO).

### <a name="registry-entries-for-add-ins"></a>Eklentiler için kayıt defteri girişleri

Microsoft Office, eklentileri bulmak ve yüklemek için kayıt defteri girişlerini kullanır. Bu kayıt defteri girişleri, dağıtım sürecinin bir parçası olarak oluşturulmalıdır. bu kayıt defteri girişleri hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](registry-entries-for-vsto-add-ins.md).

Outlook Özel form bölgelerini görüntüleyen Eklentiler, form bölgelerinin tanımlanmasına izin veren ek kayıt defteri girişleri gerektirir. kayıt defteri girişleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri için kayıt defteri girişleri](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Belge düzeyi çözümlerde herhangi bir kayıt defteri girişi gerekmez. Bunun yerine, özelleştirmenin yerini bulmak için belgenin içindeki Özellikler kullanılır. Bu özellikler hakkında daha fazla bilgi için bkz. [özel belge özelliklerine genel bakış](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>VSTO çözümüne güvenme

Bir özelleştirmenin çalışması için, bir çözümün makine tarafından güvenilir olması gerekir. Eklentiyi bir sertifikayla imzalayarak, bir içerme listesiyle bir güven ilişkisi oluşturarak veya onu makinedeki güvenilir bir konuma yükleyerek bu eklentiye güvenebilir.

imzalama için bir sertifika alma hakkında daha fazla bilgi için bkz. [ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). güvenilen çözümler hakkında daha fazla bilgi için bkz. [ekleme listelerini kullanarak Office çözümlerine güvenme](trusting-office-solutions-by-using-inclusion-lists.md). Windows Installer dosyanıza özel bir eylemle birlikte ekleme listesi girişi ekleyebilirsiniz. Ekleme listesinin etkinleştirilmesi hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma ekleme listesi güvenliği](how-to-configure-inclusion-list-security.md).

Hiçbir seçenek kullanılmazsa, kullanıcıya çözüme güvenip güvenmeyeceğine karar vermesini sağlamak için bir güven istemi görüntülenir.

Belge düzeyi çözümlerle ilgili güvenlik hakkında daha fazla bilgi için bkz. [belgelere güven verme](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Temel yükleyici oluşturma

kurulum ve dağıtım projesi şablonları, indirme için kullanılabilen [Microsoft Visual Studio ınstaller projeleri](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) uzantısına dahildir.

Office çözümü için bir yükleyici oluşturmak için bu görevlerin gerçekleştirilmesi gerekir:

- dağıtılacak Office çözümünün bileşenlerini ekleyin.
- Uygulama düzeyi eklentileri için kayıt defteri anahtarlarını yapılandırın.
- Önkoşul bileşenlerini, son kullanıcılar bilgisayarlarına yüklenebilmeleri için yapılandırın.
- Gerekli önkoşul bileşenlerinin kullanılabilir olduğunu doğrulamak için başlatma koşullarını yapılandırın. Tüm gerekli önkoşullar yüklü değilse, başlatma koşulları yüklemeyi engellemek için kullanılabilir.

İlk adım kurulum projesi oluşturmaktır.

### <a name="to-create-the-addin-setup-project"></a>Eklenti kurulum projesi oluşturmak için

1. dağıtmak istediğiniz Office eklenti Project açın. bu örnekte, exceladdın adlı bir Excel eklentisi kullanıyoruz.
2. Office Project açıkken, **dosya** menüsünde **ekle** ' yi genişletin ve **yeni Project** ' ye tıklayarak yeni bir proje ekleyin.
::: moniker range="=vs-2017"
3. **yeni Project ekle** iletişim kutusunda, **Project türleri** bölmesindeki **diğer Project türler** ' i genişletin, ardından **kurulum ve dağıtım** ' ı genişletin ve ardından **Visual Studio Yükleyicisi**' yi seçin.
4. **şablonlar** bölmesinde, **Visual Studio yüklü** şablonlar grubundan **Project kurulum** ' u seçin.
::: moniker-end
::: moniker range="=vs-2019"
3. **yeni Project ekle** iletişim kutusunda **kurulum Project** şablonunu seçin.
4. **İleri**’ye tıklayın.
::: moniker-end

5. **Ad** kutusuna **OfficeAddInSetup** yazın.
::: moniker range="=vs-2017"
6. Yeni Kurulum projesini oluşturmak için **Aç** ' a tıklayın.
::: moniker-end
::: moniker range="=vs-2019"
6. Yeni Kurulum projesini oluşturmak için **Oluştur** ' a tıklayın.
::: moniker-end

Visual Studio yeni kurulum projesi için dosya sistemi gezginini açar. Dosya sistemi Gezgini, kurulum projesine dosya eklemenize olanak tanır.

   ![Kurulum projesi için dosya sistemi Gezgini 'nin ekran görüntüsü](media/setup-project-figure-1.png)

   **Şekil 1: kurulum projesi için dosya sistemi Gezgini**

Kurulum projesinin ExcelAddIn dağıtması gerekir. Bu görev için Kurulum projesini, ExcelAddIn proje çıktısını kurulum projesine ekleyerek yapılandırabilirsiniz.

### <a name="to-add-the-exceladdin-project-output"></a>ExcelAddIn proje çıkışını eklemek için

1. **Çözüm Gezgini** **officeaddınsetup**' a sağ tıklayın, **ekle** ' ye tıklayın ve ardından **çıkış**' a Project.
2. **Project çıkış grubu ekle** iletişim kutusunda, proje listesinden **exceladdın** ve **birincil çıkış**' ı seçin.
3. Proje çıktısını kurulum projesine eklemek için **Tamam** ' ı tıklatın.

    ![kurulum Project Project çıkış grubu ekle iletişim kutusunun ekran görüntüsü](media/setup-project-figure-2.png)

    **şekil 2: kurulum Project Project çıkış grubu ekle iletişim kutusu**

Kurulum projesinin dağıtım bildirimini ve uygulama bildirimini dağıtması gerekir. Bu iki dosyayı, ExcelAddIn projesinin çıktı klasöründen tek başına dosyalar olarak kurulum projesine ekleyin.

### <a name="to-add-the-deployment-and-application-manifests"></a>Dağıtım ve uygulama bildirimlerini eklemek için

1. **Çözüm Gezgini** **OfficeAddInSetup**' a sağ tıklayın, **Ekle**' ye tıklayın ve **Dosya**' ya tıklayın.
2. **Dosya Ekle** Iletişim kutusunda **ExcelAddIn** çıkış dizinine gidin. Genellikle çıkış dizini, seçilen derleme yapılandırmasına bağlı olarak, proje kök dizininin **bin \\ yayınlama** alt klasörüdür.
3. Bu iki dosyayı kurulum projesine eklemek için **ExcelAddIn. VSTO** ve **ExcelAddIn.dll. manifest** dosyalarını seçin ve **Aç** ' a tıklayın.

    ![Çözüm Gezgini içindeki uygulama ve dağıtım bildirimlerinin ekran görüntüsü](media/setup-project-figure-3.jpg)

    **Şekil 3: Çözüm Gezgini eklenti için uygulama ve dağıtım bildirimleri**

ExcelAddIn 'e başvurmak, ExcelAddIn 'in gerektirdiği tüm bileşenleri içerir. Bu bileşenler, doğru kaydedilmelerini sağlamak için önkoşul paketleri kullanılarak dışlanmalı ve dağıtılmalıdır. Ayrıca, yükleme başlamadan önce yazılım lisans koşullarının görüntülenmesi ve kabul edilmesi gerekir.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>ExcelAddIn projesi bağımlılıklarını dışlamak için

1. **Çözüm Gezgini**, **officeaddınsetup** düğümünde, **Microsoft .NET Framework** hariç **algılanan bağımlılıklar** öğesinin altındaki tüm bağımlılık öğelerini veya ile biten herhangi bir derlemeyi seçin. **\* Utilities.dll**. Yardımcı programlar derlemeleri, uygulamanızla birlikte dağıtılmaları anlamına gelir.
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
    5. Value **özelliğini Version** olarak **değiştirme.**

4. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, daha önce tanımlanan **VSTO 2010 Çalışma** Zamanı kullanılabilirlik başlatma koşullarını doğrula'yı seçin, koşula sağ tıklayın ve Özellikler Penceresi'ni **seçin.**

5. **Condition** özelliğinin değerini **VSTORUNTIMEREDIST \> ="10.0.30319" VEYA OFFICERUNTIME \> ="10.0.21022" olarak değiştirir.** Sürüm numaraları, Eklentinizin gerektirdiği çalışma zamanının sürümlerine bağlı olarak sizin için farklı olabilir.

    ![Başlatma koşulu için Özellikler Windows ekran görüntüsü](media/setup-project-figure-9.jpg)
  
    **Şekil 9: Redist Windows Çalışma Zamanı Kullanılabilirliğini Doğrulama veya başlatma koşulu Office özellikleri**

Bir Eklenti 4.NET Framework veya daha yeni bir sürümü hedeflerse, başvurulan Birincil Birlikte Çalışma Derlemeleri'nin (PIA) içindeki Türler, VSTO ekli olabilir.

Aşağıdaki adımları gerçekleştirerek Birlikte Çalışma Türlerinin Eklentinize ekli olup olamayacaklarını kontrol etmek için:

1. Çözüm Gezgini'de Başvurular Düğümünü genişletin
2. PIA başvurularından birini seçin, örneğin, **Office.**
3. F4'e basarak veya Derlemeler bağlam menüsünden Özellikler'i seçerek özellikler pencerelerini görüntüleme.
4. Embed Interop Types **özelliğinin değerini kontrol edin.**

Değer True olarak **ayarlanırsa** Türler ekli olur ve Kurulum projesini oluşturmak [**için bölümüne atlayabilirsiniz.**](#to-build-the-setup-project)

Daha fazla bilgi için [bkz. Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Başlatma koşullarını, belirli PIA'lar için Office yapılandırmak için

1. Başlatma Koşulları **(OfficeAddInSetup)** düzenleyicisinde, Hedef Makinede Gereksinimler'e sağ tıklayın ve ardından Yükleyici Başlatma **Koşulu'Windows Ekle'ye tıklayın.** Bu başlatma koşulu, belirli Office kimliğini arayarak belirli bir PIA'yı arar.
2. Başlatma koşulu özelliklerini **göstermek için Bileşen1'i** ara'ya sağ tıklayın ve Özellikler Penceresi'ne tıklayın. 
3. Özellikler **Penceresinde şu** özellikleri ayarlayın:

    1. **(Ad)** özelliğinin değerini Paylaşılan **PIA için arama Office olarak değiştirme**
    2. ComponentID **değerini, kullanmakta** Office Bileşen Kimliği olarak değiştirebilirsiniz. Aşağıdaki tabloda Bileşen Kimliklerinin listesini bulabilirsiniz, örneğin **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. **Property** özelliğinin değerini **HASSHAREDPIA olarak değiştirir.**

4. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde **Koşul1'e** sağ  tıklayın ve Başlatma koşulu özelliklerini göstermek için Özellikler Penceresi'ne tıklayın.

5. Condition1'in **şu özelliklerini değiştirin:**

    1. **(Ad) ifadesini Paylaşılan** **PIA kullanılabilirliğini Office olarak değiştirebilirsiniz.**
    2. Koşulu  **HASSHAREDPIA olarak değiştirme.**
    3. **InstallUrl'i boş** bırakın.
    4. **İletiyi,** mevcut **değil iletisiyle etkileşim kurmak Excel bileşen olarak değiştirebilirsiniz. Lütfen şu setup.exe:**.

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

  **Şekil 11: son başlatma koşulları**

ExcelAddIn yüklemesi için başlatma koşullarını daha da iyileştirebilirsiniz. örneğin, gerçek hedef Office uygulamasının yüklenip yüklenmediğini denetlemek faydalı olabilir.

### <a name="to-build-the-setup-project"></a>Kurulum projesi oluşturmak için

1. **Çözüm Gezgini** **OfficeAddInSetup** projesine sağ tıklayın ve **Oluştur**' a tıklayın.
2. **Windows gezginini** kullanarak, **officeaddınsetup** projesinin çıkış dizinine gidin ve seçilen derleme yapılandırmasına bağlı olarak yayın veya hata ayıklama klasörüne gidin. Klasörden tüm dosyaları, kullanıcıların erişebileceği bir konuma kopyalayın.

ExcelAddIn kurulumunu test etmek için

1. **OfficeAddInSetup** 'ı kopyaladığınız konuma gidin.
2. **OfficeAddInSetup** eklentisini yüklemek için setup.exe dosyasına çift tıklayın. Görüntülenen tüm yazılım lisansı koşullarını kabul edin ve Kullanıcı bilgisayarına eklentiyi yüklemek için Kurulum Sihirbazı 'nı doldurun.

Excel Office çözümünün kurulum sırasında belirtilen konumdan yüklenmesi ve çalıştırılması gerekir.

## <a name="additional-requirements-for-document-level-solutions"></a>Belge düzeyi çözümleri için ek gereksinimler

belge düzeyi çözümlerin dağıtımı, Windows Installer kurulum projesinde birkaç farklı yapılandırma adımı gerektirir.

Belge düzeyinde bir çözümü dağıtmak için gereken temel adımların bir listesi aşağıda verilmiştir:

- Visual Studio kurulum Project oluşturun.
- Belge düzeyi çözümünüzün birincil çıkışını ekleyin. birincil çıktı ayrıca Microsoft Office belge içerir.
- Dağıtım ve uygulama bildirimlerini gevşek dosyalar olarak ekleyin.
- Bağımlı bileşenleri yükleyici paketinden (yardımcı program derlemeleri hariç) hariç tutun.
- Önkoşul paketlerini yapılandırın.
- Başlatma koşullarını yapılandırın.
- Kurulum projesi oluşturun ve sonuçları dağıtım konumuna kopyalayın.
- Kurulum 'u yürüterek belge düzeyi çözümünü kullanıcı bilgisayarında dağıtın.
- Gerekirse özel belge özelliklerini güncelleştirin.

### <a name="changing-the-location-of-the-deployed-document"></a>Dağıtılan belgenin konumunu değiştirme

belge düzeyi çözümlerini bulmak için bir Office belgesinin içindeki özellikler kullanılır. belge, VSTO derlemesiyle aynı klasöre yüklenirse hiçbir değişiklik yapılması gerekmez. Ancak, farklı bir klasöre yüklenmişse, bu özelliklerin kurulum sırasında güncelleştirilmeleri gerekir.

Bu belge özellikleri hakkında daha fazla bilgi için bkz. [özel belge özelliklerine genel bakış](custom-document-properties-overview.md).

Bu özellikleri değiştirmek için, kurulum sırasında özel bir eylem kullanmanız gerekir.

Aşağıdaki örnek, ExcelWorkbookProject adlı bir belge düzeyi çözümü ve ExcelWorkbookSetup adlı bir kurulum projesi kullanır. ExcelWorkbookSetup projesi, kayıt defteri anahtarlarının ayarlanması dışında yukarıda belirtilen adımların aynısını kullanarak yapılandırılır.

özel eylem projesini Visual Studio çözümünüze eklemek için

1. **Çözüm Gezgini** **Project Office belge dağıtımına** sağ tıklayarak çözüme yeni bir .net konsol projesi ekleyin
2. **Ekle** ' yi genişletin ve **yeni Project**' ye tıklayın.
3. Konsol uygulaması şablonunu seçin ve projeyi **Addcustomizationcustomaction** olarak adlandırın.

    ![Çözüm Gezgini-AddCustomizationCustomAction ekran görüntüsü](media/setup-project-figure-15.jpg)
  
    **Şekil 12: Çözüm Gezgini-AddCustomizationCustomAction**

4. Bu derlemelere bir başvuru ekleyin:
    1. System. ComponentModel
    2. System. Configuration. Install
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft. VisualStudio. Tools. Applications. ServerDocument

5. Bu kodu program. cs veya program. vb içine kopyalayın

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

özelleştirmeyi belgeye eklemek için VSTO belge düzeyi çözümünüzün çözüm kimliğine sahip olmanız gerekir. bu değer Visual Studio proje dosyasından alınır.

Çözüm KIMLIĞINI almak için

1. Belge düzeyi çözümünü derlemek ve çözüm KIMLIĞI özelliğini proje dosyasına eklemek için **Build (oluştur** ) menüsünde **çözüm oluştur** ' a tıklayın.
2. **Çözüm Gezgini**, belge düzeyi proje **excelworkbookprojesine** sağ tıklayın
3. Visual Studio içindeki proje dosyasına erişmek için **UnloadProject** ' e tıklayın.

    ![Excel belge çözümünü kaldırma Çözüm Gezgini ekran görüntüsü](media/setup-project-figure-16.jpg)

    **şekil 13: Excel belge çözümünü kaldırma**

4. **Çözüm Gezgini**, **excelworkbookproject** öğesine sağ tıklayın ve **editexcelworkbookproject. vbproj** ' e tıklayın veya **excelworkbookproject. csproj öğesini düzenleyin**.
5. **Excelworkbookproject** düzenleyicisinde, **PropertyGroup** öğesinin içindeki **SolutionId** öğesini bulun.
6. Bu öğenin GUID değerini kopyalayın.

    ![SolutionId alınıyor](media/setup-project-figure-17.jpg)

    **Şekil 14: SolutionId alma**

7. **Çözüm Gezgini**, **excelworkbookproject** ' e sağ tıklayın ve **Project yeniden yükle**' ye tıklayın.
8. **Excelworkbookproje** düzenleyicisini kapatmak için görüntülenen Iletişim kutusunda **Evet** ' e tıklayın.
9. **Çözüm Kimliği** , özel Install eyleminde kullanılacaktır.

Son adım, **yükleme** ve **kaldırma** adımları için özel eylemi yapılandırmaktır.

### <a name="to-configure-the-setup-project"></a>Kurulum projesini yapılandırmak için

1. **Çözüm Gezgini**, **excelworkbooksetup**' a sağ tıklayın, **ekle** ' yi genişletin ve **çıkış Project**' a tıklayın.
2. **Project çıkış grubu ekle** iletişim kutusunda, **Project** listesinde **addcustomizationcustomaction**' ye tıklayın.
3. **Birincil çıkış** ' ı seçin ve ardından **Tamam** ' a tıklayarak iletişim kutusunu kapatın ve özel eylemi içeren derlemeyi kurulum projesine ekleyin.

    ![belge bildirimi özel eylemi-Project çıkış grubu ekle penceresi ekran görüntüsü](media/setup-project-figure-18.jpg)

    **şekil 15: belge bildirimi özel eylemi-Project çıkış grubu ekle**

4. **Çözüm Gezgini**, **excelworkbooksetup** öğesine sağ tıklayın.
5. **Görünüm** ' ü genişletin ve **özel eylemler**' i tıklatın.
6. **Özel eylemler (ExcelWorkbookSetup)** düzenleyicisinde, **özel eylemler** ' i sağ tıklatın ve **özel eylem Ekle**' yi tıklatın.
7. **Project öğe seç** iletişim kutusunda, **konum** listesinde, **uygulama klasörü**' ne tıklayın. **AddCustomizationCustomAction (etkin) öğesinden birincil çıkış** ' ı seçin ve ardından, özel eylemi yüklemek Için, **Tamam** ' a tıklayın.
8. **Install düğümü** altında, **addcustomizationcustomaction (etkin) öğesinden birincil çıkış**' a sağ tıklayın ve **Yeniden Adlandır**' a tıklayın. Özel eylem **belgeyi Belgelerim 'e Kopyala ve özelleştirmeyi Ekle** şeklinde adlandırın.
9. **Kaldırma düğümü** altında **addcustomizationcustomaction (etkin) öğesinden birincil çıkış** ' a sağ tıklayın ve **Yeniden Adlandır**' a tıklayın. **Belgeyi belgeler klasöründen Kaldır** özel eylemini adlandırın.

    ![Belge bildirimi özel eylemler penceresinin ekran görüntüsü](media/setup-project-figure-19.jpg)

    **Şekil 16: belge bildirimi özel eylemleri**

10. **Özel eylemler (ExcelWorkbookSetup)** düzenleyicisinde **belgeyi Belgelerim 'e Kopyala ve özelleştirme Ekle** ' ye sağ tıklayın ve **Özellikler penceresi**' ne tıklayın.
11. **CustomActionData** **özellikleri** penceresinde, özelleştirme DLL 'inin konumunu, dağıtım bildirimini ve Microsoft Office belgenin konumunu girin. SolutionId de gereklidir.
12. Herhangi bir kurulum hatasını bir dosyaya kaydetmek isterseniz, bir günlük dosyası parametresi ekleyin.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Belgeyi Belgelerim 'e kopyalamak için özel eylemin ekran görüntüsü Özellikler penceresi](media/setup-project-figure-20.jpg)

    **Şekil 17: belgeyi Belgelerim 'e kopyalamak için özel eylem**

13. Kaldırma için özel eylem, belgenin adına ihtiyaç duyuyor ve bu Işlemi, **CustomActionData** Içinde aynı documentlocation parametresini kullanarak sağlayabilmeniz gerekir

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. **Excelworkbooksetup** projesini derleyin ve dağıtın.
15. **Belgelerim** klasörünü bulun ve ExcelWorkbookProject.xlsx dosyasını açın.

## <a name="additional-resources"></a>Ek Kaynaklar

[nasıl yapılır: Office için Visual Studio Araçları çalışma zamanını yüklemek](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Birincil Birlikte Çalışma Derlemeleri](office-primary-interop-assemblies.md)

[VSTO eklentileri için kayıt defteri girişleri](registry-entries-for-vsto-add-ins.md)

[Özel Belge Özelliklerine Genel Bakış](custom-document-properties-overview.md)

[Windows kayıt defterinde Form bölgelerini belirtme](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Belgelere Güven Verme](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Yazarlar hakkında

Wouter van Vugt, Office Open XML teknolojilerine sahip bir Microsoft MVP'si ve SharePoint, Microsoft Office ve ilgili .NET teknolojileriyle Office Business Applications (OBA) oluşturmaya odaklanan bağımsız bir danışmandır.
Wouter, MSDN gibi geliştirici topluluğu sitelerine sık katkıda bulunan bir [kullanıcıdır.](/previous-versions/office/developer/office-2007/bb879915(v=office.12)) Birçok teknik yazı ve makalenin yanı sıra Open XML: Explained e-book (Açıklandı e-kitabı) başlıklı bir kitabı da yayımladı.
Wouter, çeşitli kanallardan son teknoloji teknik içerikler sunan Bir Felemenkçe şirket olan Code-Focusing'ın kurucusudur. Wouter hakkında daha fazla bilgi için blog gönderisini okuyun.

Ted Pattison bir MVP SharePoint yazar, eğitmen ve Ted Pattison Grubunun kurucusudur. 2005 yılında Ted, Microsoft'un Geliştirici Platformu Destekçiliği grubu tarafından Windows SharePoint Services 3.0 ve Microsoft Office SharePoint Server 2007 için Ascend geliştirici eğitim müfredatı yazması için işe alındı. O zamandan beri Ted tamamen profesyonel geliştiricileri 2007'de SharePoint odaklanmıştır. Ted, Microsoft Press için Inside Windows SharePoint Services 3.0 başlıklı ve iş çözümlerinin geliştirilmesi için geliştirme platformu olarak SharePoint üzerine odaklanan bir kitap yazmayı tamamladı. Ted ayrıca MSDN Magazine için Office Space başlıklı geliştirici odaklı bir sütun yazar.
