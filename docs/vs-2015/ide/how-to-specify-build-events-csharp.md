---
title: 'Nasıl yapılır: derleme olayları belirtme (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41d3ef0efd4c9eb8eab16bd12cc79f8df1449d65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670683"
---
# <a name="how-to-specify-build-events-c"></a>Nasıl Yapılır: Yapı Olaylarını Belirtme (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yapı başlamadan önce veya derleme bittikten sonra çalışan komutları belirtmek için derleme olaylarını kullanın. Derleme olayları yalnızca derleme yapı sürecinde bu noktalara başarıyla ulaşırsa yürütülür.

 Bir proje oluşturulduğunda, PreBuildEvent.bat adlı bir dosyaya ön derleme olayları eklenir ve derleme sonrası olaylar PostBuildEvent.bat adlı bir dosyaya eklenir. Hata denetimi sağlamak istiyorsanız, derleme adımlarına kendi hata denetleme komutlarınızı ekleyin.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Oluşturma öncesi ve oluşturma sonrası olayları belirtme

#### <a name="to-specify-a-build-event"></a>Derleme olayı belirtmek için

1. **Çözüm Gezgini**, yapı olayını belirtmek istediğiniz projeyi seçin.

2. **Proje** menüsünde **Özellikler**' e tıklayın.

3. **Derleme olayları** sekmesini seçin.

4. **Oluşturma öncesi olay komut satırı** kutusunda derleme olayının sözdizimini belirtin.

    > [!NOTE]
    > Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

5. **Oluşturma sonrası olay komut satırı** kutusunda derleme olayının sözdizimini belirtin.

    > [!NOTE]
    > `call`. Bat dosyalarını çalıştıran tüm derleme sonrası komutlarının önüne bir ifade ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

6. **Oluşturma sonrası olayını Çalıştır** kutusunda, oluşturma sonrası olayının çalıştırılacağı koşullar altında belirtin.

    > [!NOTE]
    > Uzun sözdizimi eklemek veya oluşturma [öncesi olay/oluşturma sonrası olay komut satırı Iletişim kutusunda](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)herhangi bir derleme makrosunu seçmek için, bir düzenleme kutusu göstermek Için üç nokta düğmesini (**...**) tıklatın.

     Derleme olayı sözdizimi, komut isteminde veya. bat dosyasında geçerli olan herhangi bir komutu içerebilir. Sonraki tüm komutların yürütüldüğünden emin olmak için bir toplu iş dosyasının adı öncesinde gelmelidir `call` .

     **Göz önünde** Oluşturma öncesi veya oluşturma sonrası olaylarınız başarıyla tamamlanmazsa, olay eyleminizi, sıfırdan farklı bir eylem belirten (0) dışında bir kodla çıkış yaparak derlemeyi sonlandırabilirsiniz.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Örnek: derleme sonrası bir olay kullanarak bildirim bilgilerini değiştirme
 Aşağıdaki yordamda, derleme sonrası olayından (proje dizinindeki. exe. manifest dosyası) çağrılan bir. exe komutu kullanılarak uygulama bildiriminde en düşük işletim sistemi sürümünün nasıl ayarlanacağı gösterilmektedir. En düşük işletim sistemi sürümü, 4.10.0.0 gibi dört bölümden oluşan bir sayıdır. Bunu yapmak için, komut `<dependentOS>` bildirimin bölümünü değiştirir:

```
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek üzere bir. exe komutu oluşturmak için

1. Komut için bir konsol uygulaması oluşturun. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Visual C#**' yi genişletin, **Windows**' a ve ardından **konsol uygulama** şablonu ' na tıklayın. Projeyi adlandırın `ChangeOSVersionCS` .

3. Program.cs ' de, aşağıdaki satırı `using` dosyanın en üstündeki diğer deyimlere ekleyin:

   ```
   using System.Xml;
   ```

4. `ChangeOSVersionCS`Ad alanında, `Program` sınıf uygulamasını şu kodla değiştirin:

   ```
   class Program
   {
      /// <summary>
      /// This function will set the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest).
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

    Komutun iki bağımsız değişkeni vardır: uygulama bildiriminin yolu (yani, yapı işleminin bildirimi oluşturduğu klasör, genellikle ProjectName. Publish) ve yeni işletim sistemi sürümü.

5. Projeyi derleyin. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

6. . Exe dosyasını gibi bir dizine kopyalayın `C:\TEMP\ChangeOSVersionVB.exe` .

   Sonra, uygulama bildirimini değiştirmek için bu komutu derleme sonrası bir olayda çağırın.

#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Uygulama bildirimini değiştirmek üzere derleme sonrası olayını çağırmak için

1. Yayımlanacak proje için bir Windows uygulaması oluşturun. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Visual C#**' yi genişletin, **Windows**' a ve ardından **Windows Forms uygulama** şablonuna tıklayın. Projeyi adlandırın `CSWinApp` .

3. **Çözüm Gezgini**' de proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

4. Proje tasarımcısında **Yayımla** sayfasını bulun ve **Yayımlama konumunu** olarak ayarlayın `C:\TEMP\` .

5. **Şimdi Yayımla**' ya tıklayarak projeyi yayımlayın.

     Bildirim dosyası oluşturulacak ve yerleştirilecek `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest` . Bildirimi görüntülemek için, dosyaya sağ tıklayın, **birlikte Aç**' a tıklayın, **Listeden programı seç**' i seçin ve ardından **Notepad**' e tıklayın.

     Dosyasında öğesi için arama yapın `<osVersionInfo>` . Örneğin, sürüm şu olabilir:

    ```
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. Proje tasarımcısında, **derleme olayları** sekmesine tıklayın ve **Derleme sonrası Düzenle** düğmesine tıklayın.

7. **Oluşturma sonrası olay komut satırı** kutusuna aşağıdaki komutu yazın:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Projeyi derlediğinizde, bu komut uygulama bildirimindeki en düşük işletim sistemi sürümünü 5.1.2600.0 olarak değiştirir.

     `$(TargetPath)`Makro oluşturulan yürütülebilir dosyanın tam yolunu ifade ettiğinden, `$(TargetPath)` . manifest, bin dizininde oluşturulan uygulama bildirimini belirtir. Yayımlama, bu bildirimi daha önce ayarladığınız yayımlama konumuna kopyalar.

8. Projeyi yeniden yayımlayın. **Yayımla** sayfasına gidin ve **Şimdi Yayımla**' ya tıklayın.

     Bildirimi yeniden görüntüleyin. Bildirimi görüntülemek için, yayımlama dizinini açın, dosyaya sağ tıklayın, **birlikte Aç**' a tıklayın, **listeden Program Seç**' i seçin ve ardından **Notepad**' e tıklayın.

     Sürüm şu anda şunu okumalı:

    ```
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme olayları sayfası, proje Tasarımcısı (C#)](../ide/reference/build-events-page-project-designer-csharp.md) [oluşturma öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md) derleme [ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
