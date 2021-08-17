---
title: SharePoint projeleri için özel dağıtım adımı oluşturma
description: Bu kılavuzda, SharePoint çalıştıran bir sunucuda SharePoint proje çözümlerini yükseltmek için özel bir dağıtım SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 4e445ecbc48abfd91149d45af7adb19eeaa7fe03
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092715"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Adım adım kılavuz: Proje oluşturmak için özel SharePoint oluşturma
  Bir SharePoint dağıtımı Visual Studio dağıtım adımlarını belirli bir sırayla yürütür. Visual Studio birçok yerleşik dağıtım adımı içerir, ancak kendi dağıtım adımlarınızı da oluşturabilirsiniz.

 Bu kılavuzda, SharePoint çalıştıran bir sunucuda çözümleri yükseltmek için özel bir dağıtım adımı SharePoint. Visual Studio, geri alma veya çözüm ekleme gibi birçok görev için yerleşik dağıtım adımları içerir, ancak çözümleri yükseltmek için bir dağıtım adımı dahil etmemektedir. Varsayılan olarak, bir SharePoint dağıtıldığında Visual Studio önce çözümü geri çekin (zaten dağıtılmışsa) ve ardından çözümün tamamını yeniden dağıtır. Yerleşik dağıtım adımları hakkında daha fazla bilgi için bkz. Çözüm [paketlerini dağıtma, yayımlama ve SharePoint yükseltme.](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)

 Bu kılavuz aşağıdaki görevleri gösterir:

- İki ana Visual Studio gerçekleştiren bir uzantı oluşturma:

  - Uzantı, çözümlerini yükseltmek için özel bir dağıtım SharePoint tanımlar.

  - Uzantı, belirli bir proje için yürütülen dağıtım adımları kümesi olan yeni bir dağıtım yapılandırmasını tanımlayan bir proje uzantısı oluşturur. Yeni dağıtım yapılandırması, özel dağıtım adımını ve birkaç yerleşik dağıtım adımını içerir.

- Uzantı derlemesi tarafından SharePoint özel komutlar oluşturun. SharePoint komutları, uzantı derlemeleri tarafından sunucu nesne modelinde API'leri kullanmak üzere çağrıl SharePoint. Daha fazla bilgi için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Derlemelerin her Visual Studio dağıtmak için bir Uzantı (VSIX) paketi oluşturma.

- Yeni dağıtım adımını test etme.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio.

- Visual Studio SDK'sı. Bu kılavuzda, **uzantıyı dağıtmak Project** BIR VSIX paketi oluşturmak için SDK'daki VSIX Project şablonu lanmıştır. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- SharePoint için sunucu nesne modelini kullanma. Daha fazla bilgi için [bkz. SharePoint Foundation Server-Side Nesne Modelini Kullanma.](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))

- SharePoint çözümleri. Daha fazla bilgi için bkz. [Çözümlere Genel Bakış.](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))

- SharePoint yükseltme. Daha fazla bilgi için [bkz. Bir Çözümü Yükseltme.](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14))

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için üç proje oluşturmanız gerekir:

- Uzantıyı dağıtmak için VSIX paketini oluşturmak için bir VSIX projesi.

- Uzantıyı uygulayan bir sınıf kitaplığı projesi. Bu proje 4.5 .NET Framework hedefle çalışmalı.

- Özel uygulama ve komutlarını tanımlayan bir SharePoint projesi. Bu projenin 3.5 .NET Framework hedeflesi gerekir.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

3. Yeni **Project** iletişim kutusunda **Visual C#** veya Visual Basic **düğümlerini** genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > **Genişletilebilirlik düğümü** yalnızca Visual Studio SDK'sı yüklüyse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

4. İletişim kutusunun üst kısmında, .NET Framework sürümleri **listesinden 4.5'i** .NET Framework.

