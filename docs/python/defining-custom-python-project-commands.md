---
title: Python projeleri için özel menü komutlarını tanımlama
description: proje ve hedef dosyalarını düzenleyerek yürütülebilir programları, betikleri, modülleri, satır içi kod parçacıklarını ve pıp 'yi çağırmak için Visual Studio ' deki Python projesi bağlam menüsüne özel komutlar ekleyebilirsiniz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628323"
---
# <a name="define-custom-commands-for-python-projects"></a>Python projeleri için özel komutlar tanımlama

Python projelerinizle çalışma sürecinde, belirli betikleri veya modülleri çalıştırmak, PIP komutlarını çalıştırmak veya başka bir rastgele aracı çalıştırmak için bir komut penceresine geçiş yapmayı fark edebilirsiniz. İş akışınızı geliştirmek için Python proje bağlam menüsündeki **Python** alt menüsüne özel komutlar ekleyebilirsiniz. bu komutlar, bir konsol penceresinde veya Visual Studio **çıkış** penceresinde çalıştırılabilir. ayrıca, komut çıktısından hataların ve uyarıların nasıl ayrıştıralınacağını Visual Studio söylemek için normal ifadeleri de kullanabilirsiniz.

Varsayılan olarak, bu menü yalnızca tek **Run Pylınt** komutunu içerir:

![Bir projenin bağlam menüsündeki Python alt menüsünün varsayılan görünümü](media/custom-commands-default-menu.png)

Özel komutlar aynı bağlam menüsünde görünür. Özel komutlar bir proje dosyasına doğrudan eklenir ve burada bu proje için geçerlidir. Ayrıca, birden çok proje dosyasına kolayca içeri aktarılabilen bir *. targets* dosyasında özel komutlar tanımlayabilirsiniz.

Visual Studio ' deki belirli Python proje şablonları, kendi *. targets* dosyasını kullanarak kendi özel komutlarını zaten ekleyin. örneğin, şişe web Project ve flask web Project şablonlarının her ikisi de iki komut ekler, **sunucuyu başlatın** ve **hata ayıklama sunucusunu başlatır**. docgo Web Project şablonu aynı komutları ve çok daha fazlasını ekler:

![Docgo projesinin bağlam menüsündeki Python alt menüsünün görünümü](media/custom-commands-django-menu.png)

Her özel komut bir Python dosyası, bir Python modülü, satır içi Python kodu, rastgele yürütülebilir veya bir PIP komutu başvurabilir. Ayrıca, komutun nasıl ve nerede çalışacağını de belirtebilirsiniz.

> [!Tip]
> bir metin düzenleyicisinde proje dosyasında her değişiklik yaptığınızda, bu değişiklikleri uygulamak için Visual Studio projeyi yeniden yüklemeniz gerekir. Örneğin, projenin bağlam menüsünde görünmesi için bu komutlar için özel komut tanımları ekledikten sonra bir projeyi yeniden yüklemeniz gerekir.
>
> bildiğiniz gibi Visual Studio proje dosyasını doğrudan düzenlemek için bir yol sağlar. önce proje dosyasına sağ tıklayıp **projeyi kaldır**' ı seçtikten sonra yeniden sağ tıklayıp **düzenle \<project-name>** ' yi seçerek projeyi Visual Studio düzenleyicisinde açın. Daha sonra düzenlemeler yapıp kaydeder, daha sonra projeye sağ tıklayıp projeyi **yeniden yükle**' yi seçtiğinizde proje dosyasını düzenleyicide kapatmayı onaylamanızı de istenir.
>
> Ancak, özel bir komut geliştirilirken, tüm bu tıklama sıkıcı hale gelebilir. daha verimli bir iş akışı için, projeyi Visual Studio yükleyin ve ayrıca *. pyproj* dosyasını ayrı bir düzenleyicide (örneğin başka bir Visual Studio, Visual Studio Code, Not Defteri, vb.) birlikte açın. düzenleyicide yaptığınız değişiklikleri kaydeder ve Visual Studio ' a geçiş yaptığınızda, Visual Studio değişiklikleri algılar ve projenin yeniden yüklenmesini isteyip istemediğinizi sorar (**proje \<name> ortamın dışında değiştirilmiş demektir.**). **Yeniden yükle** ' yi seçtiğinizde değişiklikleriniz hemen tek bir adımda uygulanır.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>İzlenecek yol: proje dosyasına bir komut ekleme

Bu bölümde, özel komutlar hakkında bilgi edinmek için, bir projenin başlangıç dosyasını doğrudan *python.exe* kullanarak çalıştıran basit bir örnek gösterilmektedir. (Böyle bir komut, **hata ayıklama**  >  kullanma ile etkin şekilde aynıdır **Hata ayıklama olmadan Başlat**.)

