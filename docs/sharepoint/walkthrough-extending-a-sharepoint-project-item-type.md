---
title: 'izlenecek yol: SharePoint Project öğe türünü genişletme | Microsoft Docs'
description: bu izlenecek yolda, iş verileri bağlantısı (BDC) modeli proje öğesi gibi SharePoint proje öğesi türü için bir uzantı oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 589a9b09f6a59aef62f447f5ce2970eef56e85b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148785"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>izlenecek yol: SharePoint proje öğesi türünü genişletme
  SharePoint ' de Iş verileri bağlantısı (BDC) hizmeti için bir model oluşturmak üzere **Iş verileri bağlantı modeli** Proje öğesini kullanabilirsiniz. Varsayılan olarak, bu proje öğesini kullanarak bir model oluşturduğunuzda, modeldeki veriler kullanıcılara gösterilmez. ayrıca, kullanıcıların verileri görüntülemesini sağlamak için SharePoint içinde bir dış liste oluşturmanız gerekir.

 Bu kılavuzda, **Iş verileri bağlantı modeli** proje öğesi için bir uzantı oluşturacaksınız. Geliştiriciler, projesinde BDC modelindeki verileri görüntüleyen bir dış liste oluşturmak için bu uzantıyı kullanabilir. Bu izlenecek yol aşağıdaki görevleri gösterir:

- iki ana görevi gerçekleştiren bir Visual Studio uzantısı oluşturma:

  - Bir BDC modelindeki verileri görüntüleyen bir dış liste oluşturur. uzantı, listeyi tanımlayan bir *Elements.xml* dosyası oluşturmak için SharePoint proje sisteminin nesne modelini kullanır. Ayrıca, IVB modeliyle birlikte dağıtılacak şekilde dosyayı projeye ekler.

  - **Çözüm Gezgini**' deki **Iş verileri bağlantı modeli** proje öğelerine bir kısayol menü öğesi ekler. Geliştiriciler, BDC modeli için bir dış liste oluşturmak üzere bu menü öğesine tıklabilirler.

- uzantı derlemesini dağıtmak için bir Visual Studio uzantısı (vsıx) paketi oluşturma.

- Uzantı test ediliyor.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri, SharePoint ve Visual Studio.

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. bu izlenecek yol SDK 'daki **vsıx Project** şablonunu, proje öğesini dağıtmak için bir vsıx paketi oluşturmak için kullanır. daha fazla bilgi için bkz. [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- İçindeki BDC hizmeti [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Daha fazla bilgi için bkz. [IVB mimarisi](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- IVB modelleriyle ilgili XML şeması. Daha fazla bilgi için bkz. [IVB modeli altyapısı](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için iki proje oluşturmanız gerekir:

- Proje öğesi uzantısını dağıtmak için VSıX paketini oluşturmak üzere bir VSıX projesi.

- Proje öğesi uzantısını uygulayan bir sınıf kitaplığı projesi.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-vsix-project"></a>VSıX projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

3. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **genişletilebilirlik** düğümünü seçin.

    > [!NOTE]
    > **genişletilebilirlik** düğümü yalnızca Visual Studio SDK 'yı yüklediğinizde kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında bulunan Önkoşullar bölümüne bakın.

4. **yeni Project** iletişim kutusunun en üstündeki listede **.NET Framework 4,5**' ı seçin.

     SharePoint araçları uzantıları, .NET Framework bu sürümünde özellikleri gerektirir.

5. **vsıx Project** şablonunu seçin.

6. **Ad** kutusuna **Generateexternalveriveriists** yazın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Generateexternalveriveriists** projesini **Çözüm Gezgini** ekler.

7. Source. Extension. valtmanifest dosyası otomatik olarak açılmazsa, Generateexternalveriveriists projesinde kısayol menüsünü açın ve **Aç** ' ı seçin.

8. Source. Extension. valtmanifest dosyasında yazar alanı için boş olmayan bir giriş (contoso girin) olduğundan emin olun, dosyayı kaydedin ve kapatın.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. **Çözüm Gezgini**' de, **Generateexternalveriveriists** çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

2. **yeni Project ekle** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **Windows** düğümünü seçin.

3. iletişim kutusunun üst kısmındaki listede **.NET Framework 4,5**' ı seçin.

4. Proje şablonları listesinde **sınıf kitaplığı**' nı seçin.

5. **Ad** kutusuna **BdcProjectItemExtension** girin ve sonra **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme **BdcProjectItemExtension** projesini ekler ve varsayılan Class1 kod dosyasını açar.

6. Class1 kod dosyasını projeden silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Proje öğesi uzantısını oluşturmak için kod yazmadan önce, uzantı projesine kod dosyalarını ve derleme başvurularını ekleyin.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. BdcProjectItemExtension projesinde, aşağıdaki adlara sahip iki kod dosyası ekleyin:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. bdcprojectıtemextension projesini seçin ve ardından menü çubuğunda **Project**  >  **başvuru ekle**' yi seçin.

3. **Derlemeler** düğümü altında, **Framework** düğümünü seçin ve aşağıdaki derlemelerin her biri için onay kutusunu seçin:

    - System. ComponentModel. Composition

    - WindowsBase