5. **VSIX Project** şablonunu seçin, projeye **UpgradeDeploymentStep** adını ve ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], **UpgradeDeploymentStep projesini** **Çözüm Gezgini.**

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini,** UpgradeDeploymentStep çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **Sürüm'Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** **veya** Visual Basic düğümlerini genişletin ve Windows **seçin.**

3. İletişim kutusunun üst kısmında, .NET Framework sürümleri **listesinden 4.5'i** .NET Framework.

4. Sınıf Kitaplığı **proje şablonunu** seçin, projeye **DeploymentStepExtension adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**DeploymentStepExtension projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint komutu projesini oluşturmak için

1. Bu **Çözüm Gezgini,** UpgradeDeploymentStep çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **Sürüm'Project.**

2. Yeni **Project** iletişim **kutusunda, Visual C#** veya **Visual Basic** genişletin ve ardından Windows **seçin.**

3. İletişim kutusunun üst kısmında, .NET Framework **sürümleri listesinden 3.5'i** .NET Framework.

4. Sınıf Kitaplığı **proje şablonunu** seçin, projeye **SharePointCommands adını ve** ardından Tamam **düğmesini** seçin.

     Visual Studio **SharePointCommands** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Özel dağıtım adımını oluşturmak için kod yazmadan önce, kod dosyaları ve derleme başvuruları eklemeniz ve projeleri yapılandırmanız gerekir.

#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension projesini yapılandırmak için

1. **DeploymentStepExtension projesine** aşağıdaki adlara sahip iki kod dosyası ekleyin:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. DeploymentStepExtension projesinde kısayol menüsünü açın ve Başvuru **Ekle'yi seçin.**

3. Framework **sekmesinde** System.ComponentModel.Composition derlemesi onay kutusunu seçin.

4. Uzantılar **sekmesinde** Microsoft.VisualStudio onay kutusunu seçin. SharePoint ve ardından Tamam **düğmesini** seçin.

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands projesini yapılandırmak için

1. **SharePointCommands projesine** Commands adlı bir kod dosyası ekleyin.

2. Bu **Çözüm Gezgini** **SharePointCommands** proje düğümünde kısayol menüsünü açın ve Başvuru Ekle'yi **seçin.**

3. Uzantılar **sekmesinde,** aşağıdaki derlemeler için onay kutularını seçin ve ardından Tamam **düğmesine** tıklayın

    - Microsoft. SharePoint

    - Microsoft.VisualStudio. SharePoint. Komut

## <a name="define-the-custom-deployment-step"></a>Özel dağıtım adımını tanımlama
 Yükseltme dağıtım adımını tanımlayan bir sınıf oluşturun. Dağıtım adımını tanımlamak için sınıfı arabirimini <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> kullanır. Özel bir dağıtım adımı tanımlamak istediğiniz her durumda bu arabirimi gerçekleştirin.

#### <a name="to-define-the-custom-deployment-step"></a>Özel dağıtım adımını tanımlamak için

1. **DeploymentStepExtension projesinde** UpgradeStep kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra projede bazı derleme hataları olur, ancak sonraki adımlarda kod eklerken bunlar gider.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet1":::

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Özel dağıtım adımını içeren bir dağıtım yapılandırması oluşturma
 Yeni dağıtım yapılandırması için birkaç yerleşik dağıtım adımı ve yeni yükseltme dağıtım adımı içeren bir proje uzantısı oluşturun. Bu uzantıyı oluşturarak, geliştiricilerin SharePoint projelerinde yükseltme dağıtım adımını kullanmaları SharePoint olur.

 Dağıtım yapılandırmasını oluşturmak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> arabirimini kullanır. Bu arabirimi, yeni bir proje uzantısı oluşturmak SharePoint gerçekleştirin.

#### <a name="to-create-the-deployment-configuration"></a>Dağıtım yapılandırmasını oluşturmak için

1. **DeploymentStepExtension projesinde** DeploymentConfigurationExtension kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb" id="Snippet2":::

