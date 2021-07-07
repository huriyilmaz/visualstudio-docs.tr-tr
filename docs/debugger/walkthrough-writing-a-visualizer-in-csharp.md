---
title: C# ile görselleştirici | Microsoft Docs
description: C# ile basit bir görselleştirici oluşturmak için izlenecek yolu izleyin. Görselleştirici öğe şablonunu kullanarak ve kullanmadan gereken adımları gösterir.
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
ms.openlocfilehash: 47c7fa8eaa5a735f05b338101a1aefe0601e9915
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298291"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Kılavuz: C'de Görselleştirici Yazma\#

Bu kılavuzda, C# kullanarak basit bir görselleştiricinin nasıl yaz olduğu açıklanır. Bu kılavuzda oluşturacak görselleştirici, form formlarını kullanarak bir dizenin Windows görüntüler. Bu basit dize görselleştiricisi özellikle kendi içinde kullanışlı değildir, ancak diğer veri türleri için daha kullanışlı görselleştiriciler oluşturmak için izlemeniz gereken temel adımları gösterir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için Araçlar menüsüne gidip İçeri **ve** Dışarı Aktar'ı **Ayarlar.** Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

Görselleştirici kodu, hata ayıklayıcı tarafından okunacak bir DLL'ye yerleştirilemedi. Bu nedenle, ilk adım DLL için bir Sınıf Kitaplığı projesi oluşturmaktır.

## <a name="create-a-visualizer-manually"></a>Görselleştiriciyi el ile oluşturma

Görselleştirici oluşturmak için aşağıdaki görevleri izleyin.

### <a name="to-create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturmak için

* Yeni bir sınıf kitaplığı projesi oluşturun.

    ::: moniker range=">=vs-2019"
    Dosya **Yeni**  >  **Dosya'Project.**  >   Dil açılan menüsünde **C# seçin.** Arama kutusuna sınıf kitaplığı yazın **ve ardından** Sınıf Kitaplığı **(sınıf kitaplığı) .NET Framework seçin.** **İleri**’ye tıklayın. Görüntülenen iletişim kutusuna adını yazın ve `MyFirstVisualizer` Oluştur'a **tıklayın.**

    Görselleştirici projesi için .NET değil, .NET Framework sınıf kitaplığını seçin. Görselleştiricinin farklı bir .NET Framework, ancak çağıran uygulama .NET Core olabilir.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında, .NET Framework seçeneğini ve **orta** bölmede Sınıf Kitaplığı **(.NET Framework) seçeneğini seçin.**

    sınıf kitaplığı için gibi uygun bir ad yazın ve ardından `MyFirstVisualizer` Oluştur veya **Tamam'a** **tıklayın.**
    ::: moniker-end

   Sınıf kitaplığını oluşturduktan sonra, burada tanımlanan sınıfları Microsoft.VisualStudio.DebuggerVisualizers.DLL için bir başvuru eklemeniz gerekir. Ancak başvuruyu eklemeden önce bazı sınıfları anlamlı adlara sahip olacak şekilde yeniden adlandırmanız gerekir.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.cs'yi yeniden adlandırmak ve Microsoft.VisualStudio.DebuggerVisualizers eklemek için

1. Bu **Çözüm Gezgini** Class1.cs'ye sağ tıklayın ve kısayol menüsünde **Yeniden** Adlandır'ı seçin.

2. Class1.cs olan adı DebuggerSide.cs gibi anlamlı bir adla değiştirebilirsiniz.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DebuggerSide.cs dosyasındaki sınıf bildirimini yeni dosya adıyla eş eşleşmesi için otomatik olarak değiştirir.

3. Bu **Çözüm Gezgini,** Başvurular'a **sağ tıklayın** ve kısayol menüsünde **Başvuru** Ekle'yi seçin.

4. Başvuru **Ekle iletişim kutusundaki** Gözat sekmesinde **Gözat'ı** **seçin** ve Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    DLL'yi, Visual Studio'nin yükleme dizininin *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* alt dizininde bulabilirsiniz.

5. **Tamam**'a tıklayın.

