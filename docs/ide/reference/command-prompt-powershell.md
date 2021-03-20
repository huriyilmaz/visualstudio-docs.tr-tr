---
title: Geliştiriciler için komut satırı kabukları
description: .NET ve C++ araçlarını daha kolay kullanmanıza imkan tanıyan Visual Studio Geliştirici Komut İstemi, Visual Studio Developer PowerShell ve Visual Studio Terminal 'yi bulmayı ve kullanmayı öğrenin.
ms.date: 03/04/2021
ms.custom: contperf-fy21q3
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fb2c99037577528b77ab5c1b0c74bf7af9e73d1b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672331"
---
# <a name="developer-command-prompt-and-developer-powershell"></a>Geliştirici Komut İstemi ve geliştirici PowerShell

Visual Studio 2019, geliştiriciler için iki komut satırı kabuklarını içerir:

- **Visual Studio Geliştirici komut istemi** -komut satırı geliştirici araçlarını kullanmayı daha kolay hale getirmek için ayarlanan belirli ortam değişkenlerine sahip standart bir komut istemi. Visual Studio 2015 sürümünden itibaren kullanılabilir.
- **Visual Studio Geliştirici PowerShell** -bir komut isteminden daha güçlü. Örneğin, bir komutun çıkışını başka bir komutun (bir olarak bilinir) çıktısını geçirebilirsiniz *cmdlet* cmdlet . Bu kabukta Geliştirici Komut İstemi ile aynı ortam değişkenleri ayarlanmış. Visual Studio 2019 sürümünden itibaren kullanılabilir.

Her iki kabukların de komut satırı geliştirici araçlarını daha kolay bir şekilde kullanmanızı sağlayan belirli ortam değişkenleri vardır. Bu kabukların birini açtıktan sonra, farklı yardımcı programlara ait komutları bulundukları yere bildirmek zorunda kalmadan girebilirsiniz. Çalıştırabileceğiniz komutlar şunlardır:

- [`MSBuild`](../../msbuild/msbuild-command-line-reference.md), bir proje veya çözüm oluşturmak için.
- Ve gibi [araçlar .NET Framework](/dotnet/framework/tools/index) [`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool) [`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler) .
- Ve gibi C/C++ derleme araçları [`CL`](/cpp/build/reference/compiler-command-line-syntax) [`NMAKE`](/cpp/build/reference/running-nmake) .
- Ve gibi ek C/C++ derleme araçları [`LIB`](/cpp/build/reference/lib-reference) [`DUMPBIN`](/cpp/build/reference/dumpbin-reference) .
- Ve gibi [.net CLI komutları](/dotnet/core/tools/index) [`dotnet`](/dotnet/core/tools/dotnet) [`dotnet run`](/dotnet/core/tools/dotnet-run) . (Bu komutlara düzenli bir komut isteminden de erişilebilir.)

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Clrver aracını gösteren Visual Studio için Geliştirici Komut İstemi":::

Visual Studio 2019 sürüm 16,5 ' den başlayarak, Visual Studio, bu kabukların birini (Geliştirici Komut İstemi ve geliştirici PowerShell) barındırabilirler tümleşik bir **Terminal** içerir. Ayrıca, her kabuğun birden çok sekmesini de açabilirsiniz. Visual Studio Terminal, [Windows terminalinin](/windows/terminal/)üzerine kurulmuştur. Terminal 'i Visual Studio 'da açmak için, terminali **görüntüle**' yi seçin  >  .

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Birden çok sekme gösteren Visual Studio Terminal":::

Visual Studio 'daki geliştirici kabularından birini ayrı bir uygulama olarak veya Terminal penceresinde açtığınızda, bu, geçerli çözümünüzün dizinine (yüklenmiş bir çözümünüz varsa) açılır. Bu davranış, komutları çözüme veya projelerine karşı çalıştırmayı kolaylaştırır.

## <a name="start-the-shell-from-inside-visual-studio"></a>Kabuğu Visual Studio 'Nun içinden başlatın

Geliştirici Komut İstemi veya geliştirici PowerShell 'i Visual Studio içinden açmak için şu adımları izleyin:

1. Visual Studio'yu açın.

