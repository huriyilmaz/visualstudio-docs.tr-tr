---
title: Görevleri kullanarak yapı hata ayıklama görevlerini özelleştirme.vs.json launch.vs.json
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e912459f45086b1bf5f96a9458f006354e982ffd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542691"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>"Açık Klasör" geliştirme için yapı ve hata ayıklama görevlerini özelleştirme

Visual Studio birçok farklı dil ve kod tabanını nasıl çalıştıracağını bilir, ancak her şeyi nasıl çalıştıracağını bilmez. Visual Studio'da [bir kod klasörü açtıysanız](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) ve Visual Studio kodunuzu nasıl çalıştırabileceğinizi biliyorsa, ek yapılandırma olmadan hemen çalıştırabilirsiniz.

Codebase, Visual Studio'nun tanımadığı özel yapı araçları kullanıyorsa, Visual Studio'da kodu çalıştırmak ve hata ayıklamak için bazı yapılandırma ayrıntıları sağlamanız gerekir. Visual Studio'ya yapı görevlerini tanımlayarak kodunuzu nasıl *oluşturabileceğinizi*bildirirsiniz. Bir dilin kodunu oluşturmak ve çalıştırmak için gereken tüm öğeleri belirtmek için bir veya daha fazla yapı görevi oluşturabilirsiniz. Ayrıca, istediğiniz hemen hemen her şeyi yapabilecek rasgele görevler de oluşturabilirsiniz. Örneğin, bir klasörün içeriğini listelemek veya bir dosyayı yeniden adlandırmak için bir görev oluşturabilirsiniz.

Aşağıdaki *.json* dosyalarını kullanarak projesiz kod tabanınızı özelleştirin:

|Dosya adı|Amaç|
|-|-|
|*görevler.vs.json*|Özel yapı komutları ve derleyici anahtarları ve rasgele (yapı yla ilgili olmayan) görevleri belirtin.<br>**Çözüm Gezgini** sağ tık menü öğesi **Yapılandırma Görevleri**üzerinden erişilen .|
|*launch.vs.json*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>**Solution Explorer** sağ tıkmenü öğesi **Hata Ayıklama ve Başlatma Ayarları**üzerinden erişilen .|

Bu *.json* dosyaları, codebase kök klasöründe *.vs* adlı gizli bir klasörde bulunur. *Tasks.vs.json* ve *launch.vs.json* dosyaları Visual Studio tarafından, **Solution Explorer'daki**bir dosya veya klasörde **Görevleri Yapılandırveya** **Hata Ayıklama ve Başlatma Ayarlarını** seçtiğinizde gerektiğinde oluşturulur. Kullanıcılar genellikle bunları kaynak denetiminde denetlemek istemediğinden bu *.json* dosyaları gizlenir. Ancak, bunları kaynak denetiminde denetlemek istiyorsanız, dosyaları görünür oldukları kod tabanınızın köküne sürükleyin.

> [!TIP]
> Visual Studio'daki gizli dosyaları görüntülemek için Çözüm **Gezgini** araç çubuğundaki **Tüm Dosyaları Göster** düğmesini seçin.

## <a name="define-tasks-with-tasksvsjson"></a>Görevleri görevlerle tanımlama.vs.json

Komut dosyalarını veya diğer dış işlemleri, geçerli çalışma alanınızdaki dosyalarda doğrudan IDE'de görev olarak çalıştırarak otomatikleştirebilirsiniz. Bir dosyaveya klasöre sağ tıklayarak ve **Görevleri Yapılandır'ı**seçerek yeni bir görevi yapılandırabilirsiniz.

![Görevleri Yapılandırma menüsü](../ide/media/customize-configure-tasks-menu.png)

Bu, *.vs* klasöründe *tasks.vs.json* dosyasını oluşturur (veya açar). Bu dosyada bir yapı görevi veya rasgele görev tanımlayabilir ve ardından Çözüm **Gezgini** sağ tıklama menüsünden verdiğiniz adı kullanarak bu görevi çağırabilirsiniz.

Özel görevler tek tek dosyalara veya belirli bir türdeki tüm dosyalara eklenebilir. Örneğin, NuGet paket dosyaları bir "Paketleri Geri Yükleme" görevi olacak şekilde yapılandırılabilir veya tüm kaynak dosyaları tüm *.js* dosyaları için linter gibi statik bir çözümleme görevi olacak şekilde yapılandırılabilir.