1. **Python uygulama** şablonunu kullanarak "Python-customcommands" adlı yeni bir proje oluşturun. (Bkz. hızlı başlangıç: işlemden daha önce alışkın değilseniz yönergeler için [bir şablondan Python projesi oluşturma](quickstart-02-python-in-visual-studio-project-from-template.md) .)

1. *Python_CustomCommands. Kopyala* içinde kodu ekleyin `print("Hello custom commands")` .

1. **Çözüm Gezgini**' de projeye sağ tıklayın, **Python**' ı seçin ve alt menüde görünen tek komutun **Pylint ' i çalıştırdığına** dikkat edin. Özel komutlarınız aynı alt menüde görünür.

1. Giriş bölümünde önerildiği gibi, farklı bir metin düzenleyicisinde *Python-CustomCommands. pyproj* öğesini açın. Ardından, dosyanın sonuna aşağıdaki satırları, kapanış içinde hemen ekleyin `</Project>` ve dosyayı kaydedin.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Visual Studio 'e dönün ve dosya değişikliğine ilişkin istemde bulunduğunda **yeniden yükle** ' yi seçin. Ardından, eklediğiniz satırlar yalnızca Pylınt komutunu içeren varsayılan özellik grubunu çoğaltdığından, **PyLint çalıştırma** hâlâ burada gösterilen tek öğe olduğunu görmek için **Python** menüsünü yeniden denetleyin `<PythonCommands>` .

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

1. proje dosyasını kaydedin, Visual Studio geçin ve istendiğinde projeyi yeniden yükleyin. Ardından **Python-CustomCommands** projesine sağ tıklayın ve **Python**' ı seçin. Menüde bir **başlangıç dosyası Çalıştır** öğesi görmeniz gerekir. Menü öğesini görmüyorsanız, adı öğesine eklediniz seçeneğini işaretleyin `<PythonCommands>` . Ayrıca, bu makalenin ilerleyen bölümlerinde [sorun giderme](#troubleshooting) bölümüne bakın.

    ![Python bağlam alt menüsünde görünen özel komut](media/custom-commands-walkthrough-menu-item.png)

1. **Başlangıç dosyasını çalıştır** komutunu seçin ve ardından **Merhaba özel komutları** ve ardından **devam etmek için herhangi bir tuşa basarak** bir komut penceresi görürsünüz.  Pencereyi kapatmak için bir tuşa basın.

    ![Konsol penceresinde özel komut çıkışı](media/custom-commands-walkthrough-console.png)

1. Proje dosyası ile düzenleyiciye geri dönün ve `ExecuteIn` özniteliğinin değerini olarak değiştirin `output` . dosyayı kaydedin, Visual Studio geçin, projeyi yeniden yükleyin ve komutu yeniden çağırın. bu zaman, programın çıkışının Visual Studio **çıkış** penceresinde göründüğünü görürsünüz:

    ![Çıkış penceresinde özel komut çıkışı](media/custom-commands-walkthrough-output-window.png)

1. Daha fazla komut eklemek için, `<Target>` her komut için uygun bir öğe tanımlayın, hedefin adını `<PythonCommands>` özellik grubuna ekleyin ve Visual Studio projeyi yeniden yükleyin.

>[!Tip]
> proje özellikleri kullanan bir komutu çağırdıysanız (gibi) `($StartupFile)` ve belirteç tanımsız olduğu için komut başarısız olursa, projeyi yeniden yükleyene kadar komutu devre dışı bırakır Visual Studio. Projede, özelliği tanımlayacak değişiklikler yapılıyor, ancak bu komutların durumunu yenilemez, bu nedenle yine de projeyi bu gibi durumlarda yeniden yüklemeniz gerekir.

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

