---
title: 'Öğretici: Hata ayıklama C# ve C++ kodu (karışık mod)'
description: Yerel bir DLL karışık mod hata ayıklaması'nı kullanarak bir .NET Core veya .NET Framework uygulamasında hata ayıklama hakkında bilgi edinin
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
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416366"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Öğretici: Hata ayıklama C# ve aynı C++ hata ayıklama oturumu

Visual Studio, birden fazla hata ayıklayıcı türü karışık mod hata ayıklama çağrılan hata ayıklama oturumunda, etkinleştirmenize olanak tanır. Bu öğreticide, tek bir hata ayıklama oturumunda hem yönetilen hem de yerel kod hatalarını ayıklamak öğrenin.

Bu öğreticide, yönetilen bir uygulamadaki yerel kodun hatalarını ayıklamanın nasıl yapılacağı gösterilir, ancak [yönetilen kodda yerel bir uygulamadan da hata ayıklaması](../debugger/how-to-debug-in-mixed-mode.md)yapabilirsiniz. Hata ayıklayıcı, [Python ve yerel kodun](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)hatalarını ayıklama gibi diğer karışık mod hata ayıklama türlerini de destekler ve ASP.NET gibi uygulama türlerinde betik hata ayıklayıcısını kullanma.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Basit bir yerel DLL oluşturma
> * DLL çağırmak için basit bir .NET Core veya .NET Framework uygulaması oluşturma
> * Karışık mod hata ayıklama yapılandırma
> * Hata ayıklayıcıyı başlatın
> * Yönetilen bir uygulama içinde bir kesme noktasına isabet
> * Yerel kod içine adımla

## <a name="prerequisites"></a>Önkoşullar

Visual Studio, aşağıdaki iş yükleri ile yüklü olması gerekir:
- **İle masaüstü geliştirmeC++**
- Oluşturmak istediğiniz uygulama türüne bağlı olarak **.net masaüstü geliştirme** veya **.NET Core platformlar arası geliştirme**.

Visual Studio yoksa, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.

Visual Studio yüklü, ancak ihtiyacınız olan iş yüklerine sahip değilseniz, Visual Studio **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** ' ı seçin. Visual Studio Yükleyicisi, ihtiyacınız olan iş yüklerini seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-simple-native-dll"></a>Basit bir yerel DLL oluşturma

**DLL projesi dosyalarını oluşturmak için:**

1. Visual Studio 'Yu açın ve bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **boş proje**yazın, **Şablonlar**' ı seçin ve ardından **boş proje** ' yi C++seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin. Ardından, **Mixed_Mode_Debugging** gibi bir ad yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C++** altında **diğer**' i seçin ve ardından Ortadaki bölmede **boş proje**' yi seçin. Ardından, **Mixed_Mode_Debugging** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Boş proje** projesi şablonu görmüyorsanız Araçlar **ve Özellikler > ...** ' a giderek Visual Studio yükleyicisi açan **Araçlar** ' a gidin. Visual Studio Yükleyicisi'ni başlatır. İş yüküyle **Masaüstü geliştirmeyi C++**  seçin ve ardından **Değiştir**' i seçin.

    Visual Studio projesi oluşturur.

1. **Çözüm Gezgini**, **kaynak dosyalar**' ı seçin ve ardından **Proje** > **Yeni öğe Ekle**' yi seçin. Ya da, **kaynak dosyalar** ' a sağ tıklayıp > **Yeni öğe** **Ekle** ' yi seçin.

1. **Yeni öğe** iletişim kutusunda  **C++ dosya (. cpp)** öğesini seçin. **Ad** alanına **Mixed_Mode. cpp** yazın ve ardından **Ekle**' yi seçin.

    Visual Studio, yeni C++ dosyayı **Çözüm Gezgini**ekler.

1. Aşağıdaki kodu *Mixed_Mode. cpp*' ye kopyalayın:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. **Çözüm Gezgini**, **üst bilgi dosyaları**' nı seçin ve ardından **Proje** > **Yeni öğe Ekle**' yi seçin. Ya da **üst bilgi dosyalarını** sağ tıklayıp > **Yeni öğe** **Ekle** ' yi seçin.

1. **Yeni öğe** Iletişim kutusunda **üst bilgi dosyası (. h)** seçeneğini belirleyin. **Ad** alanına **Mixed_Mode. h** yazın ve ardından **Ekle**' yi seçin.

   Visual Studio **Çözüm Gezgini**yeni başlık dosyasını ekler.

