---
title: DSL Kodunu Anlama
description: Domain-Specific Language (DSL) çözümünün, Visual Studio'da DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API'yi nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84f75298bc2854172eb7ec63bd6412e5703cfad7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388587"
---
# <a name="understanding-the-dsl-code"></a>DSL Kodunu Anlama

Domain-Specific Dili (DSL) çözümü, Visual Studio'da DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API oluşturur. Bu API, DSL tanımından oluşturulan kodda tanımlanır. Bu konu başlığında, oluşturulan API açıklanmıştır.

## <a name="the-example-solution-component-diagrams"></a>Örnek çözüm: Bileşen Diyagramları

Bu konudaki örneklerin çoğunun kaynağı olan çözümü oluşturmak için Bileşen  Modelleri çözüm şablonundan bir DSL oluşturun. Bu, yeni bir DSL çözümü oluşturmada görüntülenen standart şablonlardan birisidir.

> [!NOTE]
> Bileşen Diyagramları DSL şablonu, **Alana Özgü Dil Tasarımcısı.**

F5 **tuşuna** basın ve bu çözüm şablonunu tanımadıysanız denemeyi deneyin. Özellikle bir bağlantı noktası aracını bileşene sürükleyerek bağlantı noktaları oluşturabilirsiniz ve bağlantı noktalarına bağlanabilirsiniz.