## <a name="create-the-custom-sharepoint-commands"></a>Özel SharePoint oluşturma
 Veritabanı için sunucu nesne modeline çağıran iki özel SharePoint. Bir komut, bir çözümün zaten dağıtılmış olup olmadığını belirler; diğer komut bir çözümü yükselter.

#### <a name="to-define-the-sharepoint-commands"></a>Komutlarını tanımlamak SharePoint için

1. **SharePointCommands projesinde** Komutlar kod dosyasını açın ve içine aşağıdaki kodu yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet4":::

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, özel dağıtım adımı ve SharePoint kodu artık projelerdedir. Hata olmadan derleyeklerinden emin olmak için bunları derle.

#### <a name="to-build-the-projects"></a>Projeleri oluşturmak için

1. **Çözüm Gezgini**' de, **DeploymentStepExtension** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

2. **SharePointCommands** projesi için kısayol menüsünü açın ve ardından **Oluştur**' u seçin.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSıX projesinde kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**, **UpgradeDeploymentStep** projesi altında, **kaynak. Extension. valtmanifest** dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source. Extension. valtmanifest dosyası, tüm VSıX paketlerinin gerektirdiği uzantı. valtmanifest dosyasının temelini oluşturur. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **ürün adı** kutusuna **SharePoint projeler için yükseltme dağıtım adımını** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **açıklama** kutusunda, **SharePoint projelerinde kullanılabilecek özel bir yükseltme dağıtım adımı sağlar**.

5. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Project** listesinde, **deploymentstepextension**' ı seçin ve ardından **tamam** düğmesini seçin.

9. Bildirim düzenleyicisinde **Yeni** düğmesini yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

10. **Tür** listesinde **SharePoint girin. Commands. v4**.

    > [!NOTE]
    > bu öğe Visual Studio uzantısına eklemek istediğiniz özel bir uzantıyı belirtir. Daha fazla bilgi için bkz. [varlık öğesi (VSX şeması)](/previous-versions/dd393737(v=vs.110)).

11. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

12. **Project** listesinde, **sharepointcommands**' i ve sonra **tamam** düğmesini seçin.

13. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

14. UpgradeDeploymentStep projesi için derleme çıkış klasörünün şimdi UpgradeDeploymentStep. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımını test etmek için hazırlanma
 dağıtım yükseltme adımını test etmek için, önce SharePoint sitesine örnek bir çözüm dağıtmanız gerekir. Visual Studio deneysel örneğinde uzantı hata ayıklaması yaparak başlayın. ardından, dağıtım adımını test etmek için kullanmak üzere bir liste tanımı ve liste örneği oluşturun ve ardından bunları SharePoint sitesine dağıtın. sonra, liste tanımı ve liste örneğini değiştirin ve varsayılan dağıtım işleminin SharePoint sitesindeki çözümlerin üzerine nasıl yazıldığını göstermek için bunları yeniden dağıtın.

 bu kılavuzda daha sonra liste tanımını ve liste örneğini değiştirecek ve sonra SharePoint sitesinde yükselteceksiniz.

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve ardından upgradedeploymentstep çözümünü açın.

2. DeploymentStepExtension projesinde, UpgradeStep kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırına bir kesme noktası ekleyin `CanExecute` `Execute` .

3. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  .

4. Visual Studio, uzantısı%userprofile%\appdata\local\microsoft\visualstudio\11.0exp\extensions\contoso\upgrade dağıtım adımını SharePoint, \ kullanıcı adı 1.0 ' a yükleyecek ve bir Visual Studio deneysel örneğini başlatır. Yükseltme dağıtım adımını bu Visual Studio örneğinde test edersiniz.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>liste tanımı ve liste örneğiyle bir SharePoint projesi oluşturmak için

