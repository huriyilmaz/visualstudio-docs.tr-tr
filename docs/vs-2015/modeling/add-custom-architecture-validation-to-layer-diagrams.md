---
title: Katman diyagramlarına özel mimari doğrulaması ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b5ebe4e38878df209ab6065b1dbca88cd8404b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655298"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>Katman diyagramlarına özel mimari doğrulaması ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, kullanıcılar bir projedeki kaynak kodu bir katman modeline karşı doğrulayabilir, böylece kaynak kodun bir katman diyagramındaki bağımlılıklara uygun olduğunu doğrulayabilirler. Standart bir doğrulama algoritması vardır, ancak kendi doğrulama uzantılarınızı tanımlayabilirsiniz.

 Kullanıcı bir katman diyagramında **Mimariyi Doğrula** komutunu seçtiğinde, standart doğrulama yöntemi çağrılır ve ardından yüklenmiş herhangi bir doğrulama uzantısı gelir.

> [!NOTE]
> Bir katman diyagramındaki doğrulama, UML diyagramlarındaki doğrulamayla aynı değildir. Katman diyagramında ana amaç, çözümün diğer bölümlerinde diyagramı program koduyla karşılaştırmaktır.

 Katman doğrulama uzantınızı, diğer Visual Studio kullanıcılarına dağıtabileceğiniz bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) paketleyebilir. Doğrulayıcının kendisini bir VSıX 'e yerleştirebilirsiniz veya diğer uzantılarla aynı VSıX içinde birleştirebilirsiniz. Doğrulayıcının kodunu, diğer uzantılarla aynı projede değil, kendi Visual Studio projesinde yazmanız gerekir.

