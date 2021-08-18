---
title: Visual Basic |'da görselleştirici yazma Microsoft Docs
description: Bir kılavuzda basit bir görselleştirici oluşturmak için Visual Basic. Ayrıca görselleştiricinizi test etmek için bir test sıyrısı da oluşturabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9e9515291f15a8f59dec6d8c956bb03653ce7b3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133802"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Görselleştirici Yazma

Bu kılavuzda kullanarak basit bir görselleştiricinin nasıl yaz olduğu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] açıklanır. Bu kılavuzda oluşturacak görselleştirici, Windows Forms ileti kutusunu kullanarak bir dizenin içeriğini görüntüler. Bu basit dize görselleştiricisi, projeleriniz için daha uygun olan diğer veri türleri için nasıl görselleştirici oluşturabilirsiniz?

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için Araçlar menüsüne gidin ve İçeri **ve** Dışarı **Aktar'ı seçin.** Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

Görselleştirici kodu, hata ayıklayıcı tarafından okunacak bir DLL'ye yerleştirilmalıdır. İlk adım, DLL için bir sınıf kitaplığı projesi oluşturmaktır.

## <a name="create-and-prepare-a-class-library-project"></a>Sınıf Kitaplığı Oluşturma ve Hazırlama Project

### <a name="to-create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturmak için

1. Yeni bir sınıf kitaplığı projesi oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, visual **basic** yazın, Şablonlar'ı **ve** ardından Yeni Sınıf Kitaplığı **oluştur (.NET Framework) seçin.** Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual Basic** altında .NET Standard'ı seçin ve orta bölmede Sınıf Kitaplığı **(.NET Standard) seçeneğini seçin.**
    ::: moniker-end

2. sınıf kitaplığı için gibi uygun bir ad yazın ve ardından `MyFirstVisualizer` Oluştur veya **Tamam'a** **tıklayın.**

   Sınıf kitaplığını oluşturulduğunda, burada tanımlanan sınıfları kullanmak için Microsoft.VisualStudio.DebuggerVisualizers.DLL için bir başvuru eklemeniz gerekir. Ancak öncelikle projenize anlamlı bir ad vereceksiniz.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.vb'yi yeniden adlandırmak ve Microsoft.VisualStudio.DebuggerVisualizers eklemek için

1. Bu **Çözüm Gezgini** **Class1.vb'ye** sağ tıklayın ve kısayol menüsünde Yeniden Adlandır'a **tıklayın.**

2. Class1.vb olan adı DebuggerSide.vb gibi anlamlı bir adla değiştirme.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , DebuggerSide.vb dosyasındaki sınıf bildirimini yeni dosya adıyla eş olacak şekilde otomatik olarak değiştirir.

3. Bu **Çözüm Gezgini,** İlk **Görselleştiricim'e sağ tıklayın** ve kısayol menüsünde Başvuru Ekle'ye **tıklayın.**

4. Başvuru **Ekle iletişim kutusundaki** Gözat sekmesinde **Gözat'ı** **seçin** ve Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    DLL'yi, Visual Studio'nin yükleme dizininin *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* alt dizininde bulabilirsiniz.

5. **Tamam**'a tıklayın.

6. DebuggerSide.vb dosyasında deyimlerine aşağıdaki `Imports` deyimi ekleyin:

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Hata Ayıklayıcı Tarafı Kodunu Ekleme
 Artık hata ayıklayıcı tarafı kodunu oluşturmak için hazır oluruz. Bu, görselleştirmek istediğiniz bilgileri görüntülemek için hata ayıklayıcısı içinde çalışan koddur. İlk olarak, nesnesinin bildirimini `DebuggerSide` temel sınıftan devralınarak değiştirmelisiniz. `DialogDebuggerVisualizer`

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer'dan devralmak için

1. DebuggerSide.vb dosyasında aşağıdaki kod satırına gidin:

   ```vb
   Public Class DebuggerSide
   ```

