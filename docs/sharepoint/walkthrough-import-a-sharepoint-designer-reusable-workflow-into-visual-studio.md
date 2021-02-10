---
title: 'İzlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Içeri aktarma | Microsoft Docs'
titleSuffix: ''
description: Bu kılavuzda, SharePoint Designer 'da oluşturulmuş bir yeniden kullanılabilir iş akışını Visual Studio SharePoint iş akışı projesine aktarın.
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
ms.workload:
- office
ms.openlocfilehash: d4c12626550e36acc1a135258750f2d96ac5e81d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952596"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>İzlenecek yol: SharePoint Designer yeniden kullanılabilir iş akışını Içeri aktarma

  Bu izlenecek yolda, SharePoint Designer 2010 ' de oluşturulan yeniden kullanılabilir bir iş akışının [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint iş akışı projesine nasıl aktarılacağı gösterilmektedir.

 SharePoint Designer veya *bildirim temelli iş akışlarında* oluşturulan iş akışları, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] kod yerine deyimlerden oluşur. SharePoint Designer 2010, taşınabilir ve SharePoint sitelerindeki farklı listeler tarafından kullanılabilen, bildirim temelli iş akışları olan yeniden *kullanılabilir iş akışlarını* tanıtır.

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]Sıralı ve eyalet makine iş akışları gibi ' de oluşturulan iş akışlarına *kod iş* akışları denir. Kod iş akışları, kullanıcıların iş akışının davranışını özelleştirebileceği XML dosyalarından ve kod modüllerinden oluşur.

 Visual Studio, SharePoint Designer 2010 ' de oluşturulan yeniden kullanılabilir iş akışlarını içeri aktarmanızı ve bunları SharePoint sitelerinizde kullanılmak üzere kod iş akışlarına dönüştürmenizi sağlar.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- SharePoint tasarımcısında basit, yeniden kullanılabilir bir iş akışı oluşturma.

- SharePoint Designer yeniden kullanılabilir iş akışını bir *. wsp* dosyasına ve SharePoint 'e aktarma.

- *. Wsp* dosyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Içeri aktarma yeniden kullanılabilir iş akışı projesini kullanarak içine aktarma.

- Kod ekleyerek iş akışını değiştirme.

- İçeri aktarılan iş akışını bir SharePoint sitesinde kullanma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Ve SharePoint 'in desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] .

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Hedef SharePoint alt siteleri oluştur
 İlk olarak iki yeni SharePoint alt site oluşturursunuz: bir tane, yeniden kullanılabilir iş akışlarını SharePoint Designer 'dan barındırmak için, başka bir deyişle dönüştürülen iş akışlarını barındırmak için

#### <a name="to-create-sharepoint-subsites"></a>SharePoint alt siteleri oluşturmak için

1. SharePoint Designer 2010 ' de, menü çubuğunda **Dosya**  >  **Yeni boş Web sitesi**' ni seçin.

2. **Yeni boş Web sitesi** iletişim kutusunda, iş akışını oluşturmak Istediğiniz bir SharePoint sitesine gidin veya http://<em>SystemName</em>/değerini kullanın ve **Tamam** düğmesini seçin.

    Giriş sayfası görüntülenir.

3. **Alt siteler** bölümünde **Yeni** düğmesini seçin.

4. **Yeni** iletişim kutusunda sol bölmedeki listeden **SharePoint şablonları** ' nı seçin ve sağ bölmedeki listeden **ekip sitesi** ' ni seçin.

5. **Web sitesinin konumunu belirtin** kutusunda URL 'deki Word **alt** sitesini **SPD1** ile değiştirin ve **Tamam** düğmesini seçin.

    Bu, yeni alt siteyi SharePoint Designer 'a açar. SharePoint Designer 'ın bu örneğini kapatın ve ilk örneğe (en üst düzey site) geri dönün.

6. İkinci alt siteyi oluşturmak için 3-5 adımlarını yineleyin. bu kez, içindeki Word **alt** öğesini [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] **SPD2** ile değiştirin.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer yeniden kullanılabilir iş akışı oluşturma
 SharePoint Bu örnek için kullanabileceğiniz herhangi bir yeniden kullanılabilir iş akışı içermediğinden, bir tane oluşturacaksınız. Bu basit iş akışında, bir kullanıcı görev listesinde belirli bir başlığa sahip yeni bir görev girdiğinde, görev bu kullanıcıya atanır.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer yeniden kullanılabilir iş akışı oluşturmak için

