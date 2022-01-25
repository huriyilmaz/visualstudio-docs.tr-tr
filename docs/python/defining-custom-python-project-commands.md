---
title: Python projeleri için özel menü komutları tanımlama
description: Proje ve hedef dosyalarını düzenleyerek, yürütülebilir programları, betikleri, modülleri, satır içi kod parçacıklarını ve pip'i çağırmak için Visual Studio'daki Python proje bağlam menüsüne özel komutlar ekleyebilirsiniz.
ms.date: 01/18/2022
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 9152b3683362a5c0ceab158bbac3a74a5bd494a5
ms.sourcegitcommit: f81a8f381bcdbac96d112f815737ba1df55d97a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137667401"
---
# <a name="define-custom-commands-for-python-projects"></a>Python projeleri için özel komutlar tanımlama

Python projeleriniz ile çalışma sürecinde belirli betikleri veya modülleri çalıştırmak, pip komutlarını çalıştırmak veya başka bir rastgele araç çalıştırmak için bir komut penceresine geçiş yapabilirsiniz. İş akışınızı geliştirmek için Python projesi bağlam menüsünde **Python** alt menüsüne özel komutlar ekleyebilirsiniz. Bu komutlar bir konsol penceresinde veya Visual Studio **çalıştırabilirsiniz.** Ayrıca normal ifadeleri kullanarak komut çıkışından Visual Studio ve uyarıları nasıl ayrıştırabilirsiniz?

Varsayılan olarak, bu menü yalnızca tek bir **PyLint Çalıştır komutunu** içerir:

![Projenin bağlam menüsünde Python alt menüsünün varsayılan görünümü](media/custom-commands-default-menu.png)

Özel komutlar aynı bağlam menüsünde görünür. Özel komutlar doğrudan bir proje dosyasına eklenir ve bu komutlar tek tek projeye uygulanır. Ayrıca, birden çok proje dosyasına kolayca aktarılmış bir *.targets* dosyasında özel komutlar tanımlayabilirsiniz.

Içinde belirli Python proje şablonları Visual Studio zaten *kendi .targets* dosyasını kullanarak kendi özel komutlarını ekler. Örneğin, Bottle Web Project ve Flask Web Project şablonları iki komut ekler: **Sunucuyu** başlat ve Hata **ayıklamayı başlat sunucusu.** Django Web Project şablonu aynı komutların yanı sıra birkaç tane daha ekler:

![Django projesinin bağlam menüsünde Python alt menüsünün görünümü](media/custom-commands-django-menu.png)

Her özel komut python dosyası, Python modülü, satır içi Python kodu, rastgele yürütülebilir dosya veya pip komutuna başvurur. Ayrıca, komutun nasıl ve nerede çalıştırılamayacaklarını da belirtebilirsiniz.

> [!Tip]
> Metin düzenleyicisinde proje dosyasında her değişiklik yaptığınız zaman, bu değişiklikleri uygulamak için projeyi Visual Studio yeniden yüklemek gerekir. Örneğin, bu komutların projenin bağlam menüsünde görünmesi için özel komut tanımları ekledikten sonra projeyi yeniden yükleyebilirsiniz.
>
> Bildiğiniz gibi, Visual Studio doğrudan proje dosyasını düzenlemenin bir anlamı vardır. İlk olarak proje dosyasına sağ tıklar ve Projeyi kaldır'ı **\<project-name>** **seçersiniz,** sonra yeniden sağ tıklar ve Düzenle'yi seçerek projeyi Visual Studio açarsınız. Ardından düzenlemeler yapacak ve kaydederek projeye bir kez daha sağ tıklayabilir ve Projeyi yeniden yükle'yi seçerek proje dosyasını düzenleyicide kapatarak onaylamanızı istenir.
>
> Ancak, özel bir komut geliştirerek bu tıklamaların hepsi sıkıcı olabilir. Daha verimli bir iş akışı için projeyi Visual Studio'a yükp *.pyproj* dosyasını ayrı bir düzenleyicide (Visual Studio, Visual Studio Code, Not Defteri vb.) birlikte açın. Değişiklikleri düzenleyicide kaydedip Visual Studio Visual Studio algılar ve projeyi yeniden yüklemenin gerekip gerek olmadığını sorar ( Proje, ortamın dışında **\<name> değiştirilmiştir.**). Yeniden **Yükle'yi** seçin. Değişiklikleriniz tek adımda hemen uygulanır.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Adım adım kılavuz: Proje dosyasına komut ekleme

