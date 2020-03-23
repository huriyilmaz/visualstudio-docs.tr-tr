---
title: 'Nasıl yapılır: Yapı olaylarını belirtme (Visual Basic)'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cf9cadc8fbf091fb213926fb25b232d14dc0d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115100"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Nasıl yapılır: Yapı olaylarını belirtme (Visual Basic)

Visual Basic'teki yapı olayları, derleme işleminin bir parçası olarak komut dosyalarını, makroları veya diğer eylemleri çalıştırmak için kullanılabilir. Yapı öncesi olaylar derlemeden önce oluşur; derlemeden sonra yapı sonrası olaylar oluşur.

Yapı olayları, **Project Designer'ın** **Derleme** sayfasından bulunan **Yapı Olayları** iletişim kutusunda belirtilir.

> [!NOTE]
> Visual Basic Express, yapı etkinliklerinin girişini desteklemez. Bu sadece tam Visual Studio ürün desteklenir.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Yapı öncesi ve sonrası olayları belirtme

### <a name="to-specify-a-build-event"></a>Yapı olayı belirtmek için

1. **Çözüm Gezgini'nde**seçilen bir projeyle, **Proje** menüsünde **Özellikler'i**tıklatın.

2. **Derle** sekmesini tıklatın.

3. Etkinlikler **Oluştur** iletişim kutusunu açmak için Etkinlikler **Oluştur** düğmesini tıklatın.

4. Önceden yapılanveya yapı sonrası eyleminiz için komut satırı bağımsız değişkenlerini girin ve ardından **Tamam'ı**tıklatın.

    > [!NOTE]
    > `call` *.bat* dosyalarını çalıştıran tüm yapı sonrası komutlardan önce bir deyim ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

    > [!NOTE]
    > Önceden inşa edilen veya yapı sonrası etkinliğiniz başarıyla tamamlanmazsa, olay eyleminiz intihanı başarılı bir eylemi gösteren sıfır (0) dışında bir kodla çıkararak yapıyı sonlandırabilirsiniz.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Örnek: Oluşturma sonrası olayı kullanarak manifesto bilgilerini değiştirme

Aşağıdaki yordam, uygulama bildiriminde, yapı sonrası olaydan (proje dizinindeki *.exe.manifest* dosyası) çağrılan bir *.exe* komutunu kullanarak minimum işletim sistemi sürümünün nasıl ayarlanıştırılaşını gösterir. Minimum işletim sistemi sürümü 4.10.0.0 gibi dört bölümlü bir sayıdır. Bunu yapmak için komut, `<dependentOS>` bildirimin bölümünü değiştirir:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir .exe komutu oluşturmak için

1. Komut için bir konsol uygulaması oluşturun. **Dosya** menüsünden **Yeni'yi**tıklatın ve sonra **Project'i**tıklatın.

2. Yeni **Proje** iletişim kutusunda, **Visual Basic** düğümünde **Windows'u** ve ardından **Konsol Uygulaması** şablonu'nu seçin. Projeyi `ChangeOSVersionVB`adlandırın.

3. *Module1.vb'de,* dosyanın üst `Imports` kısmındaki diğer ifadelere aşağıdaki satırı ekleyin:

   ```vb
   Imports System.Xml
   ```

4. Aşağıdaki kodu `Sub Main`ekleyin:

   ```vb
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

   Komut iki bağımsız değişken alır. İlk bağımsız değişken, uygulama bildirimine giden yoldur (diğer bir deyişle, yapı işleminin manifeste yi oluşturduğu klasör, genellikle * \<ProjectName>.publish).* İkinci bağımsız değişken yeni işletim sistemi sürümüdür.

5. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

6. *.exe* dosyasını *C:\TEMP\ChangeOSVersionVB.exe*gibi bir dizine kopyalayın.

   Ardından, uygulama bildirimini değiştirmek için yapı sonrası bir olay da bu komutu çağırın.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir oluşturma sonrası olay çağırmak için

1. Projenin yayımlanması için bir Windows uygulaması oluşturun. **Dosya** menüsünden **Yeni'yi**tıklatın ve sonra **Project'i**tıklatın.

2. Yeni **Proje** iletişim kutusunda, **Visual Basic** düğümünde **Windows Desktop'ı** ve ardından **Windows Forms App şablonu'nu** seçin. Projeyi `VBWinApp`adlandırın.
3. **Çözüm Gezgini'nde**seçilen projeyle, **Proje** menüsünde **Özellikler'i**tıklatın.

4. Proje **Tasarımcısı'nda,** **Yayımla** sayfasına gidin ve **Yayımlama konumunu** *C:\TEMP*olarak ayarlayın.

5. **Şimdi Yayımla'yı**tıklatarak projeyi yayımlayın.

     Manifesto dosyası inşa edilecek ve *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*konulacak. Bildirimi görüntülemek için dosyayı sağ tıklatın ve **Aç'a**tıklayın , ardından **program listesinden seç'i**tıklatın ve ardından Not **Defteri'ni**tıklatın.

     `<osVersionInfo>` Öğe yi bulmak için dosyada arama yapın. Örneğin, sürüm aşağıdakiler olabilir:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. Project **Designer'da,** **Derleme** sekmesine gidin ve **Etkinlikler Oluştur** iletişim kutusunu açmak için Etkinlikler **Oluştur** düğmesini tıklatın.

7. Oluşturma **Sonrası Olay Komut Satırı** kutusuna aşağıdaki komutu girin:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Projeyi oluşturduğunuzda, bu komut uygulama bildirimindeki minimum işletim sistemi sürümünü 5.1.2600.0 olarak değiştirir.

     Makro, `$(TargetPath)` çalıştırılan oluşturulan için tam yolu ifade eder. Bu nedenle, *$(TargetPath).manifest* *bin* dizini oluşturulan uygulama bildirimi ni belirtir. Yayımlama, bu bildirimi daha önce ayarladığınız yayımlama konumuna kopyalar.

8. Projeyi yeniden yayımlayın. **Yayımla** sayfasına gidin ve **Şimdi Yayımla'yı**tıklatın.

     Bildirimi yeniden görüntüleyin. Bildirimi görüntülemek için yayımlama dizinine gidin, dosyayı sağ tıklatın ve **Açık'ı** tıklatın ve ardından **programı listeden seçin**ve ardından Not **Defteri'ni**tıklatın.

     Sürüm şimdi okumalısınız:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Yayın sayfası, Proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)
- [Önceden yapı olay/Post-build olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Nasıl yapılır: Yapı olaylarını belirtin (C#)](../ide/how-to-specify-build-events-csharp.md)
