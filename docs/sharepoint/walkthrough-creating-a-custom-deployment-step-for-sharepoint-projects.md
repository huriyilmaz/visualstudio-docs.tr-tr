---
title: SharePoint projeleri için özel dağıtım adımı oluşturma
description: bu kılavuzda, SharePoint çalıştıran bir sunucuda SharePoint proje çözümlerini yükseltmek için özel bir dağıtım adımı oluşturun.
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
ms.openlocfilehash: 88345c673543093ba0af71c5c28c69507d87d330ce74ac50b199385484b2a250
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121331955"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma
  bir SharePoint projesi dağıtırken Visual Studio belirli bir sırada bir dizi dağıtım adımını yürütür. Visual Studio birçok yerleşik dağıtım adımı içerir, ancak kendi kendinize de oluşturabilirsiniz.

 Bu kılavuzda, SharePoint çalıştıran bir sunucuda çözümleri yükseltmek için özel bir dağıtım adımı oluşturacaksınız. Visual Studio, geri çekiliyor veya çözüm ekleme gibi birçok görev için yerleşik dağıtım adımları içerir, ancak çözümleri yükseltmek için bir dağıtım adımı içermez. varsayılan olarak, bir SharePoint çözümü dağıttığınızda Visual Studio, önce çözümü geri çeker (zaten dağıtılmışsa) ve sonra çözümün tamamını yeniden dağıtır. yerleşik dağıtım adımları hakkında daha fazla bilgi için bkz. [SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- iki ana görevi gerçekleştiren bir Visual Studio uzantısı oluşturma:

  - uzantı SharePoint çözümlerini yükseltmek için özel bir dağıtım adımı tanımlar.

  - Uzantı, belirli bir proje için yürütülen bir dağıtım adımları kümesi olan yeni bir dağıtım yapılandırmasını tanımlayan bir proje uzantısı oluşturur. Yeni dağıtım yapılandırması özel dağıtım adımını ve çeşitli yerleşik dağıtım adımlarını içerir.

- uzantı derlemesinin çağırdığı iki özel SharePoint komut oluşturun. SharePoint komutlar, SharePoint için sunucu nesne modelinde apı 'leri kullanmak üzere uzantı derlemeleri tarafından çağrılabilen yöntemlerdir. daha fazla bilgi için bkz. [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).

- derlemelerin her ikisini de dağıtmak için bir Visual Studio uzantısı (vsıx) paketi oluşturma.

- Yeni dağıtım adımını test etme.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio desteklenen sürümleri.

- Visual Studio SDK. bu izlenecek yol, uzantıyı dağıtmak üzere bir vsıx paketi oluşturmak için SDK 'daki **vsıx Project** şablonunu kullanır. daha fazla bilgi için bkz. [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- SharePoint için sunucu nesne modelini kullanma. daha fazla bilgi için bkz. [SharePoint Foundation Server-Side nesne modelini kullanma](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- SharePoint çözümleri. Daha fazla bilgi için bkz. [çözümlere genel bakış](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- SharePoint çözümleri yükseltiliyor. Daha fazla bilgi için bkz. [bir çözümü yükseltme](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için üç proje oluşturmanız gerekir:

- Uzantıyı dağıtmak için VSıX paketini oluşturmak üzere bir VSıX projesi.

- Uzantıyı uygulayan bir sınıf kitaplığı projesi. bu projenin .NET Framework 4,5 ' i hedeflemesi gerekir.

- özel SharePoint komutlarını tanımlayan bir sınıf kitaplığı projesi. bu projenin .NET Framework 3,5 ' i hedeflemesi gerekir.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

3. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'yı yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

5. **vsıx Project** şablonunu seçin, projeyi **upgradedeploymentstep** olarak adlandırın ve **tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüm Gezgini** Için **UpgradeDeploymentStep** projesini ekler.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**' de, UpgradeDeploymentStep çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **Windows** düğümünü seçin.

3. iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 4,5** ' ı seçin.

4. **Sınıf kitaplığı** proje şablonu ' nu seçin, projenin **DeploymentStep uzantısını** adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme **DeploymentStepExtension** projesini ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint komut projesi oluşturmak için

1. **Çözüm Gezgini**' de, UpgradeDeploymentStep çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Windows** düğümünü seçin.

3. iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **.NET Framework 3,5** ' ı seçin.

4. **Sınıf kitaplığı** proje şablonu ' nu seçin, projeyi **SharePointCommands** olarak adlandırın ve **Tamam** düğmesini seçin.

     Visual Studio, **sharepointcommands** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Özel dağıtım adımını oluşturmak için kod yazmadan önce, kod dosyalarını ve derleme başvurularını eklemeniz ve projeleri yapılandırmanız gerekir.

#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension projesini yapılandırmak için

1. **DeploymentStepExtension** projesinde, aşağıdaki adlara sahip iki kod dosyası ekleyin:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. DeploymentStepExtension projesinde kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Framework** sekmesinde, System. ComponentModel. Composition derlemesinin onay kutusunu seçin.

4. **Uzantılar** sekmesinde, Microsoft. VisualStudio ' nin onay kutusunu seçin. SharePoint derleme ve sonra **tamam** düğmesini seçin.

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands projesini yapılandırmak için

1. **SharePointCommands** projesinde komutları adlı bir kod dosyası ekleyin.

2. **Çözüm Gezgini**' de, **SharePointCommands** proje düğümündeki kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

3. **Uzantılar** sekmesinde, aşağıdaki derlemeler için onay kutularını işaretleyin ve ardından **Tamam** düğmesini seçin ' e tıklayın.

    - MICROSOFT. SharePoint

    - Microsoft. VisualStudio. SharePoint. Komut

## <a name="define-the-custom-deployment-step"></a>Özel dağıtım adımını tanımlayın
 Yükseltme dağıtım adımını tanımlayan bir sınıf oluşturun. Dağıtım adımını tanımlamak için, sınıfı <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> arabirimini uygular. Özel bir dağıtım adımı tanımlamak istediğiniz her seferinde bu arabirimi uygulayın.

#### <a name="to-define-the-custom-deployment-step"></a>Özel dağıtım adımını tanımlamak için

1. **DeploymentStepExtension** projesinde, UpgradeStep kod dosyasını açın ve ardından aşağıdaki kodu içine yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olacaktır, ancak sonraki adımlarda kod eklediğinizde bu işlemler kaybolur.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet1":::

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Özel dağıtım adımını içeren bir dağıtım yapılandırması oluşturma
 Yeni dağıtım yapılandırması için, çeşitli yerleşik dağıtım adımlarını ve yeni yükseltme dağıtım adımını içeren bir proje uzantısı oluşturun. bu uzantıyı oluşturarak, geliştiricilerin SharePoint projelerinde dağıtımı yükselt adımını kullanmasına SharePoint yardımcı olursunuz.

 Dağıtım yapılandırmasını oluşturmak için, sınıfı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> arabirimini uygular. SharePoint projesi uzantısı oluşturmak istediğiniz her seferinde bu arabirimi uygulayın.

#### <a name="to-create-the-deployment-configuration"></a>Dağıtım yapılandırmasını oluşturmak için

1. **DeploymentStepExtension** projesinde, DeploymentConfigurationExtension kod dosyasını açın ve ardından aşağıdaki kodu buraya yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb" id="Snippet2":::

## <a name="create-the-custom-sharepoint-commands"></a>özel SharePoint komutlarını oluşturma
 SharePoint için sunucu nesne modeline çağıran iki özel komut oluşturun. Bir komut, bir çözümün zaten dağıtılıp dağıtılmadığını belirler; diğer komut bir çözümü yükseltir.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutlarını tanımlamak için

1. **SharePointCommands** projesinde, komutlar kod dosyasını açın ve ardından aşağıdaki kodu içine yapıştırın.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet4":::

## <a name="checkpoint"></a>Checkpoint
 bu noktada, özel dağıtım adımının tüm kodu ve SharePoint komutları artık projelerde bulunur. Onları hatasız olarak derlendiklerinden emin olmak için oluşturun.

#### <a name="to-build-the-projects"></a>Projeleri derlemek için

1. Bu **Çözüm Gezgini** **DeploymentStepExtension** projesinin kısayol menüsünü açın ve Ardından Oluştur'a **tıklayın.**

2. **SharePointCommands projesinin kısayol menüsünü açın ve** Oluştur'a **tıklayın.**

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Uzantıyı dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için çözümünüzde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak VSIX projesinde source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX paketini yapılandırmak ve oluşturmak için

1. Bu **Çözüm Gezgini,** **UpgradeDeploymentStep** projesinin altında **source.extension.vsixmanifest** dosyasının kısayol menüsünü açın ve aç'ı **seçin.**

     Visual Studio bildirim düzenleyicisinde açılır. source.extension.vsixmanifest dosyası, tüm VSIX paketlerinin gerekli olduğu extension.vsixmanifest dosyasının temelini alır. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna SharePoint** Projeleri için **Dağıtım Adımını Yükselt yazın.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna,** **Projelerinde 4.000.000'e kadar 4.000.000'SharePoint girin.**

5. Düzenleyicinin  Varlıklar sekmesinde Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

6. Tür **listesinde** **Microsoft.VisualStudio.MefComponent'ı seçin.**

    > [!NOTE]
    > Bu değer `MefComponent` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe VSIX paketinde bir uzantı derlemenin adını belirtir. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

8. Uygulama **Project** **DeploymentStepExtension'ı** ve ardından Tamam **düğmesini** seçin.

9. Bildirim düzenleyicisinde Yeni düğmesini **yeniden** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

10. Tür **listesine** **SharePoint. Commands.v4**.

    > [!NOTE]
    > Bu öğe, uygulama uzantısına eklemek istediğiniz özel bir Visual Studio belirtir. Daha fazla bilgi için [bkz. Varlık Öğesi (VSX Şeması)](/previous-versions/dd393737(v=vs.110)).

11. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

12. İlk **Project** **SharePointCommands'i ve** ardından Tamam **düğmesini** seçin.

13. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve çözümün hatasız derlenmiş olduğundan emin olun.

14. UpgradeDeploymentStep projesinin derleme çıkış klasöründe artık UpgradeDeploymentStep.vsix dosyasının olduğundan emin olun.

     Varsayılan olarak, derleme çıkış klasörü .'dür. Proje dosyanızı içeren klasörün altında \bin\Debug klasörü.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımını test etmek için hazırlanma
 Yükseltme dağıtım adımını test etmek için önce bir örnek çözümü SharePoint dağıtmanız gerekir. Başlangıç olarak deneysel uzantı örneğinde uzantıda hata Visual Studio. Ardından dağıtım adımını test etmek için kullanmak üzere bir liste tanımı ve liste örneği oluşturun ve sonra bunları SharePoint dağıtın. Ardından, liste tanımını ve liste örneğini değiştirerek varsayılan dağıtım işleminin SharePoint sitenin çözümlerinin üzerine yazmayı göstermek için yeniden dağıtmanız gerekir.

 Bu kılavuzda daha sonra liste tanımını ve liste örneğini değiştirecek ve ardından bunları SharePoint yükselteceğiz.

#### <a name="to-start-debugging-the-extension"></a>Uzantıda hata ayıklamaya başlamak için

1. Yönetici Visual Studio ile yeniden başlatın ve UpgradeDeploymentStep çözümünü açın.

2. DeploymentStepExtension projesinde UpgradeStep kod dosyasını açın ve ardından ve yöntemlerinde ilk kod satırına bir kesme `CanExecute` `Execute` noktası ekleyin.

3. **F5** anahtarını veya menü çubuğunda Hata AyıklamaYı Başlat'ı **seçerek hata**  >  **ayıklamayı başlatabilirsiniz.**

4. Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade Deployment Step for SharePoint Projects\1.0 uzantısını yüker ve deneysel Visual Studio. Yükseltme dağıtımı adımını bu dağıtım örneğinde test Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Liste tanımı SharePoint liste örneğiyle bir proje oluşturmak için

1. Deneysel Visual Studio örneğinde, menü çubuğunda Dosya Yeni Dosya'Project.  >    >  

2. Yeni **Project** iletişim kutusunda **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

3. İletişim kutusunun en üstünde, .NET Framework **3.5** sürümünün, önceki sürümler listesinde göründüğünden emin .NET Framework.

    ve için [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] projeler, uygulamanın bu sürümünü .NET Framework.

4. Proje şablonları listesinde SharePoint **2010 Project'ı** seçin, projeye **EmployeesListDefinition** adını ve ardından **Tamam düğmesini** seçin.

5. Özel **SharePoint Sihirbazı'nda,** hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin.

6. Bu **çözüm için güven düzeyi nedir SharePoint** grup çözümü olarak dağıt **seçeneğini** belirleyin.

   > [!NOTE]
   > Yükseltme dağıtımı adımı korumalı alanlı çözümleri desteklemez.

7. Son **düğmesini** seçin.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition projesini oluşturur.

8. EmployeesListDefinition projesinin kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni Öğe'yi **seçin.**

9. Yeni Öğe **Ekle - EmployeesListDefinition** iletişim kutusunda SharePoint **genişletin** ve ardından **2010 düğümünü** seçin.

10. Liste öğesi **şablonunu** seçin, öğeye Çalışanlar Listesi **adını ve** ardından Ekle **düğmesini** seçin.

     SharePoint Özelleştirme Sihirbazı görüntülenir

11. Liste **Seç Ayarlar** sayfasında aşağıdaki ayarları doğrulayın ve ardından Son **düğmesini** seçin:

    1. **Çalışanlar Listesi,** **listeniz için hangi adı görüntülemek istiyor musunuz? kutusunda** görünür.

    2. Şunları **temel alan özelleştirilebilir bir liste oluşturun:** seçeneği seçilmiştir.

    3. **Varsayılan (Boş)** şu değere göre **özelleştirilebilir bir liste oluşturun: listesinde** seçilir.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , Bir Title sütunu ve tek bir boş örnek içeren Employees List öğesini oluşturur ve Liste Tasarımcısı'na açılır.

12. Liste Tasarımcısı'nda Sütunlar **sekmesinde** Yeni  veya var olan bir sütun adı satırı yazın'ı seçin ve ardından Sütun Görünen Adı **listesine aşağıdaki sütunları** ekleyin:

    1. Ad

    2. Şirket

    3. İş Telefonu

    4. E-mail

13. Tüm dosyaları kaydedin ve liste tasarımcısını kapatın.

14. Bu **Çözüm Gezgini,** Çalışanlar Listesi **düğümünü** genişletin ve ardından Çalışanlar Listesi **Örneği alt** düğümünü genişletin.

15. Bu *Elements.xml* dosyasında, bu dosyada varsayılan XML'yi aşağıdaki XML ile değiştirin. Bu XML listenin adını Employees olarak **değiştirir** ve Jim Hance adlı bir çalışan için bilgi ekler.

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

16. Elements.xmlkaydedin *ve* kapatın.

17. EmployeesListDefinition projesinin kısayol menüsünü açın ve ardından Aç'ı veya **Özellikler'i** **seçin.**

     Özellikler Tasarımcısı açılır.

18. Hata **SharePoint** sonra otomatik geri **alma onay** kutusunun işaretini kaldırın ve ardından özellikleri kaydedin.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Liste tanımını ve liste örneğini dağıtmak için

1. Bu **Çözüm Gezgini** **EmployeesListDefinition proje düğümünü** seçin.

2. Özellikler **penceresinde,** Etkin Dağıtım Yapılandırması **özelliğinin Varsayılan olarak** ayarlanmış olduğundan **emin olun.**

3. **F5 anahtarını seçin** veya menü çubuğunda Hata Ayıklama Başlat **Hata**  >  **Ayıklama'ya tıklayın.**

4. Projenin başarıyla derlemesini, web tarayıcısının SharePoint sitesini açtığını,  Hızlı Başlat çubuğundaki Listeler öğesinin yeni **Çalışanlar** listesini ve  Çalışanlar listesinin Jim Hance girişini de dahil olduğunu doğrulayın.

5. Web tarayıcısını kapatın.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Liste tanımını ve liste örneğini değiştirmek ve bunları yeniden vermek için

1. EmployeesListDefinition projesinde, *ÇalışanElements.xml* proje öğesinin alt öğesi olanElements.xml **dosyasını** açın.

2. Jim `Data` Hance girdisini listeden kaldırmak için öğesini ve öğesinin öğesini kaldırın.

     Bitirişte, dosya aşağıdaki XML'yi içermeli.

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

3. Elements.xmlkaydedin *ve* kapatın.

4. Çalışanlar Listesi proje öğesinin kısayol **menüsünü açın** ve ardından Aç'ı veya **Özellikler'i** **seçin.**

5. Liste Tasarımcısı'nda Görünümler **sekmesini** seçin.

6. Seçili **sütunlar listesinde Ekler'i** **seçin** ve ardından bu < kullanılabilir sütunlar listesine taşımak için yeni **sütun anahtarını** seçin.

7. Business **Telefon sütununu** Seçili sütunlar listesinden Kullanılabilir sütunlar listesine **taşımak** için önceki adımı **tekrarlayın.**

     Bu eylem, bu alanları sitenin **Çalışanlar listesinin** varsayılan görünümünden SharePoint kaldırır.

8. **F5** anahtarını veya menü çubuğunda Hata AyıklamaYı Başlat'ı **seçerek hata**  >  **ayıklamayı başlatabilirsiniz.**

9. Dağıtım **Çakışmaları iletişim kutusunun görüntülendiğinden** emin olun.

     Bu iletişim kutusu, Visual Studio bir çözümün (liste örneği) o çözümün zaten SharePoint bir siteye dağıtmaya çalıştığında görüntülenir. Bu kılavuzda yükseltme dağıtımı adımını daha sonra yürütürken bu iletişim kutusu görünmez.

10. Dağıtım **Çakışmaları iletişim** kutusunda Otomatik Olarak Çözümle **seçeneği** düğmesini seçin.

     Visual Studio, SharePoint sitenin liste örneğini siler, projesinde liste öğesini dağıtır ve ardından SharePoint açar.

11. Hızlı Başlat çubuğunun **listeler** bölümünde **çalışanlar** listesini seçin ve ardından aşağıdaki ayrıntıları doğrulayın:

    - **ekler** ve **giriş Telefon** sütunları listenin bu görünümünde görünmez.

    - Liste boş. Çözümü yeniden dağıtmak için **varsayılan** dağıtım yapılandırmasını kullandığınızda, **çalışanlar** listesi, projenizdeki yeni boş liste ile değiştirilmiştir.

## <a name="test-the-deployment-step"></a>Dağıtım adımını test etme
 Şimdi yükseltme dağıtım adımını test etmeye hazırsınız. İlk olarak, SharePoint liste örneğine bir öğe ekleyin. sonra liste tanımını ve liste örneğini değiştirin, SharePoint sitesinde yükseltin ve yükseltme dağıtımı adımının yeni öğenin üzerine yazmaz olduğunu onaylayın.

#### <a name="to-manually-add-an-item-to-the-list"></a>Listeye el ile öğe eklemek için

1. SharePoint sitesindeki şeritte, **liste araçları** sekmesinde, **öğeler** sekmesini seçin.

2. **Yeni** grupta **Yeni öğe**' yi seçin.

     Alternatif olarak, öğe listesindeki **Yeni öğe Ekle** bağlantısını seçebilirsiniz.

3. **Çalışanlar-yeni öğe** penceresinde, **başlık** kutusuna **tesisler Yöneticisi**' ni girin.

4. **Ad** kutusuna **Andy** yazın.

5. **Şirket** kutusuna **contoso** yazın.

6. **Kaydet** düğmesini seçin, yeni öğenin listede göründüğünü doğrulayın ve ardından Web tarayıcısını kapatın.

     Bu kılavuzda daha sonra bu öğeyi, yükseltme dağıtım adımının bu listenin içeriğinin üzerine yazmayacağı doğrulanacak şekilde kullanacaksınız.

#### <a name="to-test-the-upgrade-deployment-step"></a>Yükseltme dağıtım adımını test etmek için

1. Visual Studio deneysel örneğinde, **Çözüm Gezgini**' de **employeeslistdefinition** proje düğümünün kısayol menüsünü açın ve **özellikler**' i seçin.

    Özellikler Düzenleyicisi/tasarımcı açılır.

2. **SharePoint** sekmesinde, **etkin dağıtım yapılandırma** özelliğini **yükselt** olarak ayarlayın.

    Bu özel dağıtım yapılandırması, yeni yükseltme dağıtım adımını içerir.

3. **Çalışanlar listesi** proje öğesi için kısayol menüsünü açın ve **Özellikler** ' i veya **Aç**' ı seçin.

    Özellikler Düzenleyicisi/tasarımcı açılır.

4. **Görünümler** sekmesinde, **e-posta** sütununu seçin ve ardından **<** Bu sütunu **Seçilen sütunlar** listesinden **kullanılabilir sütunlar** listesine taşımak için anahtarı seçin.

    bu eylem, bu alanları SharePoint sitesindeki **çalışanlar** listesinin varsayılan görünümünden kaldırır.

5. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  .

6. diğer Visual Studio örneğindeki kodun, daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `CanExecute` .

7. **F5** tuşunu yeniden seçin veya menü çubuğunda **Hata Ayıkla**  >  **devam et**' i seçin.

8. Kodun daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `Execute` .

9. **F5** tuşunu seçin veya menü çubuğunda **Hata Ayıkla**' yı seçerek  >  son saate **devam edin** .

     web tarayıcısı SharePoint sitesini açar.

10. Hızlı başlatma alanının **listeler** bölümünde **çalışanlar** listesini seçin ve ardından aşağıdaki ayrıntıları doğrulayın:

    - Daha önce el ile eklediğiniz öğe (Andy, Tesis Yöneticisi için) listede hala vardır.

    - **iş Telefon** ve **e-posta adresi** sütunları listenin bu görünümünde görünmez.

      **yükseltme** dağıtımı yapılandırması, SharePoint sitesindeki mevcut **çalışanlar** listesi örneğini değiştirir. **Yükseltme** yapılandırması yerine **varsayılan** dağıtım yapılandırmasını kullandıysanız, bir dağıtım çakışması ile karşılaşırsınız. Visual Studio, **çalışanlar** listesini değiştirerek çakışmayı çözümleyebilir ve tesislere ait öğe, tesis yöneticisi de silinir.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 dağıtım yükseltme adımını test etmeyi bitirdikten sonra, SharePoint sitesinden liste örneğini ve liste tanımını kaldırın ve dağıtım adımı uzantısını Visual Studio ' dan kaldırın.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>liste örneğini SharePoint sitesinden kaldırmak için

1. liste zaten açık değilse SharePoint sitesindeki **çalışanlar** listesini açın.

2. SharePoint sitesindeki şeritte, **liste araçları** sekmesini seçin ve ardından **liste** sekmesini seçin.

3. **Ayarlar** grubunda, **liste Ayarlar** öğesini seçin.

4. **İzinler ve yönetim** altında **Bu listeyi Sil** komutunu seçin, listeyi geri dönüşüm kutusu 'na göndermek istediğinizi onaylamak için **Tamam** ' ı seçin ve ardından Web tarayıcısını kapatın.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>SharePoint sitesinden liste tanımını kaldırmak için

1. Visual Studio deneysel örneğinde, menü çubuğunda, **derleme**  >  **geri çek**' i seçin.

     Visual Studio liste tanımını SharePoint sitesinden geri çeker.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. uzantılar listesinde **SharePoint projeler için dağıtım adımını yükselt**' i seçin ve ardından **kaldır** komutunu seçin.

3. Açılan iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** ' i seçin ve kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** ' ı seçin.

4. her iki Visual Studio örneğini (deneysel örnek ve upgradedeploymentstep çözümünün açık olduğu Visual Studio örneğini) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [paketleme ve dağıtım SharePoint uzat](../sharepoint/extending-sharepoint-packaging-and-deployment.md)