1. Visual Studio deneysel örneğinde, menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. iletişim kutusunun üst kısmında **.NET Framework 3,5** ' nin .NET Framework sürümleri listesinde göründüğünden emin olun.

    Ve için projeleri için [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .NET Framework gereklidir.

4. proje şablonları listesinde **SharePoint 2010 Project** öğesini seçin, projeyi **employeeslistdefinition** olarak adlandırın ve **tamam** düğmesini seçin.

5. **SharePoint özelleştirme sihirbazında**, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin.

6. **bu SharePoint çözümü için güven düzeyi**' nün altında, **grup çözümü olarak dağıt** seçenek düğmesini seçin.

   > [!NOTE]
   > Yükseltme dağıtımı adımı, korumalı çözümleri desteklemez.

7. **Son** düğmesini seçin.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition projesi oluşturur.

8. EmployeesListDefinition projesi için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

9. **Add New ıtem-employeeslistdefinition** iletişim kutusunda **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

10. **Liste** öğesi şablonunu seçin, öğe **çalışanları listesini** adlandırın ve ardından **Ekle** düğmesini seçin.

     SharePoint özelleştirme sihirbazı görünür

11. **liste Ayarlar seçin** sayfasında, aşağıdaki ayarları doğrulayın ve ardından **son** düğmesini seçin:

    1. **Çalışanlar listesi** **listenizde hangi adı göstermek istiyorsunuz?** kutusunda görüntülenir.

    2. **Özelleştirilebilir liste oluşturma temeli:** seçenek düğmesi seçilir.

    3. **Varsayılan (boş)** , listesine **göre özelleştirilebilir bir liste oluştur** bölümünde seçilir.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir başlık sütunuyla ve tek bir boş örnekle çalışanlar listesi öğesi oluşturur ve liste Tasarımcısını açar.

12. Liste tasarımcısında, **sütunlar** sekmesinde, **Yeni veya var olan bir sütun adı** satırını seçin ve ardından **sütun görünen ad** listesine aşağıdaki sütunları ekleyin:

    1. Ad

    2. Şirket

    3. İş Telefonu

    4. Postadaki

13. Tüm dosyaları kaydedin ve sonra liste tasarımcısını kapatın.

14. **Çözüm Gezgini**, **çalışanlar listesi** düğümünü genişletin ve ardından **Çalışanlar liste örneği** alt düğümünü genişletin.

15. *Elements.xml* dosyasında, bu DOSYADAKI varsayılan XML 'ı aşağıdaki XML ile değiştirin. Bu XML, listenin adını **çalışanlar** olarak değiştirir ve Jim Hance adlı bir çalışana yönelik bilgiler ekler.

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

16. *Elements.xml* dosyasını kaydedin ve kapatın.

17. EmployeesListDefinition projesi için kısayol menüsünü açın ve **Aç** veya **Özellikler**' i seçin.

     Özellikler Tasarımcısı açılır.

18. **SharePoint** sekmesinde, **hata ayıklamadan sonra otomatik olarak geri çek** onay kutusunu temizleyin ve ardından özellikleri kaydedin.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Liste tanımını ve liste örneğini dağıtmak için

1. **Çözüm Gezgini**, **EmployeesListDefinition** proje düğümünü seçin.

2. **Özellikler** penceresinde, **etkin dağıtım yapılandırma** özelliğinin **varsayılan** olarak ayarlandığından emin olun.

3. **F5** tuşunu seçin veya menü çubuğunda Hata **Ayıkla**  >  **Başlat hata** Ayıkla ' yı seçin.

4. projenin başarıyla yapılandırıldığını, web tarayıcısının SharePoint sitesinde açıldığını, hızlı başlatma çubuğundaki **listeler** öğesinin yeni **çalışanlar** listesini içerdiğini ve **çalışanlar** listesinin Jim hance girişini içerdiğini doğrulayın.

5. Web tarayıcısını kapatın.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Liste tanımı ve liste örneğini değiştirmek ve onları yeniden dağıtmak için

1. EmployeesListDefinition projesinde, **çalışan listesi örneği** proje öğesinin bir alt öğesi olan *Elements.xml* dosyasını açın.

2. `Data`Listeden Jim Hance girdisini kaldırmak için öğeyi ve alt öğelerini kaldırın.

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

3. *Elements.xml* dosyasını kaydedin ve kapatın.

4. **Çalışanlar listesi** proje öğesi için kısayol menüsünü açın ve **Aç** veya **Özellikler**' i seçin.

5. Liste tasarımcısında, **Görünümler** sekmesini seçin.

6. **Seçili sütunlar** listesinde, **ekler**' i seçin ve ardından bu sütunu **kullanılabilir sütunlar** listesine taşımak için < anahtarı seçin.

7. **iş Telefon** sütununu **seçili sütunlar** listesinden **kullanılabilir sütunlar** listesine taşımak için önceki adımı tekrarlayın.

     bu eylem, bu alanları SharePoint sitesindeki **çalışanlar** listesinin varsayılan görünümünden kaldırır.

8. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  .

9. **Dağıtım çakışmaları** iletişim kutusunun göründüğünü doğrulayın.

     Visual Studio, çözümün zaten dağıtıldığı bir SharePoint sitesine bir çözüm (liste örneği) dağıtmayı denediğinde bu iletişim kutusu görüntülenir. Bu izlenecek yolda daha sonra yükseltme dağıtımı adımını çalıştırdığınızda bu iletişim kutusu görünmez.

10. **Dağıtım çakışmaları** Iletişim kutusunda **otomatik olarak çözümle** seçenek düğmesini seçin.

     Visual Studio SharePoint sitesindeki liste örneğini siler, proje içindeki liste öğesini dağıtır ve ardından SharePoint sitesini açar.

11. Çalışma **çubuğunun** Listeler Hızlı Başlat Çalışanlar listesini **seçin** ve ardından aşağıdaki ayrıntıları doğrulayın:

    - Ekler **ve** **Giriş Telefon** sütunları listenin bu görünümünde görünmez.

    - Liste boştur. Çözümü yeniden **dağıtmanız** için Varsayılan dağıtım yapılandırmasını  kullandınız. Çalışanlar listesi, projenizin yeni boş listesiyle değiştirilmiştir.

## <a name="test-the-deployment-step"></a>Dağıtım adımını test edin
 Artık yükseltme dağıtım adımını test etmeye hazırsınız. İlk olarak, SharePoint'da liste örneğine bir öğe SharePoint. Ardından liste tanımını ve liste örneğini değiştirebilir, SharePoint sitesinde yükseltin ve yükseltme dağıtım adımının yeni öğenin üzerine yazmaz.

#### <a name="to-manually-add-an-item-to-the-list"></a>Listeye el ile öğe eklemek için

1. SharePoint sitenin şeridinde, Liste Araçları **sekmesinin** altında Öğeler **sekmesini** seçin.

2. Yeni grubunda **Yeni** **Öğe'yi seçin.**

     Alternatif olarak, öğe listesinin **kendisinde Yeni** öğe ekle bağlantısını seçebilirsiniz.

3. Çalışanlar **- Yeni Öğe penceresindeki** Başlık **kutusuna Tesis** Yöneticisi **yazın.**

4. Ad **kutusuna** **Andy girin.**

5. Şirket **kutusuna** Contoso **yazın.**

6. Kaydet **düğmesini** seçin, yeni öğenin listede görüntülendiğinden emin olun ve web tarayıcısını kapatın.

     Bu kılavuzda daha sonra, yükseltme dağıtım adımının bu listenin içeriğinin üzerine yazmaz olduğunu doğrulamak için bu öğeyi kullanacağız.

#### <a name="to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımını test etmek için

1. Visual Studio deneysel örneğinde, **Çözüm Gezgini'da** **EmployeesListDefinition** proje düğümünün kısayol menüsünü açın ve Özellikler'i **seçin.**

    Özellikler Düzenleyicisi/Tasarımcısı açılır.

2. SharePoint **Sekmesinde,** Etkin Dağıtım **Yapılandırması özelliğini Upgrade** olarak **ayarlayın.**

    Bu özel dağıtım yapılandırması, yeni yükseltme dağıtım adımını içerir.

3. Çalışanlar Listesi proje öğesinin kısayol **menüsünü açın** ve özellikler'i veya **Aç'ı** **seçin.**

    Özellikler Düzenleyicisi/Tasarımcısı açılır.

4. Görünümler  sekmesinde **E-posta sütununu** seçin ve ardından bu sütunu Seçili sütunlar listesinden Kullanılabilir sütunlar listesine **<** taşımak için **anahtarı** seçin. 

    Bu eylem, bu alanları sitenin Çalışanlar **listesinin** varsayılan görünümünden SharePoint kaldırır.

5. **F5** anahtarını veya menü çubuğunda Hata AyıklamaYı Başlat'ı seçerek **hata**  >  **ayıklamayı başlatabilirsiniz.**

6. uygulamanın diğer örneğinde yer alan kodun Visual Studio daha önce yönteminde ayar güvenlik kesme noktası üzerinde durduğu `CanExecute` doğrulayın.

7. **F5 tuşuna** tekrar tıklayın veya menü çubuğunda Devam'da Hata **Ayıkla'ya**  >  **tıklayın.**

8. Kodun, yönteminde daha önce ayaranı kesme noktası üzerinde durduğu `Execute` doğrulayın.

9. **F5 tuşuna** basın veya menü çubuğunda Hata Ayıklama Devam'ı  >  **son kez** seçin.

     Web tarayıcısı, SharePoint açar.

10. Çalışma **Alanı'nın** Listeler Hızlı Başlat Çalışanlar **listesini** seçin ve ardından aşağıdaki ayrıntıları doğrulayın:

    - Daha önce el ile ekley istediğiniz öğe (Andy için tesis yöneticisi) listede yer almaktadır.

    - İş **Telefon** ve **E-posta Adresi** sütunları listenin bu görünümünde görünmez.

      Yükseltme  dağıtımı yapılandırması, SharePoint  sitesinde mevcut Employees listesi örneğini değiştirebilir. Yükseltme yapılandırması yerine **Varsayılan** dağıtım yapılandırmasını **kullandıysanız** dağıtım çakışması ile karşılaşırsınız. Visual Studio, Çalışanlar listesini değiştirerek çakışmayı çözer ve tesis yöneticisi Andy'nin öğesi silinir. 

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizleme
 Yükseltme dağıtım adımını test etme işlemini tamamladikten sonra, SharePoint siteden liste örneğini ve liste tanımını kaldırın ve dağıtım adımı uzantısını Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>SharePoint siteden liste örneğini kaldırmak için

1. Henüz **açık** değilse SharePoint sitenin Çalışanlar listesini açın.

2. SharePoint sitenin şeridinde Liste Araçları sekmesini **ve** ardından Liste **sekmesini** seçin.

3. Yeni **Ayarlar** Liste **öğesi'Ayarlar** seçin.

4. İzinler **ve Yönetim'in** altında Bu  listeyi sil komutunu seçin, listeyi geri dönüşüm kutusu onaylamak için Tamam'ı seçin ve ardından web tarayıcısını kapatın. 

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Siteden liste tanımını kaldırmak SharePoint için

1. Deneysel Visual Studio menü çubuğunda Derleme Geri Çek'i   >  **seçin.**

     Visual Studio, liste tanımını SharePoint geri çekmektedir.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde, SharePoint Projeleri için **Dağıtım Adımını Yükselt'i seçin** ve ardından Kaldır **komutunu** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizden emin olmak için Evet'i seçin ve kaldırma işlemini tamamlamak için Şimdi **Yeniden** Başlat'ı seçin. 

4. Her iki Visual Studio (deneysel örnek ve UpgradeDeploymentStep çözümünün açık olduğu Visual Studio örneği) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Paketleme SharePoint dağıtımı genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)