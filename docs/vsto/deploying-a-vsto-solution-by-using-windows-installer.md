---
title: Windows Yükleyici'yi Kullanarak Office Çözümü için Visual Studio Araçları Dağıtma
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 876781cb6967f5d10dddccd54a46e218170445ab
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432366"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Windows Yükleyici'yi Kullanarak Office Çözümü için Visual Studio Araçları Dağıtma

## <a name="summary"></a>Özet

Visual Studio Installer projesini kullanarak Office için Microsoft Visual Studio Tools (VSTO) eklentisini veya belge düzeyinde çözümü nasıl dağıttığınızı öğrenin.

Wouter van Vugt, Kod Danışmanı

Ted Pattison, Ted Pattison Grubu

Bu makale, microsoft tarafından özgün yazarların izniyle güncelleştirildi.

**Aşağıdakiler için geçerlidir:** Office, Microsoft Office, Microsoft Visual Studio için Görsel Stüdyo Araçları.

## <a name="overview"></a>Genel Bakış

Bir VSTO çözümü geliştirebilir ve bir Windows Installer paketi kullanarak çözümü dağıtabilirsiniz. Bu tartışma, basit bir Office Eklentisi dağıtma adımları içerir.

## <a name="deployment-methods"></a>Dağıtım Yöntemleri

ClickOnce, Eklentileriniz ve çözümleriniz için kurulumlar oluşturmak için kolayca kullanılabilir. Ancak, makine düzeyinde Eklentiler gibi yönetim ayrıcalıkları gerektiren Eklentiler yükleyebilir.

Yönetim ayrıcalıkları gerektiren eklentiler Windows Installer kullanılarak yüklenebilir, ancak kurulumu oluşturmak için daha fazla çaba gerekir.

ClickOnce'i kullanarak VSTO çözümünün nasıl dağıtılanabildiğini öğrenmek için [bkz.](deploying-an-office-solution-by-using-clickonce.md)

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>VSTO çalışma süresini hedefleyen Office çözümlerini dağıtma

ClickOnce ve Windows Installer paketleri, Office çözümlerini yüklerken aynı temel görevleri yapmak zorunda.

1. Önkoşul bileşenlerini kullanıcı bilgisayarına yükleyin.
2. Çözüm için belirli bileşenleri dağıtın.
3. Eklentiler için kayıt defteri girişleri oluşturun.
4. Yürütmesine izin vermek için çözüme güvenin.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Hedef Bilgisayarda Gerekli ÖnKoşul Bileşenleri

VSTO çözümlerini çalıştırmak için bilgisayara yüklenmesi gereken yazılımların listesi aşağıda verilmiştir:

- Microsoft Office 2010 veya daha yeni.
- Microsoft .NET Framework 4 veya daha yeni.
- Office Runtime için Microsoft Visual Studio 2010 Araçları.
  Çalışma süresi, Eklentileri ve belge düzeyindeçözümleri yöneten bir ortam sağlar. Runtime'ın bir sürümü Microsoft Office ile birlikte gönderilmektedir, ancak eklentinizle belirli bir sürümü yeniden dağıtmak isteyebilirsiniz.
- Gömülü Interop Türleri kullanmıyorsanız, Microsoft Office için Birincil Interop derlemeleri.
- Projeler tarafından başvurulan tüm yardımcı programlar derlemeleri.

### <a name="specific-components-for-the-solution"></a>Çözüm için Özel Bileşenler

Yükleyici paketi bu bileşenleri kullanıcının bilgisayarına yüklemelidir:

- Belge düzeyinde bir çözüm oluşturursanız, Microsoft Office belgesi.
- Özelleştirme derlemesi ve gerektirdiği tüm derlemeler.
- Yapılandırma dosyaları gibi ek bileşenler.
- Uygulama bildirimi (.manifest).
- Dağıtım bildirimi (.vsto).

### <a name="registry-entries-for-add-ins"></a>Eklentiler için Kayıt Defteri Girişleri

Microsoft Office, Eklentileri bulmak ve yüklemek için kayıt defteri girişlerini kullanır. Bu kayıt defteri girişleri dağıtım işleminin bir parçası olarak oluşturulmalıdır. Bu kayıt defteri girişleri hakkında daha fazla bilgi [için, VSTO Eklentileri için Kayıt Defteri girişlerine](registry-entries-for-vsto-add-ins.md)bakın.

