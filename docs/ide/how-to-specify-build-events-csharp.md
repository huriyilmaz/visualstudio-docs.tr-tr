---
title: 'Nasıl yapılır: derleme olaylarını belirtme (C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 134a5b7cd4bb0ffc9c00a41df12ed196dd2a9212
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115131"
---
# <a name="how-to-specify-build-events-c"></a>Nasıl yapılır: derleme olaylarını belirtme (C#)

Yapı başlamadan önce veya derleme bittikten sonra çalışan komutları belirtmek için derleme olaylarını kullanın. Derleme olayları yalnızca derleme yapı sürecinde bu noktalara başarıyla ulaşırsa yürütülür.

Bir proje oluşturulduğunda, *PreBuildEvent. bat* adlı bir dosyaya ön derleme olayları eklenir ve oluşturma sonrası olaylar, *PostBuildEvent. bat*adlı bir dosyaya eklenir. Hata denetimi sağlamak istiyorsanız, derleme adımlarına kendi hata denetleme komutlarınızı ekleyin.

## <a name="specify-a-build-event"></a>Derleme olayı belirtin

1. **Çözüm Gezgini**, yapı olayını belirtmek istediğiniz projeyi seçin.

2. **Proje** menüsünde **Özellikler**' e tıklayın.

3. **Derleme olayları** sekmesini seçin.

4. **Oluşturma öncesi olay komut satırı** kutusunda derleme olayının sözdizimini belirtin.

   > [!NOTE]
   > Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

5. **Oluşturma sonrası olay komut satırı** kutusunda derleme olayının sözdizimini belirtin.

   > [!NOTE]
   > *. Bat* dosyalarını çalıştıran tüm derleme sonrası komutları önüne bir `call` ekstresi ekleyin. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

6. **Oluşturma sonrası olayını Çalıştır** kutusunda, oluşturma sonrası olayının çalıştırılacağı koşullar altında belirtin.

   > [!NOTE]
   > Uzun sözdizimi eklemek veya oluşturma [öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusunda](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)herhangi bir derleme makrosunu seçmek için, bir düzenleme kutusu göstermek için üç nokta düğmesini ( **...** ) tıklatın.

   Derleme olayı sözdizimi, komut isteminde veya *. bat* dosyasında geçerli olan herhangi bir komutu içerebilir. Sonraki tüm komutların yürütülmesini sağlamak için bir toplu iş dosyasının adının önünde `call` olması gerekir.

   > [!NOTE]
   > Oluşturma öncesi veya oluşturma sonrası olaylarınız başarıyla tamamlanmazsa, olay eyleminizi, sıfırdan farklı bir eylem belirten (0) dışında bir kodla çıkış yaparak derlemeyi sonlandırabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki yordamda, derleme sonrası olayından (proje dizinindeki *. exe. manifest* dosyası) çağrılan bir *. exe* komutu kullanılarak uygulama bildiriminde en düşük işletim sistemi sürümünün nasıl ayarlanacağı gösterilmektedir. En düşük işletim sistemi sürümü, 4.10.0.0 gibi dört bölümden oluşan bir sayıdır. En düşük işletim sistemi sürümünü ayarlamak için, komut bildirimin `<dependentOS>` bölümünü değiştirir:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir. exe komutu oluşturma

1. Komut için yeni bir **konsol uygulaması** projesi oluşturun. Projeyi **ChangeOSVersionCS**olarak adlandırın.

2. *Program.cs*' de, aşağıdaki satırı, dosyanın en üstündeki diğer `using` yönergelerine ekleyin:

   ```csharp
   using System.Xml;
   ```

3. `ChangeOSVersionCS` ad alanında, `Program` sınıfı uygulamasını şu kodla değiştirin:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
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

   Komutun iki bağımsız değişkeni vardır: uygulama bildiriminin yolu (yani, yapı işleminin bildirimi oluşturduğu klasör, genellikle *ProjectName. Publish*) ve yeni işletim sistemi sürümü.

4. Projeyi oluşturun.

5. *. Exe* dosyasını *C:\TEMP\ChangeOSVersionVB.exe*gibi bir dizine kopyalayın.

Sonra, uygulama bildirimini değiştirmek için bu komutu derleme sonrası bir olayda çağırın.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Uygulama bildirimini değiştirmek için derleme sonrası olayını çağırma

1. Yeni bir **Windows Forms App** projesi oluşturun ve bunu **CSWinApp**olarak adlandırın.

2. **Çözüm Gezgini**' de proje seçiliyken, **Proje** menüsünde **Özellikler**' i seçin.

3. **Proje tasarımcısında** **Yayımla** sayfasını bulun ve **Yayımlama konumunu** *C:\Temp*olarak ayarlayın.

4. **Şimdi Yayımla**' ya tıklayarak projeyi yayımlayın.

   Bildirim dosyası oluşturulup *C:\Temp\ CSWinApp_1_0_0_0 \cswinapp.exe.manifest dizinine*kaydedilir. Bildirimi görüntülemek için, dosyaya sağ tıklayın, **birlikte Aç**' a tıklayın, **Listeden programı seç**' i seçin ve ardından **Notepad**' e tıklayın.

   `<osVersionInfo>` öğesi için dosyada arama yapın. Örneğin, sürüm şu olabilir:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. **Proje Tasarımcısı**' na dönün, **derleme olayları** sekmesine tıklayın ve ardından **oluşturma sonrası Düzenle**' ye tıklayın.

6. **Oluşturma sonrası olay komut satırı** kutusunda, aşağıdaki komutu girin:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Projeyi derlediğinizde, bu komut uygulama bildirimindeki en düşük işletim sistemi sürümünü 5.1.2600.0 olarak değiştirir.

   `$(TargetPath)` makro oluşturulan yürütülebilir dosyanın tam yolunu ifade ettiğinden, `$(TargetPath).manifest` *bin* dizininde oluşturulan uygulama bildirimini belirtir. Yayımlama, bu bildirimi daha önce ayarladığınız yayımlama konumuna kopyalar.

7. Projeyi yeniden yayımlayın.

   Bildirim sürümü şu anda şunu okumalı:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme olayları sayfası, proje Tasarımcısı (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Oluşturma öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