6. DebuggerSide.cs dosyasında, yönergelerine `using` aşağıdakini ekleyin:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Artık hata ayıklayıcı tarafı kodunu oluşturmak için hazır oluruz. Bu, görselleştirmek istediğiniz bilgileri görüntülemek için hata ayıklayıcısı içinde çalışan koddur. İlk olarak, nesnesinin bildirimini `DebuggerSide` temel sınıftan devralınarak değiştirebilirsiniz. `DialogDebuggerVisualizer`

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer'dan devralmak için

1. DebuggerSide.cs dosyasında aşağıdaki kod satırına gidin:

   ```csharp
   public class DebuggerSide
   ```

2. Kodu şu şekilde değiştirebilirsiniz:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` geçersiz kılmamız gereken bir soyut yöntem ( `Show` ) vardır.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show yöntemini geçersiz kılmak için

- içinde `public class DebuggerSide` aşağıdaki yöntemi **ekleyin:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  yöntemi, görselleştirici iletişim kutusunu veya diğer kullanıcı arabirimini oluşturan ve hata ayıklayıcıdan görselleştiriciye geçirilen bilgileri `Show` görüntüleyen kodu içerir. İletişim kutusunu oluşturan ve bilgileri görüntüleyen kodu eklemeniz gerekir. Bu kılavuzda, bunu Formlar ileti Windows kullanarak yapacaksınız. İlk `using` olarak, System.Windows için bir başvuru ve yönerge eklemeniz gerekir. Forms.

### <a name="to-add-systemwindowsforms"></a>Sistem eklemek için. Windows. Forms

1. Bu **Çözüm Gezgini,** Başvurular'a **sağ tıklayın** ve kısayol menüsünde **Başvuru** Ekle'yi seçin.

2. Başvuru **Ekle iletişim kutusundaki** Gözat sekmesinde **Gözat'ı** **seçin** ve ilgili System.Windows.Forms.DLL.

    *DLL'yi C:\Windows\Microsoft.NET\Framework\v4.0.30319 konumunda bulabilirsiniz.*

3. **Tamam**'a tıklayın.

4. DebuggerSide.cs dosyasında, yönergelerine `using` aşağıdakini ekleyin:

   ```csharp
   using System.Windows.Forms;
   ```

   Şimdi görselleştiricinizin kullanıcı arabirimini oluşturmak ve göstermek için kod eksersiniz. Bu ilk görselleştiriciniz olduğundan, kullanıcı arabirimini basit tutacak ve bir Message Box kullanmayacak.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Görselleştirici Çıktısını bir iletişim kutusunda göstermek için

1. `Show` yönteminde aşağıdaki kod satırını ekleyin:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Bu örnek kod, hata işlemeyi içermez. Hata işlemeyi gerçek bir görselleştiriciye veya başka bir tür uygulamaya dahil etmek gerekir.

2. Build **(Derleme)** menüsünde Build **MyFirstVisualizer (DerlememFirstVisualizer) öğesini seçin.** Projenin başarıyla derlemesi gerekir. Devam etmeden önce derleme hatalarını düzeltin.

   Bu, hata ayıklayıcı yan kodunun sonudur. Ancak bir adım daha vardır; hata ayıklayıcısı tarafına hangi sınıf koleksiyonunun görselleştiriciyi olduğunu söyleyen özniteliği.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Hata ayıklama tarafı kodu için görselleştirilen türü eklemek için

Hata ayıklayıcı tarafı kodunda özniteliğini kullanarak hata ayıklayıcı için görselleştirilen türü (nesne kaynağı) <xref:System.Diagnostics.DebuggerVisualizerAttribute> belirtirsiniz. özelliği, `Target` görselleştirilen türü ayarlar.

1. Aşağıdaki öznitelik kodunu DebuggerSide.cs'ye yönergelerinin ardından ancak `using` öncesinde `namespace MyFirstVisualizer` ekleyin:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Build **(Derleme)** menüsünde Build **MyFirstVisualizer (DerlememFirstVisualizer) öğesini seçin.** Projenin başarıyla derlemesi gerekir. Devam etmeden önce derleme hatalarını düzeltin.

   Bu noktada, ilk görselleştiriciniz tamamdır. Adımları doğru şekilde izlediyebilirsiniz, görselleştiriciyi derlemek ve içine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemek. Ancak, içine bir görselleştirici [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemeden önce doğru şekilde çalıştırıla olduğundan emin olmak için test edin. Şimdi görselleştiriciyi'ye yüklemeden çalıştırmak için bir test sıyrı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturacak.

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştiriciyi göstermek için bir Test Yöntemi eklemek için

1. sınıfına aşağıdaki yöntemi `public DebuggerSide` ekleyin:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. Build **(Derleme)** menüsünde Build **MyFirstVisualizer (DerlememFirstVisualizer) öğesini seçin.** Projenin başarıyla derlemesi gerekir. Devam etmeden önce derleme hatalarını düzeltin.

   Ardından görselleştirici DLL'nizi çağıracak yürütülebilir bir proje oluşturmanız gerekir. Kolaylık olması için konsol uygulaması projesi kullanın.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Çözüme bir konsol uygulaması projesi eklemek için

1. Bu Çözüm Gezgini, çözüme sağ tıklayın, Ekle'yi **seçin** ve ardından Yeni **Project.**

    ::: moniker range=">=vs-2019"

    Dosya **Yeni**  >  **Dosya'Project.**  >   Dil açılan menüsünde **C# seçin.** Arama kutusuna konsol uygulaması **yazın ve ardından**.NET için Konsol Uygulaması **(.NET Framework)** veya **Konsol** Uygulaması'nu seçin. **İleri**’ye tıklayın. Görüntülenen iletişim kutusuna adını yazın ve `MyTestConsole` Oluştur'a **tıklayın.**

    > [!NOTE]
    > Görselleştiriciyi test donanımı kullanarak kolayca test etmek için bir konsol .NET Framework oluşturun. Bunun yerine bir .NET konsol uygulaması oluşturabilirsiniz, ancak daha sonra açıklanan test yararlanıcısı henüz .NET için desteklenmiyor, bu nedenle test etmek için görselleştiriciyi yüklemeniz gerekir. Bu senaryo için, önce burada konsol uygulamasını oluşturun ve ardından Hata ayıklama tarafı veri [nesnesi ekleme konusunda açıklanan adımları izleyin.](#add-a-debuggee-side-data-object)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında Windows **Desktop'ı** seçin ve orta bölmede Konsol Uygulaması **(.NET Framework) seçeneğini kullanın.**

    sınıf kitaplığı için gibi uygun bir ad yazın ve ardından `MyTestConsole` Tamam'a **tıklayın.**
    ::: moniker-end

   Şimdi MyTestConsole'ın MyFirstVisualizer'ı çağırana kadar gerekli başvuruları eklemeniz gerekir.

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole'a gerekli başvuruları eklemek için

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

1. **dosya**  >  **yeni**  >  **Project** seçin. Dil açılır penceresinde **C#**' ı seçin. arama kutusuna **sınıf kitaplığı** yazın ve ardından .NET Standard için sınıf **kitaplığı (.NET Framework)** veya **sınıf kitaplığı** ' nı seçin.

   >[!NOTE]
   >bir .NET Framework test konsolu uygulaması kullanıyorsanız, bir .NET Framework sınıf kitaplığı projesi oluşturduğunuzdan emin olun.

1. **İleri**’ye tıklayın. Görüntülenen iletişim kutusunda adı yazın `MyDataObject` ve ardından **Oluştur**' a tıklayın.

1. (Yalnızca .NET Standard sınıf kitaplığı) Çözüm Gezgini, projeye sağ tıklayın ve **Project dosyayı düzenle**' yi seçin. `<TargetFramework>`Değerini olarak değiştirin `netstandard2.0` .

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

   Hata ayıklayıcının Görselleştirici için bir başvuruya ihtiyacı vardır. Başvuruyu tutmanın bir yolu, Yukarıdaki kodun yerinde tutulması.

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
