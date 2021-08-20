---
title: DLL projelerinde hata | Microsoft Docs
description: Dinamik bağlantı kitaplığı (DLL) dosyalarında hata ayıklama Visual Studio. URL Visual Studio oluşturmak, derlemek, yapılandırmak ve hata ayıklamak için Visual Studio kullanın.
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
ms.openlocfilehash: ba25ff92131f9f044e0b81d25cf49e865563161b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134122"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio 'de (C#, C++, Visual Basic, F#) HATA AYıKLAMA

DLL (dinamik bağlantı kitaplığı), birden fazla uygulama tarafından kullanılan kod ve veriler içeren bir kitaplıktır. URL'Visual Studio oluşturmak, derlemek, yapılandırmak ve hata ayıklamak için Visual Studio kullanabilirsiniz.

## <a name="create-a-dll"></a>DLL oluşturma

Aşağıdaki Visual Studio proje şablonları, URL'ler oluşturabilir:

- C#, Visual Basic veya F# Sınıf Kitaplığı
- C# veya Visual Basic Windows Forms Denetimi (WCF) Kitaplığı
- C++ Dynamic-Link Kitaplığı (DLL)

Daha fazla bilgi için bkz. [MFC hata ayıklama teknikleri.](../debugger/mfc-debugging-techniques.md)

WCF Kitaplığında Hata Ayıklama, Sınıf Kitaplığında hata ayıklamaya benzer. Ayrıntılar için [bkz. Windows Forms Denetimleri.](/dotnet/framework/winforms/controls/index)

Bir DLL'i genellikle başka bir projeden çağırmanız gerekir. DLL yapılandırmasına bağlı olarak, çağıran projede hata ayıklarken DLL koduna adım atabilir ve hata ayıkabilirsiniz.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL hata ayıklama yapılandırması