### <a name="define-custom-build-tasks"></a>Özel yapı görevlerini tanımlama

Codebase'iniz Visual Studio'nun tanımadığı özel yapı araçları kullanıyorsa, bazı yapılandırma adımlarını tamamlayana kadar Visual Studio'da kodu çalıştırıp hata ayıklayamazsınız. Visual Studio, Visual Studio'ya kodunuzu nasıl oluşturacağınızı, yeniden oluşturacağınızı ve temizleyeceğiniz için oluşturma *görevleri* sağlar. *Görevler.vs.json* oluşturma görev dosyası çiftler Visual Studio iç geliştirme döngü codebase tarafından kullanılan özel yapı araçları.

*hello.cs*adlı tek bir C# dosyasından oluşan bir kod tabanı düşünün. Böyle bir kod tabanı için *makefile* aşağıdaki gibi görünebilir:

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

Yapı, temizleme ve yeniden oluşturma hedefleri içeren böyle bir *makefile* için aşağıdaki görevleri *tanımlayabilirsiniz.vs.json* dosyası. Yapı aracı olarak NMAKE'yi kullanarak kod tabanını oluşturmak, yeniden oluşturmak ve temizlemek için üç yapı görevi içerir.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Görevlerde yapı görevlerini tanımladıktan *sonra.vs.json*, Ek sağ tıklama menüsü (bağlam menüsü) öğeleri **Çözüm Gezgini'ndeki**ilgili dosyalara eklenir. Bu örnekiçin, "yapı", "yeniden oluşturma" ve "temiz" seçenekleri herhangi bir *makefile* dosyasının bağlam menüsüne eklenir.

![yapı, yeniden oluşturma ve temiz ile dosya bağlam menüsü oluşturma](media/customize-build-rebuild-clean.png)

> [!NOTE]
> `contextType` Komutlar, ayarları nedeniyle Görevleri **Yapılandır** komutu altındaki bağlam menüsünde görünür. "yapı", "yeniden oluşturma" ve "temiz" yapı komutlarıdır, bu nedenle bağlam menüsünün ortasındaki yapı bölümünde görünürler.

Bu seçeneklerden birini seçtiğinizde, görev yürütülür. **Çıktı Çıktı** penceresinde görünür ve yapı hataları **Hata Listesinde**görünür.

### <a name="define-arbitrary-tasks"></a>Rasgele görevleri tanımlama

*Görevler.vs.json* dosyasında istediğiniz her şeyi yapmak için rasgele görevler tanımlayabilirsiniz. Örneğin, **çıktı** penceresinde şu anda seçili dosyanın adını görüntülemek veya dosyaları belirtilen bir dizinde listelemek için bir görev tanımlayabilirsiniz.

Aşağıdaki örnek, tek bir görevi tanımlayan *bir görevler.vs.json* dosyasını gösterir. Çağrıldığızaman, görev şu anda seçili *.js* dosyasının dosya adını görüntüler.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName`sağ tıklama menüsünde görünen adı belirtir.
- `appliesTo`komutun hangi dosyalarda gerçekleştirilebileceğini belirtir.
- Özellik `command` çağırmak için komut belirtir. Bu örnekte, `COMSPEC` ortam değişkeni komut satırı yorumlayıcı, genellikle *cmd.exe*tanımlamak için kullanılır.
- Özellik, `args` çağrılan komuta geçirilecek bağımsız değişkenleri belirtir.
- `${file}` Makro, **Çözüm Gezgini'nde**seçili dosyayı alır.

*tasks.vs.json'u*kurtardıktan sonra klasördeki herhangi bir *.js* dosyasına sağ tıklayabilir ve **Yankı dosya adını**seçebilirsiniz. Dosya adı **Çıktı** penceresinde görüntülenir.

> [!NOTE]
> Kod tabanınız bir görev *içermiyorsa.vs.json* dosyası, **Solution Explorer'daki**bir dosyanın sağ tıklama veya bağlam menüsünden **Görevleri Yapılandır'ı** seçerek bir tane oluşturabilirsiniz.

Sonraki örnek, *depo* gözü dizininin dosyalarını ve alt klasörlerini listeleyen bir görevi tanımlar.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}``tasks` önce bloktan önce tanımlanan özel bir makrodur. Daha sonra `args` özellik denir.

