---
title: Python projeleri için özel menü komutlarını tanımla
description: Proje ve hedef dosyalarını düzenleyerek, yürütülebilir programları, komut dosyalarını, modülleri, satır altı kod parçacıklarını ve pip'i çağırmak için Visual Studio'daki Python proje bağlam menüsüne özel komutlar ekleyebilirsiniz.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ec53a67980866ed6422fae5764bbf6a9313ef91e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957706"
---
# <a name="define-custom-commands-for-python-projects"></a>Python projeleri için özel komutları tanımlama

Python projelerinizle çalışma sürecinde, kendinizi belirli komut dosyalarını veya modülleri çalıştırmak, pip komutlarını çalıştırmak veya başka bir rasgele aracı çalıştırmak için bir komut penceresine geçerken bulabilirsiniz. İş akışınızı geliştirmek için Python proje bağlam menüsündeki **Python** alt menüsüne özel komutlar ekleyebilirsiniz. Bu komutlar konsol penceresinde veya Visual Studio **Çıktı** penceresinde çalıştırılabilir. Visual Studio'ya komut un çıktısından hataları ve uyarıları nasıl ayrıştırırınız öğretmek için de düzenli ifadeler kullanabilirsiniz.

Varsayılan olarak, bu menü yalnızca tek **Bir Run PyLint** komutunu içerir:

![Projenin bağlam menüsünde Python alt menüsünün varsayılan görünümü](media/custom-commands-default-menu.png)

Özel komutlar bu aynı bağlam menüsünde görünür. Özel komutlar, bu tek tek projeye uygulandıkları doğrudan bir proje dosyasına eklenir. *Bir .targets* dosyasında, birden çok proje dosyasına kolayca içe aktarılabilen özel komutlar da tanımlayabilirsiniz.

Visual Studio'daki bazı Python proje şablonları, *.targets* dosyasını kullanarak kendi özel komutlarını zaten ekler. Örneğin, Şişe Web Projesi ve Flask Web Project şablonları hem iki komut, **Başlat sunucusu** ve Başlat **hata ayıklama sunucusu**ekleyin. Django Web Project şablonu bu aynı komutları artı oldukça birkaç ekler:

![Django projesinin bağlam menüsünde Python alt menüsünün görünümü](media/custom-commands-django-menu.png)

Her özel komut bir Python dosyasına, Python modülüne, satır satırlı Python koduna, rasgele yürütülebilir veya pip komutuna başvurabilir. Komutun nasıl ve nerede çalıştığını da belirtebilirsiniz.

