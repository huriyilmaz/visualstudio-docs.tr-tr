---
title: HPC (Yüksek Performanslı Bilgi İşlem) Kümelerde Profil Oluşturma | Microsoft Docs
description: Uygulamanın örnekleme yöntemini kullanarak Microsoft Windows HPC kümelerinin işlem düğümleri üzerinde nasıl profil Visual Studio Profil Oluşturma Araçları.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0ddeb3271bbd0ddd9a31375d820fa0661fc7b9ad
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431386"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>HPC (yüksek performanslı bilgi işlem) kümelerine profil oluşturma

Microsoft Windows HPC kümelerinin işlem düğümlerinin profilini oluşturmak için Visual Studio Profil Oluşturma Araçları. HPC hakkında daha fazla bilgi Windows Microsoft Web sitesinde [HPC'yi](https://azure.microsoft.com/solutions/big-compute/) kullanın.

## <a name="prerequisites"></a>Önkoşullar

HPC işlem düğümünde profil oluşturmak için şunları yapın:

- Microsoft HPC Pack 2008'i aynı bilgisayara Visual Studio. Bilgisayarın HPC kümesine parçası olması gerek değildir. HPC Pack'i Microsoft İndirme [Merkezi'nden yükleyebilirsiniz.](https://www.microsoft.com/download/details.aspx?id=58506)

- .NET Framework 4'ü ve uygulamanın tek başına Profil Oluşturma Araçları HPC işlem düğümüne yükleyin. Yükleme medyası üzerinde hem .NET Framework hem de tek başına profilleyici için Visual Studio kullanılabilir. **Not** .NET Framework'i yükledikten sonra ve Profil Oluşturma Araçları.

  .NET Framework 4'ü ve tek başına Profil Oluşturma Araçları HPC işlem düğümüne yüklemek ve küme makinesi üzerinde profil oluşturmayı etkinleştirmek için şu adımları izleyin:

1. HPC paketiyle birlikte yüklü komut istemi penceresini açın.

2. Ayrı komut istemleri için aşağıdaki komutları yazın:

    1. `clusrun /all /scheduler:`*%HeadNode% %FxPath%* `/q /norestart`

    2. `clusrun /all /scheduler:`*%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:`*%HeadNode% %ProfilerPath%* `/q /norestart`

|Parametre | Açıklama |
|------------------| - |
| *%HeadNode%* | Küme için baş düğümün adı. |
| *%FxPath%* | .NET Framework 4 yükleyicisi yolu. Yükleme Visual Studio yol şu şekildedir: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | Profil Oluşturma Araçları yükleyicinin tek başına sürümünün yolu. Yükleme Visual Studio yolu şu şekildedir: Tek başına Profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>HPC işlem düğümünde profil oluşturma

HPC kümesi ve hedef bilgilerini belirtmek için HPC Performans Sihirbazı'nı kullanarak bir profil oluşturma oturumu yapılandırabilirsiniz. Performans oturumu özellik sayfalarında ek seçenekler bulabilirsiniz. Bu Profil Oluşturma Araçları gerekli hedef ikilileri otomatik olarak dağıtır ve profil oluşturma ve HPC uygulamasını başlatma.

1. Analiz **menüsünde** HPC Performans **Sihirbazı'nı Başlat'a tıklayın.** Komut kullanılamıyorsa, önkoşulların yukarıda listelenmiş olduğundan emin olun.

2. **Sihirbazın** ilk sayfasında Sonraki'ye tıklayın.

3. Sihirbazın ikinci sayfasında, profilini oluşturmak istediğiniz uygulamayı seçin.

   - içinde açık olan bir projenin profilini oluşturmak için Bir veya daha fazla kullanılabilir proje seçeneğini belirleyin ve ardından [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] listeden proje adını seçin. 

   - Açık projede yer alan bir ikili dosyanın profilini oluşturmak için Yürütülebilir **dosya (.EXE) seçeneğini** belirleyin.

4. **İleri**’ye tıklayın.

5. Sihirbazın üçüncü sayfasında:

    - Açık bir projede yer alan yürütülebilir dosyanın profilini çalıştırılabilir dosyanın profilini çalıştırılabilir dosyanın **tam yolu nedir? içinde belirtin.**

    - Açık bir projede olmayan bir yürütülebilir dosyanın profilini çalıştırılabilir olarak belirli belirli bir komut satırı bağımsız değişkenlerini Komut satırı bağımsız değişkenlerini **kullanarak işleme geçebilirsiniz.**

    - Uzaktan **çalışma dizininde,** tek tek işlem düğümlerde işlem örnekleri tarafından kullanılan klasörün yolunu belirtin.

    - Dağıtım **konumu'da,** HPC sunucusunun görüntüleri dağıtım için hazırlarken kullandığı dizinin yolunu belirtin.

6. **İleri**’ye tıklayın.

7. Sihirbazın dördüncü sayfasında:

    - Baş **Düğüm listesinde,** profil oluşturma çalıştırması içinde HPC baş düğümü olarak hareket yapan bilgisayara tıklayın. Baş Düğüm, bir kümeye gerek kalmadan yerel makinede profil oluşturmana olanak sağlayan "localhost" olabilir.

    - İşlem **sayısı listesinde,** çalıştıracak uygulamanın örnek sayısına tıklayın.

    - Profil **oluşturma seçenekleri listesinden** profil oluşturma hedefini seçin.

         Kümede belirli bir sürecin profilini  oluşturmak için, Dereceye göre profil seçeneğini belirleyin ve açılan listeden sürecin derecesi'ni seçin.

         HPC kümesinde belirli bir düğümde çalıştıran işlemlerin veya  işlemlerin profilini oluşturmak için Düğüm profili seçeneğini belirleyin ve ardından açılan listeden düğümü seçin.

8. **İleri**’ye tıklayın.

9. Sihirbazın beşinci sayfasında, profil oluşturma işlemini hemen başlatmayı veya profil oluşturma işlemini daha sonra kullanarak profil oluşturmayı Performans Gezgini.

    - Profil **oluşturmayı hemen başlatmak için sihirbaz tamam** olduktan sonra profil oluşturmayı başlat'ı seçin veya profil oluşturmayı el ile başlatmak için onay kutusunu temizleyin.

10. **Finish (Son)** düğmesine tıklayın.

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak HPC profil oluşturma özelliklerini ayarlama

Performans oturumu özellikleri sayfasının HPC Başlatma Özellikleri sayfasında HPC Profil Oluşturma Sihirbazı'nda ayar istediğiniz performans oturumu özelliklerini değiştirebilirsiniz. HPC Gelişmiş Özellikler sayfasında ek seçenekler ayarlarsiniz.

### <a name="to-open-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını açmak için

1. Gerekirse performans oturumu (.psess) dosyasını Performans Gezgini. Dosya **menüsünde Aç'a** **tıklayın** ve dosyayı bulun.

2. Bu Performans Gezgini performans oturumu adına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

3. Özellik Sayfaları iletişim kutusunda aşağıdaki yöntemlerden birini kullanın:

    - **Genel'e** tıklayın ve **HPC Kümesinde** Topla'yı seçerek HPC profili oluşturmayı açın veya HPC profili oluşturmayı devre dışı bırakmak için onay kutusunu temizleyin.

    - **HPC uygulamasını başlatan** özellikleri değiştirmek için HPC Başlatma Özellikleri'ne tıklayın.

    - Ek **seçenekleri ayarlamak için HPC** Gelişmiş Özellikler'e tıklayın

### <a name="hpc-launch-properties"></a>HPC başlatma özellikleri

|Özellik|Açıklama|
|--------------|-----------------|
|**Baş düğüm**|Profil oluşturma çalıştırması içinde HPC baş düğümü olarak hareket yapan bilgisayarı belirtir.|
|**İşlem sayısı**|Profili profili yapılan uygulamada çalıştıracak uygulama örneklerinin sayısını belirtir.|
|**Derece profili**|Kümede belirli bir sürecin profilini  oluşturmak için, Dereceye göre profil seçeneğini belirleyin ve açılan listeden sürecin derecesi'ni seçin.|
|**Düğümdeki profil**|HPC kümesinde belirli bir düğümde çalıştıran işlemlerin veya  işlemlerin profilini oluşturmak için Düğüm profili seçeneğini belirleyin ve ardından açılan listeden düğümü seçin.|
|**Uzaktan çalışma dizini**|Tek tek işlem düğümleri üzerinde işlem örnekleri tarafından kullanılan klasörün yolunu belirtir.|
|**Dağıtım konumu**|HPC sunucusunun görüntüleri dağıtım için hazırlarken kullandığı dizinin yolunu belirtir.|

### <a name="advanced-properties"></a>Gelişmiş özellikler

| Özellik | Açıklama |
|---------------------------------------| - |
| **Proje adı** | Geçerli projenin veya [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] çözümün adı. |
| **Profil oluşturma durdurulurken temizleme** | true olduğunda, yürütme dizinine dağıtılmış ikilileri kaldırır. Kullanıcı programı tarafından oluşturulan dosyalar ve dizinler bu adımda kaldırılamaz. Yürütme dizini ve dağıtım dizini IDE tarafından oluşturulduktan sonra, IDE bunları kaldırmaya çalışır ancak dosyaları IDE tarafından dağıtıldıklarına göre bunu yapmaz. |
| **Dağıtılana ek dosyalar** | İşlem düğümüne dağıt eklenecek ek dosyaların noktalı virgülle ayrılmış listesini belirtir. İletişim kutusu kullanarak birden çok dosya seçmek için üç nokta düğmesine (**...**) tıklayabilirsiniz. |
| **Mpiexec komutu** | MPI uygulamasını başlatan uygulamayı belirtir. Varsayılan değer **mpiexec.exe** |
| **Mpiexec bağımsız değişkenleri** | mpiexec.exe komutuna geçiş için bağımsız mpiexec.exe belirtir. |
| **Kümede istenen düğümler** | Uygulamanın çalıştırılacağı kümedeki düğüm sayısını belirtir. |
| **CRT dosyaları dağıtma** | Doğru olduğunda, kümede C/C++ çalışma süresini dağıtır. |
| **Ön profil betiği** | Profil oluşturma oturumu başlamadan önce yerel geliştirme bilgisayarında çalıştırılacak betiğin yolunu ve dosya adını belirtir. |
| **Profil öncesi betik bağımsız değişkenleri** | Profil öncesi betiğe geçirilecek bağımsız değişkenleri belirtir. |
| **Profil sonrası betiği** | Profil oluşturma oturumu bittikten sonra yerel geliştirme bilgisayarında çalıştırılacak betiğin yolunu ve dosya adını belirtir. |
| **Profil sonrası betik bağımsız değişkenleri** | Profil sonrası betiğe geçirilecek bağımsız değişkenleri belirtir. |
