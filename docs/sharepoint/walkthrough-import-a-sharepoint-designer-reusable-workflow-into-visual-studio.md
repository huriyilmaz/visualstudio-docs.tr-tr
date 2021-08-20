---
title: 'izlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını içeri aktarma | Microsoft Docs'
titleSuffix: ''
description: bu kılavuzda, SharePoint tasarımcısında oluşturulan yeniden kullanılabilir bir iş akışını Visual Studio SharePoint iş akışı projesine aktarın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ab8357b126ab2bfacea24cd3b922baa40fb25da4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148759"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>izlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını içeri aktarma

  bu izlenecek yol, SharePoint tasarımcısı 2010 ' de oluşturulan yeniden kullanılabilir bir iş akışının [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint bir iş akışı projesine nasıl aktarılacağını gösterir.

 SharePoint tasarımcısında veya *bildirim temelli iş akışlarında* oluşturulan iş akışları, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] kod yerine deyimlerden oluşur. SharePoint tasarımcı 2010, taşınabilir ve SharePoint sitelerde farklı listeler tarafından kullanılabilen, bildirim temelli iş akışları olan yeniden *kullanılabilir iş akışlarını* tanıtır.

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]Sıralı ve eyalet makine iş akışları gibi ' de oluşturulan iş akışlarına *kod iş* akışları denir. Kod iş akışları, kullanıcıların iş akışının davranışını özelleştirebileceği XML dosyalarından ve kod modüllerinden oluşur.

 Visual Studio, SharePoint tasarımcı 2010 ' de oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarmanızı ve bunları SharePoint sitelerinizde kullanılmak üzere kod iş akışlarına dönüştürmenizi sağlar.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- SharePoint tasarımcısında basit ve yeniden kullanılabilir bir iş akışı oluşturma.

- SharePoint Designer yeniden kullanılabilir iş akışını bir *. wsp* dosyasına ve SharePoint içine aktarma.

- *. Wsp* dosyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Içeri aktarma yeniden kullanılabilir iş akışı projesini kullanarak içine aktarma.

- Kod ekleyerek iş akışını değiştirme.

- içeri aktarılan iş akışını bir SharePoint sitesinde kullanma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]Ve SharePoint desteklenen sürümleri.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint tasarımcısı 2010.

## <a name="create-target-sharepoint-subsites"></a>hedef SharePoint alt siteleri oluştur
 ilk olarak iki yeni SharePoint alt site oluşturursunuz: biri SharePoint tasarımcısından yeniden kullanılabilir iş akışlarını barındırmak için, başka bir deyişle, dönüştürülmüş iş akışlarını barındırmak için.

#### <a name="to-create-sharepoint-subsites"></a>SharePoint alt siteleri oluşturmak için

1. SharePoint tasarımcı 2010 ' de, menü çubuğunda **dosya**  >  **yeni boş Web sitesi**' ni seçin.

2. **yeni boş Web sitesi** iletişim kutusunda, iş akışını oluşturmak istediğiniz SharePoint sitesine gidin veya http://<em>systemname</em>/değerini kullanın ve **tamam** düğmesini seçin.

    Giriş sayfası görüntülenir.

3. **Alt siteler** bölümünde **Yeni** düğmesini seçin.

4. **yeni** iletişim kutusunda sol bölmedeki listeden **SharePoint şablonlar** ' ı seçin ve sağ bölmedeki listeden **ekip sitesi** ' ni seçin.

5. **Web sitesinin konumunu belirtin** kutusunda URL 'deki Word **alt** sitesini **SPD1** ile değiştirin ve **Tamam** düğmesini seçin.

    bu, yeni alt siteyi SharePoint tasarımcısında açar. SharePoint Designer 'ın bu örneğini kapatın ve ilk örneğe (en üst düzey site) geri dönün.

