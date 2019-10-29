---
title: SharePoint projeleri için özel dağıtım adımı oluşturma
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0053b279dfdc0fd80608efb7fb663cacf217f1c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984947"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>İzlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma
  Bir SharePoint projesi dağıtırken, Visual Studio belirli bir sırada bir dizi dağıtım adımını yürütür. Visual Studio birçok yerleşik dağıtım adımı içerir, ancak kendi kendinize de oluşturabilirsiniz.

 Bu kılavuzda, SharePoint çalıştıran bir sunucuda çözümleri yükseltmek için özel bir dağıtım adımı oluşturacaksınız. Visual Studio, geri çekiliyor veya çözüm ekleme gibi birçok görev için yerleşik dağıtım adımları içerir, ancak çözümleri yükseltmek için bir dağıtım adımı içermez. Varsayılan olarak, bir SharePoint çözümünü dağıtırken, Visual Studio önce çözümü geri çeker (zaten dağıtılmışsa) ve ardından çözümün tamamını yeniden dağıtır. Yerleşik dağıtım adımları hakkında daha fazla bilgi için bkz. [SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- İki ana görevi gerçekleştiren bir Visual Studio uzantısı oluşturma:

  - Uzantı, SharePoint çözümlerini yükseltmek için özel bir dağıtım adımı tanımlar.

  - Uzantı, belirli bir proje için yürütülen bir dağıtım adımları kümesi olan yeni bir dağıtım yapılandırmasını tanımlayan bir proje uzantısı oluşturur. Yeni dağıtım yapılandırması özel dağıtım adımını ve çeşitli yerleşik dağıtım adımlarını içerir.

- Uzantı derlemesinin çağırdığı iki özel SharePoint komutu oluşturun. SharePoint komutları, SharePoint için sunucu nesne modelinde API 'Leri kullanmak için uzantı derlemeleri tarafından çağrılabilen yöntemlerdir. Daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Her iki derlemeyi dağıtmak için bir Visual Studio uzantısı (VSıX) paketi oluşturma.

- Yeni dağıtım adımını test etme.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio 'nun desteklenen sürümleri.

- Visual Studio SDK 'Sı. Bu izlenecek yol, uzantıyı dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint için sunucu nesne modelini kullanma. Daha fazla bilgi için bkz. [SharePoint Foundation sunucu tarafı nesne modelini kullanma](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- SharePoint çözümleri. Daha fazla bilgi için bkz. [çözümlere genel bakış](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- SharePoint çözümlerini yükseltme. Daha fazla bilgi için bkz. [bir çözümü yükseltme](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Uzantıyı dağıtmak için VSıX paketini oluşturmak üzere bir VSıX projesi.

- Uzantıyı uygulayan bir sınıf kitaplığı projesi. Bu projenin .NET Framework 4,5 ' i hedeflemesi gerekir.

- Özel SharePoint komutlarını tanımlayan bir sınıf kitaplığı projesi. Bu projenin .NET Framework 3,5 ' i hedeflemesi gerekir.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]başlatın.

2. Menü çubuğunda **dosya**  > **Yeni**  > **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda,  **C# Visual** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **Genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'sını yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

5. **VSIX proje** şablonu ' nu seçin, projeyi **UpgradeDeploymentStep**olarak adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **UpgradeDeploymentStep** projesini **Çözüm Gezgini**ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**' de, UpgradeDeploymentStep çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda,  **C# Visual** veya **Visual Basic** düğümlerini genişletin ve sonra **Windows** düğümünü seçin.

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

4. **Sınıf kitaplığı** proje şablonu ' nu seçin, projenin **DeploymentStep uzantısını**adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], **DeploymentStepExtension** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint komut projesini oluşturmak için

1. **Çözüm Gezgini**' de, UpgradeDeploymentStep çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda,  **C# Visual** veya **Visual Basic**öğesini genişletin ve ardından **Windows** düğümünü seçin.

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 3,5** ' ı seçin.

4. **Sınıf kitaplığı** proje şablonu ' nu seçin, projeyi **SharePointCommands**olarak adlandırın ve **Tamam** düğmesini seçin.

     Visual Studio, çözüme **SharePointCommands** projesini ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Özel dağıtım adımını oluşturmak için kod yazmadan önce, kod dosyalarını ve derleme başvurularını eklemeniz ve projeleri yapılandırmanız gerekir.

#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension projesini yapılandırmak için

1. **DeploymentStepExtension** projesinde, aşağıdaki adlara sahip iki kod dosyası ekleyin:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. DeploymentStepExtension projesinde kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Framework** sekmesinde, System. ComponentModel. Composition derlemesinin onay kutusunu seçin.

4. **Uzantılar** sekmesinde, Microsoft. VisualStudio. SharePoint derlemesinin onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands projesini yapılandırmak için

1. **SharePointCommands** projesinde komutları adlı bir kod dosyası ekleyin.

2. **Çözüm Gezgini**' de, **SharePointCommands** proje düğümündeki kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Uzantılar** sekmesinde, aşağıdaki derlemeler için onay kutularını işaretleyin ve ardından **Tamam** düğmesini seçin ' e tıklayın.

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

## <a name="define-the-custom-deployment-step"></a>Özel dağıtım adımını tanımlayın
 Yükseltme dağıtım adımını tanımlayan bir sınıf oluşturun. Dağıtım adımını tanımlamak için, sınıfı <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> arabirimini uygular. Özel bir dağıtım adımı tanımlamak istediğiniz her seferinde bu arabirimi uygulayın.

#### <a name="to-define-the-custom-deployment-step"></a>Özel dağıtım adımını tanımlamak için

1. **DeploymentStepExtension** projesinde, UpgradeStep kod dosyasını açın ve ardından aşağıdaki kodu içine yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olacaktır, ancak sonraki adımlarda kod eklediğinizde bu işlemler kaybolur.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Özel dağıtım adımını içeren bir dağıtım yapılandırması oluşturma
 Yeni dağıtım yapılandırması için, çeşitli yerleşik dağıtım adımlarını ve yeni yükseltme dağıtım adımını içeren bir proje uzantısı oluşturun. Bu uzantıyı oluşturarak SharePoint geliştiricilerinin SharePoint projelerinde dağıtımı Yükselt adımını kullanmasına yardımcı olursunuz.

 Dağıtım yapılandırmasını oluşturmak için, sınıfı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> arabirimini uygular. Her SharePoint Proje uzantısı oluşturmak istediğinizde bu arabirimi uygulayın.

#### <a name="to-create-the-deployment-configuration"></a>Dağıtım yapılandırmasını oluşturmak için

1. **DeploymentStepExtension** projesinde, DeploymentConfigurationExtension kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Özel SharePoint komutlarını oluşturma
 SharePoint için sunucu nesne modeline çağıran iki özel komut oluşturun. Bir komut, bir çözümün zaten dağıtılıp dağıtılmadığını belirler; diğer komut bir çözümü yükseltir.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutlarını tanımlamak için

1. **SharePointCommands** projesinde, komutlar kod dosyasını açın ve ardından aşağıdaki kodu içine yapıştırın.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Mak
 Bu noktada, Özel Dağıtım adımının ve SharePoint komutlarının tüm kodları artık projelerde bulunur. Onları hatasız olarak derlendiklerinden emin olmak için oluşturun.

#### <a name="to-build-the-projects"></a>Projeleri oluşturmak için

1. **Çözüm Gezgini**' de, **DeploymentStepExtension** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

2. **SharePointCommands** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSıX projesinde kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**, **UpgradeDeploymentStep** projesi altında, **kaynak. Extension. valtmanifest** dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. **Ürün adı** kutusuna **SharePoint projeleri Için yükseltme dağıtım adımını**girin.

3. **Yazar** kutusuna **contoso**girin.

4. **Açıklama** kutusuna, **SharePoint projelerinde kullanılabilecek özel bir yükseltme dağıtım adımı sağlar**.

5. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

    > [!NOTE]
    > Bu değer, Extension. valtmanifest dosyasındaki `MefComponent` öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

8. **Proje** listesinde **DeploymentStepExtension**' i seçin ve **Tamam** düğmesini seçin.

9. Bildirim düzenleyicisinde **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

10. **Tür** listesinde, **SharePoint. Commands. v4**girin.

    > [!NOTE]
    > Bu öğe, Visual Studio uzantısına eklemek istediğiniz özel bir uzantıyı belirtir. Daha fazla bilgi için bkz. [varlık öğesi (VSX şeması)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

12. **Proje** listesinde, **SharePointCommands**' i ve sonra **Tamam** düğmesini seçin.

13. Menü çubuğunda **derleme** > **Oluştur çözüm**' ü seçin ve ardından çözümün hatasız derlendiğinden emin olun.

14. UpgradeDeploymentStep projesi için derleme çıkış klasörünün şimdi UpgradeDeploymentStep. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımını test etmek için hazırlanma
 Dağıtım yükseltme adımını test etmek için, önce SharePoint sitesine örnek bir çözüm dağıtmanız gerekir. Visual Studio 'nun deneysel örneğinde uzantı hata ayıklaması yaparak başlayın. Ardından, dağıtım adımını test etmek için kullanılacak bir liste tanımı ve liste örneği oluşturun ve ardından bunları SharePoint sitesine dağıtın. Sonra, liste tanımı ve liste örneğini değiştirin ve varsayılan dağıtım işleminin SharePoint sitesindeki çözümlerin üzerine nasıl yazıldığını göstermek için bunları yeniden dağıtın.

 Bu kılavuzda daha sonra liste tanımını ve liste örneğini değiştirecek ve SharePoint sitesinde yükselteceksiniz.

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. Visual Studio 'Yu yönetici kimlik bilgileriyle yeniden başlatın ve ardından UpgradeDeploymentStep çözümünü açın.

2. DeploymentStepExtension projesinde, UpgradeStep kod dosyasını açın ve sonra `CanExecute` ve `Execute` yöntemlerinde ilk kod satırına bir kesme noktası ekleyin.

3. **F5** tuşunu seçerek veya menü çubuğunda hata **Ayıkla** > hata **ayıklamayı Başlat**' ı seçerek hata ayıklamayı başlatın.

4. Visual Studio, uzantıyı%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade dağıtım adımını SharePoint projeleri0 ' a ve Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde yükseltme dağıtım adımını test edeceksiniz.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Liste tanımıyla ve liste örneğiyle bir SharePoint projesi oluşturmak için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **dosya** > **Yeni** > **projesi**' ni seçin.

2. **Yeni proje** iletişim kutusunda, **görsel C#**  düğümü veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. İletişim kutusunun üst kısmında **.NET Framework 3,5** ' nin .NET Framework sürümleri listesinde göründüğünden emin olun.

    [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] projelerine .NET Framework bu sürümü gerekir.

4. Proje şablonları listesinde **SharePoint 2010 projesi**' ni seçin, projeyi **EmployeesListDefinition**olarak adlandırın ve **Tamam** düğmesini seçin.

5. **SharePoint Özelleştirme Sihirbazı**'nda, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin.

6. **Bu SharePoint çözümünün güven düzeyi nedir**' nin altında, **Grup çözümü olarak dağıt** seçenek düğmesini seçin.

   > [!NOTE]
   > Yükseltme dağıtımı adımı, korumalı çözümleri desteklemez.

7. **Son** düğmesini seçin.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition projesi oluşturur.

8. EmployeesListDefinition projesi için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

9. **Yeni öğe Ekle-EmployeesListDefinition** Iletişim kutusunda **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

10. **Liste** öğesi şablonunu seçin, öğe **çalışanları listesini**adlandırın ve ardından **Ekle** düğmesini seçin.

     SharePoint Özelleştirme Sihirbazı görünür

11. **Liste ayarlarını seçin** sayfasında, aşağıdaki ayarları doğrulayın ve ardından **son** düğmesini seçin:

    1. **Çalışanlar listesi** **listenizde hangi adı göstermek istiyorsunuz?** kutusunda görüntülenir.

    2. **Özelleştirilebilir liste oluşturma temeli:** seçenek düğmesi seçilir.

    3. **Varsayılan (boş)** , listesine **göre özelleştirilebilir bir liste oluştur** bölümünde seçilir.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], bir başlık sütunuyla ve tek bir boş örnekle çalışanlar listesi öğesi oluşturur ve liste Tasarımcısını açar.

12. Liste tasarımcısında, **sütunlar** sekmesinde, **Yeni veya var olan bir sütun adı** satırını seçin ve ardından **sütun görünen ad** listesine aşağıdaki sütunları ekleyin:

    1. Ad

    2. Şirketlerin

    3. İş telefonu

    4. Postadaki

13. Tüm dosyaları kaydedin ve sonra liste tasarımcısını kapatın.

14. **Çözüm Gezgini**, **çalışanlar listesi** düğümünü genişletin ve ardından **Çalışanlar liste örneği** alt düğümünü genişletin.

15. *Elements. xml* dosyasında, bu DOSYADAKI varsayılan XML 'ı aşağıdaki XML ile değiştirin. Bu XML, listenin adını **çalışanlar** olarak değiştirir ve Jim Hance adlı bir çalışana yönelik bilgiler ekler.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. *Elements. xml* dosyasını kaydedin ve kapatın.

17. EmployeesListDefinition projesi için kısayol menüsünü açın ve **Aç** veya **Özellikler**' i seçin.

     Özellikler Tasarımcısı açılır.

18. **SharePoint** sekmesinde, **hata ayıklamadan sonra otomatik olarak geri çek** onay kutusunu temizleyin ve ardından özellikleri kaydedin.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Liste tanımını ve liste örneğini dağıtmak için

1. **Çözüm Gezgini**, **EmployeesListDefinition** proje düğümünü seçin.

2. **Özellikler** penceresinde, **etkin dağıtım yapılandırma** özelliğinin **varsayılan**olarak ayarlandığından emin olun.

3. **F5** tuşunu seçin veya menü çubuğunda Hata **ayıklamayı Başlat** > **Hata Ayıkla** ' yı seçin.

4. Projenin başarıyla yapılandırıldığını, Web tarayıcısının SharePoint sitesine açıldığını, Hızlı Başlatma çubuğundaki **listeler** öğesinin yeni **çalışanlar** listesini Içerdiğini ve **çalışanlar** listesinin Jim Hance girişini içerdiğini doğrulayın.

5. Web tarayıcısını kapatın.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Liste tanımı ve liste örneğini değiştirmek ve onları yeniden dağıtmak için

1. EmployeesListDefinition projesinde, **çalışan listesi örneği** proje öğesinin bir alt öğesi olan *Elements. xml* dosyasını açın.

2. Listeden Jim Hance girdisini kaldırmak için `Data` öğesini ve alt öğelerini kaldırın.

     Bitirdiğinizde, dosya aşağıdaki XML 'yi içermelidir.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. *Elements. xml* dosyasını kaydedin ve kapatın.

4. **Çalışanlar listesi** proje öğesi için kısayol menüsünü açın ve **Aç** veya **Özellikler**' i seçin.

5. Liste tasarımcısında, **Görünümler** sekmesini seçin.

6. **Seçili sütunlar** listesinde, **ekler**' i seçin ve ardından bu sütunu **kullanılabilir sütunlar** listesine taşımak için < anahtarı seçin.

7. **Iş telefonu** sütununu **Seçili sütunlar** listesinden **kullanılabilir sütunlar** listesine taşımak için önceki adımı tekrarlayın.

     Bu eylem, SharePoint sitesindeki **çalışanlar** listesinin varsayılan görünümünden bu alanları kaldırır.

8. **F5** tuşunu seçerek veya menü çubuğunda hata **Ayıkla** > hata **ayıklamayı Başlat**' ı seçerek hata ayıklamayı başlatın.

9. **Dağıtım çakışmaları** iletişim kutusunun göründüğünü doğrulayın.

     Bu iletişim kutusu, Visual Studio çözümün zaten dağıtıldığı bir SharePoint sitesine çözüm (liste örneği) dağıtmayı denediğinde görüntülenir. Bu izlenecek yolda daha sonra yükseltme dağıtımı adımını çalıştırdığınızda bu iletişim kutusu görünmez.

10. **Dağıtım çakışmaları** Iletişim kutusunda **otomatik olarak çözümle** seçenek düğmesini seçin.

     Visual Studio, SharePoint sitesindeki liste örneğini siler, proje içindeki liste öğesini dağıtır ve SharePoint sitesini açar.

11. Hızlı Başlat çubuğunun **listeler** bölümünde **çalışanlar** listesini seçin ve ardından aşağıdaki ayrıntıları doğrulayın:

    - **Ekler** ve **Ev telefonu** sütunları listenin bu görünümünde görünmez.

    - Liste boş. Çözümü yeniden dağıtmak için **varsayılan** dağıtım yapılandırmasını kullandığınızda, **çalışanlar** listesi, projenizdeki yeni boş liste ile değiştirilmiştir.

## <a name="test-the-deployment-step"></a>Dağıtım adımını test etme
 Şimdi yükseltme dağıtım adımını test etmeye hazırsınız. İlk olarak, SharePoint 'te liste örneğine bir öğe ekleyin. Ardından liste tanımını ve liste örneğini değiştirin, SharePoint sitesinde yükseltin ve yükseltme dağıtımı adımının yeni öğenin üzerine yazmaz olduğunu onaylayın.

#### <a name="to-manually-add-an-item-to-the-list"></a>Listeye el ile öğe eklemek için

1. SharePoint sitesindeki şeritte, **Liste araçları** sekmesinde, **öğeler** sekmesini seçin.

2. **Yeni** grupta **Yeni öğe**' yi seçin.

     Alternatif olarak, öğe listesindeki **Yeni öğe Ekle** bağlantısını seçebilirsiniz.

3. **Çalışanlar-yeni öğe** penceresinde, **başlık** kutusuna **tesisler Yöneticisi**' ni girin.

4. **Ad** kutusuna **Andy**yazın.

5. **Şirket** kutusuna **contoso**yazın.

6. **Kaydet** düğmesini seçin, yeni öğenin listede göründüğünü doğrulayın ve ardından Web tarayıcısını kapatın.

     Bu kılavuzda daha sonra bu öğeyi, yükseltme dağıtım adımının bu listenin içeriğinin üzerine yazmayacağı doğrulanacak şekilde kullanacaksınız.

#### <a name="to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımını test etmek için

1. Visual Studio 'nun deneysel örneğinde, **Çözüm Gezgini**' de **EmployeesListDefinition** proje düğümünün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

    Özellikler Düzenleyicisi/tasarımcı açılır.

2. **SharePoint** sekmesinde, **etkin dağıtım yapılandırma** özelliğini **Yükselt**olarak ayarlayın.

    Bu özel dağıtım yapılandırması, yeni yükseltme dağıtım adımını içerir.

3. **Çalışanlar listesi** proje öğesi için kısayol menüsünü açın ve **Özellikler** ' i veya **Aç**' ı seçin.

    Özellikler Düzenleyicisi/tasarımcı açılır.

4. **Görünümler** sekmesinde, **e-posta** sütununu seçin ve ardından bu sütunu **Seçilen sütunlar** listesinden **kullanılabilir sütunlar** listesine taşımak için **<** anahtarını seçin.

    Bu eylem, SharePoint sitesindeki **çalışanlar** listesinin varsayılan görünümünden bu alanları kaldırır.

5. **F5** tuşunu seçerek veya menü çubuğunda hata **Ayıkla** > hata **ayıklamayı Başlat**' ı seçerek hata ayıklamayı başlatın.

6. Visual Studio 'nun diğer örneğindeki kodun, `CanExecute` yönteminde daha önce ayarladığınız kesme noktasında durduğunu doğrulayın.

7. **F5** tuşunu yeniden seçin veya menü çubuğunda **Hata Ayıkla** > **devam et**' i seçin.

8. Kodun, daha önce `Execute` yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın.

9. **F5** tuşunu seçin veya menü çubuğunda **Hata Ayıkla** ' yı seçin > son saate **devam edin** .

     Web tarayıcısı, SharePoint sitesini açar.

10. Hızlı başlatma alanının **listeler** bölümünde **çalışanlar** listesini seçin ve ardından aşağıdaki ayrıntıları doğrulayın:

    - Daha önce el ile eklediğiniz öğe (Andy, Tesis Yöneticisi için) listede hala vardır.

    - **Iş telefonu** ve **e-posta adresi** sütunları listenin bu görünümünde görünmez.

      **Yükseltme** dağıtımı yapılandırması, SharePoint sitesindeki mevcut **çalışanlar** listesi örneğini değiştirir. **Yükseltme** yapılandırması yerine **varsayılan** dağıtım yapılandırmasını kullandıysanız, bir dağıtım çakışması ile karşılaşırsınız. Visual Studio, **çalışanlar** listesini değiştirerek çakışmayı çözerek, tesislerin ve tesis yöneticisinin silineceği öğesi silinir.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Dağıtım yükseltme adımını test etmeyi tamamladıktan sonra, SharePoint sitesinden liste örneğini ve liste tanımını kaldırın ve dağıtım adımı uzantısını Visual Studio 'dan kaldırın.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Liste örneğini SharePoint sitesinden kaldırmak için

1. Liste zaten açık değilse SharePoint sitesindeki **çalışanlar** listesini açın.

2. SharePoint sitesindeki şeritte, **Liste araçları** sekmesini seçin ve ardından **liste** sekmesini seçin.

3. **Ayarlar** grubunda, **Liste ayarları** öğesini seçin.

4. **İzinler ve yönetim**altında **Bu listeyi Sil** komutunu seçin, listeyi geri dönüşüm kutusu 'na göndermek istediğinizi onaylamak için **Tamam** ' ı seçin ve ardından Web tarayıcısını kapatın.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Liste tanımını SharePoint sitesinden kaldırmak için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **derleme** > **geri çek**' i seçin.

     Visual Studio, SharePoint sitesinden liste tanımını geri çeker.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **araçlar** > **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, **SharePoint projeleri Için dağıtım adımını Yükselt**' i seçin ve ardından **Kaldır** komutunu seçin.

3. Açılan iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** ' i seçin ve kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** ' ı seçin.

4. Visual Studio 'nun her iki örneğini (deneysel örnek ve UpgradeDeploymentStep çözümünün açık olduğu Visual Studio örneği) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
