---
title: Görselleştirici yazma C# | Microsoft Docs
ms.custom: seodec18
ms.date: 04/12/2019
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a46967d5f46c4f495a07d80e5f73cfc9f9d60c1a
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542639"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>İzlenecek yol: C\# bir Görselleştirici Yazma
Bu kılavuz, C# kullanarak basit Görselleştirici yazma işlemi gösterilmektedir. Bu izlenecek yolda oluşturacağınız Görselleştirici, bir Windows forms ileti kutusunu kullanarak bir dizenin içeriklerini görüntüler. Bu basit dize Görselleştirici kendisi özellikle kullanışlı değildir, ancak diğer veri türleri için daha faydalı görselleştiriciler oluşturmak için izlemeniz gereken temel adımlarda gösterilir.

> [!NOTE]
> İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için Git **Araçları** menüsünü seçip **içeri ve dışarı aktarma ayarları**. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

Görselleştirici kod bir DLL'de hata ayıklayıcı tarafından okunacak yerleştirilmelidir. Bu nedenle, ilk adım bir sınıf kitaplığı projesi DLL için oluşturmaktır.

## <a name="create-a-visualizer-manually"></a>Görselleştirici el ile oluşturma

Görselleştirici oluşturmak için aşağıdaki görevleri izleyin.

### <a name="to-create-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturmak için

1. Yeni bir sınıf kitaplığı projesi oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **sınıf kitaplığı**yazın, **Şablonlar**' ı seçin ve ardından **Yeni bir sınıf kitaplığı oluştur (.NET Framework)** seçeneğini belirleyin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** altında **.NET Framework**' yi seçin ve ardından Ortadaki bölmede Sınıf Kitaplığı ' nı **(.NET Framework)** seçin.
    ::: moniker-end

2. Sınıf kitaplığı için `MyFirstVisualizer`gibi uygun bir ad yazın ve ardından **Oluştur** veya **Tamam**' a tıklayın.

   Sınıf kitaplığı oluşturduktan sonra tanımlanan sınıflara var. kullanabilmesi için Microsoft.VisualStudio.DebuggerVisualizers.DLL bir başvuru eklemeniz gerekir. Ancak, başvuru eklemeden önce böylece sahip oldukları anlamlı adlar bazı sınıfları yeniden adlandırmanız gerekir.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.cs yeniden adlandırıp Microsoft.VisualStudio.DebuggerVisualizers Ekle

1. İçinde **Çözüm Gezgini**Class1.cs sağ tıklatın ve seçin **Yeniden Adlandır** kısayol menüsünde.

2. Ad Class1.cs DebuggerSide.cs gibi anlamlı değiştirin.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sınıf bildirimi içinde DebuggerSide.cs yeni dosya adı ile eşleşecek şekilde otomatik olarak değiştirir.

3. İçinde **Çözüm Gezgini**, sağ **başvuruları** ve **Başvuru Ekle** kısayol menüsünde.

4. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, **Araştır** ' ı seçin ve Microsoft. VisualStudio. debuggervisualiciler. dll dosyasını bulun.

    Visual Studio 'nun yükleme dizinindeki *\<Visual Studio yükleme dizini > \Common7\IDE\PublicAssemblies* alt dizini ' nde dll 'yi bulabilirsiniz.

5. **Tamam**'ı tıklatın.

6. DebuggerSide.cs ' de, aşağıdakileri `using` yönergelerine ekleyin:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Hata ayıklayıcı tarafından çalışan kod oluşturmaya hazırsınız. Görselleştirmek istediğiniz bilgileri görüntülemek için hata ayıklayıcısı içinde çalıştırılan kod budur. İlk olarak, bildirimini değiştirmek zorunda `DebuggerSide` taban sınıfından devralan şekilde nesne `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer devralacak şekilde

1. Aşağıdaki kod satırını DebuggerSide.cs içinde gidin:

   ```csharp
   public class DebuggerSide
   ```