6. İkinci alt siteyi oluşturmak için 3-5 adımlarını yineleyin. bu kez, içindeki Word **alt** öğesini [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] **SPD2** ile değiştirin.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer yeniden kullanılabilir iş akışı oluşturma
 SharePoint bu örnek için kullanabileceğiniz herhangi bir yeniden kullanılabilir iş akışı içermediğinden, bir tane oluşturacaksınız. Bu basit iş akışında, bir kullanıcı görev listesinde belirli bir başlığa sahip yeni bir görev girdiğinde, görev bu kullanıcıya atanır.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer yeniden kullanılabilir iş akışı oluşturmak için

1. **Alt siteler** bölümünde, değiştirmek için **SPD1** sitesini seçin.

2. Şeritte yeniden **kullanılabilir Iş akışı** düğmesini seçin.

     Yeniden kullanılabilir Iş akışı oluşturma Sihirbazı görünür.

3. **Ad** kutusunda, **SPD görev iş akışı**' nı girin.

4. **Içerik türü** listesinde **görev**' i ve ardından **Tamam** düğmesini seçin.

     iş akışı SharePoint tasarımcısı iş akışı tasarımcısı 'nda açılır.

5. İş akışı tasarımcısında 1. adım ' ı ve ardından şeritte **koşul** düğmesini seçin.

6. Koşullar listesinde, **geçerli öğe alanının değere eşit olup olmadığını** seçin.

     Bu adım **, alan eşitse** adlı bir koşul ekler.

7. **IF alanı değer koşulunu eşitse** **alan** bağlantısını seçin.

8. Değer listesinde **başlık**' ı seçin.

9. **IF alanı değer koşulunu eşitse** **değer** bağlantısını seçin.

10. Kutuya **Yeni görev** girin.

     Koşul ekstresi artık **geçerli öğe: başlık yeni göreve eşitse** okur.

11. Koşul ifadesinin altındaki satırı seçin ve ardından şeritte **eylem** düğmesini seçin.

12. Eylemler listesinde, **geçerli öğedeki alanı ayarla**' yı seçin.

13. **Alandan değere Ayarla** eyleminde, **alan** bağlantısını seçin ve ardından listede **atanan**' ı seçin.

14. **Alandan değere Ayarla** eyleminde **değer** bağlantısını seçin ve ardından mevcut kullanıcılar ve Gruplar listesinde **öğeyi oluşturan kullanıcı**' yı seçin.

15. **Ekle** düğmesini ve sonra **Tamam** düğmesini seçin.

     Eylem ekstresi şimdi **geçerli öğeye atanan ayarla ' yı okur: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Yeniden kullanılabilir iş akışını kaydetme ve dağıtma
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]yalnızca *. wsp* dosyalarını içeri aktarabildiğinden, yeniden kullanılabilir iş akışını bir *. wsp* dosyası olarak kaydetmeli ve içine aktarmadan önce SharePoint dağıtmanız gerekir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> aşağıdaki yordamı gerçekleştirirken bir çalışma zamanı hatası alırsanız, yordamı SharePoint sitesine erişimi olan bir sistemde gerçekleştirmeniz gerekir.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Yeniden kullanılabilir iş akışını kaydetmek ve dağıtmak için

1. SharePoint tasarımcısının en üstünde **kaydet** düğmesini seçerek ilerlemenizi kaydedin ve sonra iş akışını **SPD1** SharePoint sitesine dağıtmak için **yayımla** düğmesini seçin.

2. Gezinti bölmesinde, **Iş akışları** nesnesini seçin.

3. Yeniden **kullanılabilir Iş akışı** altında **SPD görev iş akışı**' nı seçin.

4. Şeritte, iş akışını bir *. wsp* dosyası olarak kaydetmek için **şablon olarak kaydet** düğmesini seçin.

5. SharePoint içinde *. wsp* dosyasını görüntülemek için **SPD1** SharePoint sitesini bir tarayıcıda açın.

6. Hızlı Başlat çubuğunda **Kitaplıklar** bağlantısını seçin.

