---
title: C# dilinde bir Görselleştirici Yazma | Microsoft Docs
description: C# dilinde basit Görselleştirici oluşturmak için bir yönergeyi izleyin. Görselleştirici öğe şablonu kullanılmadan, ve ile gereken adımları gösterir.
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
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 75a7032185a7ed9db6fd2f11b28c597ab6c9dfbe
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968169"
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

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole 'a gerekli başvuruları eklemek için

1. **Çözüm Gezgini**' de, **MyTestConsole** ' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle** ' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda, sekme sekmesine **gidip** Microsoft.VisualStudio.DebuggerVisualizers.DLL öğesini seçin.

3. **Tamam**'a tıklayın.

4. **MyTestConsole** ' a sağ tıklayın ve **Başvuru Ekle** ' yi seçin.

5. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesine tıklayın ve ardından myfirstgörselleştiricisi ' e tıklayın.

6. **Tamam**'a tıklayın.

   Şimdi, test bandı sona ermesini sağlayacak kodu ekleyeceksiniz.

### <a name="to-add-code-to-mytestconsole"></a>MyTestConsole 'a kod eklemek için

1. **Çözüm Gezgini**, program. cs öğesine sağ tıklayın ve kısayol menüsünde **Yeniden Adlandır** ' ı seçin.

2. Program. cs içindeki adı TestConsole. cs gibi daha anlamlı bir değere düzenleyin.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] TestConsole. cs içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirir.

3. TestConsole. cs dosyasında aşağıdaki kodu `using` yönergelere ekleyin:

   ```csharp
   using MyFirstVisualizer;
   ```

4. Yönteminde `Main` aşağıdaki kodu ekleyin:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Şimdi ilk Görselleştiriciyi test etmeye hazırsınız.

### <a name="to-test-the-visualizer"></a>Görselleştiriciyi test etmek için

1. **Çözüm Gezgini**' de, **mytestconsole** ' a sağ tıklayın ve kısayol menüsünde **başlangıç Project olarak ayarla** ' yı seçin.

2. **Hata Ayıkla** menüsünde **Başlat**' ı seçin.

    Konsol uygulaması başlar ve Görselleştirici görüntülenir ve "Hello, World" dizesini görüntüler.

   Tebrikler. İlk görselleştirmeniz oluşturmuş ve test edilmiştir!

   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Yalnızca test bandı aracılığıyla çağırmak yerine Görselleştiriciyi kullanmak istiyorsanız, onu yüklemelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Hata ayıklanan tarafı veri nesnesi Ekle

Bu bölümde, `System.String` veri nesnesinden özel bir veri nesnesine geçiş yapabilirsiniz.  

1. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **yeni Project**' ye tıklayın. Dil açılır penceresinde **C#**' ı seçin. arama kutusuna **sınıf kitaplığı** yazın ve ardından .NET Standard için sınıf **kitaplığı (.NET Framework)** veya **sınıf kitaplığı** ' nı seçin.

   >[!NOTE]
   >bir .NET Framework test konsolu uygulaması kullanıyorsanız, bir .NET Framework sınıf kitaplığı projesi oluşturduğunuzdan emin olun.

1. **İleri**’ye tıklayın. Görüntülenen iletişim kutusunda adı yazın `MyDataObject` ve ardından **Oluştur**' a tıklayın.

1. (Yalnızca .NET Standard sınıf kitaplığı) Çözüm Gezgini, projeye sağ tıklayın ve **Project dosyayı düzenle**' yi seçin. `<TargetFramework>`Değerini olarak değiştirin `netstandard2.0` .

   ```xml
   <TargetFramework>netstandard2.0</TargetFramework>
   ```

1. `MyDataObject`Ad alanı içinde, varsayılan kodu aşağıdaki kodla değiştirin.

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

   Bu örnekte olduğu gibi, salt okunurdur bir Görselleştirici için, [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource)yöntemlerinin uygulanması gerekli değildir.

   Sonra, Myfirstgörselleştiricisi projesini yeni veri nesnesini kullanacak şekilde güncelleştirin.

1. Myfirstgörselleştiricisi projesi altındaki Çözüm Gezgini, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

1. **Projeler** altında, **myDataObject** projesini seçin.

