---
title: 'Öğretici: C# ve C++ kodunda hata ayıklama (karma mod)'
description: Karma modda hata ayıklama kullanarak bir .NET Core veya .NET Framework uygulamasından yerel DLL hatalarını ayıklamayı öğrenin
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
manager: jmartens
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 4b1d250ed5306ce101fd7482b740ad57514e4f0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899419"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Öğretici: aynı hata ayıklama oturumunda C# ve C++ hatalarını ayıklama

Visual Studio, karışık modda hata ayıklama olarak adlandırılan bir hata ayıklama oturumunda birden fazla hata ayıklayıcı türünü etkinleştirmenizi sağlar. Bu öğreticide, tek bir hata ayıklama oturumunda hem yönetilen hem de yerel kodda hata ayıklamayı öğreneceksiniz.

Bu öğreticide, yönetilen bir uygulamadaki yerel kodun hatalarını ayıklamanın nasıl yapılacağı gösterilir, ancak [yönetilen kodda yerel bir uygulamadan da hata ayıklaması](../debugger/how-to-debug-in-mixed-mode.md)yapabilirsiniz. Hata ayıklayıcı, [Python ve yerel kodun](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)hatalarını ayıklama gibi diğer karışık mod hata ayıklama türlerini de destekler ve ASP.NET gibi uygulama türlerinde betik hata ayıklayıcısını kullanma.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Basit bir yerel DLL oluşturma
> * DLL 'yi çağırmak için basit bir .NET Core veya .NET Framework uygulaması oluşturma
> * Karışık modda hata ayıklamayı yapılandırma
> * Hata ayıklayıcıyı Başlat
> * Yönetilen uygulamadaki bir kesme noktasına isabet edin
> * Yerel koda adımla

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki iş yükleriyle Visual Studio yüklü olmalıdır:
- **C++ ile masaüstü geliştirme**
- Oluşturmak istediğiniz uygulama türüne bağlı olarak **.net masaüstü geliştirme** veya **.NET Core platformlar arası geliştirme**.

