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
ms.openlocfilehash: 9bfd9ede5f26c2e872f3339f15b17b4835b40312de17de2a5316f6448a01e61c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121259376"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>"Klasör Aç" geliştirme için derleme ve hata ayıklama görevlerini özelleştirme

Visual Studio dili ve kod tabanını nasıl çalıştıracaklarını biliyor ama her şeyi nasıl çalıştıracaklarını bilmiyor. Visual Studio'de bir kod Visual Studio ve kodunuzun nasıl çalıştırılamadı yapılandırmasını biliyorsanız, bu klasörü ek bir yapılandırma olmadan hemen çalıştırabilirsiniz. [](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

Kod temeli, Visual Studio tanımaz özel derleme araçları kullanıyorsa, kod üzerinde çalıştırmak ve hata ayıklamak için bazı yapılandırma ayrıntılarını Visual Studio. Derleme görevlerini tanımlayarak Visual Studio nasıl derlemeniz *gerektirebilirsiniz?* Bir dilin kodunu derlemesi ve çalıştırması için gereken tüm öğeleri belirtmek için bir veya daha fazla derleme görevi oluşturabilirsiniz. Ayrıca, neredeyse istediğiniz her şeyi gerçekleştirebilir rastgele görevler de oluşturabilirsiniz. Örneğin, bir klasörün içeriğini listeleye veya bir dosyayı yeniden adlandırmaya yönelik bir görev oluşturabilirsiniz.

Aşağıdaki *.json* dosyalarını kullanarak projeniz olmayan kod tabanınızı özelleştirin:

|Dosya adı|Amaç|
|-|-|
|*tasks.vs.js*|Özel derleme komutlarını ve derleyici anahtarlarını ve rastgele (derlemeyle ilgili olmayan) görevleri belirtin.<br>Görevler'i **Çözüm Gezgini** menü öğesi aracılığıyla **erişilir.**|
|*launch.vs.js*|Hata ayıklama için komut satırı bağımsız değişkenlerini belirtin.<br>Uygulama aracılığıyla **erişilen Çözüm Gezgini** menü öğesi hata ayıkla ve **Başlat'a Ayarlar.**|

Bu *.json* dosyaları, kod tabanının kök klasöründe *.vs* adlı gizli bir klasörde bulunur. Dosyalarda *tasks.vs.js* ve launch.vs.js, Visual Studio'de bir dosya veya klasörde Görevleri Yapılandır veya Hata  Ayıkla  ve Ayarlar'yi Başlat'ı seçerseniz, **Çözüm Gezgini.** Kullanıcılar genellikle bunları kaynak denetimine almak istemediklerine göre bu *.json* dosyaları gizlenir. Ancak, bunları kaynak denetimine kontrol etmek için dosyaları kod tabanının köküne sürükleyin ve burada görünürler.

> [!TIP]
> Dosya çubuğunda gizli Visual Studio görüntülemek için, araç **çubuğundaki** Tüm Dosyaları **Göster Çözüm Gezgini** seçin.

## <a name="define-tasks-with-tasksvsjson"></a>Görev tanımlama ve tasks.vs.jstanımlama

Derleme betiklerini veya geçerli çalışma alanınıza sahip dosyalarınız üzerinde herhangi bir dış işlemi doğrudan IDE'de görev olarak çalıştırarak otomatik hale abilirsiniz. Bir dosya veya klasöre sağ tıklar ve Görevleri Yapılandır'ı seçerek yeni bir **görev yapılandırabilirsiniz.**

![Görevleri Yapılandır menüsü](../ide/media/customize-configure-tasks-menu.png)

Bu, .vs klasöründe *tasks.vs.jsdosyasını* oluşturur *(veya* açar). Bu dosyada bir derleme görevi veya rastgele görev tanımlayabilir ve ardından sağ tıklama  menüsünden Çözüm Gezgini çağırabilirsiniz.

Özel görevler tek tek dosyalara veya belirli bir türe sahip tüm dosyalara eklenebilir. Örneğin, NuGet dosyaları bir "Paketleri Geri Yükle" görevine sahip olacak şekilde ya da tüm kaynak dosyalar, tüm paket dosyaları için bir linter gibi statik bir analiz görevi olacak *şekilde ya*.jsolabilir.

### <a name="define-custom-build-tasks"></a>Özel derleme görevleri tanımlama

Kod tabanınız, Visual Studio tanımaz özel derleme araçları kullanıyorsa, bazı yapılandırma adımlarını tamamlayana kadar kodu Visual Studio içinde çalıştıramaz ve hata ayıkamazsiniz. Visual Studio, *kodunuzu derleme,* yeniden derleme ve temizleme Visual Studio anlatabilirsiniz derleme görevleri sağlar. Derleme *tasks.vs.jsdosyası,* iç geliştirme Visual Studio kod tabanınız tarafından kullanılan özel derleme araçlarına uygundur.

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

