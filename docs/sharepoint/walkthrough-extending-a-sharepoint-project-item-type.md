---
title: 'Adım adım kılavuz: SharePoint Project Öğe Türü | Microsoft Docs'
description: Bu kılavuzda, iş verileri bağlantısı (BDC) SharePoint proje öğesi gibi bir proje öğesi türü için bir uzantı oluşturun.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625070"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Adım adım kılavuz: SharePoint proje öğesi türünü genişletme
  İş Verileri Bağlantı **Modeli proje öğesini kullanarak** İş Verileri Bağlantısı (BDC) hizmeti için bir model oluşturabilirsiniz SharePoint. Varsayılan olarak, bu proje öğesini kullanarak bir model sanız, modelde veriler kullanıcılara görüntülenmez. Kullanıcıların verileri görüntülemelerini sağlamak için SharePoint bir dış liste de oluşturmanız gerekir.

 Bu kılavuzda İş Verileri Bağlantı Modeli proje öğesi **için bir uzantı oluşturabilirsiniz.** Geliştiriciler, projelerinde verileri BDC modelinde görüntüleyen bir dış liste oluşturmak için uzantıyı kullanabilir. Bu kılavuz aşağıdaki görevleri gösterir:

- İki ana Visual Studio gerçekleştiren bir uzantı oluşturma:

  - Verileri bir BDC modelinde görüntüleyen bir dış liste üretir. Uzantı, listeyi tanımlayan bir SharePoint oluşturmak içinElements.xml *proje* sistemi için nesne modelini kullanır. Ayrıca, BDC modeliyle birlikte dağıtılması için dosyayı projeye ekler.

  - öğesinde İş Verileri Bağlantı Modeli proje **öğelerine** bir kısayol menü öğesi **Çözüm Gezgini.** Geliştiriciler BDC modeli için bir dış liste oluşturmak için bu menü öğesini tıklar.

- Uzantı derlemesini Visual Studio bir Uzantı (VSIX) paketi oluşturma.

- Uzantıyı test etme.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows, SharePoint ve Visual Studio.

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint Araçları'Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- içinde BDC [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] hizmeti. Daha fazla bilgi için bkz. [BDC Mimarisi.](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14))

