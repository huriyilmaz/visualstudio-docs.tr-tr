---
title: 'Öğretici: Hata Ayıklama C# ve C++ kodu (karma mod)'
description: Karma mod hata ayıklama kullanarak bir .NET Core veya .NET Framework uygulamasından yerel bir DLL'yi nasıl hata ayıklama yapacağınızı öğrenin
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 06f68962eb7cdb6e4fc0290ee5c6559721afb52b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77416366"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Öğretici: Aynı hata ayıklama oturumunda C# ve C++ hata ayıklama

Visual Studio, karışık mod hata ayıklama olarak adlandırılan hata ayıklama oturumunda birden fazla hata ayıklama türünü etkinleştirmenizi sağlar. Bu öğreticide, tek bir hata ayıklama oturumunda hem yönetilen hem de yerel kodu hata ayıklamayı öğrenirsiniz.

Bu öğretici, yönetilen bir uygulamadan yerel kodu nasıl ayıklama nız gerektiğini gösterir, ancak [yerel bir uygulamadan yönetilen kodu](../debugger/how-to-debug-in-mixed-mode.md)da ayıklayabilirsiniz. Hata ayıklayıcı ayrıca [Python ve yerel kodu](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)hata ayıklama ve ASP.NET gibi uygulama türlerinde komut dosyası hata ayıklayıcı kullanma gibi karışık mod hata ayıklama diğer türleri destekler.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Basit bir yerel DLL oluşturma
> * DLL'yi aramak için basit bir .NET Core veya .NET Framework uygulaması oluşturun
> * Karışık mod hata ayıklama yapılandırma
> * Hata ayıklamayı başlatın
> * Yönetilen uygulamada bir kesme noktasına çarpma
> * Yerel koda adım atma

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki iş yükleriyle Visual Studio yüklü olmalıdır:
- **C++ ile masaüstü geliştirme**
- **.NET masaüstü geliştirme** veya **.NET Core çapraz platform geliştirme**, oluşturmak istediğiniz uygulama türüne bağlı olarak.

Visual Studio'nuz yoksa, ücretsiz olarak yüklemek için [Visual Studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin.

Visual Studio yüklüyse, ancak ihtiyacınız olan iş yüklerini bilmiyorsanız, Visual Studio **Yeni Proje** iletişim kutusunun sol bölmesinde **Görsel Studio Yükleyicisini Aç'ı** seçin. Visual Studio Yükleyici'de, ihtiyacınız olan iş yüklerini seçin ve sonra **Değiştir'i**seçin.

## <a name="create-a-simple-native-dll"></a>Basit bir yerel DLL oluşturma

**DLL projesi için dosyaları oluşturmak için:**

1. Visual Studio'u açın ve bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **Boş Proje**yazın, **Şablonlar'ı**seçin, ardından C++için **Boş Proje'yi** seçin. Görünen iletişim kutusunda **Oluştur'u**seçin. Ardından, **Mixed_Mode_Debugging** gibi bir ad yazın ve **Oluştur'u**tıklatın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C++** altında Diğer 'i seçin ve sonra orta bölmede Boş **Proje'yi**seçin. **Other** Ardından, **Mixed_Mode_Debugging** gibi bir ad yazın ve **Tamam'ı**tıklatın.
    ::: moniker-end

    **Boş Proje** proje şablonunu görmüyorsanız, Visual Studio Yükleyici'yi açan **Araçlar** > **Araçları ve Özellikleri Al...**(Visual Studio Installer'ı açar) gidin. Visual Studio Installer başlattı. C++ iş **yüküyle Masaüstü geliştirmeyi** seçin ve ardından **Değiştir'i**seçin.

    Visual Studio projeyi oluşturur.

1. **Çözüm Gezgini'nde** **Kaynak Dosyaları**seçin ve ardından **Project** > **Add New Item'i**seçin. Veya **Kaynak Dosyaları** sağ tıklatın ve**Yeni Öğe** **Ekle'yi** > seçin.

1. Yeni **Öğe** iletişim kutusunda **C++ dosyasını (.cpp)** seçin. **Ad** alanına **Mixed_Mode.cpp** yazın ve sonra **Ekle'yi**seçin.

    Visual **Studio, Solution Explorer'a**yeni C++ dosyasını ekler.

1. Aşağıdaki kodu *Mixed_Mode.cpp'ye*kopyalayın:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. **Çözüm Gezgini'nde** **Üstbilgi Dosyaları'nı**seçin ve ardından **Project** > **Add New Item'i**seçin. Veya **Üstbilgi Dosyaları'nı** sağ tıklatın ve**Yeni Öğe** **Ekle'yi** > seçin.

