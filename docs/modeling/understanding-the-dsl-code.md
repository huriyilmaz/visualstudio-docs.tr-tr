---
title: DSL Kodunu Anlama
description: Domain-Specific Dili (DSL) çözümünün, Visual Studio'da DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API'yi nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0b2b0ea3b094452258e6252412a9ace768672f6d2956b4311613e4ca3ac0a08b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398260"
---
# <a name="understanding-the-dsl-code"></a>DSL Kodunu Anlama

Domain-Specific Dili (DSL) çözümü, Visual Studio'de DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API oluşturur. Bu API, DSL tanımından oluşturulan kodda tanımlanır. Bu konu başlığında, oluşturulan API açıklanmıştır.

## <a name="the-example-solution-component-diagrams"></a>Örnek çözüm: Bileşen Diyagramları

Bu konudaki örneklerin çoğunun kaynağı olan çözümü oluşturmak için Bileşen  Modelleri çözüm şablonundan bir DSL oluşturun. Bu, yeni bir DSL çözümü oluşturmada görüntülenen standart şablonlardan biridir.

> [!NOTE]
> Bileşen Diyagramları DSL şablonu, **Alana Özgü Dil Tasarımcısı.**

F5 **tuşuna** basın ve bu çözüm şablonu hakkında bilgi sahibi değilsanız denemeyi deneyin. Özellikle bir bağlantı noktası aracını bileşene sürükleyerek bağlantı noktaları oluşturabilirsiniz ve bağlantı noktalarına bağlanabilirsiniz.

