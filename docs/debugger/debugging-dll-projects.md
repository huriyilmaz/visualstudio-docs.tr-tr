---
title: Hata Ayıklama DLL projeleri | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302205"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio'da Hata Ayıklama DL'leri (C#, C++, Visual Basic, F#)

DLL (dinamik bağlantı kitaplığı), birden fazla uygulama tarafından kullanılabilen kod ve verileri içeren bir kitaplıktır. DL'leri oluşturmak, oluşturmak, yapılandırmak ve hata ayıklamak için Visual Studio'yı kullanabilirsiniz.

## <a name="create-a-dll"></a>DLL oluşturma

Aşağıdaki Visual Studio proje şablonları DL'ler oluşturabilir:

- C#, Visual Basic veya F# Sınıf Kitaplığı
- C# veya Visual Basic Windows Formlar Kontrolü (WCF) Kitaplığı
- C++ Dinamik Bağlantı Kitaplığı (DLL)

Daha fazla bilgi için [MFC hata ayıklama tekniklerine](../debugger/mfc-debugging-techniques.md)bakın.

WCF Kitaplığı hata ayıklama, Sınıf Kitaplığı'nı hata ayıklamaya benzer. Ayrıntılar için [Windows Forms Denetimleri'ne](/dotnet/framework/winforms/controls/index)bakın.

Genellikle başka bir projeden DLL'yi çağırırsınız. Arama projesini hata ayıklamaolduğunuzda, DLL yapılandırmasına bağlı olarak, DLL koduna adım atabilir ve hata ayıklayabilirsiniz.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>DLL hata ayıklama yapılandırması

Bir uygulama oluşturmak için Visual Studio proje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] şablonu kullandığınızda, Hata Ayıklama ve Sürüm yapı yapılandırmaları için otomatik olarak gerekli ayarları oluşturur. Gerekirse bu ayarları değiştirebilirsiniz. Daha fazla bilgi için aşağıdaki makalelere bakın:

- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# hata ayıklama yapılandırmaları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılı: Hata Ayıklama ve Sürüm yapılandırmalarını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>C++ Hata Ayıklabilme Özelliğini Ayarla

Hata ayıklayıcının C++ DLL'ye bağlanması için C++ kodu `DebuggableAttribute`yayılmalıdır.

**Ayarlamak `DebuggableAttribute`için:**

1. **Solution Explorer'da** C++ DLL projesini seçin ve **Özellikler** simgesini seçin veya projeyi sağ tıklatın ve **Özellikler'i**seçin.

1. **Özellikler** bölmesinde, **Linker** > **Hata Ayıklama**altında, **Hata Ayıklama**için **Evet (/ASSEMBLYDEBUG)** seçeneğini belirleyin.