![Bileşenler ve birbirine bağlı bağlantı noktaları](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>DSL Çözümünün Yapısı
 **Dsl projesi,** DSL'nizin API'sini tanımlar. **DslPackage projesi,** Visual Studio. Ayrıca, modelden oluşturulan kodu içeren kendi projelerinizi de ekebilirsiniz.

### <a name="the-code-directories"></a>Kod dizinleri
 Bu projelerin her bir kodun çoğu **Dsl\DslDefinition.dsl konumundan oluşturulur.** Oluşturulan kod, Oluşturulan **Kod klasöründedir.** Oluşturulan bir dosyayı görmek için, oluşturan **.tt** dosyasının yanındaki **[+]** dosyasına tıklayın.

 DSL'i anlamanıza yardımcı olmak için oluşturulan kodu incelemenizi öneririz. Oluşturulan dosyaları görmek için dosyalarda *.tt Çözüm Gezgini.

 \*.tt dosyaları çok az kod oluşturma içerir. Bunun yerine, paylaşılan `<#include>` şablon dosyalarını dahil etmek için yönergeleri kullanırlar. Paylaşılan dosyalar **\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Tasarımcısı\11.0\TextTemplates** konumunda bulunabilir

 DSL çözümüne kendi program kodunuzu eklerken, bunu Oluşturulan Kod klasörünün dışında ayrı bir dosyaya ekleyin. Özel Kod klasörü **oluşturmak istiyor** olabilir. (Özel bir klasöre yeni bir kod dosyası eklerken, ilk kod iskeleti içinde ad alanını düzeltmeyi unutmayın.)

 Çözümü yeniden 7.000.000'den sonra düzenleydiğiniz düzenlemeler kaybedilir ve oluşturulan kodu doğrudan düzenlemenizi önerilmez. Bunun yerine, DSL'nizi özelleştirmek için:

- DSL Tanımı'nın birçok parametresini ayarlayın.

- Oluşturulan sınıflarda tanımlanan veya devralınan yöntemleri geçersiz kılmak için ayrı kod dosyalarında kısmi sınıflar yazın. Bazı durumlarda, oluşturulan bir  yöntemi geçersiz kılmak için DSL Tanımında bir sınıfın Çift Türetilmiş Üretir seçeneğini belirlemeniz gerekir.

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

 İlişki, İlişki *yönteminde* `Builder.Connect()` oluşturulur. Varsayılan sürüm, kaynak ve hedef model öğelerinin kabul edilebilir olduğunu doğrular ve ardından ilişkiyi örnekler. Örneğin:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Her oluşturucu sınıfı DSL Gezgini'nin Bağlantı Oluşturucuları **bölümündeki** bir düğümden oluşturulur. Bir `Connect` yöntem, bir veya daha fazla etki alanı sınıfı çifti arasında ilişkiler oluşturabilir. Her çift, DSL Gezgini'nde oluşturucu düğümü altında bulabilirsiniz bir Bağlantı Bağlantısı Yönergesi ile tanımlanır.

 Örneğin, örnek DSL'de üç ilişki türü için bir bağlantı oluşturucu bağlantı bağlama yönergeleri eklenmiştir. Bu, kullanıcıya tek bir bağlantı aracı sağlar. Örneklenmiş ilişki türü, kullanıcı tarafından seçilen kaynak ve hedef öğelerin türlerine bağlıdır.  Bağlantı Bağlantısı Yönergeleri eklemek için DSL Gezgini'nde bir oluşturucuya sağ tıklayın.

 Belirli bir etki alanı ilişkisi türü oluşturulduğunda çalıştırılan özel kod yazmak için oluşturucu düğümü altında uygun Bağlantı Bağlantısı Yönergesi'ne tıklayın. Aşağıdaki Özellikler penceresi Özel Bağlantı **Kullanır'a ayarlayın.** Çözümü yeniden üretin ve ardından ortaya çıkan hataları düzeltmek için kod girin.

 Kullanıcı bu bağlantı aracını her kullandığında çalışan özel kod yazmak için, bağlantı **oluşturucusuza ait Is Custom** özelliğini ayarlayın. Bir kaynak öğeye izin verilip izin verilmediğini, kaynak ve hedefin belirli bir bileşimine izin verilip izin verilmediğini ve bağlantı ederken modelde hangi güncelleştirmelerin yapılacaklarını karara varan kodlar sebilirsiniz. Örneğin, yalnızca diyagramda bir döngü oluşturmazsa bir bağlantıya izin veebilirsiniz. Tek bir ilişki bağlantısı yerine, kaynak ve hedef arasında birkaç ilişkili öğenin daha karmaşık bir desenini örneği olarak kullanabilirsiniz.

 `Connectors.cs`

 Genellikle başvuru ilişkilerini temsil eden diyagram öğeleri olan bağlayıcıların sınıflarını içerir. Her sınıf DSL Tanımında bir bağlayıcıdan oluşturulur. Her bağlayıcı sınıfı türetilen <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Çalışma zamanında rengi ve diğer bazı stil özelliklerini değişken yapmak için DSL Tanımı diyagramında sınıfına sağ tıklayın ve Maruz Ekle'nin **üzerine gelin.**

 Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement> .

 `Diagram.cs`

 Diyagramı tanımlayan sınıfı içerir. 'den <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> türetildi.

 Çalışma zamanında rengi ve diğer bazı stil özelliklerini değişken yapmak için DSL Tanımı diyagramında sınıfına sağ tıklayın ve Maruz Ekle'nin **üzerine gelin.**

 Ayrıca, bu dosya `FixupDiagram` modele yeni bir öğe ekleniyorsa yanıt veren kuralı içerir. Kural yeni bir şekil ekler ve şekli model öğesine bağlar.

 `DirectiveProcessor.cs`

 Bu yönerge işlemcisi, kullanıcılarının DSL örneğinizi okumak için metin şablonları yazmalarını sağlar. Yönerge işlemcisi DSL'niz için derlemeleri (DLS) yükler ve ad alanınız `using` için deyimleri etkili bir şekilde ekler. Bu, metin şablonlarındaki kodun DSL'niz içinde tanımlandığı sınıfları ve ilişkileri kullanmalarını sağlar.

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

   Örnek DSL'de bir Giriş Bağlantı Noktası veya Çıkış Bağlantı Noktası bir Bileşenle birleştirilebilir. Ayrıca Bileşenler ve Açıklamalar modelle birleştirilebilir. VMExtensionProvisioningError hatasından dolayı

   Bileşen sınıfındaki EGP işleyici yöntemleri, Bileşenin Bağlantı Noktalarını kabul etmesine izin vermez, ancak Açıklamalar'ı kabul etmez. Kök model sınıfındaki EGP işleyicisi Açıklamalar ve Bileşenler'i kabul eder, ancak Bağlantı Noktalarını kabul etmez.

  `DomainModel.cs`

  Etki alanı modelini temsil eden sınıf. 'den <xref:Microsoft.VisualStudio.Modeling.DomainModel> türetildi.

> [!NOTE]
> Bu, modelin kök sınıfıyla aynı değildir.

 Kopyalama ve Silme Kapanışları, bir öğe kopyalanır veya silinirken diğer hangi öğelerin dahil edileceklerini tanımlar. Her ilişkinin her tarafındaki **rollerin Kopyalama**  yayma ve Yayma Silme özelliklerini ayarlayıp bu davranışı kontrol altına aabilirsiniz. Değerlerin dinamik olarak belirlenecek şekilde belirlensin, Kapatma sınıflarının yöntemlerini geçersiz kılmak için kod yazabilirsiniz.

 `DomainModelResx.resx`

 Bu, etki alanı sınıflarının ve özelliklerinin açıklamaları, özellik adları, araç kutusu etiketleri, standart hata iletileri ve kullanıcıya görüntülenemedi diğer dizeler gibi dizeleri içerir. Ayrıca görüntü şekilleri için araç simgeleri ve görüntüler içerir.

 Bu dosya, yerleşik derlemeye bağlıdır ve bu kaynakların varsayılan değerlerini sağlar. Kaynakların yerelleştirilmiş sürümünü içeren bir uydu derlemesi oluşturarak DSL'nizi yerelleştirebilirsiniz. DSL yerelleştirilmiş kaynaklarla eşleşen bir kültüre yüklenirken bu sürüm kullanılır. Daha fazla bilgi için, [bkz. Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

 `DomainRelationships.cs`

 Modelde iki öğe arasındaki her bağlantı, etki alanı ilişki sınıfının bir örneğiyle temsil edilen. Tüm ilişki sınıfları, 'den <xref:Microsoft.VisualStudio.Modeling.ElementLink> türetilmiştir ve bu da 'den türetilen sınıftır. <xref:Microsoft.VisualStudio.Modeling.ModelElement> ModelElement olduğundan, bir ilişkinin örneği özelliklere sahip olabilir ve bir ilişkinin kaynağı veya hedefi olabilir.

 `HelpKeywordHelper.cs`

 Kullanıcı F1'e basıyorken kullanılan işlevleri sağlar.

 `MultiplicityValidation.cs`

 1..1 veya 1..* çokluğu belirttiğiniz ilişki rollerinde, kullanıcıya ilişkinin en az bir örneğinin gerekli olduğu konusunda uyarılmış olması gerekir. Bu dosya, bu uyarıları uygulayan doğrulama kısıtlamaları sağlar. Ekleme üst öğesi 1..1 bağlantısı doğrulanmadı.

 Bu kısıtlamaların yürütül olması için DSL Gezgini'nde **Düzenleyici\Doğrulama** düğümünde **Kullanımlar...** seçeneklerden birini ayarlasanız gerekir. Daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Bu dosya yalnızca bir etki alanı özelliğine Özel Tür Tanımlayıcısı iliştirilmişse kod içerir. Daha fazla bilgi için [bkz. Özellikler Penceresini Özelleştirme.](../modeling/customizing-the-properties-window.md)

 `SerializationHelper.cs`

- Aynı bilinen ad tarafından iki öğeye başvurulmaması için doğrulama yöntemi. Daha fazla bilgi için [bkz. Dosya Depolama ve XML Serileştirmesini Özelleştirme.](../modeling/customizing-file-storage-and-xml-serialization.md)

- Serileştirme sınıfları tarafından ortak kullanılan işlevleri sağlayan SerializationHelper sınıfı.

  `Serializer.cs`

  Her etki alanı sınıfı, ilişki, şekil, bağlayıcı, diyagram ve model için seri hale getirici sınıfı.

  Bu sınıfların özelliklerinin çoğu DSL Gezgini'nde Xml Serileştirme Davranışı altındaki **ayarlar tarafından denetlenebilirsiniz.**

  `Shapes.cs`

  DSL Tanımı'nın her şekil sınıfı için bir sınıf. Şekiller' den <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> türetildi. Daha fazla bilgi için [bkz. Dosya Depolama ve XML Serileştirmesini Özelleştirme.](../modeling/customizing-file-storage-and-xml-serialization.md)

  Oluşturulan yöntemleri kısmi bir sınıfta kendi yöntemleriniz ile geçersiz  kılmak için DSL Tanımında bağlayıcı için Çift Türetilen Üretir'i ayarlayın. Bir oluşturucusu kendi kodunuzla değiştirmek için Özel Oluşturucu **var'a ayarlayın.**

  Çalışma zamanında rengi ve diğer bazı stil özelliklerini değişken yapmak için DSL Tanımı diyagramında sınıfına sağ tıklayın ve Maruz Ekle'nin **üzerine gelin.**

  Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Öğe araçlarına öğe grubu prototipleri yükleyerek araç kutusunu ayarlar. Kullanıcı aracı çalıştırsa, bu prototiplerin kopyaları hedef öğelerle birleştirilir.

  Birkaç `CreateElementPrototype()` nesneden bir grup oluşturan bir araç kutusu öğesi tanımlamak için geçersiz kılabilirsiniz. Örneğin, alt bileşenleri olan nesneleri temsil eden bir öğe tanımlayabilirsiniz. Kodu değiştirdikten sonra, araç kutusu önbelleğini temizlemek Visual Studio deneysel Visual Studio örneğini sıfırlayın.

## <a name="generated-files-in-the-dslpackage-project"></a>DslPackage projesinde oluşturulan dosyalar
 DslPackage DSL modelini pencere, araç kutusu Visual Studio menü komutlarını yöneterek Visual Studio kabuğuna verir. Sınıfların çoğu çift türetilen, böylece herhangi bir yöntemini geçersiz kılabilirsiniz.

 `CommandSet.cs`

 Diyagramda görünen sağ tıklama menü komutları. Bu kümeye uyarlanabilir veya eklemeler lanabilir. Bu dosya komutların kodunu içerir. Menülerde komutların konumu Commands.vsct dosyası tarafından belirlenir. Daha fazla bilgi için, [bkz. Writing User Commands and Actions](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `Constants.cs`

 Guıd.

 `DocData.cs`

 *YourDsl* `DocData` bir modelin yüklenmesini ve dosyaya kaydedilesini yönetir ve Store örneğini oluşturur.

 Örneğin, DSL'nizi bir dosya yerine bir veritabanına kaydetmek için ve yöntemlerini geçersiz `Load` `Save` kılabilirsiniz.

 `DocView.cs`

 *YourDsl* `DocView` diyagramın göründüğü pencereyi yönetir. Örneğin, diyagramı bir Windows Form içine katıştırabilirsiniz:

 DslPackage projesine bir Kullanıcı Denetimi dosyası ekleyin. Diyagramın görüntülenebilir olduğu bir Panel ekleyin. Düğmeler ve diğer denetimler ekleyin. Formun kod görünümünde, adları DSL'nize ayarlayarak aşağıdaki kodu ekleyin:

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

 ve örneğini `DocData` `DocView` hazırlar. DSL paketiniz başlatıldığında düzenleyiciyi Visual Studio için kullanan standart bir arabirimi karşılar. `ProvideEditorFactory`Package.cs'de özniteliğinde buna başvurur

 `GeneratedVSCT.vsct`

 Menülerde, diyagram sağ tıklama (bağlam) menüsü, Düzenle menüsü gibi  standart menü komutlarını yer almaktadır. Komutların kodu CommandSet.cs içindedir. Standart komutları yeniden bulundurabilirsiniz veya değiştirebilir ve kendi komutlarınızı ekebilirsiniz. Daha fazla bilgi için, [bkz. Writing User Commands and Actions](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `ModelExplorer.cs`

 DSL'niz için Model Gezgini'ni tanımlar. Bu, kullanıcının diyagramla birlikte gördüğü modelin ağaç görünümü.

 Örneğin, öğelerin Model `InsertTreeView()` Gezgini'nde görünme sırası değiştirmek için geçersiz kılabilirsiniz.

 Model gezgininde seçimin diyagram seçimiyle eşitlenmiş durumda tutmasını almak için aşağıdaki kodu kullanabilirsiniz:

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

 Model gezgininin görüntülenmiyor olduğu pencereyi tanımlar. Gezgindeki öğe seçimini işleme.

 `Package.cs`

 Bu dosya DSL'nin Visual Studio. Paket sınıfındaki öznitelikler DSL'i dosya uzantınıza sahip dosyalar için işleyici olarak kaydettirin, araç kutusunu tanımlayın ve yeni bir pencerenin nasıl açılabilir olduğunu tanımlayın. Initialize() yöntemi, ilk DSL bir Visual Studio örneğine yüklendiğinde çağrılır.

 `Source.extension.vsixmanifest`

 Bu dosyayı özelleştirmek için dosyasını `.tt` düzenleyin.

> [!WARNING]
> .tt dosyasını simgeler veya görüntüler gibi kaynakları içerecek şekilde düzenlersanız, kaynağın VSIX derlemesine dahil olduğundan emin olun. Bu Çözüm Gezgini dosyasını seçin ve VSIX'e Dahil **Edin özelliğinin olduğundan** emin `True` olun.

 Bu dosya DSL'nin Visual Studio Integration Extension (VSIX) içinde nasıl paketlen olduğunu kontrol eder. Daha fazla bilgi için, [bkz. Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Domain-Specific Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
