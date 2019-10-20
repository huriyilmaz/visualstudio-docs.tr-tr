---
title: UML modelleri için doğrulama kısıtlamaları tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f279216d06972578f5173e57375c89542c71e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669894"
---
# <a name="define-validation-constraints-for-uml-models"></a>UML modelleri için doğrulama kısıtlamaları tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelin belirttiğiniz bir koşulu karşılayıp karşılamadığını test eden doğrulama kısıtlamalarını tanımlayabilirsiniz. Örneğin, bir kullanıcının devralma ilişkilerinin döngüsünü oluşturmadığından emin olmak için bir kısıtlama tanımlayabilirsiniz. Kullanıcı modeli açmaya veya kaydetmeye çalıştığında kısıtlama çağrılır ve ayrıca el ile çağrılabilir. Kısıtlama başarısız olursa, tanımladığınız bir hata iletisi hata penceresine eklenir. Bu kısıtlamaları bir Visual Studio Tümleştirme Uzantısı 'na ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

 Ayrıca, modeli veritabanları gibi dış kaynaklara karşı doğrulayan kısıtlamalar tanımlayabilirsiniz. Program kodunu bir katman diyagramına karşı doğrulamak istiyorsanız, bkz. [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 Hangi Visual Studio sürümlerini UML modellerini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-uml-models-and-diagrams.md#Requirements)bakın.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="applying-validation-constraints"></a>Doğrulama kısıtlamalarını uygulama
 Doğrulama kısıtlamaları üç durumda uygulanır: bir modeli kaydettiğinizde; bir modeli açtığınızda; **mimari** menüsünde **UML modelini doğrula** ' ya tıkladığınızda. Her durumda, genellikle bu durum için tanımlanan kısıtlamalar uygulanır, ancak genellikle her kısıtlamayı birden fazla durumda uygulamak üzere tanımlarsınız.

 Doğrulama hataları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hataları penceresinde raporlanır ve hatalı model öğelerini seçmek için hataya çift tıklayabilirsiniz.

 Doğrulama uygulama hakkında daha fazla bilgi için bkz. [UML modelinizi doğrulama](../modeling/validate-your-uml-model.md).

## <a name="defining-a-validation-extension"></a>Doğrulama uzantısı tanımlama
 Bir UML tasarımcısı için bir doğrulama uzantısı oluşturmak için, doğrulama kısıtlamalarını tanımlayan bir sınıf oluşturmanız ve sınıfı bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) katıştırmanız gerekir. VSıX kısıtlamayı yükleyen bir kapsayıcı görevi görür. Doğrulama uzantısı tanımlamanın iki alternatif yöntemi vardır:

- **Proje şablonunu kullanarak kendi VSIX 'inde bir doğrulama uzantısı oluşturun.** Bu daha hızlı bir yöntemdir. Doğrulama kısıtlamalarını menü komutları, özel araç kutusu öğeleri veya hareket işleyicileri gibi diğer tür uzantılarla birleştirmek istemiyorsanız, bunu kullanın. Tek bir sınıfta çeşitli kısıtlamalar tanımlayabilirsiniz.

- **Ayrı doğrulama sınıfı ve VSıX projeleri oluşturun.** Aynı VSıX içinde birkaç uzantı türünü birleştirmek istiyorsanız bu yöntemi kullanın. Örneğin, menü komutunuz modelin belirli kısıtlamaları gözlemmesini bekliyorsa, bir doğrulama yöntemiyle aynı VSıX 'e katabilirsiniz.

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Kendi VSIX 'inde bir doğrulama uzantısı oluşturmak için

1. **Yeni proje** iletişim kutusunda, **modelleme projeleri**' nin altında, **doğrulama uzantısı**' nı seçin.