> [!Tip]
> Bir metin düzenleyicisinde proje dosyasında değişiklik yaptığınızda, bu değişiklikleri uygulamak için projeyi Visual Studio'da yeniden yüklemeniz gerekir. Örneğin, bu komutların projenin bağlam menüsünde görünmesi için özel komut tanımları ekledikten sonra projeyi yeniden yüklemeniz gerekir.
>
> Bildiğiniz gibi, Visual Studio proje dosyasını doğrudan düzenlemesi için bir araç sağlar. Önce proje dosyasına sağ tıklayın ve **Projeyi Boşalt'ı**seçin, sonra tekrar sağ tıklayın ve Visual Studio düzenleyicisinde projeyi açmak için **proje adını>\<edin'i** seçin. Daha sonra, projeyi bir kez daha sağ tıklatın ve proje dosyasını düzenleyicide kapatmayı onaylamanızı da gerektiren **Yeniden Yükle projesini**seçin.
>
> Ancak, özel bir komut geliştirirken, tüm bu tıklamalar sıkıcı olabilir. Daha verimli bir iş akışı için projeyi Visual Studio'ya yükleyin ve *.pyproj* dosyasını ayrı bir editörde açın (Visual Studio, Visual Studio Code, Notepad, vb.) başka bir örneği gibi. Düzenleyicideki değişiklikleri kaydedip Visual Studio'ya geçtiğinızda, Visual Studio değişiklikleri algılar ve projeyi yeniden yükleyip yüklememenizi sorar (**proje \<adı> ortam dışında değiştirilmiştir.** **Yeniden Yükle'yi** seçin ve değişiklikleriniz hemen tek bir adımda uygulanır.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Walkthrough: Proje dosyasına komut ekleme

Özel komutlara alışmak için, bu bölüm doğrudan *python.exe*kullanarak bir projenin başlangıç dosyasını çalıştıran basit bir örnek üzerinden yürür. (Böyle bir komut etkili**hata ayıklama olmadan**Hata **Ayıklama** > Başlat kullanarak aynıdır.)

1. **Python Application** şablonunu kullanarak "Python-CustomKomutları" adlı yeni bir proje oluşturun. (Bkz. Hızlı Başlangıç: İşleme zaten aşina değilseniz, yönergeler [için şablondan bir Python projesi oluşturun.)](quickstart-02-python-in-visual-studio-project-from-template.md)

1. *Python_CustomCommands.py*olarak, kodu `print("Hello custom commands")`ekleyin.

1. **Solution Explorer'da**projeyi sağ tıklatın, **Python'u**seçin ve alt menüde görünen tek komutun **Run PyLint**olduğunu fark edin. Özel komutlarınız bu alt menüde görünür.

1. Girişte önerildiği gibi, *Python-CustomCommands.pyproj'u* ayrı bir metin düzenleyicisinde açın. Ardından, dosyanın sonuna kapanışın `</Project>` hemen içine aşağıdaki satırları ekleyin ve dosyayı kaydedin.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Visual Studio'ya geri dön ve dosya değişikliği hakkında sizi istediğinde **Yeniden Yükle'yi** seçin. Ardından **Python** menüsünü tekrar kontrol edin ve eklediğiniz satırlar yalnızca PyLint komutunu içeren varsayılan `<PythonCommands>` özellik grubunu kopyaladığı için **PyLint'i çalıştırın** hala orada gösterilen tek öğe olduğunu görün.

1. Proje dosyasıyla düzenleyiciye geçin ve `<Target>` `<PropertyGroup>`aşağıdaki tanımı ekleyin. Bu makalede daha sonra `Target` açıklandığı gibi, bu öğe, bir konsol penceresinde *python.exe* kullanarak başlangıç dosyasını çalıştırmak için özel bir komut tanımlar ("Başlangıç Dosyası" özelliği tarafından tanımlanır). Öznitelik, `ExecuteIn="consolepause"` kapatmadan önce bir tuşa basmanızı bekleyen bir konsol kullanır.

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

1. Öğenin aşağıdaki koda `Name` benzemesi `<PythonCommands>` için Hedef'in özniteliğinin değerini daha önce eklenen özellik grubuna ekleyin. Hedefin adını bu listeye eklemek Python **menüsüne** ekler.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Komutunuzun tanımlananlardan önce görünmesini `$(PythonCommands)`istiyorsanız, bunları bu belirteçönce yerleştirin.

1. Proje dosyasını kaydedin, Visual Studio'ya geçin ve istendiğinde projeyi yeniden yükleyin. Ardından **Python-CustomCommands** projesini sağ tıklatın ve **Python'u**seçin. Menüde bir **Çalıştır başlangıç dosyası** öğesi görmeniz gerekir. Menü öğesini görmüyorsanız, öğeye adı eklediğinizi `<PythonCommands>` denetleyin. Ayrıca, bu makalenin ilerleyen saatlerinde [Sorun Giderme'ye](#troubleshooting) bakın.

    ![Python bağlam alt menüsünde görünen özel komut](media/custom-commands-walkthrough-menu-item.png)

1. Çalıştır **başlangıç dosyası** komutunu seçin ve devam etmek için herhangi bir **tuşa basın**ardından metin **Merhaba özel komutları** ile görünen bir komut penceresi görmeniz gerekir.  Pencereyi kapatmak için bir tuşa basın.

    ![Konsol penceresinde özel komut çıkışı](media/custom-commands-walkthrough-console.png)

1. Proje dosyasıyla düzenleyiciye dönün ve özniteliğin değerini `output`''ye değiştirin. `ExecuteIn` Dosyayı kaydedin, Visual Studio'ya geçin, projeyi yeniden yükleyin ve komutu yeniden çağırın. Bu kez programın çıktısının Visual Studio'nun **Çıktı** penceresinde göründüğünü görürsünüz:

    ![Çıkış penceresinde özel komut çıkışı](media/custom-commands-walkthrough-output-window.png)

1. Daha fazla komut eklemek için, her komut için uygun `<Target>` bir öğe `<PythonCommands>` tanımlayın, hedefin adını özellik grubuna ekleyin ve projeyi Visual Studio'da yeniden yükleyin.

>[!Tip]
> Belirteç tanımlı olmadığı için `($StartupFile)`proje özelliklerini kullanan bir komut çağırırsanız ve komut başarısız olursa, Visual Studio projeyi yeniden yükleyene kadar komutu devre dışı bilebilir. Ancak, özelliği tanımlayacak projede değişiklik yapmak bu komutların durumunu yenilemez, bu nedenle yine de bu gibi durumlarda projeyi yeniden yüklemeniz gerekir.

## <a name="command-target-structure"></a>Komut hedef yapısı

Öğenin `<Target>` genel formu aşağıdaki sözde kodda gösterilir:

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

Öznitelik değerlerinde proje özellikleri veya ortam değişkenlerine başvurmak `$()` için, adı `$(StartupFile)` belirteç içinde ve `$(MSBuildProjectDirectory)`. Daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

### <a name="target-attributes"></a>Hedef öznitelikleri

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Adı | Evet | Visual Studio projesindeki komutun tanımlayıcısı. Komutun `<PythonCommands>` Python alt menüsünde görünmesi için özellik grubuna bu adın eklenmesi gerekir. |
| Etiketle | Evet | Python alt menüsünde görünen Kullanıcı Arabirimi görüntü adı. |
| Döndürür | Evet | Hedefi `@(Commands)`bir komut olarak tanımlayan içermelidir. |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem öznitelikleri

Tüm öznitelik değerleri büyük/küçük harf duyarsızdır.

| Öznitelik | Gerekli | Açıklama |
| --- | --- | --- |
| Targettype | Evet | Hedef özniteliğinin neler içerdiğini ve Bağımsız Değişken özniteliğiyle birlikte nasıl kullanıldığını belirtir:<ul><li>**çalıştırılabilir**: Hedef'te adı geçen yürütülebilir, bağımsız değişkenlerde değeri ekleyen, komut satırına doğrudan girilir gibi çalıştırın. Değer, bağımsız değişkeniçermeyen yalnızca bir program adı içermelidir.</li><li>**komut dosyası**: *Python.exe'yi* Hedef'teki dosya adı ile çalıştırın, bağımsız değişkendeki değeri takip edin.</li><li>**modül**: `python -m` Hedef'te modül adı, Bağımsız Değişkenler'deki değer takip eden çalıştırın.</li><li>**kod**: Hedef'te yer alan satır içinde kodu çalıştırın. Bağımsız değişkenler değeri yoksayılır.</li><li>**pip**: `pip` Hedef'teki komutla çalıştırın, ardından Bağımsız Değişkenler; executein "çıkış" olarak ayarlanır, ancak, pip `install` komutu varsayar ve paket adı olarak Hedef kullanır.</li></ul> |
| Hedef | Evet | TargetType'a bağlı olarak kullanılacak dosya adı, modül adı, kod veya pip komutu. |
| Bağımsız Değişkenler | İsteğe bağlı | Hedefe vermek için bir dizi bağımsız değişken (varsa) belirtir. TargetType olduğunda, `script`bağımsız değişkenlerin *python.exe'ye*değil Python programına verildiğini unutmayın. `code` TargetType için yoksayılır. |
| ExecuteIn | Evet | Komutun çalıştırılacak ortamı belirtir:<ul><li>**konsol**: (Varsayılan) Hedef ve bağımsız değişkenleri doğrudan komut satırına giriliyormuş gibi çalıştırın. Hedef çalışırken bir komut penceresi görüntülenir ve otomatik olarak kapatılır.</li><li>**consolepause**: Konsolla aynı, ancak pencereyi kapatmadan önce bir tuş tuşuna basmak için bekler.</li><li>**output**: Target'ı çalıştırUr ve sonuçlarını Visual Studio'daki **Output** penceresinde görüntüler. TargetType "pip" ise, Visual Studio paket adı olarak Hedef kullanır ve Bağımsız Değişkenler ekler.</li><li>**repl**: Python [Interactive](python-interactive-repl-in-visual-studio.md) penceresinde Hedef çalışır; isteğe bağlı ekran adı pencerenin başlığı için kullanılır.</li><li>**none**: konsol la aynı şekilde olur.</li></ul>|
| Başlangıç | İsteğe bağlı | Komutu çalıştırılan klasör. |
| ErrorRegex<br>WarningRegEx | İsteğe bağlı | Yalnızca ExecuteIn olduğunda `output`kullanılır. Her iki değer de Visual Studio'nun **Hata Listesi** penceresinde hataları ve uyarıları göstermek için çıktıyı ayrıştırdığı normal bir ifade belirtir. Belirtilmemişse, komut Hata **Listesi** penceresini etkilemez. Visual Studio'nun neler beklediği hakkında daha fazla bilgi için [Bkz.](#named-capture-groups-for-regular-expressions) |
| Gerekli Paketler | İsteğe bağlı | [*requirements.txt*](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io) ile aynı biçimi kullanarak komut için paket gereksinimleri listesi. **Run PyLint** komutu, örneğin `pylint>=1.0.0`belirtir. Komutu çalıştırmadan önce Visual Studio, listedeki tüm paketlerin yüklü olup olmadığını denetler. Visual Studio herhangi bir eksik paketleri yüklemek için pip kullanır. |
| Ortam | İsteğe bağlı | Komutu çalıştırmadan önce tanımlayacak ortam değişkenleri dizisi. Her \<değişken, name>\<= VALUE>' i kullanır ve birden çok değişken yarı kolonlarla ayrılır. Birden çok değeri olan bir değişken, 'NAME=VALUE1' gibi tek veya çift tırnak içinde bulunmalıdır; DEĞER2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Normal ifadeler için yakalama grupları nın adı

Visual Studio, bir komutun çıktısından gelen hata ve uyarıları ayrıştırırken, `ErrorRegex` değerlerdeki `WarningRegex` ve düzenli ifadelerin aşağıdaki adlandırılmış grupları kullanmasını bekler:

- `(?<message>...)`: Hata metni
- `(?<code>...)`: Hata kodu
- `(?<filename>...)`: Hatanın bildirildiği dosyanın adı
- `(?<line>...)`: Hatanın raporlandığı dosyadaki konumun satır numarası.
- `(?<column>...)`: Hatanın raporlandığı dosyadaki konumun sütun numarası.

Örneğin, PyLint aşağıdaki formun uyarılarını üretir:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Visual Studio'nun bu tür uyarılardan doğru bilgileri ayıklayıp **Hata** `WarningRegex` Listesi penceresinde göstermesine izin vermek **için, Run Pylint** komutu için değer aşağıdaki gibidir:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Değer `msg_id` aslında olması `code`gerektiğini unutmayın , [Sorun 3680](https://github.com/Microsoft/PTVS/issues/3680)bakın .)

## <a name="create-a-targets-file-with-custom-commands"></a>Özel komutlarla bir .targets dosyası oluşturma

Proje dosyasında özel komutlar tanımlanması, bunları yalnızca bu proje dosyası için kullanılabilir hale getirir. Birden çok proje dosyasındaki komutları kullanmak `<PythonCommands>` için, bunun `<Target>` yerine özellik grubunu ve tüm öğelerinizi *.targets* dosyasında tanımlarsınız. Daha sonra bu dosyayı tek tek proje dosyalarına aktarırsınız.

*.targets* dosyası aşağıdaki gibi biçimlendirilir:

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

*Bir .targets* dosyasını projeye yüklemek `<Import Project="(path)">` için, öğenin `<Project>` içinde herhangi bir yere bir öğe yerleştirin. Örneğin, projenizdeki *bir hedef* alt klasöründe *CustomCommands.targets* adlı bir dosyanız varsa, aşağıdaki kodu kullanın:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> *.targets* dosyasını her değiştirdiğinizde, yalnızca projenin kendisini değil, proje yi de içeren *çözümü* yeniden yüklemeniz gerekir.

## <a name="example-commands"></a>Örnek komutlar

### <a name="run-pylint-module-target"></a>PyLint çalıştırın (modül hedefi)

Aşağıdaki kod *Microsoft.PythonTools.targets* dosyasında görünür:

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

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Pip yüklemeyi belirli bir paketle çalıştırma (pip hedefi)

Aşağıdaki komut `pip install my-package` **Çıkış** penceresinde çalışır. Bir paket geliştirirken ve yüklemesini sınarken böyle bir komut kullanabilirsiniz. Hedef'in `install` komut yerine paket adı içerdiğini ve bu `ExecuteIn="output"`adı kullanırken varsayıldığını unutmayın.

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

### <a name="show-outdated-pip-packages-pip-target"></a>Eski pip paketlerini göster (pip hedef)

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

### <a name="run-an-executable-with-consolepause"></a>Consolepause ile çalıştırılabilir çalıştır

Aşağıdaki komut, `where` proje klasöründe başlayan Python dosyalarını göstermek için çalışır:

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

### <a name="run-server-and-run-debug-server-commands"></a>Sunucu çalıştırın ve hata ayıklama sunucu komutlarını çalıştırın

Web projeleri için **Başlat sunucusu** ve **Başlat sunucu** komutlarının nasıl tanımlandığını keşfetmek için [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub) incelemesini yapın.

### <a name="install-package-for-development"></a>Geliştirme paketi yükleyin

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

*Kaynak: [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izinli olarak kullanılır.*

### <a name="generate-windows-installer"></a>Windows yükleyici oluşturma

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

*Kaynak: [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izinli olarak kullanılır.*

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

*Kaynak: [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), izinli olarak kullanılır.*

## <a name="troubleshooting"></a>Sorun giderme

### <a name="message-the-project-file-could-not-be-loaded"></a>İleti: "Proje dosyası yüklenemedi"

Proje dosyasında sözdizimi hataları olduğunu gösterir. İleti, satır numarası ve karakter konumuyla ilgili belirli bir hatayı içerir.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Komut çalıştırıldıktan hemen sonra konsol penceresi kapanır

`ExecuteIn="console"`Yerine kullanın. `ExecuteIn="consolepause"`

### <a name="command-does-not-appear-on-the-menu"></a>Komut menüde görünmüyor

Komutun `<PythonCommands>` özellik grubuna dahil edilip edilemediğini ve komut listesindeki adın `<Target>` öğede belirtilen adla eşleşip eşleşmediğini denetleyin.

Örneğin, aşağıdaki öğelerde, özellik grubundaki "Örnek" adı hedefteki "Örnek Komut" adı ile eşleşmez. Visual Studio "Örnek" adlı bir komut bulamaz, bu nedenle hiçbir komut görünür. Komut listesinde "Örnek Komut" kullanın veya hedefin adını yalnızca "Örnek" olarak değiştirin.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>İleti: "Komut adı> \<çalıştırırken bir hata oluştu. Projeden komut \<hedef adı> alınamadı."

Öğelerin içeriğinin `<Target>` `<CreatePythonCommandItem>` yanlış olduğunu gösterir. Olası nedenler şunlardır:

- Gerekli `Target` öznitelik boş.
- Gerekli `TargetType` öznitelik boş veya tanınmayan bir değer içerir.
- Gerekli `ExecuteIn` öznitelik boş veya tanınmayan bir değer içerir.
- `ErrorRegex`veya `WarningRegex` ayar `ExecuteIn="output"`olmadan belirtilir.
- Tanımayılmamış öznitelikler öğede var. Örneğin, `Arguments`'' yerine `Argumnets` yanlış yazılmış ( yanlış yazılmış) kullanmış olabilirsiniz.

Tanımlanmamış bir özelliğe başvurursanız öznitelik değerleri boş olabilir. Örneğin, belirteci `$(StartupFile)` kullanırsanız ancak projede başlangıç dosyası tanımlanmamışsa, belirteç boş bir dize yle çözülür. Bu gibi durumlarda, varsayılan bir değer tanımlamak isteyebilirsiniz. Örneğin, Şişe, Flask ve Django proje şablonlarında tanımlanan **Çalıştır sunucusu** ve **Çalıştır hata ayıklama komutları,** proje özelliklerinde bir sunucu başlangıç dosyası belirtmediyseniz *manage.py* varsayılan olarak şablonlar.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio komutu çalıştırırken asılı ve çöküyor

Büyük olasılıkla bir konsol komutu çalıştırmaya çalışıyorsunuz `ExecuteIn="output"`, bu durumda Visual Studio çıktıyı ayrıştırmaya çalışırken çökebilir. Bunun yerine `ExecuteIn="console"` kullanın. [(Bkz. Sayı 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Çalıştırılabilir komut "bir iç veya dış komut, operable program veya toplu dosya olarak tanınmıyor"

`TargetType="executable"`Kullanırken, değeri `Target` yalnızca python veya *python.exe* gibi *python* herhangi bir bağımsız değişken olmadan *yalnızca* program adı olmalıdır. Bağımsız değişkenleri `Arguments` özniteliğe taşıyın.
