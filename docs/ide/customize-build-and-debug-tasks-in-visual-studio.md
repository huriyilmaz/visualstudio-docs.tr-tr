---
title: Görevleri kullanarak derleme hata ayıklama görevlerini özelleştirin. vs. JSON Launch. vs. JSON
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a9101db18c8c61f249d9f0b818a75024270a079
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652569"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>"Klasör aç" geliştirmesi için derleme ve hata ayıklama görevlerini özelleştirin

Visual Studio birçok farklı dili ve kod esaslarını nasıl çalıştıracağınızı bilir, ancak her şeyin nasıl çalıştırılacağını bilmez. Visual Studio 'da [bir kod klasörü açtıysanız](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) ve Visual Studio kodunuzun nasıl çalıştırılacağını biliyorsa, ek bir yapılandırma olmadan hemen çalıştırabilirsiniz.

Kod temeli, Visual Studio 'Nun tanımadığı özel yapı araçları kullanıyorsa, Visual Studio 'da kodun çalıştırılması ve hata ayıklaması için bazı yapılandırma ayrıntılarını sağlamanız gerekir. Visual Studio 'Nun *derleme görevlerini*tanımlayarak kodunuzun nasıl oluşturulacağını söyleyebilirsiniz. Bir dilin kodunu derlemek ve çalıştırmak için gereken tüm öğeleri belirtmek için bir veya daha fazla yapı görevi oluşturabilirsiniz. İstediğiniz neredeyse her şeyi yapabildiği rastgele görevler de oluşturabilirsiniz. Örneğin, bir klasörün içeriğini listelemek veya bir dosyayı yeniden adlandırmak için bir görev oluşturabilirsiniz.

Aşağıdaki *. JSON* dosyalarını kullanarak proje-Less kod tabanınızı özelleştirin:

|Dosya adı|Amaç|
|-|-|
|*Tasks. vs. JSON*|Özel derleme komutları ve derleyici anahtarları ve rastgele (derleme olmayan ilişkili) görevleri belirtin.<br>**Çözüm Gezgini** sağ tıklama menü öğesi **görevleri Yapılandır**' ı kullanarak erişilir.|
|*Launch. vs. JSON*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>**Çözüm Gezgini** menü öğesi **hata ayıklama ve başlatma ayarları**' na sağ tıklayın.|

Bu *. JSON* dosyaları, kod tabanınızın kök klasöründe *vs. ile* adlı gizli bir klasörde bulunur. Tasks *. vs. JSON* ve *Launch. vs. json* dosyaları, **Çözüm Gezgini**bir dosya veya klasör üzerinde **görevleri yapılandırma** veya **hata ayıklama ve başlatma ayarlarını** seçtiğinizde, Visual Studio tarafından gerekli bir şekilde oluşturulur. Kullanıcılar genellikle kaynak denetimine denetlemek istemediğinden, bu *. JSON* dosyaları gizlidir. Ancak onları kaynak denetimine denetleyebilmek istiyorsanız, dosyaları görünür oldukları kod tabanınızın köküne sürükleyin.

> [!TIP]
> Visual Studio 'da gizli dosyaları görüntülemek için **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** düğmesini seçin.

## <a name="define-tasks-with-tasksvsjson"></a>Görevler. vs. JSON ile görevleri tanımlama

Mevcut çalışma alanınızda bulunan dosyalar üzerinde, derleme betikleri veya diğer dış işlemleri otomatikleştirebilir ve bunları doğrudan IDE 'de görevler olarak çalıştırabilirsiniz. Bir dosya veya klasöre sağ tıklayıp **görevleri Yapılandır**' ı seçerek yeni bir görev yapılandırabilirsiniz.

![Görevler menüsünü Yapılandır](../ide/media/customize-configure-tasks-menu.png)

Bu, *. vs* klasöründeki *Tasks. vs. JSON* dosyasını oluşturur (veya açar). Bu dosyada bir yapı görevi veya rastgele bir görev tanımlayabilir ve sonra **Çözüm Gezgini** sağ tıklama menüsünde bunu verdiğiniz adı kullanarak çağırabilirsiniz.

Özel görevler tek tek dosyalara veya belirli bir türdeki tüm dosyalara eklenebilir. Örneğin, NuGet paket dosyaları bir "paket geri yükleme" görevine sahip olacak şekilde yapılandırılabilir veya tüm kaynak dosyaları, tüm *. js* dosyaları için bir Kater gibi bir statik analiz görevine sahip olacak şekilde yapılandırılabilir.

### <a name="define-custom-build-tasks"></a>Özel derleme görevlerini tanımlama

Kod tabanınız Visual Studio 'Nun tanımadığı özel yapı araçları kullanıyorsa, bazı yapılandırma adımlarını tamamlayana kadar Visual Studio 'da kodu çalıştıramazsınız ve hata ayıklayamazsınız. Visual Studio, Visual Studio 'Nun kodunuzu nasıl derleyeceğini, yeniden derleyeceğini ve temizleyeceğini söyleyebileceğiniz *derleme görevleri* sağlar. *Tasks. vs. JSON* derleme görev dosyası, Visual Studio iç geliştirme döngüsünü kod tabanınızın kullandığı özel derleme araçlarına bağar.