> [!WARNING]
> Bir doğrulama projesi oluşturduktan sonra, bu konunun sonundaki [örnek kodu](#example) kopyalayın ve ardından kendi gereksinimlerinize göre düzenleyin.

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-layer-diagrams.md#prereqs)bakın.

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Yeni bir VSıX 'te katman doğrulayıcısı tanımlama
 Doğrulayıcı oluşturmanın en hızlı yöntemi, proje şablonunu kullanmaktır. Bu, kodu ve VSıX bildirimini aynı projeye koyar.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Bir proje şablonu kullanarak bir uzantı tanımlamak için

1. **Dosya** menüsündeki **Yeni proje** komutunu kullanarak yeni bir çözümde bir proje oluşturun.

2. **Yeni proje** iletişim kutusunda, **modelleme projeleri**' nin altında, **Katman Tasarımcısı doğrulama uzantısı**' nı seçin.

    Şablon, küçük bir örnek içeren bir proje oluşturur.

   > [!WARNING]
   > Şablon doğru şekilde çalışması için:
   >
   > - @No__t_1 ve `errorTargetNodes` isteğe bağlı bağımsız değişkenleri kaldırmak için `LogValidationError` çağrılarını düzenleyin.
   >   - Özel özellikler kullanıyorsanız, [Katman diyagramlarına özel özellikler ekle](../modeling/add-custom-properties-to-layer-diagrams.md)bölümünde bahsedilen güncelleştirmeyi uygulayın.

3. Doğrulamayı tanımlamak için kodu düzenleyin. Daha fazla bilgi için bkz. [programlama doğrulaması](#programming).

4. Uzantıyı test etmek için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

   > [!NOTE]
   > Yönteminiz yalnızca belirli koşullarda çağrılacaktır ve kesme noktaları otomatik olarak çalışmayacaktır. Daha fazla bilgi için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

5. Uzantıyı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana örneğine veya başka bir bilgisayara yüklemek için, *bin \\* **. vsix** dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler** ' i kullanın.

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Ayrı bir VSıX 'e katman doğrulayıcısı ekleme
 Katman Doğrulayıcıları, komutlar ve diğer uzantıları içeren bir VSıX oluşturmak istiyorsanız, VSıX tanımlamak için bir proje oluşturmanızı ve işleyiciler için ayrı projeler oluşturmanızı öneririz. Diğer modelleme uzantısı türleri hakkında daha fazla bilgi için bkz. [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Ayrı bir VSıX 'e katman doğrulaması eklemek için

1. Yeni veya mevcut bir Visual Studio çözümünde bir sınıf kitaplığı projesi oluşturun. **Yeni proje** iletişim kutusunda,  **C# görsel** ' e ve ardından **sınıf kitaplığı**' na tıklayın. Bu proje, katman doğrulama sınıfını içerecektir.

2. Çözümünüzde bir VSıX projesi oluşturun veya oluşturun. VSıX projesi, **kaynak. Extension. valtmanifest**adlı bir dosya içerir. Bir VSıX projesi eklemeniz gerekiyorsa, şu adımları izleyin:

    1. **Yeni proje** iletişim kutusunda, **görsel C#** , **genişletilebilirlik**, **VSIX projesi**' ni seçin.

    2. **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **Başlangıç projesi olarak ayarlayın**.

3. **Source. Extension. valtmanifest**Içinde, **varlıklar**altında, katman doğrulama projesini MEF bileşeni olarak ekleyin:

    1. **Yeni**' yi seçin.

    2. **Yeni varlık Ekle** iletişim kutusunda, şunu ayarlayın:

         **Microsoft. VisualStudio. MefComponent**  =  **yazın**

         **Kaynak**  = **geçerli çözümdeki bir proje**

         *Doğrulayıcı projenize* **Proje**  = 

4. Ayrıca, katman doğrulaması olarak da eklemeniz gerekir:

    1. **Yeni**' yi seçin.

    2. **Yeni varlık Ekle** iletişim kutusunda, şunu ayarlayın:

         **Microsoft. VisualStudio. mimari Turetools. Layer. Validator** =  **yazın** . Bu, açılan listedeki seçeneklerden biri değildir. Bunu klavyeden girmeniz gerekir.

         **Kaynak**  = **geçerli çözümdeki bir proje**

         *Doğrulayıcı projenize* **Proje**  = 

5. Katman doğrulama projesine dönün ve aşağıdaki proje başvurularını ekleyin:

    |**Başvuru**|**Bunu yapmanıza izin verir**|
    |-------------------|------------------------------------|
    |Microsoft. VisualStudio. GraphModel. dll|Mimari grafiğini okuyun|
    |Microsoft. VisualStudio. mimari Turetools. Extensibility. CodeSchema. dll|Katmanlarla ilişkili kod DOM 'ı okuyun|
    |Microsoft. VisualStudio. mimari Turetools. Extensibility. Layer. dll|Katman modelini okuyun|
    |Microsoft. VisualStudio. mimari Turetools. Extensibility|Şekilleri ve diyagramları okuyun ve güncelleştirin.|
    |System. ComponentModel. Composition|Managed Extensibility Framework (MEF) kullanarak doğrulama bileşenini tanımlama|
    |Microsoft. VisualStudio. model. SDK. sürümünüze|Modelleme uzantıları tanımlama|

6. Bu konunun sonundaki örnek kodu, doğrulanmak üzere kodu içerecek şekilde Doğrulayıcı Kitaplığı projesindeki sınıf dosyasına kopyalayın. Daha fazla bilgi için bkz. [programlama doğrulaması](#programming).

7. Uzantıyı test etmek için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

    > [!NOTE]
    > Yönteminiz yalnızca belirli koşullarda çağrılacaktır ve kesme noktaları otomatik olarak çalışmayacaktır. Daha fazla bilgi için bkz. [Katman doğrulamasında hata ayıklama](#debugging).

8. VSıX 'i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana örneğine veya başka bir bilgisayara yüklemek için VSıX projesinin **bin** dizininde **. vsix** dosyasını bulun. VSıX 'i yüklemek istediğiniz bilgisayara kopyalayın. Windows Gezgini 'nde VSıX dosyasına çift tıklayın. (Windows 8 ' de dosya Gezgini.)

     Kaldırmak için, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler** ' i kullanın.

## <a name="programming"></a>Programlama doğrulaması
 Katman doğrulama uzantısı tanımlamak için aşağıdaki özelliklere sahip bir sınıf tanımlarsınız:

- Bildirimin Genel formu aşağıdaki gibidir:

  ```

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

- Bir hata keşfettiğiniz zaman, `LogValidationError()` kullanarak rapor edebilirsiniz.

  > [!WARNING]
  > İsteğe bağlı `LogValidationError` parametrelerini kullanmayın.

  Kullanıcı **Mimariyi Doğrula** menü komutunu çağırdığında, katman çalışma zamanı sistemi katmanları ve bunların yapılarını analiz etmek için bir grafik oluşturur. Grafik dört bölümden oluşur:

- Grafikte düğüm ve bağlantı olarak temsil edilen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümünün katman modelleri.

- Kod, proje öğeleri ve çözümde tanımlanan ve düğüm olarak temsil edilen diğer yapıtlar ve analiz işlemi tarafından bulunan bağımlılıkları temsil eden bağlantılar.

- Katman düğümlerinden kod yapıt düğümlerine bağlantılar.

- Doğrulayıcı tarafından bulunan hataları temsil eden düğümler.

  Grafik oluşturulduğunda, standart doğrulama yöntemi çağrılır. Bu tamamlandığında, yüklenmiş tüm uzantı doğrulama yöntemleri belirtilmemiş sırada çağırılır. Grafik, grafiği tarayabileceğiniz ve bulduğu hataları rapor eden her bir `ValidateArchitecture` yöntemine geçirilir.

> [!NOTE]
> Bu, UML diyagramlarına uygulanan doğrulama işlemi ile aynı değildir ve etki alanına özgü dillerde kullanılabilecek doğrulama işlemiyle aynı değildir.

 Doğrulama yöntemleri, bir katman modelini veya Doğrulanmakta olan kodu değiştirmemelidir.

 Grafik modeli <xref:Microsoft.VisualStudio.GraphModel> tanımlanmıştır. Asıl sınıfları <xref:Microsoft.VisualStudio.GraphModel.GraphNode> ve <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

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

## <a name="debugging"></a>Hata ayıklama doğrulaması
 Katman doğrulama uzantınızdaki hataları ayıklamak için CTRL + F5 tuşlarına basın. Deneysel bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] örneği açılır. Bu örnekte, bir katman modeli açın veya oluşturun. Bu modelin, kodla ilişkilendirilmesi ve en az bir bağımlılığı olması gerekir.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Bağımlılıklar içeren bir çözümle test etme
 Aşağıdaki özellikler mevcut olmadığı takdirde doğrulama yürütülmez:

- Katman diyagramında en az bir bağımlılık bağlantısı vardır.

- Modelde kod öğeleriyle ilişkili katmanlar vardır.

  Doğrulama uzantınızı test etmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Deneysel örneğini ilk kez başlattığınızda, bu özelliklere sahip bir çözüm açın veya oluşturun.

### <a name="run-clean-solution-before-validate-architecture"></a>Mimariyi doğrulamadan önce temiz çözümü Çalıştır
 Doğrulama kodunuzu güncelleştirdiğinizde, Validate komutunu test etmeden önce deneysel çözümdeki **Build menüsündeki Build** ( **Çözümü Temizle** ) komutunu kullanın. Doğrulama sonuçları önbelleğe alındığından bu gereklidir. Test katmanı diyagramını veya kodunu güncelleştirmediyseniz, doğrulama yöntemleri yürütülmez.

### <a name="launch-the-debugger-explicitly"></a>Hata ayıklayıcıyı açık olarak Başlat
 Doğrulama ayrı bir işlemde çalışır. Bu nedenle, doğrulama yönteminizin kesme noktaları tetiklenmeyecektir. Doğrulama başladığında işlem ayıklayıcıyı işleme açıkça iliştirmelidir.

 Hata ayıklayıcıyı doğrulama işlemine iliştirmek için, doğrulama yönteminizin başlangıcında `System.Diagnostics.Debugger.Launch()` bir çağrı ekleyin. Hata ayıklama iletişim kutusu göründüğünde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana örneğini seçin.

 Alternatif olarak, `System.Windows.Forms.MessageBox.Show()` bir çağrı ekleyebilirsiniz. İleti kutusu göründüğünde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ana örneğine gidin ve **Hata Ayıkla** menüsünde **İşleme İliştir**' e tıklayın. **GraphCmd. exe**adlı işlemi seçin.

 CTRL + F5 tuşuna basarak (**hata ayıklama olmadan Başlat**) deneysel örneği her zaman başlatın.

### <a name="deploying-a-validation-extension"></a>Doğrulama uzantısı dağıtma
 Doğrulama uzantınızı, uygun bir Visual Studio sürümünün yüklü olduğu bir bilgisayara yüklemek için hedef bilgisayarda VSıX dosyasını açın. @No__t_0 yüklü olan bir bilgisayara yüklemek için VSıX içeriğini bir Uzantılar klasörüne el ile ayıklamanız gerekir. Daha fazla bilgi için bkz. [Katman modeli uzantısı dağıtma](../modeling/deploy-a-layer-model-extension.md).

## <a name="example"></a>Örnek kod

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

## <a name="see-also"></a>Ayrıca Bkz.
 [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
