---
title: DSL Kodunu Anlama
description: Domain-Specific Language (DSL) çözümünün, Visual Studio DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API oluşturma hakkında bilgi edinin.
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
ms.openlocfilehash: 608bb21c2fb9d8335cd2ba212a6b7501392087d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116571"
---
# <a name="understanding-the-dsl-code"></a>DSL Kodunu Anlama

Domain-Specific Language (DSL) çözümü, Visual Studio DSL örneklerini okumak ve güncelleştirmek için kullanabileceğiniz bir API oluşturur. Bu API, DSL tanımından oluşturulan kodda tanımlanmıştır. Bu konuda, oluşturulan API açıklanmaktadır.

## <a name="the-example-solution-component-diagrams"></a>Örnek çözüm: Bileşen diyagramları

Bu konudaki örneklerin çoğunun kaynağı olan çözümü oluşturmak için **bileşen modelleri** çözüm ŞABLONUNDAN bir DSL oluşturun. Bu, yeni bir DSL çözümü oluştururken görüntülenen standart şablonlardan biridir.

> [!NOTE]
> Bileşen diyagramları DSL şablonuna **alana özgü dil Tasarımcısı** denir.

Bu çözüm şablonu hakkında bilginiz yoksa **F5** tuşuna basın ve deneyin. Özellikle bir bağlantı noktası aracını bir bileşene sürükleyerek ve bağlantı noktalarıyla bağlantı kurmak için bağlantı noktaları oluştururuz olduğuna dikkat edin.