Daha fazla bilgi için bkz: [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>C/C++ DLL dosya konumlarını ayarlama

Harici bir DLL hata ayıklamak için, bir arama projesi DLL'yi, [.pdb dosyasını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)ve DLL'nin gerektirdiği diğer dosyaları bulabilmeli. Bu dosyaları * \<proje klasörünüze kopyalamak>\Hata Ayıklama* çıktı klasörüne kopyalamak için özel bir yapı görevi oluşturabilir veya dosyaları el ile kopyalayabilirsiniz.

C/C++ projeleri için, üstbilgi ve LIB dosya konumlarını çıktı klasörüne kopyalamak yerine proje özelliği sayfalarında ayarlayabilirsiniz.

**C/C++ üstbilgisini ve LIB dosya konumlarını ayarlamak için:**

1. **Solution Explorer'da** C/C++ DLL projesini seçin ve **Özellikler** simgesini seçin veya projeyi sağ tıklatın ve **Özellikler'i**seçin.

1. **Özellikler** bölmesinin üst kısmında, **Yapılandırma**altında Tüm **Yapılandırmaları**seçin.

1. **C/C++** > **Genel** > **Ek Ekle Dizinleri**altında, üstbilgi dosyaları olan klasörü belirtin.

1. **Bağlayıcı** > **Genel** > **Ek Kitaplıklar Dizinleri**altında, LIB dosyaları olan klasörü belirtin.

1. **Bağlayıcı** > **Girişi** > **Ek Bağımlılıklar**altında, LIB dosyaları için tam yol ve dosya adını belirtin.

1. **Tamam'ı**seçin.

C++ proje ayarları hakkında daha fazla bilgi için [Windows C++ özellik sayfası başvurusuna](/cpp/build/reference/property-pages-visual-cpp)bakın.

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Hata Ayıklama sürümü oluşturma

Hata ayıklamaya başlamadan önce DLL'nin Hata Ayıklama sürümünü oluşturduğunuzdan emin olun. Bir DLL hata sını ayıklamak için, bir arama [uygulamasının .pdb dosyasını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ve DLL'nin gerektirdiği diğer dosyaları bulababilmesi gerekir.

DLL dosyalarını * \<arama proje klasörünüz>\Debug* çıktı klasörüne kopyalamak için özel bir yapı görevi oluşturabilir veya dosyaları el ile kopyalayabilirsiniz.

DLL'yi doğru konumda n için aradığından emin olun. Bu açık görünebilir, ancak bir arama uygulaması DLL'nin farklı bir kopyasını bulur ve yüklerse, hata ayıklama ayarladığınız kesme noktalarına asla ulaşamaz.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Bir DLL hata ayıklama

Doğrudan Bir DLL çalıştıramaz. Genellikle bir *.exe* dosyası olan bir uygulama tarafından çağrılmalıdır. Daha fazla bilgi için [Visual Studio projelerine](/cpp/ide/creating-and-managing-visual-cpp-projects)bakın - C++ .

Bir DLL hata sını ayıklamak için, [arama uygulamasından hata ayıklamaya başlayabilir](#vxtskdebuggingdllprojectsthecallingapplication)veya arama uygulamasını belirterek [DLL projesinden hata ayıklamaya](how-to-debug-from-a-dll-project.md) başlayabilirsiniz. Arama uygulaması kullanmadan DLL işlevlerini veya yöntemlerini tasarım zamanında değerlendirmek için hata ayıklayıcı [Hemen penceresini](#vxtskdebuggingdllprojectstheimmediatewindow) de kullanabilirsiniz.

Daha fazla bilgi için [hata ayıklama bölümüne ilk bakın.](../debugger/debugger-feature-tour.md)

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Arama uygulamasından hata ayıklamaya başlayın

DLL çağıran uygulama şu olabilir:

- DLL'den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aynı veya farklı bir çözümdeki bir projeden bir uygulama.
- Test veya üretim bilgisayarında zaten dağıtılan ve çalışan varolan bir uygulama.
- Web'de bulunan ve bir URL üzerinden erişilen.
- DLL'yi yerleştiren bir web sayfası olan bir web uygulaması.

Bir Arama uygulamasından Bir DLL hatasını ayıklamak için şunları yapabilirsiniz:

- Arama uygulaması için projeyi açın ve **Hata** > **Ayıklama Başlat hata ayıklama** veya **F5**tuşuna basarak hata ayıklamaya başlayın.

  or

- Test veya üretim bilgisayarında zaten dağıtılan ve çalışan bir uygulamaya takın. Bu yöntemi web sitelerinde veya web uygulamalarında DL'ler için kullanın. Daha fazla bilgi için [bkz: Çalışan bir işleme iliştirin.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

Arama uygulamasını hata ayıklamaya başlamadan önce, DLL'de bir kesme noktası ayarlayın. Bkz. [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md). DLL kesme noktası vurulduğunda, her satırdaki eylemi gözlemleyerek kodun içinden geçebilirsiniz. Daha fazla bilgi için [hata ayıklayıcıda kodu gezin'](../debugger/navigating-through-code-with-the-debugger.md)e bakın.

Hata ayıklama sırasında, **DL'leri** ve *.exe* dosyalarını doğrulamak için Modüller penceresini kullanabilirsiniz. Hata ayıklama sırasında **Modüller** penceresini açmak için **Hata Ayıklama** > **Windows** > **Modülleri'ni**seçin. Daha fazla bilgi için [bkz: Modüller penceresini kullanın.](../debugger/how-to-use-the-modules-window.md)

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Hemen pencereyi kullanma

Tasarım zamanında DLL işlevlerini veya yöntemlerini değerlendirmek için **Hemen** pencereyi kullanabilirsiniz. **Hemen** penceresi bir arama uygulaması rolünü oynar.

>[!NOTE]
>Çoğu proje türüyle tasarım zamanında **Hemen** pencereyi kullanabilirsiniz. SQL, web projeleri veya komut dosyası için desteklenmez.

Örneğin, sınıfta `Test` `Class1`adlı bir yöntemi test etmek için:

1. DLL projesi açıkken, **Hata Ayıklama** > **Pencerelerini** > **Hemen** seçerek veya **Ctrl**+**Alt**+**I'e**basarak **Hemen** pencereyi açın.

1. **Hemen** penceresine aşağıdaki C# kodunu yazarak ve **Enter**tuşuna basarak bir tür `Class1` nesnesini anında Bu yönetilen kod, uygun sözdizimi değişiklikleriyle Birlikte C# ve Visual Basic için çalışır:

   ```csharp
   Class1 obj = new Class1();
   ```

   C#'da tüm adlar tam olarak nitelikli olmalıdır. Dil hizmeti ifadeyi değerlendirmeye çalıştığında herhangi bir yöntem veya değişken geçerli kapsam ve bağlamda olmalıdır.

1. Bir `Test` `int` parametre gerektiğini varsayarsak, `Test` **Hemen** pencereyi kullanarak değerlendirin:

   ```csharp
   ?obj.Test(10);
   ```

   Sonuç **Hemen** penceresinde yazdırılır.

1. İçine bir kesme `Test` noktası yerleştirip sonra işlevi yeniden değerlendirerek hata ayıklama yapmaya devam edebilirsiniz.

   Kırılma noktası vurulacak ve sen de `Test`geçebilirsin. Yürütme ayrıldıktan `Test`sonra hata ayıklama tasarım modunda geri dönecektir.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Karışık mod hata ayıklama

Yönetilen veya yerel kodda bir DLL için bir arama uygulaması yazabilirsiniz. Yerel uygulamanız yönetilen bir DLL'yi çağırır ve her ikisini de hata ayıklamak istiyorsanız, proje özelliklerinde yönetilen ve yerel hata ayıklayıcıları etkinleştirebilirsiniz. Tam işlem, DLL projesinden veya arama uygulaması projesinden hata ayıklamaya başlamak isteyip istemediğinizbağlıdır. Daha fazla bilgi için [bkz: Karışık modda hata ayıklama.](../debugger/how-to-debug-in-mixed-mode.md)

Ayrıca, yönetilen bir arama projesinden yerel bir DLL'yi hata ayıklayabilirsiniz. Daha fazla bilgi için yönetilen [ve yerel kodu nasıl hata ayıklama göreceğiz.](how-to-debug-managed-and-native-code.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
- [C++ projelerini hata ayıklamaya hazırlanın](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F#ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++ Hata Ayıklama yapılandırması için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C# Hata Ayıklama yapılandırmaları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic Hata Ayıklama yapılandırması için proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