- BDC modelleri için XML şeması. Daha fazla bilgi için bkz. [BDC Model Altyapısı](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için iki proje oluşturmanız gerekir:

- Proje öğesi uzantısını dağıtmak için VSIX paketini oluşturmak için bir VSIX projesi.

- Proje öğesi uzantısını uygulayan bir sınıf kitaplığı projesi.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-vsix-project"></a>VSIX projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

3. Yeni **Project** iletişim kutusunda **Visual C#** veya Visual Basic **düğümlerini** genişletin ve ardından **Genişletilebilirlik düğümünü** seçin.

    > [!NOTE]
    > **Genişletilebilirlik düğümü** yalnızca Visual Studio SDK'sı yüklenirse kullanılabilir. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan önkoşullar bölümüne bakın.

4. Yeni Görünüm iletişim kutusunun en üstünde **yer alan Project** **4.5 .NET Framework seçin.**

     SharePoint araçları uzantıları, uygulamanın bu sürümünde özellikler .NET Framework.

5. **VSIX Project** seçin.

6. Ad **kutusuna** **GenerateExternalDataLists yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**GenerateExternalDataLists projesini** **Çözüm Gezgini.**

7. source.extension.vsixmanifest dosyası otomatik olarak açılmazsa GenerateExternalDataLists projesinde kısayol menüsünü açın ve Aç'ı **seçin**

8. source.extension.vsixmanifest dosyasında Yazar alanı için boş olmayan bir giriş (Contoso girin) olduğunu doğrulayın, dosyayı kaydedin ve kapatın.

#### <a name="to-create-the-extension-project"></a>Uzantı projesini oluşturmak için

1. Bu **Çözüm Gezgini** **GenerateExternalDataLists** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **Liste'yi Project.**

2. Yeni **Kullanıcı Project** iletişim kutusunda Visual **C#** veya Visual Basic **genişletin** ve ardından Windows **seçin.**

3. İletişim kutusunun en üstünde yer alan listede **4.5 .NET Framework seçin.**

4. Proje şablonları listesinde Sınıf **Kitaplığı'ı seçin.**

5. Ad **kutusuna** **BdcProjectItemExtension yazın** ve tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**BdcProjectItemExtension** projesini çözüme ekler ve varsayılan Class1 kod dosyasını açar.

6. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-extension-project"></a>Uzantı projesini yapılandırma
 Proje öğesi uzantısını oluşturmak için kod yazmadan önce, uzantı projesine kod dosyaları ve derleme başvuruları ekleyin.

#### <a name="to-configure-the-project"></a>Projeyi yapılandırmak için

1. BdcProjectItemExtension projesine aşağıdaki adlara sahip iki kod dosyası ekleyin:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. BdcProjectItemExtension projesini seçin ve ardından menü çubuğunda Başvuru **Ekle'Project**  >  **seçin.**

3. Derlemeler **düğümü** altında Çerçeve **düğümünü** seçin ve aşağıdaki derlemelerin her biri için onay kutusunu seçin:

    - System.ComponentModel.Composition

    - Windowsbase

4. Derlemeler **düğümü** altında **Uzantılar düğümünü** seçin ve ardından aşağıdaki derlemenin onay kutusunu seçin:

    - Microsoft.VisualStudio. SharePoint

5. Tamam **düğmesini** seçin.

## <a name="define-the-project-item-extension"></a>Proje öğesi uzantısını tanımlama
 İş Verileri Bağlantı Modeli proje öğesinin **uzantısını tanımlayan bir** sınıf oluşturun. uzantısını tanımlamak için sınıfı arabirimini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> kullanır. Mevcut proje öğesi türünü genişletmek istediğiniz her durumda bu arabirimi gerçekleştirin.

#### <a name="to-define-the-project-item-extension"></a>Proje öğesi uzantısını tanımlamak için

1. Aşağıdaki kodu ProjectItemExtension kod dosyasına yapıştırın.

    > [!NOTE]
    > Bu kodu ekledikten sonra proje bazı derleme hatalarına sahip olur. Sonraki adımlarda kod eklerken bu hatalar gider.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb" id="Snippet1":::

## <a name="create-the-external-data-lists"></a>Dış veri listelerini oluşturma
 BDC modelinde her `GenerateExternalDataListsExtension` varlık için dış veri listesi oluşturan sınıfının kısmi bir tanımını ekleyin. Dış veri listesini oluşturmak için bu kod ilk olarak BDC model dosyasındaki XML verilerini ayrıştırarak BDC modelinde varlık verilerini okur. Ardından, BDC modelini temel alan bir liste örneği oluşturur ve bu liste örneğini projeye ekler.

#### <a name="to-create-the-external-data-lists"></a>Dış veri listelerini oluşturmak için

1. Aşağıdaki kodu GenerateExternalDataLists kod dosyasına yapıştırın.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, proje öğesi uzantısının tüm kodu artık projededir. Projenin hatasız derlenmiş olduğundan emin olmak için çözümü derle.

#### <a name="to-build-the-solution"></a>Çözümü derlemek için

1. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Proje öğesi uzantısını dağıtmak için VSIX paketi oluşturma
 Uzantıyı dağıtmak için çözümünüzde VSIX projesini kullanarak bir VSIX paketi oluşturun. İlk olarak, VSIX projesine dahil edilen source.extension.vsixmanifest dosyasını değiştirerek VSIX paketini yapılandırabilirsiniz. Ardından, çözümü oluşturarak VSIX paketini oluşturun.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX paketini yapılandırmak ve oluşturmak için

1. Bu **Çözüm Gezgini** generateExternalDataLists projesinde source.extension.vsixmanifest dosyasının kısayol menüsünü açın ve aç'ı **seçin.**

     Visual Studio bildirim düzenleyicisinde açılır. source.extension.vsixmanifest dosyası, tüm VSIX paketleri için gerekli olan extension.vsixmanifest dosyasının temelidir. Bu dosya hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 1.0 Başvurusu.](/previous-versions/dd393700(v=vs.110))

2. Ürün Adı **kutusuna** Dış Veri Listesi **Oluşturucu yazın.**

