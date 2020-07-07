---
title: 'İzlenecek yol: SharePoint Proje uzantısı oluşturma | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df10e2da9e6b4c31894dce0669e9aa0e580b92f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015073"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>İzlenecek yol: SharePoint Proje uzantısı oluşturma
  Bu izlenecek yol, SharePoint projeleri için bir uzantı oluşturmayı gösterir. Projenin eklenmesi, silinmesi veya yeniden adlandırılması gibi proje düzeyindeki olaylara yanıt vermek için bir proje uzantısı kullanabilirsiniz. Ayrıca bir özellik değeri değiştiğinde özel özellikler ekleyebilir veya yanıt verebilirsiniz. Proje öğesi uzantılarının aksine, proje uzantıları belirli bir SharePoint proje türüyle ilişkilendirilemez. Bir proje uzantısı oluşturduğunuzda uzantı, içinde herhangi bir tür SharePoint projesi açıldığında yüklenir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Bu kılavuzda, içinde oluşturulan herhangi bir SharePoint projesine eklenen özel bir Boole özelliği oluşturacaksınız [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . **True**olarak ayarlandığında, yeni özellik projenize bir görüntü kaynak klasörü ekler veya bunları eşler. **False**olarak ayarlandığında, varsa Resimler klasörü kaldırılır. Daha fazla bilgi için bkz. [nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint projeleri için aşağıdakileri yapan bir uzantı oluşturma:

  - Özellikler penceresi özel bir proje özelliği ekler. Özelliği herhangi bir SharePoint projesi için geçerlidir.

  - Bir projeye eşlenmiş klasör eklemek için SharePoint proje nesne modelini kullanır.

  - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Projedeki eşlenmiş bir klasörü silmek için Otomasyon nesne modeli 'ni (DTE) kullanır.

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Proje özelliğinin uzantı derlemesini dağıtmak için uzantı (VSIX) paketi oluşturma.

- Proje özelliğini hata ayıklama ve test etme.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint ve ' nin desteklenen sürümleri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu izlenecek yol, **VSIX Project** [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] Proje özelliği uzantısını DAĞıTMAK üzere bir VSIX paketi oluşturmak Için içindeki VSIX proje şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için iki proje oluşturmanız gerekir:

- Proje uzantısını dağıtmak için VSıX paketi oluşturmak üzere bir VSıX projesi.

- Proje uzantısını uygulayan bir sınıf kitaplığı projesi.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > Bu düğüm yalnızca Visual Studio SDK 'sını yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin ve ardından **VSIX proje** şablonunu seçin.

5. **Ad** kutusuna **Projecbir sionpackage**girin ve **Tamam** düğmesini seçin.

     **Projecbir Sionpackage** projesi **Çözüm Gezgini**görüntülenir.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **Windows**' u seçin.

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' i seçin ve ardından **sınıf kitaplığı** proje şablonu ' nu seçin.

4. **Ad** kutusuna **ProjectExtension**yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]çözüme **ProjectExtension** projesini ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-project"></a>Projeyi yapılandırma
 Proje uzantısını oluşturmak için kod yazmadan önce, uzantı projesine kod dosyalarını ve derleme başvurularını ekleyin.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. ProjectExtension projesine **CustomProperty** adlı bir kod dosyası ekleyin.

2. **ProjectExtension** projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Başvuru Yöneticisi-CustomProperty** Iletişim kutusunda **Framework** düğümünü seçin ve ardından System. ComponentModel. Composition ve System. Windows. Forms derlemelerinin yanındaki onay kutusunu işaretleyin.

4. **Uzantılar** düğümünü seçin, Microsoft. VisualStudio. SharePoint ve EnvDTE derlemelerinin yanındaki onay kutusunu işaretleyin ve ardından **Tamam** düğmesini seçin.

5. **Çözüm Gezgini**, **ProjectExtension** projesi Için **Başvurular** klasörü altında **EnvDTE**öğesini seçin.

6. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğini **yanlış**olarak değiştirin.

## <a name="define-the-new-sharepoint-project-property"></a>Yeni SharePoint proje özelliğini tanımlayın
 Proje uzantısını ve yeni proje özelliğinin davranışını tanımlayan bir sınıf oluşturun. Yeni proje uzantısını tanımlamak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> arabirimini uygular. Bir SharePoint projesi için uzantı tanımlamak istediğinizde bu arabirimi uygulayın. Ayrıca, <xref:System.ComponentModel.Composition.ExportAttribute> sınıfını sınıfına ekleyin. Bu öznitelik [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , uygulamanızı bulmayı ve yüklemeyi sağlar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>Türü özniteliğin oluşturucusuna geçirin.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Yeni SharePoint proje özelliğini tanımlamak için

1. Aşağıdaki kodu CustomProperty kod dosyasına yapıştırın.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Çözümü derleme
 Sonra, hata olmadan derlendiğinden emin olmak için çözümü derleyin.

#### <a name="to-build-the-solution"></a>Çözümü oluşturmak için

1. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Proje özelliği uzantısını dağıtmak için bir VSıX paketi oluşturma
 Proje uzantısını dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSIX projesinde bulunan kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**, Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dosyayı bildirim tasarımcısında açar. **Meta veriler** sekmesinde görüntülenen bilgiler **Uzantılar ve güncelleştirmeler**' de görünür. Tüm VSıX paketleri. valtmanifest dosyası uzantısını gerektirir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. **Ürün adı** kutusuna **özel proje özelliği**girin.

3. **Yazar** kutusuna **contoso**girin.

4. **Açıklama** kutusunda, **görüntüler kaynak klasörünün eşlemesine geçiş yapan özel bir SharePoint proje özelliği**girin.

5. **Varlıklar** sekmesini seçin ve ardından **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

    > [!NOTE]
    > Bu değer, `MEFComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **geçerli çözüm ' de bir proje** seçin seçenek düğmesini seçin.

8. **Proje** listesinde **ProjectExtension**öğesini seçin.

     Bu değer, projede oluşturmakta olduğunuz derlemenin adını tanımlar.

9. **Yeni varlık Ekle** iletişim kutusunu kapatmak için **Tamam ' ı** seçin.

10. Menü çubuğunda, bitirdiğinizde **Dosya**  >  **Tümünü Kaydet** ' i seçin ve ardından bildirim tasarımcısını kapatın.

11. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin ve ardından projenin hatasız derlendiğinden emin olun.

12. **Çözüm Gezgini**, **Projecbir sionpackage** projesi için kısayol menüsünü açın ve **Dosya Gezgini 'nde klasörü aç** düğmesini seçin.

13. **Dosya Gezgini**' nde Projecbir sionpackage projesi için derleme çıktı klasörünü açın ve ardından klasörün Projec, sionpackage. vsix adlı bir dosya içerdiğini doğrulayın.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-project-property"></a>Proje özelliğini test etme
 Artık özel proje özelliğini test etmeye hazırsınız. Deneysel örneğinde yeni proje özelliği uzantısının hata ayıklaması ve test olması en kolay yoldur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu örneği [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , BIR VSIX veya başka bir genişletilebilirlik projesi çalıştırdığınızda oluşturulur. Projede hata ayıkladıktan sonra, uzantıyı sisteminize yükleyebilir ve sonra normal bir örneğinde hata ayıklamaya ve test etmeye devam edebilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Visual Studio 'nun deneysel örneğinde uzantı hatalarını ayıklamak ve test etmek için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yönetici kimlik bilgileriyle yeniden başlatın ve ardından Projecbir Sionpackage çözümünü açın.

2. **F5** tuşunu seçerek veya menü çubuğunda hata ayıklama **Debug**  >  **Başlat hata**Ayıkla ' yı seçerek projenizin hata ayıklama derlemesini başlatın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]uzantıyı%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1.0 dizinine yükleyerek deneysel bir örneğini başlatır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. Deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir Grup çözümü için bir SharePoint projesi oluşturun ve sihirbazdaki diğer değerler için varsayılan değerleri kullanın.

    1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

    2. **Yeni proje** iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 3,5** ' ı seçin.

         SharePoint Araç Uzantıları, uygulamasının bu sürümünde özellikleri gerektirir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. **Şablonlar** düğümü altında, **Visual C#** veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü seçin ve ardından **2010** düğümünü seçin.

    4. **SharePoint 2010 proje** şablonunu seçin ve ardından **ModuleTest** ' i projenizin adı olarak girin.

4. **Çözüm Gezgini**' de **ModuleTest** projesi düğümünü seçin.

     Yeni bir özel özellik **eşleme görüntüleri klasörü** , varsayılan değeri **false**olan **Özellikler** penceresinde görünür.

5. Bu özelliğin değerini **true**olarak değiştirin.

     Bir görüntüler kaynak klasörü SharePoint projesine eklenir.

6. Bu özelliğin değerini yeniden **false**olarak değiştirin.

     **Görüntüler klasörünü sil** Iletişim kutusunda **Evet** düğmesini seçerseniz, görüntüler kaynak klasörü SharePoint projesinden silinir.

7. Deneysel örneğini kapatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint projelerini genişletme](../sharepoint/extending-sharepoint-projects.md)
- [Nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [SharePoint proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint Araç Uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
