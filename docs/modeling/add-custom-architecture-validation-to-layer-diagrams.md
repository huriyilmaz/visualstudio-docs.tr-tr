---
title: Bağımlılık diyagramlarına özel mimari doğrulaması ekleme
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98482eed6c1ed5a8ac2e3bbb7b5ada6af9517c1d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546932"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Bağımlılık diyagramlarına özel mimari doğrulaması ekleme

Visual Studio 'da, kullanıcılar bir projedeki kaynak kodu bir katman modeline karşı doğrulayabilir, böylece kaynak kodun bir bağımlılık diyagramındaki bağımlılıklara uygun olduğunu doğrulayabilirler. Standart bir doğrulama algoritması vardır, ancak kendi doğrulama uzantılarınızı tanımlayabilirsiniz.

Kullanıcı bir bağımlılık diyagramında **Mimariyi Doğrula** komutunu seçtiğinde, standart doğrulama yöntemi çağrılır ve ardından yüklenmiş herhangi bir doğrulama uzantısı gelir.

> [!NOTE]
> Bağımlılık diyagramında, doğrulamanın ana amacı, diyagramı çözümün diğer bölümlerinde program koduyla karşılaştırmaktır.

Katman doğrulama uzantınızı, diğer Visual Studio kullanıcılarına dağıtabileceğiniz bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) paketleyebilir. Doğrulayıcının kendisini bir VSıX 'e yerleştirebilirsiniz veya diğer uzantılarla aynı VSıX içinde birleştirebilirsiniz. Doğrulayıcının kodunu, diğer uzantılarla aynı projede değil, kendi Visual Studio projesinde yazmanız gerekir.