3. Yazar **kutusuna** Contoso **yazın.**

4. Açıklama **kutusuna,** dış veri listeleri oluşturmak için kullanılan İş Verileri Bağlantı Modeli **proje öğeleri için bir uzantı girin.**

5. Düzenleyicinin  Varlıklar sekmesinde Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

6. Tür **listesinde** **Microsoft.VisualStudio.MefComponent'ı seçin.**

    > [!NOTE]
    > Bu değer `MefComponent` extension.vsixmanifest dosyasındaki öğesine karşılık gelen bir değerdir. Bu öğe VSIX paketinde bir uzantı derlemenin adını belirtir. Daha fazla bilgi için bkz. [MEFComponent Öğesi (VSX Şeması)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

8. İlk **Project** **BdcProjectItemExtension'ı** ve ardından Tamam **düğmesini** seçin.

9. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

10. Projenin hatasız derlenmiş ve derlenmiş olduğundan emin olun.

11. GenerateExternalDataLists projesinin derleme çıktı klasörünün artık GenerateExternalDataLists.vsix dosyasını içerdiğini emin olun.

     Varsayılan olarak, derleme çıkış klasörü . Proje dosyanızı içeren klasörün altında \bin\Debug klasörü.

## <a name="test-the-project-item-extension"></a>Proje öğesi uzantısını test etmek
 Artık proje öğesi uzantısını test etmeye hazır olursanız. İlk olarak, uzantı projesinin deneysel örneğinde hata ayıklamaya Visual Studio. Ardından, bir BDC modeli için bir dış Visual Studio oluşturmak üzere uzantıyı Visual Studio örneğinde kullanın. Son olarak, beklendiği gibi çalıştığını doğrulamak SharePoint sitenin dış listesini açın.

#### <a name="to-start-debugging-the-extension"></a>Uzantıda hata ayıklamaya başlamak için

1. Gerekirse yönetici kimlik Visual Studio yeniden başlatın ve generateExternalDataLists çözümünü açın.

2. BdcProjectItemExtension projesinde ProjectItemExtension kod dosyasını açın ve ardından yönteminde kod satırına bir kesme noktası `Initialize` ekleyin.

3. GenerateExternalDataLists kod dosyasını açın ve ardından yönteminde ilk kod satırına bir kesme noktası `GenerateExternalDataLists_Execute` ekleyin.

4. **F5** anahtarını veya menü çubuğunda Hata AyıklamaYı Başlat'ı seçerek **hata**  >  **ayıklamayı başlatabilirsiniz.**

     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0 uzantısını yüklüp deneysel bir Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-extension"></a>Uzantıyı test etmek için

1. Deneysel Visual Studio örneğinde, menü çubuğunda Dosya Yeni Dosya'Project.  >    >  

2. Yeni **Project** iletişim kutusunda Şablonlar düğümünü genişletin, **Visual C#** düğümünü genişletin, SharePoint **düğümünü** genişletin ve **ardından 2010'a tıklayın.** 

3. İletişim kutusunun en üstünde yer alan listede **3.5 .NET Framework emin** olun. için [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] projeler, uygulamanın bu sürümünü .NET Framework.

4. Proje şablonları listesinde, **2010 SharePoint'yi Project.**

5. Ad **kutusuna** **SharePointProjectTestBDC yazın** ve tamam **düğmesini** seçin.

6. Özelleştirme SharePoint'nda hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin, Grup çözümü olarak **dağıt'ı** seçin ve ardından Son **düğmesini** seçin.

7. SharePointProjectTestBDC projesinin kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **Öğe'yi seçin.**

8. **NewItem Ekle - SharePointProjectTestBDC** iletişim kutusunda, yüklü dil düğümünü genişletin ve SharePoint **genişletin.**

9. **2010 düğümünü** ve ardından İş Verileri Bağlantı **Modeli (yalnızca Grup Çözümü) şablonunu** seçin.

10. Ad **kutusuna** **TestBDCModel yazın** ve Ekle **düğmesini** seçin.

11. Visual Studio'nin diğer örneğinde yer alan kodun ProjectItemExtension kod dosyasının yönteminde ayar istediğiniz kesme `Initialize` noktası üzerinde durarak durduğu doğrulayın.

12. Projenin durdurulmuş örneğinde Visual Studio **F5** anahtarını seçin veya menü çubuğunda, projede hata ayıklamaya devam etmek için Devam Hata   >   Ayıkla'ya tıklayın.

13. TestBDCModel projesini derlemek, dağıtmak ve çalıştırmak için Visual Studio'nin deneysel örneğinde **F5** anahtarını seçin veya menü çubuğunda Hata AyıklamaYı Başlat Hata Ayıklamayı  >   **Başlat'ı** seçin.

     Web tarayıcısı, hata ayıklama için belirtilen SharePoint sitenin varsayılan sayfasını açar.

14. Hızlı Başlat bölümündeki  Listeler bölümünde henüz projesinde varsayılan BDC modelini temel alan bir liste olmadığını doğrulayın. İlk olarak, SharePoint kullanıcı arabirimini kullanarak veya proje öğesi uzantısını kullanarak bir dış veri listesi oluşturmanız gerekir.

15. Web tarayıcısını kapatın.

16. TestBDCModel Visual Studio açık olan örnek içinde **TestBDCModel** düğümünün kısayol menüsünü açın **ve Çözüm Gezgini** Veri Listesi **Oluştur'a tıklayın.**

17. Uygulamanın diğer örneğinde yer alan kodun Visual Studio kesme noktası üzerinde durduğu `GenerateExternalDataLists_Execute` doğrulayın. **F5 anahtarını seçin** veya projede hata ayıklamaya devam etmek için menü çubuğunda Hata Ayıklama  >   Devam'ı seçin.

18. Visual Studio deneysel örneği, TestBDCModel projesine **Entity1DataList** adlı bir liste örneği ekler ve örnek de liste örneği için **Feature2** adlı bir özellik oluşturur.

19. **F5 anahtarını** seçin veya menü çubuğunda Hata Ayıklama Hata AyıklamaYı Başlat'ı seçerek TestBDCModel projesini  >   derleme, dağıtma ve çalıştırma.

     Web tarayıcısı, hata ayıklama için kullanılan SharePoint sitenin varsayılan sayfasını açar.

20. Varlık **listesinin** Listeler Hızlı Başlat **Entity1DataList listesini** seçin.

21. Listede Tanımlayıcı1 ve İleti adlı sütunların yanı sıra Tanımlayıcı1 değeri 0 olan bir öğenin yanı sıra Tanımlayıcı1 ve İleti değerinin de Tanımlayıcı1 olduğunu Merhaba Dünya.

     İş **Verileri Bağlantı Modeli proje** şablonu, tüm bu verileri sağlayan varsayılan BDC modelini oluşturur.

22. Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizleme
 Proje öğesi uzantısını test edindikten sonra, dış listeyi ve BDC modelini SharePoint siteden kaldırın ve proje öğesi uzantısını Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Dış veri listesini siteden kaldırmak SharePoint için

1. Hızlı Başlat sitenin SharePoint **Entity1DataList listesini** seçin.

2. SharePoint sitenin Şerit'inde Liste **sekmesini** seçin.

3. Liste **sekmesinde,** grup grubunda **Ayarlar** Listele'yi **Ayarlar.**

4. İzinler **ve Yönetim'in** **altında Bu**  listeyi sil'i seçin ve sonra listeyi ilgili listeye göndermek istediğinizden emin olmak için Tamam'geri dönüşüm kutusu.

5. Web tarayıcısını kapatın.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>BDC modelini siteden kaldırmak SharePoint için

1. Deneysel Visual Studio menü çubuğunda Derleme Geri **Çek'i**  >  **seçin.**

     Visual Studio BDC modelini SharePoint kaldırır.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Proje öğesi uzantısını dosyadan kaldırmak Visual Studio

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde Dış Veri Listesi **Oluşturucu'ya ve** ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı **kaldırmak istediğinizden** emin olmak için Evet'i seçin.

4. Kaldırma **işlemini tamamlamak için** Şimdi Yeniden Başlat'ı seçin.

5. Her iki Visual Studio (deneysel örnek ve GenerateExternalDataLists çözümünün açık olduğu örnek) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)