1. **Alt siteler** bölümünde, değiştirmek için **SPD1** sitesini seçin.

2. Şeritte yeniden **kullanılabilir Iş akışı** düğmesini seçin.

     Yeniden kullanılabilir Iş akışı oluşturma Sihirbazı görünür.

3. **Ad** kutusunda, **SPD görev iş akışı**' nı girin.

4. **Içerik türü** listesinde **görev**' i ve ardından **Tamam** düğmesini seçin.

     İş akışı SharePoint Designer iş akışı Tasarımcısı 'nda açılır.

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
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yalnızca *. wsp* dosyalarını içeri aktarabildiğinden, yeniden kullanılabilir iş akışını bir *. wsp* dosyası olarak kaydetmeli ve içine aktarmadan önce SharePoint 'e dağıtmanız gerekir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Aşağıdaki yordamı gerçekleştirirken bir çalışma zamanı hatası alırsanız, yordamı SharePoint sitesine erişimi olan bir sistemde gerçekleştirmeniz gerekir.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Yeniden kullanılabilir iş akışını kaydetmek ve dağıtmak için

1. SharePoint Designer 'ın en üstünde **Kaydet** düğmesini seçerek ilerlemenizi kaydedin ve sonra Iş akışını **SPD1** SharePoint sitesine dağıtmak için **Yayımla** düğmesini seçin.

2. Gezinti bölmesinde, **Iş akışları** nesnesini seçin.

3. Yeniden **kullanılabilir Iş akışı** altında **SPD görev iş akışı**' nı seçin.

4. Şeritte, iş akışını bir *. wsp* dosyası olarak kaydetmek için **şablon olarak kaydet** düğmesini seçin.

5. SharePoint 'te *. wsp* dosyasını görüntülemek için **SPD1** SharePoint sitesini bir tarayıcıda açın.

6. Hızlı Başlat çubuğunda **Kitaplıklar** bağlantısını seçin.

7. **Belge kitaplıkları** bölümünde, **site varlıkları** bağlantısını seçin.

     **SPD görev Iş akışı** dosyası diğer site varlıkları ile listelenir.

8. Dosya listesinde, bu dosyanın adını seçin

9. **Dosya indirme** iletişim kutusunda, *. wsp* dosyasını yerel sisteminize kaydetmek için **Kaydet** düğmesini seçin.

## <a name="import-the-wsp-file-into-visual-studio"></a>. Wsp dosyasını Visual Studio 'ya aktarma
 *. Wsp* dosyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Içeri aktarma yeniden kullanılabilir iş akışı projesi kullanarak içine aktarın. Bu proje iş akışını yeniden kullanılabilir, bildirime dayalı bir iş akışından kod akışına dönüştürür. İş akışı dönüştürüldükten sonra, davranışını değiştirmek için kod kullanacaksınız.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Bir iş akışını .wsp dosyasından içeri aktarmak ve değiştirmek için

1. ' Nde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **Şablonlar** bölmesinde, yeniden **kullanılabilir SharePoint 2010 iş akışı** şablonunu seçin, projenin adını **WorkflowImportProject1** olarak bırakın ve **Tamam** düğmesini seçin.

    SharePoint Özelleştirme Sihirbazı görüntülenir.

4. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] daha önce oluşturduğunuz ikinci SharePoint alt sitesi için şunu girin: http://<em>sistem adı</em>/spd3.

5. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından **İleri** düğmesini seçin.

    Korumalı Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

6. **Yeni proje kaynağını belirtin** sayfasında, daha önce *. wsp* dosyasını kaydettiğiniz sistemdeki konuma gidin, dosyayı açın ve sonra **İleri** düğmesini seçin.

   > [!NOTE]
   > *. Wsp* dosyasındaki tüm kullanılabilir öğeleri içe aktarmak için **son** düğmesini seçin.

    Bu, içeri aktarmaya uygun yeniden kullanılabilir iş akışlarının bir listesini görüntüler.