1. Aşağıdaki kodu *Mixed_Mode. h*içine kopyalayın:

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

1. Dosyaları kaydetmek > **Dosya** **Tümünü Kaydet** ' i seçin veya **CTRL**+**SHIFT**+**S** tuşlarına basın.

**DLL projesini yapılandırmak ve derlemek için:**

1. Visual Studio araç çubuğunda **Hata Ayıkla** yapılandırma ve **x86** veya **x64** platform ' u seçin. Çağıran uygulamanız .NET Core olacaktır, her zaman 64 bit modunda çalışır, platform olarak **x64** ' u seçin.

1. **Çözüm Gezgini**, **Mixed_Mode_Debugging** projesi düğümünü seçin ve **Özellikler** simgesini seçin ya da proje düğümüne sağ tıklayıp **Özellikler**' i seçin.

1. **Özellikler** bölmesinin üst kısmında, **yapılandırmanın** **etkin (hata ayıklama)** olarak ayarlandığından ve **platformun** araç çubuğunda ayarlandıklarla aynı olduğundan emin olun: **x64**veya x86 platformu için **Win32** .

   > [!IMPORTANT]
   > Platformu **x86** 'dan **x64** 'e veya bunun tersini yaparsanız, yeni platformun özelliklerini yeniden yapılandırmanız gerekir.

1. Sol bölmedeki **yapılandırma özellikleri** altında **bağlayıcı** > **Gelişmiş**' i seçin ve **giriş noktası yok ' un**yanındaki açılan listede **Hayır**' ı seçin. **Hayır**olarak değiştirmeniz gerekiyorsa, **Uygula**' yı seçin.

1. **Yapılandırma özellikleri**' nin altında **genel**' i seçin ve **yapılandırma türü**' nün yanındaki açılan listede **dinamik kitaplık (. dll)** öğesini seçin. **Uygula**’yı ve sonra **Tamam**’ı seçin.

   ![Yerel bir DLL için geçiş](../debugger/media/mixed-mode-set-as-native-dll.png)

1. **Çözüm Gezgini** ' de projeyi seçin ve ardından **Yapı** > **derleme çözümü**' nü seçin, **F7**tuşuna basın veya projeye sağ tıklayıp **Oluştur**' u seçin.

   Projenin hatasız oluşturması gerekir.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>DLL çağırmak için basit bir yönetilen uygulama oluşturma

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **konsolu**yazın, **Şablonlar**' ı seçin ve ardından **konsol uygulaması (.NET Core)** ya da **konsol uygulaması (.NET Framework)** seçeneğini belirleyin C#. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.

    Ardından, **Mixed_Mode_Calling_App** gibi bir ad yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** veya **konsol uygulaması (.NET Core)** seçeneğini belirleyin.

    Ardından, **Mixed_Mode_Calling_App** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması** proje şablonunu görmüyorsanız **Araçlar** ve Özellikler al > ' a gidin ve Visual Studio yükleyicisi açan **Araçlar ve Özellikler...** ' a gidin. **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    > [!NOTE]
    > Var olan C++ çözümünüze yeni yönetilen proje de ekleyebilirsiniz, ancak yeni çözüm oluşturmaya daha fazla hata ayıklama senaryoları destekler.

   Visual Studio boş projeyi oluşturur ve **Çözüm Gezgini**görüntüler.

1. *Program.cs* içindeki tüm kodu aşağıdaki kodla değiştirin:

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

1. Yeni kodda, `[DllImport]` içindeki dosya yolunu dosya yolunuzla değiştirin ve yeni oluşturduğunuz *Mixed_Mode_Debugging. dll* ile değiştirin. Kod açıklaması ipuçları için bkz. *Kullanıcı adı* yer tutucusunu değiştirdiğinizden emin olun.

1. Dosyayı kaydetmek için **dosya** > +**Kaydet** ' i seçin veya **CTRL** **S** tuşuna basın.

## <a name="configure-mixed-mode-debugging"></a>Karışık mod hata ayıklama yapılandırma

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Karışık mod hata ayıklama için .NET Framework uygulamasını yapılandırmak için

1. **Çözüm Gezgini**, **Mixed_Mode_Calling_App** projesi düğümünü seçin ve **Özellikler** simgesini seçin ya da proje düğümüne sağ tıklayıp **Özellikler**' i seçin.

