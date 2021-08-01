---
title: C# dilinde bir Görselleştirici Yazma | Microsoft Docs
description: C# dilinde basit Görselleştirici oluşturmak için bir yönergeyi izleyin. Görselleştirici öğe şablonu kullanılmadan, ve ile gereken adımları gösterir.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 0122b15dafffbb99249828bf08031512a71e11f3
ms.sourcegitcommit: 24dd8fbdf88eca005e9f01328ab57150de37d432
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2021
ms.locfileid: "115014847"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>İzlenecek yol: C 'de Görselleştirici Yazma\#

Bu izlenecek yol, C# kullanılarak basit Görselleştirici nasıl yazılacağını gösterir. bu kılavuzda oluşturacağınız görselleştirici, bir Windows formu kullanarak bir dizenin içeriğini görüntüler. Bu basit dize görselleştiricisi, özellikle de yararlı değildir, ancak diğer veri türleri için daha kullanışlı Görselleştiriciler oluşturmak üzere izlemeniz gereken temel adımları gösterir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. ayarlarınızı değiştirmek için **araçlar** menüsüne gidin ve **Ayarlar içeri aktar ve dışarı aktar**' ı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

Görselleştiricisi kodu, hata ayıklayıcısı tarafından okunacak bir DLL 'ye yerleştirilmelidir. Bu nedenle, ilk adım DLL için bir sınıf kitaplığı projesi oluşturmaktır.

## <a name="create-a-visualizer-manually"></a>El ile Görselleştirici oluşturma

Görselleştirici oluşturmak için aşağıdaki görevleri izleyin.

### <a name="to-create-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturmak için

* Yeni bir sınıf kitaplığı projesi oluşturun.

    ::: moniker range=">=vs-2019"
    **dosya**  >  **yeni**  >  **Project** seçin. Dil açılır penceresinde **C#**' ı seçin. Arama kutusuna **sınıf kitaplığı** yazın ve ardından **Sınıf Kitaplığı ' nı (.NET Framework)** seçin. **İleri**’ye tıklayın. Görüntülenen iletişim kutusunda adı yazın `MyFirstVisualizer` ve ardından **Oluştur**' a tıklayın.

    görselleştirici projesi için .net değil .NET Framework sınıf kitaplığı seçtiğinizden emin olun. görselleştirici .NET Framework olması gerekir, ancak çağıran uygulama .net olabilir.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **.NET Framework** öğesini seçin ve ardından ortadaki bölmede **sınıf kitaplığı (.NET Framework)** öğesini seçin.

    Sınıf kitaplığı için, gibi uygun bir ad yazın `MyFirstVisualizer` ve ardından **Oluştur** veya **Tamam**' a tıklayın.
    ::: moniker-end

   Sınıf kitaplığını oluşturduktan sonra, burada tanımlanan sınıfları kullanabilmeniz için Microsoft.VisualStudio.DebuggerVisualizers.DLL bir başvuru eklemeniz gerekir. Ancak başvuruyu eklemeden önce, bazı sınıfları anlamlı adlara sahip olacak şekilde yeniden adlandırmanız gerekir.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1. cs 'yi yeniden adlandırmak ve Microsoft. VisualStudio. Debuggervisualiciler eklemek için

1. **Çözüm Gezgini**, Class1. cs öğesine sağ tıklayın ve kısayol menüsünde **Yeniden Adlandır** ' ı seçin.

2. Adı Class1. CS iken DebuggerSide. cs gibi anlamlı bir şekilde değiştirin.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DebuggerSide. cs içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirir.

3. **Çözüm Gezgini**' de, **Başvurular** ' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle** ' yi seçin.

4. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, **araştır** ' ı seçin ve Microsoft.VisualStudio.DebuggerVisualizers.DLL bulun.

    DLL 'yi Visual Studio yükleme dizininin *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* alt dizininde bulabilirsiniz.

5. **Tamam**'a tıklayın.

6. DebuggerSide. cs dosyasında aşağıdaki `using` yönergelere ekleyin:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Artık hata ayıklayıcı tarafı kodu oluşturmaya hazırsınız. Bu, görselleştirmek istediğiniz bilgileri göstermek için hata ayıklayıcı içinde çalışan koddur. İlk olarak, `DebuggerSide` nesne bildirimini temel sınıftan devrabir şekilde değiştirmeniz gerekir `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer 'dan devralması için

1. DebuggerSide. cs dosyasında aşağıdaki kod satırına gidin:

   ```csharp
   public class DebuggerSide
   ```

2. Kodu şu şekilde değiştirin:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` geçersiz kılmanız gereken bir soyut yönteme ( `Show` ) sahiptir.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer. Show metodunu geçersiz kılmak için

