---
title: 'adım adım kılavuz: SharePoint Project Uzantısı | Microsoft Docs'
description: Proje SharePoint, silindiğinde veya yeniden adlandırıldı gibi proje düzeyindeki olaylara yanıt vermek için kullanabileceğiniz bir proje uzantısı oluşturun.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6db7829524b43718d8c41afa7792b86bc589c75c7874bc2e447f9093d4016370
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244231"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Adım adım kılavuz: SharePoint proje uzantısı oluşturma
  Bu kılavuzda, projelerde uzantı oluşturma SharePoint göstermektedir. Proje ekleniyor, siliniyor veya yeniden adlandırıldı gibi proje düzeyindeki olaylara yanıt vermek için bir proje uzantısı kullanabilirsiniz. Ayrıca özel özellikler ekleyebilir veya bir özellik değeri değiştiklerine yanıt veebilirsiniz. Proje öğesi uzantılarının aksine, proje uzantıları belirli bir proje türüyle SharePoint olamaz. Bir proje uzantısı 7.SharePoint 000.00000000000000000000000000000000000000000000000000000000000 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]

 Bu kılavuzda, içinde oluşturulan herhangi bir uygulama projesine eklenen özel bir Boole SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturabilirsiniz. True olarak **ayarlanırsa,** yeni özellik projenize bir Images kaynak klasörü ekler veya eşler. False olarak **ayarlanırsa** Images klasörü kaldırılır (varsa). Daha fazla bilgi için, [bkz. How to: add and remove mapped folders](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Bu kılavuz aşağıdaki görevleri gösterir:

- Aşağıdaki adımları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint projeleri için uzantı oluşturma:

  - Özel proje özelliğini özel bir Özellikler penceresi. özelliği herhangi bir proje için SharePoint geçerlidir.

  - Bir SharePoint eşlenmiş klasör eklemek için proje nesne modelini kullanır.

  - Projeden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eşlenen bir klasörü silmek için otomasyon nesne modelini (DTE) kullanır.

- Proje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özelliğinin uzantı derlemesini dağıtmak için bir Uzantı (VSIX) paketi oluşturma.

- Proje özelliği hata ayıklama ve test etme.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] sürümleri, SharePoint ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu kılavuzda, proje özelliği **Project** bir VSIX paketi oluşturmak için vsIX paket şablonu [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] 1. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için iki proje oluşturmanız gerekir:

- Proje uzantısını dağıtmak için VSIX paketini oluşturmak için bir VSIX projesi.

- Proje uzantısını uygulayan bir sınıf kitaplığı projesi.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >  

3. Yeni **Project** iletişim kutusunda **Visual C#** **veya** Visual Basic genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > Bu düğüm yalnızca Visual Studio SDK'sı yüklüyse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri **listesinden .NET Framework 4.5'i** seçin ve ardından **VSIX** Project seçin.

5. Ad **kutusuna** **ProjectExtensionPackage yazın** ve tamam **düğmesini** seçin.

     **ProjectExtensionPackage projesi,** **Çözüm Gezgini.**

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** veya Visual Basic **düğümlerini** genişletin ve sonra **Windows.**

3. İletişim kutusunun üst kısmında, **.NET Framework listesinden .NET Framework 4.5'i** seçin ve ardından Sınıf Kitaplığı proje **şablonunu** seçin.

4. Ad **kutusuna** **ProjectExtension yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectExtension projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-project"></a>Projeyi yapılandırma
 Proje uzantısını oluşturmak için kod yazmadan önce, uzantı projesine kod dosyaları ve derleme başvuruları ekleyin.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. ProjectExtension projesine **CustomProperty** adlı bir kod dosyası ekleyin.

2. **ProjectExtension projesinin kısayol menüsünü açın** ve Başvuru Ekle'yi **seçin.**

3. Başvuru **Yöneticisi - CustomProperty** iletişim kutusunda **Çerçeve** düğümünü seçin ve ardından System.ComponentModel.Composition ve System'in yanındaki onay kutusunu seçin. Windows. Derlemeleri oluşturur.

4. Uzantılar **düğümünü** seçin, Microsoft.VisualStudio'nun yanındaki onay kutusunu işaretleyin. SharePoint ve EnvDTE derlemelerini seçin ve ardından Tamam **düğmesini** seçin.

5. Bu **Çözüm Gezgini,** **ProjectExtension** **projesinin** Başvurular klasörünün altında **EnvDTE'yi seçin.**

6. Özellikler penceresinde **Birlikte** Çalışma Türleri Ekle **özelliğini** False olarak **değiştirin.**

## <a name="define-the-new-sharepoint-project-property"></a>Yeni SharePoint özelliğini tanımlama
 Proje uzantısını ve yeni proje özelliğinin davranışını tanımlayan bir sınıf oluşturun. Sınıfı, yeni proje uzantısını tanımlamak için arabirimini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> kullanır. Yeni bir proje için uzantı tanımlamak istediğiniz her durumda bu SharePoint gerçekleştirin. Ayrıca <xref:System.ComponentModel.Composition.ExportAttribute> sınıfa ekleyin. Bu öznitelik, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uygulamanızı bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> özniteliğin oluşturucus una ilet.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Yeni SharePoint özelliğini tanımlamak için