Öznitelik değerlerinde proje özelliklerine veya ortam değişkenlerine başvurmak için, ve gibi bir belirteç içindeki adı kullanın `$()` `$(StartupFile)` `$(MSBuildProjectDirectory)` . daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

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
| Bağımsız değişkenler | İsteğe Bağlı | Hedefe verilecek bağımsız değişkenlerin (varsa) bir dizesini belirtir. TargetType olduğunda bağımsız değişkenlerin python programına verildiğini ve bu programa `script`python.exe. ** TargetType için `code` yoksayıldı. |
| ExecuteIn | Yes | Komutunun çalıştır çalıştırıla ortamlarını belirtir:<ul><li>**console**: (Varsayılan) Target ve bağımsız değişkenleri doğrudan komut satırına girilir gibi çalıştırır. Hedef çalışırken bir komut penceresi görüntülenir, ardından otomatik olarak kapatılır.</li><li>**consolepause:** Konsolla aynıdır, ancak pencereyi kapatmadan önce bir tuşa basın.</li><li>**output:** Target'i çalıştırır ve sonuçlarını çıkış **penceresinde** Visual Studio. TargetType "pip" ise, Visual Studio adı olarak Target'ı kullanır ve Bağımsız Değişkenleri ekler.</li><li>**repl:** Python Etkileşimli [penceresinde Hedefi](python-interactive-repl-in-visual-studio.md) çalıştırır; isteğe bağlı görünen ad, pencerenin başlığı için kullanılır.</li><li>**none:** konsol ile aynı şekilde davranır.</li></ul>|
| Başlangıç | İsteğe Bağlı | Komutunun çalıştırılalacak klasör. |
| ErrorRegex<br>WarningRegEx | İsteğe Bağlı | Yalnızca ExecuteIn olduğunda `output` kullanılır. Her iki değer de Hata Listesi penceresinde Visual Studio ve uyarıları göstermek için komut çıkışını ayrıştıran normal **bir ifade belirtir.** Belirtilmezse, komut Hata Listesi **penceresini etkilemez.** Neler beklediğiniz hakkında daha fazla Visual Studio için bkz. [Adlandırılmış yakalama grupları.](#named-capture-groups-for-regular-expressions) |
| RequiredPackages | İsteğe Bağlı | Komutla aynı biçimi kullanan komutun paket [](https://pip.pypa.io/en/stable/user_guide/#requirements-files) gereksinimlerinin listesirequirements.txt(pip.readthedocs.io). Run **PyLint** komutu, örneğin `pylint>=1.0.0` belirtir. komutunu çalıştırmadan önce Visual Studio tüm paketlerin yüklü olduğunu denetler. Visual Studio eksik paketleri yüklemek için pip kullanır. |
| Ortam | İsteğe Bağlı | Komutu çalıştırmadan önce tanımladığınız ortam değişkenleri dizesi. Her değişken, noktalı \<NAME> = \<VALUE> virgülle ayrılmış birden çok değişken içeren formu kullanır. Birden çok değere sahip bir değişken, 'NAME=VALUE1' gibi tek veya çift tırnak içinde yer alınarak; VALUE2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Normal ifadeler için adlandırılmış yakalama grupları

Bir komutun çıkışından hata ve uyarıları ayrıştırıyorsanız, Visual Studio ve değerlerinde normal ifadelerin aşağıdaki adlandırılmış grupları `ErrorRegex` `WarningRegex` kullanmasını bekler:

- `(?<message>...)`: Hatanın metni
- `(?<code>...)`: Hata kodu
- `(?<filename>...)`: Hatanın raporlandığı dosyanın adı
- `(?<line>...)`: Hatanın raporlandığı dosya konumun satır numarası.
- `(?<column>...)`: Hatanın raporlandığı dosyadaki konumun sütun numarası.

Örneğin, PyLint aşağıdaki forma uyarı üretir:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Bu Visual Studio doğru bilgileri ayıklamasına ve Bunları Hata Listesi  penceresinde göstermesine izin vermek `WarningRegex` **için, Pylint** Komutunu Çalıştır komutunun değeri aşağıdaki gibidir:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Değerde `msg_id` aslında olması gerektiğini `code` unutmayın, [bkz. Sorun 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Özel komutlarla bir .targets dosyası oluşturma

Bir proje dosyasında özel komutlar tanımlayarak bunları yalnızca bu proje dosyasında kullanabilirsiniz. Komutları birden çok proje dosyasında kullanmak için, bunun yerine özellik grubunu ve bir .targets dosyasındaki `<PythonCommands>` `<Target>` tüm *öğelerinizi tanımlarsınız.* Ardından bu dosyayı tek tek proje dosyalarına içeri aktarabilirsiniz.

*.targets* dosyası aşağıdaki gibi biçimlendirildi:

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

Projeye *bir .targets* dosyası yüklemek için öğenin herhangi `<Import Project="(path)">` bir yerine bir öğe `<Project>` yer. Örneğin, projenizin *targets* alt klasörü içinde *CustomCommands.targets* adlı bir dosyanız varsa aşağıdaki kodu kullanın:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> *.targets dosyasını her* değiştiriyorsanız, yalnızca  projenin kendisini değil, bir projeyi içeren çözümü yeniden yükleyebilirsiniz.

## <a name="example-commands"></a>Örnek komutlar

### <a name="run-pylint-module-target"></a>PyLint'i çalıştırma (modül hedefi)

Aşağıdaki kod *Microsoft.PythonTools.targets dosyasında* görünür:

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

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Belirli bir paketle pip yüklemesi çalıştırma (pip hedefi)

Aşağıdaki komut Çıktı `pip install my-package` penceresinde çalışır.  Paket geliştirerek yüklemesini test etmek için böyle bir komut kullanabilirsiniz. Target komutunun yerine paket adını içerdiğini ve bu ad, kullanırken `install` `ExecuteIn="output"` varsayılır.

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

### <a name="show-outdated-pip-packages-pip-target"></a>Outdated pip packages (pip target) gösterme

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

### <a name="run-an-executable-with-consolepause"></a>Konsolpause ile yürütülebilir dosya çalıştırma

Aşağıdaki komut yalnızca proje `where` klasöründen başlayarak Python dosyalarını göstermek için çalışır:

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

### <a name="run-server-and-run-debug-server-commands"></a>Sunucuyu çalıştırma ve hata ayıklama sunucusu komutlarını çalıştırma

Web projeleri için **Sunucuyu başlat ve** Hata ayıklama **sunucusu** komutlarını başlat komutlarının nasıl tanımlandığı hakkında bilgi için [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Geliştirme paketi yükleme

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

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izinle birlikte kullanılır.*

### <a name="generate-windows-installer"></a>Yükleyiciyi Windows oluşturma

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

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izinle birlikte kullanılır.*

### <a name="generate-wheel-package"></a>Tekerlek paketi oluşturma

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

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izinle birlikte kullanılır.*

## <a name="troubleshooting"></a>Sorun giderme

### <a name="message-the-project-file-could-not-be-loaded"></a>İleti: "Proje dosyası yüklenemedi"

Proje dosyasında söz dizimi hataları olduğunu gösterir. İleti, satır numarası ve karakter konumu ile belirli bir hatayı içerir.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Komut çalıştır alındıktan hemen sonra konsol penceresi kapanır

yerine `ExecuteIn="consolepause"` `ExecuteIn="console"` kullanın.

### <a name="command-does-not-appear-on-the-menu"></a>Komut menüde görünmüyor

Komutun özellik grubuna dahil olduğunu ve komut listesinde yer alan adın öğesinde belirtilen `<PythonCommands>` adla eşle eşle eşle olduğunu `<Target>` kontrol edin.

Örneğin, aşağıdaki öğelerde, özellik grubunda yer alan "Örnek" adı hedefte "ExampleCommand" adıyla eşleşmez. Visual Studio "Example" adlı bir komut bulamadı, bu nedenle hiçbir komut yok. Komut listesinde "ExampleCommand" kullanın veya hedefin adını yalnızca "Örnek" olarak değiştirebilirsiniz.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>İleti: "çalışırken bir hata \<command name> oluştu. Projeden komut \<target-name> alanamadı."

veya öğelerinin `<Target>` içeriğinin `<CreatePythonCommandItem>` yanlış olduğunu gösterir. Olası nedenler şunlardır:

- Gerekli `Target` öznitelik boş.
- Gerekli `TargetType` öznitelik boş veya tanınmayan bir değer içeriyor.
- Gerekli `ExecuteIn` öznitelik boş veya tanınmayan bir değer içeriyor.
- `ErrorRegex` veya `WarningRegex` ayarı olmadan `ExecuteIn="output"` belirtilir.
- Tanınmayan öznitelikler öğesinde mevcuttur. Örneğin yerine kullanılmış `Argumnets` (yanlış yazılmış) `Arguments` olabilir.

Tanımlanmamış bir özelliğe başvurursanız öznitelik değerleri boş olabilir. Örneğin, belirteci kullanırsanız ancak projede hiçbir başlangıç dosyası tanımlanmamışsa, `$(StartupFile)` belirteç boş bir dizeye çözümler. Böyle durumlarda, varsayılan bir değer tanımlamak istiyor olabilir. Örneğin, Bottle, Flask ve Django proje şablonlarında tanımlanan Sunucu çalıştır ve Hata ayıklamayı çalıştır sunucu komutları, proje özelliklerinde başka bir sunucu başlangıç dosyası belirtilmemişse varsayılan olarak *manage.py* olarak kullanılır.  

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio yanıt vermiyor ve komutu çalıştırıyorsa kilitleniyor

büyük olasılıkla ile bir konsol komutu çalıştırmaya çalışıyorsanız, `ExecuteIn="output"` bu durumda Visual Studio ayrıştırmaya çalışırken başarısız olabilir. Bunun yerine `ExecuteIn="console"` kullanın. [(Bkz. Sorun 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Yürütülebilir komut "iç veya dış komut, çalıştırılabilir program veya toplu iş dosyası olarak tanınmıyor"

kullanırken, içinde değeri python veya yalnızca python gibi bağımsız değişkenler olmadan `TargetType="executable"` `Target` program adı *python.exe* gerekir.   Tüm bağımsız değişkenleri özniteliğe taşıyın `Arguments` .
