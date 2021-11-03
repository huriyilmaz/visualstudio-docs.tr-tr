---
title: Komut satırı kabukları & istemini içerir
description: Araçlar'dan > Satırı menüsüne gidin. Visual Studio Geliştirici Komut İstemi, Geliştirici PowerShell ve terminal sayesinde .NET ve C++ araçlarını daha kolay bir şekilde kullanabilirsiniz.
author: TerryGLee
ms.author: tglee
ms.date: 10/26/2021
ms.topic: conceptual
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
monikerRange: vs-2019
ms.openlocfilehash: f25786e33a13cc526480a76a53215562146c4116
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131126512"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio Geliştirici Komut İstemi ve Geliştirici PowerShell

Visual Studio 2019'da geliştiriciler için iki komut satırı kabuğu vardır:

- **Visual Studio Geliştirici Komut İstemi** - Komut satırı geliştirici araçlarını kullanmayı kolaylaştırmak için belirli ortam değişkenleri ayarlanmış standart bir komut istemi. 2015 Visual Studio kullanılabilir.

- **Visual Studio Geliştirici PowerShell** - Komut isteminden daha güçlü. Örneğin, bir komutun çıktısını (olarak bilinir) başka *cmdlet* bir komutuna geçebilirsiniz. cmdlet Bu kabuk, ortam değişkenleriyle aynı ortam değişkenlerine Geliştirici Komut İstemi. 2019 Visual Studio kullanılabilir.

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Geliştirici Komut İstemi clrver Visual Studio gösteren bir araçtır":::

2019 Visual Studio 16.5 sürümünden itibaren Visual Studio, bu kabuklardan herhangi birini (Geliştirici Komut İstemi ve Developer PowerShell) barındıracak tümleşik **bir terminal** içerir. Ayrıca her bir kabuğun birden çok sekmeyi de açabilirsiniz. Visual Studio terminali, üzerinde [Windows Terminal.](/windows/terminal/) Terminali terminalde açmak Visual Studio Terminali **Görüntüle'yi**  >  **seçin.**

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Visual Studio sekme gösteren bir terminal":::

Visual Studio'daki geliştirici kabuklarından birini ayrı bir uygulama olarak veya Terminal penceresinde asanız geçerli çözüm dizininiz açılır (bir çözüm yüklü ise). Bu davranış, çözümde veya projelerinde komut çalıştırmayı kullanışlı hale getirir.

Her iki kabukta da komut satırı geliştirici araçlarını daha kolay bir şekilde kullanabileceğiniz belirli ortam değişkenleri ayarlanmıştır. Bu kabuklardan birini açtıktan sonra, nerede olduklarını bilmek zorunda kalmadan farklı yardımcı programlar için komutları girebilirsiniz.