2. Kodla değiştirin:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` soyut bir yöntemi vardır (`Show`), geçersiz kılmanız gerekir.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show yöntemi geçersiz kılmak için

- İçinde `public class DebuggerSide`, aşağıdaki **yöntemi:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show` Yöntemi gerçekten görselleştiricisi iletişim kutusu veya diğer kullanıcı arabirimi oluşturur ve hata ayıklayıcı'dan görselleştiriciye geçirildi bilgilerini görüntüler kodunu içerir. İletişim kutusu oluşturur ve bilgi görüntüleyen bir kod eklemeniz gerekir. Bu kılavuzda, bir Windows forms ileti kutusunu kullanarak bunu. İlk olarak, System. Windows. Forms için bir başvuru ve `using` yönergesi eklemeniz gerekir.

### <a name="to-add-systemwindowsforms"></a>System.Windows.Forms eklemek için

1. İçinde **Çözüm Gezgini**, sağ **başvuruları** ve **Başvuru Ekle** kısayol menüsünde.

2. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, **Araştır**' ı seçin ve System. Windows. Forms. dll dosyasını bulun.

    DLL 'yi *C:\Windows\Microsoft.NET\Framework\v4.0.30319*içinde bulabilirsiniz.

3. **Tamam**'ı tıklatın.

4. DebuggerSide.cs ' de, aşağıdakileri `using` yönergelerine ekleyin:

   ```csharp
   using System.Windows.Forms;
   ```

   Şimdi, oluşturma ve kullanıcı arabirimi için Görselleştirici göstermek için bazı kod ekleyeceksiniz. Bu, ilk Görselleştirici olduğundan, biz kullanıcı arabirimi basit tutmak ve bir ileti kutusunu kullanın.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>İletişim kutusunda görselleştiricisi çıkışının görüntülenmesi için

1. İçinde `Show` yöntemini aşağıdaki kod satırını ekleyin:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Bu kod örneği, hata işleme içermez. Hata gerçek Görselleştirici veya başka tür bir uygulama işleme içermesi gerekir.

2. Üzerinde **derleme** menüsünde seçin **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.

   Hata ayıklayıcı çalışan kod sonu olmasıdır. Ancak bir adım daha yoktur; hata ayıklanan yan hangi sınıfları koleksiyonu belirten özniteliği Görselleştirici oluşur.

### <a name="to-add-the-debuggee-side-code"></a>Hata ayıklanan tarafın kod eklemek için

1. `using` yönergelerinden sonra, `namespace MyFirstVisualizer`önce aşağıdaki öznitelik kodunu ekleyin:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Üzerinde **derleme** menüsünde seçin **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.

   Bu noktada, ilk Görselleştirici tamamlandı. Doğru adımları izlediyseniz, görselleştiricisi oluşturun ve içine yüklemek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Görselleştirici içine yüklemeden önce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ancak doğru şekilde çalıştığından emin olmak için sınamalısınız. Görselleştirici içine yüklemeden çalıştırmak için test bandı şimdi oluşturacak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştirici göstermek için bir Test yöntemi eklemek için