Bu görev tüm dosyalar için geçerlidir. **Çözüm Gezgini'ndeki**herhangi bir dosyadaki bağlam menüsünü açtığınızda, görevin ad **Listesi Çıktıları** menünün alt kısmında görünür. **Liste Çıktıları'nı**seçtiğinizde, *depo gözü* dizininin içeriği Visual Studio'daki **Çıktı** penceresinde listelenir.

![Bağlam menüsünde rasgele görev](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayarlar kapsamı

Bir kod tabanının kökünde ve alt dizinde birden çok *görev.vs.json* dosyası bulunabilir. Bu tasarım, esnekliğin kod tabanının farklı alt dizinlerinde farklı davranışlara sahip olmasını sağlar. Visual Studio, kod tabanı boyunca ayarları toplar veya geçersiz kılar ve dosyaları aşağıdaki sırada öncelike göre belirler:

- Kök klasörün *.vs* dizinindeki ayarlar dosyaları.
- Ayarın hesaplandığı dizin.
- Geçerli dizinin ana dizini, kök dizine kadar.
- Kök dizinindeki ayarlar dosyaları.

Bu toplama kuralları görevler için *geçerlidir.vs.json*. Diğer dosyadaki ayarların nasıl toplanmış olduğu hakkında bilgi için, bu makaledeki dosyaiçin ilgili bölüme bakın.

### <a name="properties-for-tasksvsjson"></a>Görevler için özellikler.vs.json

Bu bölümde, görevlerde belirtebileceğiniz bazı özellikler *açıklanır.vs.json*.

#### <a name="appliesto"></a>Appliesto

Herhangi bir dosya veya klasör için, `appliesTo` örneğin, `"appliesTo": "hello.js"`alana adını belirterek görev oluşturabilirsiniz. Aşağıdaki dosya maskeleri değer olarak kullanılabilir:

|||
|-|-|
|`"*"`| görev çalışma alanındaki tüm dosya ve klasörler için kullanılabilir|
|`"*/"`| görev çalışma alanındaki tüm klasörler için kullanılabilir|
|`"*.js"`| görev çalışma alanında uzantısı *.js* ile tüm dosyalar için kullanılabilir|
|`"/*.js"`| görev çalışma alanının kökünde uzantısı *.js* ile tüm dosyalar için kullanılabilir|
|`"src/*/"`| görev *src* klasörünün tüm alt klasörleri için kullanılabilir|
|`"makefile"`| görev çalışma alanındaki tüm *makefile* dosyaları için kullanılabilir|
|`"/makefile"`| görev yalnızca çalışma alanının kökündeki *makefile* için kullanılabilir|

#### <a name="macros-for-tasksvsjson"></a>Görevler için makrolar.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Herhangi bir ortam değişkenini belirtir (örneğin, ${env. PATH}, ${env.COMSPEC} vb.) geliştirici komut istemi için ayarlanır. Daha fazla bilgi [için Visual Studio için Geliştirici komut istemine](/dotnet/framework/tools/developer-command-prompt-for-vs)bakın.|
|`${workspaceRoot}`| Çalışma alanı klasörüne tam yol (örneğin, *C:\sources\hello)*|
|`${file}`| Bu görevi çalıştırmak için seçilen dosya veya klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.js)*|
|`${relativeFile}`| Dosya veya klasöre göreli yol (örneğin, *src\hello.js)*|
|`${fileBasename}`| Yol veya uzantı olmadan dosyanın adı (örneğin, *merhaba)*|
|`${fileDirname}`| Dosya adı hariç dosyaya tam yol (örneğin, *C:\sources\hello\src)*|
|`${fileExtname}`| Seçili dosyanın uzantısı (örneğin, *.js)*|

## <a name="configure-debugging-with-launchvsjson"></a>Launch.vs.json ile hata ayıklama yapılandırma

Hata ayıklama için CMake projelerini yapılandırmak için [bkz.](/cpp/build/configure-cmake-debugging-sessions)

