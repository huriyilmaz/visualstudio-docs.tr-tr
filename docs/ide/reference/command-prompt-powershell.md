---
title: Komut satırı kabukları & geliştiriciler için istem
description: Araçlar > komut satırı menüsünden Başlat. Visual Studio Geliştirici Komut İstemi, geliştirici PowerShell ve Terminal, .NET ve C++ araçlarını daha kolay kullanmanıza imkan sağlar.
author: TerryGLee
ms.author: tglee
ms.date: 06/11/2021
ms.topic: reference
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fef783475304bb1faa1788bde591a22ed610d528
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628773"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio Geliştirici Komut İstemi ve geliştirici PowerShell

Visual Studio 2019, geliştiriciler için iki komut satırı kabuklarını içerir:

- **Visual Studio Geliştirici Komut İstemi** -komut satırı geliştirici araçlarını kullanmayı daha kolay hale getirmek için ayarlanan belirli ortam değişkenlerine sahip standart bir komut istemi. 2015 Visual Studio bu yana kullanılabilir.

- **Visual Studio geliştirici PowerShell** -bir komut isteminden daha güçlü. Örneğin, bir komutun çıkışını başka bir komutun (bir olarak bilinir) çıktısını geçirebilirsiniz *cmdlet* cmdlet . Bu kabukta Geliştirici Komut İstemi ile aynı ortam değişkenleri ayarlanmış. 2019 Visual Studio bu yana kullanılabilir.

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Geliştirici Komut İstemi clrver aracını gösteren Visual Studio için":::

Visual Studio 2019 sürüm 16,5 ' den başlayarak, Visual Studio bu kabukların birini barındırabilirler (Geliştirici Komut İstemi ve geliştirici PowerShell) tümleşik bir **terminal** içerir. Ayrıca, her kabuğun birden çok sekmesini de açabilirsiniz. Visual Studio terminali [Windows Terminal](/windows/terminal/)üzerine kurulmuştur. terminal 'yi Visual Studio açmak için, terminali **görüntüle**' yi seçin  >  .

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="birden çok sekmeyi gösteren Visual Studio terminali":::

Visual Studio geliştirici kabularından birini ayrı bir uygulama olarak veya Terminal penceresinde açtığınızda, bu, geçerli çözümünüzün dizinine (yüklenmiş bir çözümünüz varsa) açılır. Bu davranış, komutları çözüme veya projelerine karşı çalıştırmayı kolaylaştırır.

Her iki kabukların de komut satırı geliştirici araçlarını daha kolay bir şekilde kullanmanızı sağlayan belirli ortam değişkenleri vardır. Bu kabukların birini açtıktan sonra, farklı yardımcı programlara ait komutları bulundukları yere bildirmek zorunda kalmadan girebilirsiniz. 