- İçinde `public class DebuggerSide` , aşağıdaki yöntemi ekleyin **:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show`Yöntemi aslında Görselleştirici iletişim kutusunu veya diğer Kullanıcı arabirimini oluşturan kodu içerir ve hata ayıklayıcıdan Görselleştirici 'e geçirilmiş bilgileri görüntüler. İletişim kutusunu oluşturan kodu eklemeniz ve bilgileri görüntüetmeniz gerekir. bu izlenecek yolda, bunu bir Windows Forms ileti kutusu kullanarak yapacaksınız. İlk olarak, `using` System. Windows için bir başvuru ve yönerge eklemeniz gerekir. Formlarındaki.

### <a name="to-add-systemwindowsforms"></a>Sistem eklemek için. Windows. Formlarındaki

1. **Çözüm Gezgini**' de, **Başvurular** ' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle** ' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, **araştır**' ı seçin ve System.Windows.Forms.DLL bulun.

    DLL dosyasını *c:\ Windows \Microsoft.NET\Framework\v4.0.30319*' de bulabilirsiniz.

3. **Tamam**'a tıklayın.

4. DebuggerSide. cs dosyasında aşağıdaki `using` yönergelere ekleyin:

   ```csharp
   using System.Windows.Forms;
   ```

   Artık Görseliniz için Kullanıcı arabirimi oluşturmak ve göstermek üzere bazı kodlar ekleyeceksiniz. Bu ilk görselleştiriciniz olduğundan, Kullanıcı arabirimini basit tutacağız ve bir Ileti kutusu kullanacaksınız.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Görselleştirici çıkışını bir iletişim kutusunda göstermek için

1. `Show` yönteminde aşağıdaki kod satırını ekleyin:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Bu örnek kod hata işleme içermez. Gerçek bir Görselleştirici veya başka bir tür uygulamaya hata işleme eklemeniz gerekir.

2. **Build** menüsünde **myfirstgörselleştirici Build**' i seçin. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Hata ayıklayıcı tarafındaki kodun sonu. Ancak bir adım daha vardır, ancak hata ayıklanan tarafa hangi sınıf koleksiyonunun Görselleştirici olduğunu söyleyen özniteliği.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Hata ayıklanan taraf kodu için görselleştirilecek türü eklemek için

Hata ayıklayıcı tarafında bulunan kodda, özniteliği kullanılarak hata ayıklanan için görselleştirilecek türü (nesne kaynağı) belirtirsiniz <xref:System.Diagnostics.DebuggerVisualizerAttribute> . `Target`Özelliği görselleştirilecek türü ayarlar.

1. Aşağıdaki öznitelik kodunu, yönergelerden sonra, ancak önce DebuggerSide. cs öğesine ekleyin `using` `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. **Build** menüsünde **myfirstgörselleştirici Build**' i seçin. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Bu noktada, ilk Görselleştiricinizi tamamlanmıştır. Adımlara doğru bir şekilde uyuldıysanız Görselleştirici oluşturup içine yükleyebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ancak, ' a bir Görselleştirici yüklemeden önce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , doğru çalıştığından emin olmak için test etmeniz gerekir. Artık Görselleştirici öğesini içine yüklemeden çalıştırmak için bir test bandı oluşturacaksınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştiriciyi göstermek üzere bir test yöntemi eklemek için

