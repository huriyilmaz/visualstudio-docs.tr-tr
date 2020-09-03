---
title: 'İzlenecek yol: C# dilinde Görselleştirici Yazma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b95ac29f3084bf8899249039ffbaa7da8c2294f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67890463"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>İzlenecek yol: C 'de Görselleştirici Yazma\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, C# kullanılarak basit Görselleştirici nasıl yazılacağını gösterir. Bu kılavuzda oluşturacağınız Görselleştirici bir Windows Forms ileti kutusu kullanarak bir dizenin içeriğini görüntüler. Bu basit dize görselleştiricisi, özellikle de yararlı değildir, ancak diğer veri türleri için daha kullanışlı Görselleştiriciler oluşturmak üzere izlemeniz gereken temel adımları gösterir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsüne gidin ve **ayarları Içeri ve dışarı aktar '** ı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

Görselleştiricisi kodu, hata ayıklayıcısı tarafından okunacak bir DLL 'ye yerleştirilmelidir. Bu nedenle, ilk adım DLL için bir sınıf kitaplığı projesi oluşturmaktır.

#### <a name="to-create-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturmak için

1. **Dosya** menüsünde **Yeni** ' yi seçin ve ardından **Yeni proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Proje türü**' nün altında, **Visual C#**' yi seçin.

3. **Şablonlar** kutusunda **sınıf kitaplığı**' nı seçin.

4. **Ad** kutusuna, sınıf kitaplığı Için Myfirstgörselleştirici gibi uygun bir ad yazın.

5. **Tamam**’a tıklayın.

   Sınıf kitaplığını oluşturduktan sonra, burada tanımlanan sınıfları kullanabilmeniz için Microsoft.VisualStudio.DebuggerVisualizers.DLL bir başvuru eklemeniz gerekir. Ancak başvuruyu eklemeden önce, bazı sınıfları anlamlı adlara sahip olacak şekilde yeniden adlandırmanız gerekir.

#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.cs yeniden adlandırmak ve Microsoft. VisualStudio. Debuggervisualiciler eklemek için

1. **Çözüm Gezgini**' de, Class1.cs ' a sağ tıklayın ve kısayol menüsünde **Yeniden Adlandır** ' ı seçin.

2. Adı Class1.cs, DebuggerSide.cs gibi anlamlı bir şekilde değiştirin.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DebuggerSide.cs içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirir.

3. **Çözüm Gezgini**' de, **Başvurular** ' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle** ' yi seçin.

4. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesinde Microsoft.VisualStudio.DebuggerVisualizers.DLL ' yi seçin.

5. **Tamam**’a tıklayın.

6. DebuggerSide.cs ' de, aşağıdaki deyimi `using` deyimlere ekleyin:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Artık hata ayıklayıcı tarafı kodu oluşturmaya hazırsınız. Bu, görselleştirmek istediğiniz bilgileri göstermek için hata ayıklayıcı içinde çalışan koddur. İlk olarak, `DebuggerSide` nesne bildirimini temel sınıftan devrabir şekilde değiştirmeniz gerekir `DialogDebuggerVisualizer` .

#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer 'dan devralması için

1. DebuggerSide.cs ' de, aşağıdaki kod satırına gidin:

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
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show`Yöntemi aslında Görselleştirici iletişim kutusunu veya diğer Kullanıcı arabirimini oluşturan kodu içerir ve hata ayıklayıcıdan Görselleştirici 'e geçirilmiş bilgileri görüntüler. İletişim kutusunu oluşturan kodu eklemeniz ve bilgileri görüntüetmeniz gerekir. Bu kılavuzda, bunu bir Windows Forms ileti kutusu kullanarak yapacaksınız. İlk olarak, `using` System. Windows. Forms için bir başvuru ve ifade eklemeniz gerekir.

#### <a name="to-add-systemwindowsforms"></a>System. Windows. Forms eklemek için

1. **Çözüm Gezgini**' de, **Başvurular** ' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle** ' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesinde System.Windows.Forms.DLL ' yi seçin.

3. **Tamam**’a tıklayın.

4. DebuggerSide.cs ' de, aşağıdaki deyimi `using` deyimlere ekleyin:

   ```csharp
   using System.Windows.Forms;
   ```

   Artık Görseliniz için Kullanıcı arabirimi oluşturmak ve göstermek üzere bazı kodlar ekleyeceksiniz. Bu ilk görselleştiriciniz olduğundan, Kullanıcı arabirimini basit tutacağız ve bir Ileti kutusu kullanacaksınız.

#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Görselleştirici çıkışını bir iletişim kutusunda göstermek için

1. `Show` yönteminde aşağıdaki kod satırını ekleyin:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Bu örnek kod hata işleme içermez. Gerçek bir Görselleştirici veya başka bir tür uygulamaya hata işleme eklemeniz gerekir.

2. **Build** menüsünde **myfirstgörselleştirici Build**' i seçin. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Hata ayıklayıcı tarafındaki kodun sonu. Ancak bir adım daha vardır, ancak hata ayıklanan tarafa hangi sınıf koleksiyonunun Görselleştirici olduğunu söyleyen özniteliği.

#### <a name="to-add-the-debuggee-side-code"></a>Hata ayıklanan tarafı kodu eklemek için

1. Aşağıdaki öznitelik kodunu deyimlerden sonra, sonra, DebuggerSide.cs öğesine ekleyin `using` `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target  = typeof(System.String),
   Description  = "My First Visualizer")]
   ```

2. **Build** menüsünde **myfirstgörselleştirici Build**' i seçin. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Bu noktada, ilk Görselleştiricinizi tamamlanmıştır. Adımlara doğru bir şekilde uyuldıysanız Görselleştirici oluşturup içine yükleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ancak, ' a bir Görselleştirici yüklemeden önce [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , doğru çalıştığından emin olmak için test etmeniz gerekir. Artık Görselleştirici öğesini içine yüklemeden çalıştırmak için bir test bandı oluşturacaksınız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştiriciyi göstermek üzere bir test yöntemi eklemek için

1. Sınıfına aşağıdaki yöntemi ekleyin `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. **Build** menüsünde **myfirstgörselleştirici Build**' i seçin. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Daha sonra, görselleştiricisi DLL 'nizi çağırmak için bir yürütülebilir proje oluşturmanız gerekir. Kolaylık olması için bir konsol uygulaması projesi kullanacağız.

