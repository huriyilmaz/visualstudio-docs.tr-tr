---
title: DLL projelerinde hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a4533c304f84d9dc59ec6b05328528870e49655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691393"
---
# <a name="debugging-dll-projects"></a>DLL Projelerinde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki şablonlar dll 'Ler oluşturur:  
  
- (C++, C# ve Visual Basic) Sınıf kitaplığı  
  
- (C++, C# ve Visual Basic): Windows Forms denetim kitaplığı  
  
   Windows denetim kitaplığı hata ayıklaması, bir sınıf kitaplığı projesinde hata ayıklamaya benzer. Çoğu durumda, Windows denetimini başka bir projeden çağıracaksınız. Çağıran projede hata ayıklarken, Windows denetiminizin koduna ileredebilir, kesme noktaları ayarlayabilir ve diğer hata ayıklama işlemlerini gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [Windows Forms denetimleri](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# ve Visual Basic): Web denetim kitaplığı  
  
   Daha fazla bilgi için bkz. [Web denetim kitaplığı (yönetilen kod)](../debugger/web-control-library-managed-code.md).  
  
- (C++): MFC ActiveX denetimi ve MFC akıllı cihaz ActiveX denetimi  
  
   ActiveX denetimleri, Internet üzerinden bir istemci bilgisayara yüklenebilen ve Web sayfalarında görüntülenen ve etkinleştirilen denetimlerdir.  
  
   Tek başına çalıştırılamadığından, ancak bir HTML Web sayfasına katıştırılması gerektiğinden, ActiveX denetimlerinde hata ayıklama, diğer denetim türlerini hata ayıklamaya benzer. Daha fazla bilgi için bkz. [nasıl yapılır: ActiveX denetiminde hata ayıklama](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): MFC akıllı cihaz DLL 'SI  
  
   Daha fazla bilgi için bkz. [MFC hata ayıklama teknikleri](../debugger/mfc-debugging-techniques.md).  
  
  Bu bölüm aşağıdaki konularda da bilgi içerir:  
  
- [Nasıl yapılır: DLL projesinde hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Nasıl Yapılır: Karışık Modda Hata Ayıklama](../debugger/how-to-debug-in-mixed-mode.md)  
  
  Bu konu, aşağıdaki bölümleri içerir ve bu, sınıf kitaplıklarının hata ayıklamaya nasıl hazırlanacağına dair hususlar sağlar:  
  
- [Hata ayıklama sürümü oluşturma](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Karışık modda hata ayıklama](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Varsayılan yapılandırma değiştirme](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [DLL hatalarını ayıklamanın yolları](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [Çağıran uygulama](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Web sayfasındaki denetimler](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [Komut penceresi](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="building-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Hata ayıklama sürümü oluşturma  
 Hata ayıklamayı nasıl başladığınızdan bağımsız olarak, önce DLL 'nin hata ayıklama sürümünü derlediğinizden ve hata ayıklama sürümünün uygulamanın onu bulmayı beklediği konumda olduğundan emin olun. Bu açık görünebilir, ancak bu adımı unutursanız, uygulama farklı bir DLL sürümü bulabilir ve yükleyebilir. Daha sonra program çalışmaya devam eder, ancak kesme noktasının neden hiçbir şekilde isabet etmediğini merak ediyor. Hata ayıklarken, hata ayıklayıcının **modüller** penceresini açarak programınızın hangi dll 'leri yüklediğini doğrulayabilirsiniz. **Modüller** penceresi, hata ayıkladığınız işlemde yüklenen her dll veya exe 'yi listeler. Daha fazla bilgi için bkz. [nasıl yapılır: modüller penceresini kullanma](../debugger/how-to-use-the-modules-window.md).  
  
 Hata ayıklayıcının C++ dilinde yazılmış koda eklemesi için kodun yaymalıdır `DebuggableAttribute` . [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) bağlayıcı seçeneğiyle bağlantı kurarak bunu kodunuza otomatik olarak ekleyebilirsiniz.  
  
## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Karışık modda hata ayıklama  
 DLL 'nizi çağıran çağıran uygulama yönetilen kodda veya yerel kodda yazılabilir. Yönetilen DLL 'niz yerel kod tarafından çağrılırsa ve her ikisinde de hata ayıklamak istiyorsanız, yönetilen ve yerel hata ayıklayıcıların her ikisinin de etkinleştirilmesi gerekir. Bunu, ** \<Project> Özellik sayfaları** iletişim kutusu veya penceresinde seçebilirsiniz. Bunu yaptığınızda, DLL projesinden veya çağıran uygulama projesinden hata ayıklamayı başlatıp başlatdığınıza bağlıdır. Daha fazla bilgi için bkz. [nasıl yapılır: karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md).  
  
## <a name="changing-default-configurations"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Varsayılan yapılandırma değiştirme  
 Proje şablonuyla bir konsol uygulaması projesi oluşturduğunuzda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklama ve yayın yapılandırmalarına yönelik gerekli ayarları otomatik olarak oluşturur. Gerekirse, bu ayarları değiştirebilirsiniz. Daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması için](../debugger/project-settings-for-a-cpp-debug-configuration.md)proje ayarları, [C# hata ayıklama yapılandırmaları](../debugger/project-settings-for-csharp-debug-configurations.md)için proje ayarları, [Visual Basic hata ayıklama yapılandırması Için proje](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ayarları ve [nasıl yapılır: hata ayıklama ve yayın yapılandırmalarını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md).  
  
## <a name="ways-to-debug-the-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL hatalarını ayıklamanın yolları  
 Bu bölümdeki projelerin her biri bir DLL oluşturur. DLL 'yi doğrudan çalıştıramazsınız; genellikle bir EXE tarafından çağrılmalıdır. Daha fazla bilgi için bkz. [Visual C++ projeleri oluşturma ve yönetme](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Çağıran uygulama aşağıdaki ölçütlerden birine benzeyebilir:  
  
- Sınıf kitaplığını içeren aynı çözümdeki başka bir projede oluşturulmuş bir uygulama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Zaten bir test veya üretim bilgisayarına dağıtılmış var olan bir uygulama.  
  
- Web üzerinde bulunur ve bir URL üzerinden erişilir.  
  
- DLL 'yi katıştıran bir Web sayfası içeren bir Web uygulaması.  
  
### <a name="debugging-the-calling-application"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Çağıran uygulamada hata ayıklama  
 DLL hata ayıklaması yapmak için, çağıran uygulamada, genellikle bir EXE veya bir Web uygulaması hata ayıklamayla başlayın. Hata ayıklamanın birkaç yolu vardır.  
  
- Çağıran uygulama için bir projeniz varsa, bu projeyi açabilir ve **Hata Ayıkla** menüsünden yürütmeyi başlatabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yürütmeyi başlatma](https://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Çağıran uygulama, zaten bir test veya üretim bilgisayarında dağıtılmış olan mevcut bir programdır ve zaten çalışıyorsa, buna iliştirebilirsiniz. DLL, Internet Explorer tarafından barındırılan bir denetimdir veya bir Web sayfasında bir denetim ise bu yöntemi kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: çalışan bir Işleme iliştirme](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- DLL projesinden hata ayıklaması yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: DLL projesinde hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md).  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Komut** penceresinden hata ayıklaması yapabilirsiniz. Bu durumda, **komut** penceresi uygulama rolünü yürütür.  
  
  Çağıran uygulamada hata ayıklamaya başlamadan önce, genellikle sınıf kitaplığında bir kesme noktası ayarlamak istersiniz. Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Kesme noktası isabet edildiğinde, sorunu yalıtana kadar her satırdaki eylemi gözlemleyerek kodda adım adım ilerleyin. Daha fazla bilgi için bkz. [kod Adımlama genel bakış](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
### <a name="controls-on-a-web-page"></a><a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Web sayfasındaki denetimler  
 Bir Web sayfası denetiminde hata ayıklamak için, bu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tür bir sayfa yoksa, onu katıştıran bir sayfa oluşturun. Ardından, kesme noktalarını Web sayfası koduna ve denetim koduna yerleştirebilirsiniz. Daha sonra Web sayfasını öğesinden çağırabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Çağıran uygulamada hata ayıklamaya başlamadan önce, genellikle DLL 'de bir kesme noktası ayarlamak istersiniz. Kesme noktası isabet edildiğinde, sorunu yalıtana kadar her satırdaki eylemi gözlemleyerek kodda adım adım ilerleyin. Daha fazla bilgi için bkz. [kesme noktaları ve Izleme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Komut penceresi  
 DLL 'deki işlevleri veya yöntemleri, çağıran bir uygulamaya sahip olmadan değerlendirebilirsiniz. Tasarım zamanı hata ayıklaması yapabilirsiniz ve **hemen** penceresini kullanırsınız. Bu şekilde hata ayıklamak için, DLL projesi açıkken aşağıdaki adımları izleyin:  
  
1. Hata ayıklayıcı **anında** penceresini açın.  
  
2. Sınıfında adlı bir yöntemi test etmek için `Test` `Class1` , `Class1` komut penceresine aşağıdaki C# kodunu yazarak türünde bir nesne oluşturun. Bu yönetilen kod, uygun sözdizimi değişikliklerinde Visual Basic ve C++ için geçerlidir:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     C# ' de, tüm adların tam olarak nitelenmiş olması gerekir. Ayrıca, tüm yöntemler veya değişkenler, hata ayıklama oturumunun geçerli kapsamı ve bağlamında olmalıdır.  
  
3. `Test`Tek bir parametre aldığını varsayarak `int` , `Test` **komut** penceresini kullanarak değerlendirin:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Sonuç, **hemen** penceresinde yazdırılır.  
  
4. `Test`Onun içine bir kesme noktası yerleştirip sonra işlevi yeniden değerlendirerek hata ayıklamaya devam edebilirsiniz:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Kesme noktası isabet eder ve adım adım ilerabileceksiniz `Test` . Yürütme ayrıldıktan sonra `Test` , hata ayıklayıcı Tasarım moduna geri alınacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Visual C++ proje türleri](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
