---
title: Bağımlılık diyagramlarına özel mimari doğrulaması ekleme
description: Bağımlılık diyagramları için özel mimari doğrulaması ekleme hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: c917ecacdfbe95965ae7a571b251e89c62c23eda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069366"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Bağımlılık diyagramlarına özel mimari doğrulaması ekleme

Kullanıcılar Visual Studio projesinde kaynak kodu katman modeline göre doğrular ve böylece kaynak kodun bağımlılık diyagramındaki bağımlılıklara uygun olduğunu doğrular. Standart bir doğrulama algoritması vardır, ancak kendi doğrulama uzantılarınızı tanımlayabilirsiniz.

Kullanıcı bağımlılık **diyagramında** Mimariyi Doğrula komutunu seçerken, standart doğrulama yöntemi çağrılır ve ardından yüklenmiş doğrulama uzantıları kullanılır.

> [!NOTE]
> Bağımlılık diyagramında doğrulamanın asıl amacı, diyagramı çözümün diğer kısımlarında yer alan program koduyla karşılaştırmaktır.

Katman doğrulama uzantınızı, diğer kullanıcılara dağıtabilirsiniz Visual Studio Tümleştirme Uzantısı (VSIX) Visual Studio paketleyebilirsiniz. Doğrulayıcınızı bir VSIX'e tek başına yer ya da diğer uzantılarla aynı VSIX'te birleştirin. Doğrulayıcının kodunu diğer uzantılar ile aynı Visual Studio kendi projesinde yazmanız gerekir.