Uygulama oluşturmak için Visual Studio proje şablonu kullanırsanız, Hata Ayıklama ve Yayın derleme yapılandırmaları [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için gerekli ayarları otomatik olarak oluşturur. Gerekirse bu ayarları değiştirebilirsiniz. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project C# hata ayıklama yapılandırmaları için ayarlar](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl kullanılır: Hata Ayıklama ve Yayın yapılandırmalarını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>C++ DebuggableAttribute ayarlama

Hata ayıklayıcının bir C++ DLL'ye eklemesi için C++ kodunun yaymanız `DebuggableAttribute` gerekir.

**ayarlamak `DebuggableAttribute` için:**

1. Çözüm Gezgini'de C++  DLL projesini seçin, **Özellikler** simgesini seçin veya projeye sağ tıklar ve Özellikler'i **seçin.**

1. Özellikler **bölmesinde,** **Linker Hata Ayıklama altında,** Hata  >  **Ayıklanabilir** Derleme **için Evet (/ASSEMBLYDEBUG)** **öğesini seçin.**

Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> C/C++ DLL dosya konumlarını ayarlama

Dış DLL'de hata ayıklamak için, çağıran proje DLL'i, [.pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)dosyasını ve DLL'nin gerektirdiği diğer dosyaları bulmalıdır. Bu dosyaları *\<project folder> \Hata* ayıklama çıkış klasörünüze kopyalamak için özel bir derleme görevi oluşturabilir veya dosyaları oraya el ile kopyaleyebilirsiniz.

C/C++ projeleri için, bunları çıkış klasörüne kopyalamak yerine proje özellik sayfalarında üst bilgi ve LIB dosya konumlarını ayarlayın.

**C/C++ üst bilgisi ve LIB dosya konumlarını ayarlamak için:**

1. Çözüm Gezgini'de C/C++  DLL projesini seçin  ve Özellikler simgesini seçin veya projeye sağ tıklar ve Özellikler'i **seçin.**

1. Özellikler bölmesinin üst **kısmında,** Yapılandırma'nın **altında Tüm** **Yapılandırmalar'ı seçin.**

1. **C/C++**  >  **Genel Ek** Dahil  >  **Dizinleri** altında, üst bilgi dosyalarını içeren klasörü belirtin.

1. Linker   >  **Genel**  >  **Ek Kitaplık dizinleri altında** LIB dosyaları olan klasörü belirtin.

1. Linker Input Additional Dependencies **(BağlantıCı** Girişi Ek  >    >  Bağımlılıkları) altında LIB dosyalarının tam yolunu ve dosya adını belirtin.

1. **Tamam**’ı seçin.

C++ proje ayarları hakkında daha fazla bilgi için [bkz. Windows C++ özellik sayfası başvurusu.](/cpp/build/reference/property-pages-visual-cpp)

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Hata ayıklama sürümü oluşturma

Hata ayıklamaya başlamadan önce DLL'nin Hata Ayıklama sürümünü derlemeyi emin olun. Dll'de hata ayıklamak için, çağıran uygulamanın [.pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) dosyasını ve DLL'nin gerektirdiği diğer dosyaları bulmalıdır.

DLL dosyalarını *\<calling project folder> \Hata* ayıklama çıkış klasörünüze kopyalamak için özel bir derleme görevi oluşturabilir veya dosyaları orada el ile kopyaleyebilirsiniz.

DLL'i doğru konumda çağırarak emin olun. Bu açıkça görünebilir, ancak çağıran bir uygulama DLL'nin farklı bir kopyasını bulursa ve yüklerse, hata ayıklayıcı hiçbir zaman ayarlayıp ayarlayıp kesme noktalarına isabetmayacak.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL'de hata ayıklama

DLL'i doğrudan çalıştıraazın. Genellikle bir uygulama tarafından çağrıl .exe. Daha fazla bilgi için [bkz. Visual Studio projeleri - C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Bir DLL'de hata [](#vxtskdebuggingdllprojectsthecallingapplication)ayıklamak için, çağıran uygulamasından hata ayıklamaya başlayabilir veya [çağıran](how-to-debug-from-a-dll-project.md) uygulamasını belirterek DLL projesinde hata ayıklamaya başlayabilirsiniz. Ayrıca, dll işlevlerini veya yöntemlerini [bir çağırma](#vxtskdebuggingdllprojectstheimmediatewindow) uygulaması kullanmadan tasarım zamanında değerlendirmek için hata ayıklayıcı Anlık penceresini de kullanabilirsiniz.

Daha fazla bilgi için [bkz. Hata ayıklayıcısına ilk bakış.](../debugger/debugger-feature-tour.md)

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Çağıran uygulamanın hata ayıklamasını başlatma

DLL çağıran uygulama şöyle olabilir:

- Aynı veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] DLL'den farklı bir çözümde yer alan bir projeden uygulama.
- Zaten bir test veya üretim bilgisayarına dağıtılmış ve çalışan mevcut bir uygulama.
- Web'de bulunur ve URL üzerinden erişilir.
- DLL'nin ekli olduğu bir web sayfasına sahip bir web uygulaması.

Çağıran bir uygulamanın DLL'lerinden hata ayıklamak için şunları sebilirsiniz:

- Çağıran uygulama için projeyi açın ve Hata AyıklamaYı Başlat Hata Ayıklamayı Başlat'ı seçerek **veya**  >   F5 tuşuna basarak hata **ayıklamaya başlayabilirsiniz.**

  veya

- Zaten dağıtılmış ve bir test veya üretim bilgisayarda çalışan bir uygulamaya ekleme. Web sitelerine veya web uygulamalarına yönelik URL'ler için bu yöntemi kullanın. Daha fazla bilgi için, [bkz. How to: Attach to a running process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Çağıran uygulamada hata ayıklamaya başlamadan önce DLL'de bir kesme noktası ayarlayın. Bkz. [Kesme noktaları kullanma.](../debugger/using-breakpoints.md) DLL kesme noktası isabet edinca, her satırda eylemi gözlemleyerek kodda adım adım atabilirsiniz. Daha fazla bilgi için [bkz. Hata ayıklayıcısında kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

Hata ayıklama sırasında Modüller penceresini **kullanarak** UYGULAMAnın yük.exe *dosyaları* doğruabilirsiniz. Modüller **penceresini açmak için** hata ayıklama sırasında Modüller'de **hata**  >  **Windows**  >  **seçin.** Daha fazla bilgi için [bkz. Nasıl kullanılır: Modüller penceresini kullanma.](../debugger/how-to-use-the-modules-window.md)

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Hemen penceresini kullanma

Tasarım zamanında DLL **işlevlerini** veya yöntemlerini değerlendirmek için Hemen penceresini kullanabilirsiniz. Hemen **penceresi,** çağıran bir uygulamanın rolünü oynar.

>[!NOTE]
>Çoğu proje **türüyle** tasarım zamanında Anında penceresini kullanabilirsiniz. Bu, web projeleri SQL betikler için desteklanmaz.

Örneğin sınıfında adlı bir yöntemi test `Test` etmek `Class1` için:

1. DLL projesi açıkken, Anında Hata Ayıkla'Windows veya    >    >   Ctrl Alt I **tuşlarına** basarak Anında + **penceresini** + **açın.**

1. Anında pencereye aşağıdaki `Class1` C# kodunu yazarak ve Enter tuşuna basarak **türünde bir** nesne örneği **oluşturma.** Bu yönetilen kod C# ve Visual Basic söz dizimi değişiklikleriyle birlikte çalışır:

   ```csharp
   Class1 obj = new Class1();
   ```

   C# içinde tüm adların tam olması gerekir. Dil hizmeti ifadeyi değerlendirmeye çalıştığında tüm yöntemlerin veya değişkenlerin geçerli kapsamda ve bağlamda olması gerekir.

1. Bunun tek bir `Test` parametreyi `int` kabul ediyor olduğunu `Test` varsayarak, Hemen penceresini kullanarak **değerlendirin:**

   ```csharp
   ?obj.Test(10);
   ```

   Sonuç, Anında penceresinde **yazdırılır.**

1. Hata ayıklamaya devam etmek için içine bir kesme noktası yerleştirerek ve `Test` ardından işlevi yeniden değerlendirin.

   Kesme noktası isabetli olur ve adım adım üzerinden `Test` geçerek. Yürütmeden `Test` sonra, hata ayıklayıcı tasarım moduna geri döner.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Karma mod hata ayıklama

Yönetilen veya yerel kodda DLL için bir çağrı uygulaması yazabilirsiniz. Yerel uygulamanız yönetilen DLL'yi çağırıyorsa ve her ikisinde de hata ayıklamak istiyorsanız, proje özelliklerinde hem yönetilen hem de yerel hata ayıklayıcılarını etkinleştirebilirsiniz. Tam işlem, DLL projesinde hata ayıklamayı başlatmak mı yoksa çağıran uygulama projesini mi başlatmak istediğinize bağlıdır. Daha fazla bilgi için [bkz. Karma modda hata ayıklama.](../debugger/how-to-debug-in-mixed-mode.md)

Ayrıca, yönetilen bir çağıran projeden yerel DLL'de hata ayıklar. Daha fazla bilgi için [bkz. Yönetilen ve yerel kodda hata ayıklama.](how-to-debug-managed-and-native-code.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
- [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# ve Visual Basic türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project C++ Hata Ayıklama yapılandırması için yapılandırma ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project C# Hata Ayıklama yapılandırmaları için ayarlar](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project Hata Ayıklama yapılandırması Visual Basic ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