1. DebuggerSide. cs öznitelik kodunda, hedef değeri güncelleştirin, `System.String` olarak değiştirme `MyDataObject.CustomDataObject` .

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. Myfirstgörselleştiricisi projesinde, yöntemi için kodu `Show` aşağıdaki kodla değiştirin.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Önceki kod, form başlığında göstermek için veri nesnesinin bir özelliğini kullanır.

   Ardından, konsol uygulamasını özel veri nesnesini kullanacak şekilde güncelleştirin.

1. MyTestConsole projesi altında Çözüm Gezgini, **Başvurular** veya **Bağımlılıklar** düğümüne sağ tıklayın ve öğesine bir proje başvurusu ekleyin `MyDataObject` .

1. Program. cs ' de, `Main` yöntemindeki kodu aşağıdaki kodla değiştirin.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (.NET konsol uygulaması) `TestShowVisualizer` Test bandı desteklenmediğinden, çağrıyı bir try-catch ifadesinde içine alın.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   Konsol uygulamasının Görselleştirici için bir çalışma zamanı başvurusu olması gerekir. Önceki kodu, açıklama eklemek yerine tutarak başvuruyu koruyabilirsiniz.

1. .NET Framework konsol uygulaması için, test bandı çalıştırabilirsiniz ( **F5** tuşuna basın) veya [nasıl yapılır: görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)konusundaki yönergeleri izleyebilirsiniz.

   uygulamayı test bandı kullanarak çalıştırırsanız, uygulama Windows formunu gösterir.

1. Bir .NET konsol uygulaması için ve öğesini, `MyFirstVisualizer.dll` `MyDataObject.dll` [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)bölümünde açıklanan klasörlere kopyalayın.

1. Görselleştiriciyi yükledikten sonra bir kesme noktası ayarlayın, konsol uygulamasını çalıştırın ve üzerine gelin `customDataObject` . Her şey doğru şekilde ayarlandıysa, büyüteç simgesini ![Visualizersimgesini](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")görmeniz gerekir.

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Görselleştirici Büyüteç simgesi.":::

   Büyüteç Camı ' ndan **Myfirstgörselleştirici** ' ı seçtiğinizde, başlığında veri nesne metniyle birlikte görüntülenir.

   ![bir Windows formu gösteren görselleştirici](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Görselleştiricisi öğesi şablonunu kullanarak Görselleştirici oluşturma

Şimdiye kadar, Bu anlatım el ile Görselleştirici oluşturmayı göstermiştir. Bu bir öğrenme alıştırması olarak gerçekleştirildi. Basit bir Görselleştirici nasıl çalıştığını bildiğinize göre, bir tane oluşturmak için daha kolay bir yol vardır: görselleştiricisi öğesi şablonu.

İlk olarak, yeni bir sınıf kitaplığı projesi oluşturmanız gerekir.

### <a name="to-create-a-new-class-library"></a>Yeni bir sınıf kitaplığı oluşturmak için

1. **Dosya** menüsünde **Yeni > Project**' ni seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** altında **.NET Framework**' ı seçin.

3. Orta bölmede **sınıf kitaplığı**' nı seçin.

4. **Ad** kutusuna, sınıf kitaplığı Için MySecondVisualizer gibi uygun bir ad yazın.

5. **Tamam**'a tıklayın.

   Şimdi, buna bir Görselleştirici öğesi ekleyebilirsiniz:

### <a name="to-add-a-visualizer-item"></a>Bir Görselleştirici öğesi eklemek için

1. **Çözüm Gezgini**, Mysecondgörselleştirici öğesine sağ tıklayın.

2. Kısayol menüsünde **Ekle** ' yi ve ardından **Yeni öğe**' yi seçin.

3. **Yeni öğe Ekle** iletişim kutusunda, **Visual C# öğeleri** altında, **hata ayıklayıcı görselleştiricisi**' ı seçin.

4. **Ad** kutusuna, SecondVisualizer. cs gibi uygun bir ad yazın.

5. **Ekle**'ye tıklayın.

   Bu, hepsi bu kadar. SecondVisualizer. cs dosyasına bakın ve şablonun sizin için eklediği kodu görüntüleyin. Devam edin ve kodu deneyin. Temel bilgileri öğrenmiş olduğunuza göre, size ait daha karmaşık ve yararlı Görselleştiriciler oluşturma yönteminiz vardır.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Görselleştiricisi mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
