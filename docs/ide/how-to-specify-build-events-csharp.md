---
title: 'Nasıl yapılır: Yapı olaylarını belirtin (C#)'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115131"
---
# <a name="how-to-specify-build-events-c"></a>Nasıl yapılır: Yapı olaylarını belirtin (C#)

Yapı başlamadan önce veya yapı bittikten sonra çalışan komutları belirtmek için yapı olaylarını kullanın. Yapı olayları yalnızca yapı işleminde bu noktalara başarıyla ulaşırsa yürütülür.

Bir proje inşa edildiğinde, *PreBuildEvent.bat* adlı bir dosyaya önceden oluşturulmuş olaylar eklenir ve post-build olaylar *PostBuildEvent.bat*adlı bir dosyaya eklenir. Hata denetimi sağlamak istiyorsanız, yapı adımlarına kendi hata denetimi komutlarınızı ekleyin.

## <a name="specify-a-build-event"></a>Bir yapı olayı belirtin

1. **Çözüm Gezgini'nde,** yapı olayını belirtmek istediğiniz projeyi seçin.

2. **Proje** menüsünde **Özellikler'i**tıklatın.

3. Olayları **Oluştur** sekmesini seçin.

4. Yapı **öncesi olay komut satırı** kutusunda, yapı olayının sözdizimini belirtin.

   > [!NOTE]
   > Proje güncelse ve hiçbir yapı tetiklenmiyorsa, önceden yapı olayları çalışmaz.

5. Yapı **sonrası olay komut satırı** kutusunda, yapı olayının sözdizimini belirtin.

   > [!NOTE]
   > `call` *.bat* dosyalarını çalıştıran tüm yapı sonrası komutlardan önce bir deyim ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

6. Yapı **sonrası olay** kutusunu Çalıştır'da, yapı sonrası olayı hangi koşullaraltında çalıştıracaklarını belirtin.

   > [!NOTE]
   > Uzun sözdizimi eklemek veya [Yapı Öncesi olay/post-build olay komut satırı iletişim kutusundan](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)herhangi bir yapı makrosu seçmek için, bir düzen kutusunu görüntülemek için elips düğmesini (**...**) tıklatın.

   Yapı olayı sözdizimi, komut isteminde veya *.bat* dosyasında geçerli olan tüm komutları içerebilir. Sonraki tüm komutların yürütülmediğinden `call` emin olmak için bir toplu iş dosyasının adı önce olmalıdır.

   > [!NOTE]
   > Önceden inşa edilen veya yapı sonrası etkinliğiniz başarıyla tamamlanmazsa, olay eyleminiz intihanı başarılı bir eylemi gösteren sıfır (0) dışında bir kodla çıkararak yapıyı sonlandırabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki yordam, yapı sonrası olaydan (proje dizinindeki *.exe.manifest* dosyası) çağrılan bir *.exe* komutu kullanarak uygulama bildiriminde en az işletim sistemi sürümünün nasıl ayarlanır olduğunu gösterir. Minimum işletim sistemi sürümü 4.10.0.0 gibi dört bölümlü bir sayıdır. Minimum işletim sistemi sürümünü ayarlamak için komut, `<dependentOS>` bildirimin bölümünü değiştirir:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir .exe komutu oluşturma

1. Komut için yeni bir **Konsol Uygulaması** projesi oluşturun. Proje **ChangeOSVersionCS**adı.

2. *Program.cs,* dosyanın üst kısmındaki `using` diğer yönergelere aşağıdaki satırı ekleyin:

   ```csharp
   using System.Xml;
   ```

3. `ChangeOSVersionCS` Ad alanında, `Program` sınıf uygulamasını aşağıdaki kodla değiştirin:

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

   Komut iki bağımsız değişken alır: uygulama bildiriminin yolu (diğer bir deyişle, yapı işleminin bildirimi oluşturduğu klasör, genellikle *Projectname.publish),* ve yeni işletim sistemi sürümü.

4. Projeyi derleyin.

5. *.exe* dosyasını *C:\TEMP\ChangeOSVersionVB.exe*gibi bir dizine kopyalayın.

Ardından, uygulama bildirimini değiştirmek için yapı sonrası bir olay da bu komutu çağırın.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Uygulama bildirimini değiştirmek için bir oluşturma sonrası olay çağırma

1. Yeni bir **Windows Forms App** projesi oluşturun ve adını **CSWinApp.**

2. **Çözüm Gezgini'nde**seçilen projeyle, **Project** menüsünde **Özellikler'i**seçin.

3. Proje **Tasarımcısı'nda** **Yayımla** sayfasını bulun ve **Yayımlama konumunu** *C:\TEMP*olarak ayarlayın.

4. **Şimdi Yayımla'yı**tıklatarak projeyi yayımlayın.

   Bildirim dosyası oluşturulur ve *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*kaydedilir. Bildirimi görüntülemek için dosyayı sağ tıklatın, **Aç'ı**tıklatın , **listeden programı seçin'i**seçin ve ardından **Not Defteri'ni**tıklatın.

   `<osVersionInfo>` Öğe yi bulmak için dosyada arama yapın. Örneğin, sürüm aşağıdakiler olabilir:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. **Project**Designer'da, **Etkinlikler Oluştur** sekmesini tıklatın ve ardından **Post-build'i edit'i**tıklatın.

6. Oluşturma **Sonrası Olay Komut Satırı** kutusuna aşağıdaki komutu girin:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Projeyi oluşturduğunuzda, bu komut uygulama bildirimindeki minimum işletim sistemi sürümünü 5.1.2600.0 olarak değiştirir.

   `$(TargetPath)` Makro, oluşturulabilir oluşturma nın tam yolunu ifade `$(TargetPath).manifest` ettiği için, *depo* gözü dizinde oluşturulan uygulama bildirimini belirtir. Yayımlama, bu bildirimi daha önce ayarladığınız yayımlama konumuna kopyalar.

7. Projeyi yeniden yayımlayın.

   Manifesto sürümü şimdi okumalıdır:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Etkinlikler sayfası oluştur, Proje Tasarımcısı (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Önceden yapı olay/Post-build olay komut satırı iletişim kutusu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Nasıl yapılır: Yapı olaylarını belirtme (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
