---
title: Python projeleri için özel menü komutlarını tanımlama
description: Proje ve hedef dosyalarını düzenleyerek yürütülebilir programları, betikleri, modülleri, satır içi kod parçacıklarını ve PIP 'yi çağırmak için Visual Studio 'daki Python proje bağlam menüsüne özel komutlar ekleyebilirsiniz.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e9e7fe418528bb888672b1b73d421d811b9e69e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386991"
---
# <a name="define-custom-commands-for-python-projects"></a>Python projeleri için özel komutlar tanımlama

Python projelerinizle çalışma sürecinde, belirli betikleri veya modülleri çalıştırmak, PIP komutlarını çalıştırmak veya başka bir rastgele aracı çalıştırmak için bir komut penceresine geçiş yapmayı fark edebilirsiniz. İş akışınızı geliştirmek için Python proje bağlam menüsündeki **Python** alt menüsüne özel komutlar ekleyebilirsiniz. Bu komutlar, bir konsol penceresinde veya Visual Studio **çıktı** penceresinde çalıştırılabilir. Ayrıca, Visual Studio 'Nun komut çıktısından hataların ve uyarıların nasıl ayrıştıralınacağını bildirmek için normal ifadeler de kullanabilirsiniz.

Varsayılan olarak, bu menü yalnızca tek **Run Pylınt** komutunu içerir:

![Bir projenin bağlam menüsündeki Python alt menüsünün varsayılan görünümü](media/custom-commands-default-menu.png)

Özel komutlar aynı bağlam menüsünde görünür. Özel komutlar bir proje dosyasına doğrudan eklenir ve burada bu proje için geçerlidir. Ayrıca, birden çok proje dosyasına kolayca içeri aktarılabilen bir *. targets* dosyasında özel komutlar tanımlayabilirsiniz.

Visual Studio 'daki belirli Python proje şablonları, kendi *. targets* dosyasını kullanarak kendi özel komutlarını zaten ekler. Örneğin, şişe Web projesi ve Flask Web projesi şablonlarının ikisi de iki komut ekler, **sunucuyu başlatın** ve **hata ayıklama sunucusu başlatır**. Docgo Web projesi şablonu aynı komutları ve çok daha fazlasını ekler:

![Docgo projesinin bağlam menüsündeki Python alt menüsünün görünümü](media/custom-commands-django-menu.png)

Her özel komut bir Python dosyası, bir Python modülü, satır içi Python kodu, rastgele yürütülebilir veya bir PIP komutu başvurabilir. Ayrıca, komutun nasıl ve nerede çalışacağını de belirtebilirsiniz.

> [!Tip]
> Bir metin düzenleyicisinde proje dosyasında her değişiklik yaptığınızda, bu değişiklikleri uygulamak için projeyi Visual Studio 'ya yeniden yüklemeniz gerekir. Örneğin, projenin bağlam menüsünde görünmesi için bu komutlar için özel komut tanımları ekledikten sonra bir projeyi yeniden yüklemeniz gerekir.
>
> Bildiğiniz gibi, Visual Studio proje dosyasını doğrudan düzenlemek için bir yol sağlar. Önce proje dosyasına sağ tıklayıp **Projeyi Kaldır**' ı seçtikten sonra yeniden sağ tıklayıp **Düzenle \<project-name> ** ' yi seçerek projeyi Visual Studio düzenleyicisinde açın. Daha sonra düzenlemeler yapıp kaydeder, daha sonra projeye sağ tıklayıp projeyi **yeniden yükle**' yi seçtiğinizde proje dosyasını düzenleyicide kapatmayı onaylamanızı de istenir.
>
> Ancak, özel bir komut geliştirilirken, tüm bu tıklama sıkıcı hale gelebilir. Daha verimli bir iş akışı için, projeyi Visual Studio 'Ya yükleyin ve ayrıca *. pyproj* dosyasını ayrı bir düzenleyicide (örneğin, Visual Studio 'nun başka bir örneği, Visual Studio Code, Not defteri, vb.) birlikte açın. Düzenleyicide yaptığınız değişiklikleri kaydettiğinizde ve Visual Studio 'ya geçtiğinizde, Visual Studio değişiklikleri algılar ve projeyi yeniden yükleyip yükleyemeyeceğini sorar (**Proje \<name> ortamın dışında değiştirilmiş demektir.**). **Yeniden yükle** ' yi seçtiğinizde değişiklikleriniz hemen tek bir adımda uygulanır.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>İzlenecek yol: proje dosyasına bir komut ekleme

Bu bölümde, özel komutlar hakkında bilgi edinmek için, bir projenin başlangıç dosyasını doğrudan *python.exe*kullanarak çalıştıran basit bir örnek gösterilmektedir. (Böyle bir komut, **hata ayıklama**  >  kullanma ile etkin şekilde aynıdır **Hata ayıklama olmadan Başlat**.)