Özel form bölgelerini görüntüleyen Outlook Eklentileri, form bölgelerinin tanımlanmasına izin veren ek kayıt defteri girişleri gerektirir. Kayıt defteri girişleri hakkında daha fazla bilgi için [Bkz. Outlook form bölgeleri için Kayıt Defteri girişleri.](registry-entries-for-vsto-add-ins.md#OutlookEntries)

Belge düzeyindeki çözümler herhangi bir kayıt defteri girişi gerektirmez. Bunun yerine, belgeiçindeki özellikler özelleştirmeyi bulmak için kullanılır. Bu özellikler hakkında daha fazla bilgi için Bkz. [Özel Belge Özellikleri Genel Bakış.](custom-document-properties-overview.md)

### <a name="trusting-the-vsto-solution"></a>VSTO Çözümüne Güvenmek

Özelleştirmenin çalışması için, bir çözüme makine tarafından güvenilmesi gerekir. Eklenti, manifestoyu bir sertifikayla imzalayarak, ekleme listesiyle güven ilişkisi oluşturarak veya makinede güvenilir bir konuma yükleyerek güvenilir olabilir.

İmzalama için nasıl sertifika alacağıhakkında daha fazla bilgi için [ClickOnce Dağıtım ve Authenticode](../deployment/clickonce-and-authenticode.md)bölümüne bakın. Çözümlere güvenme hakkında daha fazla bilgi [için, Dahil Etme Listelerini Kullanarak Office Çözümlerine Güvenme'ye](trusting-office-solutions-by-using-inclusion-lists.md)bakın. Windows Installer dosyanızda özel bir eylem içeren bir dahil etme listesi girişi ekleyebilirsiniz. İçerme listesini etkinleştirme hakkında daha fazla bilgi için [bkz.](how-to-configure-inclusion-list-security.md)

Her iki seçenek de kullanılmazsa, çözüme güvenip güvenmemeye karar vermelerine izin vermek için kullanıcıya bir güven istemi görüntülenir.

Belge düzeyindeki çözümlerle ilgili güvenlik hakkında daha fazla bilgi [için belgelere güven verme 'ye](granting-trust-to-documents.md)bakın.

## <a name="creating-a-basic-installer"></a>Temel Yükleyici Oluşturma

Kurulum ve Dağıtım proje şablonları, indirilebilen [Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) uzantısıile birlikte verilir.

Office çözümü için yükleyici oluşturmak için şu görevlerin gerçekleştirilmesi gerekir:

- Dağıtılacak Office Çözümü bileşenlerini ekleyin.
- Uygulama düzeyindeki Eklentiler için kayıt defteri anahtarlarını yapılandırın.
- Ön koşul bileşenlerini, son kullanıcı bilgisayarlarına yüklenebilecek şekilde yapılandırın.
- Gerekli ön koşul bileşenlerinin kullanılabilir olup olmadığını doğrulamak için başlatma koşullarını yapılandırın. Gerekli tüm ön koşullar yüklenmezse yüklemeyi engellemek için başlatma koşulları kullanılabilir.

İlk adım kurulum projesi oluşturmaktır.

### <a name="to-create-the-addin-setup-project"></a>AddIn Kurulumu projesini oluşturmak için

1. Dağıtmak istediğiniz Office AddIn Projesini açın. Bu örnekte, ExcelAddIn adlı bir Excel Eklentisi kullanıyoruz.
2. Office Project Open ile **Dosya** menüsünde, **Ekle'yi** genişletin ve yeni bir proje eklemek için **Yeni Proje'yi** tıklatın.
::: moniker range="=vs-2017"
3. Yeni **Proje Ekle** iletişim kutusunda, Proje **türleri bölmesindeki** **Diğer Proje Türlerini** genişletin, ardından **Kurulum ve Dağıtım'ı** genişletin ve ardından Visual **Studio Installer'ı**seçin.
4. **Şablonlar** bölmesinde, **Visual Studio yüklü** şablonlar grubundan Kurulum **Projesi'ni** seçin.
::: moniker-end
::: moniker range="=vs-2019"
3. Yeni **Proje Ekle** iletişim **kutusunda, Kurulum Projesi** şablonu'nu seçin.
4. **İleri**'ye tıklayın.
::: moniker-end

5. **Ad** kutusuna **OfficeAddInSetup**yazın.
::: moniker range="=vs-2017"
6. Yeni kurulum projesini oluşturmak için **Aç'ı** tıklatın.
::: moniker-end
::: moniker range="=vs-2019"
6. Yeni kurulum projesini oluşturmak için **Oluştur'u** tıklatın.
::: moniker-end

Visual Studio, yeni kurulum projesi için Dosya Sistemi Gezgini'ni açar. Dosya Sistemi Gezgini, kurulum projesine dosya eklemenize olanak tanır.

   ![Kurulum projesi için Dosya Sistemi Gezgini ekran görüntüsü](media/setup-project-figure-1.png)

   **Şekil 1: Kurulum projesi için Dosya Sistemi Gezgini**

Kurulum projesinin ExcelAddIn'i dağıtması gerekir. Bu görev için kurulum projesini kurulum projesine ExcelAddIn proje çıktısını ekleyerek yapılandırabilirsiniz.

### <a name="to-add-the-exceladdin-project-output"></a>ExcelAddIn proje çıktısını eklemek için

1. Çözüm **Gezgini'nde** **OfficeAddInSetup'ı**sağ tıklatın, **Ekle'yi** tıklatın ve ardından **Proje Çıktısı'nı**tıklatın.
2. Proje **Çıktı Grubu Ekle** iletişim kutusunda, proje listesinden **ExcelAddIn'i** ve **Birincil Çıktı'yı**seçin.
3. Proje çıktısını kurulum projesine eklemek için **Tamam'ı** tıklatın.

    ![Kurulum Projesi Proje Çıktı Grubu Ekle iletişim kutusunun ekran görüntüsü](media/setup-project-figure-2.png)

    **Şekil 2: Kurulum Projesi Proje Çıktı Grubu Ekle iletişim kutusu**

Kurulum projesinin dağıtım bildirimini ve uygulama bildirimini dağıtması gerekir. Bu iki dosyayı ExcelAddIn projesinin çıktı klasöründen tek başına dosya olarak kurulum projesine ekleyin.

### <a name="to-add-the-deployment-and-application-manifests"></a>Dağıtım ve uygulama bildirimlerini eklemek için

1. Çözüm **Gezgini'nde** **OfficeAddInSetup'ı**sağ tıklatın, **Ekle'yi**tıklatın ve **Dosya'yı**tıklatın.
2. Dosyaları **Ekle** iletişim kutusunda, **ExcelAddIn** çıktı dizine gidin. Genellikle çıktı dizini, seçili yapı yapılandırması bağlı olarak proje kök dizininin **depo\\gözü yayımı** alt klasörüdür.
3. **ExcelAddIn.vsto** ve **ExcelAddIn.dll.manifest** dosyalarını seçin ve bu iki dosyayı kurulum projesine eklemek için **Aç'ı** tıklatın.

    ![Solution Explorer'da Uygulama ve dağıtım bildirimlerinin ekran görüntüsü](media/setup-project-figure-3.jpg)

    **Şekil 3: Eklenti Çözüm Gezgini için uygulama ve dağıtım bildirimleri**

ExcelAddIn'e başvurmak, ExcelAddIn'in gerektirdiği tüm bileşenleri içerir. Bu bileşenler, doğru kaydedilebilmeleri için ön koşul paketleri kullanılarak dışlanmalıdır ve dağıtılmalıdır. Ayrıca, yükleme başlamadan önce Yazılım Lisans Koşulları görüntülenmeli ve kabul edilmelidir.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>ExcelAddIn proje bağımlılıklarını hariç tutmak için

1. **OfficeAddInSetup** düğümünde **Çözüm Gezgini'nde,** **Microsoft .NET Framework** veya 'ile biten derleme ler dışında Algılanan **Bağımlılıklar** öğesinin altındaki tüm bağımlılık öğelerini ** \*seçin. Utilities.dll**. Yardımcı Programlar derlemeleri, uygulamanızla birlikte dağıtılmak üzeredir.
2. Gruba sağ tıklayın ve **Özellikler'i**seçin.
3. **Özellikler** penceresinde, bağımlı **Exclude** derlemeleri kurulum projesinden hariç tutmak için **Özelliği True** olarak değiştirin. Yardımcı Programlar derlemelerini hariç tutmadığından emin olun.

    ![Dışlanmak üzere bağımlılıkları gösteren Çözüm Gezgini ekran görüntüsü](media/setup-project-figure-4.jpg)

    **Şekil 4: Bağımlılıkları hariç**

Windows Installer paketinizi, bootstrapper olarak da bilinen bir Kurulum programı ekleyerek ön koşul bileşenlerini yükecek şekilde yapılandırabilirsiniz. Bu kurulum programı önkoşul bileşenleri, bootstrapping denilen bir işlem yükleyebilirsiniz.

**ExcelAddIn**için, Eklenti'nin düzgün çalıştırılaabilmesi için bu ön koşulların yüklenmesi gerekir:

- Office Solution'ın hedeflenen Microsoft .NET Framework sürümü.
- Office Runtime için Microsoft Visual Studio 2010 Araçları.

Bağımlı bileşenleri ön koşul olarak yapılandırmak için

1. Çözüm **Gezgini'nde** **OfficeAddInSetup** projesini sağ tıklatın ve **Özellikler'i**seçin.
2. **OfficeAddInSetup Özellik Sayfaları** iletişim kutusu görüntülenir.
3. **Önkoşullar** düğmesini tıklatın.
4. Önkoşullar iletişim kutusunda ,.NET Framework'ün doğru sürümünü ve Office Runtime için Microsoft Visual Studio Tools'u seçin.

    ![Önkoşullar İletişim Kutusu Ekran Görüntüsü](media/setup-project-figure-5.png)

    **Şekil 5: Önkoşullar İletişim Kutusu**

    > [!NOTE]
    >Visual Studio Kurulum Projenizde yapılandırılan ön koşul paketlerinden bazıları seçili yapı yapılandırmasına bağlıdır. Kullandığınız her yapı yapılandırması için doğru ön koşul bileşenlerini seçmeniz gerekir.

Microsoft Office, kayıt defteri anahtarlarını kullanarak Eklentileri bulur. HKEY\_CURRENT\_USER kovanındaki anahtarlar, her bir kullanıcı için eklentiyi kaydetmek için kullanılır. HKEY\_LOCAL\_MACHINE kovanınaltındaki anahtarlar, eklentiyi makinenin tüm kullanıcıları için kaydetmek için kullanılır. Kayıt defteri anahtarları hakkında daha fazla bilgi için [VSTO Eklentileri için Kayıt Defteri girişlerine](registry-entries-for-vsto-add-ins.md)bakın.

### <a name="to-configure-the-registry"></a>Kayıt defterini yapılandırmak için

1. Çözüm **Gezgini'nde** **OfficeAddInSetup'ı**sağ tıklatın.
2. **Görünümü**Genişlet.
3. Kayıt defteri düzenleyicisi penceresini açmak için **Kayıt Defteri'ni** tıklatın.
4. **Registry (OfficeAddInSetup)** düzenleyicisinde, **\_HKEY\_LOCAL MACHINE'i** ve ardından **Yazılım'ı**genişletin.
5. **HKEY\_LOCAL\_\\MACHINE Software**altında bulunan ** \[Üretici\]**?tuşu silin.
6. **Genişlet\_HKEY\_CURRENT USER** ve sonra **Yazılım**.
7. **HKEY\_CURRENT\_\\KULLANICI Yazılımı**altında bulunan ** \[\] Üretici** anahtarını silin.
8. Eklenti yüklemesi için kayıt defteri anahtarları eklemek için **Kullanıcı/Makine Kovan** tuşuna sağ tıklayın, **Yeni Anahtar'ı**seçin. Yeni anahtarın adı için **metin Yazılımı'nı** kullanın. Yeni oluşturulan **Yazılım** anahtarına sağ tıklayın ve **Microsoft**metniyle yeni bir anahtar oluşturun.
9. Eklenti kaydı için gereken tüm anahtar hiyerarşisini oluşturmak için benzer bir işlem kullanın:

    **Kullanıcı / Makine\\\\Hive\\\\Yazılım Microsoft\\\\Office Excel Addins SampleCompany.ExcelAddIn**

    Şirket Adı genellikle teklik sağlamak için eklentiadı için bir önek olarak kullanılır.

10. **SampleCompany.ExcelAddIn** tuşuna sağ tıklayın, **Yeni'yi**seçin ve **String değerini**tıklatın. Ad için **Açıklama** metnini kullanın.
11. Üç değer daha eklemek için bu adımı kullanın:
    - **FriendlyName** türü **String** adı
    - **DWORD** türünün Yük Davranışı **DWORD**
    - **Tip** **String'in bildirimi**

12. Kayıt defteri düzenleyicisinde **Açıklama** değerini sağ tıklatın ve **Özellikler Penceresi'ni**tıklatın. Özellikler **Penceresinde,** Değer özelliği için **Excel Demo AddIn** girin.
13. Kayıt defteri düzenleyicisinde **FriendlyName** anahtarını seçin. Özellikler **Penceresinde,** **Değer** özelliğini **Excel Demo AddIn**olarak değiştirin.
14. Kayıt defteri düzenleyicisinde **LoadBehavior** anahtarını seçin. Özellikler **Penceresinde,** **Değer** özelliğini **3 olarak değiştirin.** LoadBehavior için değer 3 eklenti ana bilgisayar uygulamasının başında yüklenmesi gerektiğini gösterir. Yük davranışı hakkında daha fazla bilgi [için, VSTO Eklentileri için Kayıt Defteri girişlerine](registry-entries-for-vsto-add-ins.md)bakın.

15. Kayıt defteri düzenleyicisinde **Manifest** anahtarını seçin. Özellikler **Penceresinde,** **Değer** özelliğini **dosya:///[TARGETDIR]ExcelAddIn.vsto|vstolocal** olarak değiştirin

    ![Kayıt Defteri Düzenleyicisinin Ekran Görüntüsü](media/setup-project-figure-6.png)

    **Şekil 6: Kayıt defteri anahtarlarını ayarlama**

      VSTO çalışma süresi, dağıtım bildirimini bulmak için bu kayıt defteri anahtarını kullanır. [TARGETDIR] makrosu, eklentinin yüklü olduğu klasörle değiştirilir. Makro son \ karakterini içerecek, bu nedenle dağıtım bildiriminin dosya adı \ karakteri olmadan ExcelAddIn.vsto olmalıdır.
      **Vstolocal** postfix, VSTO çalışma zamanı eklentisinin ClickOnce önbelleği yerine bu konumdan yüklenmesi gerektiğini söyler. Bu düzeltmenin kaldırılması, çalışma zamanının özelleştirmeyi ClickOnce önbelleğine kopyalamasına neden olur.

   >[!WARNING]
   >Visual Studio'daki Kayıt Defteri Editörü'ne çok dikkat etmelisiniz. Örneğin, yanlışlıkla DeleteAtUninstall'ı yanlış anahtar için ayarlarsanız, kayıt defterinin etkin bir bölümünü silebilir ve kullanıcı bilgisayarını tutarsız veya daha da kötüsü bozuk bir durumda bırakabilirsiniz.

Office'in 64 bit sürümleri eklentileri aramak için 64 bit kayıt defteri kovanı kullanır. Eklentileri 64 bit kayıt kovanının altına kaydetmek için kurulum projesinin hedef platformunun yalnızca 64 bit olarak ayarlanabilmesi gerekir.

1. Çözüm gezgininde **OfficeAddInSetup** projesini seçin.
2. **Özellikler** penceresine gidin ve **TargetPlatform** özelliğini **x64**olarak ayarlayın.

Office'in hem 32 bit hem de 64 bit sürümleri için bir Eklenti yüklemek, iki ayrı MSI paketi oluşturmanızı gerektirir. Biri 32 bit, diğeri 64 bit.

  ![64 bit Office'e Eklentiler kaydetmek için Hedef Platformu gösteren Özellikler Penceresiekran görüntüsü](media/setup-project-figure-7.jpg)

  **Şekil 7: Eklentileri 64 bit Office'e kaydetmek için Hedef Platform**

MSI paketi Eklenti'yi veya çözümü yüklemek için kullanılırsa, gerekli ön koşullar yüklenmeden yüklenebilir. Ön koşullar yüklenmezse Eklenti'nin yüklenmesini engellemek için MSI'daki Başlatma Koşullarını kullanabilirsiniz.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>VSTO Çalışma Süresini algılamak için bir başlatma koşulunu yapılandırma

1. Çözüm **Gezgini'nde** **OfficeAddInSetup'ı**sağ tıklatın.
2. **Görünümü**Genişlet.
3. **Başlatma Koşulları'nı**tıklatın.
4. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, **Hedef Makine'de Gereksinimler'e**sağ tıklayın ve ardından **Kayıt Defteri Başlatma Koşulu Ekle'yi**tıklatın. Bu arama koşulu, VSTO çalışma zamanının yükleştirdiği bir anahtar için kayıt defterinde arama yapabilir. Anahtarın değeri daha sonra adlandırılmış bir özellik aracılığıyla yükleyicinin çeşitli parçaları için kullanılabilir. Başlatma koşulu, belirli bir değeri denetlemek için arama koşulu tarafından tanımlanan özelliği kullanır.
5. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, **Kayıt Defteri Arama1** arama koşulunu seçin, koşulu sağ tıklatın ve **Özellikler Penceresi'ni**seçin.

6. **Özellikler** penceresinde, şu özellikleri ayarlayın:
   1. **(Ad)** değerini **VSTO 2010 Çalışma Süresini Ara**olarak ayarlayın.
   2. **Mülkün** değerini **VSTORUNTIMEREDIST**olarak değiştirin.
   3. Microsoft **\\VSTO Runtime\\Setup\\v4R** için **RegKey** değerini ayarlayın
   4. **Root** özelliğini **vsdrrHKLM**olarak ayarlayın.
   5. **Değer** özelliğini **Sürüm**olarak değiştirin.

7. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, **Koşul1** başlatma koşulunu seçin, koşulu sağ tıklatın ve **Özellikler Penceresi'ni**seçin.
8. Özellikler penceresinde, şu özellikleri ayarlayın:
   1. **(Adı)** **VSTO 2010 Çalışma Zamanı kullanılabilirliğini doğrulamak**için ayarlayın.
   2. **Koşulun** değerini **\>VSTORUNTIMEREDIST ="10.0.30319"** olarak değiştirin
   3. **InstallURL** özelliğini boş bırakın.
   4. **Office** **Runtime için Visual Studio 2010 Araçları'na İleti'yi ayarlayın yüklü değil. Eklentiyi yüklemek için lütfen Setup.exe'yi çalıştırın.**

        ![Çalışma Zamanı Kullanılabilirliğini Doğrula başlatma durumu için Özellikler Penceresinin ekran görüntüsü](media/setup-project-figure-8.jpg)

        **Şekil 8: Çalışma Zamanı Kullanılabilirliğini Doğrula başlatma koşulu için Özellikler Penceresi**

 Yukarıdaki başlatma koşulu, bootstrapper paketi tarafından yüklendiğinde VSTO çalışma zamanının varlığını açıkça denetler.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Office tarafından yüklenen VSTO Çalışma Süresini algılamak için bir başlatma koşulunu yapılandırma

1. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, **Sağ tıklayarak Hedef Arama Makinesi'ni**tıklatın ve ardından **Kayıt Defteri Arama**ekle'yi tıklatın.
2. Kayıt **Defteri Için AramaGiriş1** arama koşulunu seçin, koşulu sağ tıklatın ve **Özellikler Penceresi'ni**seçin.
3. **Özellikler** penceresinde, şu özellikleri ayarlayın:
    1. **(Ad)** değerini Office **VSTO Runtime'ı aramak için**ayarlayın.
    2. **Mülkün** değerini **OfficeRuntime**olarak değiştirin.
    3. Microsoft **\\VSTO Runtime\\Setup\\v4**için **RegKey** değerini ayarlayın.
    4. **Root** özelliğini **vsdrrHKLM**olarak ayarlayın.
    5. **Değer** özelliğini **Sürüm**olarak değiştirin.

4. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, daha önce tanımlanan **VSTO 2010 Çalışma Zamanı kullanılabilirliğini doğrula** düğmesini seçin, koşulu sağ tıklatın ve **Özellikler Penceresi'ni**seçin.

5. **Durum** özelliğinin değerini **VSTORUNTIMEREDIST \>="10.0.30319" VEYA MEMURUNTIME\>="10.0.21022"** olarak değiştirin. Eklentinizin gerektirdiği çalışma zamanının sürümlerine bağlı olarak sürüm numaraları sizin için belki de farklıdır.

    ![Başlatma durumu için Windows Özellikleri ekran görüntüsü](media/setup-project-figure-9.jpg)
  
    **Şekil 9: Redist veya Office başlatma koşulu yla Çalışma Zamanı Kullanılabilirliğini Doğrula'yı Doğrulamak için Windows özellikleri**

Bir Eklenti .NET Framework 4'ü veya daha yeniyi hedefliyorsa, başvurulan Birincil Interop Derlemeleri (PIA) içindeki türler VSTO derlemesine katıştılabilir.

Interop Türlerinin Eklentinize gömülü pönce olup olmayacağını aşağıdaki adımları gerçekleştirerek denetlemek için:

1. Çözüm Gezgini'nde Başvuru Düğümü'ni genişletme
2. Örneğin, **Office**PIA başvurularından birini seçin.
3. F4 tuşuna basarak veya Derlemeler bağlam menüsünden Özellikler'i seçerek özellikler pencerelerini görüntüleyin.
4. Özelliğin değerini kontrol **Et Embed Interop Türleri**.

Değer **True**olarak ayarlanmışsa, Türler katıştırılmış olur ve kurulum projesi bölümünü [**oluşturmak için**](#to-build-the-setup-project) aşağı atlayabilirsiniz.

Daha fazla bilgi için [Bkz. Tür Eşdeğerliği ve Gömülü Interop Türleri](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Office PI'leri için bunu algılamak için başlatma koşullarını yapılandırmak için

1. Başlatma **Koşulları(OfficeAddInSetup)** düzenleyicisinde, **Hedef Makine'de Gereksinimler'e**sağ tıklayın ve ardından **Windows Installer Başlat Koşulunu Ekle'yi tıklatın.** Bu başlatma koşulu, belirli bileşen kimliğini arayarak bir Office PIA'yı arar.
2. **Bileşen1 için Ara'yı** sağ tıklatın ve başlatma koşulunun özelliklerini göstermek için **Özellikler Penceresi'ni** tıklatın.
3. Özellikler **Penceresinde,** bu özellikleri ayarlayın:

    1. **(Ad)** özelliğinin değerini **Office Paylaşılan PIA'yı Arama** olarak değiştirme
    2. Kullanmakta olduğunuz Office bileşeni için **Bileşen Kimliği'nin** değerini Bileşen Kimliği olarak değiştirin. **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}** gibi bileşen kimliklerinin listesini aşağıdaki tabloda bulabilirsiniz.
    3. **Özellik** özelliğinin değerini **HASSHAREDPIA**olarak değiştirin.

4. Başlatma **Koşulları (OfficeAddInSetup)** düzenleyicisinde, **Koşul1'i** sağ tıklatın ve başlatma koşulunun özelliklerini göstermek için **Özellikler Penceresi'ni** tıklatın.

5. **Koşul1'in**bu özelliklerini değiştirin:

    1. **(Adı)** Office **Paylaşılan PIA kullanılabilirliğini doğrulamak**için değiştirin.
    2. **Durumu** **HASSHAREDPIA**olarak değiştirin.
    3. **InstallUrl'yi** boş bırakın.
    4. Excel ile etkileşim için **gerekli** bileşen İletiyi **değiştirin kullanılamıyor. Lütfen setup.exe çalıştırın.**

    ![Office Paylaşılan PIA başlatma koşulu için Özellikler Penceresinin ekran görüntüsü](media/setup-project-figure-10.jpg)
  
    **Şekil 10: Office Paylaşılan PIA başlatma koşulu doğrula özellikleri penceresi**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Microsoft Office için Birincil Interop Derlemelerinin Bileşen Kimlikleri

|Birincil interop montajı|Office 2010|Office 2013|Office 2013 (64 bit)|Office 2016|Office 2016 (64 bit)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Formlar 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Akıllı Etiket|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office Paylaşılan|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Son başlatma koşullarının ekran görüntüsü](media/setup-project-figure-11.jpg)

  **Şekil 11: Son fırlatma koşulları**

ExcelAddIn yüklemesi için başlatma koşullarını daha da hassaslaştırabilirsiniz. Örneğin, gerçek hedef Office uygulamasının yüklü olup olmadığını denetlemek yararlı olabilir.

### <a name="to-build-the-setup-project"></a>Kurulum projesini oluşturmak için

1. Çözüm **Gezgini'nde** **OfficeAddInSetup** projesini sağ tıklatın ve **Oluştur'u**tıklatın.
2. **Windows Gezgini'ni**kullanarak, **OfficeAddInSetup** projesinin çıktı dizinine gidin ve seçili yapı yapılandırmasına bağlı olarak Sürüm veya Hata Ayıklama klasörüne gidin. Klasördeki tüm dosyaları kullanıcıların erişebileceği bir konuma kopyalayın.

ExcelAddIn kurulumını sınamak için

1. **OfficeAddInSetup'ı** kopyaladığınız konuma gidin.
2. **OfficeAddInSetup** eklentisini yüklemek için setup.exe dosyasına çift tıklayın. Görünen tüm Yazılım Lisans Koşullarını kabul edin ve eklentiyi kullanıcı bilgisayarına yüklemek için kurulum sihirbazını tamamlayın.

Excel Office çözümü kurulum sırasında belirtilen konumdan yüklemeli ve çalıştırılmalıdır.

## <a name="additional-requirements-for-document-level-solutions"></a>Belge Düzeyinde Çözümler için Ek Gereksinimler

Belge düzeyinde çözümlerin dağıtılması, Windows Yükleyici kurulum projesinde birkaç farklı yapılandırma adımı gerektirir.

Belge düzeyinde bir çözüm dağıtmak için gereken temel adımların bir listesi aşağıda veda edebilirsiniz:

- Visual Studio Kurulum Projesini oluşturun.
- Belge düzeyi çözümünüzün birincil çıktısını ekleyin. Birincil çıktı, Microsoft Office belgesini de içerir.
- Dağıtım ve uygulama gevşek dosya olarak tezahürleri ekleyin.
- Bağımlı bileşenleri yükleyici paketinden hariç taçık (yardımcı programlar derlemeleri hariç).
- Ön koşul paketlerini yapılandırın.
- Başlatma koşullarını yapılandırın.
- Kurulum projesini oluşturun ve sonuçları dağıtım konumuna kopyalayın.
- Kurulumu gerçekleştirerek belge düzeyindeki çözümü kullanıcı bilgisayarına dağıtın.
- Gerekirse özel belge özelliklerini güncelleştirin.

### <a name="changing-the-location-of-the-deployed-document"></a>Dağıtılan Belgenin Konumunu Değiştirme

Office belgesinin içindeki özellikler, belge düzeyi çözümlerini bulmak için kullanılır. Belge VSTO derlemesi ile aynı klasöre yüklenmişse, değişiklik gerekmez. Ancak, farklı klasöre yüklenmişse, bu özelliklerin kurulum sırasında güncelleştirilmesi gerekir.

Bu belge özellikleri hakkında daha fazla bilgi için Bkz. [Özel Belge Özellikleri Genel Bakış.](custom-document-properties-overview.md)

Bu özellikleri değiştirmek için kurulum sırasında özel bir eylem kullanmanız gerekir.

Aşağıdaki örnekte ExcelWorkbookProject adlı belge düzeyinde bir çözüm ve ExcelWorkbookSetup adlı bir kurulum projesi kullanır. ExcelWorkbookSetup projesi, kayıt defteri anahtarlarını ayarlamak dışında yukarıda özetlenen adımlar kullanılarak yapılandırılır.

Visual Studio çözümünüze özel eylem projesini eklemek için

1. **Çözüm** Gezgini'ndeki **Office Belge Dağıtım Projesi'ni** sağ tıklayarak çözüme yeni bir .NET Console projesi ekleme
2. **Ekle'yi** genişletin ve **Yeni Proje'yi**tıklatın.
3. Konsol Uygulaması şablonunu seçin ve projeye **AddCustomizationCustomAction**adını girin.

    ![Çözüm Explorer ekran görüntüsü - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Şekil 12: Çözüm Gezgini - AddCustomizationCustomAction**

4. Bu derlemelere başvuru ekleyin:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Bu kodu Program.cs veya Program.vb olarak kopyalayın

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

Belgeye özelleştirmeeklemek için VSTO belge düzeyindeki çözümünüzün çözüm kimliğine sahip olmanız gerekir. Bu değer Visual Studio proje dosyasından alınır.

Çözüm kimliğini almak için

1. **Yapı** menüsünde, belge düzeyinde çözüm oluşturmak ve çözüm kimliği özelliğini proje dosyasına eklemek için **Çözüm Oluştur'u** tıklatın.
2. Çözüm **Gezgini'nde,** belge düzeyindeki proje **ExcelWorkbookProject'e** sağ tıklayın
3. Visual Studio'nun içinden proje dosyasına erişmek için **Project'i Boşalt'ı** tıklatın.

    ![Çözüm Gezgini Unloading Excel Belge Çözümü Ekran Görüntüsü](media/setup-project-figure-16.jpg)

    **Şekil 13: Excel Belge Çözümünü Boşaltma**

4. Çözüm **Gezgini'nde** **ExcelWorkbookProject'e** sağ tıklayın ve **ExcelWorkbookProject.vbproj'u edin** veya **ExcelWorkbookProject.csproj'u edit'i**tıklatın.
5. **ExcelWorkbookProject** düzenleyicisinde, **SolutionID** öğesini **PropertyGroup** öğesinin içinde bulun.
6. Bu öğenin GUID değerini kopyalayın.

    ![SolutionID'nin Alınması](media/setup-project-figure-17.jpg)

    **Şekil 14: SolutionID'nin alınması**

7. Çözüm **Gezgini'nde** **ExcelWorkbookProject'e** sağ tıklayın ve **Project'i Yeniden Yükle'yi**tıklatın.
8. **ExcelWorkbookProject** düzenleyicisini kapatmak için görünen iletişim kutusunda **Evet'i** tıklatın.
9. **Çözüm Kimliği,** Özel Yükleme Eyleminde kullanılacaktır.

Son adım, **Yükle** ve **Kaldır** adımları için özel eylemi yapılandırmaktır.

### <a name="to-configure-the-setup-project"></a>Kurulum projesini yapılandırmak için

1. Çözüm **Gezgini'nde,** **ExcelWorkbookSetup'ı**sağ tıklatın, **Ekle'yi** genişletin ve **Proje Çıktısı'nı**tıklatın.
2. Proje **Çıktı Grubu Ekle** iletişim kutusunda, **Proje** listesinde **AddCustomizationCustomAction'ı**tıklatın.
3. İletişim kutusunu kapatmak ve kurulum projesine özel eylemi içeren derlemeyi eklemek için **Birincil Çıktı'yı** seçin ve **Tamam'ı** tıklatın.

    ![Belge Bildirimi Özel Eyleminin Ekran Görüntüsü - Proje Çıktı Grubu Ekle penceresi](media/setup-project-figure-18.jpg)

    **Şekil 15: Belge Bildirimi Özel Eylem - Proje Çıktı Grubu Ekle**

4. Çözüm **Gezgini'nde** **ExcelWorkbookSetup'ı**sağ tıklatın.
5. **Görünümü** Genişletin ve **Özel Eylemler'i**tıklatın.
6. Özel **Eylemler (ExcelWorkbookSetup)** düzenleyicisinde, **Özel Eylemler'e** sağ tıklayın ve **Özel Eylem Ekle'yi**tıklatın.
7. Project iletişim kutusunda **Öğeseç'de,** **Ara** listesinde **Uygulama Klasörü'nü**tıklatın. **AddCustomizationCustomAction'dan Birincil Çıktı'yı (etkin)** seçin ve Yükle adımına özel eylemi eklemek için **Tamam'ı** tıklatın.
8. Install **düğümünün**altında, **AddCustomizationCustomAction'dan Birincil çıktıyı**sağ tıklatın ve **Yeniden Adlandır'ı**tıklatın. Özel eylem **Belgelerim'e belgeyi kopyala ve özelleştirme ekle.**
9. Kaldır **düğümünün**altında, **AddCustomizationCustomAction(Etkin)'den Birincil çıktıyı** sağ tıklatın ve **Yeniden Adlandır'ı**tıklatın. Özel eylemi adlandırın **Belgeler klasöründen belgeyi kaldırın.**

    ![Belge Bildirimi Özel Eylemler penceresinin ekran görüntüsü](media/setup-project-figure-19.jpg)

    **Şekil 16: Belge Bildirimi Özel Eylemleri**

10. Özel **Eylemler (ExcelWorkbookSetup)** düzenleyicisinde, **Belgelerimi Kopyala'yı** sağ tıklatın ve özelleştirme ekleme ve **Özellikler Penceresi'ni**tıklatın.
11. **CustomActionData** **Properties** penceresinde, özelleştirme DLL'sinin konumunu, dağıtım bildirimini ve Microsoft Office belgesinin konumunu girin. SolutionID de gereklidir.
12. Herhangi bir kurulum hatasını bir dosyaya günlüğe kaydetmek istiyorsanız, logfile parametresi ekleyin.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Belgeyi Belgelerimin Özellikleripencerene Kopyalamak Için Özel Eylemin Ekran Görüntüsü](media/setup-project-figure-20.jpg)

    **Şekil 17: Belgelerimi Belgelerime Kopyalamak Için Özel Eylem**

13. Kaldırma için Özel Eylem belgenin adı gerekir, **Bunu CustomActionData** aynı belgeKonum parametresini kullanarak sağlayabilirsiniz

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. **ExcelWorkbookSetup** projesini derleyip dağıtın.
15. **Belgelerimle** klasöre bakın ve ExcelWorkbookProject.xlsx dosyasını açın.

## <a name="additional-resources"></a>Ek Kaynaklar

[Nasıl yapılır: Office Runtime için Visual Studio Araçlarını Yükleyin](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office Birincil Birlikte Çalışma Derlemeleri](office-primary-interop-assemblies.md)

[VSTO Eklentileri için kayıt defteri girişleri](registry-entries-for-vsto-add-ins.md)

[Özel Belge Özelliklerine Genel Bakış](custom-document-properties-overview.md)

[Windows Kayıt Defterinde Form Bölgelerini Belirtme](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Belgelere Güven Verme](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Yazarlar Hakkında

Wouter van Vugt, Office Open XML teknolojileri ve SharePoint, Microsoft Office ve ilgili .NET teknolojileri ile Office İş Uygulamaları (OBA) oluşturmaya odaklanan bağımsız bir danışman ile Microsoft MVP'sidir.
[Wouter, OpenXmlDeveloper.org](http://openxmldeveloper.org/) ve [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12))gibi geliştirici topluluk sitelerine sık sık katkıda bulunmaktadır. O birkaç teknik bildiri ve makaleler yanı sıra açık XML başlıklı satırda mevcut bir kitap yayınladı: Açık e-kitap.
Wouter, çeşitli kanallar aracılığıyla en ileri teknik içerik sunmaya odaklanan Hollandalı bir şirket olan Code-Counsel'ın kurucusudur. Onun blogunu okuyarak ve [Code-Counsel Web sitesini](http://www.code-counsel.net/)ziyaret ederek Wouter hakkında daha fazla bilgi edinebilirsiniz.

Ted Pattison, SharePoint MVP'si, yazarı, eğitmeni ve Ted Pattison Group'un kurucusudur. 2005 sonbaharında Ted, Microsoft'un Geliştirici Platformu Evangelizm grubu tarafından Windows SharePoint Services 3.0 ve Microsoft Office SharePoint Server 2007 için Ascend geliştirici eğitim müfredatını yazar olarak işe alındı. O zamandan beri Ted, sharepoint 2007 teknolojileri konusunda profesyonel geliştiricileri eğitmeye odaklanmıştır. Ted, Microsoft Press için Inside Windows SharePoint Services 3.0 adlı bir kitap yazmayı bitirdi ve sharepoint'in iş çözümleri oluşturmak için geliştirme platformu olarak nasıl kullanılacağına odaklandı. Ted ayrıca MSDN Magazine için Office Space başlıklı geliştirici odaklı bir köşe yazısı yazıyor.