1. Yeni **Öğe** iletişim kutusunda **Üstbilgi dosyası (.h)**'yi seçin. **Ad** alanına **Mixed_Mode.h** yazın ve sonra **Ekle'yi**seçin.

   Visual **Studio, Solution Explorer'a**yeni üstbilgi dosyası ekler.

1. Aşağıdaki kodu *Mixed_Mode.h'ye*kopyalayın:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. **Dosyaları** > kaydetmek için Dosya**Yı Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.

**DLL projesini yapılandırmak ve oluşturmak için:**

1. Visual Studio araç çubuğunda **Hata Ayıklama** yapılandırmasını ve **x86** veya **x64 platformlarını** seçin. Arama uygulamanız her zaman 64 bit modunda çalışan .NET Core olacaksa, platform olarak **x64'i** seçin.

1. **Çözüm Gezgini'nde,** **proje düğümüMixed_Mode_Debugging** seçin ve **Özellikler** simgesini seçin veya proje düğümüne sağ tıklayın ve **Özellikler'i**seçin.

1. **Özellikler** bölmesinin üst kısmında, **Yapılandırmanın** **Active(Hata Ayıklama)** olarak ayarlandığınızdan ve **Platform'un** araç çubuğunda ayarladığıyla aynı olduğundan emin olun: **x64**veya x86 platformu için **Win32.**

   > [!IMPORTANT]
   > Platformu **x86'dan** **x64'e** veya tam tersi bir platforma değiştirirseniz, yeni platformun özelliklerini yeniden yapılandırmanız gerekir.

1. Sol bölmedeki **Yapılandırma Özellikleri** altında, **Bağlayıcı** > **Gelişmiş'i**seçin ve Giriş **Noktası Yok'un**yanındaki açılır noktada No 'yu seçin. **No** **Hayır**olarak değiştirmeniz gerekiyorsa **Uygula'yı**seçin.

1. **Yapılandırma Özellikleri**altında **Genel'i**seçin ve **Configuration Type'ın**yanındaki açılır açılır durumda **Dinamik Kitaplık (.dll) seçeneğini belirleyin.** **Uygula**’yı ve sonra **Tamam**’ı seçin.

   ![Yerel bir DLL'ye geçiş](../debugger/media/mixed-mode-set-as-native-dll.png)

1. **Solution Explorer'da** projeyi seçin ve ardından **Yapı** > **Çözümü'nü**seçin, **F7**tuşuna basın veya projeye sağ tıklayın ve **Oluştur'u**seçin.

   Projenin hatasız oluşturması gerekir.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>DLL'yi aramak için basit yönetilen bir uygulama oluşturun

1. Visual Studio'u açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **konsol**yazın, **Şablonlar'ı**seçin ve ardından C# için **Konsol Uygulaması (.NET Core)** veya **Konsol Uygulaması'nı (.NET Framework)** seçin. Görünen iletişim kutusunda **Oluştur'u**seçin.

    Ardından, **Mixed_Mode_Calling_App** gibi bir ad yazın ve **Oluştur'u**tıklatın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **Windows Desktop'ı**seçin ve daha sonra orta bölmede Konsol **Uygulaması (.NET Framework)** veya **Konsol Uygulaması 'nı (.NET Core)** seçin.

    Ardından, **Mixed_Mode_Calling_App** gibi bir ad yazın ve **Tamam'ı**tıklatın.
    ::: moniker-end

    **Konsol Uygulaması** proje şablonu görmüyorsanız, Visual Studio Installer'ı açan **Araçlar** > **Araçları ve Özellikleri Al...**(Visual Studio Installer'ı açar) gidin. **.NET masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

    > [!NOTE]
    > Yeni yönetilen projeyi varolan C++ çözümünüzüde de ekleyebilirsiniz, ancak yeni bir çözüm oluşturmak daha fazla hata ayıklama senaryosunu destekler.

   Visual Studio boş projeoluşturur ve **Solution Explorer'da**görüntüler.

1. *Program.cs'daki* tüm kodu aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. Yeni kodda, dosya yolunu `[DllImport]` yeni oluşturduğunuz *Mixed_Mode_Debugging.dll'ye* dosya yolunuzla değiştirin. İpuçları için kod yorumuna bakın. *Kullanıcı adı* yer tutucuyu değiştirdiğinden emin olun.

1. **Dosyayı** > **Program.cs Kaydet'i** seçin veya dosyayı kaydetmek için **Ctrl**+**S** tuşuna basın.

## <a name="configure-mixed-mode-debugging"></a>Karışık mod hata ayıklama yapılandırma

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Bir .NET Framework uygulaması için karma mod hata ayıklama yapılandırmak için

