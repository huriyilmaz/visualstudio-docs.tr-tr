---
title: Nasıl yapı olayları belirtme (Visual Basic)
description: Derleme işleminin bir Visual Basic olarak betikleri, makroları veya diğer eylemleri çalıştırmak için Visual Basic derleme olaylarının nasıl kullanıla olacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 272fa3bd66f863744986ed5dace44cf8327c08b02dd2e767ebff9e939cc19e65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121318739"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Nasıl yapı olayları belirtme (Visual Basic)

Derleme Visual Basic derleme işleminin bir parçası olarak betikleri, makroları veya diğer eylemleri çalıştırmak için kullanılabilir. Derleme öncesi olaylar derlemeden önce gerçekleşir; derleme sonrası olaylar derlemeden sonra oluşur.

Derleme olayları, Derleme Olayları **iletişim kutusunda** belirtilir ve derleme **tasarımcısının** Derleme **Project kullanılabilir.**

> [!NOTE]
> Visual Basic Express, derleme olaylarının girişini desteklemez. Bu yalnızca tam üründe Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Derleme öncesi ve derleme sonrası olayları belirtme

### <a name="to-specify-a-build-event"></a>Derleme olayı belirtmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'ye** **tıklayın.**

2. Derle **sekmesine** tıklayın.

3. Derleme Olayları **iletişim kutusunu** açmak için Derleme **Olayları düğmesine** tıklayın.

4. Derleme öncesi veya derleme sonrası eyleminiz için komut satırı bağımsız değişkenlerini girin ve ardından Tamam'a **tıklayın.**

    > [!NOTE]
    > Tüm derleme `call` sonrası komutların öncesinde bir deyimi ekleyin ve *.bat* ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

    > [!NOTE]
    > Derleme öncesi veya derleme sonrası olayınız başarıyla tamamlansa da, olay eylemini sıfır (0) dışında bir kodla çıkararak derlemeyi sonlandırabilirsiniz. Bu, başarılı bir eylem olduğunu gösterir.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Örnek: Derleme sonrası olay kullanarak bildirim bilgilerini değiştirme

Aşağıdaki yordam, derleme sonrası olaydan (proje dizininde *.exe.manifest dosyası)* adlı bir.exekomutu kullanarak uygulama *bildiriminde* en düşük işletim sistemi sürümünü ayarlamayı gösterir. En düşük işletim sistemi sürümü, 4.10.0.0 gibi dört parçalı bir sayıdır. Bunu yapmak için komut `<dependentOS>` bildirimin bölümünü değiştirir:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini .exe bir komut oluşturmak için

1. komutu için bir konsol uygulaması oluşturun. Dosya menüsünde **Yeni** 'ye **ve** ardından Yeni'ye **Project.**

2. Yeni **Project** iletişim kutusunda, **Visual Basic** düğümünde Windows'yi  ve ardından **Konsol Uygulaması şablonunu** seçin. Projeyi olarak `ChangeOSVersionVB` adlar.

3. *Module1.vb dosyasında,* dosyanın üst kısmında yer alan `Imports` diğer deyimlerine aşağıdaki satırı ekleyin:

   ```vb
   Imports System.Xml
   ```

4. aşağıdaki kodu 'ye `Sub Main` ekleyin:

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

   komutu iki bağımsız değişken alır. İlk bağımsız değişken, uygulama bildiriminin yoludur (yani derleme işleminin bildirimi oluşturduğu klasör, genellikle *\<ProjectName> .publish).* İkinci bağımsız değişken, yeni işletim sistemi sürümüdür.

5. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

6. Dosya *.exe* gibi bir dizine kopyalayın *C:\TEMP\ChangeOSVersionVB.exe.*

   Ardından, uygulama bildirimini değiştirmek için derleme sonrası bir olayda bu komutu çağırabilirsiniz.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için derleme sonrası olayı çağırmak için

1. Projenin Windows için bir uygulama oluşturun. Dosya menüsünde **Yeni** 'ye **ve** ardından Yeni'ye **Project.**

2. Yeni **Project** iletişim kutusunda, **Visual Basic** **Desktop'ı Windows ve** Windows Forms Uygulaması **şablonunu** seçin. Projeyi olarak `VBWinApp` adlar.
3. proje öğesinde **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

4. Project **Tasarımcısı'nda** Yayımla sayfasına **gidin ve** Yayımlama konumu'na *C:\TEMP olarak ayarlayın.* 

5. Şimdi Yayımla'ya tıklayarak **projeyi yayımlayın.**

     Bildirim dosyası yerleşik olarak *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest içine konacak.* Bildirimi görüntülemek için, dosyaya sağ tıklayın ve **Birlikte aç'a** tıklayın, ardından Listeden programı  **seçin'e** tıklayın ve sonra da Not Defteri.

     dosyasında öğesi için `<osVersionInfo>` arama. Örneğin, sürüm şöyle olabilir:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. Project **Tasarımcısı'nda** Derle sekmesine **gidin** ve  Derleme Olayları iletişim kutusunu açmak **için Olayları Derle düğmesine** tıklayın.

7. Derleme **Sonrası Olay Komut Satırı kutusuna** aşağıdaki komutu girin:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Projeyi derlemek için bu komut uygulama bildiriminde en düşük işletim sistemi sürümünü 5.1.2600.0 olarak değiştirir.

     Makro, `$(TargetPath)` oluşturulacak yürütülebilir dosyanın tam yolunu ifade ediyor. Bu *nedenle$(TargetPath).manifest,* bin dizininde oluşturulan uygulama *bildirimini* belirtir. Yayımlama, bu bildirimi daha önce ayarlayıp yayımlama konumu olarak kopyalayacak.

8. Projeyi yeniden yayımlayın. Yayımla sayfasına **gidin ve** Şimdi **Yayımla'ya tıklayın.**

     Bildirimi yeniden görüntüleme. Bildirimi görüntülemek için yayımlama dizinine gidin, dosyaya sağ  tıklayın, Birlikte aç'a tıklayın ve ardından Listeden **programı** seçin'e ve ardından **Not Defteri.**

     Sürüm artık şunları okumalı:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme sayfası, Project Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Yayımlama sayfası, Project Tasarımcısı](../ide/reference/publish-page-project-designer.md)
- [Derleme öncesi olay/Derleme sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Nasıl yap: Derleme olaylarını belirtme (C#)](../ide/how-to-specify-build-events-csharp.md)
