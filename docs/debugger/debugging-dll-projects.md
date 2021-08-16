---
title: DLL projelerinde hata ayıkla | Microsoft Docs
description: Visual Studio içindeki dinamik bağlantı kitaplığı (DLL) dosyalarında hata ayıklayın. dll 'leri oluşturmak, derlemek, yapılandırmak ve hatalarını ayıklamak için Visual Studio kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7fbeca9fbe809e157190aab60a8ecdd33b000b7a65ac35986f12aa3a767b1140
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264091"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio hata ayıklama dll 'leri (C#, C++, Visual Basic, F #)

DLL (dinamik bağlantı kitaplığı), birden fazla uygulama tarafından kullanılabilen kod ve verileri içeren bir kitaplıktır. dll 'leri oluşturmak, derlemek, yapılandırmak ve hatalarını ayıklamak için Visual Studio kullanabilirsiniz.

## <a name="create-a-dll"></a>DLL oluşturma

aşağıdaki Visual Studio proje şablonları dll 'ler oluşturabilir:

- C#, Visual Basic veya F # sınıf kitaplığı
- C# veya Visual Basic Windows Forms Control (WCF) kitaplığı
- C++ Dynamic-Link kitaplığı (DLL)

Daha fazla bilgi için bkz. [MFC hata ayıklama teknikleri](../debugger/mfc-debugging-techniques.md).

WCF kitaplığı hata ayıklaması, bir sınıf kitaplığında hata ayıklamaya benzer. ayrıntılar için bkz. [Windows Forms denetimleri](/dotnet/framework/winforms/controls/index).

Genellikle başka bir projeden DLL çağırırın. Çağıran projede hata ayıkladığınızda, DLL yapılandırmasına bağlı olarak, DLL kodunda bir adım adım ve hata ayıklama yapabilirsiniz.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL hata ayıklama yapılandırması

bir uygulama oluşturmak için Visual Studio proje şablonu kullandığınızda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklama ve yayın derleme yapılandırmalarına yönelik gerekli ayarları otomatik olarak oluşturur. Gerekirse bu ayarları değiştirebilirsiniz. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>C++ hata ayıklama Ggableattribute özelliğini ayarlama

Hata ayıklayıcının bir C++ DLL 'sine eklemesi için, C++ kodunun yaymalıdır `DebuggableAttribute` .

**Ayarlamak için `DebuggableAttribute` :**

1. **Çözüm Gezgini** ' de C++ DLL projesini seçin ve **Özellikler** simgesini seçin ya da projeye sağ tıklayıp **Özellikler**' i seçin.

1. **Özellikler** bölmesinde, **bağlayıcı**  >  **hata ayıklama** altında, **hata ayıklanabilir derlemesi** için **Evet (/ASSEMBLYDEBUG)** öğesini seçin.

Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> C/C++ DLL dosyası konumlarını ayarla

Bir dış DLL 'de hata ayıklamak için, çağıran bir proje DLL 'yi, [. pdb dosyasını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)ve DLL 'in gerektirdiği diğer dosyaları bulabilmelidir. Bu dosyaları *\<project folder> \debug* çıkış klasörünüze kopyalamak için özel bir yapı görevi oluşturabilir veya dosyaları el ile kopyalayabilirsiniz.

C/C++ projeleri için, çıktı klasörüne kopyalamak yerine, proje özellik sayfalarında üst bilgi ve LıB dosya konumlarını ayarlayabilirsiniz.

**C/C++ üst bilgisi ve LIB dosya konumlarını ayarlamak için:**

1. **Çözüm Gezgini** ' de C/C++ DLL projesini seçin ve **Özellikler** simgesini seçin ya da projeye sağ tıklayıp **Özellikler**' i seçin.

1. **Özellikler** bölmesinin üst kısmında, **yapılandırma** altında **tüm yapılandırmalar**' ı seçin.

1. **C/C++**  >  **genel**  >  **ek içerme dizinleri** altında, üst bilgi dosyaları içeren klasörü belirtin.

1. **Bağlayıcı**  >  **genel**  >  **ek kitaplıklar dizinleri** altında LIB dosyaları içeren klasörü belirtin.

1. **Bağlayıcı**  >  **girişi**  >  **ek bağımlılıklar** altında LIB dosyaları için tam yolu ve dosya adını belirtin.

1. **Tamam**’ı seçin.

