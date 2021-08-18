---
title: Python projeleri için özel menü komutları tanımlama
description: Proje ve hedef dosyalarını düzenleyerek, yürütülebilir programları, betikleri, modülleri, satır içi kod parçacıklarını ve pip'i çağırmak için Visual Studio'daki Python proje bağlam menüsüne özel komutlar ekleyebilirsiniz.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 63679d590e341cce8f5ee76d4b359821b3f213b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140446"
---
# <a name="define-custom-commands-for-python-projects"></a>Python projeleri için özel komutlar tanımlama

Python projeleriniz ile çalışma sürecinde belirli betikleri veya modülleri çalıştırmak, pip komutlarını çalıştırmak veya başka bir rastgele araç çalıştırmak için bir komut penceresine geçiş yapabilirsiniz. İş akışınızı geliştirmek için Python projesi bağlam menüsünde **Python** alt menüsüne özel komutlar ekleyebilirsiniz. Bu komutlar bir konsol penceresinde veya Visual Studio **çalıştırabilirsiniz.** Ayrıca, komut çıkışından hataları ve uyarıları Visual Studio için normal ifadeleri de kullanabilirsiniz.

Varsayılan olarak, bu menü yalnızca tek bir **PyLint Çalıştır komutunu** içerir:

![Projenin bağlam menüsünde Python alt menüsünün varsayılan görünümü](media/custom-commands-default-menu.png)

Özel komutlar aynı bağlam menüsünde görünür. Özel komutlar doğrudan bir proje dosyasına eklenir ve bu komutlar bu projeye uygulanır. Ayrıca, birden çok proje dosyasına kolayca aktarılmış bir *.targets* dosyasında özel komutlar tanımlayabilirsiniz.

Içinde belirli Python proje Visual Studio zaten *kendi .targets* dosyasını kullanarak kendi özel komutlarını ekler. Örneğin, Bottle Web Project ve Flask Web Project şablonları iki komut ekler: **Sunucuyu başlat** ve Hata **ayıklamayı başlat sunucusu.** Django Web Project şablonu aynı komutların yanı sıra birkaç tane daha ekler:

![Django projesinin bağlam menüsünde Python alt menüsünün görünümü](media/custom-commands-django-menu.png)

Her özel komut python dosyası, Python modülü, satır içi Python kodu, rastgele yürütülebilir dosya veya pip komutuna başvurur. Ayrıca, komutun nasıl ve nerede çalıştırılamayacaklarını da belirtebilirsiniz.

> [!Tip]
> Metin düzenleyicisinde proje dosyasında her değişiklik yaptığınız zaman, bu değişiklikleri uygulamak için projeyi Visual Studio yeniden yüklemek gerekir. Örneğin, bu komutların projenin bağlam menüsünde görünmesi için özel komut tanımları ekledikten sonra projeyi yeniden yükleyebilirsiniz.
>
> Bildiğiniz gibi, Visual Studio doğrudan proje dosyasını düzenlemenin bir anlamı vardır. İlk olarak proje dosyasına sağ tıklar ve Projeyi kaldır'ı **\<project-name>** **seçersiniz,** sonra yeniden sağ tıklar ve Düzenle'yi seçerek projeyi Visual Studio açarsınız. Ardından düzenlemeler yapacak ve kaydederek projeye bir kez daha sağ tıklayabilir ve Projeyi yeniden yükle'yi seçerek proje dosyasının düzenleyicide kapatılamadıktan emin olun.
>
> Ancak, özel bir komut geliştirerek bu tıklamaların hepsi sıkıcı olabilir. Daha verimli bir iş akışı için projeyi Visual Studio'a yük dengelemenin yanı sıra *.pyproj* dosyasını ayrı bir düzenleyicide (Visual Studio, Visual Studio Code, Not Defteri vb.) açın. Değişiklikleri düzenleyicide kaydedip Visual Studio Visual Studio algılar ve projeyi yeniden yüklemenin gerekip gerek olmadığını sorar ( Proje, ortamın dışında **\<name> değiştirilmiştir.**). Yeniden **Yükle'yi** seçin. Değişiklikleriniz tek adımda hemen uygulanır.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Adım adım kılavuz: Proje dosyasına komut ekleme