4. **Derlemeler** düğümü altında, **Uzantılar** düğümünü seçin ve ardından aşağıdaki derlemenin onay kutusunu seçin:

    - Microsoft. VisualStudio. SharePoint

5. **Tamam** düğmesini seçin.

## <a name="define-the-project-item-extension"></a>Proje öğesi uzantısını tanımlama
 **Iş verileri bağlantı modeli** proje öğesinin uzantısını tanımlayan bir sınıf oluşturun. Uzantıyı tanımlamak için sınıfı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> arabirimini uygular. Varolan bir proje öğesi türünü genişletmek istediğiniz zaman bu arabirimi uygulayın.

#### <a name="to-define-the-project-item-extension"></a>Proje öğesi uzantısını tanımlamak için

1. Aşağıdaki kodu ProjectItemExtension kod dosyasına yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra, projede bazı derleme hataları olur. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb" id="Snippet1":::

## <a name="create-the-external-data-lists"></a>Dış veri listelerini oluşturma
 `GenerateExternalDataListsExtension`BDC modelindeki her varlık için bir dış veri listesi oluşturan sınıfın kısmi tanımını ekleyin. Dış veri listesini oluşturmak için, bu kod ilk olarak BDC modeli dosyasındaki XML verilerini ayrıştırarak BDC modelindeki varlık verilerini okur. Ardından, IVB modelini temel alan bir liste örneği oluşturur ve bu liste örneğini projeye ekler.

#### <a name="to-create-the-external-data-lists"></a>Dış veri listeleri oluşturmak için

1. Aşağıdaki kodu Generateexternalveriveriists kod dosyasına yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 İzlenecek yolun bu noktasında, proje öğesi uzantısının tüm kodu artık projede. Projenin hatasız derlendiğinden emin olmak için çözümü oluşturun.

#### <a name="to-build-the-solution"></a>Çözümü oluşturmak için

1. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Proje öğesi uzantısını dağıtmak için bir VSıX paketi oluşturma
 Uzantıyı dağıtmak için, çözümünüzdeki VSıX projesini kullanarak bir VSıX paketi oluşturun. İlk olarak, VSIX projesinde bulunan kaynak. Extension. valtmanifest dosyasını değiştirerek VSıX paketini yapılandırın. Ardından, çözümü oluşturarak VSıX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSıX paketini yapılandırmak ve oluşturmak için

1. **Çözüm Gezgini**, Generateexternalveriists projesinde source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **Aç** öğesini seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar. Source. Extension. valtmanifest dosyası, uzantısının temelini oluşturur. valtmanifest dosyası tüm VSıX paketleri için gereklidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)).

2. **Ürün adı** kutusuna **dış veri listesi Oluşturucu** girin.

3. **Yazar** kutusuna **contoso** girin.

4. **Açıklama** kutusuna, **dış veri listeleri oluşturmak Için kullanılabilecek Iş verileri bağlantı modeli proje öğeleri için bir uzantı** girin.

5. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

6. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

    > [!NOTE]
    > Bu değer, `MefComponent` extension. valtmanifest dosyasındaki öğesine karşılık gelir. Bu öğe VSıX paketindeki bir uzantı derlemesinin adını belirtir. Daha fazla bilgi için bkz. [MefComponent öğesi (VSX şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

8. **Project** listesinde **bdcprojectıtemextension**' ı seçin ve ardından **tamam** düğmesini seçin.

9. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

10. Projenin hata olmadan derlendiğini ve derlendiğinden emin olun.

11. Generateexternalveriists projesi için derleme çıkış klasörünün şimdi Generateexternalveriveriists. vsix dosyasını içerdiğinden emin olun.

     Varsayılan olarak, yapı çıktı klasörü... proje dosyanızı içeren klasörün altındaki \bin\Debug klasörü.

## <a name="test-the-project-item-extension"></a>Proje öğesi uzantısını test etme
 Artık proje öğesi uzantısını test etmeye hazırsınız. İlk olarak, Visual Studio deneysel örneğinde uzantı projesinde hata ayıklamayı başlatın. ardından, bir BDC modeli için bir dış liste oluşturmak üzere Visual Studio deneysel örneğinde uzantıyı kullanın. son olarak, SharePoint sitesinde dış listeyi açarak beklendiği gibi çalıştığını doğrulayın.

#### <a name="to-start-debugging-the-extension"></a>Uzantının hatalarını ayıklamaya başlamak için

1. gerekirse, yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve ardından generateexternalveriveriists çözümünü açın.

2. BdcProjectItemExtension projesinde ProjectItemExtension kod dosyasını açın ve sonra yöntemdeki kod satırına bir kesme noktası ekleyin `Initialize` .

3. Generateexternalverists kod dosyasını açın ve sonra yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `GenerateExternalDataLists_Execute` .

4. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  .

     Visual Studio, uzantıyı%userprofile%\appdata\local\microsoft\visualstudio\10.0exp\extensions\contoso\external Data List generator\1.0 dizinine yükleyerek Visual Studio deneysel bir örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin.

2. **yeni Project** iletişim kutusunda **şablonlar** düğümünü genişletin, **Visual C#** düğümünü genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

3. iletişim kutusunun üst kısmındaki listede **.NET Framework 3,5** ' nin seçili olduğundan emin olun. İçin projeler [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .NET Framework bu sürümü gerektirir.

4. proje şablonları listesinde **SharePoint 2010 Project** öğesini seçin.

5. **Ad** kutusuna **SharePointProjectTestBDC** yazın ve **Tamam** düğmesini seçin.

6. SharePoint özelleştirme sihirbazında, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin, **grup çözümü olarak dağıt**' ı seçin ve ardından **son** düğmesini seçin.

7. Sharepointprojecttestivb projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

8. **Add newıtem-sharepointprojecttestbdc** iletişim kutusunda, yüklü dil düğümünü genişletin, **SharePoint** düğümünü genişletin.

9. **2010** düğümünü seçin ve ardından **Iş verileri bağlantı modeli (yalnızca Grup çözümü)** şablonunu seçin.

10. **Ad** kutusuna **TestBDCModel** girin ve sonra **Ekle** düğmesini seçin.

11. diğer Visual Studio örneğindeki kodun, `Initialize` projectıtemextension kod dosyasının yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın.

12. Visual Studio durdurulan örneğinde **F5** tuşuna basın veya menü çubuğunda,   >  projede hata ayıklamaya devam etmek için **devam et** ' i seçin.

13. Visual Studio deneysel örneğinde **F5** tuşunu seçin veya menü **çubuğunda hata**  >  **ayıklamayı başlat** ' ı seçerek **testbdcmodel** projesini oluşturun, dağıtın ve çalıştırın.

     web tarayıcısı, hata ayıklama için belirtilen SharePoint sitesinin varsayılan sayfasına açılır.

14. Hızlı başlatma alanındaki **listeler** bölümünün, henüz PROJEDEKI varsayılan İVB modelini temel alan bir liste içermediğini doğrulayın. önce SharePoint kullanıcı arabirimini kullanarak veya proje öğesi uzantısını kullanarak bir dış veri listesi oluşturmanız gerekir.

15. Web tarayıcısını kapatın.

16. testbdcmodel projesi açık olan Visual Studio örneğinde, **Çözüm Gezgini** içindeki **testbdcmodel** düğümünün kısayol menüsünü açın ve **dış veri listesi oluştur**' u seçin.

17. Visual Studio diğer örneğindeki kodun, yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `GenerateExternalDataLists_Execute` . **F5** **tuşunu seçin veya** menü çubuğunda,  >  projede hata ayıklamaya devam etmek için **devam et** ' i seçin.

18. Visual Studio deneysel örneği, testbdcmodel projesine **Entity1DataList** adlı bir liste örneği ekler ve örnek ayrıca liste örneği için **özellik2** adlı bir özellik oluşturur.

19. **F5** tuşunu seçin veya menü **çubuğunda hata**  >  **ayıklamayı Başlat** ' ı seçerek TestBDCModel projesini oluşturun, dağıtın ve çalıştırın.

     web tarayıcısı, hata ayıklama için kullanılan SharePoint sitesinin varsayılan sayfasına açılır.

20. Hızlı başlatma alanının **listeler** bölümünde **Entity1DataList** listesini seçin.

21. Listenin, Identifier1 değeri 0 ve Merhaba Dünya Ileti değeri olan bir öğeye ek olarak Identifier1 ve Message adlı sütunlar içerdiğini doğrulayın.

     **Iş verileri bağlantı modeli** proje şablonu, tüm bu verileri sağlayan varsayılan İVB modelini oluşturur.

22. Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 proje öğesi uzantısını test etmeyi bitirdikten sonra, dış liste ve BDC modelini SharePoint sitesinden kaldırın ve proje öğesi uzantısını Visual Studio kaldırın.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>dış veri listesini SharePoint sitesinden kaldırmak için

1. SharePoint sitesinin hızlı başlat alanında **Entity1DataList** listesini seçin.

2. SharePoint sitesindeki şeritte **liste** sekmesini seçin.

3. **liste** sekmesinde, **Ayarlar** grubunda, **liste Ayarlar**' nı seçin.

4. **İzinler ve yönetim** altında **Bu listeyi Sil**' i seçin ve ardından listeyi geri dönüşüm kutusu 'na göndermek istediğinizi onaylamak için **Tamam** ' ı seçin.

5. Web tarayıcısını kapatın.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>ivb modelini SharePoint sitesinden kaldırmak için

1. Visual Studio deneysel örneğinde, menü çubuğunda, **derleme**  >  **geri çek**' i seçin.

     Visual Studio BDC modelini SharePoint sitesinden kaldırır.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Proje öğesi uzantısını Visual Studio kaldırmak için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde **dış veri listesi Oluşturucu**' yı seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** ' i seçin.

4. Kaldırma işlemini gerçekleştirmek için **Şimdi yeniden Başlat** ' ı seçin.

5. her iki Visual Studio örneğini (deneysel örnek ve generateexternalveriists çözümünün açık olduğu örneği) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)