1. **Çözüm Gezgini'nde,** **proje düğümüMixed_Mode_Calling_App** seçin ve **Özellikler** simgesini seçin veya proje düğümüne sağ tıklayın ve **Özellikler'i**seçin.

1. Sol bölmede Hata Ayıklama'yı seçin, **yerel kodu hata ayıklama** kutusunu etkinleştir'i seçin ve sonra değişiklikleri kaydetmek için özellikler sayfasını kapatın. **Debug**

    ![Karışık mod hata ayıklama etkinleştirme](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Bir .NET Core uygulaması için karışık mod hata ayıklama yapılandırmak için

Visual Studio 2017'den başlayan Visual Studio'nun çoğu sürümünde, bir .NET Core uygulamasında yerel kod için karışık mod hata ayıklama özelliğini etkinleştirmek için proje özellikleri yerine *launchSettings.json* dosyasını kullanmanız gerekir. Bu özellik için UI güncelleştirmelerini izlemek için bu [GitHub sorununa](https://github.com/dotnet/project-system/issues/1125)bakın.

1. **Solution Explorer'da,** **Özellikleri**genişletin ve *launchSettings.json* dosyasını açın.

   >[!NOTE]
   >Varsayılan olarak, *launchSettings.json* *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*' de dir. *launchSettings.json* yoksa, **Çözüm Gezgini'nde** **Mixed_Mode_Calling_App** projesini seçin ve ardından **Özellikler** simgesini seçin veya projeyi sağ tıklatın ve **Özellikler'i**seçin. **Hata Ayıklama** sekmesinde geçici bir değişiklik yapın ve projeyi oluşturun. Bu bir *launchSettings.json* dosyası oluşturur. **Hata Ayıklama** sekmesinde yaptığınız değişikliği geri getirin.

1. *launchsettings.json* dosyasında aşağıdaki satırı ekleyin:

    ```csharp
    "nativeDebugging": true
    ```

    Dosyanın tamamı aşağıdaki örnek gibi görünecektir:

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>Bir kesme noktası ayarlayın ve hata ayıklamaya başlayın

1. C# projesinde, açık *Program.cs.* En sol kenar boşluğuna tıklayarak, satırı seçerek ve **F9**tuşuna basarak veya satırı sağ tıklatarak ve **Breakpoint** > **Ekle Kesme Noktası'nı**seçerek aşağıdaki kod satırına bir kesme noktası ayarlayın.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Kesme noktasını ayarladığınız sol kenar boşluğunda kırmızı bir daire görüntülenir.

1. **F5 tuşuna**basın, Visual Studio araç çubuğundaki yeşil oku seçin veya hata ayıklama başlatmak için **Hata Ayıklama** > **Başlat hata ayıklama'yı** seçin.

   Hata ayıklama ayarladığınız kesme noktasında duraklar. Sarı ok, hata ayıklamanın şu anda duraklatılmış olduğu yeri gösterir.

## <a name="step-in-and-out-of-native-code"></a>Yerel koda girip çıkma

1. Yönetilen uygulamada hata ayıklama duraklatılmışken, **F11**tuşuna basın veya **Hata Ayıklama** > **Adımını**seçin.

   *Mixed_Mode.h* yerel üstbilgi dosyası açılır ve hata ayıklayıcının duraklatılmış olduğu sarı oku görürsünüz.

   ![Yerel koda geçme](../debugger/media/mixed-mode-step-into-native-code.png)

1. Artık kesme noktalarını ayarlayabilir ve vurabilir ve yerel veya yönetilen koddaki değişkenleri inceleyebilirsiniz.

   - Değerlerini görmek için kaynak koddaki değişkenlerin üzerine girin.

   - Otomatik ve **Yerel** **ler** pencerelerinde değişkene ve değerlerine bakın.

   - Hata ayıklamada duraklatılmış olsa da, **Watch** pencerelerini ve **Yığın'ı Arama** penceresini de kullanabilirsiniz.

1. Hata ayıklama bir satırı ilerletmek için **F11** tuşuna tekrar basın.

1. **Yürütmeye**+devam etmek ve yönetilen uygulamada yeniden duraklatmak için Shift**F11'e** basın veya **Hata Ayıklama** > **Adımı'nı** seçin.

1. Uygulamayı hata ayıklamaya devam etmek için **F5** tuşuna basın veya yeşil oku seçin.

Tebrikler! Karışık mod hata ayıklama ile ilgili eğitimi tamamladınız.

## <a name="next-step"></a>Sonraki adım

Bu öğreticide, karışık modhatagging'i etkinleştirerek yönetilen bir uygulamadan yerel kodu nasıl ayıkladığınızı öğrendiniz. Diğer hata ayıklama özelliklerine genel bakış için bkz:

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