1. Sınıfına aşağıdaki yöntemi ekleyin `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. Üzerinde **derleme** menüsünde seçin **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.

   Ardından, DLL, Görselleştirici çağırmak için bir yürütülebilir proje oluşturmanız gerekir. Kolaylık olması için bir konsol uygulama projesini kullanacağız.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Bir konsol uygulaması projesi çözüme eklemek için

1. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **Yeni proje**' ye tıklayın.

    ::: moniker range=">=vs-2019"
    Arama kutusunda **konsol uygulaması**yazın, **Şablonlar**' ı seçin ve ardından **Yeni bir konsol uygulaması oluştur (.NET Framework)** öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin.
    ::: moniker-end

2. Sınıf kitaplığı için `MyTestConsole`gibi uygun bir ad yazın ve ardından **Oluştur** veya **Tamam**' a tıklayın.

   Artık gerekli MyTestConsole MyFirstVisualizer çağırabilmek başvuran eklemeniz gerekir.

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole gerekli başvuruları eklemek için

1. İçinde **Çözüm Gezgini**, sağ **MyTestConsole** ve **Başvuru Ekle** kısayol menüsünde.

2. **Başvuru Ekle** iletişim kutusunda, sekme sekmesine, Microsoft. VisualStudio. Debuggervisualiciler. dll **' yi seçin** .

3. **Tamam**'ı tıklatın.

4. Sağ **MyTestConsole** ve **Başvuru Ekle** yeniden.

5. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **projeleri** sekmesine ve ardından MyFirstVisualizer tıklayın.

6. **Tamam**'ı tıklatın.

   Şimdi, test bandı tamamlamak için kod ekleyeceksiniz.

### <a name="to-add-code-to-mytestconsole"></a>Kod için MyTestConsole eklemek için

1. İçinde **Çözüm Gezgini**, Program.cs sağ tıklatın ve seçin **Yeniden Adlandır** kısayol menüsünde.

2. Program.cs adından TestConsole.cs gibi daha anlamlı olacak şekilde düzenleyin.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], TestConsole.cs içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirir.

3. TestConsole.cs ' de, aşağıdaki kodu `using` yönergelerine ekleyin:

   ```csharp
   using MyFirstVisualizer;
   ```

4. Yönteminde `Main`, aşağıdaki kodu ekleyin:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Şimdi, ilk görselleştiriciyi sınamak hazır olursunuz.

### <a name="to-test-the-visualizer"></a>Görselleştiriciyi sınamak için

1. İçinde **Çözüm Gezgini**, sağ **MyTestConsole** ve **başlangıç projesi olarak ayarla** kısayol menüsünde.

2. Üzerinde **hata ayıklama** menüsünde seçin **Başlat**.

    Konsol uygulaması başlatır ve Görselleştirici görünür ve "Hello, World" dizesini görüntüler

   Tebrikler. Yalnızca yerleşik ve test, ilk Görselleştirici.

   Görselleştiricisindeki kullanmak istiyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemek zorunda yalnızca, test bandı çağırmak yerine,. Daha fazla bilgi için [nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Görselleştirici öğe şablonu kullanarak Görselleştirici oluşturma

Şu ana kadar bu izlenecek yolda Görselleştirici el ile oluşturmak nasıl göstermiştir. Bu öğrenme alıştırma olarak yapıldı. Artık basit Görselleştirici nasıl çalıştığını öğrendiğinize göre oluşturmak için daha kolay bir yolu yoktur: Görselleştirici öğe şablonu kullanarak.

İlk olarak, yeni bir sınıf kitaplığı projesi oluşturmanız gerekir.

### <a name="to-create-a-new-class-library"></a>Yeni bir sınıf kitaplığı oluşturmak için

1. Üzerinde **dosya** menüsünde seçin **yeni > Proje**.

2. **Yeni proje** iletişim kutusunda, **görsel C#** altında **.NET Framework**' yi seçin.

3. Orta bölmede seçin **sınıf kitaplığı**.

4. İçinde **adı** MySecondVisualizer gibi bir sınıf kitaplığı için uygun bir ad yazın.

5. **Tamam**'ı tıklatın.

   Şimdi, kendisine görselleştiricisi öğe ekleyebilirsiniz:

### <a name="to-add-a-visualizer-item"></a>Görselleştirici öğe eklemek için

1. İçinde **Çözüm Gezgini**, MySecondVisualizer sağ tıklayın.

2. Kısayol menüsünde **Ekle** ve ardından **yeni öğe**.

3. İçinde **Yeni Öğe Ekle** iletişim kutusunun **Visual C# öğeleri**seçin **hata ayıklama görselleştiricisi**.

4. İçinde **adı** SecondVisualizer.cs gibi uygun bir ad yazın.

5. **Ekle**'yi tıklatın.

   Tüm İşte bu kadar kolay olmasıdır. Dosyaya SecondVisualizer.cs bakması ve şablon sizin için eklenen kodu görüntüleyin. Devam edin ve kodla denemeler yapın. Temel bilgileri artık bildiğinize göre olsun daha karmaşık ve kullanışlı görselleştiriciler kendi oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [Görselleştirici Mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl Yapılır: Görselleştirici Yükleme](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