1. **Python uygulama** şablonunu kullanarak "Python-customcommands" adlı yeni bir proje oluşturun. (Bkz. hızlı başlangıç: işlemden daha önce alışkın değilseniz yönergeler için [bir şablondan Python projesi oluşturma](quickstart-02-python-in-visual-studio-project-from-template.md) .)

1. *Python_CustomCommands. Kopyala*içinde kodu ekleyin `print("Hello custom commands")` .

1. **Çözüm Gezgini**' de projeye sağ tıklayın, **Python**' ı seçin ve alt menüde görünen tek komutun **Pylint ' i çalıştırdığına**dikkat edin. Özel komutlarınız aynı alt menüde görünür.

1. Giriş bölümünde önerildiği gibi, farklı bir metin düzenleyicisinde *Python-CustomCommands. pyproj* öğesini açın. Ardından, dosyanın sonuna aşağıdaki satırları, kapanış içinde hemen ekleyin `</Project>` ve dosyayı kaydedin.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Visual Studio 'ya geri dönün ve dosya değişikliğini istediğinizde, **yeniden yükle** ' yi seçin. Ardından, eklediğiniz satırlar yalnızca Pylınt komutunu içeren varsayılan özellik grubunu çoğaltdığından, **PyLint çalıştırma** hâlâ burada gösterilen tek öğe olduğunu görmek için **Python** menüsünü yeniden denetleyin `<PythonCommands>` .

1. Proje dosyası ile düzenleyiciye geçiş yapın ve `<Target>` öğesinden sonra aşağıdaki tanımı ekleyin `<PropertyGroup>` . Bu makalenin ilerleyen kısımlarında açıklandığı gibi, bu `Target` öğe, bir konsol penceresinde *python.exe* kullanarak başlangıç dosyasını ("startupfile" özelliği tarafından tanımlanır) çalıştırmak için özel bir komut tanımlar. Özniteliği, `ExecuteIn="consolepause"` kapatmadan önce bir tuşa basmanız için bekleyen bir konsol kullanır.

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

1. `Name` `<PythonCommands>` Daha önce eklenen özellik grubuna hedef özniteliğinin değerini ekleyin, böylece öğe aşağıdaki koda benzer şekilde görünür. Hedefin adını bu listeye eklemek, **Python** menüsüne ne ekler.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Komutunuz içinde tanımlanmadan önce görünmesini istiyorsanız `$(PythonCommands)` , bu belirteci önce koyun.