Özel komutlar hakkında bilgi sahibi olmak için bu bölümde, doğrudanpython.exekullanarak bir projenin başlangıç dosyasını *çalıştıran basit bir örnek vepython.exe.* (Bu tür bir komut, Hata Ayıklama kullanmakla **etkili bir şekilde aynıdır**  >  **Hata Ayıklama olmadan başlat.)**

1. Python Uygulama şablonunu kullanarak "Python-CustomCommands" adlı yeni **bir proje** oluşturun. (İşlem [hakkında bilgi sahibi değilken yönergeler için](quickstart-02-python-in-visual-studio-project-from-template.md) bkz. Hızlı Başlangıç: Şablondan Python projesi oluşturma.)

1. *Python_CustomCommands.py'de* kodunu `print("Hello custom commands")` ekleyin.

1. içinde projeye sağ **tıklayın Çözüm Gezgini** **Python'u** seçin ve altmenüste görünen tek komutun **Run PyLint (PyLint** Çalıştır) olduğunu göreceksiniz. Özel komutlarınız aynı alt menüde görünür.

1. Girişte önerilen şekilde *Python-CustomCommands.pyproj'ı ayrı* bir metin düzenleyicisinde açın. Ardından dosyanın sonuna aşağıdaki satırları kapanış dosyasının hemen içine ekleyin `</Project>` ve dosyayı kaydedin.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Dosya değişikliği Visual Studio **yeniden yükle'yi** seçin. Ardından **Python** menüsünü yeniden kontrol edin ve pylint komutunu içeren varsayılan özellik grubunu çoğaltarak burada gösterilen tek öğenin **PyLint'i** çalıştırmaya devam etmek `<PythonCommands>` olduğunu göreceksiniz.

1. Proje dosyasıyla düzenleyiciye geçiş yapın ve sonra `<Target>` aşağıdaki tanımı `<PropertyGroup>` ekleyin. Bu makalenin devamlarında da belirtildiği gibi, bu öğe bir konsol penceresindeki dosyaları kullanarak başlangıç dosyasını `Target` ("StartupFile" özelliğiyle tanımlanır) *python.exe* özel bir komut tanımlar. özniteliği, `ExecuteIn="consolepause"` kapatmadan önce bir tuşa basmanı bekler.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Öğesinin aşağıdaki koda benzini ifade etmek için target özniteliğinin değerini daha `Name` önce eklenen özellik grubuna `<PythonCommands>` ekleyin. Hedefin adını bu listeye eklemek, Python menüsüne **ekleyen addır.**

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Komutun içinde tanımlananlardan önce görünmesini görmek `$(PythonCommands)` için, bunları bu belirtecin önünde yer alır.

1. Proje dosyasını kaydedin, Visual Studio açın ve istendiğinde projeyi yeniden yükleyin. Ardından **Python-CustomCommands projesine sağ tıklayın ve** **Python'ı seçin.** Menüde Başlangıç dosyasını **çalıştır öğesini** görüyor olun. Menü öğesini görmüyorsanız, öğeye adın `<PythonCommands>` eklenmiştir. Ayrıca bu [makalenin devamlarında](#troubleshooting) sorun giderme makalesine bakın.

    ![Python bağlam alt menüsü üzerinde görünen özel komut](media/custom-commands-walkthrough-menu-item.png)

1. Başlangıç dosyasını **çalıştır komutunu seçin.** Devam etmek için  Hello özel komutları metninin ve ardından Herhangi bir tuşa basın metninin yer alan bir komut **penceresi görüntülenir.**  Pencereyi kapatmak için bir tuşa basın.

    ![Konsol penceresinde özel komut çıktısı](media/custom-commands-walkthrough-console.png)

1. Proje dosyasıyla düzenleyiciye geri dönüp özniteliğinin değerini `ExecuteIn` olarak `output` değiştirebilirsiniz. Dosyayı kaydedin, Visual Studio'a geçiş yapma, projeyi yeniden yükleme ve komutu yeniden çağırma. Bu kez, programın çıkışını Visual Studio **penceresinde** görebilirsiniz:

    ![Çıkış penceresinde özel komut çıktısı](media/custom-commands-walkthrough-output-window.png)

1. Daha fazla komut eklemek için, her komut için uygun bir öğe tanımlayın, özellik grubuna hedefin adını ekleyin ve `<Target>` `<PythonCommands>` Visual Studio.