> [!WARNING]
> Bir doğrulama projesi oluşturduktan sonra, bu konunun sonundaki örnek kodu kopyalayın ve bunu kendi ihtiyaçlarınıza göre düzenleyin. [](#example)

## <a name="requirements"></a>Gereksinimler

Bkz. [Gereksinimler.](../modeling/extend-layer-diagrams.md#requirements)

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Yeni VSIX'te Katman Doğrulayıcı Tanımlama

Doğrulayıcı oluşturmanın en hızlı yöntemi proje şablonunu kullanmaktır. Bu, kodu ve VSIX bildirimini aynı projeye yer alır.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Proje şablonu kullanarak uzantı tanımlamak için

1. Yeni bir Katman **Tasarımcısı Doğrulama Uzantısı projesi** oluşturun.

    Şablon, küçük bir örnek içeren bir proje oluşturur.

   > [!WARNING]
   > Şablonun düzgün çalışması için:
   >
   > - İsteğe bağlı `LogValidationError` ve bağımsız değişkenlerini kaldırmak için çağrıları `errorSourceNodes` `errorTargetNodes` düzenleyin.
   > - Özel özellikler kullanıyorsanız Bağımlılık diyagramları için özel özellikler [ekleme içinde belirtilen güncelleştirmeyi kullanın.](../modeling/add-custom-properties-to-layer-diagrams.md)

2. Doğrulamanızı tanımlamak için kodu düzenleyin. Daha fazla bilgi için bkz. [Programlama Doğrulaması.](#programming)

3. Uzantıyı test etmek için [bkz. Hata Ayıklama Katmanı Doğrulaması.](#debugging)

   > [!NOTE]
   > Yönteminiz yalnızca belirli durumlarda çağrılır ve kesme noktaları otomatik olarak çalışmaz. Daha fazla bilgi için [bkz. Hata Ayıklama Katmanı Doğrulaması.](#debugging)

::: moniker range="vs-2017"

4. Uzantıyı Visual Studio ana örneğine veya başka bir bilgisayara yüklemek için bin dizininde *.vsix* *dosyasını* bulun. Yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için Araçlar menüsünde **Uzantılar ve** Güncelleştirmeler'i seçin. 

::: moniker-end

::: moniker range=">=vs-2019"

4. Uzantıyı Visual Studio ana örneğine veya başka bir bilgisayara yüklemek için bin dizininde *.vsix* *dosyasını* bulun. Yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için Uzantılar **menüsünde Uzantıları** **Yönet'i** seçin.

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Ayrı BIR VSIX'e Katman Doğrulayıcı Ekleme

Katman doğrulayıcıları, komutları ve diğer uzantıları içeren bir VSIX oluşturmak için VSIX'i tanımlamak üzere bir proje ve işleyiciler için ayrı projeler oluşturmanızı öneririz.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Ayrı bir VSIX'e katman doğrulaması eklemek için

1. Yeni bir Sınıf **Kitaplığı projesi** oluşturun. Bu proje katman doğrulama sınıfını içerir.

2. Çözümde bir **VSIX Project** veya oluşturun. VSIX projesi, **source.extension.vsixmanifest adlı bir dosya içerir.**

3. Bu **Çözüm Gezgini** VSIX projesinin sağ tıklama menüsünde Başlangıç olarak ayarla'yı **Project.**

4. **source.extension.vsixmanifest içinde,** **Varlıklar'ın** altına katman doğrulama projesini MEF bileşeni olarak ekleyin:

    1. **Yeni**'yi seçin.

    2. Yeni **Varlık Ekle iletişim** kutusunda şunları ayarlayın:

         **Tür**  =  **Microsoft.VisualStudio.MefComponent**

         **Kaynak**  =  **Geçerli çözümde bir proje**

         **Project**  =  *doğrulayıcı projeniz*

5. Katman doğrulaması olarak da eklemeniz gerekir:

    1. **Yeni**'yi seçin.

    2. Yeni **Varlık Ekle iletişim** kutusunda şunları ayarlayın:

         **Tür**  =  **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Bu, açılan listede yer alan seçeneklerden biri değildir. Klavyeden girmeniz gerekir.

         **Kaynak**  =  **Geçerli çözümde bir proje**

         **Project**  =  *doğrulayıcı projeniz*

6. Katman doğrulama projesine geri dönüp aşağıdaki proje başvurularını ekleyin:

    |**Başvuru**|**Bu size ne sağlar?**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Mimari grafını okuma|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Katmanlarla ilişkili DOM kodunu okuma|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Katman modelini okuma|
    |Microsoft.VisualStudio.ArchitectureTools.Genişletilebilirlik|Şekilleri ve diyagramları okuma ve güncelleştirme.|
    |System.ComponentModel.Composition|Managed Extensibility Framework (MEF) kullanarak doğrulama bileşenini tanımlama|
    |Microsoft.VisualStudio.Modeling.Sdk. [sürüm]|Modelleme uzantılarını tanımlama|

7. Doğrulama kodunu içermesi için bu konunun sonundaki örnek kodu doğrulayıcı kitaplığı projesinde sınıf dosyasına kopyalayın. Daha fazla bilgi için bkz. [Programlama Doğrulaması.](#programming)

8. Uzantıyı test etmek için [bkz. Hata Ayıklama Katmanı Doğrulaması.](#debugging)

    > [!NOTE]
    > Yönteminiz yalnızca belirli durumlarda çağrılır ve kesme noktaları otomatik olarak çalışmaz. Daha fazla bilgi için [bkz. Hata Ayıklama Katmanı Doğrulaması.](#debugging)

9. VSIX'i Visual Studio ana örneğine veya başka bir bilgisayara yüklemek için VSIX projesinin bin dizininde **.vsix** dosyasını bulun.  VsIX'i yüklemek istediğiniz bilgisayara kopyalayın. Windows Explorer'da VSIX dosyasına çift tıklayın.

## <a name="programming-validation"></a><a name="programming"></a> Programlama Doğrulaması

Katman doğrulama uzantısını tanımlamak için aşağıdaki özelliklere sahip bir sınıf tanımlayın:

- Bildirimin genel biçimi aşağıdaki gibidir:

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

- Bir hata bulasanız kullanarak bunu `LogValidationError()` bildirebilirsiniz.

  > [!WARNING]
  > isteğe bağlı parametrelerini `LogValidationError` kullanmayın.

Kullanıcı Mimariyi **Doğrula** menü komutunu çağırsa, katman çalışma zamanı sistemi bir grafik üretmek için katmanları ve yapıtlarını analiz eder. Graf dört parçadan oluşur:

- Grafikte düğümler ve Visual Studio olarak temsil edilen bir çözüm olan Visual Studio katmanı modelleri.

- Çözümde tanımlanan ve düğüm olarak temsil edilen kod, proje öğeleri ve diğer yapıtlar ve analiz işlemi tarafından bulunan bağımlılıkları temsil eden bağlantılar.

- Katman düğümlerinden kod yapıt düğümlerine bağlantılar.

- Doğrulayıcı tarafından bulunan hataları temsil eden düğümler.

Graf 10000000000000000000000000000000000000000 Bu tamamlandığında, yüklü uzantı doğrulama yöntemleri belirtilmemiş sırada çağrılır. Graf her yönteme `ValidateArchitecture` geçirildi ve bu yöntem grafı tarar ve bulduğu hataları rapor eder.

> [!NOTE]
> Bu, etki alanına özgü dillerde kullanılan doğrulama işlemiyle aynı değildir.

Doğrulama yöntemleri katman modelini veya doğrulanmış kodu değiştirmez.

Graf modeli içinde <xref:Microsoft.VisualStudio.GraphModel> tanımlanır. Temel sınıfları ve <xref:Microsoft.VisualStudio.GraphModel.GraphNode> <xref:Microsoft.VisualStudio.GraphModel.GraphLink> 'tir.

Her Düğüm ve her Bağlantının temsil ettiği öğe veya ilişki türünü belirten bir veya daha fazla Kategori vardır. Tipik bir grafiğin düğümleri aşağıdaki kategorilere sahip:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Katmanlardan kodda öğelere bağlantılar "Temsil Eder" kategorisine sahiptir.

## <a name="debugging-validation"></a><a name="debugging"></a> Hata Ayıklama Doğrulaması

Katman doğrulama uzantınıza hata ayıklamak için CTRL+F5 tuşlarına basın. Deneysel bir Visual Studio açılır. Bu örnekte bir katman modeli açın veya oluşturun. Bu modelin kodla ilişkilendirilmiş olması ve en az bir bağımlılığı olması gerekir.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Bağımlılıkları içeren bir Çözümle test

Aşağıdaki özellikler mevcut olmadığı sürece doğrulama yürütülmez:

- Bağımlılık diyagramında en az bir bağımlılık bağlantısı vardır.

- Modelde kod öğeleriyle ilişkili katmanlar vardır.

Deneysel bir örneği ilk kez başlatan Visual Studio uzantınızı test etmek, bu özelliklere sahip bir çözüm açmak veya oluşturmak için kullanılır.

### <a name="run-clean-solution-before-validate-architecture"></a>Mimariyi Doğrulamadan Önce Temiz Çözümü Çalıştırma

Doğrulama kodunuzu her güncelleştirin,  Doğrulama komutunu test etmek için **önce** deneysel çözümün Derleme menüsündeki Çözümü Temizle komutunu kullanın. Doğrulama sonuçları önbelleğe alınmış olduğundan bu gereklidir. Test bağımlılığı diyagramını veya kodunu güncelleştirmemiş olursanız doğrulama yöntemleri yürütülmez.

### <a name="launch-the-debugger-explicitly"></a>Hata Ayıklayıcıyı Açıkça Başlatma

Doğrulama ayrı bir işlemde çalışır. Bu nedenle doğrulama yönteminizin kesme noktaları tetiklanmaz. Doğrulama başlatıldında hata ayıklayıcıyı işleme açıkça ekleyemedik.

Hata ayıklayıcısını doğrulama sürecine eklemek için doğrulama yönteminizin `System.Diagnostics.Debugger.Launch()` başlangıcına bir çağrısı ekler. Hata ayıklama iletişim kutusu görüntülendiğinde, hata ayıklama iletişim kutusunun Visual Studio.

Alternatif olarak, için bir çağrı eklemek de `System.Windows.Forms.MessageBox.Show()` vardır. İleti kutusu görüntülendiğinde, uygulamanın ana örneğine Visual Studio **hata** ayıkla menüsünde İşleme **Ekle'ye tıklayın.** Graphcmd.exeadlı işlemi **seçin.**

Deneysel örneği her zaman CTRL+F5 tuşlarına basarak başlat (**Hata Ayıklama olmadan başlat).**

### <a name="deploying-a-validation-extension"></a>Doğrulama Uzantısı Dağıtma

Doğrulama uzantınızı, uygulamanın uygun bir sürümünün Visual Studio yüklemek için hedef bilgisayarda VSIX dosyasını açın.

## <a name="example-code"></a><a name="example"></a> Örnek kod

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