Özel komutlar hakkında bilgi sahibi olmak için bu bölümde, doğrudanpython.exekullanarak projenin başlangıç dosyasını *çalıştıran basit bir örnek vepython.exe.* (Bu tür bir komut, Hata Ayıklama kullanmakla **etkili bir şekilde aynıdır**  >  **Hata Ayıklama olmadan başlat.)**

1. Python Uygulama şablonunu kullanarak "Python-CustomCommands" adlı yeni **bir proje** oluşturun. (İşlem [hakkında bilgi sahibi değilken yönergeler için](quickstart-02-python-in-visual-studio-project-from-template.md) bkz. Hızlı Başlangıç: Şablondan Python projesi oluşturma.)

1. *Python_CustomCommands.py'de* kodunu `print("Hello custom commands")` ekleyin.

1. içinde projeye sağ **tıklayın Çözüm Gezgini** **Python'u** seçin ve altmenüste görünen tek komutun **Run PyLint (PyLint** Çalıştır) olduğunu göreceksiniz. Özel komutlarınız bu alt menüde görünür.

1. Girişte önerilen şekilde *Python-CustomCommands.pyproj'ı ayrı* bir metin düzenleyicisinde açın. Ardından dosyanın sonuna aşağıdaki satırları kapanış dosyasının hemen içine ekleyin `</Project>` ve dosyayı kaydedin.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Dosya değişikliği Visual Studio yeniden **yükle'yi** seçin. Ardından **Python** menüsünü yeniden kontrol edin ve PyLint komutunu içeren varsayılan özellik grubunu çoğaltarak **PyLint'i** çalıştırmanın burada gösterilen tek öğe olduğunu `<PythonCommands>` göreceksiniz.

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

1. Proje dosyasını kaydedin, Visual Studio ve istendiğinde projeyi yeniden yükleyin. Ardından **Python-CustomCommands projesine sağ tıklayın ve** **Python'ı seçin.** Menüde Başlangıç dosyasını **çalıştır öğesini** görüyor olun. Menü öğesini görmüyorsanız, öğeye adın ekleniyor olup olmadığını `<PythonCommands>` kontrol edin. Ayrıca bu [makalenin devamlarında](#troubleshooting) sorun giderme makalesine bakın.

    ![Python bağlam alt menüsü üzerinde görünen özel komut](media/custom-commands-walkthrough-menu-item.png)

1. Başlangıç dosyasını **çalıştır komutunu seçin.** Devam etmek için  Hello özel komutları metninin ve ardından Herhangi bir tuşa basın metninin yer alan bir komut **penceresi görüntülenir.**  Pencereyi kapatmak için bir tuşa basın.

    ![Konsol penceresinde özel komut çıktısı](media/custom-commands-walkthrough-console.png)

1. Proje dosyasıyla düzenleyiciye geri dönüp özniteliğinin değerini `ExecuteIn` olarak `output` değiştirebilirsiniz. Dosyayı kaydedin, Visual Studio'a geçiş yapma, projeyi yeniden yükleme ve komutu yeniden çağırma. Bu kez programın çıkışını, Visual Studio **penceresinde** görebilirsiniz:

    ![Çıkış penceresinde özel komut çıktısı](media/custom-commands-walkthrough-output-window.png)

1. Daha fazla komut eklemek için, her komut için uygun bir öğe tanımlayın, özellik grubuna hedefin adını ekleyin ve `<Target>` `<PythonCommands>` Visual Studio.