c++ proje ayarları hakkında daha fazla bilgi için bkz. [Windows C++ özellik sayfası başvurusu](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Hata ayıklama sürümü oluşturma

Hata ayıklamaya başlamadan önce DLL 'nin hata ayıklama sürümünü ayarladığınızdan emin olun. Bir DLL dosyasında hata ayıklamak için, çağıran bir uygulama [. pdb dosyasını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ve DLL 'nin gerektirdiği diğer dosyaları bulabilmelidir.

DLL dosyalarını *\<calling project folder> \debug* çıkış klasörünüze kopyalamak için özel bir yapı görevi oluşturabilir veya dosyaları el ile kopyalayabilirsiniz.

DLL dosyasını doğru konumunda çağırdığınızdan emin olun. Bu açık görünebilir, ancak çağıran bir uygulama DLL 'nin farklı bir kopyasını bulup yüklerse, hata ayıklayıcı sizin ayarladığınız kesme noktalarına hiçbir şekilde ulaşmayacaktır.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL hatalarını ayıklama

Bir DLL dosyasını doğrudan çalıştıramazsınız. Genellikle bir *.exe* dosyası olan bir uygulama tarafından çağrılmalıdır. daha fazla bilgi için bkz. [Visual Studio projeler-C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Bir DLL dosyasında hata ayıklamak için, [çağıran uygulamadan hata ayıklamayı başlatabilir](#vxtskdebuggingdllprojectsthecallingapplication)veya çağıran uygulamayı belirterek [DLL projesinden hata ayıklaması](how-to-debug-from-a-dll-project.md) yapabilirsiniz. Ayrıca, çağıran bir uygulama kullanmadan, tasarım zamanında DLL işlevleri veya yöntemleri değerlendirmek için hata ayıklayıcı [anında penceresini](#vxtskdebuggingdllprojectstheimmediatewindow) de kullanabilirsiniz.

Daha fazla bilgi için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Çağıran uygulamadan hata ayıklamayı Başlat

DLL 'yi çağıran uygulama şunları yapabilir:

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Aynı veya dll 'den farklı bir çözümde bulunan bir projeden uygulama.
- Zaten dağıtılan ve bir test ya da üretim bilgisayarında çalışan mevcut bir uygulama.
- Web üzerinde bulunur ve bir URL üzerinden erişilir.
- DLL 'yi katıştıran bir Web sayfasına sahip bir Web uygulaması.

Çağıran bir uygulamadaki DLL hatalarını ayıklamak için şunları yapabilirsiniz:

- Çağıran uygulama için projeyi açın **ve hata ayıklamayı**  >  **Başlat hata ayıklamayı başlatın** veya **F5**'e basın.

  veya

- Zaten dağıtılan ve test ya da üretim bilgisayarında çalışan bir uygulamaya iliştirme. Web sitelerindeki veya Web Apps 'teki dll 'Ler için bu yöntemi kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: çalışan bir Işleme iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Çağıran uygulamada hata ayıklamaya başlamadan önce, DLL 'de bir kesme noktası ayarlayın. Bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md). DLL kesme noktası isabet edildiğinde, kodu adım adım ilerleyerek her satırdaki eylemi gözlemleyerek yapabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

Hata ayıklama sırasında, dll 'Leri ve uygulamanın yüklediği dosyaları *.exe* doğrulamak için **modüller** penceresini kullanabilirsiniz. **modüller** penceresini açmak için hata ayıklama sırasında Windows modülleri **hata ayıkla**' yı seçin  >    >  . Daha fazla bilgi için bkz. [nasıl yapılır: modüller penceresini kullanma](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Hemen penceresini kullanma

Tasarım zamanında DLL işlevlerini veya yöntemlerini değerlendirmek için **hemen** penceresini kullanabilirsiniz. **Komut** penceresi, çağıran bir uygulamanın rolünü yürütür.

>[!NOTE]
>En çok proje türüyle tasarım zamanında **hemen** penceresini kullanabilirsiniz. SQL, web projeleri veya betik için desteklenmez.

Örneğin, sınıfında adlı bir yöntemi test etmek için `Test` `Class1` :

1. DLL projesi açıkken **hata ayıkla** Windows hemen '  ni seçerek  >    >   veya **Ctrl** + **Alt** + **I** tuşlarına basarak hemen pencereyi açın.

1. `Class1` **Komut** penceresine aşağıdaki C# kodunu yazıp **ENTER** tuşuna basarak bir nesne oluşturun. bu yönetilen kod, uygun sözdizimi değişikliklerinde C# ve Visual Basic için geçerlidir:

   ```csharp
   Class1 obj = new Class1();
   ```

   C# ' de, tüm adların tam olarak nitelenmiş olması gerekir. Dil hizmeti ifadeyi değerlendirmeye çalıştığında, herhangi bir yöntem veya değişken geçerli kapsamda ve bağlamda olmalıdır.

1. `Test`Tek bir parametre aldığını varsayarak `int` , `Test` **komut** penceresini kullanarak değerlendirin:

   ```csharp
   ?obj.Test(10);
   ```

   Sonuç, **hemen** penceresinde yazdırılır.

1. `Test`İçinde bir kesme noktası yerleştirip sonra işlevi yeniden değerlendirerek hata ayıklamaya devam edebilirsiniz.

   Kesme noktası isabet eder ve adım adım ilerlenebilir `Test` . Yürütme ayrıldıktan sonra `Test` , hata ayıklayıcı Tasarım moduna geri alınacaktır.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Karışık modda hata ayıklama

Yönetilen veya yerel koddaki DLL için bir çağıran uygulama yazabilirsiniz. Yerel uygulamanız yönetilen bir DLL 'yi çağırırsa ve her ikisinde de hata ayıklamak istiyorsanız, proje özelliklerinde hem yönetilen hem de yerel hata ayıklayıcıları etkinleştirebilirsiniz. Tam işlem, DLL projesinden veya çağıran uygulama projesinde hata ayıklamayı başlatmak isteyip istemediğinize bağlıdır. Daha fazla bilgi için bkz. [nasıl yapılır: karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md).

Ayrıca, yönetilen bir çağıran projeden yerel bir DLL dosyasında hata ayıklayabilirsiniz. Daha fazla bilgi için bkz. [yönetilen ve yerel kodda hata ayıklama](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
- [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++ hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