7. **İçeri aktarılacak öğeleri seçin** kutusunda, **SPD görev iş akışı** iş akışını seçin ve ardından **son** düğmesini seçin.

    İçeri aktarma işlemi tamamlandıktan sonra, **SPD_Workflow_TestFT** adlı bir iş akışını içeren **WorkflowImportProject1** adlı bir proje oluşturulur. Bu klasörde, iş akışının tanım dosyası *Elements.xml* ve iş akışı Tasarımcısı dosyası (*. xoml*). Tasarımcı iki dosya içerir: kurallar dosyası (. Rules) ve arka plan kod dosyası (projenizin programlama diline bağlı olarak *. cs* veya *. vb*).

8. **Çözüm Gezgini**, **Içeri aktarılan diğer dosyalar** klasörünü silin.

9. *Elements.xml* dosyasında, öğesini silin `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. **Çözüm Gezgini**' de, **WorkflowImportProject1**' ı seçin ve ardından menü çubuğunda, Başlangıç   >  öğesi olarak **WorkflowImportProject1** ayarlamak için **Başlangıç projesi olarak proje ayarla** ' yı seçin.

     Bu, projede hata ayıklarken listeyi hemen görüntüler.

11. **Içeri aktarma yeniden kullanılabilir SharePoint 2010 Iş akışı** şablonu içeri aktarılan iş akışı için ilişkilendirme özelliği değerlerini içeri aktarmadığından, bunları girmeniz gerekir. Bunu yapmak için:

    1. **Çözüm Gezgini** **SPD_Workflow_TestFT** düğümünü seçin.

    2. **Hedef liste** özelliği gibi liste özelliklerinden birinin yanındaki üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

    3. SharePoint Özelleştirme Sihirbazı 'nda eksik değerleri doldurup **son** düğmesini seçin.

12. . Xoml dosyasını seçin ve ardından menü çubuğunda,   >  içeri aktarılan iş akışını iş akışı tasarımcısında görüntülemek için Görünüm **Tasarımcısı** ' nı seçin.

13. **Araç kutusunun** **Windows Workflow v 3.0** düğümünde aşağıdaki adımlardan birini gerçekleştirin:

    - **Kod** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **SequenceActivity1** etkinliğinin altındaki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    - **Kod** etkinliğini **araç kutusu** ' ndan iş akışı tasarımcısına sürükleyin ve **SequenceActivity1** etkinliğinin altındaki satıra bağlayın.

      Bu, **CodeActivity1** adlı iş akışı tasarımcısına bir etkinlik ekler. Bu etkinlikte Kullanıcı iş akışını başlattığında Duyurular listesinde duyuru oluşturan bir kod eylemi ekleyeceksiniz.

14. Aşağıdaki adım kümelerinden birini uygulayın:

    - Bir olay işleyicisi oluşturmak ve kodu görüntülemek için **CodeActivity1** öğesine çift tıklayın.

    - **CodeActivity1** için **Özellikler** penceresinde, **ExecuteCode** özelliğinin değerini **codeActivity_ExecuteCode** olarak ayarlayın.

15. Var olan **using** veya **Imports** yönergelerinin altına şunu ekleyin:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. `codeActivity1_ExecuteCode`Şu kodla değiştirin:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtın ve iş akışını ilişkilendirin
 Sonra, bir SharePoint sitesine dağıtmak için WorkflowImportProject1 çalıştırın ve sonra değiştirilmiş, dönüştürülmüş iş akışını görüntülemek ve test etmek için iş akışını Görevler listesiyle ilişkilendirirsiniz.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Projeyi dağıtmak ve iş akışını ilişkilendirmek için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dönüştürülen iş akışı projesini çalıştırmak ve dağıtmak Için **F5** tuşunu seçin.

2. Hızlı Başlat çubuğunda görevler listesini göstermek için **Görevler** bağlantısını seçin.

3. **Liste araçları** sekmesinde, **öğeler** düğmesini seçin ve sonra **Yeni öğe** düğmesini seçin.

     **Görevler-yeni öğe** iletişim kutusu açılır.

4. **Başlık** kutusuna **Yeni görev** girin ve **Kaydet** düğmesini seçin.

5. **Liste araçları** sekmesinde **liste** düğmesini seçin ve ardından **Liste ayarları** düğmesini seçin.

     **Liste ayarları** sayfası görüntülenir.

6. **İzinler ve yönetim** bölümünde, **iş akışı ayarları** bağlantısını seçin.

     **Iş akışı ayarları** sayfası görüntülenir.

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
- [Mevcut bir SharePoint sitesinden öğeleri içeri aktar](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
