---
title: HPC üzerinde profil oluşturma (yüksek performanslı bilgi Işlem) kümeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b63f9ddf29ff74a4aa4bf089c266e12e37bb2f50
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535544"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>HPC (Yüksek Performanslı Hesaplama) Kümelerinde Profil Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veya Profil Oluşturma Araçları örnekleme yöntemini kullanarak Microsoft Windows HPC kümelerinin işlem düğümlerinde profil oluşturabilirsiniz [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] . HPC hakkında daha fazla bilgi için bkz. Microsoft Web sitesinde [büyük işlem: HPC & Batch](https://azure.microsoft.com/solutions/big-compute/) .  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bir HPC işlem düğümünde profil yapmak için aşağıdakileri yapmanız gerekir:  
  
- Microsoft HPC Pack 2008 'i ile aynı bilgisayara yükler [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] . Bilgisayar HPC kümesinin bir parçası olmak zorunda değildir. HPC Pack 'i [Microsoft Indirme merkezi](https://www.microsoft.com/download/details.aspx?id=2800)' nde yükleyebilirsiniz.  
  
- [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]HPC işlem düğümüne profil oluşturma araçları ve tek başına sürümünü yükler. Yükleme medyasında hem hem de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] tek başına profil Oluşturucu için yükleme programları vardır [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] . **Göz önünde** ' İ yükledikten sonra ve Profil Oluşturma Araçları yüklemeden önce işlemi yeniden başlatmanız gerekir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
  [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]Etkin BIR HPC işlem düğümüne ve tek başına profil oluşturma araçları yüklemek ve küme makinesinde profil oluşturmayı etkinleştirmek için şu adımları izleyin:  
  
1. HPC Pack ile yüklenen komut istemi penceresini açın.  
  
2. Aşağıdaki komutları ayrı komut istemlerine yazın:  
  
    1. `clusrun /all /scheduler:`*% Headnode%% FxPath%*`/q /norestart`  
  
    2. `clusrun /all /scheduler:`*% Headnode%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3. `clusrun /all /scheduler:`*% Headnode%% ProfilerPath%*`/q /norestart`  
  
|Söz dizimi öğesi|Açıklama|  
|-|-|  
|*Baş düğümüne*|Kümenin baş düğümünün adı.|  
|*% FxPath%*|[!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]Yükleyicinin yolu. [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]Yükleme medyasında yol: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*% ProfilerPath%*|Profil Oluşturma Araçları yükleyicisinin bağımsız sürümünün yolu. [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]Yükleme medyasında yol: tek başına Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>HPC Işlem düğümünde profil oluşturma  
 HPC kümesi ve hedef bilgilerini belirtmek için HPC performans sihirbazını kullanarak bir profil oluşturma oturumu yapılandırırsınız. Performans oturumu özellik sayfalarında ek seçenekler belirleyebilirsiniz. Profil Oluşturma Araçları, gerekli hedef ikilileri otomatik olarak dağıtır ve profil oluşturucu ve HPC uygulamasını başlatır.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Bir HPC işlem düğümünde profil oluşturma  
  
1. **Çözümle** menüsünde **HPC Performans Sihirbazını Başlat**' ı tıklatın. Komut kullanılamıyorsa, yukarıda listelenen önkoşullara sahip olduğunuzdan emin olun.  
  
2. Sihirbazın ilk sayfasında **İleri** ' ye tıklayın.  
  