C# *Hello.cs*adlı tek bir dosyadan oluşan bir kod temeli düşünün. Böyle bir kod temeli için *derleme görevleri dosyası* şöyle görünebilir:

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

*Tasks. vs. JSON*içinde derleme görevleri tanımladıktan sonra, **Çözüm Gezgini**ilgili dosyalara sağ tıklama menüsü (bağlam menüsü) öğeleri eklenir. Bu örnek için, "derleme", "yeniden derleme" ve "Temizleme" seçenekleri, *derleme görevleri* dosyası dosyalarının bağlam menüsüne eklenir.

![derleme, yeniden oluşturma ve Temizleme ile derleme görevleri dosyası bağlam menüsü](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Komutlar, `contextType` ayarları nedeniyle **görevleri Yapılandır** komutunun altındaki bağlam menüsünde görüntülenir. "derleme", "yeniden derleme" ve "Temizleme" yapı komutlardır, bu nedenle bağlam menüsünün ortasındaki derleme bölümünde görünürler.

Bu seçeneklerden birini belirlediğinizde, görev yürütülür. Çıktı, **Çıkış** penceresinde görünür ve derleme hataları **hata listesi**görüntülenir.

### <a name="define-arbitrary-tasks"></a>Rastgele görevleri tanımlama

Yalnızca istediğiniz herhangi bir şeyi yapmak için *Tasks. vs. JSON* dosyasında rastgele görevler tanımlayabilirsiniz. Örneğin, seçili dosyanın adını **Çıkış** penceresinde göstermek veya belirtilen bir dizindeki dosyaları listelemek için bir görev tanımlayabilirsiniz.

Aşağıdaki örnek, tek bir görevi tanımlayan *Tasks. vs. JSON* dosyasını gösterir. Çağrıldığında, görev seçili olan *. js* dosyasının dosya adını görüntüler.

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
- `appliesTo`, komutun hangi dosyalara gerçekleştirileceğini belirtir.
- @No__t_0 özelliği çağrılacak komutu belirtir. Bu örnekte, `COMSPEC` ortam değişkeni, genellikle *cmd. exe*komut satırı yorumlayıcısını belirlemek için kullanılır.
- @No__t_0 özelliği, çağrılan komuta geçirilecek bağımsız değişkenleri belirtir.
- @No__t_0 makrosu seçili dosyayı **Çözüm Gezgini**alır.

*Tasks. vs. JSON*dosyasını kaydettikten sonra, klasördeki herhangi bir *. js* dosyasına sağ tıklayıp **yankı dosya adı**' nı seçebilirsiniz. Dosya adı **Çıkış** penceresinde görüntülenir.

> [!NOTE]
> Kod tabanınız bir *Tasks. vs. JSON* dosyası içermiyorsa, **Çözüm Gezgini**bir dosyanın sağ tıklama veya bağlam menüsünden **görevleri Yapılandır** ' ı seçerek bir tane oluşturabilirsiniz.

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

- `${outDir}`, ilk olarak `tasks` bloğundan önce tanımlanan özel bir makrodur. Daha sonra `args` özelliğinde çağırılır.

Bu görev tüm dosyalar için geçerlidir. **Çözüm Gezgini**bir dosya üzerinde bağlam menüsünü açtığınızda, görevin ad **listesi çıktıları** menünün alt kısmında görünür. **Liste çıktıları**' nı seçtiğinizde, *bin* dizininin Içeriği Visual Studio 'daki **Çıkış** penceresinde listelenir.

![Bağlam menüsünde rastgele görev](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayarlar kapsamı

Birden çok *görev. vs. JSON* dosyası, bir kod temelinin kökünde ve alt dizinlerinde bulunabilir. Bu tasarım, kod temelinin farklı alt dizinlerinde farklı davranışa sahip olmak için esneklik sağlar. Visual Studio, dosyaları aşağıdaki sırada önceliklendirerek, kod temeli genelinde ayarları toplar veya geçersiz kılar:

- Kök klasörün *. vs* dizinindeki ayar dosyaları.
- Bir ayarın hesaplandığı dizin.
- Kök dizine kadar olan geçerli dizinin üst dizini.
- Kök dizindeki ayarlar dosyaları.

Bu toplama kuralları *Tasks. vs. JSON*için geçerlidir. Diğer dosyadaki ayarların nasıl toplandığından ilgili bilgi için, bu makaledeki dosyanın ilgili bölümüne bakın.

### <a name="properties-for-tasksvsjson"></a>Tasks. vs. JSON için Özellikler

Bu bölümde, *Tasks. vs. JSON*içinde belirtebileceğiniz özelliklerden bazıları açıklanmaktadır.

#### <a name="appliesto"></a>appliesTo

@No__t_0 alanında adını belirterek herhangi bir dosya veya klasör için görevler oluşturabilirsiniz, örneğin `"appliesTo": "hello.js"`. Aşağıdaki dosya maskeleri değer olarak kullanılabilir:

|||
|-|-|
|`"*"`| görev, çalışma alanındaki tüm dosya ve klasörler için kullanılabilir|
|`"*/"`| görev, çalışma alanındaki tüm klasörler için kullanılabilir|
|`"*.js"`| görev, çalışma alanında *. js* uzantısına sahip tüm dosyalar için kullanılabilir|
|`"/*.js"`| görev, çalışma alanının kökünde *. js* uzantısına sahip tüm dosyalar için kullanılabilir|
|`"src/*/"`| görev *src* klasörünün tüm alt klasörlerinde kullanılabilir|
|`"makefile"`| görev, çalışma alanındaki tüm *derleme görevleri* dosyası dosyaları için kullanılabilir|
|`"/makefile"`| görev yalnızca çalışma alanının kökündeki *derleme görevleri dosyası* tarafından kullanılabilir|

#### <a name="macros-for-tasksvsjson"></a>Görevler için makrolar. vs. JSON

|||
|-|-|
|`${env.<VARIABLE>}`| Herhangi bir ortam değişkenini belirtir (örneğin, $ {env. Geliştirici komut istemi için ayarlanan PATH}, $ {env. COMSPEC} ve benzeri). Daha fazla bilgi için bkz. [Visual Studio Için Geliştirici komut istemi](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Çalışma alanı klasörünün tam yolu (örneğin, *C:\sources\hello*)|
|`${file}`| Bu görevi çalıştırmak için seçilen dosya veya klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.exe*)|
|`${relativeFile}`| Dosya veya klasörün göreli yolu (örneğin, *src\hello.exe*)|
|`${fileBasename}`| Dosyanın yolu veya uzantısı olmayan adı (örneğin, *Merhaba*)|
|`${fileDirname}`| Dosya adı hariç dosyanın tam yolu (örneğin, *C:\sources\hello\src*)|
|`${fileExtname}`| Seçilen dosyanın uzantısı (örneğin, *. js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Launch. vs. JSON ile hata ayıklamayı yapılandırma

1. Kod tabanınızı hata ayıklama için yapılandırmak üzere **Çözüm Gezgini** öğesinde, çalıştırılabilir dosyanızın sağ tıklama veya bağlam menüsünden **hata ayıklama ve başlatma ayarları** menü öğesini seçin.

   ![Hata ayıklama ve başlatma ayarları bağlam menüsü](media/customize-debug-launch-menu.png)

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
   > Açık klasör projelerindeki özel derleme ve hata ayıklama görevleri hakkında ek ayrıntılar için bkz. [Visual Studio 'da derleme C++ sistemleri için klasör açma desteği.](/cpp/build/open-folder-projects-cpp) C++

### <a name="specify-arguments-for-debugging"></a>Hata ayıklama için bağımsız değişkenler belirtin

*Launch. vs. JSON* dosyasında hata ayıklama için geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz. Aşağıdaki örnekte gösterildiği gibi `args` dizisindeki bağımsız değişkenleri ekleyin:

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
> *Launch. vs. JSON* içindeki `configurations` Array özelliği, kod temeli ve *. vs* dizini için kök dizin &mdash;the iki dosya konumundan okunurdur. Bir çakışma varsa, *. vs\launch.vs.JSON*içindeki değere öncelik verilir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

Bu konuda açıklanan üç *. JSON* dosyasına ek olarak, Visual Studio kod tabanınızda varsa bazı ek dosyalardan de ayarları okur.

### <a name="vscodesettingsjson"></a>. vscode\settings.JSON

Visual Studio, *. vscode*adlı bir dizinde olan *Settings. JSON*adlı dosyadan sınırlı ayarları okur. Bu işlevsellik, daha önce Visual Studio Code daha önce geliştirilen codetabanlar için verilmiştir. Şu anda, *. vscode\settings.JSON* ' dan okunan tek ayar, Çözüm Gezgini ve bazı arama araçlarından dosyaları görsel olarak filtreleyen `files.exclude`.

Kod tabanınızda herhangi bir sayıda *. vscode\settings.JSON* dosyası ekleyebilirsiniz. Bu dosyadan okunan ayarlar, *. vscode* üst dizinine ve tüm alt dizinlerine uygulanır.

### <a name="gitignore"></a>. gitignore

*. gitignore* dosyaları git 'e hangi dosyaların yoksayılacağını bildirmek için kullanılır; diğer bir deyişle, iade etmek istemediğiniz dosya ve dizinler. *. gitignore* dosyaları genellikle kod temelinin tüm geliştiricileriyle paylaşılabilmesi için bir kod temelinin parçası olarak dahil edilir. Visual Studio, öğeleri görsel olarak ve bazı arama araçlarından filtrelemek için *. gitignore* dosyalarındaki desenleri okur.

*. Gitignore* dosyasından okunan ayarlar, üst dizinine ve tüm alt dizinlere uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [İçin CMake projeleriC++](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE Başvurusu](/cpp/build/reference/nmake-reference)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