>[!Tip]
> gibi proje özelliklerini kullanan bir komutu çağırırsanız ve belirteci tanımlanmamış olduğundan komut başarısız olursa, Visual Studio projeyi yeniden yükleyene kadar komutu devre dışı `($StartupFile)` bıraktır. Ancak, özelliği tanımlayarak projede değişiklik yapmak bu komutların durumunu yenilemez, bu nedenle yine de böyle durumlarda projeyi yeniden yüklemeniz gerekir.

## <a name="command-target-structure"></a>Komut hedefi yapısı

Öğesinin genel `<Target>` biçimi aşağıdaki sahte kodda gösterilir:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Öznitelik değerlerde proje özelliklerine veya ortam değişkenlerine başvurmak için ve gibi bir `$()` belirteç içindeki adı `$(StartupFile)` `$(MSBuildProjectDirectory)` kullanın. Daha fazla bilgi için [bkz. MSBuild.](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Hedef öznitelikler

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Ad | Yes | Visual Studio projesinde komutun tanımlayıcısı. Komutun `<PythonCommands>` Python altmenüsnde görünmesi için bu ad özellik grubuna eklenmiştir. |
| Etiketle | Yes | Python alt menüsünde görünen kullanıcı arabirimi görünen adı. |
| Döndürülenler | Yes | Hedefi komut `@(Commands)` olarak tanımlayan içermesi gerekir. |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem öznitelikleri

Tüm öznitelik değerleri büyük/büyük/büyük harfe duyarlı değildir.

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Targettype | Yes | Target özniteliğinin ne içerdiğini ve Arguments özniteliğiyle birlikte nasıl kullanıla olduğunu belirtir:<ul><li>**yürütülebilir:** Doğrudan komut satırına girilir gibi, Değeri Bağımsız Değişkenler'e ek olarak Target içinde adlı yürütülebilir dosyayı çalıştırın. Değerin bağımsız değişkenler olmadan yalnızca bir program adı içermesi gerekir.</li><li>**script:** *python.exe* dosya adı ile birlikte, ardından Bağımsız Değişkenler'de değeriyle birlikte çalıştırın.</li><li>**module:** Target içinde modül adını ve ardından `python -m` Bağımsız Değişkenler'de değerini çalıştırın.</li><li>**code:** Target içinde yer alan satır içi kodu çalıştırın. Bağımsız Değişkenler değeri yoksayılır.</li><li>**pip:** Target içinde komutuyla, ardından Bağımsız Değişkenler ile çalıştırın; ExecuteIn "output" olarak ayarlanır, ancak pip komutu varsayıyor ve paket adı olarak `pip` `install` Target'ı kullanıyor.</li></ul> |
| Hedef | Yes | TargetType'a bağlı olarak, kullanmak üzere dosya adı, modül adı, kod veya pip komutu. |
| Bağımsız değişkenler | İsteğe Bağlı | Hedefe vermek için bağımsız değişken dizesini (varsa) belirtir. TargetType olduğunda `script` , bağımsız değişkenlerin *python.exe* değil Python programına verildiğini unutmayın. TargetType için yok sayıldı `code` . |
| Executeın | Yes | Komutun çalıştırılacağı ortamı belirtir:<ul><li>**konsol**: (varsayılan) hedefi ve bağımsız değişkenleri doğrudan komut satırına girilmiş gibi çalıştırır. Hedef çalışırken bir komut penceresi görünür, sonra otomatik olarak kapatılır.</li><li>**consolepause**: konsol ile aynı, ancak pencereyi kapatmadan önce bir KeyPress için bekler.</li><li>**Çıkış**: hedefi çalıştırır ve sonuçları Visual Studio **çıktı** penceresinde görüntüler. TargetType, "pıp" ise, Visual Studio paket adı olarak hedefi kullanır ve bağımsız değişkenleri ekler.</li><li>**REPL**: [Python etkileşimli](python-interactive-repl-in-visual-studio.md) penceresinde hedefi çalıştırır; Pencerenin başlığı için isteğe bağlı görünen ad kullanılır.</li><li>**hiçbiri**: konsoluyla aynı şekilde davranır.</li></ul>|
| Başlangıç | İsteğe Bağlı | Komutun çalıştırılacağı klasör. |
| ErrorRegex<br>WarningRegEx | İsteğe Bağlı | Yalnızca ExecuteIn olduğunda kullanılır `output` . her iki değer de, **Hata Listesi** penceresinde hata ve uyarıları göstermek için komut çıkışını Visual Studio çözümleyen bir normal ifade belirtir. Belirtilmemişse, komut **hata listesi** penceresini etkilemez. Visual Studio beklediği hakkında daha fazla bilgi için bkz. [adlandırılmış yakalama grupları](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | İsteğe Bağlı | [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (Pip.readthedocs.io) ile aynı biçimi kullanan komuta ait paket gereksinimlerinin bir listesi. Örneğin, **Pylınt komutunu çalıştırın** , örneğin belirtir `pylint>=1.0.0` . komutu çalıştırmadan önce, Visual Studio listedeki tüm paketlerin yüklendiğini denetler. Visual Studio eksik paketleri yüklemek için pıp kullanır. |
| Ortam | İsteğe Bağlı | Komutu çalıştırmadan önce tanımlanacak ortam değişkenleri dizesi. Her değişken, formunu \<NAME> = \<VALUE> noktalı virgülle ayırarak birden çok değişken ile kullanır. Birden çok değeri olan bir değişken, ' NAME = DEĞER1; içinde olduğu gibi tek veya çift tırnak içinde bulunmalıdır. DEĞER2 '. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Normal ifadeler için adlandırılmış yakalama grupları

bir komutun çıktısından hata ve uyarı ayrıştırılırken Visual Studio, `ErrorRegex` ve değerlerindeki normal ifadelerin `WarningRegex` aşağıdaki adlandırılmış grupları kullanmasını bekliyor:

- `(?<message>...)`: Hatanın metni
- `(?<code>...)`: Hata kodu
- `(?<filename>...)`: Hatanın bildirildiği dosyanın adı
- `(?<line>...)`: Dosyadaki hatanın bildirildiği konumun satır numarası.
- `(?<column>...)`: Dosyadaki hatanın bildirildiği konumun sütun numarası.

Örneğin, PyLint aşağıdaki biçimde uyarılar üretir:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Visual Studio, bu uyarılardan doğru bilgileri ayıklamasını ve **Hata Listesi** penceresinde göstermesini sağlamak için, `WarningRegex` **pylınt komutunu çalıştır** komutunun değeri aşağıdaki gibidir:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

( `msg_id` Değerde gerçekten olması gerektiğini unutmayın `code` , bkz. [sorun 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Özel komutlarla bir. targets dosyası oluşturma

Bir proje dosyasında özel komutların tanımlanması, bunları yalnızca o proje dosyası için kullanılabilir hale getirir. Komutları birden fazla proje dosyasında kullanmak için, bunun yerine `<PythonCommands>` özellik grubunu ve tüm `<Target>` öğelerinizi bir *. targets* dosyasında tanımlarsınız. Daha sonra bu dosyayı tekil proje dosyalarına aktarırsınız.

*. Targets* dosyası şu şekilde biçimlendirilir:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Bir *. targets* dosyasını bir projeye yüklemek için, öğesini `<Import Project="(path)">` öğesi içinde bir yere yerleştirin `<Project>` . Örneğin, projenizdeki bir *hedef* alt klasörde *customcommands. targets* adlı bir dosyanız varsa, aşağıdaki kodu kullanın:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> *. Targets* dosyasını her değiştirdiğinizde yalnızca projenin kendisini değil, bir projeyi içeren *çözümü* yeniden yüklemeniz gerekir.

## <a name="example-commands"></a>Örnek komutlar

### <a name="run-pylint-module-target"></a>PyLint (modül hedefi) Çalıştır

Aşağıdaki kod, *Microsoft. PythonTools. targets* dosyasında görünür:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Belirli bir paket (PIP hedefi) ile PIP yüklemeyi Çalıştır

Aşağıdaki komut `pip install my-package` **Çıkış** penceresinde çalışır. Bir paket geliştirirken ve yüklemesini sınarken bu tür bir komutu kullanabilirsiniz. Hedefin, kullanırken kabul edilen komutu yerine paket adını içerdiğini unutmayın `install` `ExecuteIn="output"` .

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Eski PIP paketlerini göster (PIP hedefi)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Consolepause ile yürütülebilir dosya çalıştırma

Aşağıdaki komut, yalnızca `where` proje klasöründen başlayarak Python dosyalarını göstermek için çalışır:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Sunucu Çalıştır ve hata ayıklama sunucusu komutlarını çalıştır

Web projeleri için **sunucu Başlat** ve **hata ayıklama sunucu** komutlarının nasıl tanımlandığını araştırmak için [Microsoft. PythonTools. Web. targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub) inceleyin.

### <a name="install-package-for-development"></a>Geliştirme için paketi yükler

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) öğesinden, izin ile birlikte kullanılır.*

### <a name="generate-windows-installer"></a>Windows yükleyicisi oluştur

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) öğesinden, izin ile birlikte kullanılır.*

### <a name="generate-wheel-package"></a>Tekerlek paketi oluştur

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) öğesinden, izin ile birlikte kullanılır.*

## <a name="troubleshooting"></a>Sorun giderme

### <a name="message-the-project-file-could-not-be-loaded"></a>İleti: "proje dosyası yüklenemedi"

Proje dosyasında söz dizimi hatalarının olduğunu gösterir. İleti, satır numarası ve karakter konumu ile belirli bir hatayı içerir.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Konsol penceresi komut çalıştırıldıktan sonra hemen kapanır

`ExecuteIn="consolepause"`Yerine kullanın `ExecuteIn="console"` .

### <a name="command-does-not-appear-on-the-menu"></a>Komut menüde görünmüyor

Komutun özellik grubuna dahil edilip edilmediğini `<PythonCommands>` ve komut listesindeki adın öğesinde belirtilen adla eşleşip eşleşmediğini denetleyin `<Target>` .

Örneğin, aşağıdaki öğelerde, özellik grubundaki "örnek" adı, hedefteki "ExampleCommand" adıyla eşleşmez. Visual Studio "Example" adlı bir komut bulmadığından hiçbir komut görüntülenmez. Komut listesindeki "ExampleCommand" komutunu kullanın ya da hedefin adını yalnızca "örnek" olarak değiştirin.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>İleti: "çalışırken bir hata oluştu \<command name> . Komut \<target-name> projeden alınamadı. "

Veya öğelerinin içeriğinin yanlış olduğunu gösterir `<Target>` `<CreatePythonCommandItem>` . Olası nedenler şunlardır:

- Gerekli `Target` öznitelik boş.
- Gerekli `TargetType` öznitelik boş veya tanınmayan bir değer içeriyor.
- Gerekli `ExecuteIn` öznitelik boş veya tanınmayan bir değer içeriyor.
- `ErrorRegex` veya `WarningRegex` ayarı olmadan belirtilir `ExecuteIn="output"` .
- Öğesinde tanınmayan öznitelikler var. Örneğin, `Argumnets` yerine (yanlış yazılmış) kullanmış olabilirsiniz `Arguments` .

Tanımlı olmayan bir özelliğe başvurursanız, öznitelik değerleri boş olabilir. Örneğin, belirtecini kullanırsanız `$(StartupFile)` ancak projede hiç başlangıç dosyası tanımlanmamışsa, belirteç boş bir dizeye dönüşür. Böyle durumlarda, varsayılan bir değer tanımlamak isteyebilirsiniz. Örneğin, proje özelliklerinde bir sunucu başlangıç dosyası belirtmediyse, **Sunucu Çalıştır** ve **hata ayıklama sunucusu Çalıştır** , *Manage.py* , Flask ve docgo proje şablonlarında varsayılan olarak

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio, komutu çalıştırırken yanıt vermeyi ve kilitlenmeleri durduruyor

büyük olasılıkla, ile bir konsol komutu çalıştırmaya çalışıyoruz `ExecuteIn="output"` , bu durumda Visual Studio çıktıyı ayrıştırmaya çalışırken kilitlenme olabilir. Bunun yerine `ExecuteIn="console"` kullanın. (Bkz. [sorun 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Yürütülebilir komut "iç veya dış komut, çalıştırılabilir program veya toplu iş dosyası olarak tanınmıyor"

Kullanırken `TargetType="executable"` , içindeki değeri `Target` *yalnızca* *Python* veya *python.exe* gibi herhangi bir bağımsız değişken olmadan program adı olmalıdır. Bağımsız değişkenleri özniteliğine `Arguments` taşıma.