Derleme, *temizleme ve* yeniden derleme hedeflerini içeren böyle bir derleme dosyası için aşağıdakitasks.vs.js *tanımlayabilirsiniz.* Derleme aracı olarak NMAKE kullanarak kod tabanını oluşturmak, yeniden derlemek ve temizlemek için üç derleme görevi içerir.

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

üzerinde derleme görevleri tanımladığınız *tasks.vs.js,* öğesinde ilgili dosyalara ek sağ tıklama menüsü (bağlam menüsü) **öğeleri Çözüm Gezgini.** Bu örnekte, herhangi bir derleme dosyası dosyasının bağlam menüsüne "derleme", "yeniden derleme" ve *"temizleme" seçenekleri* eklenir.

![derleme, yeniden derleme ve temizleme ile derleme dosyası bağlam menüsü](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Komutlar, ayarları nedeniyle Görevleri **Yapılandır komutunun** altındaki bağlam menüsünde `contextType` görünür. "build", "rebuild" ve "clean" derleme komutlarıdır, bu nedenle bağlam menüsünün ortasındaki derleme bölümünde görünürler.

Bu seçeneklerden birini seçerek görev yürütülür. Çıkış, Çıkış **penceresinde,** derleme hataları ise Hata Listesinde **görünür.**

### <a name="define-arbitrary-tasks"></a>Rastgele görevler tanımlama

Tam olarak istediğiniz her şeyi *tasks.vs.js* rastgele görevler tanımlayabilirsiniz. Örneğin, o anda seçili olan dosyanın adını Çıkış penceresinde  görüntülemek veya belirtilen dizinde dosyaları listeleyecek bir görev tanımlayabilirsiniz.

Aşağıdaki örnekte, tek *tasks.vs.jstanımlayan* bir dosyada bir dosyanın nasıl tanımladığı gösterir. Çağrıldığında, görev seçili durumdaki dosyanın dosya *adını*.jsgörüntüler.

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
- `appliesTo` komutun hangi dosyalarda gerçekleştirilecek olduğunu belirtir.
- `command`özelliği çağrılan komutu belirtir. Bu örnekte ortam `COMSPEC` değişkeni, komut satırı yorumlayıcıyı tanımlamak ** için kullanılır ve genelliklecmd.exe.
- `args`özelliği, çağrılan komuta geçirilen bağımsız değişkenleri belirtir.
- Makro, `${file}` seçilen dosyayı Çözüm Gezgini. 

Üzerinetasks.vs.js *sonra,* klasördeki herhangi bir dosya *.js* tıklar ve Echo dosya **adı'ı seçebilirsiniz.** Dosya adı Çıkış **penceresinde** görüntülenir.

> [!NOTE]
> Kod tabanınız dosyada bir tasks.vs.jsiçeriyorsa, dosyanın sağ  tıklama menüsünden veya bir dosyanın bağlam menüsünden Görevleri Yapılandır'ı seçerek bir **Çözüm Gezgini.**

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

Bu görev tüm dosyalar için geçerlidir. Çözüm Gezgini'daki herhangi bir dosyada bağlam menüsünü açabilirsiniz. Görevin **adı** Liste Çıkışları menüsünün alt kısmında görünür. Çıkışları **Listele'yi** seçerseniz, bin *dizininin* içeriği, **dizinde** yer alan Çıkış penceresinde Visual Studio.

![Bağlam menüsünde rastgele görev](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ayarlar kapsamı

Bir *tasks.vs.jskök* dizininde ve alt dizinlerde birden çok dosya dosyası olabilir. Bu tasarım, esnekliğin kod tabanının farklı alt dizinlerde farklı davranışa sahip olmasına olanak sağlar. Visual Studio tüm ayarları toplar veya geçersiz kılar ve dosyalara aşağıdaki sırayla önceliklerini ayarlar:

- Ayarlar klasörünün *.vs* dizinindeki dosyaları görüntüler.
- Bir ayarın hesapta olduğu dizin.
- Geçerli dizinin üst dizini, kök dizine kadar.
- Ayarlar dizine dosya ekler.

Bu toplama kuralları, üzerindetasks.vs.js *geçerlidir.* Diğer dosya ayarlarının nasıl toplanmış olduğu hakkında bilgi için bu makalede bu dosyaya karşılık gelen bölüme bakın.

### <a name="properties-for-tasksvsjson"></a>tasks.vs.jsözellikleri

Bu bölümde, üzerinde uygulama içinde belirtebilirsiniz bazı *tasks.vs.jsaçıktır.*

#### <a name="appliesto"></a>Appliesto

Alanında adını belirterek herhangi bir dosya veya klasör için görevler `appliesTo` oluşturabilirsiniz, örneğin `"appliesTo": "hello.js"` . Aşağıdaki dosya maskeleri değer olarak kullanılabilir:

|Dosya maskesi|Açıklama|
|-|-|
|`"*"`| görevi çalışma alanında tüm dosya ve klasörler için kullanılabilir|
|`"*/"`| görevi çalışma alanında tüm klasörler için kullanılabilir|
|`"*.js"`| görev, çalışma alanında uzantılı tüm *.js* kullanılabilir|
|`"/*.js"`| görev, çalışma alanının kökünde *uzantı.js* tüm dosyalar tarafından kullanılabilir|
|`"src/*/"`| görevi, *src* klasörünün tüm alt klasörleri tarafından kullanılabilir|
|`"makefile"`| görevi çalışma alanı içinde *tüm makefile* dosyaları için kullanılabilir|
|`"/makefile"`| görevi yalnızca çalışma alanının kökünde bulunan *makefile* için kullanılabilir|

#### <a name="macros-for-tasksvsjson"></a>tasks.vs.jsiçin makrolar

|Makro|Açıklama|
|-|-|
|`${env.<VARIABLE>}`| Herhangi bir ortam değişkenlerini belirtir (örneğin, ${env. Geliştirici komut istemi için ayarlanmış PATH}, ${env.COMSPEC} gibi). Daha fazla bilgi için [bkz. Geliştirici Komut İstemi Geliştirici PowerShell.](../ide/reference/command-prompt-powershell.md)|
|`${workspaceRoot}`| Çalışma alanı klasörünün tam yolu (örneğin, *C:\sources\hello*)|
|`${file}`| Bu görevi çalıştırmak için seçilen dosyanın veya klasörün tam yolu (örneğin, *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Dosya veya klasörün göreli yolu (örneğin, *src\hello.js*)|
|`${fileBasename}`| Dosyanın yolu veya uzantısı olmayan adı (örneğin, *Merhaba*)|
|`${fileDirname}`| Dosya adı hariç dosyanın tam yolu (örneğin, *C:\sources\hello\src*)|
|`${fileExtname}`| Seçilen dosyanın uzantısı (örneğin,  *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>launch.vs.jsile hata ayıklamayı yapılandırma

CMake projelerini hata ayıklama için yapılandırmak için bkz. [CMake hata ayıklama oturumlarını yapılandırma](/cpp/build/configure-cmake-debugging-sessions).

1. kod tabanınızı hata ayıklama için yapılandırmak için, **Çözüm Gezgini** içinde, çalıştırılabilir dosyanızın sağ tıklama veya bağlam menüsünden **hata ayıkla ve başlat Ayarlar** menü öğesini seçin.

   ![hata ayıklama ve Ayarlar bağlam menüsü başlatma](media/customize-debug-launch-menu.png)

1. **Hata ayıklayıcı Seç** iletişim kutusunda bir seçenek belirleyin ve ardından **Seç** düğmesini seçin.

   ![Bir hata ayıklayıcı iletişim kutusu seçin](media/customize-select-a-debugger.png)

   Dosyadaki *launch.vs.js* henüz yoksa, oluşturulur.

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

Dosyadaki *launch.vs.js* hata ayıklama için geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz. `args`Aşağıdaki örnekte gösterildiği gibi, dizideki bağımsız değişkenleri ekleyin:

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
> `configurations` *launch.vs.json* öğesinde dizi özelliği &mdash; , kod temeli ve *. vs* dizini için kök dizin olan iki dosya konumundan okunurdur. Bir çakışma varsa, *.vs\launch.vs.jsüzerindeki* değere öncelik verilir.

## <a name="additional-settings-files"></a>Ek ayarlar dosyaları

bu konuda açıklanan üç *. json* dosyasına ek olarak Visual Studio, kod tabanınızda varsa bazı ek dosyalardan da ayarları okur.

### <a name="vscodesettingsjson"></a>Üzerinde .vscode\settings.js

Visual Studio, *. vscode* adlı bir dizinde ise, *settings.js* adlı bir dosyadan sınırlı ayarları okur. Bu işlevsellik, daha önce Visual Studio Code daha önce geliştirilen codetabanlar için verilmiştir. Şu anda *.vscode\settings.json* ' dan okunan tek ayar, `files.exclude` Çözüm Gezgini ve bazı arama araçlarından dosyaları görsel olarak filtreleyerek.

Kod tabanınızdaki dosyalarda istediğiniz sayıda *.vscode\settings.js* olabilir. bu dosyadan okunan Ayarlar, *. vscode* üst dizinine ve tüm alt dizinlerine uygulanır.

### <a name="gitignore"></a>.gitignore

*. gitignore* dosyaları git 'e hangi dosyaların yoksayılacağını bildirmek için kullanılır; diğer bir deyişle, iade etmek istemediğiniz dosya ve dizinler. *. gitignore* dosyaları genellikle kod temelinin tüm geliştiricileriyle paylaşılabilmesi için bir kod temelinin parçası olarak dahil edilir. Visual Studio, öğeleri görsel olarak ve bazı arama araçlarından filtrelemek için *. gitignore* dosyalarındaki desenleri okur.

*. gitignore* dosyasından okunan Ayarlar, üst dizinine ve tüm alt dizinlere uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje veya çözüm olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ için CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE başvurusu](/cpp/build/reference/nmake-reference)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