![Bileşenler ve birbirine bağlı bağlantı noktaları](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>DSL çözümünün yapısı
 **DSL** projesi DSL için API 'yi tanımlar. **DslPackage** projesi, Visual Studio ile nasıl tümleştiğini tanımlar. Ayrıca, modelden oluşturulan kodu da içerebilen kendi projelerinizi ekleyebilirsiniz.

### <a name="the-code-directories"></a>Kod dizinleri
 Bu projelerin her birinde bulunan kodun çoğu **Dsl\dsldefinition.exe**' den oluşturulmuştur. Oluşturulan kod, **oluşturulan kod** klasöründedir. Oluşturulan bir dosyayı görmek için üretilen **. tt** dosyasının yanındaki **[+]** düğmesine tıklayın.

 DSL 'yi anlamanıza yardımcı olması için üretilen kodu incelemenizi öneririz. Oluşturulan dosyaları görmek için Çözüm Gezgini içindeki *. tt dosyalarını genişletin.

 \*. Tt dosyaları çok az üretilen kod içerir. Bunun yerine, `<#include>` paylaşılan şablon dosyalarını dahil etmek için yönergeleri kullanırlar. paylaşılan dosyalar **\program files \ Microsoft Visual Studio 10.0 \ Common7\IDE\Extensions\Microsoft\DSL sdk\dsl designer\11.0\texttemplates** dizininde bulunabilir

 Kendi program kodunuzu DSL çözümüne eklediğinizde, oluşturulan kod klasörünün dışında ayrı bir dosyaya ekleyin. **Özel bir kod** klasörü oluşturmak isteyebilirsiniz. (Özel bir klasöre yeni bir kod dosyası eklediğinizde, ilk kod isketadaki ad alanını düzeltmeyi unutmayın.)

 Çözümü yeniden oluşturduğunuzda düzenlemeleriniz kaybolacağı için, oluşturulan kodu doğrudan düzenlememenizi önemle tavsiye ederiz. Bunun yerine, DSL 'yi özelleştirmek için:

- DSL tanımındaki birçok parametreyi ayarlayın.

- Oluşturulan sınıflar tarafından tanımlanan veya tarafından devralınan yöntemleri geçersiz kılmak için kısmi sınıfları ayrı kod dosyalarına yazın. Bazı durumlarda, üretilen bir yöntemi geçersiz kılabilmek için DSL tanımındaki bir sınıfın **çift türetilmiş** seçeneğini ayarlamanız gerekir.

- DSL tanımında, üretilen kodun kendi kodunuz için ' kancalar ' sağlamasına neden olan seçenekleri ayarlayın.

     Örneğin, bir etki alanı sınıfına ait **özel Oluşturucu** seçeneğini ayarlarsanız ve sonra çözümü oluşturursanız, hata iletilerini görürsünüz. Bu hata iletilerinden birine çift tıkladığınızda, oluşturulan kodda özel kodunuzun ne sağlaması gerektiğini açıklayan Yorumlar görürsünüz.

- Uygulamanıza özel kod oluşturmak için kendi metin şablonlarınızı yazın. birçok projede ortak olan şablonların parçalarını paylaşmak için içerme dosyalarını kullanabilir ve kendi dosya yapınız ile başlatılan projeleri ayarlamak için Visual Studio proje şablonları oluşturabilirsiniz.

## <a name="generated-files-in-dsl"></a>DSL 'de oluşturulan dosyalar
 Aşağıdaki oluşturulan dosyalar **DSL** projesinde görüntülenir.

 *Yourdsl*`Schema.xsd`

 DSL örneklerini içeren dosyalar için şema. Bu dosya, derleme (**bin**) dizinine kopyalanır. DSL 'yi yüklediğinizde, model dosyalarının doğrulanması için bu dosyayı **\program files \ Microsoft Visual Studio 11.0 \ xml\schemas dizinine** kopyalayabilirsiniz. Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

 DSL Gezgini 'ndeki seçenekleri ayarlayarak serileştirme 'i özelleştirirseniz, şema buna uygun olarak değişir. Ancak, kendi serileştirme kodunuzu yazarsanız, bu dosya artık gerçek şemayı temsil edemeyebilir. daha fazla bilgi için bkz. [dosya Depolama ve XML serileştirmesini özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Bağlantı Oluşturucu, ilişki oluşturan bir sınıftır. Bu, bir bağlantı aracının arkasındaki koddur. Bu dosya, her bağlantı aracı için bir çift sınıf içerir. Adları, etki alanı ilişkisi ve bağlantı aracının adlarından türetilir: *ilişki* Oluşturucu ve *connectortool* ConnectAction.

 (Bileşen çözümü örneğinde, bağlantı oluşturucularının birine ConnectionBuilder denir, bu bir rastlantı, çünkü etki alanı ilişkisi bağlantı olarak adlandırılmaktadır.)

 İlişki, *ilişki* `Builder.Connect()` yönteminde oluşturulur. Varsayılan sürüm, kaynak ve hedef model öğelerinin kabul edilebilir olduğunu doğrular ve ardından ilişkiyi başlatır. Örnek:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Her Oluşturucu sınıfı, DSL Gezgini 'ndeki **bağlantı oluşturucuları** bölümünde bir düğümden oluşturulur. Bir `Connect` Yöntem, bir veya daha fazla etki alanı sınıfı çifti arasında ilişkiler oluşturabilir. her bir çift, bir bağlantı Bağlan yönergesi tarafından tanımlanır ve bu, oluşturucu düğümü altında DSL gezgini 'nde bulabilirsiniz.

 örneğin, örnek DSL 'deki üç ilişki türünün her biri için bir bağlantı oluşturucu bağlantısına Bağlan yönergeler ekleyebilirsiniz. Bu, kullanıcıya tek bir bağlantı aracı sağlar. Oluşturulan ilişki türü, Kullanıcı tarafından seçilen kaynak ve hedef öğelerin türlerine bağlıdır.  bağlantı Bağlan yönergeleri eklemek için DSL gezgininde bir oluşturucuya sağ tıklayın.

 belirli bir etki alanı ilişkisi türü oluşturulduğunda çalışan özel kod yazmak için, oluşturucu düğümünün altındaki uygun bağlantı Bağlan yönergesini seçin. Özellikler penceresi, **özel Bağlan kullanır**' ı ayarlayın. Çözümü yeniden derleyin ve ardından ortaya çıkan hataları düzeltmek için kodu sağlayın.

 Kullanıcı bu bağlantı aracını her kullandığında çalışan özel kod yazmak için, bağlantı oluşturucusunun **özel** özelliğini ayarlayın. Kaynak öğeye izin verilip verilmeyeceğini, kaynak ve hedefin belirli bir birleşimine izin verilip verilmeyeceğini ve bir bağlantı yapıldığında modele hangi güncelleştirmelerin yapılması gerektiğine karar veren kodu sağlayabilirsiniz. Örneğin, bir bağlantıya yalnızca diyagramda bir döngü oluşturacaksa izin verebilirsiniz. Tek bir ilişki bağlantısı yerine, kaynak ve hedef arasında birbiriyle ilişkili birkaç öğenin daha karmaşık bir örüntüsünün örneğini oluşturabilirsiniz.

 `Connectors.cs`

 Genellikle başvuru ilişkilerini temsil eden diyagram öğeleri olan bağlayıcıların sınıflarını içerir. Her sınıf DSL tanımındaki bir bağlayıcıdan oluşturulur. Her bağlayıcı sınıfı, öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Çalışma zamanında rengi ve diğer stil özellikleri değişkenlerini yapmak için, DSL tanımı diyagramında sınıfa sağ tıklayın ve **sunulan Ekle**' ye gelin.

 Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> . Örneğin ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement> .

 `Diagram.cs`

 Diyagramı tanımlayan sınıfı içerir. Öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> .

 Çalışma zamanında rengi ve diğer stil özellikleri değişkenlerini yapmak için, DSL tanımı diyagramında sınıfa sağ tıklayın ve **sunulan Ekle**' ye gelin.

 Ayrıca, bu dosya, `FixupDiagram` modele yeni bir öğe eklendiğinde yanıt veren kuralını içerir. Kural yeni bir şekil ekler ve şekli model öğesine bağlar.

 `DirectiveProcessor.cs`

 Bu yönerge işlemcisi, kullanıcılarınızın DSL örneğini okuyan metin şablonları yazmasına yardımcı olur. Yönerge işlemcisi, DSL 'niz için derlemeleri (dll 'Ler) yükler ve `using` ad alanınız için etkin bir şekilde deyimler ekler. Bu, metin şablonlarındaki kodun DSL 'de tanımladığınız sınıfları ve ilişkileri kullanmasına izin verir.

 Daha fazla bilgi için, bkz. [Domain-Specific dilden kod üretme](../modeling/generating-code-from-a-domain-specific-language.md) ve [özel T4 metin şablonu yönerge işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Soyut sınıflar ve model kök sınıfı dahil, tanımladığınız etki alanı sınıflarının uygulamaları. Bunlar öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.ModelElement> .

 Her etki alanı sınıfı şunları içerir:

- Her etki alanı özelliği için bir özellik tanımı ve iç içe geçmiş işleyici sınıfı. OnValueChanging () ve OnValueChanged () öğesini geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md).

   Örnek DSL 'de, `Comment` sınıfı bir özellik `Text` ve bir işleyici sınıfı içerir `TextPropertyHandler` .

- Bu alan sınıfının katıldığı ilişkiler için erişimci özellikleri. (Rol özellikleri için iç içe bir sınıf yoktur.)

   Örnek DSL 'de, sınıfı, `Comment` katıştırma ilişkisi aracılığıyla üst modeline erişen erişimcileri içerir `ComponentModelHasComments` .

- Kurucu. Bunları geçersiz kılmak istiyorsanız, set alanı sınıfında **özel Oluşturucusu vardır** .

- Öğe grubu prototipi (EGP) işleyici yöntemleri. Bu, Kullanıcı bu sınıfın örneklerine başka bir öğe *birleştirecan* (eklemek) için gereklidir. Genellikle Kullanıcı bunu bir öğe aracından veya başka bir şekilden sürükleyerek veya yapıştırarak yapar.

   Örnek DSL'de bir Giriş Bağlantı Noktası veya Çıkış Bağlantı Noktası bir Bileşenle birleştirilebilir. Ayrıca Bileşenler ve Açıklamalar modelle birleştirilebilir. VMExtensionProvisioningError hatasından dolayı

   Bileşen sınıfındaki EGP işleyicisi yöntemleri, Bileşenin Bağlantı Noktalarını kabul etmesine izin vermez, ancak Açıklamalar'ı kabul etmez. Kök model sınıfındaki EGP işleyicisi Açıklamalar ve Bileşenler'i kabul eder, ancak Bağlantı Noktalarını kabul etmez.

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

 1...1 veya 1..* çokluğu belirttiğiniz ilişki rollerinde, kullanıcıya ilişkinin en az bir örneğinin gerekli olduğu konusunda uyarılmış olması gerekir. Bu dosya, bu uyarıları uygulayan doğrulama kısıtlamaları sağlar. Ekleme üst öğesi 1..1 bağlantısı doğrulanmadı.

 Bu kısıtlamaların yürütül olması için DSL Gezgini'nde **Düzenleyici\Doğrulama** düğümünde **Kullanımlar...** seçeneklerden birini ayarlasanız gerekir. Daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Bu dosya yalnızca bir etki alanı özelliğine Özel Tür Tanımlayıcısı iliştirilmişse kod içerir. Daha fazla bilgi için [bkz. Özellikler Penceresini Özelleştirme.](../modeling/customizing-the-properties-window.md)

 `SerializationHelper.cs`

- Aynı bilinen ad tarafından iki öğeye başvurulmaması için doğrulama yöntemi. Daha fazla bilgi için, [bkz. Dosya Depolama ve XML Serileştirme özelleştirme.](../modeling/customizing-file-storage-and-xml-serialization.md)

- Serileştirme sınıfları tarafından ortak kullanılan işlevleri sağlayan SerializationHelper sınıfı.

  `Serializer.cs`

  Her etki alanı sınıfı, ilişki, şekil, bağlayıcı, diyagram ve model için seri hale getirici sınıfı.

  Bu sınıfların özelliklerinin çoğu DSL Gezgini'nde Xml Serileştirme Davranışı altındaki **ayarlar tarafından denetlenebilirsiniz.**

  `Shapes.cs`

  DSL Tanımında her şekil sınıfı için bir sınıf. Şekiller' den <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> türetildi. Daha fazla bilgi için, [bkz. Dosya Depolama ve XML Serileştirme özelleştirme.](../modeling/customizing-file-storage-and-xml-serialization.md)

  Oluşturulan yöntemleri kısmi bir sınıfta kendi yöntemleriniz ile geçersiz  kılmak için DSL Tanımında bağlayıcı için Çift Türetilmiş Üretir'i ayarlayın. Bir oluşturucusu kendi kodunuzla değiştirmek için Özel Oluşturucu **var'a ayarlayın.**

  Çalışma zamanında rengi ve diğer bazı stil özelliklerini değişken yapmak için DSL Tanımı diyagramında sınıfına sağ tıklayın ve Maruz Ekle'nin **üzerine gelin.**

  Çalışma zamanında ek stil özellikleri değişkeni yapmak için bkz. <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Öğe araçlarına öğe grubu prototipleri yükleyerek araç kutusunu ayarlar. Kullanıcı aracı çalıştırsa, bu prototiplerin kopyaları hedef öğelerle birleştirilir.

  Birkaç `CreateElementPrototype()` nesneden bir grup oluşturan bir araç kutusu öğesi tanımlamak için geçersiz kılabilirsiniz. Örneğin, alt bileşenleri olan nesneleri temsil eden bir öğe tanımlayabilirsiniz. Kodu değiştirdikten sonra, araç kutusu önbelleğini temizlemek Visual Studio deneme örneğini sıfırlayın.

## <a name="generated-files-in-the-dslpackage-project"></a>DslPackage projesinde oluşturulan dosyalar
 DslPackage, pencere, araç kutusu ve menü komutlarını Visual Studio DSL modelini Visual Studio kabuğuna verir. Sınıfların çoğu çift türetilen, böylece herhangi bir yöntemini geçersiz kılabilirsiniz.

 `CommandSet.cs`

 Diyagramda görünen sağ tıklama menü komutları. Bu kümeye uyarlanabilir veya eklemeler lanabilir. Bu dosya komutların kodunu içerir. Menülerde komutların konumu Commands.vsct dosyası tarafından belirlenir. Daha fazla bilgi için [bkz. Kullanıcı Komutları ve Eylemleri Yazma.](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

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

 ve örneğini `DocData` `DocView` hazırlar. DSL paketiniz başlatıldığında düzenleyiciyi açmak Visual Studio standart bir arabirimi karşılar. `ProvideEditorFactory`Package.cs'de özniteliğinde başvurur

 `GeneratedVSCT.vsct`

 Menülerde, diyagram sağ tıklama (bağlam) menüsü, Düzenle menüsü gibi  standart menü komutlarını yer almaktadır. Komutların kodu CommandSet.cs içindedir. Standart komutları yeniden bulundurabilirsiniz veya değiştirebilir ve kendi komutlarınızı ekebilirsiniz. Daha fazla bilgi için [bkz. Kullanıcı Komutları ve Eylemleri Yazma.](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

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