Visual Studio yoksa, ücretsiz olarak yüklemek için [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.

Visual Studio yüklü, ancak ihtiyacınız olan iş yüklerine sahip değilseniz, Visual Studio **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** ' ı seçin. Visual Studio Yükleyicisi, ihtiyacınız olan iş yüklerini seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-simple-native-dll"></a>Basit bir yerel DLL oluşturma

**DLL projesi dosyalarını oluşturmak için:**

1. Visual Studio 'Yu açın ve bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **boş proje** yazın, **Şablonlar**' ı seçin ve ardından C++ için **boş proje** ' yi seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin. Ardından, **Mixed_Mode_Debugging** gibi bir ad yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C++** altında **diğer**' i seçin ve ardından Ortadaki bölmede **boş proje**' yi seçin. Ardından, **Mixed_Mode_Debugging** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Boş proje** projesi şablonunu görmüyorsanız, **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açan araçlar ' a gidin. Visual Studio Yükleyicisi başlatılır. C++ iş yükü **Ile masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

    Visual Studio projeyi oluşturur.

1. **Çözüm Gezgini**, **kaynak dosyalar**' ı seçin ve ardından **Proje**  >  **Yeni öğe Ekle**' yi seçin. Ya da, **kaynak dosyalar** ' a sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin.

1. **Yeni öğe** iletişim kutusunda **C++ dosyası (. cpp)** öğesini seçin. **Ad** alanına **Mixed_Mode. cpp** yazın ve ardından **Ekle**' yi seçin.

    Visual Studio **Çözüm Gezgini** yeni C++ dosyasını ekler.

1. Aşağıdaki kodu *Mixed_Mode. cpp*' ye kopyalayın:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. **Çözüm Gezgini**, **üst bilgi dosyaları**' nı ve ardından **Proje**  >  **Ekle yeni öğe**' yi seçin. Ya da **üstbilgi dosyaları** ' na sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin.

1. **Yeni öğe** Iletişim kutusunda **üst bilgi dosyası (. h)** seçeneğini belirleyin. **Ad** alanına **Mixed_Mode. h** yazın ve ardından **Ekle**' yi seçin.

   Visual Studio **Çözüm Gezgini** yeni başlık dosyasını ekler.

1. Aşağıdaki kodu *Mixed_Mode. h* içine kopyalayın:

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

1. **Dosya**  >  **Tümünü Kaydet** ' i seçin veya +  +  dosyaları kaydetmek için CTRL SHIFT 'e basın.

**DLL projesini yapılandırmak ve derlemek için:**

1. Visual Studio araç çubuğunda **Hata Ayıkla** yapılandırma ve **x86** veya **x64** platform ' u seçin. Çağıran uygulamanız .NET Core olacaktır, her zaman 64 bit modunda çalışır, platform olarak **x64** ' u seçin.

1. **Çözüm Gezgini**, **Mixed_Mode_Debugging** projesi düğümünü seçin ve **Özellikler** simgesini seçin ya da proje düğümüne sağ tıklayıp **Özellikler**' i seçin.

1. **Özellikler** bölmesinin üst kısmında, **yapılandırmanın** **etkin (hata ayıklama)** olarak ayarlandığından ve **platformun** araç çubuğunda ayarlandıklarla aynı olduğundan emin olun: **x64** veya x86 platformu için **Win32** .

   > [!IMPORTANT]
   > Platformu **x86** 'dan **x64** 'e veya bunun tersini yaparsanız, yeni platformun özelliklerini yeniden yapılandırmanız gerekir.

1. Sol bölmedeki **yapılandırma özellikleri** altında **bağlayıcı**  >  **Gelişmiş**' i seçin ve **giriş noktası yok ' un** yanındaki açılan listede **Hayır**' ı seçin. **Hayır** olarak değiştirmeniz gerekiyorsa, **Uygula**' yı seçin.

1. **Yapılandırma özellikleri**' nin altında **genel**' i seçin ve **yapılandırma türü**' nün yanındaki açılan listede **dinamik kitaplık (. dll)** öğesini seçin. **Uygula**’yı ve sonra **Tamam**’ı seçin.

   ![Yerel DLL 'ye geç](../debugger/media/mixed-mode-set-as-native-dll.png)

1. **Çözüm Gezgini** ' de projeyi seçin ve ardından yapı   >  **oluşturma çözümü** oluştur ' u seçin, **F7** tuşuna basın veya projeye sağ tıklayıp **Oluştur**' u seçin.

   Projenin hatasız oluşturması gerekir.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>DLL 'yi çağırmak için basit bir yönetilen uygulama oluşturma

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **konsolu** yazın, **Şablonlar**' ı seçin ve ardından C# için **konsol uygulaması (.NET Core)** ya da **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.

    Ardından, **Mixed_Mode_Calling_App** gibi bir ad yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında **Windows Masaüstü**' nün ardından orta bölmedeki **konsol uygulaması (.NET Framework)** veya **konsol uygulaması (.NET Core)** seçeneğini belirleyin.

    Ardından, **Mixed_Mode_Calling_App** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması** proje şablonunu görmüyorsanız **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açan araçlar ' a gidin. **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    > [!NOTE]
    > Ayrıca, yeni yönetilen projeyi mevcut C++ çözümünüze ekleyebilirsiniz. Karışık modda hata ayıklama görevinin daha zor olması için projeyi yeni bir çözümde oluşturacağız.

   Visual Studio boş projeyi oluşturur ve **Çözüm Gezgini** görüntüler.

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

1. Yeni kodda, içindeki dosya yolunu `[DllImport]` Dosya yolunuzla yeni oluşturduğunuz *Mixed_Mode_Debugging.dll* değiştirin. İpuçları için kod yorumu bölümüne bakın. *Kullanıcı adı* yer tutucusunu değiştirdiğinizden emin olun.

1. Dosya   >  **Kaydet program.cs** seçin veya  + dosyayı kaydetmek için CTRL **S** tuşuna basın.

## <a name="configure-mixed-mode-debugging"></a>Karışık modda hata ayıklamayı yapılandırma

1. **Çözüm Gezgini**, **Mixed_Mode_Calling_App** projesi düğümünü seçin ve **Özellikler** simgesini seçin ya da proje düğümüne sağ tıklayıp **Özellikler**' i seçin.

1. Sol bölmedeki **Hata Ayıkla** ' yı seçin, **yerel kod hata ayıklamayı etkinleştir** onay kutusunu seçin ve ardından değişiklikleri kaydetmek için Özellikler sayfasını kapatın.

    ![Karışık modda hata ayıklamayı etkinleştir](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="set-a-breakpoint-and-start-debugging"></a>Kesme noktası ayarlama ve hata ayıklamayı başlatma

1. C# projesinde *program.cs* öğesini açın. En soldaki kenar boşluğuna tıklayarak, satırı seçip **F9** tuşuna basarak ya da satıra sağ **tıklayıp kesme noktası**  >  **Ekle kesme noktası**' nı seçerek aşağıdaki kod satırında bir kesme noktası ayarlayın.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Sol kenar boşluğunda, kesme noktasını ayarladığınız kırmızı bir daire görünür.

1. **F5** tuşuna basın, Visual Studio araç çubuğunda yeşil oku seçin veya hata ayıklamayı başlatmak   >  için hata **ayıklamayı Başlat** ' ı seçin.

   Hata ayıklayıcı, ayarladığınız kesme noktasında duraklatılır. Sarı bir ok, hata ayıklayıcının Şu anda duraklatıldığını gösterir.

## <a name="step-in-and-out-of-native-code"></a>Yerel kod içine ve dışına adımla

1. Yönetilen uygulamada hata ayıklama duraklatıldığında, **F11** tuşuna basın veya **hata ayıklama**  >  **adımı**' nı seçin.

   *Mixed_Mode. h* yerel üstbilgi dosyası açılır ve hata ayıklayıcının duraklatıldığı sarı oku görürsünüz.

   ![Yerel koda adımla](../debugger/media/mixed-mode-step-into-native-code.png)

1. Şimdi, kesme noktaları ayarlayıp, yerel veya Yönetilen koddaki değişkenleri inceleyebilirsiniz.

   - Değerlerini görmek için kaynak kodundaki değişkenlerin üzerine gelin.

   - **Oto** ve **Yereller** pencerelerinde değişkene ve bunların değerlerine bakın.

   - Hata ayıklayıcıda duraklalarken, **Gözcü** pencereleri ve **çağrı yığını** penceresini de kullanabilirsiniz.

1. Hata ayıklayıcıyı bir satır ilerlemek için **F11** tuşuna basın.

1.  + Yürütmeye devam etmek için SHIFT **F11** tuşuna basın veya **hata ayıklama**  >  **adımını** seçin seçeneğini belirleyin.

1. Uygulamada hata ayıklamaya devam etmek için **F5** tuşuna basın veya yeşil oku seçin.

Tebrikler! Karışık modda hata ayıklama öğreticisini tamamladınız.

## <a name="next-step"></a>Sonraki adım

Bu öğreticide, karışık modda hata ayıklamayı etkinleştirerek, yönetilen bir uygulamadaki yerel kodun hatalarını ayıklamanın nasıl yapılacağını öğrendiniz. Diğer hata ayıklayıcı özelliklerine genel bakış için bkz.:

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
