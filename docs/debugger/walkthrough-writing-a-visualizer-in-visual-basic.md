---
title: Visual Basic bir Görselleştirici yazın | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25720f31c721cae44ed5425631a86b3a41bf475e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84180551"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Görselleştirici Yazma

Bu izlenecek yol, kullanarak basit bir Görselleştirici nasıl yazılacağını gösterir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Bu kılavuzda oluşturacağınız Görselleştirici bir Windows Forms ileti kutusu kullanarak bir dizenin içeriğini görüntüler. Bu basit dize görselleştiricisi, projelerinize daha uygun olan diğer veri türleri için Görselleştiriciler oluşturma şeklini gösteren temel bir örnektir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsüne gidin ve **Içeri aktar ve dışarı aktar** ' ı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

Görselleştiricisi kodu, hata ayıklayıcı tarafından okunacak bir DLL 'ye yerleştirilmelidir. İlk adım DLL için bir sınıf kitaplığı projesi oluşturmaktır.

## <a name="create-and-prepare-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturma ve hazırlama

### <a name="to-create-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturmak için

1. Yeni bir sınıf kitaplığı projesi oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Visual Basic**yazın, **Şablonlar**' ı seçin ve ardından **Yeni bir sınıf kitaplığı oluştur (.NET Framework)** seçeneğini belirleyin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual Basic**altında **.NET Standard**' i seçin ve ardından Ortadaki bölmede **sınıf kitaplığı (.NET Standard)** öğesini seçin.
    ::: moniker-end

2. Sınıf kitaplığı için, gibi uygun bir ad yazın `MyFirstVisualizer` ve ardından **Oluştur** veya **Tamam**' a tıklayın.

   Sınıf kitaplığını oluşturduktan sonra, burada tanımlanan sınıfları kullanabilmeniz için Microsoft.VisualStudio.DebuggerVisualizers.DLL bir başvuru eklemeniz gerekir. Ancak ilk olarak, projenize anlamlı bir ad verirsiniz.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1. vb ' i yeniden adlandırmak ve Microsoft. VisualStudio. Debuggervisualiciler eklemek için

1. **Çözüm Gezgini**, **Class1. vb**öğesine sağ tıklayın ve kısayol menüsünde **Yeniden Adlandır**' a tıklayın.

2. Name. vb olan adı DebuggerSide. vb gibi bir anlamlı olacak şekilde değiştirin.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DebuggerSide. vb içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirir.

3. **Çözüm Gezgini**, **ilk görselleştiricisi**' e sağ tıklayın ve kısayol menüsünde **Başvuru Ekle**' ye tıklayın.

4. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, **araştır** ' ı seçin ve Microsoft.VisualStudio.DebuggerVisualizers.DLL bulun.

    DLL 'yi, Visual Studio 'nun yükleme dizininin * \<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* alt dizininde bulabilirsiniz.

5. **Tamam**’a tıklayın.

6. DebuggerSide. vb içinde, aşağıdaki deyimi `Imports` deyimlere ekleyin:

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Hata ayıklayıcı tarafında kod ekleme
 Artık hata ayıklayıcı tarafı kodu oluşturmaya hazırsınız. Bu, görselleştirmek istediğiniz bilgileri göstermek için hata ayıklayıcı içinde çalışan koddur. İlk olarak, `DebuggerSide` nesne bildirimini temel sınıftan devrabir şekilde değiştirmeniz gerekir `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer 'dan devralması için

1. DebuggerSide. vb dosyasında aşağıdaki kod satırına gidin:

   ```vb
   Public Class DebuggerSide
   ```

2. Kodu aşağıdaki gibi görünecek şekilde düzenleyin:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` , geçersiz kılmanız gereken tek bir soyut yöntemi vardır `Show` .

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer. Show metodunu geçersiz kılmak için

- İçinde `public class DebuggerSide` , aşağıdaki yöntemi ekleyin:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  `Show`Yöntemi aslında Görselleştirici iletişim kutusunu veya başka Kullanıcı arabirimini oluşturan kodu içerir ve hata ayıklayıcıdan Görselleştirici 'e geçirilmiş bilgileri görüntüler. İletişim kutusunu oluşturan kodu eklemeniz ve bilgileri görüntüetmeniz gerekir. Bu izlenecek yolda, bunu bir Windows Forms ileti kutusu kullanarak yapacaksınız. İlk olarak, için bir başvuru ve `Imports` ifade eklemeniz gerekir <xref:System.Windows.Forms> .

### <a name="to-add-systemwindowsforms"></a>System. Windows. Forms eklemek için

1. **Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, **araştır**' ı seçin ve System.Windows.Forms.DLL bulun.

    DLL 'yi *C:\Windows\Microsoft.NET\Framework\v4.0.30319*içinde bulabilirsiniz.

3. **Tamam**’a tıklayın.

4. DebuggerSide.cs ' de, aşağıdaki deyimi `Imports` deyimlere ekleyin:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Görselleştirici Kullanıcı arabirimini oluşturma
 Artık Görseliniz için Kullanıcı arabirimi oluşturmak ve göstermek üzere bazı kod ekleyeceksiniz. Bu ilk görselleştiriciniz olduğundan, Kullanıcı arabirimini basit tutacaksınız ve bir Ileti kutusu kullanacaksınız.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Görselleştirici çıkışını bir iletişim kutusunda göstermek için