1. Hata ayıklama için kod tabanınızı yapılandırmak **için, Solution Explorer'da** yürütülebilir dosyanızın sağ tıklama veya bağlam menüsünden **Hata Ayıklama ve Başlat Ayarları** menüsüöğesini seçin.

   ![Hata Ayıklama ve Başlatma Ayarları bağlam menüsü](media/customize-debug-launch-menu.png)

1. Hata **Ayıklama** iletişim kutusunu seç kutusunda bir seçenek seçin ve ardından **Seç** düğmesini seçin.

   ![Hata ayıklama iletişim kutusu seçin](media/customize-select-a-debugger.png)

   *Launch.vs.json* dosyası zaten yoksa oluşturulur.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Ardından, **Solution Explorer'da**çalıştırılabilir dosyaya sağ tıklayın ve **Başlangıç Öğesi olarak ayarla'yı**seçin.

   Yürütülebilir kod tabanınız için başlangıç öğesi olarak belirlenir ve hata ayıklama **Başlat** düğmesinin başlığı, çalıştırılabilir inizin adını yansıtacak şekilde değişir.

   ![Özelleştirilmiş Başlat düğmesi](media/customize-start-button.png)

   **F5'i**seçtiğinizde, hata ayıklama başlatılır ve önceden ayarlamış olabileceğiniz herhangi bir kesme noktasında durur. Tüm tanıdık hata ayıklama pencereleri mevcuttur ve işlevseldir.

   > [!IMPORTANT]
   > C++ açık klasör projelerindeki özel yapı ve hata ayıklama görevleri hakkında ek ayrıntılar için [Visual Studio'da C++ yapı sistemleri için Açık Klasör desteğine](/cpp/build/open-folder-projects-cpp)bakın.

### <a name="specify-arguments-for-debugging"></a>Hata ayıklama için bağımsız değişkenleri belirtin

*Launch.vs.json* dosyasında hata ayıklama için geçmek için komut satırı bağımsız değişkenleri belirtebilirsiniz. Aşağıdaki örnekte `args` gösterildiği gibi, dizideki bağımsız değişkenleri ekleyin:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Bu dosyayı kaydettiğinizde, yeni yapılandırmanın adı hata ayıklama hedef açılır listesinde görünür ve hata ayıklama başlatmak için seçebilirsiniz. İstediğiniz kadar hata ayıklama yapılandırması oluşturabilirsiniz.

![Hata ayıklama yapılandırmaları açılır liste](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` *launch.vs.json'daki* dizi özelliği iki dosya&mdash;noktasından kod tabanının kök dizini ve *.vs* dizininden okunur. Çakışma varsa, öncelik *.vs\launch.vs.json*değeriverilir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

Visual Studio, bu konuda açıklanan üç *.json* dosyasına ek olarak, kod tabanınızda varsa bazı ek dosyaların ayarlarını da okur.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual *Studio, settings.json*adlı bir dosyadan sınırlı ayarları okur, *eğer .vscode*adlı bir dizindeyse. Bu işlevsellik, daha önce Visual Studio Code'da geliştirilmiş kod tabanları için sağlanır. Şu anda *,vscode\settings.json* adresinden okunan tek ayar, Solution Explorer'da ve bazı arama araçlarında dosyaları görsel olarak filtreleyen bir ayardır. `files.exclude`

Codebase'inizde herhangi bir sayıda *.vscode\settings.json* dosyası olabilir. Bu dosyadan okunan ayarlar *.vscode'un* ana dizinine ve tüm alt dizinlerine uygulanır.

### <a name="gitignore"></a>.gitignore

*.gitignore* dosyaları Git'e hangi dosyaları yoksayması gerektiğini söylemek için kullanılır; diğer bir deyişle, hangi dosyaları ve dizinleri iade etmek istemiyorum. *.gitignore* dosyaları genellikle bir kod tabanının parçası olarak dahil edilir, böylece ayarlar kod tabanının tüm geliştiricileri ile paylaşılabilir. Visual Studio öğeleri görsel olarak ve bazı arama araçlarından filtrelemek için *.gitignore* dosyalarındaki desenleri okur.

*.gitignore* dosyasından okunan ayarlar, ana dizinine ve tüm alt dizinlere uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ için CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE başvurusu](/cpp/build/reference/nmake-reference)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