1. Proje dosyasını kaydedin, Visual Studio 'ya geçin ve istendiğinde projeyi yeniden yükleyin. Ardından **Python-CustomCommands** projesine sağ tıklayın ve **Python**' ı seçin. Menüde bir **başlangıç dosyası Çalıştır** öğesi görmeniz gerekir. Menü öğesini görmüyorsanız, adı öğesine eklediniz seçeneğini işaretleyin `<PythonCommands>` . Ayrıca, bu makalenin ilerleyen bölümlerinde [sorun giderme](#troubleshooting) bölümüne bakın.

    ![Python bağlam alt menüsünde görünen özel komut](media/custom-commands-walkthrough-menu-item.png)

1. **Başlangıç dosyasını çalıştır** komutunu seçin ve ardından **Merhaba özel komutları** ve ardından **devam etmek için herhangi bir tuşa basarak**bir komut penceresi görürsünüz.  Pencereyi kapatmak için bir tuşa basın.

    ![Konsol penceresinde özel komut çıkışı](media/custom-commands-walkthrough-console.png)

1. Proje dosyası ile düzenleyiciye geri dönün ve `ExecuteIn` özniteliğinin değerini olarak değiştirin `output` . Dosyayı kaydedin, Visual Studio 'ya geçin, projeyi yeniden yükleyin ve komutu yeniden çağırın. Bu zaman, Visual Studio 'nun **Çıkış** penceresinde programın çıkışının göründüğünü görürsünüz:

    ![Çıkış penceresinde özel komut çıkışı](media/custom-commands-walkthrough-output-window.png)

1. Daha fazla komut eklemek için, `<Target>` her komut için uygun bir öğe tanımlayın, hedefin adını `<PythonCommands>` özellik grubuna ekleyin ve Visual Studio 'da projeyi yeniden yükleyin.

>[!Tip]
> Proje özellikleri kullanan bir komutu çağırdıysanız (gibi) `($StartupFile)` ve belirteç tanımsız olduğu için komut başarısız olursa, projeyi yeniden yükleyene kadar, Visual Studio komutu devre dışı bırakır. Projede, özelliği tanımlayacak değişiklikler yapılıyor, ancak bu komutların durumunu yenilemez, bu nedenle yine de projeyi bu gibi durumlarda yeniden yüklemeniz gerekir.

## <a name="command-target-structure"></a>Komut hedefi yapısı

Öğesinin genel formu `<Target>` aşağıdaki sözde kodda gösterilmiştir:

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

Öznitelik değerlerinde proje özelliklerine veya ortam değişkenlerine başvurmak için, ve gibi bir belirteç içindeki adı kullanın `$()` `$(StartupFile)` `$(MSBuildProjectDirectory)` . Daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Hedef öznitelikleri

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Ad | Yes | Visual Studio projesi içindeki komut için tanımlayıcı. Bu ad, `<PythonCommands>` komutun Python alt menüsünde görünmesi için özellik grubuna eklenmelidir. |
| Etiketle | Yes | Python alt menüsünde görünen kullanıcı arabirimi görünen adı. |
| Döndürülenler | Yes | `@(Commands)`, Hedefi bir komut olarak tanıtan içermelidir. |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem öznitelikleri

Tüm öznitelik değerleri büyük/küçük harfe duyarlıdır.

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Öğesi | Yes | Target özniteliğinin neleri içerdiğini ve bağımsız değişkenler özniteliğiyle birlikte nasıl kullanıldığını belirtir:<ul><li>**yürütülebilir**: hedef içinde adlı yürütülebilir dosyayı, doğrudan komut satırına girildiği gibi bağımsız değişkenlerde değeri ekleyerek çalıştırın. Değer yalnızca bağımsız değişken içermeyen bir program adı içermelidir.</li><li>**betik**: *python.exe* , hedefte dosya adı Ile ve ardından bağımsız değişkenlerdeki değerle çalıştırın.</li><li>**Modül**: `python -m` sonra, hedefteki modül adı ve ardından bağımsız değişkenlerde değeri ile çalıştırın.</li><li>**kod**: hedefte bulunan satır içi kodu çalıştırın. Bağımsız değişkenler değeri yok sayılır.</li><li>**PIP**: `pip` target içindeki komutla, sonra bağımsız değişkenler Ile çalıştırın; executeın "output" olarak ayarlanır, ancak, PIP komutu kabul eder `install` ve paket adı olarak hedefi kullanır.</li></ul> |
| Hedef | Yes | TargetType öğesine bağlı olarak kullanılacak dosya adı, modül adı, kod veya PIP komutu. |
| Arguments | İsteğe Bağlı | Hedefe verilecek bağımsız değişkenlerin (varsa) bir dizesini belirtir. TargetType olduğunda `script` , bağımsız değişkenlerin *python.exe*değil Python programına verildiğini unutmayın. TargetType için yok sayıldı `code` . |
| Executeın | Yes | Komutun çalıştırılacağı ortamı belirtir:<ul><li>**konsol**: (varsayılan) hedefi ve bağımsız değişkenleri doğrudan komut satırına girilmiş gibi çalıştırır. Hedef çalışırken bir komut penceresi görünür, sonra otomatik olarak kapatılır.</li><li>**consolepause**: konsol ile aynı, ancak pencereyi kapatmadan önce bir KeyPress için bekler.</li><li>**Çıkış**: hedefi çalıştırır ve sonuçları Visual Studio 'daki **Çıkış** penceresinde görüntüler. TargetType, "PIP" ise, Visual Studio paket adı olarak hedefi kullanır ve bağımsız değişkenleri ekler.</li><li>**REPL**: [Python etkileşimli](python-interactive-repl-in-visual-studio.md) penceresinde hedefi çalıştırır; Pencerenin başlığı için isteğe bağlı görünen ad kullanılır.</li><li>**hiçbiri**: konsoluyla aynı şekilde davranır.</li></ul>|
| Başlangıç | İsteğe Bağlı | Komutun çalıştırılacağı klasör. |
| ErrorRegex<br>WarningRegEx | İsteğe Bağlı | Yalnızca ExecuteIn olduğunda kullanılır `output` . Her iki değer de, Visual Studio 'Nun **hata listesi** penceresinde hata ve uyarıları göstermek için komut çıkışını ayrıştırmak için bir normal ifade belirtir. Belirtilmemişse, komut **hata listesi** penceresini etkilemez. Visual Studio 'Nun beklediği hakkında daha fazla bilgi için bkz. [adlandırılmış yakalama grupları](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | İsteğe Bağlı | [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (Pip.readthedocs.io) ile aynı biçimi kullanan komuta ait paket gereksinimlerinin bir listesi. Örneğin, **Pylınt komutunu çalıştırın** , örneğin belirtir `pylint>=1.0.0` . Komutu çalıştırmadan önce, Visual Studio listedeki tüm paketlerin yüklü olduğunu denetler. Visual Studio eksik paketleri yüklemek için PIP kullanır. |
| Ortam | İsteğe Bağlı | Komutu çalıştırmadan önce tanımlanacak ortam değişkenleri dizesi. Her değişken, formunu \<NAME> = \<VALUE> noktalı virgülle ayırarak birden çok değişken ile kullanır. Birden çok değeri olan bir değişken, ' NAME = DEĞER1; içinde olduğu gibi tek veya çift tırnak içinde bulunmalıdır. DEĞER2 '. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Normal ifadeler için adlandırılmış yakalama grupları

Bir komutun çıktısından hata ve uyarı ayrıştırılırken, Visual Studio, `ErrorRegex` ve değerlerindeki normal ifadelerin `WarningRegex` aşağıdaki adlandırılmış grupları kullanmasını bekler:

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

Visual Studio 'Nun bu tür uyarılardan doğru bilgileri ayıklamasını ve **hata listesi** penceresinde göstermesini sağlamak Için, `WarningRegex` **Pylınt komutunu çalıştır** komutunun değeri aşağıdaki gibidir:

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

Web projeleri için **sunucu Başlat** ve **hata ayıklama sunucu** komutlarının nasıl tanımlandığını araştırmak Için, [Microsoft. PythonTools. Web. targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub) ' ı inceleyin.

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

*[Fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) öğesinden, izin ile kullanılır.*

### <a name="generate-windows-installer"></a>Windows Installer oluştur

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

*[Fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) öğesinden, izin ile kullanılır.*

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

*[Fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) öğesinden, izin ile kullanılır.*

## <a name="troubleshooting"></a>Sorun giderme

### <a name="message-the-project-file-could-not-be-loaded"></a>İleti: "proje dosyası yüklenemedi"

Proje dosyasında söz dizimi hatalarının olduğunu gösterir. İleti, satır numarası ve karakter konumu ile belirli bir hatayı içerir.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Konsol penceresi komut çalıştırıldıktan sonra hemen kapanır

`ExecuteIn="consolepause"`Yerine kullanın `ExecuteIn="console"` .

### <a name="command-does-not-appear-on-the-menu"></a>Komut menüde görünmüyor

Komutun özellik grubuna dahil edilip edilmediğini `<PythonCommands>` ve komut listesindeki adın öğesinde belirtilen adla eşleşip eşleşmediğini denetleyin `<Target>` .

Örneğin, aşağıdaki öğelerde, özellik grubundaki "örnek" adı, hedefteki "ExampleCommand" adıyla eşleşmez. Visual Studio "example" adlı bir komut bulmadığından hiçbir komut görüntülenmez. Komut listesindeki "ExampleCommand" komutunu kullanın ya da hedefin adını yalnızca "örnek" olarak değiştirin.

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
- `ErrorRegex`veya `WarningRegex` ayarı olmadan belirtilir `ExecuteIn="output"` .
- Öğesinde tanınmayan öznitelikler var. Örneğin, `Argumnets` yerine (yanlış yazılmış) kullanmış olabilirsiniz `Arguments` .

Tanımlı olmayan bir özelliğe başvurursanız, öznitelik değerleri boş olabilir. Örneğin, belirtecini kullanırsanız `$(StartupFile)` ancak projede hiç başlangıç dosyası tanımlanmamışsa, belirteç boş bir dizeye dönüşür. Böyle durumlarda, varsayılan bir değer tanımlamak isteyebilirsiniz. Örneğin, proje özelliklerinde bir sunucu başlangıç dosyası belirtmediyse, **Sunucu Çalıştır** ve **hata ayıklama sunucusu Çalıştır** , *Manage.py* , Flask ve docgo proje şablonlarında varsayılan olarak

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Komutu çalıştırırken Visual Studio yanıt vermeyi ve kilitlenmeleri durduruyor

Büyük olasılıkla, ile bir konsol komutu çalıştırmaya çalışıyoruz `ExecuteIn="output"` , bu durumda Visual Studio çıktıyı ayrıştırmaya çalışırken kilitlenme olabilir. Bunun yerine `ExecuteIn="console"` kullanın. (Bkz. [sorun 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Yürütülebilir komut "iç veya dış komut, çalıştırılabilir program veya toplu iş dosyası olarak tanınmıyor"

Kullanırken `TargetType="executable"` , içindeki değeri `Target` *yalnızca* *Python* veya *python.exe* gibi herhangi bir bağımsız değişken olmadan program adı olmalıdır. Tüm bağımsız değişkenleri özniteliğe taşıyın `Arguments` .