|Popüler komutlar|Description|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Proje veya çözüm oluşturma|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| CLR için [.NET Framework aracı](/dotnet/framework/tools/index)|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|ayrıştırıcı için [.NET Framework aracı](/dotnet/framework/tools/index)|
|[`dotnet`](/dotnet/core/tools/dotnet)|[.Net CLI komutu](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[.Net CLI komutu](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|C/C++ derleme aracı|
|[`NMAKE`](/cpp/build/reference/running-nmake)|C/C++ derleme aracı|
|[`LIB`](/cpp/build/reference/lib-reference)| C/C++ derleme aracı|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| C/C++ derleme aracı|


## <a name="start-in-visual-studio"></a>Visual Studio başla

Visual Studio içinden Geliştirici Komut İstemi veya geliştirici PowerShell 'i açmak için şu adımları izleyin:

1. Visual Studio'yu açın.

1. Menü çubuğunda **Araçlar**  >  **komut satırı**  >  **Geliştirici komut istemi** veya **Geliştirici PowerShell**' i seçin.

   ![Visual Studio 'de komut istemi menü öğesi](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Windows menüsünden başlat

kabukların başlatılması için başka bir yöntem de Başlat menüsü. Visual Studio sürümüne ve yüklediğiniz ek sdk ve iş yüklerine bağlı olarak birden çok komut istemi olabilir. 

### <a name="windows-10"></a>Windows 10

1.  ![ klavyede Windows logo tuşunu başlat ' ı seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) ve **V** harfine kaydırın.

1. **Visual Studio 2019** klasörünü genişletin.

1. Vs 2019 için VS 2019 veya **Geliştirici PowerShell** **için geliştirici komut istemi** seçin.

   Alternatif olarak, görev çubuğundaki arama kutusuna kabuğun adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladıktan sonra istediğiniz sonucu seçebilirsiniz.

   ![Windows 10 arama davranışının gösterildiği animasyonlu GIF](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. klavyede Windows logo tuşuna Windows logo tuşuna basarak **başlangıç** ekranına gidin ![ .](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) Örneğin, klavyenizde.

1. **Başlat** ekranında, CTRL tuşuna basarak  +  **uygulamalar** listesini açın ve ardından **V** tuşuna basın. bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste getirir.

1. Vs 2019 için VS 2019 veya **Geliştirici PowerShell** **için geliştirici komut istemi** seçin.

### <a name="windows-7"></a>Windows 7

1. **Başlat** ' ı ve ardından **tüm programlar**' ı seçin.

1. vs 2019 için **Visual Studio 2019**  >  **Visual Studio Araçları**  >  **Geliştirici Komut İstemi** ve **vs 2019 için geliştirici PowerShell**' i seçin.

   ![Windows 7 Başlat menüsü komut istemiyle vurgulandı](./media/developer-command-prompt-for-vs/windows-7-menu.png)

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka sdk 'lar yüklüyse, ek komut istemleri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="start-from-file-browser"></a>Dosya tarayıcısından Başlat 

genellikle, yüklediğiniz kabukların kısayolları, *%programdata%\microsoft\ Windows \start Menu\Programs\ Visual Studio 2019 \ Visual Studio Araçları* gibi Visual Studio için **başlangıç menüsü** klasörüne yerleştirilir. Ancak, komut istemi araması beklenen sonuçları oluşturmazsa, makinenizde dosyaları el ile bulmayı deneyebilirsiniz.

### <a name="developer-command-prompt"></a>Geliştirici Komut İstemi

*VsDevCmd.bat* olan komut istemi dosyasının adını arayın veya *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2019 \ Community \Common7\Tools* (Visual Studio sürümünüze ve yükleme konumunuza göre yol değişiklikleri) gibi Visual Studio araçlar klasörüne gidin.

Komut istemi dosyasını bulduktan sonra, aşağıdaki komutu normal bir komut istemi penceresine girerek açın:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

ya da Windows **çalıştır** iletişim kutusuna aşağıdaki komutu girin:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Visual Studio yüklemenizin eşleşmesi için yolu düzenlemeniz gerekir.

### <a name="developer-powershell"></a>Geliştirici PowerShell

*Launch-VsDevShell.ps1* adlı bir PowerShell betik dosyası arayın veya *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2019 \ Community \Common7\Tools* gibi Visual Studio araçlar klasörüne gidin. (yol Visual Studio sürümüne, sürümüne ve yükleme konumunuza göre değişir.) powershell dosyasını bulduktan sonra, bir Windows PowerShell veya powershell 6 isteminde aşağıdaki komutu girerek çalıştırın:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

varsayılan olarak, başlatan geliştirici PowerShell, *Launch-VsDevShell.ps1* dosyasının bulunduğu yükleme yolunu Visual Studio yükleme için yapılandırılır.

> [!TIP]
> Çalıştırmak için [yürütme ilkesinin](/powershell/module/microsoft.powershell.core/about/about_execution_policies) ayarlanmış olması gerekir cmdlet .

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Terminal](/windows/terminal/)
- [.NET Framework Araçları](/dotnet/framework/tools/index)
- [Komut satırından Microsoft C++ araç takımını kullanın](/cpp/build/building-on-the-command-line)
- [Visual Studio Code kullanıcılar](https://code.visualstudio.com/docs/cpp/config-msvc#:~:text=To%20open%20the%20Developer%20Command,item%20to%20open%20the%20prompt.)
