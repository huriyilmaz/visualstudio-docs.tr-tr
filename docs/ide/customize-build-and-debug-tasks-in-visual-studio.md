---
title: JSON dosyalarıyla derleme hata ayıklama görevlerini özelleştirme
description: Visual Studio tanımadığı bir kod temeli çalıştırmak ve hata ayıklamak üzere görevleri özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/21/2022
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
ms.openlocfilehash: 59f27edc76a0a7d42bf988961f90f8812c44b0c2
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650404"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>"Klasör aç" geliştirmesi için derleme ve hata ayıklama görevlerini özelleştirin

Visual Studio birçok farklı dili ve kod esaslarını çalıştırmayı bilir, ancak her şeyin nasıl çalıştırılacağını bilmez. Visual Studio [bir kod klasörünü açtıysanız](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Visual Studio ve kodunuzu nasıl çalıştıracağınızı biliyorsanız, ek bir yapılandırma olmadan hemen çalıştırabilirsiniz.

kod temeli Visual Studio tanımadığı özel yapı araçları kullanıyorsa, çalıştırmak ve Visual Studio kodda hata ayıklamak için bazı yapılandırma ayrıntılarını sağlamanız gerekir. *derleme görevlerini* tanımlayarak kodunuzun nasıl oluşturulacağını Visual Studio söyleyebilirsiniz. Bir dilin kodunu derlemek ve çalıştırmak için gereken tüm öğeleri belirtmek için bir veya daha fazla yapı görevi oluşturabilirsiniz. İstediğiniz neredeyse her şeyi yapabildiği rastgele görevler de oluşturabilirsiniz. Örneğin, bir klasörün içeriğini listelemek veya bir dosyayı yeniden adlandırmak için bir görev oluşturabilirsiniz.

Aşağıdaki *. JSON* dosyalarını kullanarak proje-Less kod tabanınızı özelleştirin:

|Dosya adı|Amaç|
|-|-|
|*Tasks. vs. JSON*|Özel derleme komutları ve derleyici anahtarları ve rastgele (derleme olmayan ilişkili) görevleri belirtin.<br>**Çözüm Gezgini** sağ tıklama menü öğesi **görevleri Yapılandır**' ı kullanarak erişilir.|
|*Launch. vs. JSON*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>**Çözüm Gezgini** sağ tıklayıp menü öğesi **hata ayıklama ve Ayarlar başlatın**.|

Bu *. JSON* dosyaları, kod tabanınızın kök klasöründe *vs. ile* adlı gizli bir klasörde bulunur. tasks *. vs. json* ve *launch. vs. json* dosyaları, **Çözüm Gezgini**' deki bir dosya veya klasör üzerinde **görevleri yapılandır** veya **hata ayıkla ve Ayarlar başlat ' ı** seçerek Visual Studio tarafından gerekli bir şekilde oluşturulur. Kullanıcılar genellikle kaynak denetimine denetlemek istemediğinden, bu *. JSON* dosyaları gizlidir. Ancak, bunları kaynak denetimine denetleyebilmek istiyorsanız dosyaları dosya sisteminizden veya Çözüm Gezgini kod tabanınızın köküne sürükleyin ve burada görünür.

> [!TIP]
> gizli dosyaları Visual Studio görüntülemek için, **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** düğmesini seçin.

## <a name="define-tasks-with-tasksvsjson"></a>Görevler. vs. JSON ile görevleri tanımlama

Mevcut çalışma alanınızda bulunan dosyalar üzerinde, derleme betikleri veya diğer dış işlemleri otomatikleştirebilir ve bunları doğrudan IDE 'de görevler olarak çalıştırabilirsiniz. Bir dosya veya klasöre sağ tıklayıp **görevleri Yapılandır**' ı seçerek yeni bir görev yapılandırabilirsiniz.

![Görevler menüsünü Yapılandır](../ide/media/customize-configure-tasks-menu.png)

Bu, *. vs* klasöründeki *Tasks. vs. JSON* dosyasını oluşturur (veya açar). Bu dosyada bir yapı görevi veya rastgele bir görev tanımlayabilir ve sonra **Çözüm Gezgini** sağ tıklama menüsünde bunu verdiğiniz adı kullanarak çağırabilirsiniz.

Özel görevler tek tek dosyalara veya belirli bir türdeki tüm dosyalara eklenebilir. örneğin, NuGet paket dosyaları bir "paket geri yükleme" görevine sahip olacak şekilde yapılandırılabilir veya tüm kaynak dosyaları, tüm *.js* dosyaları için bir kater gibi bir statik analiz görevine sahip olacak şekilde yapılandırılabilir.

### <a name="define-custom-build-tasks"></a>Özel derleme görevlerini tanımlama

kod tabanınız Visual Studio tanımadığı özel yapı araçları kullanıyorsa, bazı yapılandırma adımlarını tamamlayana kadar Visual Studio kodu çalıştıramazsınız ve hatalarını ayıklayamazsınız. Visual Studio, kodunuzu oluşturma, yeniden oluşturma ve temizleme Visual Studio söyleyebileceğiniz *derleme görevleri* sağlar. *tasks. vs. json* derleme görev dosyası, Visual Studio iç geliştirme döngüsünü kod tabanınızın kullandığı özel derleme araçlarına bağar.

*Hello. cs* adlı tek bir C# dosyasından oluşan bir kod temeli düşünün. Böyle bir kod temeli için *derleme görevleri dosyası* şöyle görünebilir:

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

Oluşturma, temizleme ve yeniden oluşturma hedeflerini içeren böyle bir *derleme görevleri* dosyası için, aşağıdaki *Görevler. vs. JSON* dosyasını tanımlayabilirsiniz. Derleme aracı olarak NMAKE kullanarak kod temeli oluşturmaya, yeniden oluşturmaya ve temizlemeye yönelik üç derleme görevi içerir.

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

*Tasks. vs. JSON* içinde derleme görevleri tanımladıktan sonra, **Çözüm Gezgini** ilgili dosyalara sağ tıklama menüsü (bağlam menüsü) öğeleri eklenir. Bu örnek için, "derleme", "yeniden derleme" ve "Temizleme" seçenekleri, *derleme görevleri* dosyası dosyalarının bağlam menüsüne eklenir.

![derleme, yeniden oluşturma ve Temizleme ile derleme görevleri dosyası bağlam menüsü](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Komutlar, ayarları nedeniyle **görevleri Yapılandır** komutunun altındaki bağlam menüsünde görüntülenir `contextType` . "derleme", "yeniden derleme" ve "Temizleme" yapı komutlardır, bu nedenle bağlam menüsünün ortasındaki derleme bölümünde görünürler.

Bu seçeneklerden birini belirlediğinizde, görev yürütülür. Çıktı, **Çıkış** penceresinde görünür ve derleme hataları **hata listesi** görüntülenir.

### <a name="define-arbitrary-tasks"></a>Rastgele görevleri tanımlama

Yalnızca istediğiniz herhangi bir şeyi yapmak için *Tasks. vs. JSON* dosyasında rastgele görevler tanımlayabilirsiniz. Örneğin, seçili dosyanın adını **Çıkış** penceresinde göstermek veya belirtilen bir dizindeki dosyaları listelemek için bir görev tanımlayabilirsiniz.

Aşağıdaki örnek, tek bir görevi tanımlayan *Tasks. vs. JSON* dosyasını gösterir. Çağrıldığında, görev seçili olan *.js* dosyanın dosya adını görüntüler.

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

- `taskName` sağ tıklama menüsünde görüntülenen adı belirtir.
- `appliesTo` komutun hangi dosyalara uygulanabilir olduğunu belirtir.
- `command`Özelliği çağrılacak komutu belirtir. Bu örnekte, `COMSPEC` ortam değişkeni, genellikle *cmd.exe* komut satırı yorumlayıcısını belirlemek için kullanılır.
- `args`Özelliği, çağrılan komuta geçirilecek bağımsız değişkenleri belirtir.
- `${file}`Makro seçili dosyayı **Çözüm Gezgini** alır.

*Tasks. vs. JSON* dosyasını kaydettikten sonra, klasördeki herhangi bir *.js* dosyasına sağ tıklayıp **yankı dosya adı**' nı seçebilirsiniz. Dosya adı **Çıkış** penceresinde görüntülenir.

> [!NOTE]
> Kod tabanınız bir *Tasks. vs. JSON* dosyası içermiyorsa, **Çözüm Gezgini** bir dosyanın sağ tıklama veya bağlam menüsünden **görevleri Yapılandır** ' ı seçerek bir tane oluşturabilirsiniz.

Sonraki örnek, *bin* dizininin dosyalarını ve alt klasörlerini listeleyen bir görevi tanımlar.

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

- `${outDir}` , bloğundan önce ilk tanımlanan özel bir makrodur `tasks` . Daha sonra `args` özelliğinde çağırılır.

Bu görev tüm dosyalar için geçerlidir. **Çözüm Gezgini** bir dosya üzerinde bağlam menüsünü açtığınızda, görevin ad **listesi çıktıları** menünün alt kısmında görünür. **Liste çıktıları**' nı seçtiğinizde, *bin* dizininin Içeriği Visual Studio ' deki **Çıkış** penceresinde listelenir.

![Bağlam menüsünde rastgele görev](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayarlar kapsamı

Birden çok *görev. vs. JSON* dosyası, bir kod temelinin kökünde ve alt dizinlerinde bulunabilir. Bu tasarım, kod temelinin farklı alt dizinlerinde farklı davranışa sahip olmak için esneklik sağlar. , dosyaları aşağıdaki sırada önceliklendirerek, kod temeli boyunca toplamaları veya geçersiz kılma ayarlarını Visual Studio:

- kök klasörün *. vs* dizinindeki dosyaları Ayarlar.
- Bir ayarın hesaplandığı dizin.
- Kök dizine kadar olan geçerli dizinin üst dizini.
- kök dizindeki dosyaları Ayarlar.

Bu toplama kuralları *Tasks. vs. JSON* için geçerlidir. Diğer dosyadaki ayarların nasıl toplandığından ilgili bilgi için, bu makaledeki dosyanın ilgili bölümüne bakın.

### <a name="properties-for-tasksvsjson"></a>Tasks. vs. JSON için Özellikler

Bu bölümde, *Tasks. vs. JSON* içinde belirtebileceğiniz özelliklerden bazıları açıklanmaktadır.

#### <a name="appliesto"></a>appliesTo

Alanında adını belirterek herhangi bir dosya veya klasör için görevler oluşturabilirsiniz `appliesTo` , örneğin `"appliesTo": "hello.js"` . Aşağıdaki dosya maskeleri değer olarak kullanılabilir:

|Dosya maskesi|Description|
|-|-|
|`"*"`| görev, çalışma alanındaki tüm dosya ve klasörler için kullanılabilir|
|`"*/"`| görev, çalışma alanındaki tüm klasörler için kullanılabilir|
|`"*.js"`| görev, çalışma alanındaki uzantıya *.js* tüm dosyalar için kullanılabilir|
|`"/*.js"`| görev, uzantı *.js* çalışma alanının kökündeki tüm dosyalar için kullanılabilir|
|`"src/*/"`| görev *src* klasörünün tüm alt klasörlerinde kullanılabilir|
|`"makefile"`| görev, çalışma alanındaki tüm *derleme görevleri* dosyası dosyaları için kullanılabilir|
|`"/makefile"`| görev yalnızca çalışma alanının kökündeki *derleme görevleri dosyası* tarafından kullanılabilir|

#### <a name="macros-for-tasksvsjson"></a>Görevler için makrolar. vs. JSON

|Makroya|Description|
|-|-|
|`${env.<VARIABLE>}`| Herhangi bir ortam değişkenini belirtir (örneğin, $ {env. YOL}, $ {env. COMSPEC} ve benzeri) Geliştirici komut istemi için ayarlanır. Daha fazla bilgi için bkz. [Geliştirici komut istemi ve geliştirici PowerShell](../ide/reference/command-prompt-powershell.md).|
|`${workspaceRoot}`| Çalışma alanı klasörünün tam yolu (örneğin, *C:\sources\hello*)|
|`${file}`| Bu görevi çalıştırmak için seçilen dosya veya klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Dosya veya klasörün göreli yolu (örneğin, *src\hello.js*)|
|`${fileBasename}`| Yol veya uzantı olmadan dosyanın adı (örneğin, *hello*)|
|`${fileDirname}`| Dosya adı hariç dosyanın tam yolu (örneğin, *C:\sources\hello\src*)|
|`${fileExtname}`| Seçilen dosyanın uzantısı (örneğin,  *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Launch.vs.json ile hata ayıklamayı yapılandırma

CMake projelerini hata ayıklama için yapılandırmak için [bkz. CMake hata ayıklama oturumlarını yapılandırma.](/cpp/build/configure-cmake-debugging-sessions)

1. Kod tabanınızı hata ayıklama için yapılandırmak **üzere,**  Çözüm Gezgini dosyanın sağ tıklama veya bağlam menüsünden Hata Ayıkla ve Ayarlar Başlat menü öğesini seçin.

   ![Hata Ayıklama ve Ayarlar başlat bağlam menüsü](media/customize-debug-launch-menu.png)

1. Hata **Ayıklayıcı Seçin iletişim** kutusunda bir seçenek belirleyin ve ardından Seç **düğmesini** seçin.

   ![Hata Ayıklayıcı iletişim kutusu seçin](media/customize-select-a-debugger.png)

   *launch.vs.json* dosyası zaten yoksa oluşturulur.

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

1. Ardından, dosyasındaki yürütülebilir dosyaya sağ **tıklayın Çözüm Gezgini** Başlangıç Öğesi Olarak **Ayarla'yı seçin.**

   Yürütülebilir dosya, kod tabanınız için başlangıç öğesi olarak belirlenmiştir ve hata ayıklama **Başlat** düğmesinin başlığı yürütülebilir dosyanın adını yansıtacak şekilde değişir.

   ![Özelleştirilmiş Başlat düğmesi](media/customize-start-button.png)

   **F5'i seçerseniz,** hata ayıklayıcı zaten ayarlamış olduğunuz herhangi bir kesme noktası üzerinde başlat ve durur. Tüm tanıdık hata ayıklayıcı pencereleri kullanılabilir ve işlevseldir.

   > [!IMPORTANT]
   > C++ açık klasör projelerinde özel derleme ve hata ayıklama görevleri hakkında ek ayrıntılar için bkz. C++ derleme sistemleri için Klasör Aç [desteği Visual Studio.](/cpp/build/open-folder-projects-cpp)

### <a name="specify-arguments-for-debugging"></a>Hata ayıklama için bağımsız değişkenleri belirtme

*launch.vs.json* dosyasında hata ayıklama için geçiş yapmak için komut satırı bağımsız değişkenleri belirtebilirsiniz. Aşağıdaki örnekte gösterildiği gibi `args` bağımsız değişkenleri diziye ekleyin:

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

Bu dosyayı kaydederek hata ayıklama hedefi açılan listesinde yeni yapılandırmanın adı görünür ve hata ayıklayıcıyı başlatmak için bu dosyayı seçebilirsiniz. Ne kadar çok hata ayıklama yapılandırması oluşturabilirsiniz?

![Yapılandırmalarda hata ayıklama açılan listesi](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` *launch.vs.json* dosyasındaki array özelliği, kod tabanının kök dizininde ve .vs dizininde yer alan &mdash; *iki dosya konumdan* okunur. Bir çakışma varsa, *.vs\launch.vs.json* konumundaki değere öncelik verilir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

Bu konuda açıklanan *üç .json* dosyasına ek olarak, Visual Studio kod tabanınız içinde mevcutsa bazı ek dosyalardan da ayarları okur.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio, *.vscode* adlı bir dizinde yer alan *settings.json* adlı bir dosyadan sınırlı ayarları okur. Bu işlevsellik, daha önce bu hizmette geliştirilmiş olan kod temelleri Visual Studio Code. Şu anda *,vscode\settings.json'dan* okunan tek ayar, dosyaları bazı arama `files.exclude` araçlarında Çözüm Gezgini filtreleyerek özelliğidir.

Kod tabanınıza istediğiniz *sayıda .vscode\settings.json* dosyası girebilirsiniz. Ayarlar dosyadan okunan her şey *.vscode'ın* üst dizinine ve tüm alt dizinlerine uygulanır.

### <a name="gitignore"></a>.gitignore

*.gitignore* dosyaları Git'e hangi dosyaların yoksaymak zorunda olduğunu söylemek için kullanılır; başka bir ifadeyle, hangi dosyaları ve dizinleri iade etmek istemeyebilirsiniz? *.gitignore* dosyaları genellikle bir kod tabanının parçası olarak dahil edilir, böylece ayarlar kod tabanının tüm geliştiricileriyle paylaşılır. Visual Studio ve bazı arama araçlarından öğeleri filtrelemek için *.gitignore* dosyalarında desenleri okur.

Ayarlar *.gitignore dosyasından* okunan her şey, üst dizinine ve tüm alt dizinlerine uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ için CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE başvurusu](/cpp/build/reference/nmake-reference)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