1. Menü çubuğunda **Araçlar**  >  **komut satırı**  >  **Geliştirici komut istemi** veya **Geliştirici PowerShell**' i seçin.

   ![Visual Studio 'da komut istemi menü öğesi](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="use-the-windows-start-menu"></a>Windows Başlat menüsünü kullanma

Visual Studio sürümüne ve yüklediğiniz ek SDK ve iş yüklerine bağlı olarak birden çok komut istemi olabilir. Aşağıdaki adımlar çalışmazsa, [makinenizde dosyaları el ile bulmayı](#manually-locate-the-file) deneyebilir veya [kabuğu Visual Studio 'nun içinden başlatabilirsiniz](#start-the-shell-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1.  ![ Klavyede Windows logo tuşunu Başlat ' ı seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) ve **V** harfine kaydırın.

1. **Visual Studio 2019** klasörünü genişletin.

1. Vs 2019 için VS 2019 veya **Geliştirici PowerShell** **için geliştirici komut istemi** seçin.

   Alternatif olarak, görev çubuğundaki arama kutusuna kabuğun adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladıktan sonra istediğiniz sonucu seçebilirsiniz.

   ![Windows 10 ' da arama davranışını gösteren animasyonlu GIF](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Klavyede Windows logosu tuşu Windows logosu tuşuna basarak **Başlangıç** ekranına gidin ![ .](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) Örneğin, klavyenizde.

1. **Başlat** ekranında, CTRL tuşuna basarak  +  **uygulamalar** listesini açın ve ardından **V** tuşuna basın. Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste görüntüler.

1. Vs 2019 için VS 2019 veya **Geliştirici PowerShell** **için geliştirici komut istemi** seçin.

### <a name="windows-7"></a>Windows 7

1. **Başlat** ' ı ve ardından **tüm programlar**' ı seçin.

1. Vs 2019 için **Visual Studio 2019**  >  **Visual Studio Araçları**  >  **Geliştirici komut istemi** veya **vs 2019 için geliştirici PowerShell**' i seçin.

   ![Komut istemi vurgulanmış olarak Windows 7 Başlat menüsü](./media/developer-command-prompt-for-vs/windows-7-menu.png)

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka SDK 'lar yüklüyse, ek komut istemleri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locate-the-file"></a>Dosyayı el ile bulma

Genellikle, yüklediğiniz kabukların kısayolları, *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Araçları* gibi Visual Studio Için **Başlat menüsü** klasörüne yerleştirilir. Ancak, komut istemi araması beklenen sonuçları oluşturmazsa, makinenizde dosyaları el ile bulmayı deneyebilirsiniz.

### <a name="developer-command-prompt"></a>Geliştirici Komut İstemi

*VsDevCmd.bat* olan komut istemi dosyasının adını arayın veya *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüz, sürüm ve yükleme konumunuza göre yol değişiklikleri) gibi Visual Studio için Araçlar klasörüne gidin.

Komut istemi dosyasını bulduktan sonra, aşağıdaki komutu normal bir komut istemi penceresine girerek açın:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Veya Windows **Çalıştır** iletişim kutusuna aşağıdaki komutu girin:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Visual Studio yüklemenizin eşleşmesi için yolu düzenlemeniz gerekir.

### <a name="developer-powershell"></a>Geliştirici PowerShell

*Launch-VsDevShell.ps1* adlı bir PowerShell betik dosyası arayın veya Visual Studio için Araçlar klasörüne gidin (örneğin, *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools*. (Yol, Visual Studio sürümünüz, sürümünüz ve yükleme konumunuza göre değişir.) PowerShell dosyasını bulduktan sonra, bir Windows PowerShell veya PowerShell 6 isteminde aşağıdaki komutu girerek çalıştırın:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Varsayılan olarak, başlatan geliştirici PowerShell, *Launch-VsDevShell.ps1* dosyanın bulunduğu yükleme yolunu Içeren Visual Studio yüklemesi için yapılandırılır.

> [!TIP]
> Çalıştırmak için [yürütme ilkesinin](/powershell/module/microsoft.powershell.core/about/about_execution_policies) ayarlanmış olması gerekir cmdlet .

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirici PowerShell](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Yeni Visual Studio terminaline merhaba deyin](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Windows Terminal](/windows/terminal/)
- [.NET Framework Araçları](/dotnet/framework/tools/index)
- [Dış araçları yönetme](../managing-external-tools.md)
- [Komut satırından Microsoft C++ araç takımını kullanın](/cpp/build/building-on-the-command-line)