1. Sol bölmedeki **Hata Ayıkla** ' yı seçin, **yerel kod hata ayıklamayı etkinleştir** onay kutusunu seçin ve ardından değişiklikleri kaydetmek için Özellikler sayfasını kapatın.

    ![Karışık modda hata ayıklama etkinleştirme](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Karışık mod hata ayıklama için .NET Core uygulamasını yapılandırmak için

Visual Studio 'nun çoğu Visual Studio 2017 sürümünden itibaren, bir .NET Core uygulamasında yerel kod için karışık modda hata ayıklamayı etkinleştirmek üzere proje özellikleri yerine *Launchsettings. JSON* dosyasını kullanmanız gerekir. Bu özelliğe yönelik kullanıcı arabirimi güncelleştirmelerini izlemek için bu [GitHub sorununa](https://github.com/dotnet/project-system/issues/1125)bakın.

1. **Çözüm Gezgini**, **Özellikler**' i genişletin ve *launchsettings. JSON* dosyasını açın.

   >[!NOTE]
   >Varsayılan olarak, *Launchsettings. JSON* , *C:\users\username\source\repos\ Mixed_Mode_Calling_App \properties*dizininde bulunur. *Launchsettings. JSON* yoksa, **Çözüm Gezgini** **Mixed_Mode_Calling_App** projesi seçin ve ardından **Özellikler** simgesini seçin ya da projeye sağ tıklayıp **Özellikler**' i seçin. **Hata ayıklama** sekmesinde geçici bir değişiklik yapın ve projeyi derleyin. Bu işlem bir *Launchsettings. JSON* dosyası oluşturur. **Hata ayıklama** sekmesinde yaptığınız değişikliği tekrar alın.

1. *Launchsettings. JSON* dosyasında aşağıdaki satırı ekleyin:

    ```csharp
    "nativeDebugging": true
    ```

    Tam dosya aşağıdaki örnekteki gibi görünür:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Bir kesme noktası ayarlayın ve hata ayıklamayı Başlat

1. C# Projesinde *program.cs*öğesini açın. En soldaki kenar boşluğuna tıklayarak, satırı seçip **F9**tuşuna basarak ya da satıra sağ **tıklayıp kesme noktası** **Ekle** > kesme noktası ' nı seçerek aşağıdaki kod satırında bir kesme noktası ayarlayın.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Kırmızı bir daire Kesme noktasının ayarlandığı sol kenar boşluğunda görünür.

1. **F5**tuşuna basın, Visual Studio araç çubuğunda yeşil oku seçin veya hata ayıklamayı başlatmak Için hata **ayıklamayı Başlat** > hata **Ayıkla** ' yı seçin.

   Hata ayıklayıcı, ayarladığınız kesme noktasına duraklatır. Sarı bir ok, hata ayıklayıcı şu anda duraklatılmış burada gösterir.

## <a name="step-in-and-out-of-native-code"></a>Yerel kod, içeri ve dışarı adım

1. Yönetilen uygulamada hata ayıklama duraklatıldığında, **F11**tuşuna basın veya > **adımla** **Hata Ayıkla** ' yı seçin.

   *Mixed_Mode. h* yerel üstbilgi dosyası açılır ve hata ayıklayıcının duraklatıldığı sarı oku görürsünüz.

   ![Yerel kod içine adımla](../debugger/media/mixed-mode-step-into-native-code.png)

1. Şimdi, ayarlayabilir ve kesme noktaları isabet ve yerel veya yönetilen kodda değişkenleri denetleyin.

   - Değerleri görmek için kaynak kodundaki değişkenleri üzerine gelin.

   - **Oto** ve **Yereller** pencerelerinde değişkene ve bunların değerlerine bakın.

   - Hata ayıklayıcıda duraklalarken, **Gözcü** pencereleri ve **çağrı yığını** penceresini de kullanabilirsiniz.

1. Hata ayıklayıcıyı bir satır ilerlemek için **F11** tuşuna basın.

1. Yürütmeye devam etmek ve yönetilen uygulamada yeniden duraklatmak için **shıft**+**F11** tuşuna basın veya **Hata Ayıkla** > **Step Out** ' ı seçin.

1. Uygulamada hata ayıklamaya devam etmek için **F5** tuşuna basın veya yeşil oku seçin.

Tebrikler! Karışık mod hata ayıklama şirket öğreticisini tamamladınız.

## <a name="next-step"></a>Sonraki adım

Bu öğreticide, karma mod hata ayıklama etkinleştirerek yönetilen yerel kod hata ayıklama öğrendiniz. Diğer hata ayıklayıcı özelliklerine genel bakış için bkz:

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