1. Sınıfına aşağıdaki yöntemi ekleyin `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. **Build** menüsünde **myfirstgörselleştirici Build**' i seçin. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Daha sonra, görselleştiricisi DLL 'nizi çağırmak için bir yürütülebilir proje oluşturmanız gerekir. Basitlik için bir konsol uygulaması projesi kullanın.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Çözüme bir konsol uygulaması projesi eklemek için

1. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **yeni Project**' ye tıklayın.

    ::: moniker range=">=vs-2019"

    **dosya**  >  **yeni**  >  **Project** seçin. Dil açılır penceresinde **C#**' ı seçin. arama kutusuna **konsol uygulaması** yazın ve ardından **konsol uygulaması (.NET Framework)** veya .net için **konsol uygulaması** ' nı seçin. **İleri**’ye tıklayın. Görüntülenen iletişim kutusunda adı yazın `MyTestConsole` ve ardından **Oluştur**' a tıklayın.

    > [!NOTE]
    > test bandı kullanarak görselleştiriciyi kolayca test etmek istiyorsanız bir .NET Framework konsol uygulaması oluşturun. Bunun yerine bir .NET konsol uygulaması oluşturabilirsiniz, ancak daha sonra açıklanan test bandı .NET için henüz desteklenmiyor, bu yüzden test etmek için Görselleştirici yüklemeniz gerekir. Bir .NET konsol uygulaması için öncelikle konsol uygulamasını buradan oluşturun, gerekli DLL ve proje başvurularını ekleyin ve ardından [hata ayıklanan tarafı veri nesnesi ekleme](#add-a-debuggee-side-data-object)bölümünde açıklanan adımları uygulayın. ASP.NET Core senaryolar için bkz. [.net 5.0 + için özel hata ayıklayıcı tarafı konuları](../debugger/create-custom-visualizers-of-data.md#special-debugger-side-considerations-for-net-50).
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **masaüstü Windows**' yi seçin ve ardından ortadaki bölmede **konsol uygulaması ' nı (.NET Framework)** seçin.

    Sınıf kitaplığı için, gibi uygun bir ad yazın `MyTestConsole` ve ardından **Tamam**' a tıklayın.
    ::: moniker-end

   Şimdi, MyTestConsole Myfirstgörselleştirici çağırabilmesi için gerekli başvuruları eklemeniz gerekir.

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole'a gerekli başvuruları eklemek için

1. Bu **Çözüm Gezgini,** **MyTestConsole'a** sağ tıklayın ve kısayol **menüsünde Başvuru** Ekle'yi seçin.

2. Başvuru Ekle **iletişim kutusunda** Gözat sekmesinde **Ekle'yi** Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. **Tamam**'a tıklayın.

4. **MyTestConsole'a sağ tıklayın ve** yeniden Başvuru **Ekle'yi** seçin.

5. Başvuru Ekle **iletişim kutusunda** Projeler sekmesine **ve** ardından MyFirstVisualizer'a tıklayın.

6. **Tamam**'a tıklayın.

   Şimdi testi tamamlamak için kodu eksersiniz.

### <a name="to-add-code-to-mytestconsole"></a>MyTestConsole'a kod eklemek için

1. Bu **Çözüm Gezgini** Program.cs'ye sağ tıklayın ve kısayol menüsünde **Yeniden** Adlandır'ı seçin.

2. Program.cs'den adı TestConsole.cs gibi daha anlamlı bir adla düzenleyin.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] TestConsole.cs dosyasındaki sınıf bildirimini otomatik olarak yeni dosya adıyla eş olacak şekilde değiştirir.

3. TestConsole.cs içinde yönergelerine aşağıdaki `using` kodu ekleyin:

   ```csharp
   using MyFirstVisualizer;
   ```

4. yönteminde `Main` aşağıdaki kodu ekleyin:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Artık ilk görselleştiricinizi test etmeye hazır oluruz.

### <a name="to-test-the-visualizer"></a>Görselleştiriciyi test etmek için

1. Bu **Çözüm Gezgini,** **MyTestConsole'a** sağ tıklayın ve kısayol menüsünde **Başlangıç** Project Olarak Ayarla'yı seçin.

2. Hata **Ayıkla menüsünde** Başlat'ı **seçin.**

    Konsol uygulaması başlatılır ve Görselleştirici görünür ve "Hello, World" dizesini görüntüler.

   Tebrikler. İlk görselleştiricinizi yeni derler ve test ederiz!

   Görselleştiricinizi yalnızca test donanımından aramak yerine içinde kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemeniz gerekir. Daha fazla bilgi için, [bkz. How to: Install a Visualizer](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Hata ayıklama tarafı veri nesnesi ekleme

Bu bölümde, veri nesnesinden `System.String` özel bir veri nesnesine geçebilirsiniz.  

1. Bu Çözüm Gezgini, çözüme sağ tıklayın, Ekle'yi **seçin** ve ardından Yeni **Project.** Dil açılan listesinde **C# seçin.** Arama kutusuna sınıf kitaplığı **yazın** ve ardından sınıf kitaplığı **(.NET Framework)** veya Sınıf Kitaplığı'.NET Standard. 

   >[!NOTE]
   >Bir test konsolu .NET Framework kullanıyorsanız, bir sınıf kitaplığı projesi .NET Framework emin olun.

1. **İleri**’ye tıklayın. Görüntülenen iletişim kutusuna adını yazın ve `MyDataObject` Oluştur'a **tıklayın.**

1. (.NET Standard sınıf kitaplığı) Bu Çözüm Gezgini projeye sağ tıklayın ve Dosyada **Düzenle'Project seçin.** değerini `<TargetFramework>` olarak `netstandard2.0` değiştirme.

   ```xml
   <TargetFramework>netstandard2.0</TargetFramework>
   ```

1. Ad `MyDataObject` alanının içinde varsayılan kodu aşağıdaki kodla değiştirin.

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   Bu örnekte olduğu gibi salt okunur bir görselleştirici için [VisualizerObjectSource yöntemlerinin uygulanması gerekmez.](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource)

   Ardından MyFirstVisualizer projesini yeni veri nesnesini kullanmak üzere güncelleştirin.

1. MyFirstVisualizer Çözüm Gezgini altında BulunanLar düğümüne sağ tıklayın ve **Başvuru** Ekle'yi **seçin.**

1. Projeler **altında** **MyDataObject projesini** seçin.

1. DebuggerSide.cs öznitelik kodunda Hedef değerini olarak değiştirerek `System.String` `MyDataObject.CustomDataObject` güncelleştirin.

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. MyFirstVisualizer projesinde yönteminin kodunu `Show` aşağıdaki kodla değiştirin.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Yukarıdaki kod, Form başlığında göstermek için veri nesnesinin bir özelliğini kullanır.

   Ardından, özel veri nesnesini kullanmak için konsol uygulamasını güncelleştirin.

1. MyTestConsole Çözüm Gezgini altında, Başvurular veya Bağımlılıklar  düğümüne sağ **tıklayın** ve için bir proje başvurusu `MyDataObject` ekleyin.

1. Program.cs'de yönteminde yer `Main` alan kodu aşağıdaki kodla değiştirin.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (.NET konsol uygulaması) test sıyrı `TestShowVisualizer` desteklenmeyen bir try-catch deyiminde çağrısının içine.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   Konsol uygulamasının görselleştiriciye bir çalışma zamanı başvurusuna ihtiyacı vardır. Açıklama yapmak yerine önceki kodu koruyarak başvuruya devam ettirebilirsiniz.

1. Bir .NET Framework konsolu uygulaması için, test uzmunu çalıştırabilirsiniz **(F5** tuşuna basın) veya Nasıl yapılır: Görselleştirici [yükleme yönergelerini takip edin.](../debugger/how-to-install-a-visualizer.md)

   Uygulamayı test sıyrısı kullanarak çalıştırdısanız, uygulama Windows gösterir.

1. Bir .NET konsol uygulaması için, ve 'yi Nasıl Musunuz? Görselleştirici yükleme `MyFirstVisualizer.dll` `MyDataObject.dll` konusunda açıklanan [klasörlere kopyalayın.](../debugger/how-to-install-a-visualizer.md)

1. Görselleştiriciyi yükledikten sonra bir kesme noktası ayarlayın, konsol uygulamasını çalıştırın ve üzerine `customDataObject` gelin. Her şey doğru şekilde ayarlanmışsa büyüteç simgesini ![VisualizerIcon olarak görüyor olun.](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Görselleştirici büyüteç simgesi.":::

   **Büyüteçten MyFirstVisualizer'ı** seçtiğiniz zaman başlıkta veri nesnesi metninin yer alan Form' olduğunu görüyorsunuz.

   ![Windows Formunu gösteren görselleştirici](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Görselleştirici öğe şablonunu kullanarak görselleştirici oluşturma

Şimdiye kadar bu kılavuzda görselleştiriciyi el ile nasıl oluşturabilirsiniz? Bu bir öğrenme alıştırması olarak yapıldı. Artık basit bir görselleştiricinin nasıl çalıştığını biliyorsunuz. Görselleştirici öğesi şablonunu kullanarak bir görselleştirici oluşturmanın daha kolay bir yolu vardır.

İlk olarak, yeni bir sınıf kitaplığı projesi oluşturmanız gerekir.

### <a name="to-create-a-new-class-library"></a>Yeni bir sınıf kitaplığı oluşturmak için

1. Dosya menüsünde **Yeni** **dosya'> Project.**

2. Yeni Project iletişim **kutusundaki** **Visual C#** altında, Yeni'yi **.NET Framework.**

3. Orta bölmede Sınıf **Kitaplığı'ı seçin.**

4. Ad **kutusuna** sınıf kitaplığı için MySecondVisualizer gibi uygun bir ad yazın.

5. **Tamam**'a tıklayın.

   Şimdi görselleştirici öğesini ekebilirsiniz:

### <a name="to-add-a-visualizer-item"></a>Görselleştirici öğesi eklemek için

1. Bu **Çözüm Gezgini,** MySecondVisualizer'a sağ tıklayın.

2. Kısayol menüsünde Ekle'yi seçin **ve** ardından Yeni **Öğe'ye tıklayın.**

3. Yeni Öğe **Ekle iletişim kutusundaki** Visual C# Öğeleri altında Hata **Ayıklayıcı** **Görselleştiricisi'ne tıklayın.**

4. Ad **kutusuna** SecondVisualizer.cs gibi uygun bir ad yazın.

5. **Ekle**'ye tıklayın.

   Tek gereken bu. SecondVisualizer.cs dosyasına bakın ve şablon tarafından sizin için eklenen kodu görüntüleniyor. Devam edin ve kodla denemeler yapalım. Temel bilgileri artık biliyorsunuz, artık kendi karmaşık ve kullanışlı görselleştiricilerinizi oluşturma yolundadır.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Görselleştirici Mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl kurulur: Görselleştirici Yükleme](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
