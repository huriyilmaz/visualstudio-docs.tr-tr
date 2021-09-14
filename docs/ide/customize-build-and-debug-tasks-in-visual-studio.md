---
title: JSON dosyalarıyla derleme hata ayıklama görevlerini özelleştirme
description: Bazı yapılandırma ayrıntılarını sağlamak için görevleri özelleştirmeyi ve bu temelin tanımadığını Visual Studio hata ayıklamayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d05ffcc5140edcf04dd03b591df100831304fc6b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628809"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>"Klasör Aç" geliştirme için derleme ve hata ayıklama görevlerini özelleştirme

Visual Studio dil ve kod tabanı çalıştırmayı bilir, ancak her şeyi nasıl çalıştıracaklarını bilmiyor. [Visual Studio'de](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) bir kod Visual Studio açtıysanız ve kodunuzun nasıl çalıştırılamadı yapılandırmasını biliyorsanız, herhangi bir ek yapılandırmaya gerek kalmadan hemen çalıştırabilirsiniz.

Kod temeli, Visual Studio tanımaz özel derleme araçları kullanıyorsa, kod üzerinde çalıştırmak ve hata ayıklamak için bazı yapılandırma ayrıntılarını Visual Studio. Derleme görevlerini tanımlayarak Visual Studio nasıl derlemeniz *gerektirebilirsiniz?* Bir dilin kodunu derlemesi ve çalıştırması için gereken tüm öğeleri belirtmek için bir veya daha fazla derleme görevi oluşturabilirsiniz. Ayrıca, neredeyse istediğiniz her şeyi gerçekleştirebilir rastgele görevler de oluşturabilirsiniz. Örneğin, bir klasörün içeriğini listeleye veya bir dosyayı yeniden adlandırmaya yönelik bir görev oluşturabilirsiniz.

Aşağıdaki *.json* dosyalarını kullanarak projeniz olmayan kod tabanınızı özelleştirin:

|Dosya adı|Amaç|
|-|-|
|*tasks.vs.json*|Özel derleme komutlarını ve derleyici anahtarlarını ve rastgele (derlemeyle ilgili olmayan) görevleri belirtin.<br>Görevler'i **Çözüm Gezgini** menü öğesi aracılığıyla **erişilir.**|
|*launch.vs.json*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>Uygulama aracılığıyla **erişilen Çözüm Gezgini** menü öğesi hata ayıkla ve **Başlat'a Ayarlar.**|

Bu *.json* dosyaları, kod tabanının kök klasöründe *.vs* adlı gizli bir klasörde bulunur. *tasks.vs.json* ve *launch.vs.json* dosyaları, Visual Studio'de bir dosya veya klasörde Görevleri  Yapılandır  veya Hata Ayıkla ve Ayarlar'yi Başlat'ı seçerek gerektiğinde **Çözüm Gezgini.** Kullanıcılar genellikle bunları kaynak denetimine almak istemediklerine göre bu *.json* dosyaları gizlenir. Ancak, bunları kaynak denetimine kontrol etmek için dosyaları kod tabanının köküne sürükleyin ve burada görünürler.

> [!TIP]
> Dosya çubuğunda gizli Visual Studio görüntülemek için, araç **çubuğundaki** Tüm Dosyaları Göster **Çözüm Gezgini** seçin.

## <a name="define-tasks-with-tasksvsjson"></a>tasks.vs.json ile görevleri tanımlama

Derleme betiklerini veya geçerli çalışma alanınıza sahip dosyalarınız üzerinde herhangi bir dış işlemi doğrudan IDE'de görev olarak çalıştırarak otomatik hale ebilirsiniz. Bir dosya veya klasöre sağ tıklar ve Görevleri Yapılandır'ı seçerek yeni bir **görev yapılandırabilirsiniz.**

![Görevleri Yapılandır menüsü](../ide/media/customize-configure-tasks-menu.png)

Bu işlem, .vs klasöründe *tasks.vs.json* dosyasını oluşturur *(veya* açar). Bu dosyada bir derleme görevi veya rastgele görev tanımlayabilir ve ardından sağ tıklama  menüsünden Çözüm Gezgini çağırabilirsiniz.

Özel görevler tek tek dosyalara veya belirli bir türe sahip tüm dosyalara eklenebilir. Örneğin, NuGet dosyaları bir "Paketleri Geri Yükle" görevine sahip olacak şekilde ya da tüm kaynak dosyalar, tüm paket dosyaları için bir linter gibi statik bir analiz görevi olacak *şekilde ya*.jsolabilir.

### <a name="define-custom-build-tasks"></a>Özel derleme görevleri tanımlama

Kod tabanınız, Visual Studio tanımaz özel derleme araçları kullanıyorsa, bazı yapılandırma adımlarını tamamlayana kadar kodu Visual Studio içinde çalıştıramaz ve hata ayıkamazsiniz. Visual Studio, kodunuzu *derleme,* yeniden derleme ve temizleme Visual Studio anlatabilirsiniz derleme görevleri sağlar. *tasks.vs.json* derleme görev dosyası, iç Visual Studio döngüyü kod tabanınız tarafından kullanılan özel derleme araçlarına eşler.

*hello.cs* adlı tek bir C# dosyasından oluşan bir kod tabanı düşünün. Böyle *bir kod* temeli için makefile şöyle olabilir:

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

Derleme, *temizleme ve yeniden* derleme hedeflerini içeren böyle bir derleme dosyası için aşağıdaki *tasks.vs.json dosyasını tanımlayabilirsiniz.* Derleme aracı olarak NMAKE kullanarak kod tabanını oluşturmak, yeniden derlemek ve temizlemek için üç derleme görevi içerir.

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

*tasks.vs.json'da* derleme görevleri tanımladığınız zaman, öğesinde ilgili dosyalara sağ tıklama menüsü (bağlam menüsü) **Çözüm Gezgini.** Bu örnekte, herhangi bir derleme dosyası dosyasının bağlam menüsüne "derleme", "yeniden derleme" ve *"temizleme" seçenekleri* eklenir.

![derleme, yeniden derleme ve temizleme ile derleme dosyası bağlam menüsü](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Komutların ayarları nedeniyle Görevleri Yapılandır **komutunun altındaki** bağlam menüsünde `contextType` görünür. "build", "rebuild" ve "clean" derleme komutlarıdır, bu nedenle bağlam menüsünün ortasındaki derleme bölümünde görünürler.

Bu seçeneklerden birini seçerek görev yürütülür. Çıkış, Çıkış **penceresinde,** derleme hataları ise Hata Listesinde **görünür.**

### <a name="define-arbitrary-tasks"></a>Rastgele görevler tanımlama

Tam olarak istediğiniz her şeyi yapmak için *tasks.vs.json* dosyasında rastgele görevler tanımlayabilirsiniz. Örneğin, o anda seçili olan dosyanın adını Çıkış penceresinde  görüntülemek veya belirtilen dizinde dosyaları listeleyecek bir görev tanımlayabilirsiniz.

Aşağıdaki örnek, tek bir *görevi tanımlayan tasks.vs.json* dosyasını gösterir. Çağrıldığında, görev seçili durumdaki dosyanın dosya *adını*.jsgörüntüler.

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

- `taskName` sağ tıklama menüsünde görünen adı belirtir.
- `appliesTo` komutun hangi dosyalarda gerçekleştirile olduğunu belirtir.
- `command`özelliği, çağrılan komutu belirtir. Bu örnekte, ortam `COMSPEC` değişkeni genellikle komut satırı yorumlayıcıyı ** tanımlamak için kullanılır vecmd.exe.
- `args`özelliği, çağrılan komuta geçirilen bağımsız değişkenleri belirtir.
- Makro, `${file}` seçilen dosyayı **dosyasından Çözüm Gezgini.**

*tasks.vs.json dosyasını* kaydeddikten sonra klasördeki herhangi bir *.js* tıklar ve Echo dosya **adı'yı seçebilirsiniz.** Dosya adı Çıkış **penceresinde** görüntülenir.

> [!NOTE]
> Kod tabanınız *bir tasks.vs.json* dosyası içeriyorsa, içinde bir  dosyanın sağ tıklama veya bağlam menüsünden Görevleri Yapılandır'ı seçerek bir **tane Çözüm Gezgini.**

Sonraki örnek, bin dizininin dosyalarını ve alt klasörlerini listeleye bir *görev* tanımlar.

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

- `${outDir}` , ilk olarak blok öncesinde tanımlanan özel bir `tasks` makro. Ardından özelliğinde `args` çağrılır.

Bu görev tüm dosyalar için geçerlidir. Çözüm Gezgini'da herhangi bir dosyada bağlam menüsünü Çözüm Gezgini, görevin  adı men altında görüntülenir. Çıkışları **Listele'yi** seçerseniz, bin *dizininin* içeriği, **dizinde yer** alan Çıkış penceresinde Visual Studio.

![Bağlam menüsünde rastgele görev](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayarlar kapsamı

Bir kod tabanının kökünde ve alt dizininde birden çok *tasks.vs.json* dosyası olabilir. Bu tasarım, esnekliğin kod tabanının farklı alt dizinlerde farklı davranışa sahip olmasına olanak sağlar. Visual Studio tüm ayarları toplar veya geçersiz kılar ve dosyalara aşağıdaki sırayla önceliklerini ayarlar:

- Ayarlar klasörünün *.vs* dizinindeki dosyaları seçin.
- Bir ayarın hesapta olduğu dizin.
- Geçerli dizinin üst dizini, kök dizine kadar.
- Ayarlar dizine dosya ekler.

Bu toplama kuralları *tasks.vs.json için geçerlidir.* Diğer dosya ayarlarının nasıl toplanmış olduğu hakkında bilgi için bu makalede bu dosyaya karşılık gelen bölüme bakın.

### <a name="properties-for-tasksvsjson"></a>tasks.vs.json özellikleri

Bu *bölümde, tasks.vs.json içinde belirtebilirsiniz bazı özellikler açıklanmış olur.*

#### <a name="appliesto"></a>Appliesto

Alanında adını belirterek herhangi bir dosya veya klasör için görevler `appliesTo` oluşturabilirsiniz, örneğin `"appliesTo": "hello.js"` . Aşağıdaki dosya maskeleri değer olarak kullanılabilir:

|Dosya maskesi|Description|
|-|-|
|`"*"`| görevi çalışma alanında tüm dosya ve klasörler için kullanılabilir|
|`"*/"`| görevi çalışma alanında tüm klasörler için kullanılabilir|
|`"*.js"`| görev, çalışma alanında uzantılı tüm *.js* kullanılabilir|
|`"/*.js"`| görev, çalışma alanının kökünde *uzantı.js* tüm dosyalar tarafından kullanılabilir|
|`"src/*/"`| görevi, *src* klasörünün tüm alt klasörleri tarafından kullanılabilir|
|`"makefile"`| görevi çalışma alanı içinde *tüm makefile* dosyaları için kullanılabilir|
|`"/makefile"`| görevi yalnızca çalışma alanının kökünde bulunan *makefile* için kullanılabilir|

#### <a name="macros-for-tasksvsjson"></a>tasks.vs.json makroları

|Makro|Description|
|-|-|
|`${env.<VARIABLE>}`| Herhangi bir ortam değişkenlerini belirtir (örneğin, ${env. Geliştirici komut istemi için ayarlanmış PATH}, ${env.COMSPEC} gibi). Daha fazla bilgi için [bkz. Geliştirici Komut İstemi Geliştirici PowerShell](../ide/reference/command-prompt-powershell.md).|
|`${workspaceRoot}`| Çalışma alanı klasörünün tam yolu (örneğin, *C:\sources\hello*)|
|`${file}`| Bu görevi çalıştırmak için seçilen dosyanın veya klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Dosya veya klasörün göreli yolu (örneğin, *src\hello.js*)|
|`${fileBasename}`| Dosyanın yolu veya uzantısı olmayan adı (örneğin, *Merhaba*)|
|`${fileDirname}`| Dosya adı hariç dosyanın tam yolu (örneğin, *C:\sources\hello\src*)|
|`${fileExtname}`| Seçilen dosyanın uzantısı (örneğin,  *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Launch. vs. JSON ile hata ayıklamayı yapılandırma

CMake projelerini hata ayıklama için yapılandırmak için bkz. [CMake hata ayıklama oturumlarını yapılandırma](/cpp/build/configure-cmake-debugging-sessions).

1. kod tabanınızı hata ayıklama için yapılandırmak için, **Çözüm Gezgini** içinde, çalıştırılabilir dosyanızın sağ tıklama veya bağlam menüsünden **hata ayıkla ve başlat Ayarlar** menü öğesini seçin.

   ![hata ayıklama ve Ayarlar bağlam menüsü başlatma](media/customize-debug-launch-menu.png)

1. **Hata ayıklayıcı Seç** iletişim kutusunda bir seçenek belirleyin ve ardından **Seç** düğmesini seçin.

   ![Bir hata ayıklayıcı iletişim kutusu seçin](media/customize-select-a-debugger.png)

   *Launch. vs. JSON* dosyası zaten yoksa, oluşturulur.

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

1. Sonra, **Çözüm Gezgini**' de çalıştırılabilir dosyaya sağ tıklayın ve **Başlangıç öğesi olarak ayarla**' yı seçin.

   Yürütülebilir dosya, kod tabanınız için başlangıç öğesi olarak atanır ve hata ayıklama **Başlangıç** düğmesinin başlığı, yürütülebilir dosyanızın adını yansıtacak şekilde değişir.

   ![Özelleştirilmiş Başlangıç düğmesi](media/customize-start-button.png)

   **F5**' i seçtiğinizde, hata ayıklayıcı önceden ayarlamış olduğunuz herhangi bir kesme noktasında başlatılır ve duraklar. Tüm tanıdık hata ayıklayıcı pencereleri kullanılabilir ve çalışır.

   > [!IMPORTANT]
   > C++ açık klasör projelerinde özel derleme ve hata ayıklama görevleriyle ilgili ek ayrıntılar için, bkz. [Visual Studio Içindeki c++ derleme sistemleri Için klasör açma desteği](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Hata ayıklama için bağımsız değişkenler belirtin

*Launch. vs. JSON* dosyasında hata ayıklama için geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz. `args`Aşağıdaki örnekte gösterildiği gibi, dizideki bağımsız değişkenleri ekleyin:

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

Bu dosyayı kaydettiğinizde, yeni yapılandırmanın adı hata ayıklama hedefi açılır listesinde görünür ve hata ayıklayıcıyı başlatmak için bunu seçebilirsiniz. Dilediğiniz kadar çok hata ayıklama yapılandırması oluşturabilirsiniz.

![Hata ayıklama yapılandırması açılan listesi](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` *Launch. vs. JSON* ' daki Array özelliği, iki dosya konumundan &mdash; , kod temeli için kök dizin ve *. vs* Directory tarafından okundu. Bir çakışma varsa, *. vs\launch.vs.JSON* içindeki değere öncelik verilir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

bu konuda açıklanan üç *. json* dosyasına ek olarak Visual Studio, kod tabanınızda varsa bazı ek dosyalardan da ayarları okur.

### <a name="vscodesettingsjson"></a>. vscode\settings.JSON

Visual Studio, *. vscode* adlı bir dizinde olan *settings. json* adlı bir dosyadaki sınırlı ayarları okur. Bu işlevsellik, daha önce Visual Studio Code daha önce geliştirilen codetabanlar için verilmiştir. Şu anda, dosyaları Çözüm Gezgini ve bazı arama araçlarından görsel olarak filtreleyerek *. vscode\settings.JSON* öğesinden okunan tek ayar `files.exclude` .

Kod tabanınızda herhangi bir sayıda *. vscode\settings.JSON* dosyası ekleyebilirsiniz. bu dosyadan okunan Ayarlar, *. vscode* üst dizinine ve tüm alt dizinlerine uygulanır.

### <a name="gitignore"></a>.gitignore

*. gitignore* dosyaları git 'e hangi dosyaların yoksayılacağını bildirmek için kullanılır; diğer bir deyişle, iade etmek istemediğiniz dosya ve dizinler. *. gitignore* dosyaları genellikle kod temelinin tüm geliştiricileriyle paylaşılabilmesi için bir kod temelinin parçası olarak dahil edilir. Visual Studio, öğeleri görsel olarak ve bazı arama araçlarından filtrelemek için *. gitignore* dosyalarındaki desenleri okur.

*. gitignore* dosyasından okunan Ayarlar, üst dizinine ve tüm alt dizinlere uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ için CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE başvurusu](/cpp/build/reference/nmake-reference)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