3. Sihirbazın ikinci sayfasında, profil atamak istediğiniz uygulamayı seçin.  
  
    - İçinde açık olan bir projeyi profil için [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , **bir veya daha fazla kullanılabilir proje** seçeneğini belirleyin ve ardından listeden proje adını seçin.  
  
    - Açık bir projede olmayan bir ikilinin profilini eklemek için **çalıştırılabilir (. EXE dosyası)** seçeneğini.  
  
4. **İleri**’ye tıklayın.  
  
5. Sihirbazın üçüncü sayfasında:  
  
    - Açık bir projede olmayan bir yürütülebilirin profilini oluşturuyorsanız, **yürütülebilir dosyanın tam yolu olan**ikili dosyanın yolunu belirtin.  
  
    - Açık bir projede olmayan bir yürütülebilir dosya profili oluşturuyorsanız, **komut satırı bağımsız değişkenlerinde**işleme geçirilecek komut satırı bağımsız değişkenlerini belirtebilirsiniz.  
  
    - **Uzak çalışma dizini**' nde, bireysel işlem düğümlerinde işlem örnekleri tarafından kullanılan klasörün yolunu belirtin.  
  
    - **Dağıtım konumu**' nda HPC sunucusunun dağıtım için görüntüleri hazırlamak üzere kullandığı dizinin yolunu belirtin.  
  
6. **İleri**’ye tıklayın.  
  
7. Sihirbazın dördüncü sayfasında:  
  
    - **Baş düğüm** listesinde, profil oluşturma çalıştırmasında HPC head düğümü olarak davranan bilgisayara tıklayın. Baş düğüm "localhost" olabilir ve bu, yerel makinede bir kümeye gerek duymadan profil gerçekleştirmenizi sağlar.  
  
    - **Işlem sayısı** listesinde, çalıştırılacak uygulamanın örnek sayısına tıklayın.  
  
    - **Profil oluşturma seçenekleri** listesinden profil oluşturma hedefini seçin.  
  
         Kümede belirli bir işlemi profili eklemek için, **derece üzerinde profil** seçeneğini belirleyin ve ardından açılır listeden işlemin sırasını seçin.  
  
         HPC kümesindeki belirli bir düğümde çalışan işlem veya işlemlerin profilini belirlemek için **düğüm üzerinde profil** seçeneğini belirleyin ve ardından açılan listeden düğümü seçin.  
  
8. **İleri**’ye tıklayın.  
  
9. Sihirbazın beşinci sayfasında, profil oluşturucuyu ve profil oluşturma işlemini hemen başlatmayı veya Performans Gezgini kullanarak daha sonra profil oluşturmayı başlatmayı seçebilirsiniz.  
  
    - Profil oluşturmayı hemen başlatmak için **sihirbaz bittikten sonra profil oluşturmayı Başlat** ' ı seçin veya profil oluşturmayı el ile başlatmak için onay kutusunun işaretini kaldırın.  
  
10. **Son**'a tıklayın.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak HPC profil oluşturma özelliklerini ayarlama  
 Performans oturumu özellikleri sayfasının HPC Başlatma Özellikleri sayfasında HPC profil oluşturma Sihirbazı 'nda ayarladığınız performans oturumu özelliklerini değiştirebilirsiniz. HPC gelişmiş özellikler sayfasında ek seçenekleri ayarlarsınız.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını açmak için  
  
1. Gerekirse, Performans Gezgini ' de performans oturumu (. psess) dosyasını açın. **Dosya** menüsünde **Aç** ' a tıklayın ve dosyayı bulun.  
  
2. Performans Gezgini, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
3. Özellik sayfaları iletişim kutusunda, aşağıdaki yöntemlerden birini kullanın:  
  
    - **Genel** ' e tıklayın ve HPC profil oluşturmayı açmak Için HPC **kümesinde topla** ' yı seçin veya HPC profil oluşturmayı devre dışı bırakmak için onay kutusunun işaretini kaldırın.  
  
    - HPC uygulamasını Başlatan özellikleri değiştirmek için **HPC Başlatma Özellikleri** ' ne tıklayın.  
  
    - Ek seçenekleri ayarlamak için **HPC gelişmiş özellikler** ' e tıklayın  
  
### <a name="hpc-launch-properties"></a>HPC Başlatma Özellikleri  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Baş düğüm**|Profil oluşturma çalıştırmasında HPC head düğümü olarak davranan bilgisayarı belirtir.|  
|**İşlem sayısı**|Profili oluşturulan uygulamada çalıştırılacak uygulamanın örnek sayısını belirtir.|  
|**Sırasıyla profil**|Kümede belirli bir işlemi profili eklemek için, **derece üzerinde profil** seçeneğini belirleyin ve ardından açılır listeden işlemin sırasını seçin.|  
|**Düğüm üzerindeki profil**|HPC kümesindeki belirli bir düğümde çalışan işlem veya işlemlerin profilini belirlemek için **düğüm üzerinde profil** seçeneğini belirleyin ve ardından açılan listeden düğümü seçin.|  
|**Uzak çalışma dizini**|Bireysel işlem düğümlerinde işlem örnekleri tarafından kullanılan klasörün yolunu belirtir.|  
|**Dağıtım konumu**|HPC sunucusunun dağıtım için görüntüleri hazırlamak üzere kullandığı dizinin yolunu belirtir.|  
  
### <a name="advanced-properties"></a>Gelişmiş Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**Proje adı**|Geçerli [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Proje veya çözümün adı.|  
|**Profil Oluşturucu durdurulduğunda temizle**|Doğru olduğunda, yürütme dizinine dağıtılan ikilileri kaldırır. Kullanıcı programı tarafından oluşturulan dosyalar ve dizinler bu adımda kaldırılmaz. Yürütme dizini ve dağıtım dizini IDE tarafından oluşturulduysa, IDE bunları kaldırmaya çalışır, ancak IDE tarafından dağıtılmayan dosyalar varsa bunu yapmaz.|  
|**Dağıtılacak ek dosyalar**|İşlem düğümünde dağıtılacak ek dosyaların noktalı virgülle ayrılmış bir listesini belirtir. Bir iletişim kutusunu kullanarak birden çok dosya seçmek için üç nokta düğmesini (**...**) tıklayabilirsiniz.|  
|**Mpiexec komutu**|MPı uygulamasını Başlatan uygulamayı belirtir. Varsayılan değer **mpiexec.exe**|  
|**Mpiexec bağımsız değişkenleri**|mpiexec.exe komutuna geçirilecek bağımsız değişkenleri belirtir.|  
|**Kümede istenen düğümler**|Uygulamanın çalıştırılacağı kümedeki düğüm sayısını belirtir.|  
|**CRT dosyaları dağıtma**|Doğru olduğunda, kümede C/C++ çalışma süresini dağıtır.|  
|**Ön profil betiği**|Profil oluşturma oturumu başlamadan önce yerel geliştirme bilgisayarında çalıştırılacak betiğin yolunu ve dosya adını belirtir.|  
|**Profil öncesi betik bağımsız değişkenleri**|Profil öncesi betiğe geçirilecek bağımsız değişkenleri belirtir.|  
|**Profil sonrası betiği**|Profil oluşturma oturumu bittikten sonra yerel geliştirme bilgisayarında çalıştırılacak betiğin yolunu ve dosya adını belirtir.|  
|**Profil sonrası betik bağımsız değişkenleri**|Profil sonrası betiğe geçirilecek bağımsız değişkenleri belirtir.|