2. Kodu şu şekilde olacak şekilde düzenleyin:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` geçersiz kılmamız gereken `Show` bir soyut yöntemi vardır.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show yöntemini geçersiz kılmak için

- içinde `public class DebuggerSide` aşağıdaki yöntemi ekleyin:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  yöntemi, görselleştirici iletişim kutusunu veya başka bir kullanıcı arabirimini oluşturan kodu içerir ve hata ayıklayıcıdan görselleştiriciye geçirilen `Show` bilgileri görüntüler. İletişim kutusunu oluşturan ve bilgileri görüntüleyen kodu eklemeniz gerekir. Bu kılavuzda, bunu Formlar ileti Windows kullanarak yapacaksınız. İlk olarak, için bir başvuru ve `Imports` deyimi eklemeniz <xref:System.Windows.Forms> gerekir.

### <a name="to-add-systemwindowsforms"></a>Sistem eklemek için. Windows. Forms

1. Bu **Çözüm Gezgini,** Başvurular'a **sağ** tıklayın ve kısayol menüsünde Başvuru Ekle'ye **tıklayın.**

2. Başvuru **Ekle iletişim kutusundaki** Gözat sekmesinde **Gözat'ı** **seçin** ve System.Windows.Forms.DLL.

    *DLL'yi C:\Windows\Microsoft.NET\Framework\v4.0.30319 konumunda bulabilirsiniz.*

3. **Tamam**'a tıklayın.

4. DebuggerSide.cs dosyasında deyimlerine aşağıdaki `Imports` deyimini ekleyin:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Görselleştiricinizin kullanıcı Kullanıcı Arabirimi
 Şimdi görselleştiriciniz için kullanıcı arabirimini oluşturmak ve göstermek için kod eksersiniz. Bu ilk görselleştiriciniz olduğundan, kullanıcı arabirimini basit tutacak ve bir Message Box kullanabilirsiniz.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Görselleştirici çıkışını bir iletişim kutusunda göstermek için

1. `Show` yönteminde aşağıdaki kod satırını ekleyin:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Bu örnek kod, hata işlemeyi içermez. Hata işlemeyi gerçek bir görselleştiriciye veya başka bir tür uygulamaya dahil etmek gerekir.

2. Build **(Derleme)** menüsünde **Build MyFirstVisualizer (Derleme MyFirstVisualizer) seçeneğine tıklayın.** Projenin başarıyla derlemesi gerekir. Devam etmeden önce derleme hatalarını düzeltin.

## <a name="add-the-necessary-attribute"></a>Gerekli Özniteliği Ekleme
 Bu, hata ayıklayıcı tarafı kodunun sonudur. Ancak bir adım daha vardır: hata ayıklayıcı tarafına sınıf koleksiyonunun görselleştiriciyi hangileri olduğunu söyleyen özniteliği.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Hata ayıklama tarafı kodu için görselleştirilen türü eklemek için

Hata ayıklayıcı tarafı kodunda, özniteliğini kullanarak hata ayıklayıcı için görselleştirilen türü (nesne kaynağı) <xref:System.Diagnostics.DebuggerVisualizerAttribute> belirtirsiniz. özelliği, `Target` görselleştirilen türü ayarlar.

1. Aşağıdaki öznitelik kodunu DebuggerSide.vb dosyasında deyimlerden sonra ancak `Imports` önce `namespace MyFirstVisualizer` ekleyin:

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. Build **(Derleme)** menüsünde **Build MyFirstVisualizer (Derleme MyFirstVisualizer) seçeneğine tıklayın.** Projenin başarıyla derlemesi gerekir. Devam etmeden önce derleme hatalarını düzeltin.

## <a name="create-a-test-harness"></a>Test Sıkınları Oluşturma
 Bu noktada, ilk görselleştiriciniz tamamdır. Adımları doğru şekilde izlediyebilirsiniz, görselleştiriciyi derlemek ve içine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemek. Ancak, içine bir görselleştirici [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemeden önce doğru şekilde çalıştırıla olduğundan emin olmak için test edin. Şimdi görselleştiriciyi içine yüklemeden çalıştırmak için bir test uznum [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturacak.

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştiriciyi göstermek için bir test yöntemi eklemek için

1. sınıfına aşağıdaki yöntemi `public DebuggerSide` ekleyin:

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. Build **(Derleme)** menüsünde **Build MyFirstVisualizer (Derleme MyFirstVisualizer) seçeneğine tıklayın.** Projenin başarıyla derlemesi gerekir. Devam etmeden önce derleme hatalarını düzeltin.

   Ardından görselleştirici DLL'nizi çağıracak yürütülebilir bir proje oluşturmanız gerekir. Kolaylık olması için bir konsol uygulaması projesi kullanın.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Çözüme bir konsol uygulaması projesi eklemek için

1. Bu Çözüm Gezgini, çözüme sağ tıklayın, Ekle'yi **seçin** ve ardından Yeni **Project.**

    ::: moniker range=">=vs-2019"
    Arama kutusuna visual basic yazın, Şablonlar'ı **seçin,** ardından Yeni Konsol Uygulaması oluştur (yeni konsol **uygulaması) .NET Framework.** Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual Basic** altında Windows **Masaüstü** seçeneğini ve orta bölmede Konsol Uygulaması **(.NET Framework) seçeneğini seçin.**
    ::: moniker-end

2. sınıf kitaplığı için gibi uygun bir ad yazın ve ardından `MyTestConsole` Oluştur veya **Tamam'a** **tıklayın.**

   Şimdi MyTestConsole'ın MyFirstVisualizer'ı çağırana kadar gerekli başvuruları eklemeniz gerekir.

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole'a gerekli başvuruları eklemek için

1. Bu **Çözüm Gezgini,** **MyTestConsole'a** sağ tıklayın ve kısayol menüsünde Başvuru Ekle'ye **tıklayın.**

2. Başvuru Ekle **iletişim kutusundaki** Gözat  sekmesinde Microsoft.VisualStudio.DebuggerVisualizers'a tıklayın.

3. **Tamam**'a tıklayın.

4. **MyTestConsole'a sağ tıklayın** ve ardından Başvuru **Ekle'ye yeniden** tıklayın.

5. Başvuru **Ekle iletişim kutusunda** Projeler sekmesine **tıklayın** ve ardından MyFirstVisualizer'ı seçin.

6. **Tamam**'a tıklayın.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Test UzmaNızı Bitirin ve Görselleştiricinizi Test Sınayın
 Şimdi testi tamamlamak için kodu eksersiniz.

### <a name="to-add-code-to-mytestconsole"></a>MyTestConsole'a kod eklemek için

1. Bu **Çözüm Gezgini** **Program.vb'ye** sağ tıklayın ve kısayol menüsünde Yeniden Adlandır'a **tıklayın.**

2. Module1.vb'den adını **TestConsole.vb gibi uygun bir adla düzenleyin.**

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]TestConsole.vb dosyasındaki sınıf bildirimini yeni dosya adıyla eş olacak şekilde otomatik olarak değiştirir.

3. TestConsole içinde. vb, aşağıdaki deyimi `Imports` ekleyin:

   ```vb
   Imports MyFirstVisualizer
   ```

4. yönteminde `Main` aşağıdaki kodu ekleyin:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Artık ilk görselleştiricinizi test etmeye hazır oluruz.

### <a name="to-test-the-visualizer"></a>Görselleştiriciyi test etmek için

1. Bu **Çözüm Gezgini,** **MyTestConsole'a** sağ tıklayın ve kısayol menüsünde Başlangıç Olarak **Ayarla'ya Project.**

2. Hata **Ayıkla menüsünde** Başlat'a **tıklayın.**

    Konsol uygulaması başlatılır. Görselleştirici görünür ve "Hello, World" dizesini görüntüler.

   Tebrikler. İlk görselleştiricinizi yeni ve test ettiniz.

   Görselleştiricinizi yalnızca test donanımından aramak yerine içinde kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemeniz gerekir. Daha fazla bilgi için, [bkz. How to: Install a Visualizer](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görselleştirici Mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl kurulur: Görselleştirici Yükleme](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)