1. Aşağıdaki kodu CustomProperty kod dosyasına yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs" id="Snippet1":::

## <a name="build-the-solution"></a>Çözümü derleme
 Ardından, hatasız derlenmiş olduğundan emin olmak için çözümü derle.

#### <a name="to-build-the-solution"></a>Çözümü derlemek için

1. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Proje özelliği uzantısını dağıtmak için VSIX paketi oluşturma
 Proje uzantısını dağıtmak için çözümünüzde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak, VSIX projesine dahil edilen source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından, çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX paketini yapılandırmak ve oluşturmak için

1. Bu **Çözüm Gezgini** source.extension.vsixmanifest dosyasının kısayol menüsünü açın ve aç **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosyayı bildirim tasarımcısında açar. Meta Veriler sekmesinde görüntülenen **bilgiler,** Uzantılar ve **Güncelleştirmeler'de de görünür.** Tüm VSIX paketleri extension.vsixmanifest dosyasını gerektirir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna Özel** Uygulama Özelliği **Project girin.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna** Images kaynak **klasörünün projeyle SharePoint geçişli** özel bir SharePoint proje özelliği girin.

5. Varlıklar **sekmesini** ve ardından Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

6. Tür **listesinde** **Microsoft.VisualStudio.MefComponent'ı seçin.**

    > [!NOTE]
    > Bu değer `MEFComponent` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe VSIX paketinde bir uzantı derlemenin adını belirtir. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Kaynak **listesinde** Geçerli çözümde **proje seçeneğini belirleyin.**

8. Yeni **Project** **ProjectExtension'ı seçin.**

     Bu değer, projede derlemekte olduğunu derlemenin adını tanımlar.

9. Yeni **Varlık** Ekle iletişim **kutusunu kapatmak için Tamam'ı** seçin.

10. Menü çubuğunda, **bitirişte Dosya**  >  **Tüm Dosyaları** Kaydet'i seçin ve ardından bildirim tasarımcısını kapatın.

11. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve projenin hatasız derlenmiş olduğundan emin olun.

12. Bu **Çözüm Gezgini** **ProjectExtensionPackage** projesinin kısayol menüsünü açın ve Klasör Aç düğmesini **Dosya Gezgini** seçin.

13. Bu **Dosya Gezgini** ProjectExtensionPackage projesinin derleme çıkış klasörünü açın ve ardından klasörde ProjectExtensionPackage.vsix adlı bir dosya olduğunu doğrulayın.

     Varsayılan olarak, derleme çıkış klasörü . Proje dosyanızı içeren klasörün altında \bin\Debug klasörü.

## <a name="test-the-project-property"></a>Proje özelliğini test etmek
 Artık özel proje özelliğini test etmeye hazır oluruz. Deneysel bir örneğinde yeni proje özelliği uzantısında hata ayıklamak ve test etmek en kolay [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yöntemdir. Bu örneği [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , BIR VSIX veya başka bir genişletilebilirlik projesi çalıştırdığınızda oluşturulur. Projede hata ayıkladıktan sonra, uzantıyı sisteminize yükleyebilir ve sonra normal bir örneğinde hata ayıklamaya ve test etmeye devam edebilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Visual Studio deneysel örneğinde uzantı hatalarını ayıklamak ve test etmek için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yönetici kimlik bilgileriyle yeniden başlatın ve ardından Projecbir Sionpackage çözümünü açın.

2. **F5** tuşunu seçerek veya menü çubuğunda hata ayıklama   >  **Başlat hata** Ayıkla ' yı seçerek projenizin hata ayıklama derlemesini başlatın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]uzantıyı%userprofile%\appdata\local\microsoft\visualstudio\11.0exp\extensions\contoso\custom Project property\1.0 dizinine yükleyip deneysel bir örneğini başlatır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. deneysel örneğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir grup çözümü için bir SharePoint projesi oluşturun ve sihirbazdaki diğer değerler için varsayılan değerleri kullanın.

    1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

    2. **yeni Project** iletişim kutusunun en üstünde .NET Framework sürümleri listesinde **.NET Framework 3,5** ' i seçin.

         SharePoint araç uzantıları bu sürümünde özellikleri gerektirir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. **şablonlar** düğümü altında, **Visual C#** veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü seçin ve ardından **2010** düğümünü seçin.

    4. **SharePoint 2010 Project** şablonunu seçin ve ardından **moduletest** ' i projenizin adı olarak girin.

4. **Çözüm Gezgini**' de **ModuleTest** projesi düğümünü seçin.

     Yeni bir özel özellik **eşleme görüntüleri klasörü** , varsayılan değeri **false** olan **Özellikler** penceresinde görünür.

5. Bu özelliğin değerini **true** olarak değiştirin.

     bir görüntüler kaynak klasörü SharePoint projesine eklenir.

6. Bu özelliğin değerini yeniden **false** olarak değiştirin.

     **görüntüler klasörünü sil** iletişim kutusunda **evet** düğmesini seçerseniz, SharePoint projesinden görüntüler kaynak klasörü silinir.

7. Deneysel örneğini kapatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint projelerini genişlet](../sharepoint/extending-sharepoint-projects.md)
- [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [SharePoint proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [özel verileri SharePoint araçları uzantılarıyla ilişkilendir](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)