> [!WARNING]
> Bir doğrulama projesi oluşturduktan sonra, bu konunun sonundaki [örnek kodu](#example) kopyalayın ve ardından kendi gereksinimlerinize göre düzenleyin.

## <a name="requirements"></a>Gereksinimler

[Gereksinimlere](../modeling/extend-layer-diagrams.md#requirements)bakın.

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Yeni bir VSıX 'te katman doğrulayıcısı tanımlama

Doğrulayıcı oluşturmanın en hızlı yöntemi, proje şablonunu kullanmaktır. Bu, kodu ve VSıX bildirimini aynı projeye koyar.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Bir proje şablonu kullanarak bir uzantı tanımlamak için

1. Yeni bir **Katman Tasarımcısı doğrulama uzantısı** projesi oluşturun.

    Şablon, küçük bir örnek içeren bir proje oluşturur.

   > [!WARNING]
   > Şablonun düzgün çalışmasını sağlamak için:
   >
   > - `LogValidationError`İsteğe bağlı bağımsız değişkenleri kaldırmak için çağrılarını düzenleyin `errorSourceNodes` `errorTargetNodes` .
   > - Özel özellikler kullanıyorsanız, [bağımlılık diyagramlarına özel özellikler ekle](../modeling/add-custom-properties-to-layer-diagrams.md)bölümünde bahsedilen güncelleştirmeyi uygulayın.

2. Doğrulamayı tanımlamak için kodu düzenleyin. Daha fazla bilgi için bkz. [programlama doğrulaması](#programming).

3. Uzantıyı test etmek için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

   > [!NOTE]
   > Yönteminiz yalnızca belirli koşullarda çağrılacaktır ve kesme noktaları otomatik olarak çalışmayacaktır. Daha fazla bilgi için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

::: moniker range="vs-2017"

4. Uzantıyı Visual Studio 'nun ana örneğine veya başka bir bilgisayara yüklemek için *bin* dizininde *. vsix* dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler** ' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

4. Uzantıyı Visual Studio 'nun ana örneğine veya başka bir bilgisayara yüklemek için *bin* dizininde *. vsix* dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için **Uzantılar** menüsünde **Uzantıları Yönet** ' i seçin.

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Ayrı bir VSıX 'e katman doğrulayıcısı ekleme

Katman Doğrulayıcıları, komutlar ve diğer uzantıları içeren bir VSıX oluşturmak istiyorsanız, VSıX tanımlamak için bir proje oluşturmanızı ve işleyiciler için ayrı projeler oluşturmanızı öneririz.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Ayrı bir VSıX 'e katman doğrulaması eklemek için

1. Yeni bir **sınıf kitaplığı** projesi oluşturun. Bu proje, katman doğrulama sınıfını içerecektir.

2. Çözümünüzde bir **VSIX projesi** bulun veya oluşturun. VSıX projesi, **kaynak. Extension. valtmanifest**adlı bir dosya içerir.

3. **Çözüm Gezgini**, VSIX projesinin sağ tıklama menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.

4. **Source. Extension. valtmanifest**Içinde, **varlıklar**altında, katman doğrulama projesini MEF bileşeni olarak ekleyin:

    1. **Yeni**'yi seçin.

    2. **Yeni varlık Ekle** iletişim kutusunda, şunu ayarlayın:

         **Tür**  =  **Microsoft. VisualStudio. MefComponent**

         **Kaynak**  =  **Geçerli çözümdeki bir proje**

         **Proje**  =  *Doğrulayıcı projeniz*

5. Ayrıca, katman doğrulaması olarak da eklemeniz gerekir:

    1. **Yeni**'yi seçin.

    2. **Yeni varlık Ekle** iletişim kutusunda, şunu ayarlayın:

         **Tür**  =  **Microsoft. VisualStudio. mimari Turetools. Layer. Validator**. Bu, açılan listedeki seçeneklerden biri değildir. Bunu klavyeden girmeniz gerekir.

         **Kaynak**  =  **Geçerli çözümdeki bir proje**

         **Proje**  =  *Doğrulayıcı projeniz*

6. Katman doğrulama projesine dönün ve aşağıdaki proje başvurularını ekleyin:

    |**Başvuru**|**Bunu yapmanıza izin verir**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Mimari grafiğini okuyun|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Katmanlarla ilişkili kod DOM 'ı okuyun|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Katman modelini okuyun|
    |Microsoft. VisualStudio. mimari Turetools. Extensibility|Şekilleri ve diyagramları okuyun ve güncelleştirin.|
    |System. ComponentModel. Composition|Managed Extensibility Framework (MEF) kullanarak doğrulama bileşenini tanımlama|
    |Microsoft. VisualStudio. model. SDK. sürümünüze|Modelleme uzantıları tanımlama|

7. Bu konunun sonundaki örnek kodu, doğrulanmak üzere kodu içerecek şekilde Doğrulayıcı Kitaplığı projesindeki sınıf dosyasına kopyalayın. Daha fazla bilgi için bkz. [programlama doğrulaması](#programming).

8. Uzantıyı test etmek için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

    > [!NOTE]
    > Yönteminiz yalnızca belirli koşullarda çağrılacaktır ve kesme noktaları otomatik olarak çalışmayacaktır. Daha fazla bilgi için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

9. VSıX 'i Visual Studio 'nun ana örneğine veya başka bir bilgisayara yüklemek için VSıX projesinin **bin** dizininde **. vsix** dosyasını bulun. VSıX 'i yüklemek istediğiniz bilgisayara kopyalayın. Windows Gezgini 'nde VSıX dosyasına çift tıklayın.

## <a name="programming-validation"></a><a name="programming"></a>Programlama doğrulaması

Katman doğrulama uzantısı tanımlamak için aşağıdaki özelliklere sahip bir sınıf tanımlarsınız:

- Bildirimin Genel formu aşağıdaki gibidir:

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Bir hata keşfettiğiniz zaman, kullanarak rapor edebilirsiniz `LogValidationError()` .

  > [!WARNING]
  > İsteğe bağlı parametrelerini kullanmayın `LogValidationError` .

Kullanıcı **Mimariyi Doğrula** menü komutunu çağırdığında, katman çalışma zamanı sistemi katmanları ve bunların yapılarını analiz etmek için bir grafik oluşturur. Grafik dört bölümden oluşur:

- Visual Studio çözümünün, grafikte düğüm ve bağlantı olarak temsil edilen katman modelleri.

- Kod, proje öğeleri ve çözümde tanımlanan ve düğüm olarak temsil edilen diğer yapıtlar ve analiz işlemi tarafından bulunan bağımlılıkları temsil eden bağlantılar.

- Katman düğümlerinden kod yapıt düğümlerine bağlantılar.

- Doğrulayıcı tarafından bulunan hataları temsil eden düğümler.

Grafik oluşturulduğunda, standart doğrulama yöntemi çağrılır. Bu tamamlandığında, yüklenmiş tüm uzantı doğrulama yöntemleri belirtilmemiş sırada çağırılır. Grafik her metoda geçirilir ve bu, `ValidateArchitecture` grafiği tarayabilmesi ve bulduğu hataları bildirebilir.

> [!NOTE]
> Bu, etki alanına özgü dillerde kullanılabilen doğrulama işlemiyle aynı değildir.

Doğrulama yöntemleri, bir katman modelini veya Doğrulanmakta olan kodu değiştirmemelidir.

Grafik modeli içinde tanımlanmıştır <xref:Microsoft.VisualStudio.GraphModel> . Asıl sınıfları <xref:Microsoft.VisualStudio.GraphModel.GraphNode> ve ' dir <xref:Microsoft.VisualStudio.GraphModel.GraphLink> .

Her bir düğüm ve her bağlantı, temsil ettiği öğe veya ilişki türünü belirten bir veya daha fazla kategoriye sahiptir. Tipik bir grafiğin düğümleri aşağıdaki kategorilere sahiptir:

- DSL. LayerModel

- DSL. Layer

- DSL. Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Katmanların koddaki öğelere olan bağlantıları "temsil" kategorisine sahiptir.

## <a name="debugging-validation"></a><a name="debugging"></a>Hata ayıklama doğrulaması

Katman doğrulama uzantınızdaki hataları ayıklamak için CTRL + F5 tuşlarına basın. Visual Studio 'nun deneysel bir örneği açılır. Bu örnekte, bir katman modeli açın veya oluşturun. Bu modelin, kodla ilişkilendirilmesi ve en az bir bağımlılığı olması gerekir.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Bağımlılıklar içeren bir çözümle test etme

Aşağıdaki özellikler mevcut olmadığı takdirde doğrulama yürütülmez:

- Bağımlılık diyagramında en az bir bağımlılık bağlantısı vardır.

- Modelde kod öğeleriyle ilişkili katmanlar vardır.

Doğrulama uzantınızı test etmek için Visual Studio 'nun deneysel bir örneğini ilk kez başlattığınızda, bu özelliklere sahip bir çözüm açın veya oluşturun.

### <a name="run-clean-solution-before-validate-architecture"></a>Mimariyi doğrulamadan önce temiz çözümü Çalıştır

Doğrulama kodunuzu güncelleştirdiğinizde, Validate komutunu test etmeden önce deneysel çözümdeki **Build menüsündeki Build** ( **Çözümü Temizle** ) komutunu kullanın. Doğrulama sonuçları önbelleğe alındığından bu gereklidir. Test bağımlılığı diyagramını veya kodunu güncelleştirmediyseniz, doğrulama yöntemleri yürütülmez.

### <a name="launch-the-debugger-explicitly"></a>Hata ayıklayıcıyı açık olarak Başlat

Doğrulama ayrı bir işlemde çalışır. Bu nedenle, doğrulama yönteminizin kesme noktaları tetiklenmeyecektir. Doğrulama başladığında işlem ayıklayıcıyı işleme açıkça iliştirmelidir.

Hata ayıklayıcıyı doğrulama işlemine iliştirmek için, doğrulama yönteminizin başlangıcında öğesine bir çağrı ekleyin `System.Diagnostics.Debugger.Launch()` . Hata ayıklama iletişim kutusu göründüğünde, Visual Studio 'nun ana örneğini seçin.

Alternatif olarak, öğesine bir çağrı ekleyebilirsiniz `System.Windows.Forms.MessageBox.Show()` . İleti kutusu göründüğünde, Visual Studio 'nun ana örneğine gidin ve **Hata Ayıkla** menüsünde **işleme Ekle**' ye tıklayın. **Graphcmd.exe**adlı işlemi seçin.

CTRL + F5 tuşuna basarak (**hata ayıklama olmadan Başlat**) deneysel örneği her zaman başlatın.

### <a name="deploying-a-validation-extension"></a>Doğrulama uzantısı dağıtma

Doğrulama uzantınızı, uygun bir Visual Studio sürümünün yüklü olduğu bir bilgisayara yüklemek için hedef bilgisayarda VSıX dosyasını açın.

## <a name="example-code"></a><a name="example"></a>Örnek kod

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