2. Yeni projede **. cs** dosyasını açın ve doğrulama kısıtlamalarınızı uygulamak için sınıfını değiştirin.

    Daha fazla bilgi için bkz. [doğrulama kısıtlamasını değerlendirme](#Implementing).

   > [!IMPORTANT]
   > **. Cs** dosyalarınızın aşağıdaki `using` ifadesini içerdiğinden emin olun:
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. Yeni yöntemler tanımlayarak daha fazla kısıtlama ekleyebilirsiniz. Bir yöntemi doğrulama yöntemi olarak tanımlamak için, bu özniteliğin ilk doğrulama yöntemiyle aynı şekilde etiketlenmesi gerekir.

4. F5 'e basarak kısıtlamalarınızı test edin. Daha fazla bilgi için bkz. [doğrulama kısıtlaması yürütme](#Executing).

5. Projeniz tarafından oluşturulan dosya **sepeti \\ \* \\ \*. vsix** dosyasını kopyalayarak başka bir bilgisayara menü komutunu yükler. Daha fazla bilgi için bkz. [Uzantı yükleme ve kaldırma](#Installing).

   Diğer **. cs** dosyalarını eklediğinizde, genellikle aşağıdaki `using` deyimlerini yapmanız gerekir:

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 Alternatif yordam aşağıda verilmiştir:

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Bir sınıf kitaplığı projesinde ayrı bir doğrulama kısıtlaması oluşturmak için

1. Mevcut bir VSıX çözümüne ekleyerek veya yeni bir çözüm oluşturarak bir sınıf kitaplığı projesi oluşturun.

    1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

    2. **Yüklü şablonlar**altında, **görsel C#**  veya **Visual Basic**' i genişletin ve ardından Orta sütundaki **sınıf kitaplığı**' nı seçin.

2. Çözümünüz bir tane içermiyorsa, bir VSıX projesi oluşturun:

    1. **Çözüm Gezgini**, çözümün kısayol menüsünde, **Ekle**, **Yeni proje**' yi seçin.

    2. **Yüklü şablonlar**altında,  **C# görsel** veya **Visual Basic**' ı genişletin, ardından **genişletilebilirlik**' i seçin. Orta sütunda **VSIX projesi**' ne tıklayın.

3. VSıX projesini çözümün başlangıç projesi olarak ayarlayın.

    - Çözüm Gezgini, VSıX projesinin kısayol menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.

4. **Source. Extension. valtmanifest**dosyasında, **içerik**' in altında, sınıf kitaplığı projesini MEF bileşeni olarak ekleyin:

    1. **Meta veriler** sekmesinde VSIX için bir ad belirleyin.

    2. **Hedefleri yüklensin** sekmesinde, Visual Studio sürümlerini hedef olarak ayarlayın.

    3. **Varlıklar** sekmesinde **Yeni**' yi seçin ve iletişim kutusunda, şunu ayarlayın:

         @No__t_1**MEF bileşeni** **yazın**

         **Kaynak**  = **geçerli çözümdeki bir proje**

         *Sınıf kitaplığı projenizden* **Proje**  = 

#### <a name="to-define-the-validation-class"></a>Doğrulama sınıfını tanımlamak için

1. Doğrulama projesi şablonundan kendi VSıX 'i ile bir doğrulama sınıfı oluşturduysanız, bu yordama ihtiyacınız yoktur.

2. Doğrulama sınıfı projesinde, aşağıdaki [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] derlemelerine başvuruları ekleyin:

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. Aşağıdaki örneğe benzer bir kod içeren sınıf kitaplığı projesine bir dosya ekleyin.

    - Her doğrulama kısıtlaması, belirli bir öznitelikle işaretlenmiş bir yöntem içinde yer alır. Yöntemi, model öğesi türünün bir parametresini kabul eder. Doğrulama çağrıldığında, doğrulama çerçevesi her doğrulama yöntemini parametre türüne uyan her model öğesine uygular.

    - Bu yöntemleri, herhangi bir sınıfa ve ad alanına yerleştirebilirsiniz. Tercihlerinizi tercihlerinize göre değiştirin.

    ```
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using Microsoft.VisualStudio.Modeling.Validation;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.Uml.Classes;
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.

    namespace Validation
    {
      public class MyValidationExtensions
      {
        // SAMPLE VALIDATION METHOD.
        // All validation methods have the following attributes.
        [Export(typeof(System.Action<ValidationContext, object>))]
        [ValidationMethod(
           ValidationCategories.Save
         | ValidationCategories.Open
         | ValidationCategories.Menu)]
        public void ValidateClassNames
          (ValidationContext context,
           // This type determines what elements
           // will be validated by this method:
           IClass elementToValidate)
        {
          // A validation method should not change the model.

          List<string> attributeNames = new List<string>();
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)
          {
            string name = attribute.Name;
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))
            {
              context.LogError(
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),
                "001", elementToValidate);
            }
            attributeNames.Add(name);
          }

        }
        // Add more validation methods for different element types.
      }
    }
    ```

## <a name="Executing"></a>Doğrulama kısıtlaması yürütülüyor
 Test amaçları için doğrulama yöntemlerinizi hata ayıklama modunda yürütün.

#### <a name="to-test-the-validation-constraint"></a>Doğrulama kısıtlamasını test etmek için

1. **F5**tuşuna basın veya **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' ı seçin.

     Deneysel bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] örneği başlar.

     **Sorun giderme**: yeni bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlamazsa:

    - Birden çok projeniz varsa, VSıX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.

    - Çözüm Gezgini, başlangıç veya yalnızca projenin kısayol menüsünde **Özellikler**' i seçin. Proje özellikleri düzenleyicisinde **Hata Ayıkla** sekmesini seçin. **dış program Başlat** alanındaki dizenin, genellikle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tam yol adı olduğundan emin olun:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Deneysel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bir modelleme projesi açın veya oluşturun ve bir modelleme diyagramı açın veya oluşturun.

3. Önceki bölümde verilen örnek kısıtlama için bir test ayarlamak için:

    1. Bir sınıf diyagramı açın.

    2. Bir sınıf oluşturun ve aynı ada sahip iki öznitelik ekleyin.

4. Diyagram üzerinde herhangi bir yerdeki kısayol menüsünde **Doğrula**' yı seçin.

5. Modeldeki hatalar hatalar penceresinde raporlanır.

6. Hata raporuna çift tıklayın. Raporda belirtilen öğeler ekranda görünür durumdaysa vurgulanacaktır.

     **Sorun giderme**: **Doğrula** komutu menüde görünmezse şunları yaptığınızdan emin olun:

    - Doğrulama projesi, VSıX projesindeki **kaynak. Extensions. manifest** içindeki **VARLıKLAR** sekmesinde bir MEF bileşeni olarak listelenir.

    - Doğru `Export` ve `ValidationMethod` öznitelikleri doğrulama yöntemlerine iliştirilir.

    - `ValidationCategories.Menu`, `ValidationMethod` özniteliği için bağımsız değişkenine dahildir ve mantıksal OR (&#124;) kullanılarak diğer değerlerle birlikte oluşturulur.

    - Tüm `Import` ve `Export` özniteliklerinin parametreleri geçerlidir.

## <a name="Implementing"></a>Kısıtlama değerlendiriliyor
 Doğrulama yöntemi, uygulamak istediğiniz doğrulama kısıtlamasının doğru mi yoksa yanlış mi olduğunu belirlemelidir. True ise, hiçbir şey yapmaz. Yanlış ise, `ValidationContext` parametresi tarafından sunulan yöntemleri kullanarak bir hata bildirmelidir.

> [!NOTE]
> Doğrulama yöntemleri modeli değiştirmemelidir. Kısıtlamaların ne zaman veya hangi sırada yürütüleceğini garanti yoktur. Doğrulama çalıştırmasının içindeki bir doğrulama yönteminin ardışık yürütmeleri arasında bilgi geçirmek istiyorsanız, [birden çok doğrulamayı koordine](#ContextCache)etme altında açıklanan bağlam önbelleğini kullanabilirsiniz.

 Örneğin, her türün (sınıf, arabirim veya Numaralandırıcı) en az üç karakter uzunluğunda bir ada sahip olduğundan emin olmak istiyorsanız, bu yöntemi kullanabilirsiniz:

```
public void ValidateTypeName(ValidationContext context, IType type)
{
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)
  {
    context.LogError(
      string.Format("Type name {0} is too short", type.Name),
               "001", type);
   }
 }
```

 Modelde gezinmek ve okumak için kullanabileceğiniz yöntemler ve türler hakkında bilgi edinmek için bkz. [UML API Ile programlama](../modeling/programming-with-the-uml-api.md) .

### <a name="about-validation-constraint-methods"></a>Doğrulama kısıtlaması yöntemleri hakkında
 Her doğrulama kısıtlaması aşağıdaki formun bir yöntemi tarafından tanımlanır:

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 Her doğrulama yönteminin öznitelikleri ve parametreleri aşağıdaki gibidir:

|||
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Yöntemi, Managed Extensibility Framework (MEF) kullanarak doğrulama kısıtlaması olarak tanımlar.|
|`[ValidationMethod (ValidationCategories.Menu)]`|Doğrulamanın gerçekleştirileceği zaman belirtir. Birden fazla seçeneği birleştirmek&#124;istiyorsanız BIT düzeyinde OR () kullanın.<br /><br /> `Menu` = doğrulama menüsü tarafından çağırılır.<br /><br /> `Save` = modeli kaydederken çağırılır.<br /><br /> model açılırken `Open` = çağrılır. `Load` = modeli kaydederken çağrılır, ancak bir nedeni için kullanıcıyı, modeli yeniden açmak mümkün olmayabileceğini uyarır. Model ayrıştırıldıktan önce yükleme sırasında da çağırılır.|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|İkinci parametreyi, kısıtlamasının uygulanmasını istediğiniz öğe türüne göre `IElement` değiştirin. Kısıtlama yöntemi belirtilen türdeki tüm öğelerde çağrılacaktır.<br /><br /> Yöntemin adı önemli değildir.|

 İkinci parametrede farklı türlerle istediğiniz kadar çok doğrulama yöntemi tanımlayabilirsiniz. Doğrulama çağrıldığında her bir doğrulama yöntemi parametre türüne uyan her model öğesinde çağrılır.

### <a name="reporting-validation-errors"></a>Doğrulama hatalarını bildirme
 Bir hata raporu oluşturmak için, `ValidationContext` tarafından sunulan yöntemleri kullanın:

 `context.LogError("error string", errorCode, elementsWithError);`

- `"error string"` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görünür Hata Listesi

- `errorCode`, hatanın benzersiz tanımlayıcısı olması gereken bir dizedir

- `elementsWithError` modeldeki öğeleri tanımlar. Kullanıcı hata raporuna çift tıkladığında, bu öğeyi temsil eden şekil seçilir.

  `LogError(),`, `LogWarning()` ve `LogMessage()` iletileri hata listesinin farklı bölümlerine yerleştirir.

## <a name="how-validation-methods-are-applied"></a>Doğrulama yöntemlerinin uygulanma şekli
 , Bir sınıfın öznitelikleri ve bir işlemin parametreleri gibi ilişkiler ve daha büyük öğelerin parçaları dahil olmak üzere modeldeki her öğeye uygulanır.

 Her doğrulama yöntemi, ikinci parametresindeki türe uyan her öğeye uygulanır. Diğer bir deyişle, örneğin, ikinci bir parametresi `IUseCase` bir doğrulama yöntemi ve onun üst türü `IElement` ile başka bir şekilde tanımlarsanız, bu yöntemlerin her ikisi de modeldeki her kullanım örneğine uygulanır.

 Türlerin hiyerarşisi [UML model öğe türlerinde](../modeling/uml-model-element-types.md)özetlenir.

 Ayrıca, öğelere aşağıdaki ilişkileri uygulayarak erişebilirsiniz. Örneğin, `IClass` bir doğrulama yöntemi tanımlamanız durumunda, kendi özelliklerine sahip olabilirsiniz:

```
public void ValidateTypeName(ValidationContext context, IClass c)
{
   foreach (IProperty property in c.OwnedAttributes)
   {
       if (property.Name.Length < 3)
       {
            context.LogError(
                 string.Format(
                        "Property name {0} is too short",
                        property.Name),
                 "001", property);
        }
   }
}
```

### <a name="creating-a-validation-method-on-the-model"></a>Modelde doğrulama yöntemi oluşturma
 Her doğrulama çalışması sırasında bir doğrulama yönteminin tam olarak bir kez çağrıldığından emin olmak istiyorsanız, `IModel` doğrulayabilirsiniz:

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>Şekilleri ve diyagramları doğrulama
 Doğrulama yöntemlerinin birincil amacı modeli doğrulayacağından, diyagramlar ve şekiller gibi görüntüleme öğelerinde doğrulama yöntemleri çağrılmaz. Ancak diyagram bağlamını kullanarak geçerli diyagrama erişebilirsiniz.

 Doğrulama sınıfınıza içeri aktarılan özellik olarak `DiagramContext` bildirin:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 Bir doğrulama yönteminde, varsa geçerli odak diyagramına erişmek için `DiagramContext` kullanabilirsiniz:

```
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;
  if (focusDiagram != null)
  {
    foreach (IShape<IUseCase> useCaseShape in
              focusDiagram.GetChildShapes<IUseCase>())
    { ...
```

 Bir hatayı günlüğe kaydetmek için şeklin gösterdiği model öğesini edinmeniz gerekir, çünkü `LogError` bir şekil geçiremezsiniz:

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="ContextCache"></a>Birden çok doğrulamayı koordine etme
 Doğrulama çağrıldığında, örneğin bir diyagram menüsünden Kullanıcı tarafından her bir doğrulama yöntemi her bir model öğesine uygulanır. Bu, doğrulama çerçevesinin tek bir çağrısında aynı yöntemin farklı öğelere birçok kez uygulanabileceğini gösterir.

 Bu, öğeler arasındaki ilişkilerle ilgilenen doğrulamalar için bir sorun gösterir. Örneğin, ' den başlayan bir doğrulama yazabilir, bir kullanım örneği ve bir döngü olmadığını doğrulamak için **dahil etme** ilişkilerinden geçiş yapabilirsiniz. Ancak yöntem, çok sayıda **ekleme** bağlantısı olan bir modelde her kullanım örneğine uygulandığında, modelin aynı alanlarının tekrar tekrar işlenmesi olasıdır.

 Bu durumdan kaçınmak için, doğrulama çalıştırması sırasında bilgilerin korunduğu bir bağlam önbelleği vardır. Doğrulama yöntemlerinin farklı yürütmeleri arasında bilgi geçirmek için kullanabilirsiniz. Örneğin, bu doğrulama çalıştırmasında zaten ele alınmış öğelerin bir listesini saklayabilirsiniz. Önbellek her doğrulama çalıştırmasının başlangıcında oluşturulur ve farklı doğrulama çalıştırmaları arasında bilgi geçirmek için kullanılamaz.

|||
|-|-|
|`context.SetCacheValue<T> (name, value)`|Bir değer depola|
|`context.TryGetCacheValue<T> (name, out value)`|Bir değer alın. Başarılı olursa true döndürür.|
|`context.GetValue<T>(name)`|Bir değer alın.|
|`Context.GetValue<T>()`|Belirtilen türde bir değer alır.|

## <a name="Installing"></a>Uzantı yükleme ve kaldırma
 Hem kendi bilgisayarınıza hem de diğer bilgisayarlara bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı yükleyebilirsiniz.

#### <a name="to-install-an-extension"></a>Uzantı yüklemek için

1. Bilgisayarınızda, VSıX projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **klasörü Windows Gezgini 'nde aç**' ı seçin.

    2. Dosya **bin \\ \* bulun \\** _yourproject_ **. vsix**

2. **. Vsix** dosyasını, uzantıyı yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

    - Hedef bilgisayar, **kaynak. Extension. valtmanifest**içinde belirttiğiniz [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sürümlerinden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasını açın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. @No__t_0 başlatın veya yeniden başlatın.

#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Yüklü uzantıları**genişletin.

3. Uzantıyı seçin ve ardından **Kaldır**' ı seçin.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı şu konumda silerek uzantıyı kaldırabilirsiniz: *% LocalAppData%* genellikle *DriveName*: \Users \\*UserName*\AppData\Local:

   *% LocalAppData%* **\microsoft\visualstudio \\ [sürüm] \Extensions**

## <a name="Example"></a>Örneğinde
 Bu örnek, öğeler arasındaki bağımlılık ilişkisindeki döngüleri bulur.

 Her ikisini de Kaydet ve Doğrula menü komutunda doğrular.

```
/// <summary>
/// Verify that there are no loops in the dependency relationsips.
/// In our project, no element should be a dependent of itself.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">Element to start validation from.</param>
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu
     | ValidationCategories.Save | ValidationCategories.Open)]
public void NoDependencyLoops(ValidationContext context, INamedElement element)
{
    // The validation framework will call this method
    // for every element in the model. But when we follow
    // the dependencies from one element, we will validate others.
    // So we keep a list of the elements that we don't need to validate again.
    // The list is kept in the context cache so that it is passed
    // from one execution of this method to another.
    List<INamedElement> alreadySeen = null;
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))
    {
       alreadySeen = new List<INamedElement>();
       context.SetCacheValue("No dependency loops", alreadySeen);
    }

    NoDependencyLoops(context, element,
                new INamedElement[0], alreadySeen);
}

/// <summary>
/// Log an error if there is any loop in the dependency relationship.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">The element to be validated.</param>
/// <param name="dependants">Elements we've followed in this recursion.</param>
/// <param name="alreadySeen">Elements that have already been validated.</param>
/// <returns>true if no error was detected</returns>
private bool NoDependencyLoops(ValidationContext context,
    INamedElement element, INamedElement[] dependants,
    List<INamedElement> alreadySeen)
{
    if (dependants.Contains(element))
    {
        context.LogError(string.Format("{0} should not depend on itself", element.Name),
        "Fabrikam.UML.NoGenLoops", // unique code for this error
        dependants.SkipWhile(e => e != element).ToArray());
            // highlight elements that are in the loop
        return false;
    }
    INamedElement[] dependantsPlusElement =
        new INamedElement[dependants.Length + 1];
    dependants.CopyTo(dependantsPlusElement, 0);
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;

    if (alreadySeen.Contains(element))
    {
        // We have already validated this when we started
        // from another element during this validation run.
        return true;
    }
    alreadySeen.Add(element);

    foreach (INamedElement supplier in element.GetDependencySuppliers())
    {
        if (!NoDependencyLoops(context, supplier,
             dependantsPlusElement, alreadySeen))
        return false;
    }
    return true;
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [UML API ile](../modeling/programming-with-the-uml-api.md) [modelleme uzantısı programlama tanımlama ve yüklemeyi](../modeling/define-and-install-a-modeling-extension.md)