|Popüler komutlar|Description|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Proje veya çözüm oluşturma|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| CLR [için .NET Framework](/dotnet/framework/tools/index) aracı|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|Bir [.NET Framework](/dotnet/framework/tools/index) için bir araç|
|[`dotnet`](/dotnet/core/tools/dotnet)|[.NET CLI komutu](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[.NET CLI komutu](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|C/C++ derleme aracı|
|[`NMAKE`](/cpp/build/reference/running-nmake)|C/C++ derleme aracı|
|[`LIB`](/cpp/build/reference/lib-reference)| C/C++ derleme aracı|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| C/C++ derleme aracı|

## <a name="start-in-visual-studio"></a>Başlangıç olarak Visual Studio

Geliştirici Komut İstemi veya Developer PowerShell'i Visual Studio:

1. Visual Studio'yu açın.

1. Menü çubuğunda Araçlar Komut **Satırı'Geliştirici Komut İstemi**  >    >  **veya Geliştirici** **PowerShell'i seçin.**

   ![Komut istemi menü öğesi Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Başlat menüsünden Windows başlat

Kabukları başlatmanın bir diğer yolu da Başlat menüsü. Visual Studio sürümüne ve yüklü olan tüm ek SDK'lere ve iş yüklere bağlı olarak birden çok komut istemine sahip olabilirsiniz.

### <a name="windows-10"></a>Windows 10

1. Klavyede **Windows** ![ logo tuşuyla başlat'ı seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) ve V harfine **kaydırın.**

1. Visual Studio **2019 klasörünü** genişletin.

1. **VS 2019 için Geliştirici Komut İstemi** veya VS **2019 için Geliştirici PowerShell'i seçin.**

   Alternatif olarak, görev çubuğundaki arama kutusuna kabuğun adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladığında istediğiniz sonucu seçebilirsiniz.

   ![Dosyada arama davranışını gösteren animasyonlu gif Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Windows logo  tuşuna basarak Windows ![ ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) örneğin, klavyenizde.

1. Başlangıç **ekranında,** Uygulamalar listesini açmak **için Ctrl** + **Tab** **tuşuna basın** ve ardından V'ye **basın.** Bu, tüm yüklü komut istemlerini içeren Visual Studio getirir.

1. **VS 2019 için Geliştirici Komut İstemi** veya VS **2019 için Geliştirici PowerShell'i seçin.**

### <a name="windows-7"></a>Windows 7

1. **Başlat'ı** seçin ve ardından Tüm **Programlar'ı genişletin.**

1. VS **2019 için Visual Studio 2019** Visual Studio Araçları Geliştirici Komut İstemi veya  >    >  **VS 2019** için **Geliştirici PowerShell'i seçin.**

   ![Windows 7 Başlat menüsü komut istemi vurgulanmış](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Windows 10 SDK veya önceki sürümleri gibi başka [SDK'lar](https://developer.microsoft.com/windows/downloads/windows-10-sdk) [yüklüyse,](https://developer.microsoft.com/windows/downloads/sdk-archive)ek komut istemleri bulabilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="start-from-file-browser"></a>Dosya tarayıcıdan başlama

Genellikle, yüklü kabuklar için kısayollar Visual Studio için  Başlat Menüsü klasörüne yerleştirilir; örneğin, *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Araçları*. Ancak komut isteminde arama yapmak beklenen sonuçları üretmezse, makinenizin dosyalarını el ile bulmaya çalışabilirsiniz.

### <a name="developer-command-prompt"></a>Geliştirici Komut İstemi

komut istemi dosyasının adını *(VsDevCmd.bat)* bulun veya *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüz, sürümünüz ve yükleme konumunuz için yol değişiklikleri) gibi Visual Studio için Araçlar klasörüne gidin.

Komut istemi dosyasını bulasanız, normal bir komut istemi penceresine aşağıdaki komutu girerek dosyayı açın:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Veya Çalıştır iletişim kutusuna aşağıdaki Windows  girin:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Yolu, uygulama yüklemesi ile eşleşmesi için Visual Studio gerekir.

### <a name="developer-powershell"></a>Geliştirici PowerShell

*Launch-VsDevShell.ps1* adlı bir PowerShell betiği dosyası bulun veya *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* gibi Visual Studio için Araçlar klasörüne gidin. (Yol, Visual Studio sürümüne ve yükleme konumunuza göre değişir.) PowerShell dosyasını bulamadan önce bir Windows PowerShell veya PowerShell 6 istemine aşağıdaki komutu girerek çalıştırın:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Varsayılan olarak, başlatan Geliştirici PowerShell, Visual Studio dosyasının bulunduğu yükleme yolu *Launch-VsDevShell.ps1* için yapılandırılır.

> [!TIP]
> [çalıştırması](/powershell/module/microsoft.powershell.core/about/about_execution_policies) için yürütme ilkesi ayar cmdlet gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Terminal](/windows/terminal/)
- [.NET Framework Araçları](/dotnet/framework/tools/index)
- [Komut satırına ait Microsoft C++ araç kümesi kullanma](/cpp/build/building-on-the-command-line)
- [Visual Studio Code kullanıcılar](https://code.visualstudio.com/docs/cpp/config-msvc#:~:text=To%20open%20the%20Developer%20Command,item%20to%20open%20the%20prompt.)