7. **Belge kitaplıkları** bölümünde, **site varlıkları** bağlantısını seçin.

     **SPD görev Iş akışı** dosyası diğer site varlıkları ile listelenir.

8. Dosya listesinde, bu dosyanın adını seçin

9. **Dosya indirme** iletişim kutusunda, *. wsp* dosyasını yerel sisteminize kaydetmek için **Kaydet** düğmesini seçin.

## <a name="import-the-wsp-file-into-visual-studio"></a>. Wsp dosyasını Visual Studio içine aktarın
 *. Wsp* dosyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Içeri aktarma yeniden kullanılabilir iş akışı projesi kullanarak içine aktarın. Bu proje iş akışını yeniden kullanılabilir, bildirime dayalı bir iş akışından kod akışına dönüştürür. İş akışı dönüştürüldükten sonra, davranışını değiştirmek için kod kullanacaksınız.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Bir iş akışını .wsp dosyasından içeri aktarmak ve değiştirmek için

1. ' nde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **şablonlar** bölmesinde, yeniden **kullanılabilir SharePoint 2010 iş akışı** şablonunu seçin, projenin adını **WorkflowImportProject1** olarak bırakın ve **tamam** düğmesini seçin.

    SharePoint özelleştirme sihirbazı görüntülenir.

4. **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] daha önce oluşturduğunuz ikinci SharePoint alt site için şunu girin: http://<em>sistem adı</em>/spd3.

5. **bu SharePoint çözümü için güven düzeyi nedir?** bölümünde, **grup çözümü olarak dağıt** seçenek düğmesini seçin ve sonra **ileri** düğmesini seçin.

    Korumalı Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

6. **Yeni proje kaynağını belirtin** sayfasında, daha önce *. wsp* dosyasını kaydettiğiniz sistemdeki konuma gidin, dosyayı açın ve sonra **İleri** düğmesini seçin.

   > [!NOTE]
   > *. Wsp* dosyasındaki tüm kullanılabilir öğeleri içe aktarmak için **son** düğmesini seçin.

    Bu, içeri aktarmaya uygun yeniden kullanılabilir iş akışlarının bir listesini görüntüler.

7. **İçeri aktarılacak öğeleri seçin** kutusunda, **SPD görev iş akışı** iş akışını seçin ve ardından **son** düğmesini seçin.

    İçeri aktarma işlemi tamamlandıktan sonra, **SPD_Workflow_TestFT** adlı bir iş akışını içeren **WorkflowImportProject1** adlı bir proje oluşturulur. Bu klasörde, iş akışının tanım dosyası *Elements.xml* ve iş akışı Tasarımcısı dosyası (*. xoml*). Tasarımcı iki dosya içerir: kurallar dosyası (. Rules) ve arka plan kod dosyası (projenizin programlama diline bağlı olarak *. cs* veya *. vb*).

8. **Çözüm Gezgini**, **Içeri aktarılan diğer dosyalar** klasörünü silin.