1. `Show` yönteminde aşağıdaki kod satırını ekleyin:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Bu örnek kod hata işleme içermez. Hata işlemeyi gerçek bir Görselleştirici veya başka bir tür uygulama içermelidir.

2. **Build** menüsünde **myfirstgörselleştirici Build**' e tıklayın. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

## <a name="add-the-necessary-attribute"></a>Gerekli özniteliği ekleyin
 Hata ayıklayıcı tarafındaki kodun sonu. Ancak, başka bir adım daha vardır: hata ayıklanan tarafa hangi sınıf koleksiyonunun Görselleştirici olduğunu belirten öznitelik.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Hata ayıklanan taraf kodu için görselleştirilecek türü eklemek için

Hata ayıklayıcı tarafında bulunan kodda, özniteliği kullanılarak hata ayıklanan için görselleştirilecek türü (nesne kaynağı) belirtirsiniz <xref:System.Diagnostics.DebuggerVisualizerAttribute> . `Target`Özelliği görselleştirilecek türü ayarlar.

1. Aşağıdaki öznitelik kodunu DebuggerSide. vb öğesine ekleyerek deyimlerden sonra, `Imports` ancak önce `namespace MyFirstVisualizer` :

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. **Build** menüsünde **myfirstgörselleştirici Build**' e tıklayın. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

## <a name="create-a-test-harness"></a>Test bandı oluşturma
 Bu noktada, ilk Görselleştiricinizi tamamlanmıştır. Adımlara doğru bir şekilde uyuldıysanız Görselleştirici oluşturup içine yükleyebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ancak, ' a bir Görselleştirici yüklemeden önce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , doğru çalıştığından emin olmak için test etmeniz gerekir. Artık Görselleştirici öğesini içine yüklemeden çalıştırmak için bir test bandı oluşturacaksınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştiriciyi göstermek üzere bir test yöntemi eklemek için

1. Sınıfına aşağıdaki yöntemi ekleyin `public DebuggerSide` :

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. **Build** menüsünde **myfirstgörselleştirici Build**' e tıklayın. Projenin başarıyla oluşturulması gerekir. Devam etmeden önce tüm derleme hatalarını düzeltin.

   Daha sonra, görselleştiricisi DLL 'nizi çağırmak için bir yürütülebilir proje oluşturmanız gerekir. Basitlik için bir konsol uygulaması projesi kullanın.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Çözüme bir konsol uygulaması projesi eklemek için

1. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **Yeni proje**' ye tıklayın.

    ::: moniker range=">=vs-2019"
    Arama kutusunda, **Visual Basic**yazın, **Şablonlar**' ı seçin ve ardından **Yeni bir konsol uygulaması oluştur (.NET Framework)** öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual Basic**altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması ' nı (.NET Framework)** seçin.
    ::: moniker-end

2. Sınıf kitaplığı için, gibi uygun bir ad yazın `MyTestConsole` ve ardından **Oluştur** veya **Tamam**' a tıklayın.

   Şimdi, MyTestConsole Myfirstgörselleştirici çağırabilmesi için gerekli başvuruları eklemeniz gerekir.

### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole 'a gerekli başvuruları eklemek için

1. **Çözüm Gezgini**' de, **MyTestConsole**' a sağ tıklayın ve kısayol menüsünde **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **Araştır** sekmesinde, Microsoft. VisualStudio. debuggervisualiciler ' ı tıklatın.

3. **Tamam**’a tıklayın.

4. **MyTestConsole**' a sağ tıklayın ve ardından **Başvuru Ekle** ' ye tıklayın.

5. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesine tıklayın ve ardından myfirstgörselleştirici ' ı seçin.

6. **Tamam**’a tıklayın.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Test ortamınızı tamamlayın ve Görselleştiriciyi test edin
 Şimdi, test bandı sona ermesini sağlayacak kodu ekleyeceksiniz.

### <a name="to-add-code-to-mytestconsole"></a>MyTestConsole 'a kod eklemek için

1. **Çözüm Gezgini**, **program. vb**öğesine sağ tıklayın ve kısayol menüsünde **Yeniden Adlandır**' a tıklayın.

2. Bu adı, Module1. vb olan **TestConsole. vb**gibi bir değere düzenleyin.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]TestConsole. vb içindeki sınıf bildirimini yeni dosya adıyla eşleşecek şekilde otomatik olarak değiştirdiğine dikkat edin.

3. TestConsole 'da. vb, aşağıdaki ifadeyi ekleyin `Imports` :

   ```vb
   Imports MyFirstVisualizer
   ```

4. Yönteminde `Main` aşağıdaki kodu ekleyin:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Şimdi ilk Görselleştiriciyi test etmeye hazırsınız.

### <a name="to-test-the-visualizer"></a>Görselleştiriciyi test etmek için

1. **Çözüm Gezgini**' de, **MyTestConsole**' a sağ tıklayın ve kısayol menüsünde **Başlangıç projesi olarak ayarla**' ya tıklayın.

2. **Hata Ayıkla** menüsünde **Başlat**' a tıklayın.

    Konsol uygulaması başlar. Görselleştirici görünür ve "Hello, World" dizesini görüntüler.

   Tebrikler. İlk görselleştirmeniz oluşturmuş ve test edilmiştir.

   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Yalnızca test bandı aracılığıyla çağırmak yerine Görselleştiriciyi kullanmak istiyorsanız, onu yüklemelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görselleştirici Mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)