#### <a name="to-add-a-console-application-project-to-the-solution"></a>Çözüme bir konsol uygulaması projesi eklemek için

1. **Dosya** menüsünde, **Ekle** öğesini ve ardından **Yeni proje**' yi tıklatın.

2. **Yeni Proje Ekle** iletişim kutusunda, **Şablonlar** kutusunda **konsol uygulaması**' nı seçin.

3. **Ad** kutusuna konsol uygulaması için gibi anlamlı bir ad yazın `MyTestConsole` .

4. **Tamam**’a tıklayın.

   Şimdi, MyTestConsole Myfirstgörselleştirici çağırabilmesi için gerekli başvuruları eklemeniz gerekir.

#### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole 'a gerekli başvuruları eklemek için

1. **Çözüm Gezgini**' de, **MyTestConsole** ' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle** ' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesinde Microsoft.VisualStudio.DebuggerVisualizers.DLL ' yi seçin.

3. **Tamam**’a tıklayın.

4. **MyTestConsole** ' a sağ tıklayın ve **Başvuru Ekle** ' yi seçin.

5. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesine tıklayın ve ardından myfirstgörselleştiricisi ' e tıklayın.

6. **Tamam**’a tıklayın.

   Şimdi, test bandı sona ermesini sağlayacak kodu ekleyeceksiniz.

#### <a name="to-add-code-to-mytestconsole"></a>MyTestConsole 'a kod eklemek için

1. **Çözüm Gezgini**' de, program.cs ' a sağ tıklayın ve kısayol menüsünde **Yeniden Adlandır** ' ı seçin.

2. Program.cs ' dan adı, TestConsole.cs gibi daha anlamlı bir değere düzenleyin.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] TestConsole.cs içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirir.

3. TestConsole.cs ' de, aşağıdaki kodu `using` deyimlere ekleyin:

   ```csharp
   using MyFirstVisualizer;
   ```

4. Yönteminde `Main` aşağıdaki kodu ekleyin:

   ```
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Şimdi ilk Görselleştiriciyi test etmeye hazırsınız.

#### <a name="to-test-the-visualizer"></a>Görselleştiriciyi test etmek için

1. **Çözüm Gezgini**' de, **MyTestConsole** ' a sağ tıklayın ve kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

2. **Hata Ayıkla** menüsünde **Başlat**' ı seçin.

    Konsol uygulaması başlar ve Görselleştirici görüntülenir ve "Hello, World" dizesini görüntüler.

   Tebrikler. İlk görselleştirmeniz oluşturmuş ve test edilmiştir.

   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Yalnızca test bandı aracılığıyla çağırmak yerine Görselleştiriciyi kullanmak istiyorsanız, onu yüklemelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md).

## <a name="using-the-visualizer-item-template"></a>Görselleştiricisi öğesi şablonunu kullanma
 Şimdiye kadar, Bu anlatım el ile Görselleştirici oluşturmayı göstermiştir. Bu bir öğrenme alıştırması olarak gerçekleştirildi. Basit bir Görselleştirici nasıl çalıştığını bildiğinize göre, bir tane oluşturmak için daha kolay bir yol vardır: görselleştiricisi öğesi şablonu.

 İlk olarak, yeni bir sınıf kitaplığı projesi oluşturmanız gerekir.

#### <a name="to-create-a-new-class-library"></a>Yeni bir sınıf kitaplığı oluşturmak için

1. **Dosya** menüsünde, **Ekle** öğesini ve ardından **Yeni proje**' yi tıklatın.

2. **Yeni Proje Ekle** iletişim kutusunda, **Proje türü**' nün altında, **Visual C#**' yi seçin.

3. **Şablonlar** kutusunda **sınıf kitaplığı**' nı seçin.

4. **Ad** kutusuna, sınıf kitaplığı Için MySecondVisualizer gibi uygun bir ad yazın.

5. **Tamam**’a tıklayın.

   Şimdi, buna bir Görselleştirici öğesi ekleyebilirsiniz:

#### <a name="to-add-a-visualizer-item"></a>Bir Görselleştirici öğesi eklemek için

1. **Çözüm Gezgini**, Mysecondgörselleştirici öğesine sağ tıklayın.

2. Kısayol menüsünde **Ekle** ' yi ve ardından **Yeni öğe**' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusundaki **Şablonlar**, **Visual Studio yüklü şablonlar**altında **hata ayıklayıcı görselleştiricisi**' ı seçin.

4. **Ad** kutusuna, SecondVisualizer.cs gibi uygun bir ad yazın.

5. **Ekle**'ye tıklayın.

   Bu, hepsi bu kadar. SecondVisualizer.cs dosyasına bakın ve şablonun sizin için eklediği kodu görüntüleyin. Devam edin ve kodu deneyin. Temel bilgileri öğrenmiş olduğunuza göre, size ait daha karmaşık ve yararlı Görselleştiriciler oluşturma yönteminiz vardır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Görselleştirici Mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