9. *Elements.xml* dosyasında, öğesini silin `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. **Çözüm Gezgini**' de, **WorkflowImportProject1**' ı seçin ve ardından menü çubuğunda, başlangıç   >  öğesi olarak **WorkflowImportProject1** ayarlamak için Project **başlangıç Project olarak ayarla** ' yı seçin.

     Bu, projede hata ayıklarken listeyi hemen görüntüler.

11. **içeri aktarma SharePoint 2010 iş akışı** şablonu içeri aktarılan iş akışı için ilişkilendirme özelliği değerlerini içeri aktarmadığından, bunları girmeniz gerekir. Bunu yapmak için:

    1. **Çözüm Gezgini** **SPD_Workflow_TestFT** düğümünü seçin.

    2. **hedef liste** özelliği gibi liste özelliklerinden birinin yanındaki üç nokta (![ASP.NET Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) düğmesini seçin.

    3. SharePoint özelleştirme sihirbazında eksik değerleri girin ve ardından **son** düğmesini seçin.

12. . Xoml dosyasını seçin ve ardından menü çubuğunda,   >  içeri aktarılan iş akışını iş akışı tasarımcısında görüntülemek için Görünüm **Tasarımcısı** ' nı seçin.

13. **araç kutusunun** **Windows Workflow v 3.0** düğümünde aşağıdaki adımlardan birini gerçekleştirin:

    - **Kod** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **SequenceActivity1** etkinliğinin altındaki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    - **Kod** etkinliğini **araç kutusu** ' ndan iş akışı tasarımcısına sürükleyin ve **SequenceActivity1** etkinliğinin altındaki satıra bağlayın.

      Bu, **CodeActivity1** adlı iş akışı tasarımcısına bir etkinlik ekler. Bu etkinlikte Kullanıcı iş akışını başlattığında Duyurular listesinde duyuru oluşturan bir kod eylemi ekleyeceksiniz.

14. Aşağıdaki adım kümelerinden birini uygulayın:

    - Bir olay işleyicisi oluşturmak ve kodu görüntülemek için **CodeActivity1** öğesine çift tıklayın.

    - **CodeActivity1** için **Özellikler** penceresinde, **ExecuteCode** özelliğinin değerini **codeActivity_ExecuteCode** olarak ayarlayın.

15. Var olan **using** veya **Imports** yönergelerinin altına şunu ekleyin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb" id="Snippet1":::

16. `codeActivity1_ExecuteCode`Şu kodla değiştirin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb" id="Snippet2":::

## <a name="deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtın ve iş akışını ilişkilendirin
 sonra, bir SharePoint sitesine dağıtmak için WorkflowImportProject1 çalıştırın ve ardından değiştirilen, dönüştürülmüş iş akışını görüntülemek ve test etmek için iş akışını görevler listesiyle ilişkilendirirsiniz.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtmak ve iş akışını ilişkilendirmek için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dönüştürülen iş akışı projesini çalıştırmak ve dağıtmak Için **F5** tuşunu seçin.

2. Hızlı Başlat çubuğunda görevler listesini göstermek için **Görevler** bağlantısını seçin.

3. **Liste araçları** sekmesinde, **öğeler** düğmesini seçin ve sonra **Yeni öğe** düğmesini seçin.

     **Görevler-yeni öğe** iletişim kutusu açılır.

4. **Başlık** kutusuna **Yeni görev** girin ve **Kaydet** düğmesini seçin.

5. **liste araçları** sekmesinde **liste** düğmesini seçin ve ardından **liste Ayarlar** düğmesini seçin.

     **liste Ayarlar** sayfası görüntülenir.

6. **izinler ve yönetim** bölümünde, **iş akışı Ayarlar** bağlantısını seçin.

     **iş akışı Ayarlar** sayfası görüntülenir.

7. **Iş akışı Ekle** bağlantısını seçin.

8. **Iş akışı** listesinde **WorkflowImportProject1-SPD iş akışı sınaması**' nı seçin.

9. **Ad** kutusunda, **SPD iş akışı testi** girin ve **Tamam** düğmesini seçin.

10. Hızlı Başlat çubuğunda **Görevler** listesini seçin.

11. **Yeni görev**' in yanındaki oku seçin ve ardından listede **iş akışları**' nı seçin.

12. **Yeni bir Iş akışı Başlat** bölümünde, **SPD iş akışı testinin** bağlantısını seçin ve ardından Iş akışını başlatmak için **Başlat** düğmesini seçin.

    > [!NOTE]
    > Alternatif olarak, iş akışı ayarları Sihirbazı 'nı çalıştırarak ve iş akışını otomatik ilişkilendirmek üzere ayarlayarak bir iş akışını bir listeyle otomatik olarak ilişkilendirebilirsiniz.

     İş akışı tarafından iki eylem gerçekleştirildiğine dikkat edin: adınızın görevin **atanan** sütununda göründüğünü ve **Duyurular** listesinde bir duyuru göründüğünü unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
