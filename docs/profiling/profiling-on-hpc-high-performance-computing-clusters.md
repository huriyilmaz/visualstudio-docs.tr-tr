---
title: HPC (Yüksek Performanslı Bilgi İşlem) Kümelerinde Profil Oluşturma | Microsoft Dokümanlar
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f2d3949194dedab6d7e7ea2faa1aea304d889bc4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772126"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>HPC (yüksek performanslı bilgi işlem) kümeleri profili

Visual Studio Profil Oluşturma Araçları'nın örnekleme yöntemini kullanarak Microsoft Windows HPC kümelerinin bilgi işlem düğümlerinde profil oluşturabilirsiniz. HPC hakkında daha fazla bilgi için Microsoft Web sitesinde [Windows HPC'ye](https://azure.microsoft.com/solutions/big-compute/) bakın.

## <a name="prerequisites"></a>Önkoşullar

Bir HPC işlem düğümünde profil çıkarmak için aşağıdakileri yapmanız gerekir:

- Visual Studio ile aynı bilgisayara Microsoft HPC Pack 2008'i yükleyin. Bilgisayar HPC kümesinin bir parçası olmak zorunda değildir. HPC Paketini [Microsoft Download Center'a](https://www.microsoft.com/download/details.aspx?id=4812)yükleyebilirsiniz.

- .NET Framework 4'ü ve Profil Oluşturma Araçları'nın tek başına sürümünü HPC bilgi işlem düğümüne yükleyin. Visual Studio kurulum ortamlarında hem .NET Framework hem de tek başına profil oluşturucu için yükleme programları mevcuttur. **Not** .NET Framework'ü yükledikten sonra ve Profil Oluşturma Araçlarını yüklemeden önce bilgi işlemle yeniden başlatmanız gerekir.

  Etkin bir HPC bilgi işlem düğümüne .NET Framework 4 ve tek başına Profil Oluşturma Araçları yüklemek ve küme makinesinde profil oluşturmayı etkinleştirmek için aşağıdaki adımları izleyin:

1. HPC paketiyle yüklü komut istemi penceresini açın.

2. Aşağıdaki komutları ayrı komut istemlerine yazın:

    1. `clusrun /all /scheduler:`*%HeadNode% %FxPath%*`/q /norestart`

    2. `clusrun /all /scheduler:`*%HeadNode%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:`*%HeadNode% %ProfilerPath%*`/q /norestart`

| | |
|------------------| - |
| *%HeadNode%* | Küme için baş düğümünün adı. |
| *%FxPath%* | .NET Framework 4 yükleyicisine giden yol. Visual Studio kurulum ortamında yol şudur: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | Profil Oluşturma Araçları yükleyicisinin bağımsız sürümüne giden yol. Visual Studio kurulum medyasında yol şudur: Bağımsız Profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>HPC işlem düğümündeki profil

HPC kümesini ve hedef bilgilerini belirtmek için HPC Performans Sihirbazı'nı kullanarak bir profil oluşturma oturumu yapılandırırsınız. Performans oturumu özelliği sayfalarında ek seçenekler ayarlayabilirsiniz. Profil Oluşturma Araçları gerekli hedef ikililerini otomatik olarak dağır ve profil oluşturucuyu ve HPC uygulamasını başlayır.

1. **Analiz** menüsünde, **HPC Performans Sihirbazı Başlat'ı**tıklatın. Komut kullanılamıyorsa, yukarıda listelenen ön koşullara sahip olduğunuzdan emin olun.

2. Sihirbazın ilk sayfasında **İleri'yi** tıklatın.

3. Sihirbazın ikinci sayfasında, profilini çıkarmak istediğiniz uygulamayı seçin.

   - Şu anda açık olan [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]bir projenin profilini çıkarmak için, **Bir veya daha fazla kullanılabilir proje** seçeneğini seçin ve ardından listeden proje adını seçin.

   - Açık bir projede olmayan bir ikilinin profilini çıkarmak için **Çalıştırılabilir (. EXE dosyası)** seçeneği.

4. **İleri**'ye tıklayın.

5. Sihirbazın üçüncü sayfasında:

    - Açık bir projede olmayan bir yürütülebilir profil çıkarıyorsanız, **yürütülebilir**için tam yol nedir ikili dosyaya giden yolu belirtin.

    - Açık bir projede olmayan bir yürütülebilir profil çıkarıyorsanız, **Komut satırı bağımsız değişkenlerinde**işleme geçmek için herhangi bir komut satırı bağımsız değişkeni belirtebilirsiniz.

    - **Uzaktan çalışma dizininde,** tek tek işlem düğümleri üzerinde işlem örnekleri tarafından kullanılan klasöre giden yolu belirtin.

    - **Dağıtım konumunda,** HPC sunucusunun görüntüleri dağıtım için sahnelemek için kullandığı dizine giden yolu belirtin.

6. **İleri**'ye tıklayın.

7. Sihirbazın dördüncü sayfasında:

    - Kafa **Düğümü** listesinde, profil oluşturma çalışmasında HPC kafa düğümü gibi davranan bilgisayarı tıklatın. Kafa Düğümü, kümeye gerek kalmadan yerel makinede profil oluşturmanıza olanak tanıyan "localhost" olabilir.

    - İşlem **Sayısı** listesinde, çalışacak uygulamanın örnek sayısını tıklatın.

    - Profil **oluşturma seçenekleri** listesinden profil oluşturma hedefini seçin.

         Kümedeki belirli bir işlemin profilini çıkarmak **için, sıralama seçeneğinde Profil'i** seçin ve ardından açılan listeden işlemin sıralamasını seçin.

         HPC kümesinde belirli bir düğümüzerinde çalışan işlem veya işlemlerin profilini çıkarmak için düğüm **seçeneğinde Profil'i** seçin ve ardından açılan listeden düğümü seçin.

8. **İleri**'ye tıklayın.

9. Sihirbazın beşinci sayfasında, profil oluşturma işlemini hemen başlatmayı veya Daha sonra Performans Gezgini'ni kullanarak profil oluşturmayı seçebilirsiniz.

    - Sihirbaz ın profil oluşturmayı hemen başlatmasına başlamak için **sihirbaz bittikten sonra Profil Oluşturmayı Başlat'ı** seçin veya profil oluşturmayı el ile başlatmak için onay kutusunu temizleyin.

10. **Son**'a tıklayın.

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Performans oturumu özelliği sayfalarını kullanarak HPC profil oluşturma özelliklerini ayarlama

Performans oturumu özellikleri sayfasının HPC Başlatma Özellikleri sayfasında Ki FPC Profil Oluşturma Sihirbazı'nda ayarladığınız performans oturumu özelliklerini değiştirebilirsiniz. HPC Gelişmiş Özellikler sayfasında ek seçenekler ayarlarsınız.

### <a name="to-open-the-performance-session-property-pages"></a>Performans oturumu özelliği sayfalarını açmak için

1. Gerekirse Performans Gezgini'nde performans oturumu (.psess) dosyasını açın. **Dosya** menüsünde **Aç'ı** tıklatın ve dosyayı bulun.

2. Performans Gezgini'nde, performans oturumu adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

3. Özellik Sayfaları iletişim kutusunda aşağıdaki yöntemlerden birini kullanın:

    - **Genel'i** tıklatın ve ardından HPC profil oluşturmayı açmak veya HPC profil oluşturmayı devre dışı kıdamak için onay kutusunu temizlemek için **HPC Cluster'da Topla'yı** seçin.

    - HPC uygulamasını başlatan özellikleri değiştirmek için **HPC Başlatma Özellikleri'ni** tıklatın.

    - Ek seçenekler ayarlamak için **HPC Gelişmiş Özellikler'i** tıklatın

### <a name="hpc-launch-properties"></a>HPC başlatma özellikleri

|Özellik|Açıklama|
|--------------|-----------------|
|**Baş düğüm**|Profil oluşturma çalışmasında HPC kafa düğümü gibi davranan bilgisayarı belirtir.|
|**İşlem sayısı**|Profilli uygulamada çalışacak uygulama örneklerinin sayısını belirtir.|
|**Sıralama profili**|Kümedeki belirli bir işlemin profilini çıkarmak **için, sıralama seçeneğinde Profil'i** seçin ve ardından açılan listeden işlemin sıralamasını seçin.|
|**Düğüm deki profil**|HPC kümesinde belirli bir düğümüzerinde çalışan işlem veya işlemlerin profilini çıkarmak için düğüm **seçeneğinde Profil'i** seçin ve ardından açılan listeden düğümü seçin.|
|**Uzaktan çalışma dizini**|Tek tek işlem düğümleri üzerinde işlem örnekleri tarafından kullanılan klasöre giden yolu belirtir.|
|**Dağıtım konumu**|HPC sunucusunun görüntüleri dağıtım için sahnelemek için kullandığı dizine giden yolu belirtir.|

### <a name="advanced-properties"></a>Gelişmiş özellikler

| Özellik | Açıklama |
|---------------------------------------| - |
| **Proje adı** | Geçerli [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] projenin veya çözümün adı. |
| **Profil oluşturucu durdurulduğunda temizleme** | Doğru olduğunda, yürütme dizinine dağıtılan ikilileri kaldırır. Bu adımda kullanıcı programı tarafından oluşturulan dosyalar ve dizinler kaldırılmaz. Yürütme dizini ve dağıtım dizini IDE tarafından oluşturulduysa, IDE bunları kaldırmaya çalışır, ancak IDE tarafından dağıtılmayan dosyaları varsa bunu yapmaz. |
| **Dağıtılabilmek için ek dosyalar** | İşlem düğümünde dağıtılabilmek için herhangi bir ek dosyanın yarı nokta noktalı ayrı listesini belirtir. Bir iletişim kutusu kullanarak birden fazla dosya seçmek için elipsis (**...**) düğmesini tıklatabilirsiniz. |
| **Mpiexec komutu** | MPI uygulamasını başlatan uygulamayı belirtir. Varsayılan değer **mpiexec.exe** |
| **Mpiexec bağımsız değişkenleri** | Mpiexec.exe komutuna geçmek için bağımsız değişkenleri belirtir. |
| **Kümede istenen düğümler** | Uygulamayı çalıştıracak kümedeki düğüm sayısını belirtir. |
| **CRT dosyalarını dağıtma** | Doğru olduğunda, C/C++ çalışma süresini kümeye dağıtır. |
| **Ön profil komut dosyası** | Profil oluşturma oturumu başlamadan önce yerel geliştirme bilgisayarında çalışacak bir komut dosyasının yolunu ve dosya adını belirtir. |
| **Ön profil komut dosyası bağımsız değişkenleri** | Ön profil komut dosyasına geçmek için bağımsız değişkenleri belirtir. |
| **Profil sonrası komut dosyası** | Profil oluşturma oturumu sona erdikten sonra yerel geliştirme bilgisayarında çalışacak bir komut dosyasının yolunu ve dosya adını belirtir. |
| **Profil sonrası komut dosyası bağımsız değişkenleri** | Profil sonrası komut dosyasına geçecek bağımsız değişkenleri belirtir. |