![Bileşenler ve birbirine bağlı bağlantı noktaları](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>DSL Çözümünün Yapısı
 **Dsl projesi,** DSL'nizin API'sini tanımlar. **DslPackage projesi,** Visual Studio. Ayrıca, modelden oluşturulan kodu içeren kendi projelerinizi de ekebilirsiniz.

### <a name="the-code-directories"></a>Kod dizinleri
 Bu projelerin her bir kodun çoğu **Dsl\DslDefinition.dsl konumundan oluşturulur.** Oluşturulan kod, Oluşturulan **Kod klasöründedir.** Oluşturulan bir dosyayı görmek için, oluşturan **.tt** dosyasının yanındaki **[+]** dosyasına tıklayın.

 DSL'i anlamanıza yardımcı olmak için oluşturulan kodu incelemenizi öneririz. Oluşturulan dosyaları görmek için dosyalarda *.tt Çözüm Gezgini.

 \*.tt dosyaları çok az kod oluşturma içerir. Bunun yerine, paylaşılan `<#include>` şablon dosyalarını dahil etmek için yönergeleri kullanırlar. Paylaşılan dosyalar **\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Tasarımcısı\11.0\TextTemplates** konumunda bulunabilir

 DSL çözümüne kendi program kodunuzu eklerken, oluşturulan kod klasörünün dışında, ayrı bir dosyaya ekleyin. Özel Kod klasörü **oluşturmak istiyor** olabilir. (Özel bir klasöre yeni bir kod dosyası eklerken, ilk kod iskeleti içinde ad alanını düzeltmeyi unutmayın.)

 Çözümü yeniden 7.000.000'den sonra düzenleydiğiniz düzenlemeler kaybedilir ve oluşturulan kodu doğrudan düzenlemenizi önerilmez. Bunun yerine, DSL'nizi özelleştirmek için:

- DSL Tanımı'nın birçok parametresini ayarlayın.

- Oluşturulan sınıflarda tanımlanan veya devralınan yöntemleri geçersiz kılmak için ayrı kod dosyalarında kısmi sınıflar yazın. Bazı durumlarda, oluşturulan bir  yöntemi geçersiz kılmak için DSL Tanımında bir sınıfın Çift Türetilmiş Üretir seçeneğini ayarlamalısiniz.

- DSL Tanımında, oluşturulan kodun kendi kodunuz için 'kancalar' sağlamalarını sağlayacak seçenekleri ayarlayın.

     Örneğin, bir etki alanı sınıfının **Özel Oluşturucuya** Sahip seçeneği ayarlanır ve ardından çözümü oluşturursanız hata iletileriyle karşınız olur. Bu hata iletilerinden birini çift tıklarsanız, oluşturulan kodda özel kodunuzun neler sağlaması gerektiğini açıklayan açıklamalarla karşınıza çıkar.

- Uygulamanıza özgü kod oluşturmak için kendi metin şablonlarınızı yazın. Ekleme dosyalarını kullanarak şablonların birçok proje için ortak olan bölümlerini paylaşabilir ve kendi dosya yapınız ile başlatılan projeleri ayarlamak için Visual Studio proje şablonları oluşturabilirsiniz.

## <a name="generated-files-in-dsl"></a>Dsl'de Oluşturulan Dosyalar
 Aşağıdaki oluşturulan dosyalar Dsl **projesinde** görünür.

 *YourDsl*`Schema.xsd`

 DSL'nizin örneklerini içeren dosyaların şeması. Bu dosya derleme ( bin )**dizinine** kopyalanır. DSL'nizi yükleyinken, model dosyalarının doğrulanması için bu dosyayı **\Program Files\Microsoft Visual Studio 11.0\Xml\Schemas** dizinine kopyaabilirsiniz. Daha fazla bilgi için, [bkz. Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

 DSL Gezgini'nde seçenekleri ayarerek serileştirmeyi özellerseniz şema buna göre değişir. Ancak, kendi serileştirme kodunuzu yazarsanız, bu dosya artık gerçek şemayı temsil etmeyebilirsiniz. Daha fazla bilgi için [bkz. Dosya Depolama ve XML Serileştirmesini Özelleştirme.](../modeling/customizing-file-storage-and-xml-serialization.md)

 `ConnectionBuilders.cs`

 Bağlantı oluşturucu, ilişkiler oluşturan bir sınıftır. Bağlantı aracının arkasındaki koddur. Bu dosya, her bağlantı aracı için bir sınıf çifti içerir. Adları etki alanı ilişkisi ve bağlantı aracının adlarından türetildi: *İlişki* Oluşturucusu ve *ConnectorTool* ConnectAction.

 (Bileşen çözümü örneğinde, bağlantı oluşturucularından biri ConnectionBuilder olarak adlandırılmıştır, Etki alanı ilişkisi Connection olarak adlandırılmış olduğundan bu bir onaytır.)

 İlişki, İlişki *yönteminde* `Builder.Connect()` oluşturulur. Varsayılan sürüm, kaynak ve hedef model öğelerinin kabul edilebilir olduğunu doğrular ve ardından ilişkiyi örnekler. Örnek:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Her oluşturucu sınıfı, DSL Gezgini'nin Bağlantı **Oluşturucuları bölümündeki** bir düğümden oluşturulur. Bir `Connect` yöntem, bir veya daha fazla etki alanı sınıfı çifti arasında ilişkiler oluşturabilir. Her çift, dsl gezgininde oluşturucu düğümü altında Bağlan bağlantı oluşturma yönergesi ile tanımlanır.

 Örneğin, örnek DSL'de üç ilişki türü için bir bağlantı oluşturucu bağlantı Bağlan Yönergeleri eklenmiştir. Bu, kullanıcıya tek bir bağlantı aracı sağlar. Örneklenmiş ilişki türü, kullanıcı tarafından seçilen kaynak ve hedef öğelerin türlerine bağlıdır.  Link Bağlan Yönergeleri eklemek için DSL Gezgini'nde bir oluşturucuya sağ tıklayın.

 Belirli bir etki alanı ilişkisi türü oluşturulduğunda çalıştırılan özel kod yazmak için oluşturucu düğümü altında uygun Bağlantı Bağlan Yönergesi'ne tıklayın. Bu Özellikler penceresi, Uses **Custom Bağlan**. Çözümü yeniden oluşturma ve ardından ortaya çıkan hataları düzeltmek için kod girin.

 Kullanıcı bu bağlantı aracını her kullandığında çalışan özel kod yazmak için, bağlantı **oluşturucusuza ait Is Custom** özelliğini ayarlayın. Bir kaynak öğeye izin verilip izin verilmediğini, kaynak ve hedefin belirli bir bileşimine izin verilip izin verilmediğini ve bağlantı ederken modelde hangi güncelleştirmelerin yapılacaklarını karara varan kodlar sebilirsiniz. Örneğin, yalnızca diyagramda bir döngü oluşturmazsa bir bağlantıya izin veebilirsiniz. Tek bir ilişki bağlantısı yerine, kaynak ve hedef arasında birkaç ilişkili öğenin daha karmaşık bir desenini örneği olarak kullanabilirsiniz.

 `Connectors.cs`

 Genellikle başvuru ilişkilerini temsil eden diyagram öğeleri olan bağlayıcıların sınıflarını içerir. Her sınıf DSL Tanımında bir bağlayıcıdan oluşturulur. Her bağlayıcı sınıfı türetilen <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Çalışma zamanında rengi ve diğer bazı stil özelliklerini değişken yapmak için DSL Tanımı diyagramında sınıfına sağ tıklayın ve Maruz Ekle'nin **üzerine gelin.**

 Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement> .

 `Diagram.cs`

 Diyagramı tanımlayan sınıfı içerir. 'den <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> türetildi.

 Çalışma zamanında rengi ve diğer bazı stil özelliklerini değişken yapmak için DSL Tanımı diyagramında sınıfına sağ tıklayın ve Maruz Ekle'nin **üzerine gelin.**

 Ayrıca, bu dosya `FixupDiagram` modele yeni bir öğe ekleniyorsa yanıt veren kuralını içerir. Kural yeni bir şekil ekler ve şekli model öğesine bağlar.

 `DirectiveProcessor.cs`

 Bu yönerge işlemcisi, kullanıcılarının DSL örneğinizi okumak için metin şablonları yazmalarını sağlar. Yönerge işlemcisi DSL'niz için derlemeleri (DLL) yükler ve ad alanınız `using` için deyimleri etkili bir şekilde ekler. Bu, metin şablonlarındaki kodun DSL'niz içinde tanımlandığı sınıfları ve ilişkileri kullanmalarını sağlar.

 Daha fazla bilgi için, [bkz. Creating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md) and Creating Custom [T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Soyut sınıflar ve model kök sınıfı da dahil olmak üzere tanımlandığı etki alanı sınıflarının uygulamaları. Bunlar, türetilen <xref:Microsoft.VisualStudio.Modeling.ModelElement> .

 Her etki alanı sınıfı şunları içerir:

- Her etki alanı özelliği için bir özellik tanımı ve iç içe işleyici sınıfı. OnValueChanging() ve OnValueChanged() değerlerini geçersiz kılamazsınız. Daha fazla bilgi için [bkz. Etki Alanı Özellik Değeri Değişikliği İşleyicileri.](../modeling/domain-property-value-change-handlers.md)

   Örnek DSL'de sınıfı `Comment` bir özellik ve bir `Text` işleyici sınıfı `TextPropertyHandler` içerir.

- Bu etki alanı sınıfının katıldığı ilişkiler için erişimci özellikleri. (Rol özellikleri için iç içe geçmiş bir sınıf yoktur.)

   Örnek DSL'de `Comment` sınıfının, ekleme ilişkisi aracılığıyla üst modeline erişen erişimcileri `ComponentModelHasComments` vardır.

- Kurucular. Bunları geçersiz kılmak için etki alanı sınıfında **Özel Oluşturucu var'a** ayarlayın.

- Öğe Grubu Prototipi (EGP) işleyici yöntemleri. Kullanıcı başka bir öğeyi bu *sınıfın örneklerine* birleştire (ekleyebilir) ise bunlar gereklidir. Genellikle kullanıcı bunu bir öğe aracından veya başka bir şekilden sürükleyerek veya yapıştırarak yapar.

   Örnek DSL 'de, bir giriş bağlantı noktası veya çıkış bağlantı noktası bir bileşen üzerinde birleştirilebilir. Ayrıca, bileşenler ve açıklamalar model üzerinde birleştirilebilir. VMExtensionProvisioningError hatasından dolayı

   Bileşen sınıfındaki EGP işleyici yöntemleri, bir bileşenin bağlantı noktalarını kabul etmesine izin vermez, ancak açıklamaları kabul etmez. Kök model sınıfındaki EGP işleyicisi açıklamaları ve bileşenleri kabul eder, ancak bağlantı noktalarını kabul etmez.

  `DomainModel.cs`

  Etki alanı modelini temsil eden sınıf. Öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.DomainModel> .

> [!NOTE]
> Bu, modelin kök sınıfıyla aynı değildir.

 Kopyalama ve silme kapanışları, bir öğe kopyalandığında veya silindiğinde diğer öğelerin dahil edileceğini tanımlar. Bu davranışı, her ilişkinin her bir tarafındaki rollerin **Kopyala** ve bu özellik **silme özelliklerini yayar** ayarlayarak denetleyebilirsiniz. Değerlerin dinamik olarak belirlenmesi isterseniz, kapanış sınıflarının yöntemlerini geçersiz kılmak için kod yazabilirsiniz.

 `DomainModelResx.resx`

 Bu, etki alanı sınıfları ve özellikler, özellik adları, araç kutusu etiketleri, standart hata iletileri ve kullanıcıya görüntülenebilecek diğer dizeler gibi dizeler içerir. Ayrıca, görüntü şekilleri için araç simgeleri ve görüntüler içerir.

 Bu dosya, oluşturulan derlemeye bağlanır ve bu kaynakların varsayılan değerlerini sağlar. Kaynakların yerelleştirilmiş bir sürümünü içeren bir uydu derlemesi oluşturarak DSL 'nizi yerelleştirebilirsiniz. Bu sürüm, DSL yerelleştirilmiş kaynaklarla eşleşen bir kültüre yüklendiğinde kullanılacaktır. Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

 `DomainRelationships.cs`

 Bir modeldeki iki öğe arasındaki her bağlantı, bir etki alanı ilişki sınıfının örneğiyle temsil edilir. Tüm ilişki sınıfları öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.ElementLink> ve bu, sırasıyla öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.ModelElement> . Bir ModelElement olduğundan, ilişkinin bir örneği özelliklere sahip olabilir ve bir ilişkinin kaynağı veya hedefi olabilir.

 `HelpKeywordHelper.cs`

 Kullanıcı F1 tuşuna bastığında kullanılan işlevleri sağlar.

 `MultiplicityValidation.cs`

 1... 1 veya 1.. * çokluğunu belirttiğiniz ilişki rollerinde, Kullanıcı ilişkinin en az bir örneğinin gerekli olduğu konusunda uyarılmalıdır. Bu dosya, bu uyarıları uygulayan doğrulama kısıtlamalarını sağlar. 1.. 1 gömme üst öğesine bağlantı doğrulanmadı.

 Bu kısıtlamaların yürütülmesi için DSL Gezgini 'ndeki **Editor\validation** düğümündeki **...** seçeneklerinden birini ayarlamış olmanız gerekir. Daha fazla bilgi için bkz. [Domain-Specific dilinde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Bu dosya yalnızca bir etki alanı özelliğine özel bir tür tanımlayıcısı eklediyseniz kod içerir. Daha fazla bilgi için bkz. [Özellikler penceresini özelleştirme](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Aynı bilinen iki öğeye başvurulmadan emin olmak için bir doğrulama yöntemi. daha fazla bilgi için bkz. [dosya Depolama ve XML serileştirmesini özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

- Serileştirme sınıfları tarafından yaygın olarak kullanılan işlevleri sağlayan SerializationHelper sınıfı.

  `Serializer.cs`

  Her etki alanı sınıfı, ilişki, şekil, bağlayıcı, Diyagram ve model için seri hale getirici sınıfı.

  Bu sınıfların özelliklerinin birçoğu, **XML serileştirme davranışı** altında DSL Gezgini 'ndeki ayarlar tarafından denetlenebilir.

  `Shapes.cs`

  DSL tanımındaki her şekil sınıfı için bir sınıf. Şekiller öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> . daha fazla bilgi için bkz. [dosya Depolama ve XML serileştirmesini özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

  Oluşturulan yöntemleri kısmi bir sınıfta kendi yöntemleriniz ile geçersiz kılmak için, küme, DSL tanımındaki bağlayıcı için **çift türetilmiş oluştur oluşturur** . Bir oluşturucuyu kendi kodunuzla değiştirmek için, kümesinin **özel Oluşturucusu vardır**.

  Çalışma zamanında rengi ve diğer stil özellikleri değişkenlerini yapmak için, DSL tanımı diyagramında sınıfa sağ tıklayın ve **sunulan Ekle**' ye gelin.

  Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. Örneğin <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Öğesi grup prototiplerini öğe araçlarına yükleyerek araç kutusunu ayarlar. Bu prototiptürlerin kopyaları, Kullanıcı aracı çalıştırdığında hedef öğelerle birleştirilir.

  `CreateElementPrototype()`Birkaç nesne grubunu oluşturan bir araç kutusu öğesi tanımlamak için geçersiz kılabilirsiniz. Örneğin, alt bileşenlere sahip nesneleri temsil etmek için bir öğe tanımlayabilirsiniz. kodu değiştirdikten sonra, araç kutusu önbelleğini temizlemek için Visual Studio deneysel örneğini sıfırlayın.

## <a name="generated-files-in-the-dslpackage-project"></a>DslPackage projesinde oluşturulan dosyalar
 dslpackage,, pencereyi, araç kutusunu ve menü komutlarını yönetmek için DSL modelini Visual Studio shell 'e bağar. Sınıfların çoğu çift türetilir, böylece yöntemlerinden herhangi birini geçersiz kılabilirsiniz.

 `CommandSet.cs`

 Diyagramda görünür olan sağ tıklama menü komutları. Bu kümeyi uyarlayabilir veya ekleyebilirsiniz. Bu dosya, komutların kodunu içerir. Menülerde komutların konumu Commands. vsct dosyası tarafından belirlenir. Daha fazla bilgi için bkz. [Kullanıcı komutları ve eylemleri yazma](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `Constants.cs`

 Yapılamıyor.

 `DocData.cs`

 *Yourdsl* `DocData` bir modelin yüklenmesini ve dosyaya kaydedilmesini yönetir ve mağaza örneği oluşturur.

 Örneğin, DSL 'yi bir dosya yerine bir veritabanına kaydetmek istiyorsanız, `Load` ve yöntemlerini geçersiz kılabilirsiniz `Save` .

 `DocView.cs`

 *Yourdsl* `DocView` Diyagramın göründüğü pencereyi yönetir. Örneğin, diyagramı bir Windows formu içine katabilirsiniz:

 DslPackage projesine bir kullanıcı denetim dosyası ekleyin. Diyagramın görüntülenebileceği bir panel ekleyin. Düğmeleri ve diğer denetimleri ekleyin. Formun kod görünümünde, aşağıdaki kodu ekleyerek adı DSL 'nize göre ayarlama:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}
```

 `EditorFactory.cs`

 `DocData`Ve oluşturur `DocView` . DSL paketiniz başlatıldığında bir düzenleyiciyi açmak için Visual Studio kullanılan standart bir arabirimi karşılar. Bu, `ProvideEditorFactory` Package. cs dosyasındaki özniteliğinde başvurulur

 `GeneratedVSCT.vsct`

 Menülerde sağ tıklama (bağlam) menüsü, **düzenleme** menüsü gibi menülerde standart menü komutlarını bulur. Komutların kodu CommandSet. cs dosyasında bulunur. Standart komutları yeniden konumlandıralabilir veya değiştirebilir ve kendi komutlarınızı ekleyebilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı komutları ve eylemleri yazma](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `ModelExplorer.cs`

 DSL için model Gezginini tanımlar. Bu, kullanıcının diyagram ile birlikte gördüğü modelin ağaç görünümüdür.

 Örneğin, `InsertTreeView()` model Gezgininde öğelerin görünme sırasını değiştirmek için geçersiz kılabilirsiniz.

 Model Gezgini 'ndeki seçimin diyagram seçimiyle eşitlenmiş kalmasını istiyorsanız aşağıdaki kodu kullanabilirsiniz:

```csharp
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}
```

 `ModelExplorerToolWindow.cs`

 Model Gezgini 'nin görüntülendiği pencereyi tanımlar. Gezgin içindeki öğelerin seçimini işler.

 `Package.cs`

 Bu dosya, DSL 'nin Visual Studio nasıl tümleştirildiğini tanımlar. Paket sınıfındaki öznitelikler, dosya uzantınızı içeren dosyalar için bir işleyici olarak DSL 'yi kaydeder, onun araç kutusunu tanımlar ve yeni bir pencerenin nasıl açılacağını tanımlar. ınitialize () yöntemi, ilk DSL bir Visual Studio örneğine yüklendiğinde bir kez çağrılır.

 `Source.extension.vsixmanifest`

 Bu dosyayı özelleştirmek için `.tt` dosyayı düzenleyin.

> [!WARNING]
> . Tt dosyasını simgeler veya görüntüler gibi kaynakları içerecek şekilde düzenlerseniz, kaynağın VSıX derlemesinde bulunduğundan emin olun. Çözüm Gezgini, dosyayı seçin ve **VSIX 'e dahil et** özelliğinin olduğundan emin olun `True` .

 bu dosya, DSL 'nin bir Visual Studio tümleştirme uzantısı 'na (vsıx) nasıl paketlendiğini denetler. Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Domain-Specific dilini özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