>[!Tip]
> gibi proje özelliklerini kullanan bir komutu çağırırsanız ve belirteci tanımlanmamış olduğundan komut başarısız olursa, Visual Studio projeyi yeniden yükleyene kadar komutu devre dışı `($StartupFile)` bırakamaz. Ancak, özelliği tanımlayarak projede değişiklik yapmak bu komutların durumunu yenilemez, bu nedenle yine de böyle durumlarda projeyi yeniden yüklemeniz gerekir.

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
| Targettype | Yes | Target özniteliğinin ne içerdiğini ve Arguments özniteliğiyle birlikte nasıl kullanıla olduğunu belirtir:<ul><li>**yürütülebilir:** Doğrudan komut satırına girilir gibi, Değeri Bağımsız Değişkenler'e ek olarak Target içinde adlı yürütülebilir dosyayı çalıştırın. Değerin bağımsız değişkenler olmadan yalnızca bir program adı içermesi gerekir.</li><li>**betik:** *python.exe* dosya adı ile birlikte, ardından Bağımsız Değişkenler'de değeriyle birlikte çalıştırın.</li><li>**module:** Target içinde modül adını ve ardından Bağımsız `python -m` Değişkenler'de değerini çalıştırın.</li><li>**code:** Target içinde yer alan satır içi kodu çalıştırın. Bağımsız Değişkenler değeri yoksayılır.</li><li>**pip:** Target içinde komutuyla, ardından Bağımsız Değişkenler ile çalıştırın; ExecuteIn "output" olarak ayarlanır, ancak pip komutu varsayıyor ve paket adı olarak `pip` `install` Target'ı kullanıyor.</li></ul> |
| Hedef | Yes | TargetType'a bağlı olarak, kullanmak üzere dosya adı, modül adı, kod veya pip komutu. |
| Bağımsız değişkenler | İsteğe Bağlı | Hedefe vermek için bağımsız değişken dizesini (varsa) belirtir. TargetType olduğunda bağımsız değişkenlerin python programına verildiğini ve bu programa `script`python.exe. ** TargetType için `code` yoksayıldı. |
| ExecuteIn | Yes | Komutun çalıştırılacak ortamı belirtir:<ul><li>**console:**(Varsayılan) Target ve bağımsız değişkenleri doğrudan komut satırına girilir gibi çalıştırır. Hedef çalışırken bir komut penceresi görüntülenir, ardından otomatik olarak kapatılır.</li><li>**consolepause:** Konsolla aynıdır, ancak pencereyi kapatmadan önce bir tuşa basın.</li><li>**output:** Target'i çalıştırır ve sonuçlarını çıkış **penceresinde** Visual Studio. TargetType "pip" ise, Visual Studio adı olarak Target'ı kullanır ve Bağımsız Değişkenleri ekler.</li><li>**repl:** Python Etkileşimli penceresinde [Hedefi](python-interactive-repl-in-visual-studio.md) çalıştırır; isteğe bağlı görünen ad, pencerenin başlığı için kullanılır.</li><li>**none:** konsol ile aynı şekilde davranır.</li></ul>|
| Başlangıç | İsteğe Bağlı | Komutunun çalıştırılalacak klasör. |
| ErrorRegex<br>WarningRegEx | İsteğe Bağlı | Yalnızca ExecuteIn olduğunda `output` kullanılır. Her iki değer de komut çıktısını ayrıştırarak Visual Studio listesi penceresinde hataları ve uyarıları gösterecek şekilde bir **normal ifade** belirtir. Belirtilmezse, komut Hata Listesi **penceresini etkilemez.** Neleri beklediğiniz hakkında daha Visual Studio için bkz. [Adlandırılmış yakalama grupları.](#named-capture-groups-for-regular-expressions) |
| RequiredPackages | İsteğe Bağlı | Komutla aynı biçimi kullanan komutun paket [](https://pip.pypa.io/en/stable/user_guide/#requirements-files) gereksinimlerinin listesirequirements.txt(pip.readthedocs.io). Run **PyLint** komutu, örneğin `pylint>=1.0.0` belirtir. komutunu çalıştırmadan önce Visual Studio tüm paketlerin yüklü olduğunu denetler. Visual Studio eksik paketleri yüklemek için pip kullanır. |
| Ortam | İsteğe Bağlı | Komutu çalıştırmadan önce tanımladığınız ortam değişkenleri dizesi. Her değişken, noktalı \<NAME> = \<VALUE> virgülle ayrılmış birden çok değişken içeren formu kullanır. Birden çok değere sahip bir değişken, 'NAME=VALUE1; DEĞER2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Normal ifadeler için adlandırılmış yakalama grupları

Bir komutun çıkışından hata ve uyarıları ayrıştırıyorsanız, Visual Studio ve değerlerinde normal ifadelerin aşağıdaki adlandırılmış grupları `ErrorRegex` `WarningRegex` kullanmasını bekler:

- `(?<message>...)`: Hatanın metni
- `(?<code>...)`: Hata kodu
- `(?<filename>...)`: Hatanın raporlandığı dosyanın adı
- `(?<line>...)`: Hatanın raporlandığı dosyada yer alan konumun satır numarası.
- `(?<column>...)`: Hatanın raporlandığı dosyadaki konumun sütun numarası.

Örneğin, PyLint aşağıdaki formda uyarılar üretir:

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

Aşağıdaki komut Çıktı `pip install my-package` penceresinde çalışır.  Paket geliştirerek yüklemesini test etmek için böyle bir komut kullanabilirsiniz. Target komutunun yerine paket adını içerdiğini ve bu ad kullanırken `install` varsayılır. `ExecuteIn="output"`

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

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izniyle kullanılır.*

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

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izniyle kullanılır.*

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

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izniyle kullanılır.*

## <a name="troubleshooting"></a>Sorun giderme

### <a name="message-the-project-file-could-not-be-loaded"></a>İleti: "Proje dosyası yüklenemedi"

Proje dosyasında söz dizimi hataları olduğunu gösterir. İleti, satır numarası ve karakter konumu ile belirli bir hatayı içerir.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Komut çalıştır alındıktan hemen sonra konsol penceresi kapanır

yerine `ExecuteIn="consolepause"` `ExecuteIn="console"` kullanın.

### <a name="command-does-not-appear-on-the-menu"></a>Komut menüde görünmüyor

Komutun özellik grubuna dahil olduğunu ve komut listesinde yer alan adın öğesinde belirtilen `<PythonCommands>` adla eşle olduğunu `<Target>` kontrol edin.

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

Tanımlanmamış bir özelliğe başvurursanız öznitelik değerleri boş olabilir. Örneğin, belirteci kullanırsanız ancak projede hiçbir başlangıç dosyası tanımlanmamışsa, `$(StartupFile)` belirteç boş bir dizeye çözümleyicidir. Böyle durumlarda, varsayılan bir değer tanımlamak istiyor olabilir. Örneğin, Bottle, Flask ve Django proje şablonlarında tanımlanan Sunucu çalıştır ve Hata ayıklamayı çalıştır sunucu komutları, proje özelliklerinde başka bir sunucu başlangıç dosyası belirtilmemişse varsayılan olarak *manage.py* olarak kullanılır.  

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio yanıt vermiyor ve komut çalıştırıyorsa kilitleniyor

büyük olasılıkla ile bir konsol komutu çalıştırmaya çalışıyorsanız, `ExecuteIn="output"` bu durumda Visual Studio ayrıştırmaya çalışırken başarısız olabilir. Bunun yerine `ExecuteIn="console"` kullanın. [(Bkz. Sorun 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Yürütülebilir komut "iç veya dış komut, çalıştırılabilir program veya toplu iş dosyası olarak tanınmıyor"

kullanırken, içinde değeri python veya yalnızca python gibi bağımsız değişkenler olmadan `TargetType="executable"` `Target` program adı *python.exe* gerekir.   Bağımsız değişkenleri özniteliğine `Arguments` taşıma.
